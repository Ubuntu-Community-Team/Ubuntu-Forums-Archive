---
title: "Is it possible to hack Ubuntu, with no active services?"
date: 2005-08-01
forum: Server Platforms
---

### Post by ekravche on 2005-08-01
Hello,

Short rant: 

After having Win XP hacked for the 10th time, I've decided to give linux a try. I heard that ubuntu distribution was easy to install and use. One of the problems that I had with XP is that it exposes to many services to the outside world. And even behind a well configured firewall these services can be exploited with all the xp service packs applied. 

Ubuntu questions: 

I'm curious to know whether I can disable some default services that expose end points to the outside world in Ubuntu? I'm also curious if anyone can point me to sources that explain how to do that?

Another question that I have is whether Ubuntu supports a security model where I can configure application access? For instance I would like to run DC++, which is an open source file sharing application, and I would like to restrict DC++ to only write and read data from a certain directory, and its subdirectories, on the disk drive

Thank you in advance.

---

### Post by adwait on 2005-08-01
For the first question:
Use
```
 sudo rcconf 
```

For the second question:
There is an option to do this from the program itself, in most file sharing programs. If not......create a user with read/write permission only to the directories you want. Then run DC++ as that user using 
```
 sudo -u <username> dc++ 
```

---

### Post by ekravche on 2005-08-01
great! I've done the second part. That is I've created a user with limited permissions, who I will use to run my DC++ client. Which services would you recommend to deactivate so that my system will be secure? Also are there any open source anti-virus solutions for ubuntu?

Thanx in advance.

---

### Post by adwait on 2005-08-01
To the best of my knowledge, you don't need an antivirus on Linux, because there are hardly 6-7 viruses for Linux. And those too, are just experimental ones, which never got out of the Lab.

Umm, I guess you could turn off the ssh and ftp services if you dont need them. But, it doesn't make your system any less secure if they are on.....just that turning them off, will produce a faster performance.

---

### Post by word_virus on 2005-08-01
[QUOTE=ekravche] Which services would you recommend to deactivate so that my system will be secure? Also are there any open source anti-virus solutions for ubuntu?

Thanx in advance.[/QUOTE]

Ubuntu installs with no world-facing services enabled by default.  Nothing to deactivate.

If you need an anti-virus program I recommend ClamAV -- mostly for virus scanning NTFS (Windows) partitions

---

### Post by craigevil on 2005-08-01
Bastille is a good place to start when it comes to hardening your system.

Along with a firewall.

