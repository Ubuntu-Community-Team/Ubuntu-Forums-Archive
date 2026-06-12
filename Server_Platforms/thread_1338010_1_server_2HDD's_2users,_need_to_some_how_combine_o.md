---
title: "1 server 2HDD's 2users, need to some how combine or split?"
date: 2009-11-26
forum: Server Platforms
---

### Post by husskii on 2009-11-26
Hi I just purchased a new server and have ubuntu server 9.04 installed. I have created 2user accounts plus root & each user gets rdp access to the server. 
I have just realized that I am missing 1 of my HDD's, well its there but its setup as /dev/sda1 to /dev/sda3 and /dev/sdb1 to /dev/sdb3 and I can only access /dev/sda1 to /dev/sda3  between both users. I have read abit about others that have had this problem and I think what I need is raid 0 setup, so I can access both HDD's as one, as Im sure it wouldnt be possible to have 1 HDD per user (or would it)
Now Im only new to Linux and have progressed quiet well with the support of other generous members in this forum, But I'm not sure how to tell if I have raid setup or not. Also I wouldn't know where to start in setting up raid, I have read a few post but most are either talking about windows and Linux in dual boot or splitting up the HDD's (maybe I miss understood them) 
If possible can I get some help setting up my server so that I can access the both HDD's and put them to good use.

Help is needed and much appreciated...
Thanks
Husskii

If its of any help, this is what my partition table looks like..

