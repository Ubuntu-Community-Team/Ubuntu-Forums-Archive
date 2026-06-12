---
title: "virtual machine to run Windows program"
date: 2017-02-09
forum: Virtualisation
---

### Post by pradtf2 on 2017-02-09
we have a ubuntu 16.04 server which
- serves as gateway
- runs our websites

we want to run a 32bit Windows program (metatrader4) so we can rdp into it.

options i think we have:

1. install X and wine on the server and manually run mt4 (don't know if rdp is possible)
2. install wine and try to run mt4 (don't think this can be done since we don't have X)
3. create a virtual machine and put Windows on with mt4, then rdp into it (like a typical vps)
4. create a virtual machine with ubuntu (presumably the desktop) and wine mt4, then rdp into it (like a typical vps)

#4 is my preferred option since mt4 wines very nicely.

i imagine than #3 or #4 are better options than the first two?

i would appreciate confirmation of the last statement before proceeding to implement a virtual machine.
we would use ubuntu's kvm system as opposed to virtualbox or openvz.

in friendship,
prad

---

### Post by Habitual on 2017-02-09
Gold rating, I guess is pretty "good".
[https://appdb.winehq.org/objectManager.php?sClass=version&iId=2893](https://appdb.winehq.org/objectManager.php?sClass=version&iId=2893)

So, looks like wine may just do it.

---

