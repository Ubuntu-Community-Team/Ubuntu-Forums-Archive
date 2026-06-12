---
title: "Advice wanted on upgrading"
date: 2014-02-23
forum: System76 Support
---

### Post by ShowMeGrrl on 2014-02-23
I switched from Windows XP to Ubuntu Linux for my desktop computer in 2010. I bought a robust Wild Dog from System 76. By and large, I have been very happy with the switch. There are so many things I love about Ubuntu Linux. I have Windows XP on a virtual machine for the few times i need to resort to Windows. (I've weaned myself off Quicken and switched to KMyMoney, so that was a major step away from Windows.)

Sooo, I have a System76 Wild Dog with Ubuntu 10.04 on it. As you no doubt know 10.04 is losing support. My versions of many programs (most notably, Open Office, Chromium browser, and KMyMoney) are outdated. I am getting to the point where I am thinking more and more about updating to the current Ubuntu version. But here are my hesitations:

1) I have never installed a Linux operating system. I can follow directions, including on the command line, but I'm far from being a confident, experienced Linux user. I would rather use my machine than tinker with it.

2) I keep thinking about the if-it-ain't-broke-don't-fix-it factor. My machine works and works pretty well right now. I worry that if I upgrade, I suddenly I will find the microphone doesn't work, the camera doesn't work, the ethernet doesn't work etc.
 
3) I worry that System76 customized my Ubuntu 10.04 so it would "match" the hardware on my Wild Dog -- the Nvidia graphics card, the CD-RW/DVD-RW drive etc.  How would I add in System76 "tweaks" to the new Ubuntu 14.04?

4) I worry about backing up all my data. I have years of data that I have been porting from old PC to new PC every five years. Using the wonderful program grsync, I back up my data just about every night to a Western Digital external drive. If I were going to upgrade my desktop, I would do a clean install (exactly how I would do that, I don't know) and thus would be (I'm guessing) wiping my data off my PC. My lone copy would be on this external drive. I worry that I would hook the external drive up to the new OS and it would say something alarming like "I don't accept your partitions" or "I don't accept your file system, please reformat."  I worry, in short, about losing my data.

Here are the specs for my Wild Dog: 
Graphics 1 GB nVidia GeForce GT240
Memory 8 GB - 4 x 2 GB - DDR3 - 1333 MHz
Operating System Ubuntu 10.04 (Lucid Lynx) 64 Bit Linux
Optical Drive CD-RW / DVD-RW
Processor Intel Core i7-860 2.80 GHz L2 8 MB DMI 2.5 GTs - 4 Cores with Hyperthreading
Storage Options 1 TB SATA II 300 Mbps – 7200 RPM 32MB Buffer
No Wireless -- I connect to the Internet via ethernet cable.

I am looking for advice on 1) Should I upgrade or wait the two years until I plan to buy a new desktop PC?  and 2) If I upgrade, how do I go about it and avoid some of the things I'm worried about?

Thanks for your help,

Jane

---

### Post by sudodus on 2014-02-24
I think you are better prepared for an upgrade or fresh install than most people.

0. If you want to be even better prepared, go get a second external HDD, and make an extra backup, for example a cloned image of the internal drive and keep it there. You can use Clonezilla for that purpose. Alternatively you can have the same information on both external drives made with grsync. (Anyway it is possible to have double security, with one of the backup drives in another house in case of fire).

The specs of your computer show me that it will run well with any of the current Ubuntu versions (12.04 LTS or 13.10) and flavours Lubuntu, Xubuntu, standard Ubuntu and Kubuntu. I recommend 12.04 LTS because it is well debugged and polished and has long time support until April 2017. Maybe you can take the next step in August to version 14.04 LTS, which by that time should be reasonably well debugged (four months after the release).

I suggest that you try a few of the Ubuntu flavours live. Download the iso files, test the md5sum, make a USB boot drive and try each of them without installing until you find what you like. Ask questions here if you have need a proprietary driver for the nvidia card and have problems installing it. But my experience is that 12.04 LTS is better running nvidia cards with the built in nouveau driver (than 10.04 LTS).

1. If you are happy with Ubuntu 12.04 LTS, you can try upgrading directly from 10.04 LTS:

- update/dist-upgrade 10.04 LTS
- upgrade to 12.04 LTS with the upgrading tool.

It usually works but is risky, so if you have problems, rely on the backup.

2. You can also keep your /home directory and use it as a separate home partition in an otherwise fresh install of 12.04 LTS

3. or (of course) make a completely fresh install and afterwards restore your personal data and tweak the system.

---