/dev/sda1 to /dev/sda3 
[[IMG=http://lookpic.com/i/571/JqKA0fCr.jpeg]](http://lookpic.com/i/571/JqKA0fCr.jpeg) 

/dev/sdb1 to /dev/sdb3 
[[IMG=http://lookpic.com/i/512/eERB4mhW.jpeg]](http://lookpic.com/i/512/eERB4mhW.jpeg)

It looks like its already been setup as raid, but am unsure what type of raid and couldn't find any options regarding raid or how to link them..

---

### Post by scorp123 on 2009-11-26
If this is really a professional server that deserves to be called like that (and not just a normal PC) chances are its disks are already setup as RAID 1 mirror via its BIOS. You will have to check its SATA/SAS controller setup.

**RAID 0 is NOT recommended.** If one disk gets hosed (e.g. mechanical failure) you will run into **_BIG_** troubles.

[http://en.wikipedia.org/wiki/Raid_0#RAID_0](http://en.wikipedia.org/wiki/Raid_0#RAID_0)

" ... A RAID 0 (also known as a stripe set or striped volume) splits data evenly across two or more disks (striped) with no parity information for redundancy. ... "

Please read that again: **_no_ redundancy.** If one disk gets hosed you lose ALL your data because the data was evenly split across the two.

I'd leave the disks mirrored. If one disk fails ... no big deal. Just replace it, re-establish the mirror, and you're good to go again and will not lose any data.

---

### Post by husskii on 2009-11-26
Thanks for getting back to me, In relation to losing all the data, I dnt really mind because I already have another server which I backup all my data to. I current server I'm trying to configure is so that both me an a friend can use it and would need to acquire the both HDD's because 750GB isn't much room these days and we would fill it up fast.

The ppl i bought the server off are saying I need to mount the HDD to be able to use it, but isnt already mounted is its showing as /dev/sdb 

thanks

---

### Post by memilanuk on 2009-11-26
Perhaps LVM would be a better option than RAID 0?  That way you can 'grow' the volume group as you later add more/bigger hard drives.  I'm just not sure how you would go about backing out of your current setup short of a re-install?

---

### Post by husskii on 2009-11-26
hi memilanuk
A reinstall is ok to me, as I havent used the server yet its only a day old :)

I setup LVM on my home server which also has 2 hdds but again only the first hdd I installed the OS on was showing...

are you telling me that as my HDD grows it will then start to move onto the 2nd HDD as the first one fills up... or am I ment to do something when I reinstall so it can combine them both...

thanks

---

### Post by memilanuk on 2009-11-27
Assuming you are installing from the Server disc... take a look [here]("https://help.ubuntu.com/9.10/serverguide/C/advanced-installation.html#lvm").  

The short version is there is a point during the install when you have the opportunity to just format the drives (in which case it takes the first available drive, IIRC, which might be why you don't see the second drive?), and partition it, or to set up software RAID or Logical Volume Manager (LVM) - or both.  Read the directions, and the linked howtos, for more information.

The general concept is that the LVM exists as a 'layer' over the physical hardware of the drives.  Instead of creating partitions on the drives themselves, you add the first drive (physical volume, or PV) to the volume group (VG).  You then partition that volume group as desired - whether it be one big / partition, or multiple smaller partitions.  When your drive start becoming full, you can add the second drive as a new physical volume to the volume group, and voila! it now appears to the operating system as if you have a 1.5TB drive instead of a 750GB drive.  Later if you add two 2TB drives to the volume group, your storage expands accordingly - yet the operating system still sees it as one big drive, rather than multiple drives that you have to juggle the space on.  

The downside is that if one drive in the volume group goes TU, you'll have problems all the way.

Take some time, read up on it, and give it a whirl.  Sounds like you have a system that you can play around with a bit, so it'll be a good learning opportunity.

---

### Post by husskii on 2009-11-27
Im installing the OS remotely and can always reinstall as I havent started to use it yet.. but Im not using the cd install as I cant access the cd rom not sure if it even has one.. its an ovh server..

Ill try that link and see if it help.. (i hope)

also I think maybe I should ask them to not setup as raid... then ill install with LVM, because all I want is to be able to access both hdd's... 

do u think that might work.. 
Im testing now on home pc.. but using cd at home.. maybe i should try it without cd.. but I dnt know how...

If I format my pc and try the http command in dos, would it install ubuntu or do i need something else first before I can start getting apps from the net,, such as http or apt-get...

---

### Post by memilanuk on 2009-11-28
To be honest, I don't have any experience with doing remote installs such as you describe.  Everything I've ever done has been local to me, either using a full CD/DVD to install from, or a smaller CD or iso image to do a network install (and pull the files in as needed).

I have no idea how you would go about doing a local install on your PC without a CD or at least an ISO image at hand.  I don't think you'll be able to simulate that part.  Just stick the CD in and reboot, and it should launch you into the installation process where you can reformat drives, make them part of a volume group, and all that jazz.

An option (if you actually use your PC for anything meaningful and/or don't want to risk disruption of your internet connectivity in the event of a driver problem) may be to download Virtualbox PUEL (Personal Use & Evaluation License) and do some trial runs on that.  Create a couple virtual disks, they don't have to be huge, say 5-10GB each, and then go through the installation process and see what you should expect as far as the installation process and setting up LVM, software RAID. etc.  That way you have some idea of what to do when it comes time to do the remote install for real.  If the Virtualbox install of Ubuntu doesn't work the way you want, it's real simple to wipe and start over ;)

---

### Post by husskii on 2009-11-28
I ended up installing from cd on my home pc, and managed to get the 2nd hdd to show, but instead of counting both hdds as one and showing say 50GB available, it ended up making the 2nd hdd as a media drive, like an ext hdd... 

not sure why but ye that was how it installed...

I'm just using an old pc which is p3, I use this pc to practice on so im cool if it stuff up :)

Is Virtualbox PUEL like KVM because I tried the 
egrep '(vmx|svm)' /proc/cpuinfo command and It didnt work, I tried it before so I could help test koala :)

---

### Post by memilanuk on 2009-11-28
It sounds like you need to slow down and actually read / experiment with some of the options when you go through the install instead of blowing through as fast as possible and letting the installer choose the default choices.  You had plenty of opportunity to set up LVM and get *both* drives together in one volume group.  You need to stop trying to ram through this, and do some reading in the manual and in the community documentation.  I know enough to get through the process myself, but I have neither the time nor the inclination to walk you through every single keystroke via these forums.  Sorry.

Good luck.

---

### Post by husskii on 2009-12-04
hi memilanuk thanks for all your help, but I have to disagree with you on your last post, I read everything I come accross, but the info and help on the os etc is made for linux users that know and understand the system, not too helpfull for novice linux users like my self, thats why I like using this forum and a few others, because you will always find someone willing to give a hand and explain what you dnt understand ;)

Again Thanks heaps for all your help I like to think I learned a fair bit from this post, also thank you for the tutorial on LVM it help a lot and gave me a better understanding on how it works, I went with raid 0 tho and configured the second hdd as a extended partition to my home folder (if thats how u describe it lol) and I now have 1.4TB available in my home folder. 

I have now completed the setup and have reached my goal of making both hdd's count as one, even better I explored webmin and decided to install webmin on my server and now life hasn't been easier, when it comes to hdd quotas, Im sure there is more to it and am learning more as I explore lol...

much appreciated
Husskii :)

oh just before i go, I messed up my 2nd server and couldn't get apt-get to work, after removing x-window-system-core, I kept getting an error > "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

and I tried manual install etc but nothing worked, so I decided to reinstall the kernel and messed up big time, after reboot the server was unreachable.. anyways I have asked the host for a reinstall... 

I tried finding a command I could use thru putty to reinstall the server but came up empty handed.. just for future preference is it possible to reinstall the server thru putty if u dnt have local access to the server.

---

