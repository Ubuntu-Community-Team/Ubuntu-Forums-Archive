---
title: "Server not recieving mail"
date: 2008-12-05
forum: Server Platforms
---

### Post by t_ras on 2008-12-05
Ubuntu 8.10; KDE 3.5; Using Postfix configured by and for ISPconfig with my domain and IP behind router, but all comps with real IP

I have a mail server with the given configuration. I has no problems till recently, when suddenly I stopped receiving mail. 
When I try to send mail from my work the server tries to send several times and then claims for "connection timed out".
I tried telnet to port 25 and it worked fine and sent the mail, but unfortunately I only checked it from within my LAN. 
If it doesn't work from out side it might be my new router (Edimax), though I don't use NAT and the FW is disabled...
Any other ideas?

---

### Post by t_ras on 2008-12-05
OK, the problem is from out side the LAN. on the other hand (as you can see) I have no problem browsing the NET....

---

### Post by Wayne_V on 2008-12-05
You can test if port 25 is open using a portscanner site ([http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm)  for example).  If you just got a new router and you do not have a fixed IP it's possible your IP address changed as well.

---

### Post by t_ras on 2008-12-06
Thanks for the help. I'll keep that address. It seems my router was faulty and stacked on natting.

---

