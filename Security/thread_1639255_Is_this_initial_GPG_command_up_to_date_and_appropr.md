---
title: "Is this initial GPG command up to date and appropriate?"
date: 2010-12-06
forum: Security
---

### Post by spaceboy909 on 2010-12-06
I know from past experience that Wiki's and guides can have out dated, or even less than the best info sometimes, so I want to double check on this.

[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

The above guide suggests this command and parameters:
```
gpg --cert-digest-algo=SHA256 --default-preference-list="h10 h8 h9 h11 s9 s8 s7 s3 z2 z3 z1 z0" --gen-key
```But in other guides I've seen, they just have:  "gpg --gen-key", and skip the other parameters.  Which approach should I take?

If it matters, I'm just starting out with packaging and develpment.....nothing heavy duty!

---

### Post by CharlesA on 2010-12-06
Are you trying to create your gpg keypair?

---

### Post by cariboo on 2010-12-06
I found the instructions [here]("https://help.launchpad.net/YourAccount/ImportingYourPGPKey"), very easy to follow.

---

### Post by spaceboy909 on 2010-12-06
> **CharlesA said:**
> Are you trying to create your gpg keypair?
Yes, I'm starting from scratch.

> **cariboo907 said:**
> I found the instructions [here]("https://help.launchpad.net/YourAccount/ImportingYourPGPKey"), very easy to follow.
Thanks, I'll check that out.  Since I'll be using a Launchpad account, that might be the best place for me to start.  :)

---

### Post by CharlesA on 2010-12-06
I used Passwords and Encryption Keys in Ubuntu Desktop to create my keypair.

---

