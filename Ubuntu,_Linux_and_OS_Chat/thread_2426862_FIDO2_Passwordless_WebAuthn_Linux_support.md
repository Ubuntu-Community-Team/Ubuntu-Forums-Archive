---
title: "FIDO2 Passwordless WebAuthn Linux support ?"
date: 2019-09-14
forum: Ubuntu, Linux and OS Chat
---

### Post by Sami Lehtinen on 2019-09-14
I've tested a few [FIDO2]("https://fidoalliance.org/fido2/") authenticators with Ubuntu (Xubuntu 18.04 to be exact) and I couldn't get passwordless authentication to work with Firefox. This isn't in official Ubuntu support forum, because I think this is much more generic issue. 

Does anyone know if there's a project to add FIDO2 passwordless support to Linux? With Windows it seems that the passwordless authentication is handled by the Operating System prompt window, but normal U2F is handled by Firefox.

I do find several posts (forums, blogs, articles) about Linux needs FIDO2 support, but I couldn't find any information if it's being already developed. 

 - Thank you

My test posts: [ [SoloKeys & FIDO2 & U2F with Linux / Ubuntu in general]("https://www.sami-lehtinen.net/blog/fido2-webauthn-ctap2-public-key-authentication-u2f") & [eWBM L2]("https://www.sami-lehtinen.net/blog/fido2-ewbm-goldengate-security-key-g310") ]

---

### Post by TheFu on 2019-09-14
I am clueless, but not using passwords violates the entire idea of 2FA, doesn't it?

[https://www.linuxjournal.com/content/webauthn-web-authentication-yubikey-5](https://www.linuxjournal.com/content/webauthn-web-authentication-yubikey-5)

Linux isn't Windows, as you know.

---

### Post by Sami Lehtinen on 2019-09-15
Violate [2FA / MFA]("https://en.wikipedia.org/wiki/Multi-factor_authentication")? No, it's 2FA. With SoloKeys and most of Level 1 FIDO2 Authenticators, you'll be using PIN to unlock private key stored in HSM = 2FA. And with Level 2 like the eWBM Biometric Goldenkey equipped with fingerprint reader you'll use fingerprint t o unlock the private key stored in HSM.

In both cases even if it's passwordless, it's still a 2FA authentication using two factors.

Sure I know Linux isn't Windows. But having FIDO2 authentication to work would be great. This is one of the standards which I personally happen to really like, because it solves so many classic problems of authentication.

I've had so many long discussions about these questions and approaching the problem from different aspect. Some would prefer the standard system key manager to support features required for WebAuthn and so on. Fact is that nothing prevents doing software implementation, as well as there's support for native HSM modules like TPM and Android Keystore, etc.

I'm quite sure someone will come up with PAM module for Linux login. But it still doesn't fix the inherent lack of support for FIDO2.

---

