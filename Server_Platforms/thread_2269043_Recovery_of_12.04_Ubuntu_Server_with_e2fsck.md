---
title: "Recovery of 12.04 Ubuntu Server with e2fsck"
date: 2015-03-13
forum: Server Platforms
---

### Post by Marc-NJ on 2015-03-13
So I was able to use e2fsck to recover a bad superblock on my Ubuntu 12.04 LTS system and thankfully it's back up and running.  However, I was hoping the community here could answer two question regarding this:


1) I looked in /lost+found after I was able to reboot and get into the system, and there's nothing there.  Does that mean all of my files were recovered and exist in the same place and the system didn't need to move any to lost+found, or am I potentially looking in the wrong place?  Is there any easy way I can check to see if any data is possibly missing after the e2fsck recovery?


2) It occurs to me that my Ubuntu server is relatively critical to my small business (I'm running a few software applications on there, including ownCloud that stores a lot of my data).  I have CrashPlan installed on there that is backing up the actual data, but having to rebuild the entire server if it crashed (or the hard drive failed) and then restore the data would put me out of commission for quite a while.  Can I get a server that is running some sort of RAID (maybe RAID1?) with multiple hard drives, and that way if one fails I can just revert to another one with no downtime or loss of data? 


And if so:
a) can anyone suggest where I can get a relatively good, cheap server (maybe last year's model, or the year before - right now I'm running the Ubuntu server on a desktop workstation from a few years ago) that supports RAID?
b) Will I be able to take my existing Ubuntu server installation on the current hardware and just "move" it over to this new server, or do I have to start from scratch basically?  If I can "move" it over relatively easily, can someone point me to some tutorial/instruction on how?
c) If I have to start from scratch, is it recommended to continue with Ubuntu Server 12.04 LTS, or go with the newer 14.04 LTS version?




All advice/suggestions/help are greatly appreciated!

---

### Post by nerdtron on 2015-03-13
> 1) I looked in /lost+found after I was able to reboot and get into the  system, and there's nothing there.  Does that mean all of my files were  recovered and exist in the same place and the system didn't need to move  any to lost+found, or am I potentially looking in the wrong place?  Is  there any easy way I can check to see if any data is possibly missing  after the e2fsck recovery?

Just my opinion here. If you do find any file on the lost+find folder, that file is probably corrupted so you are better off restoring that file from your backups, rather than run fsck or file recovery. If you did not find any file in lost+found, your files are probably good after the disk check.

> 2) It occurs to me that my Ubuntu server is relatively critical to my  small business (I'm running a few software applications on there,  including ownCloud that stores a lot of my data).  I have CrashPlan  installed on there that is backing up the actual data, but having to  rebuild the entire server if it crashed (or the hard drive failed) and  then restore the data would put me out of commission for quite a while.   Can I get a server that is running some sort of RAID (maybe RAID1?)  with multiple hard drives, and that way if one fails I can just revert  to another one with no downtime or loss of data? 
Although RAID is not a substitute for data backups, it definitely minimizes downtime on failed hard drives. I won't recommend software raid because sometimes it can be a pain to setup/rebuild. 
And since this is a small business I think it would be good to invest on a server hardware that is capable of hardware RAID1.


And if so:
> a) can anyone suggest where I can get a relatively good, cheap server  (maybe last year's model, or the year before - right now I'm running the  Ubuntu server on a desktop workstation from a few years ago) that  supports RAID?
I don't have a specific model in mind, it really depends on your budget, but HP and Dell servers are quite good.

> b) Will I be able to take my existing Ubuntu server installation on the  current hardware and just "move" it over to this new server, or do I  have to start from scratch basically?  If I can "move" it over  relatively easily, can someone point me to some tutorial/instruction on  how?
c) If I have to start from scratch, is it recommended to continue with  Ubuntu Server 12.04 LTS, or go with the newer 14.04 LTS version?

