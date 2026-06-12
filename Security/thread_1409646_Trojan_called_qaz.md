---
title: "Trojan called qaz"
date: 2010-02-17
forum: Security
---

### Post by whshao on 2010-02-17
I am put in charge of cleaning out viruses and trojans at work, but have never ran into any case on any ubuntu before. However, while port scanning a computer running Kubuntu 8.04, I saw a port open called "qaz":

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2010-02-17 17:42 PST
Interesting ports on 10.44.225.133:
Not shown: 1708 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
80/tcp   open     http
139/tcp  open     netbios-ssn
445/tcp  open     microsoft-ds
7597/tcp filtered qaz
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.17 - 2.6.18
Uptime: 0.020 days (since Wed Feb 17 17:14:08 2010)
Network Distance: 2 hops

And after googling it, it occurs to be a trojan. However, the port seems to be already filtered out by the OS according to the above. Does this mean the system's safe? Or should I do anything else? I don't know exactly where to look for the trojan executables.

Thanks in advance,
Weber

---

### Post by adam814 on 2010-02-17
Running "lsof -i" and "netstat -tulpn" should show any processes on your system listening on a port.  I suppose it's possible a rootkit could hide the processes, but if it's an application you recognize and trust you'll know you're probably ok.

Probably the best thing to do if you can actually confirm you've been infected (and it's not a normal application listening on a weird port) is just to restore from backups and keep an eye on it for a while to make sure your backup isn't infected too.

Alternately you could just bite the bullet and re-format and re-install.

---

### Post by 2hot6ft2 on 2010-02-17
> Name: 	Qaz
Aliases: 	Worm.Qaz, W32.HLLW.Qaz, Notepad, W32/QAZ.worm, Note.com, Qazwsx, W95/Qaz,
Ports: 	139, 7597 (ports can not be changed)
Files: 	Qaz.zip - 40,548 bytes Qaz trojan notepad.exe - 120,320 bytes Notepad.exe - 120,320 bytes Qazwsx.hsq - Note.com - [53 kb] - 119,296 bytes - 120,297 bytes - 122,880 bytes
Created: 	July 2000
Requires: 	N/A
[B][COLOR="DarkRed"]Actions: 	Remote Access / Downloading trojan / Worm / Network trojan
	It mails the IP-address of the infected computer, probably to the sender. Loads every time the user launches Notepad as Qaz has take the original Notepad´s place. Spreads to all sharess on the network with Full Access privileges granted. 
[/COLOR][/B]
Figures it would probably work in wine since it replaces notepad.

[http://www.glocksoft.com/trojan_list/Qaz.htm](http://www.glocksoft.com/trojan_list/Qaz.htm)

[URL="http://www.pchell.com/virus/qaz.shtml"]Qaz Trojan Information and Removal
[/URL]

Looks like a reinstall to me too.

---

### Post by cdenley on 2010-02-18
> **whshao said:**
> 
Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2010-02-17 17:42 PST
Interesting ports on 10.44.225.133:
Not shown: 1708 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
80/tcp   open     http
139/tcp  open     netbios-ssn
445/tcp  open     microsoft-ds
7597/tcp **[COLOR="Red"]filtered[/COLOR]** qaz
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.17 - 2.6.18
Uptime: 0.020 days (since Wed Feb 17 17:14:08 2010)
Network Distance: 2 hops

filtered != open

---

### Post by adam814 on 2010-02-18
That just means you likely have a firewall blocking any incoming connections.  It can probably still send data out.

---

### Post by cdenley on 2010-02-18
> **adam814 said:**
> That just means you likely have a firewall blocking any incoming connections.  It can probably still send data out.

What is "it"? Traffic being rejected on port 7597 does not indicate the existence of anything. It should get rejected.

---

### Post by adam814 on 2010-02-18
Fair enough, blocked traffic on the port wouldn't mean anything special, what's weird is it shows up as filtered.  What firewall are you using?  Also, are you scanning against your external IP?  Sometimes ISPs will block ports known to be opened by trojans, so you might not even have one.

---

### Post by cdenley on 2010-02-18
> **adam814 said:**
> Fair enough, blocked traffic on the port wouldn't mean anything special, what's weird is it shows up as filtered.  What firewall are you using?  Also, are you scanning against your external IP?  Sometimes ISPs will block ports known to be opened by trojans, so you might not even have one.

Exactly. He is scanning the IP "10.44.225.133", which is reserved for private networks so it is not open to the internet. With an arbitrary network address like that, I would guess he is part of some big network, which may very well filter that port to minimize windows infections.

---

