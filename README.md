# ElGamal Encryption and Related Zero-Knowledge Proofs

[![Build Status](https://github.com/slowli/elastic-elgamal/workflows/Rust/badge.svg?branch=main)](https://github.com/slowli/elastic-elgamal/actions)
[![License: MIT OR Apache-2.0](https://img.shields.io/badge/License-MIT%2FApache--2.0-blue)](https://github.com/slowli/elastic-elgamal#license)
![rust 1.51.0+ required](https://img.shields.io/badge/rust-1.51.0+-blue.svg?label=Required%20Rust)

**Documentation:**
[![crate docs (master)](https://img.shields.io/badge/master-yellow.svg?label=docs)](https://slowli.github.io/elastic-elgamal/elastic_elgamal/)

Implementation of [ElGamal encryption] and related zero-knowledge proofs
with pluggable crypto backend.

The following protocols are included:

- Additively homomorphic ElGamal encryption
- Zero-knowledge proofs of zero encryption and Boolean value encryption
- Zero-knowledge range proofs for ElGamal ciphertexts
- Additively homomorphic 1-of-n choice encryption and the corresponding
  zero-knowledge proof of correctness
- Threshold ElGamal encryption via [Shamir's secret sharing][sss],
  including distributed key generation and verifiable distributed decryption.

## ⚠ Warnings

While the logic in this crate relies on standard cryptographic assumptions
(complexity of [decisional Diffie–Hellman][DDH], [computational Diffie–Hellman][CDH]
and [discrete log][DLP] problems in certain groups),
it has not been independently verified for correctness or absence of side-channel attack
vectors. **Use at your own risk.**

ElGamal encryption is not a good choice for general-purpose public-key encryption
since it is vulnerable to [chosen-ciphertext attacks][CCA]. For security,
decryption operations should be limited on the application level.

## Usage

Add this to your `Crate.toml`:

```toml
[dependencies]
elastic-elgamal = "0.1.0" 
```

See the crate docs for the examples of usage.

## Naming

"Elastic" refers to pluggable backends, encryption with a key shared
among a variable number of participants, and the construction of zero-knowledge ring proofs
(a proof consists of a variable number of rings, each of which consists of a variable number
of admissible values).
`elastic_elgamal` is also one of [autogenerated Docker container names][docker-rng].

## License

Licensed under either of [Apache License, Version 2.0](LICENSE-APACHE)
or [MIT license](LICENSE-MIT) at your option.

<small>Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in `elastic-elgamal` by you, as defined in the Apache-2.0 license,
shall be dual licensed as above, without any additional terms or conditions.</small>

[ElGamal encryption]: https://en.wikipedia.org/wiki/ElGamal_encryption
[sss]: https://en.wikipedia.org/wiki/Shamir%27s_Secret_Sharing
[DDH]: https://en.wikipedia.org/wiki/Decisional_Diffie%E2%80%93Hellman_assumption
[CDH]: https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_problem
[DLP]: https://en.wikipedia.org/wiki/Discrete_logarithm
[CCA]: https://en.wikipedia.org/wiki/Chosen-ciphertext_attack
[docker-rng]: https://github.com/moby/moby/blob/master/pkg/namesgenerator/names-generator.go
