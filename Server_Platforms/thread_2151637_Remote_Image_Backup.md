---
title: "Remote Image Backup"
date: 2013-06-05
forum: Server Platforms
---

### Post by bubylou on 2013-06-05
I'm looking for a way of backing up remote windows servers to a Linux server so that they can then be mounted in something like virtual box for disaster recovery. I know of plenty of image creating tools but then what would be the best way to push these image backups to my Linux server. Imaging software recommendations still welcome.

---

### Post by Shrek01 on 2013-06-05
There are so many different cases.  I wish you had been more specific so I am going to give an example of what I would do if a remote win server doesn't boot (so remote I have no way to get my hands on the HD) and I need to recover data.

I would get them a live CD (I like Knoppix for this, but it could be Ubuntu), and have them boot the server with it.  Have them set up ssh.
You then can access the system from your remote location, mount the windows partitions, and recover the files.

---

### Post by Shrek01 on 2013-06-05
Well, you've changed your post since my response so let me ask you a question.  Do you really need the image of the whole partition/HD?

---

### Post by grunge09 on 2013-06-05
Have you looked into Vmware.   This app can "clone" or virtualize your server to another machine for backup.

---

### Post by bubylou on 2013-06-05
I was looking at doing complete disaster protection such as if the building was somehow destroyed. The windows servers themselves have some form of there own backups or redundancy for small issues.
I need to create a boot-able system image so that i could potentially run that server temporarily from another location.

I was looking into Vmware but I think I can find a free solution that meets my needs.

---

### Post by Shrek01 on 2013-06-05
For cold cloning over a network I liked [Partimage]("http://www.partimage.org"). It has a client and server component, but it runs on Linux (you would need a Live CD, or dual boot with Linux)

---

### Post by LHammonds on 2013-06-05
What you are asking can be fairly tricky.  Why?  Because Windows loaded onto a physical box has specific hardware drivers (HAL) and loading that image into a virtual can be problematic if not done right.

When I converted my physical servers into virtual servers, I used ColdClone MOA (IIRC) to make the transfer.  Some images went without a problem, others not so much.  But all of them needed tweaking such as setting the correct CPU (single vs multi) since most servers were multi-cpu but when moved to the virtual, I use just 1 CPU to improve overall performance of the host.  Other things that can be sticky are RAID and video card drivers.

If your disaster recovery plan is to get the servers running in a virtual environment after a disaster, I suggest getting them into a virtual environment BEFORE the disaster.  That will make your disaster recovery process much less prone to failure and complications and will actually help make the servers more portable.

If you just want to rip the partitions off and stick them on a remote folder so you can restore them to another physical server, I use a package called DriveImageXML which is installed directly into Windows and can run on a schedule to create backups while online (no need to go offline to create partition images...even the boot partition).  To restore, you can use a boot CD such as BartPE with the DriveImageXML plugin and restore to another machine.  You can have the image accessible from a network location, USB drive, etc.

LHammonds

---

### Post by bubylou on 2013-06-05
Thank you all for the advice thus far. Right now im looking at just doing the occasional cold image backup with automated backups for data files. Although full blown virtualization would be the best option it may be hard for me to convince people to use it. I was just looking for some tools to use and what setups other people may use.

---

### Post by LHammonds on 2013-06-06
Well, if done right, nobody would know you virtualized the servers. :)

I assume nobody actually logs onto those Windows Servers and uses them as desktop machines as well.

If you could virtualize the server now, I would do it.  Make sure your hardware is supported by ESXi and then give it a shot (if not, try it anyway and see if it works)

Your most powerful server would be the best candidate to virtualize 1st.

I would use DriveImageXML to make a full partition backup of the server, blow out the current OS and install VMware ESXi.  Once that is loaded, I would then use vSphere client to create a virtual machine and restore the OS inside that and clean up the drivers.  If it works, you will have 1 virtual server running on top of ESXi.

If the server is not too demanding, you might even be able to squeeze another virtual server or two on the same box.  If you can free up a physical server, you could use it as a target to replicate your production servers to an alternate host for backup and disaster recovery.

The best way to virtualize servers is not by restoring a physical server inside a virtual but to install the OS inside the virtual to start with.  Then install your applications and restore just the data.  This provides a "clean" OS without issues from left-over hardware which could complicate performance and reliability.

Another major benefit to running production servers virtualized are snapshots.  Do you ever need to patch the operating system, patch the application or perform upgrades?  Simply take a snapshot, do the work and if anything goes sideways due to software or human error, simply revert the snapshot and it never happened!  I can't tell you how effective this has been and allowed me to test out patches/upgrades without fear of going through a complicated restore.  It is as simple as pushing a button to save the server, do the work and then push a button to commit the changes or revert back.

LHammonds

---

