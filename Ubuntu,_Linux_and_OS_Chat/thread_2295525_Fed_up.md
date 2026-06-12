---
title: "Fed up"
date: 2015-09-19
forum: Ubuntu, Linux and OS Chat
---

### Post by Lewjay on 2015-09-19
I am fed up with UBUNTU.  I decided to install this on my desktop computer (64bit,  1TB HD, 6GB ram running WIN10)  I went to the website and looked at the 14.04 version and spent an hour or so downloading.  Only option I got was to BURN TO CD.  Then it says my DVD was not large enough (700MB)  So I dug around and found an install version 12.o2 and ran it.  Once it was loaded, I then did the update which took another hour.  So finally I have 14.04 UBUNTU on my machine.  Played around for a bit and then went to restart to go back to WIN10.   GRUB RESCUE is the only thing that comes up.  Tried again, no luck.  Looked on the FORUM and find that there is a problem with WIN 10 and it's hibernation.  Did not see ANY Disclaimer on the download site about fixing this before installation.   NOW I'M HOSED!!!
I'm trying to fix this using my TRY UBUNTU 12.02 without any luck.  I cannot get the BOOT REPAIR to run,  I can't find a way to get rid of this partition, and all the help I can see does not make any sense at all.  
I even tried to do a system recovery but it was for WIN7 and since I had only recently upgraded to WIN10 I had not made a new recover disk.  Trying to find someone that can create one for me but no luck so far.

---

### Post by ian-weisser on 2015-09-19
[EDIT] nknwin and Buck Ball's advice below is excellent. Listen to them.

---

### Post by Bucky Ball on 2015-09-19
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by nknwn on 2015-09-19
You should be able to save your important user files by using the Ubuntu live disk. Boot to Ubuntu and copy or burn your files.

Assuming you have a Windows 7 product key: Download Windows 7 ISO (to make your own win 7 install DVD) from a link here: [https://www.microsoft.com/en-gb/software-download/home](https://www.microsoft.com/en-gb/software-download/home)

If the Windows installer has trouble with your Linux partition delete it by booting to your Ubuntu live disk. Use GParted if available.

---

### Post by Bucky Ball on 2015-09-19
As above. Windows has no idea about EXT Ubuntu partitions. Boot from the Live install DVD/CD/USB (incidentally, the error you were getting about 700mb not being enough suggests you were using a CD, not a DVD), launch Gparted and delete the EXT partitions, as suggested.

---

### Post by monkeybrain20122 on 2015-09-19
Instead of posting a rant here you should have created a support thread if you are interested in getting help. 
> I went to the website and looked at the 14.04 version and spent an hour or so downloading.


If it took you an hr to download the iso you have slow internet connection. since you are downloading with Windows it has nothing to do with Ubuntu if your Windows connection is not up to par (takes me ~ 5 minutes to get the iso and my internet is not very fast  since I use wifi and live in a basement)

> Only option I got was to BURN TO CD.  Then it says my DVD was not large enough (700MB)  

Again you don't have a DVD/usb flash drive is not Ubuntu's problem. Other than some light Linux distros it is hard to find modern operating systems that fit into one CD. The CD is simply an obsolete medium for software. Instead of CD/DVD I would use a usb flash drive, these are ubiquitous and quite cheap, reusable, can multiboot and support persistence. I would rather have one or two around then to keep a stack of DVDs (who still use DVDs?) 
> So I dug around and found an install version 12.o2 and ran it.  Once it  was loaded, I then did the update which took another hour.  So finally I  have 14.04 UBUNTU on my machine.


That is a very slow way to get 14.04 (install 12.04 then upgrade) You probably should wait after you get a usb flash drive/DVD

> Played around for a bit and then went to restart to go back to WIN10.    GRUB RESCUE is the only thing that comes up.  Tried again, no luck.   Looked on the FORUM and find that there is a problem with WIN 10 and  it's hibernation.  Did not see ANY Disclaimer on the download site about  fixing this before installation.   NOW I'M HOSED!!!

Why should there be any disclaimer on Ubuntu's download site? Does MS provide any support for dualbooting? It is MS that makes it difficult to boot other OSes by messing with the hardware.

---

### Post by QIII on 2015-09-19
There is neither profit nor purpose in ranting on the one hand or becoming defensive and pointing at someone else as the culprit on the other.

@Lewjay:  If you want support, start a polite thread in an appropriate help forum and ask for specific help.

Since this has already taken a turn for the argumentative: Closed.

---

