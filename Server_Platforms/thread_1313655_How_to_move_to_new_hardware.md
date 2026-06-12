---
title: "How to move to new hardware"
date: 2009-11-03
forum: Server Platforms
---

### Post by breauxlg on 2009-11-03
I have been running 8.04 lts for a while now, and have several websites running on it using the perfect server ispconfig2 tutorial. I originally installed it on a decommissioned windows 2003 server that I had replaced with a new 2008 server. I now want to move the Ubuntu install to a brand new Dell server that I bought and received today. What is the minimal OS I need to install on the new server to be able to move the old server over with all of my additions, users and websites? What is the simplest path to do this? Many, many, many thanks in advance for a simple way to do this. I seem to remember a forum article that showed how to do this, but I can't for the life of me find the right combination of search criteria to be able to get back to that article. Again, Thanks.
Lynn

---

### Post by cariboo on 2009-11-04
You really should have to do anything, just move your hard drives to the new computer and your good to go. I just swapped the motherboard, cpu and ram in my server, I didn't need to do anything, I replaced the hardware and turned it on.

---

### Post by happyhacker on 2009-11-04
I will want to install the latest Ubuntu soon on new hardware but I don't want to move the old drives over.

Is it possible to port the OS and everything else by taring stuff up and moving thew file over by webmin and going from there. I was wondering if I install Ubuntu the copy over my environment.

Is there a tutorial(s)?

---

### Post by breauxlg on 2009-11-04
I am going to all new hardware including disks, faster, bigger, etc. So I need to move the OS and data.

---

### Post by happyhacker on 2009-11-04
Are you asking for advice like me or do you already know what to do?

---

### Post by koenn on 2009-11-04
you can get some inspiration from 
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

and

[http://users.telenet.be/mydotcom/howto/linux/clone.htm](http://users.telenet.be/mydotcom/howto/linux/clone.htm)

---

### Post by viper250 on 2009-11-04
download and burn the iso for clonezilla you can clone everything using crossover cable or usb print and follow the instructions for the type of cloning you want
works good for me

---

### Post by breauxlg on 2009-11-04
Definitely asking for advice here. I'm just going from one server to another, hardware-wise. No old hardware moving to new server. I can mount new drive in old server if need be. New server has 4 500Gig hard drives, old server has 2 250 gig hard drives. Second drive for backup. All of my stuff is on the first hard drive on the old server.

---

### Post by breauxlg on 2009-11-05
Does clonezilla allow moving to different hardware?

---

### Post by viper250 on 2009-11-06
I have had no problems with it but if you are unsure you can install your os in the new server and sync your data from the old machine via crossover cable between the machines or patch cable thru a hub. Im not positive but I think that ubuntu server has a network os install function. I know that clonezilla has a network cloning version
(i have over 150 different versions of linux in my collection and actively use about 9 of them).
 My old server is still running as slave to the new one.
 this is great because it greatly speeds up downloads even when using bit torrent but I cant wait until they install the fiber optic network in our area
anyway here is a website that may have more info  [http://ubuntulinuxhelp.com/](http://ubuntulinuxhelp.com/)

---

### Post by breauxlg on 2009-11-06
I just cloned the disk, and now I have a bunch of free space at the end, past the swap partition. Can I just delete the swap partition, expand the primary partition and then re-create the swap partition at the end of the disk?

---

### Post by JHan816 on 2009-11-06
I was looking at doing something similar with my home server using the Remastersys utility.
 
[http://www.remastersys.klikit-linux.com/ubuntu.html](http://www.remastersys.klikit-linux.com/ubuntu.html)
 
I created a backup CD of my server but did not get to restore to the new system yet. It does boot as a live CD. I guess there will be some tweaking to do once it is installed.
 
It is something to look into, I hope it helps.

---