["Securing Debian Manual"](http://www.debian.org/doc/user-manuals#securing) is a good thing to read.

---

### Post by ekravche on 2005-08-01
When I run netstat the following services seem to be running by default

Protocol	IP Source	Port/Service	State
tcp	127.0.0.1	631	LISTEN
tcp	127.0.0.1	25	LISTEN
tcp6	::1	25	LISTEN
udp	0.0.0.0	68	

Any ideas why I need those services to be present?

---

### Post by word_virus on 2005-08-01
[QUOTE=ekravche]When I run netstat the following services seem to be running by default

Protocol	IP Source	Port/Service	State
tcp	127.0.0.1	631	LISTEN
tcp	127.0.0.1	25	LISTEN
tcp6	::1	25	LISTEN
udp	0.0.0.0	68	

Any ideas why I need those services to be present?[/QUOTE]

631 is the Cups daemon, 25 is the postfix daemon, they provide some needed system functionality (point a browser at localhost:631 for the "cups way" to configure your printer, and some programs leave you important email messages after you install them, so you need a MTA (mail transfer agent) to get those messages some place you can read them later) they are configured to only listen to localhost.

IANA lists udp/68 as the bootstrap protocol client.  Not open on my box, so not sure exactly what it does.  If you're feeling paranoid about it I recommend "Firestarter", it's an excellent graphical firewall program.

---

### Post by ekravche on 2005-08-02
[QUOTE=adwait]For the first question:
Use
```
 sudo rcconf 
```
[/QUOTE]

I've tried running sudo rcconf, but it came back with an error saying command not recognized. I'm using bash as my shell btw.

What really bothers me is this service. I want to disable it.

Protocol	IP Source	Port/Service	State
udp	0.0.0.0	68

---

### Post by ekravche on 2005-08-05
[QUOTE=adwait]For the first question:
Use
```
 sudo rcconf 
```
[/QUOTE]

I've tried running sudo rcconf, but it came back with an error saying command not recognized. I'm using bash as my shell btw.

What really bothers me is this service. I want to disable it.

Protocol	IP Source	Port/Service	State
udp	0.0.0.0	68

---

### Post by heimo on 2005-08-05
[QUOTE=ekravche]I've tried running sudo rcconf, but it came back with an error saying command not recognized. I'm using bash as my shell btw.

What really bothers me is this service. I want to disable it.

Protocol    IP Source    Port/Service    State
udp    0.0.0.0    68[/QUOTE]

DHCP client, which is used to configure network settings automaticly (from DHCP server). rcconf said "unrecognized" because it's not installed by default.

See this thread:
[http://www.ubuntuforums.org/showthread.php?t=54298](http://www.ubuntuforums.org/showthread.php?t=54298)

[http://packages.ubuntu.com/hoary/admin/rcconf](http://packages.ubuntu.com/hoary/admin/rcconf)
[https://wiki.ubuntu.com/UniversePackages](https://wiki.ubuntu.com/UniversePackages)

---

### Post by ekravche on 2005-08-07
I was able to disable the DHCP service running on 

udp 0.0.0.0 68

All I've done was disable DHCP and enter the ip, dns, mask, and other info manually.

---

### Post by ekravche on 2005-08-07
How do I disable these services?

Protocol	IP Source	Port/Service	State
tcp	127.0.0.1	631	LISTEN
tcp	127.0.0.1	25	LISTEN
tcp6	::1	25	LISTEN

Thank you in advance.

---

### Post by Yagisan on 2005-08-07
[QUOTE=ekravche]How do I disable these services?

Protocol	IP Source	Port/Service	State
tcp	127.0.0.1	631	LISTEN
tcp	127.0.0.1	25	LISTEN
tcp6	::1	25	LISTEN

Thank you in advance.[/QUOTE]
You do know that tcp address 127.0.0.1 is the localhost ?, it can not be accessed by any other machine. tcp6 ::1 is the ip6 version of the localhost address. It also can not be accessed by any other machine. To close port 631, uninstall cups (you then lose the ablity to print.) To close port 25 uninstall postfix (you will then break your ubuntu, ALL Linux, BSD and Solaris systems need a localhost mail delivery service for system messages, you are LESS secure if you disable it.)

As a security professional, I think is great that you have an interest in securing your machine, but, please don't go blindly turning off something that "might" have a security issue. This isn't Windows, nothing in a default desktop install listens by default on an external IP address. If it is running on 127.0.0.1 it is because it is needed on the local machine.

And before I go, Welcome to Ubuntu.

Yagisan

---

### Post by NewbieLearnLinux on 2006-09-15
> **ekravche said:**
> I've tried running sudo rcconf, but it came back with an error saying command not recognized. I'm using bash as my shell btw.


Me, too. 

Any help ?

---

### Post by snoogie on 2007-02-20
> **NewbieLearnLinux said:**
> Me, too. 

Any help ?

sudo apt-get install rcconf

to install rcconf

---

### Post by ekravche on 2007-07-26
I'm just wondering if someone can check whether my machine is secure. Here is my ip x.x.x.x I'm beginning to suspect that I was hacked, but I can't confirm it. Could someone please confirm it?

Thank you in advance.

---

### Post by heimo on 2007-07-26
> **ekravche said:**
> I'm just wondering if someone can check whether my machine is secure. Here is my ip xx.xx.xx.xxx I'm beginning to suspect that I was hacked, but I can't confirm it. Could someone please confirm it?

Thank you in advance.

How do you suspect that your computer got hacked? Based on an IP address it's pretty much not possible to tell if a computer has been broken into (unless it's really obvious, at least one can't tell that the computer has NOT been hacked). And no one should take an IP address from forum and "search" (like port scan or anything) it. If you suspect you got hacked, there is just one way to recover. Do not use that computer, do not trust it to anything. If neccessary, file it to your local authorities (probably in most countries it's a crime to "hack" into someones computer) and follow their advice. If you are not going to do that, make a backup of your personal files using known clean copy of operating system (like a Live CD), format the whole computer and reinstall.

---

### Post by lisati on 2007-07-26
Be careful about putting your IP address on any forum if you're worried about people breaking into it. While the majority of the people who regularly visit this forum are probably ok, you don't want to tempt the scoundrels out there......

---

### Post by ekravche on 2007-07-26
> **heimo said:**
> How do you suspect that your computer got hacked? Based on an IP address it's pretty much not possible to tell if a computer has been broken into (unless it's really obvious, at least one can't tell that the computer has NOT been hacked). And no one should take an IP address from forum and "search" (like port scan or anything) it. If you suspect you got hacked, there is just one way to recover. Do not use that computer, do not trust it to anything. If neccessary, file it to your local authorities (probably in most countries it's a crime to "hack" into someones computer) and follow their advice. If you are not going to do that, make a backup of your personal files using known clean copy of operating system (like a Live CD), format the whole computer and reinstall.

Thanx for the advise. I'll do a port scan and see if it finds anything

---

### Post by meatpan on 2007-07-26
> **ekravche said:**
> I'm just wondering if someone can check whether my machine is secure.

Consider learning how to check if your own machine is safe.  Here are two relatively painless tasks you can do:

o Make sure you have the latest ubuntu security updates
o Install and run a program, such as nessus.  Nessus is a remote security scanner that can check for hundreds of known security exploits.   The program is common, and exists in the ubuntu repositories.  If you need to know more, search for one of the many nessus how-to's available in these forums.

Good luck.

---

### Post by az on 2007-07-26
Why do you think you have been cracked?

---

### Post by Modernity on 2007-07-26
Don't forget to check your logs. they can be your best friend if you think you have been attacked (better terminology for being hacked). if you think someone is trying to log into your SSH by port scanning and the such, please check your auth.log. This will tell you if someone is trying to try to break in. Check the other logs i.e. Samba, Apache and etc. to see what else is going on, in reference to the services you have running.

---

### Post by ekravche on 2007-08-11
Just wondering if it's possible to hack Ubuntu with no active services such as ssh running, behind a hardware firewall? The only thing that's running is a firefox browser and even that is running in a limited privs user account.

Thank you in advance

---

### Post by koenn on 2007-08-11
> **ekravche said:**
> Just wondering if it's possible to hack Ubuntu with no active services such as ssh running, behind a hardware firewall? The only thing that's running is a firefox browser and even that is running in a limited privs user account.

Thank you in advance
your question has been asked and answered in this same thread. I suggest you read it.

---

