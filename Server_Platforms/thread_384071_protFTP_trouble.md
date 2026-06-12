---
title: "protFTP trouble"
date: 2007-03-14
forum: Server Platforms
---

### Post by rangerxlt8 on 2007-03-14
HEllo everyone I am new to Linux and these boards.....OK I followed this [http://ubuntuguide.org/wiki/Ubuntu_Edgy#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#FTP_Server)  guide, nd excellent guide BTW on setting up the FTP.  Proftp is installed and the .conf file edited.

When I type: sudo /etc/init.d/proftpd start
This is what is spit back at me:
* Starting ftp server proftpd                                                               
- IPv6 getaddrinfo 'bohdan-ubuntu' error: Name or service not known

**FYI bohdan-ubuntu is the login name I use for Linux..

I have no idea what this means.....

TIA

---

### Post by scxtt on 2007-03-14
try adding your hostname to the end of the line "::1 ip6-localhost ip6-loopback" in /etc/hosts ...

```
[font=courier]# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback [color=green]**bohdan-ubuntu**[/color]
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/font]
```then stop/start proftpd ...

---

### Post by rangerxlt8 on 2007-03-14
> **scxtt said:**
> try adding your hostname to the end of the line "::1 ip6-localhost ip6-loopback" in /etc/hosts ...

```
[font=courier]# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback [color=green]**bohdan-ubuntu**[/color]
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/font]
```then stop/start proftpd ...
EDIT: I found the file, now editing..

---

### Post by scxtt on 2007-03-14
i use:

**sudo vi /etc/hosts**
type **i** to insert text, arrow keys should move you around to where you want to edit ...
then type **:wq** to save

---

### Post by rangerxlt8 on 2007-03-14
Ok it worked....TY....

Now I need to tinker to see if I can log in...I'm sure I will run into some issues//

, how do I log into the FTP?  This might be a broad question So I will tinker a bit.  And for now the server is running...

EDIT: Apache2 is also installed, but I do not know what step to take now...  When I go to the apache page shows...

---

### Post by scxtt on 2007-03-14
just so long as port 21 points to the host proftpd is running on, you should be fine ... by default, i think proftpd will allow anyone to connect that has a valid account on the server, you can change that of course by editing the config file ...

for apache2, the "home" folder is /var/www ... so you'd want to start putting files in there ...

---

### Post by rangerxlt8 on 2007-03-14
Ok proftp port is configured as 1080..  If the domain name is rangerxlt8.homelinux.com, what address do I use in the FTP browser, if: DefaultRoot /home/FTP-shared
.

When I try to connect to , nothing happens...The browser spits back that the connection is bad...

Do I have to configure anything in Apache2 so it works with proftp?

---

### Post by scxtt on 2007-03-15
what are the contents of your **/etc/proftpd/proftpd.conf** file?

if you're using a GUI ftp client, it generally separates the hostname from the port - at any rate it'd be rangerxlt8.homelinux.com:1080 (it's a colon, not a slash) ... then you specify a directory ...

---

### Post by rangerxlt8 on 2007-03-15
Thanks buddy for helping me.  Turns out my buddy configured my router to send the FTP to the wrong static IP... I have to reinstall proftp and configure again...

---

### Post by scxtt on 2007-03-15
why would you have to reinstall proftpd?

---

### Post by rangerxlt8 on 2007-03-15
> **scxtt said:**
> why would you have to reinstall proftpd?

Lol in a fit of rage against the machine I sudo removed proftpd and then reinstalled ubuntu<----such a linux noob lol!  The entire time the router was configured badd, but now I understand ithe IP configuration and whatnot..

Anyway the server is up and running, transferring about 8.5GB of .mp3 from my Windows XP box for safe keeping...  

Scxtt thanks a bunch for helping me, as Linux was greek to me a few days ago, and still is, but I think I have teh basics..  The Folder permissions were a PITA to set but in the end they are all configured correctly.

Oh and one more thing, what are commands for moving files\directories around the file system?

---

### Post by scxtt on 2007-03-15
i've been there ;) ... but back in my Red Hat and Fedora days ... those are the things that really teach you tho, so it's all good :)

---

### Post by rangerxlt8 on 2007-03-20
From log files, it looks like someone tried logging in with username Administrator\Admin a few thousand times...... This someone was trying to gain access by running a password bot?

---

### Post by scxtt on 2007-03-20
probably ... i get lots of hits on "common" ports (i forward from my router) - mostly for 22 (ssh) ... +1 for firewalls :) ... but as long as that's not your username + password, you're fine ... besides, looks like something expecting windows anyway ;)

---

