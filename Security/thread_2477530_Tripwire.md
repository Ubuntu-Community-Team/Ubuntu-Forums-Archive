---
title: "Tripwire"
date: 2022-07-26
forum: Security
---

### Post by jacksonguitars on 2022-07-26
Dear sirs and ladies!

Tripwire reports this file as being changed " etc/apt/trusted.gpg.d/google-chrome.gpg" do I have to worry about it?

---

### Post by Frogs Hair on 2022-07-28
***Moved to Security. ***

---

### Post by #&amp;thj^% on 2022-07-28
> **jacksonguitars said:**
> Dear sirs and ladies!

Tripwire reports this file as being changed " etc/apt/trusted.gpg.d/google-chrome.gpg" do I have to worry about it?

This is Debian's security best practices, >> apt-key is deprecated and will not be available after Debian 11 / Ubuntu 22.04 

GPG keys for third party repositories should be added to "/usr/share/keyrings" and referenced with the signed-by option in the "source.list.d" entry.
Source: [https://wiki.debian.org/DebianRepository/UseThirdParty](https://wiki.debian.org/DebianRepository/UseThirdParty)
I wouldn't fret over this, been around since 2014, >>>[https://bugs.chromium.org/p/chromium/issues/detail?id=440870](https://bugs.chromium.org/p/chromium/issues/detail?id=440870)
I only heed anything outside of this:
```
# 2022/07/28 14:26:31 :  ok (last run)
# 2022/07/28 14:24:31 :  ok  (but init may masq some changes)
# congratulations : no problems detected
```

---

### Post by jacksonguitars on 2022-08-07
Thank you, sir.

---

