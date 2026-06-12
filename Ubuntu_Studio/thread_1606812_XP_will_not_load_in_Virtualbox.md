---
title: "XP will not load in Virtualbox"
date: 2010-10-27
forum: Ubuntu Studio
---

### Post by fumfumfum on 2010-10-27
Hi guys, I'm having trouble getting windows XP to start in Virtualbox.

I installed it off a .iso image and the install and setup went fine, but every time I try to power on XP I get an error message saying an error is caused by sptd.sys (see attached file for screenshot)

Can anybody help me out? Or should I be posting on a windows forum since this is kind of a windows related issue...

---

### Post by trulan on 2010-10-27
I think I've seen this error once but I honestly have no idea what the deal was any more.  I'd recommend browsing on over to the virtualbox forum for this one:
[http://forums.virtualbox.org/](http://forums.virtualbox.org/)

---

### Post by odzk on 2010-12-14
> **fumfumfum said:**
> Hi guys, I'm having trouble getting windows XP to start in Virtualbox.

I installed it off a .iso image and the install and setup went fine, but every time I try to power on XP I get an error message saying an error is caused by sptd.sys (see attached file for screenshot)

Can anybody help me out? Or should I be posting on a windows forum since this is kind of a windows related issue...

same problem here.

---

### Post by Priere on 2010-12-14
maybe your install is corrupted? Redo an other installation and wait and see.

---

### Post by sterken64 on 2010-12-19
**sptd.sys file information**

 			The process [**SCSI Pass Through Direct Host**]("http://www.google.com/search?q=%22SCSI%20Pass%20Through%20Direct%20Host%22") or [**sptd**]("http://www.google.com/search?q=%22sptd%22") belongs to the software [**sptd**]("http://www.google.com/search?q=%22sptd%22") or [**SCSI Pass Through Direct**]("http://www.google.com/search?q=%22SCSI%20Pass%20Through%20Direct%22") by [**Duplex Secure Ltd**]("http://www.google.com/search?q=%22Duplex%20Secure%20Ltd%22").
 			**Description:** File sptd.sys is located in the folder  C:\Windows\System32\drivers. Known file sizes on Windows XP are 642,560 bytes (22% of all  occurrence), 685,816 bytes, 717,296 bytes, 639,224 bytes, 664,064 bytes,  643,072 bytes, 646,392 bytes, 611,064 bytes, 682,232 bytes, 691,696  bytes, 715,248 bytes, 721,904 bytes, 716,272 bytes, 722,416 bytes,  697,328 bytes, 648,952 bytes, 436,792 bytes.[IMG]http://www.file.net/img/space.gif[/IMG] 
The driver can be started or stopped from Services in the Control Panel or by other [programs]("http://www.neuber.com/taskmanager"). The program has no visible window. There is no detailed description of  this service. It is not a Windows system file. The file is a file  without information about the maker of this file.  Therefore the technical security rating is *53% dangerous*, however also read the users reviews.


This is some technical stuff about this system file.


I think its a good idea to look into the discs setting of your XP machine in virtualbox.
i suspect that there is a problem with the choise of your disk-controller


good luck


the dutch guy

---

### Post by josvanr on 2011-01-17
bump... any luk?

---

