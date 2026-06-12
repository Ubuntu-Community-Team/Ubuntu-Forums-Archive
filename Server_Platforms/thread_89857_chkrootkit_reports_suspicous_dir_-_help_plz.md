---
title: "chkrootkit reports suspicous dir - help plz"
date: 2005-11-13
forum: Server Platforms
---

### Post by jamesford on 2005-11-13
i have no idea about rootkits and i suspect this is probably nothing but a confirmation would be nice.

chkrootkit reports:
Searching for suspicious files and dirs, it may take a while...
/lib/modules/2.6.12-9-k7/volatile/.mounted

i also notice when i type 'mount', it says:
tmpfs on /lib/modules/2.6.12-9-k7/volatile type tmpfs (rw,mode=0755)

is this anything to worry about ?

thank you :)

---

### Post by Kyral on 2005-11-14
Its clear I think. If you ls it you will see things like the NVidia Driver. I have it on my system as well

---

### Post by jamesford on 2005-11-14
thanks, yeah ive found out it must be the ATI drivers

---

