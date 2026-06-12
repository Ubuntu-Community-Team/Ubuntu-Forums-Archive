---
title: "hdd temp , which one ?"
date: 2010-10-03
forum: Server Platforms
---

### Post by pablosanchezuy on 2010-10-03
hi there

i'm having a situation here with the title above.

1. Linux xxxxxxx 2.6.32-24-server #43-Ubuntu SMP Thu Sep 16 16:05:42 UTC 2010 x86_64 GNU/Linux

aka lucid/amd64/server edition

2. smartmontools logs :
smartd[1015]: Device: /dev/sdb, SMART Usage Attribute: 194 Temperature_Celsius changed from 68 to 67

3. hddtemp shows :
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
|/dev/sda|SAMSUNG HD753LJ|38|C||/dev/sdb|SAMSUNG HD753LJ|35|C|Connection closed by foreign host.

4. md1 is failing on /dev/sda
smartd[1015]: Device: /dev/sda, 1 Currently unreadable (pending) sectors

i guess i should count on 2 not 3 , right ?
server is on a remote (reachable) location, so i'm going on monday

regards

pablo

---

### Post by P4man on 2010-10-03
Not quite sure, but is it possible smartmontools is giving a highest temperature recorded? I know its a smart feature, I have one or two drives with a red flag next to that attribute, interpreted as "failed in the past" (which is accurate, in my previous case there was no HD cooling and they did get smoking hot).

hddtemp will show the current temperatures.

---

### Post by pablosanchezuy on 2010-10-03
thanks

eating "man smartd" now....

---