### Post by rangerxlt8 on 2007-03-20
> **scxtt said:**
> probably ... i get lots of hits on "common" ports (i forward from my router) - mostly for 22 (ssh) ... +1 for firewalls :) ... but as long as that's not your username + password, you're fine ... besides, looks like something expecting windows anyway ;)

HA suckers!  What kind of strain does this put on a system?  The login attempts were multiple times per second... The server is a Dual Core Pentium D overclocked, 1gb of ram...

---

### Post by scxtt on 2007-03-20
can't be much @ all ... i'd imagine it could lighten the load if you have a firewall even denying them the chance to try ...

---

### Post by rangerxlt8 on 2007-03-20
> **scxtt said:**
> can't be much @ all ... i'd imagine it could lighten the load if you have a firewall even denying them the chance to try ...

When you say firewall, does a LinkSys router count as a firewall?

---

### Post by scxtt on 2007-03-20
for the most part ... if you don't forward a port - a "hit" on your modem for that port will go no where ... so if a "bot" is trying to login via ssh (port 22) and your router doesn't forward port 22 anywhere (to a PC running an ssh server that's "listening") - nothing happens ...

but since i do use SSH and i do forward port 22 - i use a software firewall (iptables w/ a kmyfirewall frontend) to BLOCK any IPs that i haven't explicitly allowed ...

so if those requests that you have were to hit me - i'd allow them through my router, but when they hit my firewall they'd be blocked entirely (w/ no chance to make a login attempt) then an entry is added to /var/log/messages as part of kmyfirewall ...

---

### Post by rangerxlt8 on 2007-03-20
5800 tries today.  I have to do something. I am using gproftpd, is there any kind of security I can integrate that will block these attempts from even getting to login tries?  I don't know much about SSL and SSH...

I am using port 21 and I realize that is a very common port...  Any ideas?

---

### Post by Mr. C. on 2007-03-20
> **rangerxlt8 said:**
> 5800 tries today.  I have to do something.

What is it you feel you need to do?  If you have a port open, it will get discovered, and the attempts to exploit weaknesses will be endless.  You can go through all sorts of hoops to try to block failed attempts, but in the end, they get blocked one way or another.

Have strong passwords, be sure to keep your system updated on security patches, and move on.

MrC

---

### Post by rangerxlt8 on 2007-03-20
> **Mr. C. said:**
> What is it you feel you need to do?  If you have a port open, it will get discovered, and the attempts to exploit weaknesses will be endless.  You can go through all sorts of hoops to try to block failed attempts, but in the end, they get blocked one way or another.

Have strong passwords, be sure to keep your system updated on security patches, and move on.

MrC
Strike DEATH apon he who tries to invade my PC nah lol, I suppose there is not much I can do..

---

### Post by Mr. C. on 2007-03-20
Exactly.  Not much you can do.  Its like a block party...tough to keep out the freeloaders from the next neighborhood.

MrC

---

### Post by scxtt on 2007-03-21
> **rangerxlt8 said:**
> 5800 tries today.  I have to do something. I am using gproftpd, is there any kind of security I can integrate that will block these attempts from even getting to login tries?  I don't know much about SSL and SSH...

I am using port 21 and I realize that is a very common port...  Any ideas?what are you using FTP for?  well, i guess that's obvious, but what i'm asking is - do you have a specific set of users that are allowed to connect?  like i said, for the most part i just allow my work IP to connect to my box, using a firewall - and also like i said, any IP that's NOT my work IP is rejected automatically w/ NO CHANCE to login ...

so can you narrow down who is even allowed to connect and then block anyone else out w/ a firewall?  and remember, you can always change the firewall to suit new IPs ...

---

### Post by rangerxlt8 on 2007-03-21
The FTP is accessed by friends who have accounts, but they do not have static IPs, so limiting to certain FTP is out of the question..  I guess I'm content that the system is secure,,

---

### Post by scxtt on 2007-03-21
do you mean they will access it from various places (at home, at work, at an internet cafe, etc.) or their ISP changes their IP randomly?

---

### Post by Mr. C. on 2007-03-21
> **rangerxlt8 said:**
> The FTP is accessed by friends who have accounts, but they do not have static IPs, so limiting to certain FTP is out of the question..  I guess I'm content that the system is secure,,

You'll find that even with dynamic IPs, they will be within a network block of IPs for that provider.  Allowing access to the ranges your friends will use will cut out 99% of the net and block those unwanted intruders.

If you aren't sure how to do this, have your friend(s) connect to FTP.  When they do, take note of their IPs via **netstat**.  Once you have the IPs, you can use

```
whois *IP*
```

to get the range of IPs typically used for that provider.  Then, open FTP for that range or set of ranges.

MrC

---

### Post by rangerxlt8 on 2007-03-21
Well they access it from home\school and myself as well.  I will tinker around a bit....

---

