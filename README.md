# Vault Sentinel Policies

Endpoint governing policies:

1. `validate_zip_codes` validates that any key named "zipcode", "zip_code", or "zip-code" contains a valid 5-digit U.S. zipcode.  EGP Policy, paths = secret/*
2. `validate_state_codes` validates that any key named "state" contains a valid U.S. state code.  EGP Policy, paths = secret/*
3. `validate_root_aws_keys` validates that any path having both access_key and secret_key keys contain valid AWS keys.  EGP Policy, paths = *
  a. This ensures that the root keys for an instance of the AWS secrets engine in path <path>/config/root are valid.
  b. Since the AWS secret engine may exist at multiple paths, the path is set to "*".
4. `business_hours` EGP on one namespace that only allows writing secrets between 8am and 8pm EDT on Monday to Friday.  EGP Policy, paths = secret/*
