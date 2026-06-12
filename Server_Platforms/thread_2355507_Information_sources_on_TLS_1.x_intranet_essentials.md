---
title: "Information sources on TLS 1.x intranet essentials?"
date: 2017-03-13
forum: Server Platforms
---

### Post by bcschmerker on 2017-03-13
I am currently researching to-do's for building a new Ethernet for a member Congregation of the OMS Holiness Church of North America.  I already plan on locking client browsers to Transport Layer Security, ideally the latest draft of 1.3 but with 1.2 as a fallback; anticipated UI softwares include OpenLP 2.4-up, Mozilla Firefox 52-up, LibreOffice 5.3-up, and other applications with as few security holes as currently possible.  Ideally, I'd use twisted-Edwards-curve key exchange and authentication algorithms, as the IETF is already writing curve25519 into TLS 1.3; and Camellia128-GCM block and ChaCha20-Poly1305 stream ciphers (as both accept SHA256 hashes).  (The public Ethernet would use AES128_GCM_SHA256, AES256_GCM_SHA384, and CHACHA20_POLY1305_SHA256 ciphers on ECC_256_SHA384 and RSA_8192_SHA384 certificates from a Public Registry to be determined.)

The rub I'm anticipating is certification and a private root therefor; the internal certs would ideally be ED25519's with at least a SHA256 and ideally a SHA512 hash.  What information is available on the build procedures for TLS in general; and what "top" Packages (with required libraries among the Depends thereof) would be useful for the task?

---

