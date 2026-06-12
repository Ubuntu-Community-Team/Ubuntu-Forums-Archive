---
title: "Fail to intsall ubuntu 8.04LTS Server Edition"
date: 2008-08-20
forum: Server Platforms
---

### Post by sahwan on 2008-08-20
i don't know why isn't install success 

after scanning the CD with the 'Additional Component Loading'

the installer gave me a massage that he Failed to copy file from CD-ROM. Retry?

if i retry same massage abeer i download the ISO & Burn it on anther CD but the same massage abeer 

i used an original CD that was sent to me by ubuntu but the same message again

i am trying to intall it on IBM Server with Name 'e server' Model No. 'XSeries 330'

with 2 pantum III 1.4 GHz & 2GB ram with 2 * 73GB hard disk

any idea?

---

### Post by jonabyte on 2008-08-20
Could be a hardware issue with the computer itself. Hard drive, controller....

---

### Post by sahwan on 2008-08-20
> **jonabyte said:**
> Could be a hardware issue with the computer itself. Hard drive, controller....

i don't think so 

i just finish the 6.06LTS Server Edition & it works fine

i think some thing in command line most be add

any other ideas?

---

### Post by Ximbiot on 2008-08-20
What about a driver that the installer knows is needed for your particular hardware configuration but which got left off the install CD for some reason?

Is it possible to perform a network install with the hardy install CDs?

---

### Post by sahwan on 2008-08-20
the hard disks are 2 scsi drivers

i think from adaptec 

link for the server on IBM website 

[https://www-304.ibm.com/systems/support/supportsite.wss/selectproduct?familyind=5050276&typeind=5098407&modelind=5097183&osind=5053383&continue.x=21&continue.y=17&brandind=5000008&oldbrand=5000008&oldfamily=5050276&oldtype=5098407&taskind=2&matrix=Y&psid=bm](https://www-304.ibm.com/systems/support/supportsite.wss/selectproduct?familyind=5050276&typeind=5098407&modelind=5097183&osind=5053383&continue.x=21&continue.y=17&brandind=5000008&oldbrand=5000008&oldfamily=5050276&oldtype=5098407&taskind=2&matrix=Y&psid=bm)

---

### Post by finalmillenium on 2008-08-23
I'm currently having a similar problem on a different version of the same server.

My problem is that it can't even pass the cd test.
But it passed burn checking, md5sum for the image, and it works fine in every other system I tried it in.

---

### Post by windependence on 2008-08-23
I don't think it's his hardware. Sounds like it's pretty plain vanilla.

Try burning the CD at a much slower speed, say 4X.

-Tim

---

### Post by finalmillenium on 2008-08-24
> **windependence said:**
> I don't think it's his hardware. Sounds like it's pretty plain vanilla.

Try burning the CD at a much slower speed, say 4X.

-Tim

I tried it.  I also tried a different optical drive.  I even tried ubuntu server 7.10.  Same problem.

---

### Post by wirepuller134 on 2008-08-24
We are in the process of replacing several ibm xseries 342 servers.  Today I tried to install Ubuntu server 8.04, for a forum member to see if I could duplicate his issue.  It hangs on install when attempting to read from the cd drive to copy files to the hard drive for install.  I was thinking at first it was the scsi cd drive, but when I installed an ide drive, same issue.  I shut down the planer scsi controller and installed an ide harddrive and it installed without a problem.  
   We presently run Solaris, Red Hat, and Fedora on that series without a problem.  We are still new to Ubuntu (using on desktops since may or so without any issues).  I'll try the install on one of the new servers when we get more caught up on the upgrade, as we would prefer to standardize the server room to one distribution.

---

### Post by sahwan on 2008-08-25
i think its some thing in the bios

i read some article about the pnp bios 

i will try & keep update

---

### Post by wirepuller134 on 2008-08-26
Ok after a call to ibm for the old xseries 342, this is what they said to do to install.  Not sure why it worked but it did.  On boot up when prompted press ctr A, go to the drive you are going to be booting from and press f6 to set it to defaults.  press esc twice to confirm changes, resume boot up and install OS.  They also suggested flashing the BIOS with the newest version 1.08, ours still loaded with 1.04.  Good luck and happy installs!!

This worked for what I was attempting to do, these servers are being phased out here, and just wanted to see if I could get Ubuntu to install with the original hardware.

---

### Post by finalmillenium on 2008-08-30
This did not help my situation.  The problem I'm having is related to the cd-rom drive and the ubuntu installer.  It just won't work right.

---

