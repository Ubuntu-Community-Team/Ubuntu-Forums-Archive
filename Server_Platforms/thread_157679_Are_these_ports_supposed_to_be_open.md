---
title: "Are these ports supposed to be open ?"
date: 2006-04-09
forum: Server Platforms
---

### Post by xXx 0wn3d xXx on 2006-04-09
I just want to make sure that I'm safe (not that anything would happen :neutral: )

---

### Post by Requiem on 2006-04-09
[QUOTE=MasterChief1234]I just want to make sure that I'm safe (not that anything would happen :neutral: )[/QUOTE]

I don't thinks so, go to menu System/Administration/Services and tick off apache or anithing labeled "web server" that should deactivate ports 80 and 443.

Then in System/Administration/Login Mannager (I'm not shure if it is called "login mannager" or something else) deactivate remote login for both root and normal usrs (unless you want to login remotely to this computer). That should put port 23 to sleep unless you are using a FTP, that's what port 23 is for AFAIK.

Port 5431 is a mystery, try to find anything suspicious in menu System/Administration/Services.

I think you may have to reboot in orther for the services to actually shutdown.

You could also shut them manually or maybe the services manager will do it for you (likely)

unfortunately a¿im away from my ubuntu machine right now.

---

### Post by trent dillman on 2006-04-10
what does ```
nmap -v -p1-65535 127.0.0.1
``` say?

---

### Post by Kresten Kjaer on 2006-04-10
I encourage you to stop telnet.
If you need to login remotely at least use ssh, and set the max_login_tries to 5 or less, to stop crackers bruteforcing you.

---

### Post by xXx 0wn3d xXx on 2006-04-10
[QUOTE=Kresten Kjaer]I encourage you to stop telnet.
If you need to login remotely at least use ssh, and set the max_login_tries to 5 or less, to stop crackers bruteforcing you.[/QUOTE]
I don't have telenet and I don't use ssh. I have no idea why these ports are open...how can I change the max login attemps ?

---

### Post by echo $USER on 2006-04-11
[QUOTE=MasterChief1234]I don't have telenet and I don't use ssh. I have no idea why these ports are open...how can I change the max login attemps ?[/QUOTE]
Open /etc/sshd/sshd.conf and edit the max_login_attempts entry.  Im not sure where the telnet config file is,  but it will be in /etc somewhere.

---

