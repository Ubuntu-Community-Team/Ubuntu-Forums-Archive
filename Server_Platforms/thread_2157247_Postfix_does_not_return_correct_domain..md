---
title: "Postfix does not return correct domain."
date: 2013-06-24
forum: Server Platforms
---

### Post by Bob Fletcher on 2013-06-24
I am trying to set up postfix and I have reached a point of testing it. I have given it the domain "mail.merciadragon.net". From the examples of telnet testing this is the domain that it should return both on the initial connection and when I issue an "HELO" but what it return's is the machine name "LittleDragon.merciadradon.net". The file in "/etc/mailname" is "mail.merciadragon.net".
So where in the config is it getting this name from and how can I rectify the issue as I am sure this will cause some problem with clients trying to connect.

Any help greatly appreciated

Robert…
Ubuntu server 13.04

---

### Post by priyans on 2013-06-25
Try this : 
 
Edit main.cf and give below values:

myhostname =   [COLOR=#000000]mail.merciadragon.net
[/COLOR]mydomain = [COLOR=#000000]mail.merciadragon.net[/COLOR] 

and comment out the present value assignments for the above parameters.

Then run ->  postfix stop ; postfix start

---

### Post by Bob Fletcher on 2013-06-28
Sorry for the delay, high have been down for several days as I had a number of issues but thank you for dressing this one for me.

Robert

---

