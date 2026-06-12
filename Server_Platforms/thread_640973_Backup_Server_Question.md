---
title: "Backup Server Question"
date: 2007-12-14
forum: Server Platforms
---

### Post by jaywatkins on 2007-12-14
Hello

I would like to set up Ubuntu as a sort of 'network attached storage' for my office.  I have an ancient Dell Optiplex GX-240 with two HDDs, and Ubuntu 7.04 installed.  7.10 would not install on it for some reason.  The first HDD is 40GB in size and contains the install, while the second drive is 500GB in size and has nothing on it.  I formatted the 500GB drive as one partiton, and would like to share it out using Samba.  

I created a directory named 'backup' in /mnt/backup and mounted it.  The folder backup appears in my home directory, and will not persist whenever the computer reboots.  How can I make sure the backup folder is mounted to the 500GB drive every time the server restarts, and not mounted in my user's home directory?

Thanks

---

### Post by stalker145 on 2007-12-14
> **jaywatkins said:**
> Hello

I would like to set up Ubuntu as a sort of 'network attached storage' for my office.  I have an ancient Dell Optiplex GX-240 with two HDDs, and Ubuntu 7.04 installed.  7.10 would not install on it for some reason.  The first HDD is 40GB in size and contains the install, while the second drive is 500GB in size and has nothing on it.  I formatted the 500GB drive as one partiton, and would like to share it out using Samba.  

I created a directory named 'backup' in /mnt/backup and mounted it.  The folder backup appears in my home directory, and will not persist whenever the computer reboots.  How can I make sure the backup folder is mounted to the 500GB drive every time the server restarts, and not mounted in my user's home directory?

Thanks

You are going to need to edit /etc/fstab to allow the mounting of your drive at boot.  Check out the Psychocats web site for a [nice little HowTo]("http://www.psychocats.net/ubuntu/mountlinux"). If you're talking about mounting this drive SAMBA-style (it is on the remote computer), then you can try [this thread]("http://ubuntuforums.org/showthread.php?t=509931") (and there are more).

---

### Post by bproven on 2007-12-15
Hey, I like Ubuntu as much as the next guy, but in your use case I would recommend just grabbing one of the pre-built NAS appliances.  For instance one of these should work great for you with minimum setup:

Both have nice web GUIs to get you going:

openfiler (based on redhat/centos): [http://www.openfiler.com/](http://www.openfiler.com/)
freenas (lighter based on BSD): [http://www.freenas.org/](http://www.freenas.org/)

I've used both and they are very good for this purpose.

---

### Post by jaywatkins on 2007-12-15
Thanks!

The Psychocats tutorial is great!  I have never heard of that site before.

I was considering Freenas, but was stopped by the setup process of getting the .iso onto a CD-ROM.

Thanks again.

---

### Post by sciurus on 2007-12-18
> **jaywatkins said:**
> Thanks!

I was considering Freenas, but was stopped by the setup process of getting the .iso onto a CD-ROM.



[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by bproven on 2007-12-18
> **sciurus said:**
> [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)


Cool -  nice tutorial.  You shouldn't let burning an iso stop you ;)  Good luck and glad to see it worked for you...

---

### Post by jaywatkins on 2007-12-18
I have it working thanks in part to the excellent tutorial posted on psychcocats.com and howtoforge.com

Thanks for all of the great suggestions.  Anyone have any tutorials on  how to configure IPSec on Ubuntu?

---

