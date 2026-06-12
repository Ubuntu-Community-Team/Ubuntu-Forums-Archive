---
title: "Need to set up Ubuntu server edition for Web hosting purpose"
date: 2008-08-02
forum: Server Platforms
---

### Post by anindya23 on 2008-08-02
Hello,
      I need to set up Ubuntu Server Edtion 8.04 for Web hosting purpose.For this, I have some questions to find out answers.
      
      I would like give you the following information about Server.

     # XEON CPU 2Ghz, RAM:1GB,2 HD each 80GB

    1. During Server Edition installation,do i need raid1(Software Raid) configuration?if so,is there any need for /home partion?
    2. During raid 1(Software Raid) configuration,what would be the partion?I mean, how much space for /root?how much for swap and if /home partition is needed,how much for /home partition?
    3. I dont want to use remote desktop.Development pc is running on windows.How can i host my files from development pc to LAMP server?
    4. Plz can anyone give specific instruction to configure raid 1(if possible,Visual instruction) during installation?

---

### Post by Mumbly on 2008-08-02
Take a look at this site. It looks like it has the information you may need to setup a software based RAID array.

[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1]("http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1")

---

### Post by anindya23 on 2008-08-02
thanx.
    I read this articles but it does not give answers of all of my questions.plz check my all questions.

---

### Post by windependence on 2008-08-02
> **anindya23 said:**
> Hello,
      I need to set up Ubuntu Server Edtion 8.04 for Web hosting purpose.For this, I have some questions to find out answers.
      
      I would like give you the following information about Server.

     # XEON CPU 2Ghz, RAM:1GB,2 HD each 80GB

    1. During Server Edition installation,do i need raid1(Software Raid) configuration?if so,is there any need for /home partion?
    2. During raid 1(Software Raid) configuration,what would be the partion?I mean, how much space for /root?how much for swap and if /home partition is needed,how much for /home partition?
    3. I dont want to use remote desktop.Development pc is running on windows.How can i host my files from development pc to LAMP server?
    4. Plz can anyone give specific instruction to configure raid 1(if possible,Visual instruction) during installation?

There will be many opinions on this. It is not necessary IMHO to set up RAID1 on every boxen on Earth, ESPECIALLY software RAID.
 
If you are going to set up a production web server, you would be far better off buying an inexpensive hardware RAID card and running your OS on a small separate drive, and then store your site data on a RAID5 array set up on your hardware controller. The RAID5 array will be faster than a single drive under a normal web server load.

-Tim

---

### Post by redraiderbum on 2008-08-02
> 1. During Server Edition installation,do i need raid1(Software Raid) configuration?if so,is there any need for /home partion?

No you don't need a raid1 configuration.  You don't have to do any raiding if you don't want.  As to whether or not to make /home a separate partition, sometimes it is recommended for a web server to help increase the security by increasing the virtual 'distance' between the root and home parts of the system.  That said, you do not have to do it.  Either way you can always move it at some point after installation if you wish.

> 2. During raid 1(Software Raid) configuration,what would be the partion?I mean, how much space for /root?how much for swap and if /home partition is needed,how much for /home partition?

This is a situation specific question.  Depending on how much memory you have you may want a bigger or smaller swap.  For my desktop I have 2 GB of memory and I make my swap 2 GB.  Swap is essentially the same as a pagefile in windows, but it is on a separate partition.  If you have a ton of memory you may not need a swap at all; if you have 512 MB of memory you will probably need a swap before the installation can proceed for some distros.  You probably don't need a swap bigger than 4 GB, but some people do.  

Root is where most programs are installed so if all you are going to do is install programs to root it doesn't need more than 20 GB.  If you are planning on having all of your storage on separate partitions I would leave 15-20 GB for Root.  If you are going to have your web server, mail server, home directories, and storage on the same partition as root then you are going to need enough space to hold everything.  Again if you are unhappy with the size you chose, you can always mount your web server, home directories, etc. on a different disk or partition that you add later.

If you have a separate partition for /home you only need as much space as stuff you are going to put there.  Virtually nothing else is put there by default except for storage.

> 3. I dont want to use remote desktop.Development pc is running on windows.How can i host my files from development pc to LAMP server?

I don't understand your question.  If you mean you want to develop the web page on a windows box then transfer them to the LAMP server without a remote desktop, then you could just setup the lamp server with an ftp or samba share.  Once you transfer the files over to the LAMP server via ftp, samba, nfs, or whatever you could just log on via ssh to the server and move them to the web server directory.  Or you could just use a program like putty and logon via ssh and directly put them in the correct folder.

> 4. Plz can anyone give specific instruction to configure raid 1(if possible,Visual instruction) during installation?

I prefer configuring raid situations after installation.  Here is an article I found quite helpful.  It is for raid 5 but you can get the picture and just choose a different raid level.

[http://www.howinthetech.com/quick-and-dirty-linux-software-raid5/](http://www.howinthetech.com/quick-and-dirty-linux-software-raid5/)

If you install during install essentially what you do is partition each of the disk as a 'linux software raid' disk then you can proceed to the raid manager and configure the raid1.  After configuring raid1 you can proceed with partitioning the array with root, swap, and whatever other partitions you have decided upon.

---

### Post by anindya23 on 2008-08-03
Many Many thanx to Windepence and Specially Redraiderbum.

---

