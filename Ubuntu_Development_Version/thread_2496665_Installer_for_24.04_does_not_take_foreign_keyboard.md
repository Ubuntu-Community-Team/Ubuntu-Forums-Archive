---
title: "Installer for 24.04 does not take foreign keyboard choise into account during install"
date: 2024-04-07
forum: Ubuntu Development Version
---

### Post by michaelsidenius on 2024-04-07
Ubuntu 24.04 AMD64 Desktop install ISO, dated 2024-04-07 09:19.
During install, when you choose a foreign keyboard, it will not be taken this into account when setting up the first admin account (for hostname, name and password entering).

---

### Post by #&amp;thj^% on 2024-04-07
This belongs in Ubuntu Development Version.....as it is still in Development ATM
22.04 is the current stable LTS

---

### Post by ajgreeny on 2024-04-07
Moved to **Ubuntu Development Version**.

I did not see this problem last night, about 10 hours ago when installing the new ISO of Xubuntu.
Which version of Noble did you use?

---

### Post by Yahoé on 2024-04-08
I have experienced this issue under flavours, Ubuntu Unity and Ubuntu Mate.

---

### Post by Claus7 on 2024-04-08
Hello,

does this sound relevant?
[https://ubuntuforums.org/showthread.php?t=2486629](https://ubuntuforums.org/showthread.php?t=2486629)

it is not possible to use a non latin keyboard unless you write your username, which is acceptable if non latin characters are entered. The rest, e.g. password, should be provided with a latin keyboard in order to get recognized. The thing is that if you choose your local non latin keyboard, you do not have at the same time an english one available to switch to when is needed.

Regards!

---

### Post by corradoventu on 2024-04-09
May be this problem? [https://bugs.launchpad.net/subiquity/+bug/2060387](https://bugs.launchpad.net/subiquity/+bug/2060387)

---