### Post by ShowMeGrrl on 2014-02-24
> **sudodus said:**
> I think you are better prepared for an upgrade or fresh install than most people.

0. If you want to be even better prepared, go get a second external HDD, and make an extra backup, for example a cloned image of the internal drive and keep it there. You can use Clonezilla for that purpose. Alternatively you can have the same information on both external drives made with grsync. (Anyway it is possible to have double security, with one of the backup drives in another house in case of fire).

The specs of your computer show me that it will run well with any of the current Ubuntu versions (12.04 LTS or 13.10) and flavours Lubuntu, Xubuntu, standard Ubuntu and Kubuntu. I recommend 12.04 LTS because it is well debugged and polished and has long time support until April 2017. Maybe you can take the next step in August to version 14.04 LTS, which by that time should be reasonably well debugged (four months after the release).

I suggest that you try a few of the Ubuntu flavours live. Download the iso files, test the md5sum, make a USB boot drive and try each of them without installing until you find what you like. Ask questions here if you have need a proprietary driver for the nvidia card and have problems installing it. But my experience is that 12.04 LTS is better running nvidia cards with the built in nouveau driver (than 10.04 LTS).

1. If you are happy with Ubuntu 12.04 LTS, you can try upgrading directly from 10.04 LTS:

- update/dist-upgrade 10.04 LTS
- upgrade to 12.04 LTS with the upgrading tool.

It usually works but is risky, so if you have problems, rely on the backup.

2. You can also keep your /home directory and use it as a separate home partition in an otherwise fresh install of 12.04 LTS

3. or (of course) make a completely fresh install and afterwards restore your personal data and tweak the system.


Thank you, Sudodus. Very helpful. I guess I will wait until August to do the 14.04 LTS. If I'm going to go to the risk and hassle of upgrading, I might as well get the most current LTS version.

I should clarify that my "backup" is just my Home dir including hidden files but minus Virtual Box and some Google and Gwibber files that take forever to backup. Is that backup sufficient if I wipe my entire disk for a clean install?

That is a good suggestion to get a second external HDD. I will do that. And then I guess I'll do a cloned drive there. I know nothing about Clonezilla, so that will be a learning experience.

I am assuming the process would be: 

1. Wipe the existing HDD (which has two partitions, an ext4 and an ntfs used by my Virtual Box Windows XP). 

2. Do a clean install of 14.04 LTS

3. Install new app programs (such as KMyMoney, Libre Office, Thunderbird, Chromium etc.)

4. But what do I do about my backup? I assume I don't want to just copy it lock-stock-and-barrel into the new HOME dir, because the backup contains all those hidden files from the OLD programs. So does this mean I should individually copy-and-paste my personal data files and folders over to the new install?

---

### Post by untrustytahr on 2014-02-24
Sudodus has provided you with pretty solid information.  There are one or two points that I would add.

You didn't say what type of virtualization software that you were using.  You might want to create a clone of the virtual disk image.  How that is done depends on what application you're using (vmware, virtualbox, xen, etc...) and what verision.  After you restore it, the safest bet is to turn off the network interface if you are going to continue using it for the applications that only use Windows.  The reason for turning them off is you don't want 'the outside world' to be able to reach it since it won't receive security updates anymore.  If the network connection stays on and the computer becomes compromised, it could be used to island hop your network.

I'm not familiar with grsync.  A quick look seems like it's just rsync-ing the files which is fine.  Some backup programs use specialized formatting (deja dup/duplicity) that could be problematic.  You really can't go wrong with good 'ol TAR on the home directory and put the tar file on an external HD/stick/sd card depending on it's size if you're a super-paranoid, double security, type-A personality :)

finding out the size of home directory:

sudo du -h --max-depth=0  /home

That will give you an idea of the size medium you would need for the tarfile.  It's probably easiest to tar the entire home directory but that would also copy alot of the hidden config settings for the applications you run.  You can also just tar your data files in particualr directories (i.e Documents, Pictures) since your new applications might have very different technologies/config settings since version 10.

I like the idea of trying the Live version first.  That allows you to see what hardware issues you might have before actually making any changes.

