---
title: "Will 18.04 upgrade to OpenSSL 1.1.1 or later? (ED25519 support)"
date: 2018-07-05
forum: Server Platforms
---

### Post by michael-steffens-b on 2018-07-05
The current release of libss1.1 in Bionic is 1.1.0g-2ubuntu4.1. OpenSSL upstream is currently emitting a series of pre-releases of 1.1.1. Will that version, once finally released by OpenSSL, propagate into the current Ubuntu LTS version?
Motivation is support of the ED25519 signature algorithm, which is being introduced by OpenSSL-1.1.1. I'd like to know whether I can expect it to become available in 18.04 during LTS lifetime.

Thanks a lot in advance!

---

### Post by deadflowr on 2018-07-06
Likelihood is not that high.
Ubuntu never upgrades versions of software unless it's impossible not to.
They'll patch the heck of out of it, but most likely won't upgrade it to a new version.

---

### Post by Irihapeti on 2018-07-07
If you're talking about using ED25519 format keys, then this is already available in OpenSSL in 18.04

I've recently changed my keys to that format.

---

### Post by michael-steffens-b on 2018-07-09
> **Irihapeti said:**
> If you're talking about using ED25519 format keys, then this is already available in OpenSSL in 18.04

I've recently changed my keys to that format.

Yes, that's what I need to accomplish! However, using the libssl1.1 release 1.1.0g-2ubuntu4.1, nginx fails to load certificate and key

```

SSL: error:0609E09C:digital envelope routines:pkey_set_type:unsupported algorithm error:0B09406F:x509 certificate routines:x509_pubkey_decode:unsupported algorithm error:140AB18F:SSL routines:SSL_CTX_use_certificate:ee key too small

```

For the attempt above I have used an ED25519 key and a X.509 certificate generated using the CLI from release 1.1.1-pre8, as the one coming with 18.04 also rejects that:

```

# openssl genpkey -algorithm ED25519
Algorithm ED25519 not found

```

What OpenSSL library are you using on 18.04 and how did you generate key and certificate?

---

### Post by Irihapeti on 2018-07-09
I think you may be right. I was thinking of OpenSSH keys, which can be generated using the standard version installed in 18.04. I've yet to upgrade the certificates for my webserver.

My apologies.

---

### Post by michael-steffens-b on 2018-07-09
> **deadflowr said:**
> 
They'll patch the heck of out of it, but most likely won't upgrade it to a new version.


So I could rephrase my question: Would you consider ED25519 support likely to be patched into 18.04 bundled OpenSSL 1.1.0?

---

### Post by michael-steffens-b on 2018-07-09
I have submitted a bug to get ED25519 included in Bionic OpenSSL: [https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/1780807](https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/1780807)

You might want to support this request by upvoting, in case it also affects you.

---