I suggest you reinstall. Just leave your current server running (to reduce downtime), and independently configure your new server, preferably 14.04, or if you really want to stick to 12.04 which is still supported to 2017.
After you reinstall the OS and configure anything you need, copy all your data to the new server.

---

### Post by tgalati4 on 2015-03-13
The other option that is becoming popular is to purchase a virtual server in the cloud.  As prices have come down, it is quite compelling to spin up a server from a cloud provider and migrate your applications.  Again, you could migrate to 14.04 and use that as a test platform to make sure all of your applications work correctly.  There may be concerns with security and data privacy, etc and those you will have to address, but having an off-site server is handy when disaster strikes.

Check craigslist for used HP Proliant or Dell PowerEdge servers, there are a lot of them floating around.  There are also several power-efficient servers that are starting to make inroads to the traditional rack-server market with ARM chips and Intel Atom chipsets.  Again, build that with 14.04 and all your apps.  After 6 months make the switch-over and then retire or rebuild or repurpose your current server.  Because of falling hardware prices, you can build two identical servers and keep one on ready-standby (off, but tested and updated once a month).

How much downtime can you afford?  How many Agony Units to build your server until it is functional?  With some of the new provisioning tools available, you can write some scripts to build a new server quickly.

Your superblock issue was the wakeup call.

---

### Post by Marc-NJ on 2015-03-15
All - thanks very much for the replies and information.

Turns out I'm not quite out of the woods yet, as my server crashed again last night and I'm guessing it's the same issue.  I definitely do want to move forward with a better solution, but have to plan it out (i.e. getting the new server, finding time to set-up Ubuntu Server 14.04 LTS on it, transitioning my data and applications, etc.), so I'm thinking for now the easiest course of action is to get a brand new hard drive and just image the data from the existing one to the new one (maybe using Clonezilla).  Does that make sense?

Thanks again!

---

### Post by SeijiSensei on 2015-03-15
The cheapest option I could price at Dell is a [T110]("http://configure.us.dell.com/dellstore/config.aspx?oc=bect12b2b&model_id=poweredge-t110-2&c=us&l=en&s=bsd&cs=04").  I doubled the memory to 8 GB and added a second 500 GB hard drive in a RAID1 configuration.  That costs just under $700.

Frankly since you already have a machine, I'd just install two new hard drives into it and set up a software RAID1 array using the Linux MD functionality built into the kernel.  I'd still replace the drive you have as it seems to be heading south.  If you have another drive lying around that is at least 20 GB in size, I'd install the operating system on that, then use two large drives to create a RAID1 and mount that as /home.

---

### Post by tgalati4 on 2015-03-15
Don't forget to check the power supply with a voltmeter or through the BIOS.  A failing PSU can cause disk hiccups that look like impending failure.

---

### Post by Marc-NJ on 2015-03-16
> **SeijiSensei said:**
> The cheapest option I could price at Dell is a [T110]("http://configure.us.dell.com/dellstore/config.aspx?oc=bect12b2b&model_id=poweredge-t110-2&c=us&l=en&s=bsd&cs=04").  I doubled the memory to 8 GB and added a second 500 GB hard drive in a RAID1 configuration.  That costs just under $700.

Frankly since you already have a machine, I'd just install two new hard drives into it and set up a software RAID1 array using the Linux MD functionality built into the kernel.  I'd still replace the drive you have as it seems to be heading south.  If you have another drive lying around that is at least 20 GB in size, I'd install the operating system on that, then use two large drives to create a RAID1 and mount that as /home.

The machine I'm using now for the Ubuntu server only supports one hard drive (I think), so I am planning to just get a replacement 2 TB drive (my current drive is 2 TB) and clone it - do you think that makes sense?  I believe I can also go even larger, but then during the clone process (or thereafter) I have to somehow expand my current partition to take advantage of the additional free space (which I recall was possible).

