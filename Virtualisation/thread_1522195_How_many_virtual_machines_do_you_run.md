---
title: "How many virtual machines do you run?"
date: 2010-07-01
forum: Virtualisation
---

### Post by tmette on 2010-07-01
Just got done setting up my new Ubuntu desktop with Virtual Box installed.  Installing Linux Mint as a virtual machine right now.  Just curious how many of you out there use your virtual machines and which/how many you all have.  I'm sure I'll start a Windows XP virtual machine soon since doing web development I'll want to test sites in IE.

---

### Post by flick on 2010-07-01
I use VirtualBox occasionally, to test distros. Window shopping, really. :P

---

### Post by robots.jpg on 2010-07-02
There are usually 5-7 running at a time here.  We have VMware server (running on Ubuntu Server) hosting a fax server, a file server, a Windows terminal server, a copy of an ancient SCO UNIX server, and a test machine.

Then on my desktop, I have a few different distributions of Ubuntu Desktop/Server and Windows under VirtualBox for testing various things.  It sure beats having a bank of old PCs running next to me.

---

### Post by stlsaint on 2010-07-02
Really it will come down to home ram/hdd space you have. The more storage space the more vm's you can run. Also a good processor of course will help. IE: a quad core can support more than a duo core!

---

### Post by celldweller1591 on 2010-07-03
I run 2 VMs in KVM (XP pro and edubuntu), 5 in VMware payer  (opensolaris, opensuse 11.2, ubuntu studio 10.04, ubuntu netbook remix  10.04 and windows 7 pro) and 1 (Xubuntu)in Vbox... 
Quite a virtual Ubuntu i have :). But my specs make me run only 2 VMs at  a time !!

---

### Post by TheFu on 2010-07-03
I have 4 physical systems and each is able to run some kind of virtual machines. 2 of them are "production systems" and run multiple VMs 24/7/365 providing services for a few companies. They are all C2D or better and most have 8GB of RAM.

The count appears to be 13 today. 9 are running right now. I'm not counting any non-running test VMs for TinyCore, eBox, Asterisk, or other specific testing.


[LIST=1]
[*]P-1 - Xen/Ubuntu 8.04
[/LIST]

[LIST]
[*]Zimbra - email, IM, ldap, comm VM
[*]vTiger - CRM VM
[*]Typo - RoR Blog VM
[*]Alfresco/Wiki/Project/BZR VM
[*]Monitoring/Alarming VM
[*]PKI VPN VM backup VM
[/LIST]

[LIST=1]
[*]P-2 - ESXi 4.x
[/LIST]

[LIST]
[*]Win7 Pro - Accounting apps
[*]Ubuntu 8.04 - VPN prod VM
[*]OpenSolaris - test VM
[/LIST]

[LIST=1]
[*]P-3 - Lubuntu 10.04 KVM/VirtualBox OSE (backup server for all VMs)
[/LIST]

[LIST]
[*]xubuntu 10.04 VM - testing performance solutions - er - it sucks.
[*]WinXP VM - MS-Office, Quicken, VMware Management, Visio, Video Editing
[/LIST]

[LIST=1]
[*]P-4 - Win7 Ult - media center - VirtualBox
[/LIST]

[LIST]
[*]WinXP Pro VM - work MS-Office - barely used
[*]xUbuntu 8.04 desktop
[/LIST]
P-3 and P-4 run VMs "on-demand" for a specific purpose, not 24/7. Sadly, P-3 virtualbox VMs loses performance a few hours after starting and cause the P-3 host system to lock up completely after about 4-6 days of constant running (just on, not heavy use).  KVM tests had such poor performance on that machine that it only lasted 10 days before being removed. There were other minor issues with KVM that simply were unacceptable for use too.

Xen performance has been rock solid for almost 2 yrs, but we use paravirtual client OS installs, not HVM. Only Linux systems work there.  ESXi installs are HVM, rock solid and perform well, but management of the system sucks since only MS-Windows can be used for that (vSphere client is Windows-only). Backup tools are $900+ and usually MS-Windows based, which also sucks. If they had non-MS-Windows tools, I would have switched to ESXi YEARS ago.

---

### Post by JohnYYC on 2010-07-08
I have one host machine that I use for testing:

Ubuntu 9.10 64bit
AMD Phenom II X4 925 Processor
8GB DDR3 RAM
300GB 10K RPM - Virtualbox guests
1TB 7200 RPM -Backups

I have 12 virtual machines and 6 are running at any given time. Most of them are Ubuntu Server's, I have a few XP/Vista/Server 2003. Then I have a large number of production hosts that have anywhere from 6 to 24 guests running on each at any given time.

---

### Post by sh1ny on 2010-07-08
I've always figured a picture is worth a thousand words, so here goes ( i've just saved you reading 9981 words ) :

[IMG]http://farm5.static.flickr.com/4093/4774369403_9cfd63a6ba_b.jpg[/IMG]


