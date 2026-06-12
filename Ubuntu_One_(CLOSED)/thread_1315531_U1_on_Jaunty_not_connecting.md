---
title: "U1 on Jaunty not connecting"
date: 2009-11-05
forum: Ubuntu One (CLOSED)
---

### Post by RavanH on 2009-11-05
Since a few days, Ubuntu One client on my Jaunty 64bit install does not connect anymore. No errors or anything, just nothing... On another system with Karmic 32bit, it works just fine!

I filed a bug report on [https://bugs.launchpad.net/ubuntuone-client/+bug/475470](https://bugs.launchpad.net/ubuntuone-client/+bug/475470)

Anyone have similar experience?

UPDATE: well, that bugreport just got marked as duplicate of [https://bugs.launchpad.net/ubuntuone-client/+bug/357395](https://bugs.launchpad.net/ubuntuone-client/+bug/357395) where it says U1 needs Network Manager to function... Hmmm, that sucks :( ! I use Wicd and need it because of my RT2500 wireless card.

---

### Post by andrea000 on 2009-11-05
Just read on another post it's a bug in
python and it should be fixed now i run
karmic and it's been running since 9.10
came out.

---

### Post by RavanH on 2009-11-08
hi andrea,

apparently, it is related to the fact that i am not using network manager to connect (but wicd instead) and somehow U1 has some kind of dependency on it... even though NM is not required when installing U1.

hope it will be fixed one day because U1 is now unusable for me :(

---

