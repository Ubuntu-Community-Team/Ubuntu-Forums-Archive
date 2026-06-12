---
title: "Do I need a server??"
date: 2007-09-22
forum: Server Platforms
---

### Post by aristotlewilde on 2007-09-22
Ok, I have been an Ubuntu user since Breezy, but am still a novice when it comes to IT type of stuff, so forgive me if thisi comes off as really stupid.  

Anyway, I was looking for a new case to build my next PC in, and I fell in love with the way Dell's Poweredge servers look.  I found one the other day at what I consider a reasonable price, so I picked up this Dual PIII 450mhz Poweredge 2300.  For good measure, I grabbed a Compaq Proliant ML350 (PIII 600mhz) as well, because I kind of liked the stormtrooper-ish look of it.  

Anyway, I was wondering, since I will have some extra server hardware sitting around, what uses I might have for it?  What uses would I have for a server at home?

I'm all for learning new stuff.

---

### Post by bukwirm on 2007-09-23
You might just want to play around with computer and learn some new things.

If so, the stuff discussed [here]("https://help.ubuntu.com/7.04/server/C/") might get you started.

---

### Post by PilotJLR on 2007-09-23
If you add hard disk capacity to it, it could work as a backup server, music server, etc.

---

### Post by aristotlewilde on 2007-09-23
Thanks folks.  I will just plug it in and go :)

I had already read that server guide.  It's over my head.

---

### Post by netlogic on 2007-09-23
my home server does many things for me.

1. dial-in server with my mobile phone when i can't get net access
2. media server
3. podcast catching server using bash shell and cron
4. ssh server that i can access all my documents from any client sites. it is on the net all the time, i apply following security procedures.
a) client docs are encrypted using truecrypt
b) i use a private and public key for ssh
c) i have a very good firewall ruleset
d) registered my name to many Dynamic DNS 
e) have few other instances of ssh server running in virtual machines on different ports in case the site is blocking it. the main machine is set to xyz port, but the striped down  VM (less 50megs) is running on a port such as 443, so I can bounce back in the internal network.
5. proxy server. in case, the site is blocking email sites
6. VPN server
7. Backup server

---

### Post by HermanAB on 2007-09-23
If you need to ask, then you don't need one...

---

### Post by aristotlewilde on 2007-09-24
> **HermanAB said:**
> If you need to ask, then you don't need one...


Best answer yet.  ALthough it is a little closed-minded.

---

### Post by Brazen on 2007-09-24
Start small and pick one little thing you want to do.  An easy and very usefull start would be to set up a home file server, just for sharing files between the computers in your house.  You can get fancy and provide various means of accessing your files from the internet, but let's just keep it simple since you are a beginner.

Use the LTS release of Ubuntu (Ubuntu Dapper) and start with this page: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/installing-samba.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/installing-samba.html)

Once you've mastered the information on that page, click the right-arrow at the bottom to go on to the next page.

---

### Post by dave_helmut on 2007-09-26
> **netlogic said:**
> my home server does many things for me.

1. dial-in server with my mobile phone when i can't get net access
2. media server
3. podcast catching server using bash shell and cron
4. ssh server that i can access all my documents from any client sites. it is on the net all the time, i apply following security procedures.
a) client docs are encrypted using truecrypt
b) i use a private and public key for ssh
c) i have a very good firewall ruleset
d) registered my name to many Dynamic DNS 
e) have few other instances of ssh server running in virtual machines on different ports in case the site is blocking it. the main machine is set to xyz port, but the striped down  VM (less 50megs) is running on a port such as 443, so I can bounce back in the internal network.
5. proxy server. in case, the site is blocking email sites
[COLOR="Red"]6. VPN server[/COLOR]
7. Backup server


According to the [Ubuntu Server Guide, ]("https://help.ubuntu.com/7.04/server/C/") VPN services was not mentioned.

I have a need to set up a freeware server (Ubuntu?) to behave as a MS VPN server would; in that a Windows XP VPN client can connect to my internal network.

Is there a way to set up Ubuntu as a VPN server that Windows XP clients can connect to using the default VPN client?

Thanks!

Dave

---

### Post by /etc/init.d/ on 2007-09-26
> **dave_helmut said:**
> Is there a way to set up Ubuntu as a VPN server that Windows XP clients can connect to using the default VPN client?

The built-in Windows VPN client uses L2TP, so you should be able to connect it to any Linux server running an L2TP VPN.  There is a package called l2tp (virtual package for l2tpd) that should provide you with a server.

I've never used it though, so I can't be of any help in configuring it.  There may be other L2TP-supporting VPN servers if that one isn't very good.

Edit:  Apparently the built-in Windows VPN client supports IPsec and PPTP as well. That's just about all of them, so any VPN server should technically work.

---