P.S. There are more, but i can't access them from home :/ I think the total count is below 50.

---

### Post by naelq on 2010-07-08
@ **sh1ny**, RAM? :D

---

### Post by slooksterpsv on 2010-07-09
@sh1ny - I'm jealous. Is that KVM? Do you really get good performance for your guests? If so when I used KVM I got bad performance. I get better with VirtualBox, but to each their own.

---

### Post by sh1ny on 2010-07-09
> **naelq said:**
> @ **sh1ny**, RAM? :D

The hardware is ranging, but it's mostly :

Intel(R) Xeon(R) CPU E5520  @ 2.27GHz ( either 1 or 2 of those, the host with the color wings named guests is with 2 cpu's )
Between 8 and 24GB RAM on each ( the host with lilja/kashmir has 8G :F )
Usually we use mdadm for raid but i'm starting to like hwraids more and more... just not the cheap ones. LSI preferred. And i recently switched from raid5 to raid6 due to.....let's say bad luck, shall we ? :)

> **slooksterpsv said:**
> @sh1ny - I'm jealous. Is that KVM? Do you really get good performance for your guests? If so when I used KVM I got bad performance. I get better with VirtualBox, but to each their own.

Yeh, it's all kvm. I use virtualbox for a desktop VM or two, but that's all. The performance is good, as long as you're not depending too much on disk I/O. We have a few samba servers running as guests and it ain't something i'm proud of :D Other than that, the performance with KVM is great.

---

### Post by TheFu on 2010-07-10
> **slooksterpsv said:**
> @sh1ny - I'm jealous. Is that KVM? Do you really get good performance for your guests? If so when I used KVM I got bad performance. I get better with VirtualBox, but to each their own.

It looks like he has 10 Linux-based VMs under a single host. Doing that really isn't too difficult provided most are low IO clients **OR** enough disk IO and GigE networking is on the host system AND enough RAM.  8GB is probably enough RAM for low RAM requirement systems. At that point, it becomes a tuning exercise.

---

### Post by naelq on 2010-07-10
any others with production usage? or it is ESXi for production?

---

### Post by sh1ny on 2010-07-10
> **TheFu said:**
> It looks like he has 10 Linux-based VMs under a single host. Doing that really isn't too difficult provided most are low IO clients **OR** enough disk IO and GigE networking is on the host system AND enough RAM.  8GB is probably enough RAM for low RAM requirement systems. At that point, it becomes a tuning exercise.


Well the host with the colorwing vm's has 12G RAM and 2x Xeon 5520, and guests are as follows :

bluewing - 4096 RAM/4 Cores - Web Hosting, Emails/FTP/DNS, Mysql
dev - 1024 RAM/2 Cores - Bzr, Some ruby and php apps, mysql
purplewing - 2048 RAM/2 Cores - Mysql and Postgresql - moderate usage
redwing - 1024 RAM/2 Cores - Zabbix server, Zabbix frontend ( works on the pgsql on purplewing ), couple of websites
whitewing - 512 RAM/2 Cores - staging/testing server
yellowwing - 4096 RAM/4 Cores - Zimbra email, currently not much accounts on it

RAM usage is around ~10G ( yay for KSM ), CPU usage is light atm (from ~1 to ~9 loadavg ), but i don't expect any hard I/O disk usage, at least not soon.

---

### Post by slooksterpsv on 2010-07-11
> **sh1ny said:**
> Well the host with the colorwing vm's has 12G RAM and 2x Xeon 5520, and guests are as follows :

bluewing - 4096 RAM/4 Cores - Web Hosting, Emails/FTP/DNS, Mysql
dev - 1024 RAM/2 Cores - Bzr, Some ruby and php apps, mysql
purplewing - 2048 RAM/2 Cores - Mysql and Postgresql - moderate usage
redwing - 1024 RAM/2 Cores - Zabbix server, Zabbix frontend ( works on the pgsql on purplewing ), couple of websites
whitewing - 512 RAM/2 Cores - staging/testing server
yellowwing - 4096 RAM/4 Cores - Zimbra email, currently not much accounts on it

RAM usage is around ~10G ( yay for KSM ), CPU usage is light atm (from ~1 to ~9 loadavg ), but i don't expect any hard I/O disk usage, at least not soon.

Sorry had to clean up drool off of myself lol, I love Virtualization, as soon as Graphics cards can be handled by the Guest - some work some don't - I'll be using that extensively.

---

### Post by sh1ny on 2010-07-11
> **slooksterpsv said:**
> Sorry had to clean up drool off of myself lol, I love Virtualization, as soon as Graphics cards can be handled by the Guest - some work some don't - I'll be using that extensively.


KVM doesn't work good for desktop guests and that's why i ain't trying to use it for them. I'm sticking to VBox for that. For servers - not really much of a choice tho, if i want to keep using ubuntu server that is. Anyway, so far i'm very happy with the way things work and won't trade it for any other virt tech out there.

---

