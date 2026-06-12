---
title: "help regarding squirrelmail"
date: 2009-07-28
forum: Server Platforms
---

### Post by pawan_lal on 2009-07-28
hello friends,
i had configured postfix on **Ubuntu 8.04 lts**, my server is running smooth n i am able to receive n send emails properly from my postfix. i had installed Squirrelmail on Ubuntu n i did port forwarding in my router port 80. now when i am accessing squirrelmail locally on lan its opening but when i am opening squirrelmail from web than i am getting error,

**You are not authorized to view this page**

 The Web server you are attempting to reach has a list of IP addresses that are not allowed to access the Web site, and the IP address of your browsing computer is on this list. [B]HTTP Error 403.6 - Forbidden: IP address of the client 	has been rejected.
Internet Information Services (IIS)[/B]


plz  guide  me  so  that  i  can  access squirrelmail  from outside also

thx

---

### Post by grantemsley on 2009-07-28
The error message is from IIS - Microsoft's web server.

So it isn't getting to your computer at all.  Perhaps you are using the wrong IP address?

---

### Post by hessiess on 2009-07-28
Your ISP may be proxying/blocking port 80, in which case you cannot do anything besides run on a different port.

---

### Post by a9k3d on 2009-07-28
There could also be another router between you and your external IP address (ext-ip).
try **mtr -rc 1 ext-ip** it will return one line per router. If there is more than line you have more works ahead. Probably a tunnel to a friends box that isn't behind two routers.

---