I actually have a several-years old HP desktop that was top-of-the-line when I bought it, and it already has 2 x 1 TB drives in it that I believe use some form of hardware RAID.  I was thinking of just using this machine at some point and swapping out the 1 TB drives for 2 or bigger TB drives (including the one I'll be purchasing shortly) and setting up this machine as my new Ubuntu 14.04 Server when I have the time.

Also - I know you recommended putting the OS on a separate drive, but was that just because you initially thought I was going to do software RAID and it made sense at that point, or is the OS always recommended to go on a separate drive (and if so, why?)?

Thanks!

---

### Post by Marc-NJ on 2015-03-16
> **tgalati4 said:**
> Don't forget to check the power supply with a voltmeter or through the BIOS.  A failing PSU can cause disk hiccups that look like impending failure.

I don't have a voltmeter unfortunately :(   How can I check the PSU through the BIOS?

Thanks!

---

### Post by SeijiSensei on 2015-03-16
> **Marc_Bressman said:**
> The machine I'm using now for the Ubuntu server only supports one hard drive (I think), so I am planning to just get a replacement 2 TB drive (my current drive is 2 TB) and clone it - do you think that makes sense?  I believe I can also go even larger, but then during the clone process (or thereafter) I have to somehow expand my current partition to take advantage of the additional free space (which I recall was possible).
Pretty much every PC I've ever seen supports at least four hard drives.  In the old days with IDE drives, there would be two motherboard connectors for ribbon cables supporting two drives each.  Machines with SATA should have four cable connectors.

> I actually have a several-years old HP desktop that was top-of-the-line when I bought it, and it already has 2 x 1 TB drives in it that I believe use some form of hardware RAID.
Some hardware RAID devices have good support in the kernel, others do not.  I'd try booting that machine from an Ubuntu Server DVD and see what it detects.  If Ubuntu doesn't see the drives, I'd give [CentOS]("http://www.centos.org/") a try as well.  

> Also - I know you recommended putting the OS on a separate drive, but was that just because you initially thought I was going to do software RAID and it made sense at that point, or is the OS always recommended to go on a separate drive (and if so, why?)?
It makes using software RAID more convenient.  If you have just the two drives, you'll need to set aside room on the first drive for the OS.  The second drive would then be partitioned so that it matches the first. You'd convert the two large partitions into RAID1 with the free space on the second drive available for other purposes.  I usually just back up the OS partition on the first drive to the equally-sized partition on the second.

---

### Post by Marc-NJ on 2015-03-17
So it turns out I'm in a worse spot than I thought.  I went out earlier today and bought a 4 TB drive figuring I would eventually set up 2 x 4 TB (with RAID) in a different machine for redundancy, but for the time being I'd use the 4 TB for my existing server set-up and just clone the data to it.  However, I didn't realize that my existing Ubuntu Server machine doesn't support UEFI and therefore doesn't support GPT (to allow for 2+ TB drives).  So my next step was just to clone images of the existing drive to a partition I created on the new drive so at least I'd have a backup.  However, most of the partitions from the existing drive failed to clone and stated the drives had errors preventing the clone process.

With no other option I could see left, I used GParted to run e2fsck with the -y switch, but after it finished I had a hundred or so files in the lost+found directory from who knows where.  At this point, it seems like my options are to try and clone the existing drive to a new 2 TB drive I buy, and then see if I can figure out where those lost+found files come from, or I can start the process to see if I can set up Ubuntu Server 14.04 LTS on that HP desktop that has hardware RAID (and get a second 4 TB drive for it).  

I do use a headless CrashPlan install on the Ubuntu server to back up my data, so it's apparently all safe in the cloud, although getting it back to me could take some time and/or money (either I have to download 500+ GB, or I have to pay around $170 for a drive shipped to me).  Plus, after I set up the Ubuntu server 14.04, I have to then figure out how to transfer over the backed up software (and associated data) to it.  I use things like ownCloud, ScreenConnect, and a few other things.

Anyway, looks like I have my work cut-out for me at this point, although at least now I'll be using RAID1 so hopefully this won't happen again.  

Anyone have any suggestions or advice regarding the above, or should I just get to it?

Thanks!

---

