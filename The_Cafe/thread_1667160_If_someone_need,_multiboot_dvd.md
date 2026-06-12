---
title: "If someone need, multiboot dvd"
date: 2011-01-14
forum: The Cafe
---

### Post by asteriks on 2011-01-14
Hi everybody, many times I saw on Internet that people ask how to create Linux multi boot DVD, so, here are some new distros, installed in one DVD. 
  I chose 4shared for hosting of files, because they don’t have so big limitations about download as others have, although maximum file size for upload is 200MB. I had to split/separate 4GB into 21 file. You must download 21 times 190MB, unzip and get one iso file 4GB. I used 7-Zip software for that. Some hosting solutions where people can upload 5GB simply didn’t work or I had to wait 6 hours to upload one file and I didn’t have time for that.
  You can download all files from here: **[http://linuxdvd.4shared.com](http://linuxdvd.4shared.com)**
   
  In any case, ISO was created with SarduCD software, therefore there are some utilities and not only linux distros. 
   
  Here are **utilities**:
  NT password (cd100627.iso)
  Ophcrack (ophcrack xp live cd 2.3.1.iso)
  Ultimate Boot CD (ubcd503.iso)
   
  And next **linux distros**:
  Backtrack (bt4-r2.iso)
  Fedora (fedora-14.iso)
  Ubuntu (ubuntu10.10.iso)
   
  _Note No1_: when I uploaded file sardu.zip.006, internet connection was broken at the end of upload, but I think everything is okay, if something is wrong, you can [send me information]("http://www.4shared.com/u/FW671Z78/saschapredic.html") and I will upload again that file. 
  _Note No2_: when you boot DVD after burning, you should know that backtrack will show console situation, you will have to type **startx** in order to get graphic interface/GUI. After that, you will have to start network, backtrack by default is not connected with network, in order to be able to use internet, open console and type: **sudo update-rc.d networking defaults**
  If this doesn’t help, you will have to ask in backtrack forum for help. And by default, backtrack username is **root** and password **toor**, if you need it.

------------------

There is **one more Linux MultiBoot DVD** iso image created on January 16.2011. Here are links for download, all of it in one folder [http://www.megaupload.com/?f=WERFXXY5](http://www.megaupload.com/?f=WERFXXY5)
Here are versions of all included files: [Screenshot]("http://blog.predicsasa.com/wp-content/uploads/2011/01/screenshot5.jpg")

Inside of 4GB iso file are next things: 

_* Antivirus_
AOSS PC Tools
Avira Antivir Rescue ystem
VBA Rescue

_* Utility_
Clonezilla
GParted
NT Password
Ophcrack
Ping
Redo Backup Live CD
Hiren's Boot CD
System Rescue CD
Ultimate Boot CD

_* Linux Live_
Austrumi (I checked with Virtual Box, here is what I  got for Austrumi: [boot menu]("http://blog.predicsasa.com/wp-content/uploads/2011/01/austrumilinuxboot.jpg") was okay but [boot was stopped]("http://blog.predicsasa.com/wp-content/uploads/2011/01/austrumifail.jpg"). Austrumi kernel need **pae** and what is pae, I don’t know. If you know how to edit iso image before burning to DVD, you can correct this mistake.)
Damn Small Linux
Fedora
Puppy
Slax
Ubuntu

_* Windows_
Windows XP Recovery Disk
Win 7 Recovery Disk

---

### Post by asteriks on 2012-05-14
Hi, I created again multiboot iso image, with newer versions/distros, sardu1.iso is 3.36GB and it can be burned to DVD and sardu2.iso is 5.9GB (included backtrack 5 R2 gnome) and it can be burned to dual layer DVD or installed to USB.

sardu1: [http://d01.megashares.com/?d01=70YBooc](http://d01.megashares.com/?d01=70YBooc)
sardu2: [http://d01.megashares.com/?d01=0V5G64d](http://d01.megashares.com/?d01=0V5G64d)

**sardu1 details:**
_antivirus:_
f-secure rescue 3.14-44905
panda safe 4.4.3.0

_utility:_
clonezilla 20120326-oneiric
GParted 0.12.1-1
NTpassword 110511
Ophcrack 2.3.1 vista and xp
Partition Wizard 7.1
Ultimate Boot CD 511
Hiren's Boot CD 15.1 (lot of software: [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd))

_Linux_:
Fedora 16 i686
Limp (120MB)
Ubuntu 11.10 i386

**sardu2 details:**
the same like sardu1 + added backtrack 5 R2 Gnome

**note**: when you install it, you can boot Hiren's CD and choose Mini Win XP and there are lot of softwares to use.

---

### Post by asteriks on 2013-03-15
I made new Sardu DVD, 4.07GB file, March 14.2013. if you need it, you can download it and burn to DVD. I think this is nice collection, instead to have 3 or 5 CD/DVD, you get all in one DVD.

[http://dfiles.eu/files/i6ivk4b1v](http://dfiles.eu/files/i6ivk4b1v) (information.txt file 476B)
[http://dfiles.eu/files/30btvus0p](http://dfiles.eu/files/30btvus0p) (sardu.7z.001 1.81GB)
[http://dfiles.eu/files/gu8f9nvg8](http://dfiles.eu/files/gu8f9nvg8) (sardu.7z.002 1.81GB)
[http://dfiles.eu/files/spcryq7ar](http://dfiles.eu/files/spcryq7ar) (sardu.7z.003 437MB)

information.txt:

**Antivirus: **
Dr.Web Live (drweb-livecd-602.iso) 
Panda Safe 4.4.3 
 
**Utilities: **
NT Password (cd110511.iso) 
Ophcrack without tables (ophcrack-notables-livecd-3.4.0.iso) so you must have tables downloaded to USB.
Hiren's Boot CD 15.2 
 
**Linux: **
Puppy Linux (Slacko Puppy 5.5) 
Slax (7.0.6 i486) 
xPUD (xpud-0.9.2.iso) 
Ubuntu (ubuntu-mini-remix-12.04-i3386.iso) this is basic ubuntu 200MB, I got only Terminal and then I should use it to install Ubuntu to PC "from scratch", but for live DVD use, you can use Kubuntu.
Kubuntu (kubuntu-12.10-Desktop-i386.iso) 
Mint (linux mint cinnamon 14.1 dvd 32bit) 
Tails (tails-i386-0.17.iso) this is privacy distro of linux, you get connected to Internet through Tor network (proxies). 

although it is big question how much tails and tor network are really independent from american intelligence: 
[https://tails.boum.org/forum/Who_is_Sponsor_Bravo__63__/](https://tails.boum.org/forum/Who_is_Sponsor_Bravo__63__/)
admin of forum also censored/deleted topic: A highbandwith Tor node operator also flies a Predator B drone.
38 "operators" collectively carry half of all Tor traffic: [https://tails.boum.org/forum/Who_carries_half_of_all_Tor_traffic__63____38_operators/](https://tails.boum.org/forum/Who_carries_half_of_all_Tor_traffic__63____38_operators/)

so, tails and Tor are secure how much you make it to be secured. don't believe to developers.

---

### Post by Muhammad_Anas on 2013-10-03
Thanks a lot! I was long searching for a multi-boot iso. I'm downloading all parts. just a question; Should I extract all parts in a folder and then make .iso but how? is there any software for that?
By the way only this link (4Shared) is working all other are not. I understand it's an old post though!

---

