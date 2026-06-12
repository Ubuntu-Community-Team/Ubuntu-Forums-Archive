---
title: "[SOLVED] file server dapper or feisty"
date: 2007-06-01
forum: Server Platforms
---

### Post by sartic on 2007-06-01
I need stable and fast file server. Server will be amd sempron 3.0, 512MB, mobo width amd chipset.
Dapper or feisty? Please write some pro and contra.

---

### Post by logical_thought on 2007-06-01
What kind of file server are you looking for? If you wanting to share with Windows and Linux on your local network you need to use samba. If it is just to share files with only Linux, NFS should work. If you want to share over the internet...a ftp server like sftpd would work.

---

### Post by Chayak on 2007-06-01
Either one will serve files the only difference being feisty has the latest and greatest software but dapper having the tried and true of sorts.  If you want a simple NAS I'd point you towards [freeNAS]("http://www.freenas.org") It's lightweight and doesn't require all that much in the way of hardware or memory and is really easy to configure.

---

### Post by sartic on 2007-06-01
> **logical_thought said:**
> What kind of file server are you looking for? If you wanting to share with Windows and Linux on your local network you need to use samba. If it is just to share files with only Linux, NFS should work. If you want to share over the internet...a ftp server like sftpd would work.

LAN file server, clients will be windows. It will be file/backup server. I am considering ftp server because of resume possibilites (file will be big and lan is only 100mb).

---

### Post by sartic on 2007-06-01
> **Chayak said:**
> Either one will serve files the only difference being feisty has the latest and greatest software but dapper having the tried and true of sorts.  If you want a simple NAS I'd point you towards [freeNAS]("http://www.freenas.org") It's lightweight and doesn't require all that much in the way of hardware or memory and is really easy to configure.

Thx 4 url. I will investigate that but i guess it is specialized server.  Today it will be file/backup server tommorow it can be used as printer server, intranet im... etc. Dapper has 1yr longer support than feisty. I am "afraid" of amd chipset never installed linux on that platform.

---

### Post by telex4 on 2007-06-01
I doubt the chipset will pose any problems. I'd go with Dapper fot the long-term support and stability. There's no need for the "latest and greatest" on a file server :)

If it doesn't work after the initial install because of some drive problem that Fiesty has fixed, just upgrade. Better yet, check on launchpad and search the web to see if there are any known problems with the specific hardware.

---

### Post by logical_thought on 2007-06-01
> **sartic said:**
> LAN file server, clients will be windows. It will be file/backup server. I am considering ftp server because of resume possibilites (file will be big and lan is only 100mb).

Well, if its going serve to windows clients, you really only have two good options, samba or ftp. If you decided on ftp, I found vsftpd to be very secure and useful (At least when I was using it).

Also, if there are no driver problems I found that vsftpd worked great on dapper.

---

### Post by sartic on 2007-06-04
> **logical_thought said:**
> Well, if its going serve to windows clients, you really only have two good options, samba or ftp. If you decided on ftp, I found vsftpd to be very secure and useful (At least when I was using it).

Also, if there are no driver problems I found that vsftpd worked great on dapper.

Didn't tried that. I would love 2 find something as zftp suite on win32 ... fast and peace of cake 2 admin (nice gui).

4 all ... today was disaster. I built server width 2 sata2 disk 320GB. Mobo is Epox s.AM2 EP-AT690G-Pro (amd chipset 690g).
1. dapper livecd ... kernal panic
2. #1 width nopic... same
3. feisty livecd ... freeze during splash
4. #3 width noapic ... same as #3
5
6
.... tried 2 disable noapic in bios , didn't find hpet in bios option as 1 suggested...

Tommorow i will try "pci=nomsi irqpoll noapic acpi=off" . If that doesn't help ... that's all i found on forums.
Anyone where can i find detail explanation 2 all command line options 4 livecd?

ps: i use livecd... because it is faster and it works for my native language out of box. 
ps #2 : i will try also disabling onboard lan and using some older lan pci.

any hints more?

---

### Post by sartic on 2007-06-05
Dapper doesn't work on this mobo at all. Onboard LAN is not working out of box, i am waiting now for plain pci lan card... and i have problem width shutdown. I have freezed splash after shuting down.

---

### Post by coxy on 2007-06-05
I would suggest downloading the Dapper server CD which is a text based installer that will give you a server environment only (no desktop). You can then install the packages you require and have a very light and fast installtion. I have never used the live CDs to install my servers, desktops or laptops because I prefer the text based installer; but that is just me!

If you are still having problems then you could try Debian Etch which is the current stable release of Debian. You can get the net install .iso from [http://www.debian.org](http://www.debian.org) which will leave you with a similar environment to the Dapper server disk. Debian servers are well known for the stabilty and reliabilty.

---

### Post by sartic on 2007-06-05
> **coxy said:**
> I would suggest downloading the Dapper server CD which is a text based installer that will give you a server environment only (no desktop). You can then install the packages you require and have a very light and fast installtion. I have never used the live CDs to install my servers, desktops or laptops because I prefer the text based installer; but that is just me!

If you are still having problems then you could try Debian Etch which is the current stable release of Debian. You can get the net install .iso from [http://www.debian.org](http://www.debian.org) which will leave you with a similar environment to the Dapper server disk. Debian servers are well known for the stabilty and reliabilty.

No thx, 2 reason:
1. Sempron and 512mb is more than enough 2 serve 5-10 clients on this lan
2. I prefer gui 4 admin and i can always use tightvnc 2 admin that server.

I solved lan problems when i put rtl8139 pc card. Shutdown is still problem but that machine is server so it won't be shut down 4 long time...

Now I am looking 4 backup program width schedule 4 backuping 1 dir 2 another disk. Any idea (please gui version :) ?

Not quite happy width speed of transfer, but is stable and free server. Still stumbled why samba is slow not near 5MB/s i have on win lans.

---

### Post by sartic on 2007-06-06
Solved all problems. Slow transfer solved by "auto-detect" or "auto-sense" in lan properties 4 win clients.
"Simple backup" i choose 4 backup (have gui and schedule). FTP was dropped because 2 reasons: people that work on win32 didn't know what is ftp, and they can not easy open and save from their familiar programs files they want.
Another quest is jabber ;)

Conclusion Dapper is not 4 this new amd chipset (we need new lts or respin of dapper). Feisty is working but no real shutdown, lan and agp doesn't work out of box (neither one was must 4 me in this situation)

ps: thx 4 all hints i found on this forums, so i am giving back something 2 users of amd 690G :)

---