The tweaks should be handled by the system76 driver (with the possible exception of the nividia card) which might require manual installation ([http://knowledge76.com/index.php/Restoring_Your_System#Important_information_about_Proprietary_Graphics.21](http://knowledge76.com/index.php/Restoring_Your_System#Important_information_about_Proprietary_Graphics.21))  I don't have one to know.

You seem fairly well prepared as sudodus said.  The only thing that gave me pause is where you said:
I would do a clean install (exactly how I would do that, I don't know) and thus would be (I'm guessing) wiping my data off my PC...

but you asked the 'right questions'.  You should never 'guess' if you're wiping your data. ;)  Clean install typically means you'll be removing the partitions/filesystems and installing a entire new system.  Yes, that would destroy what's there (and most install programs would warn you first).

---

### Post by untrustytahr on 2014-02-24
Well, it looks like you responed while I was typing a response.
FWIW, if you are going to get a second drive, why not just get an internal one and swap them out?  That way if chaos strikes, you can just put the old one back in and you're back where you started.  Once you're happy with the new install, you can put the old drive back in wipe it and have a second drive for space.

---

### Post by ShowMeGrrl on 2014-02-24
> **untrustytahr said:**
> Sudodus has provided you with pretty solid information.  There are one or two points that I would add.

You didn't say what type of virtualization software that you were using.  You might want to create a clone of the virtual disk image.  How that is done depends on what application you're using (vmware, virtualbox, xen, etc...) and what verision.  After you restore it, the safest bet is to turn off the network interface if you are going to continue using it for the applications that only use Windows.  The reason for turning them off is you don't want 'the outside world' to be able to reach it since it won't receive security updates anymore.  If the network connection stays on and the computer becomes compromised, it could be used to island hop your network.

I'm not familiar with grsync.  A quick look seems like it's just rsync-ing the files which is fine.  Some backup programs use specialized formatting (deja dup/duplicity) that could be problematic.  You really can't go wrong with good 'ol TAR on the home directory and put the tar file on an external HD/stick/sd card depending on it's size if you're a super-paranoid, double security, type-A personality :)

finding out the size of home directory:

sudo du -h --max-depth=0  /home

That will give you an idea of the size medium you would need for the tarfile.  It's probably easiest to tar the entire home directory but that would also copy alot of the hidden config settings for the applications you run.  You can also just tar your data files in particualr directories (i.e Documents, Pictures) since your new applications might have very different technologies/config settings since version 10.

I like the idea of trying the Live version first.  That allows you to see what hardware issues you might have before actually making any changes.

The tweaks should be handled by the system76 driver (with the possible exception of the nividia card) which might require manual installation ([http://knowledge76.com/index.php/Restoring_Your_System#Important_information_about_Proprietary_Graphics.21](http://knowledge76.com/index.php/Restoring_Your_System#Important_information_about_Proprietary_Graphics.21))  I don't have one to know.

You seem fairly well prepared as sudodus said.  The only thing that gave me pause is where you said:
I would do a clean install (exactly how I would do that, I don't know) and thus would be (I'm guessing) wiping my data off my PC...

but you asked the 'right questions'.  You should never 'guess' if you're wiping your data. ;)  Clean install typically means you'll be removing the partitions/filesystems and installing a entire new system.  Yes, that would destroy what's there (and most install programs would warn you first).

Thanks, more good info!

I like the idea of a TAR of the Home dir to a new external HDD.  Is there a limit on the size of a TAR?  I mean a limit other than the capacity of the hard drive to which I would copy it? My Home dir = 422GB. Is that too big to TAR?

Another question: Where do I find the data that is in my Windows XP? I mean obviously I can find the data from WITHIN Windows XP when I am running Virtual Box. But I mean can I access that WindowsXP data from outside the Virtual Machine? Where does it reside? Or am I asking the wrong question?

Microsoft's ending of support for Windows XP is another reason to upgrade. Good suggestion to turn off the network on it when the support stops. I am thinking that I might not install any version of Windows on my 14.04, though it will mean I have to get a new scanner, because Linux does not support my scanner.

So my questions:  A limit on size of a TAR?  And where does the personal data for my Windows XP on Virtual Box reside? Can I access it from outside Virtual Box?

---

### Post by ShowMeGrrl on 2014-02-24
> **untrustytahr said:**
> Well, it looks like you responed while I was typing a response.
FWIW, if you are going to get a second drive, why not just get an internal one and swap them out?  That way if chaos strikes, you can just put the old one back in and you're back where you started.  Once you're happy with the new install, you can put the old drive back in wipe it and have a second drive for space.

That's a great thought! The only problem is I have never installed an internal drive. In fact, I've never installed anything in my box. I am rather terrified to do anything like that. Is it easy and safe to do?

---

### Post by untrustytahr on 2014-02-24
> **ShowMeGrrl said:**
> So my questions:  A limit on size of a TAR?  And where does the personal data for my Windows XP on Virtual Box reside? Can I access it from outside Virtual Box?
I had to look these sizes up can't guarantee it's validity...
 
tar doesn't have a realistic size limit (2^63-1) bytes total size... don't even know what it's called.  No individual file within tarball larger than ~ 68GB
 
The filesystem also needs to be able to handle the file sizes.  Ext4 - > 16TB,  NTFS - > 16TB.  Fat32 won't work because it doesn't do >4GB.
 
As for your XP data, it depends how you setup the virtual machine.  If you chose the default settings when setting up the vm, then they will be contained within the .vdi file in your home directory.  You wouldn't read them directly.  They are read from within Virtualbox which is why I suggested cloning/exporting your vm.

---

### Post by untrustytahr on 2014-02-24
> **ShowMeGrrl said:**
> That's a great thought! The only problem is I have never installed an internal drive. In fact, I've never installed anything in my box. I am rather terrified to do anything like that. Is it easy and safe to do?

Adding/Removing hard drives isn't difficult at all.  It can be scary if you've never done it, but it's not difficult.  The internet is loaded with videos and articles on how to do it.  Just remember to unplug the electricity from the box and discharge any static electricity on you before touching it.  If you don't think you'll remember how to put things back together, take some pictures with a camera before you disassemble anything.

---

### Post by sudodus on 2014-02-25
> **ShowMeGrrl said:**
> Thank you, Sudodus. Very helpful. I guess I will wait until August to do the 14.04 LTS. If I'm going to go to the risk and hassle of upgrading, I might as well get the most current LTS version.

I should clarify that my "backup" is just my Home dir including hidden files but minus Virtual Box and some Google and Gwibber files that take forever to backup. Is that backup sufficient if I wipe my entire disk for a clean install?

Only you can answer that question. If that backup contains what you need it is sufficient, otherwise not.
> 
That is a good suggestion to get a second external HDD. I will do that. And then I guess I'll do a cloned drive there. I know nothing about Clonezilla, so that will be a learning experience.

*untrustytahr* gave you some other options how to use an extra HDD. Use it the way you think best :-)
> 
I am assuming the process would be:

0. Backup your data and *verify* that you have a good backup
> 
 1. Wipe the existing HDD (which has two partitions, an ext4 and an ntfs used by my Virtual Box Windows XP). 

2. Do a clean install of 14.04 LTS

You can upgrade stepwise between LTS versions (10.04 - 12.04 - 14.04). But a clean install is cleaner and more likely to succeed.
> 
3. Install new app programs (such as KMyMoney, Libre Office, Thunderbird, Chromium etc.)

4. But what do I do about my backup? I assume I don't want to just copy it lock-stock-and-barrel into the new HOME dir, because the backup contains all those hidden files from the OLD programs. So does this mean I should individually copy-and-paste my personal data files and folders over to the new install?

Do what I suggested in my first post (post #2), try with a /home partition using your old /home directory. It is a shortcut, that may or may not work. Otherwise you have to do it manually as you describe.

---

### Post by coldraven on 2014-02-25
> but minus Virtual Box and some Google and Gwibber files that take forever to backup.
That may be because you are trying to back-up files that are bigger than 4GB to a drive that is formatted as FAT32.
The solution would be to buy another external drive and use gparted to format it to ext4 or NTFS. You would then be able to copy large files over.

As already mentioned the simplest solution would be to just put a new drive into your machine. Then put the old drive into a cheap enclosure so that you can always access your data, presuming that it's not encrypted.
I put a bigger drive into this laptop, it was easy and took 10 minutes.

---

### Post by MoebusNet on 2014-02-25
@ShowMeGrrl: I don't think anyone has suggested that you try out a Live-DVD or Live-USB copy of Ubuntu yet. This would allow you to verify hardware compatibility wthout making changes to your present hard drive; you simply boot from the Live-version and try it out. Also, I think the separate System76 drivers have been rolled into 12.04.4 by now - it would still be a good idea to try out the Live version first to make sure.

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD) (this was written before the iso images were too big to fit on a CD; they fit on a DVD now. The priciples are the same, though.)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) (this talks about installation mainly, but also talks about running Ubuntu from USB without installing.)

[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver) (these drivers are usually rolled into Ubuntu as it is updated.)

Hopefully this will give you an option to help your decision about upgrading.

---

### Post by sudodus on 2014-02-25
> **MoebusNet said:**
> @ShowMeGrrl: I don't think anyone has suggested that you try out a Live-DVD or Live-USB copy of Ubuntu yet. This would allow you to verify hardware compatibility wthout making changes to your present hard drive; you simply boot from the Live-version and try it out.

... I did in post #2, but it is worth mentioning again :-D

---

