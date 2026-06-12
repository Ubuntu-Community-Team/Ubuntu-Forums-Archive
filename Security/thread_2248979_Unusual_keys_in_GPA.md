---
title: "Unusual keys in GPA"
date: 2014-10-18
forum: Security
---

### Post by DanR01 on 2014-10-18
I installed GPA (GNU Privacy Assistant) through Synaptic. It fails to launch correctly from the dash; however if run from the terminal via 

```
sudo gpa
```

it works and displays multiple keys that I have never added (see screenshot). These seem to be keys that relate to German Federal agencies or their associates.

When I run as a normal user, or root

```
gpg --list-keys
```

I don't see these keys.

Can anyone explain?

---

### Post by CitadelUniversal on 2014-10-19
If in doubt on how to use the GPA Software please have a look at it's documentation here [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)  - & also here [https://www.gnupg.org/documentation/index.html](https://www.gnupg.org/documentation/index.html) - these should help you out if not please report back.

---

