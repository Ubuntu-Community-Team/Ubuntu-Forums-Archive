---
title: "Starting a new server from an old one - help please!"
date: 2016-02-18
forum: Server Platforms
---

### Post by david472 on 2016-02-18
I lost a RAID server in the last little while so now I am going to start over.
0) The system has three drives (2 x RAID and one for the OS)
1) I have two hard drives (exactly the same 1TB WD x2).
2) One is brand new never been formatted
3) The second drive is one that I tried to resurrect the old server with, so I am guessing it has RAID info on it, but it never mounted)
4) How much RAM do I really need - right now I have 2gig?

Do I need to format any or all of the drives before starting?

What is my next step?  Thank in advance

---

### Post by darkod on 2016-02-18
1. On the brand new HDD you will need to create identical partitions in size as on the other raid member. DO NOT format these partitions, mdadm uses the partitions and the filesystem is on the /dev/mdX devices (arrays).

2. The disk that was part of raid probably has superblock metadata on it, so you will have to zero the superblock on all partitions of that disk. After that you can use mdadm and create the new array(s).

3. 2GB of memory is enough for ubuntu server to run correctly. For any high loads you would need more, but for basic home server that will be just fine to start with.

That should be it. You can create the raid during installation or later because the OS will be on a separate disk anyway. You can install the OS and create the raid later, it's up to you...

---

### Post by david472 on 2016-02-18
Ok, so ...

1) do I need to format the original OS drive?
2) I want to start over, so I don't care about the old RAID info or partition, how to I do brand new on this?
3) What should I download for the server?

---

### Post by darkod on 2016-02-18
1. Yes, better to format it so that all old data is gone. You can do that with the installer.
2. Formatting the new array(s) will delete all the data anyway, so don't worry about that. However, depending what you want to do, you can keep the partition layout on the old raid disk and create identical layout on the new disk too, or remove the old partitions completely and make new partitions on both raid disks. But that means partitioning two disks instead of only one so if you intend to use the same raid layout as before it makes no sense to destroy the partitions on the old disk too. Does that make sense? :)
3. The Ubuntu Server 14.04 LTS version, the 64bit (amd64). [http://releases.ubuntu.com/trusty/](http://releases.ubuntu.com/trusty/)

Actually the new LTS (16.04) comes out in two months but right now 14.04 is still the latest LTS version available. That ISO burned to a CD is all you need. Alternatively you can install from USB stick...

---

### Post by david472 on 2016-02-19
Well, the original 1TB drive (call it drive A), is still intact ,but it never mounted.  I have put that 1TB drive A aside and I am not using it for this.  Consider it a paper weight.

The second drive in the array (Drive B) was new and was used in an attempt to fix the server.


The two other drives
1) 1TB brand new 
2) 1TB drive B (that was used in attempt to resurrect the server )

I am thinking that maybe it is better to start over and remove everything? Yes no?

Should I use the USB drive to install UBUNTU server?  Is that going to be the best option?

---

### Post by darkod on 2016-02-19
USB or CD depends entirely on you... What ever you feel more comfortable with and you have access to.

As for removing everything, that's a good option too. Go for it...

---

### Post by TheFu on 2016-02-22
After reading everything, the only answer to the questions I have is ... "**it depends**."

Should you format the disks?  **It depends**.  Completely up to you and whether any data on those drives is desired or not.  If you aren't positive about the installation wiping things, then I'd delete the partitions and recreate them.

Is 2G enough RAM?  **It depends**.  I have "servers" with 384MB of RAM that don't swap at all.  Then there are other servers doing geospatial stuff that swap with 32G of RAM.  The purpose matters.  The workload matters. A typical home file server would use most of the RAM after 512MB as disk buffers which will speed up file transfers. Not a bad thing at all.

For home users, backups are 100x more important than RAID.  Be certain you have backups working before screwing around with RAID. Please. Of course, if this is just a play box and the data doesn't matter, then even backups are an "it depends" answer. ;)

Specific questions with appropriate background data get the best answers.  It is hard to know what to provide when just starting out and it is hard for me to ask for more details with such a wide list of possibilities for a "home server."  Guess **that depends** too. ;)

---

### Post by david472 on 2016-02-23
Ok so I have downloaded the new server files  and I have a blank USB.  How do I install the server to USB first?

---

### Post by TheFu on 2016-02-23
There are 50 ways, assuming the "new server files" is an ISO file.

dd  <--- the way I do it
mkusb <---- the easy way on Linux
yumi  <---- the easy way on Windows; allows multiple ISOs to be installed on a single USB for booting
unetbootin <--- many people use this successfully, but I have **never** gotten it to work the way I want.
All depends on what you want.  BTW, if you learn by watching, there are lots of youtube videos about this stuff and there's a walk-through for most Ubuntu installs.

Please realize that "server" won't have any GUI, so if you expect a point-n-click setup, that doesn't happen. Perhaps a desktop ubuntu would be better? I only mention this because of the last question. Most server admins would know how to create a bootable flash drive in their sleep.  Nothing hard about it but it is a basic skill easily mastered.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) might be helpful. It explains those commands above in more detail.

---

### Post by david472 on 2016-02-23
Ok I have created a startup USB from the previously running Ubuntu server - but that server is now kapput.  So I am going to have to create the USB start up from windows -so I am going to be using YUMI it looks like.

I have the server files on the USB, but I am suddenly asking myself the question - is the USB now the Bootdisk or is it just used for installing the software on a HD inside the machine?

---

### Post by TheFu on 2016-02-29
> **david472 said:**
> I have the server files on the USB, but I am suddenly asking myself the question - is the USB now the Bootdisk or is it just used for installing the software on a HD inside the machine?

I don't know what "server files on the USB" means. Is that from creating an install from an ISO or did you just copy some files over?

The more exact you are with your information, the better help we can be.

---

### Post by david472 on 2016-03-01
I used the YUMI program to put the server files on the USB.

---

### Post by TheFu on 2016-03-01
> **david472 said:**
> I used the YUMI program to put the server files on the USB.

Thanks.  That is clear.

Normally, this is called "creating a flash install drive" or "making a bootable flash drive."

You must install this onto some other media, usually a HDD or SSD to make a "server."  Some desktop versions of Linux will let you try out the OS using these flash drives without installing anything, but performance will be poor.

---

### Post by david472 on 2016-03-03
I came across something no one has talked about yet in the process of installing - it says it needs a http proxy or something?  What should I put in here?  I am at home and going from memory...any ideas?

---

### Post by TheFu on 2016-03-03
If you need a proxy, then fill that out.
If you don't need a proxy, ignore it.  I've never needed to enter a proxy server from a home ISP, but always need to provide it at work.

---

### Post by david472 on 2016-03-04
I am not sure what it wants from me.  What does the proxy do?

It is telling me that ONE OR MORE drive containing serial ATA RAID configuration. Do you wish to activate them?
One of the drives has some stuff on it, but I want to start over and have a fresh install on everything --- how should I proceed?

---

### Post by darkod on 2016-03-04
Then say No. It finds traces of raid on the disks, some of them have been used in raid before. If you want to start fresh, ignore it and say No to activate.

Then do the partitioning as you wish...

Are you using raid on that machine? Because if you are, and if it's fakeraid, then you might need to activate it so it can use the arrays.

---

### Post by david472 on 2016-03-06
IT is a software RAID, I believe DMRAID or something?
Also for the partitioning - I am not sure which to pick?  The RAID is going to have video files on it (2x 1TB drives), and nothing else.

---

### Post by darkod on 2016-03-06
If it uses dmraid most probably it is fakeraid (bios raid), without dedicated HW raid card. In that case it's better to use mdadm SW raid rather than that. If you can disable the raid in the raid bios and just use something like JBOD (to pass the disks directly to the OS without creating any raid).

Then during the installation of ubuntu server you can configure mdadm SW raid.

If you want, you can use the dmraid fakeraid but that's neither HW nor SW raid, something in between. More messy and less flexible. It's up to you...

---

### Post by david472 on 2016-03-07
Ok, here is where I am at.  The last stuff went over my head - I am trying to start over Darko, so I hope I have followed all the steps right so far.  Not sure if I can go back now.
[IMG][IMG]http://i66.tinypic.com/28tj9qd.jpg[/IMG][/IMG]

---

### Post by darkod on 2016-03-08
First, you can always go back. You don't even have the OS installed yet. :) You can always start again...

This is a very strange setup. Did you configure that raid device #126 or that's traces from old SW raid?

Also I am confused about your disks shown. I see sda (the usb stick), then sdc and sdd. But no sdb. There should be one because bios reports them in order and if there are sdc and sdd usually there should be sdb too.

From what is shown I see only one 1TB disk. So where is the other one to create raid from them?

Did you disable raid in the bios? If you use SW raid you need to disable raid in the bios so that the built-in controller does not do anything. And if you had tried using the bios raid earlier you might need to clean the disk(s) from remains of metadata.

---

### Post by david472 on 2016-03-08
IT is the remains of an old computer :
-250gig hard drive was the original boot drive with the old server
-1gig usb with the server YUMI software on it
-1TB Brand New unformatted
-1TB Brand New, but was used to try and save the old server so there must be information on it of some sort

---

### Post by darkod on 2016-03-08
It still leaves many questions unanswered. Most important, is bios raid disabled or not???

sdd is probably the new unformatted disk. You see how it doesn't show any partitions or free space below it. Because it has no partition table at all.

But all of that still doesn't explain why the other 1TB disk is not shown. I wonder if it's best to boot the machine with ubuntu desktop live cd/usb into live mode, and look around before starting the server install.

That's why I would do:
1. Make sure in the motherboard bios that raid is off/disabled.
2. Boot the machine in live mode and check disks with:
```
sudo blkid
sudo parted -l (that's small L)
```

If you post the output of that we will have a better picture.

---

### Post by david472 on 2016-03-08
RAID BIOS : I won't know until I get back to it, I am at meeting all day and gathering as much info as I can until I can get back to it. The person that used to run the server said it is SW raid so he doesn't know why it would be enabled.
I am not sure why the 1TB is not showing.  It was the one that I was using to attempt to fix the older server with.  I hope nothing has happened to it because of that attempt.
How do I boot into live mode?  How do I get to a shell from where I am so I acn enter in those commands?

---

### Post by darkod on 2016-03-08
Use the ubuntu desktop iso to make the desktop live cd/usb and use the Try Ubuntu option when booting with it. It will boot live mode. After that simply open Terminal and you can type commands and copy/paste their output.

---

### Post by TheFu on 2016-03-09
> **david472 said:**
> I am not sure what it wants from me.  What does the proxy do?

[https://en.wikipedia.org/wiki/Proxy_server](https://en.wikipedia.org/wiki/Proxy_server) - most people using proxies at home would know it because they either set it up or paid for a service.  At work, I hope that a proxy is required. IMHO, any work site that doesn't mandate a proxy for all outbound traffic is foolish and on the low-end of a security conscious company.

I agree with Darkod about RAID. Use Linux SW RAID. There are very few reasons to use FakeRAID. I cannot think of any reasons that I would ever use it.

If the machine doesn't have any data on it, I don't understand all the caution. You cannot harm anything.  Do 15 different installs and try all the options.  Nothing teaches like trying things out for yourself and seeing what happens. Nothing to lose.  Go play with the box.  It will be faster learning than all the back-and-forth here. It has already been 2 weeks. There are lots of youtube walk-thru videos on installing Ubuntu server.  Watch a few of those, if you learn that way.  There is also an ubuntu server manual ... [https://help.ubuntu.com/lts/serverguide/serverguide.pdf](https://help.ubuntu.com/lts/serverguide/serverguide.pdf)   Might be of some help.

---

### Post by david472 on 2016-03-09
Thanks for the response.  I do understand I have some learning to do, but I find it is typical with most thing that experts understand almost everything - but it is the little steps trip up the novice user, hence why it is taking a long time. I appreciate everyone's patience! 
*  Also, I only have 1 hour or less each day to work on this thing so that makes it more difficult as well...

Darko, I made a boot CD for Ubuntu only to find out there is no CD tray in the computer.  To complete the commands you asked, I will have to set up a USB boot tonight.
Darko, I went into the BIOS and deleted the RAID that was already on one of the disks.  But I did check out this screen here:
[IMG]http://i66.tinypic.com/2dtwyhl.jpg[/IMG]

It gives me options for the RAID, but does not say "NO RAID", so I left it as it stands.
I am experimenting with partitions - I picked the first one - and it asks me to delete the previous partition, which I did.
I am in the middle of the first partition, which I assume is on one disk at a time?  I will have to do the same for the other disk after this one.  

I was looking up Software RAID videos, but one I was hoping for, looks like it is using the TWO RAID DRIVES as a boot drive as well.  Not my setup.  Video here :[https://www.youtube.com/watch?v=z84oBqOxsD0](https://www.youtube.com/watch?v=z84oBqOxsD0)
Does the SW raid require I do it manually?

---

### Post by darkod on 2016-03-09
According to that image, the best option is the factory default of RAID Autodetect / AHCI. It says raid will be detected if present, otherwise it uses plain AHCI mode which is what you need.

The RAID On option says it will configure raid on every boot. Which is not what you want.

As for the video, just ignore the part where he sets up raid array as root partition, and focus on how he does the raid. You will install the OS on the 250GB disk and no problem.

---

### Post by david472 on 2016-03-09
But knowing how clueless I am on this, which part is where he sets up the raid as a root partition?  How much should I miss?
PS - stopped the partitioning I was doing and started over.  I guess it is nice knowing that is nothing i can really ruin at this point.

Well, I guess I can ruin something, it does not boot to YUMI anymore from the USB!  This is after I stopped the partition and changed the BIOS to [COLOR=#000000]RAID Autodetect / AHCI[/COLOR].  It is booting to the 250 gig hard drive, even though I have it should be booting to USB FIRST in the BIOS.  Very frustrating!

---

### Post by TheFu on 2016-03-09
> **david472 said:**
> Thanks for the response.  I do understand I have some learning to do, but I find it is typical with most thing that experts understand almost everything - but it is the little steps trip up the novice user, hence why it is taking a long time. I appreciate everyone's patience! 
*  Also, I only have 1 hour or less each day to work on this thing so that makes it more difficult as well...
 
Does the SW raid require I do it manually?

I've been running Unix systems since the early 1990s - wouldn't call myself an expert. Think I know about 10%.  Kept trying to do things the Windows way for years and was always frustrated. Eventually, I gave in and learned the Unix way - became much happier and finally the genius of the system architecture "clicked" for me.  Haven't looked back since, but it did take a few years of daily, constant, use.

Does SW-RAID require manual setup?  I've never done it any other way, except manually. Don't know if there is another way that actually works, but I've never tried.).  This is a Linux server and "manual" is the name of the game.  Nothing good is "automatic", I'm afraid.  Even when there are automatic methods, I find they don't do what I want/need, unless I created the automatic method myself (usually using something like a bash script or ansible).

My 1st 5 minutes on a server: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) - might be helpful, though not about RAID or running 1 server. The key is to take good notes and make a reproducible process.  If you need photos, fine. Whatever works.

---

### Post by darkod on 2016-03-09
> **david472 said:**
> But knowing how clueless I am on this, which part is where he sets up the raid as a root partition?  How much should I miss?
PS - stopped the partitioning I was doing and started over.  I guess it is nice knowing that is nothing i can really ruin at this point.

Well, I guess I can ruin something, it does not boot to YUMI anymore from the USB!  This is after I stopped the partition and changed the BIOS to [COLOR=#000000]RAID Autodetect / AHCI[/COLOR].  It is booting to the 250 gig hard drive, even though I have it should be booting to USB FIRST in the BIOS.  Very frustrating!

In linux each partition or SW raid device has to have a mount point to be used. In the partitioning step, when you select a partition or md raid device, you can then select which filesystem you want to use on it (for example ext4) and which mount point to mount it on.

The partition or md device that you set with mount point / is where the OS will be installed. That's how you know...

Changing the SATA mode to AHCI should not affect usb booting. Double check if the usb is still bootable (cna you boot another machine with it?) and try again. Also if the machine has quick boot menu I often use that instead of switching bios boot options. Much faster and many computers have it years ago. But anyway the usb booting should work if the usb is still ok.

---

### Post by david472 on 2016-03-09
Yep the USB is still ok, I used it prior to halting the installation (but maybe it got corrupted then, who knows). I am going to have to reinstall the Server on the USB tonight along with YUMI.
Unfortunately, it is now booting directly to the 1/2 completed installation of the ubuntu server 14.04.4.  Booting to the 250gig hard drive, sheesh.  Not sure why.

I think I should reformat the old drives to ensure there is nothing on them.  Can I do this in Windows or do I have to do it in Ubuntu?  I am only doing it to get rid of the information, I know I am going to be reformatting it once it gets back into the server.

---

### Post by darkod on 2016-03-10
Like TheFu said short while ago, you are overthinking it. Espeacially since you say you don't have much time daily to dedicate to this project, I would use that time more efficiently.

Yes, you can format the disks in advance but there is really no need. The installer allows you total control and in the partitioning step you can do all needed actions. Formatting on windows is not helping you at all because windows by default will create ntfs partitions that you will not use. So you would have to repartition anyway.

The installer does not care if there is data currently on the disks. Just start the installation and that's it. In the partitioning step if you highlight the disk (like /dev/sdd) and hit Enter it will ask you if you want to create new blank partition table. Select msdos (that is the most used one for disks up to 2TB) and it will remove all current partitions. Then you can create new ones in the free (unpartitioned) space.

You also commented that you can't boot the usb installer now. That would be more important to solve instead of formatting the disks. Because you need to boot the installer process to install... :)

I am more worried why /dev/sdb does not show currently. If it continues like that, you will have to create ubuntu desktop (not server) on the usb and boot into live mode like I mentioned, so you can take a look at the disks what's going on.

---

### Post by david472 on 2016-03-10
I am thinking about spending the $30 bucks and getting this hardware RAID controller:
[http://www.canadacomputers.com/product_info.php?cPath=48_19_918&item_id=021549&sid=s9nr954g5n49sd2o7ine4ldng5](http://www.canadacomputers.com/product_info.php?cPath=48_19_918&item_id=021549&sid=s9nr954g5n49sd2o7ine4ldng5)
This way, I am not using FakeRaid or even a software RAID.  It is cheap enough that I don't mind considering I am not getting reimbursed.

---

### Post by TheFu on 2016-03-10
Don't - just don't.   A useful RAID controller runs $200+.  Anything less is EOL and will likely only be supported by very old Linux kernels, if supported at all. The link doesn't say anything about Linux support.  I've been burned. Please learn from this.

Lots of sub-$200 "raid controllers" are fake-RAID. Beware.

Probably want an LSI controller (3ware was bought by LSI) to avoid the hassles.

RAID is for HA (High Availability) or Performance.  Any other need can be solved better, with less hassle, and cheaper without RAID.  High performance SW-RAID can be accomplished using a nice JBOD controller - something like a Supermicro AOC-SAS2LP-MV8 (US$111 on Amazon).

---

### Post by david472 on 2016-03-10
Well, thank you for that.  I guess I will just go the SW raid route then.

---

### Post by TheFu on 2016-03-10
If you want to know the performance - there's a tool for that. bonnie++  There's also f3 for flash drive testing.

Glad to have helped.

---

### Post by david472 on 2016-03-10
Well, today I am going to try it again.  I reformatted the USB drive with the newest version of ubuntu server and put YUMI on it.  I only wish that YUMI had a LIVE option so I could go in and run Ubuntu from memory.

---

### Post by TheFu on 2016-03-10
> **david472 said:**
> Well, today I am going to try it again.  I reformatted the USB drive with the newest version of ubuntu server and put YUMI on it.  I only wish that YUMI had a LIVE option so I could go in and run Ubuntu from memory.

It isn't Yumi - it is "Ubuntu Server" with the limitation - you can load both Ubuntu Server and Ubuntu desktops and 20 other Linux distros onto the flash drive using Yumi, BTW.  Some support live-boot and others are only installers.  Yumi is a multi-boot creation tool.

Also - I wouldn't load the "latest server" - it isn't LTS, therefore is isn't worth my time.  LTS gets 5 yrs of support. All other releases get 6-9 months, hence "not worth my time."

---

### Post by david472 on 2016-03-10
Well, I am back to the partition stage.  I can't tell which drive I am partitioning here?  This is also the place it tells me to do it manually, should I skip the rest and just try the manual route?
[IMG]http://i65.tinypic.com/34xnczb.jpg[/IMG]

---

### Post by darkod on 2016-03-11
As you can see, the names of the disks are in parenthesis. That first line says (sdb). But you definitely want the Manual option for more control and especially if you want to set up the raid during install.

Note that because your OS will not be on the raid, you can install only the OS first (ignore raid) and set up the raid later when you have the system running. It is your choice when you do it...

---

### Post by david472 on 2016-03-11
Oh man, I was all set to start with the raid...ok.  Back to the start. 

USed : LVM partitioning
Picked : OpenSSH server because it told me it was the best option here [http://www.tecmint.com/ubuntu-14-04-server-installation-guide-and-lamp-setup/](http://www.tecmint.com/ubuntu-14-04-server-installation-guide-and-lamp-setup/)

Followed the instructions, finished the installation and rebooted...
Here is what happened 
1) The instructions clearly say to remove the USB installation device and reboot after the GRUB bootloader.  Did it and rebooted
2) Changed the sequence in the BIOS so it would not boot from USB and instead boot from the newly installed 250gig ubuntu server drive.
3) It doesn't boot and hangs on start up.  It tells me it is initializing boot agent and just hangs. The drive is shown in the bios, but refuses to boot to it.  Sigh.  Going to try and install again and see what happens...
4) Inserted the USB again to reinstall
5) rebooted and set the usb as one of the bootup sequence
6) It goes to the SHELL of ubuntu server with GRUB startup - weird?  Why did it need the USB to do this?  That is just the ISO and YUMI file??? 
7) Doesn't give me any time to select from the GRUB start up menu and just boots to the shell.

In all of that, it is obvious where I went wrong?

---

### Post by darkod on 2016-03-11
What can often happen with installing from usb sticks is if the stick was /dev/sda, the installer can (wrongly) put the bootloader on it, because it considers /dev/sda as the first disk. If it does need the stick plugged in to boot, boot it like that, when you see the prompt log in with the username and password you selected when installing, and then show me the output of:
```
sudo parted -l (small L)
```

I will tell you how to put the bootloader on the correct disk. I'm waiting...

PS. Actually that parted command might give long output because you have three disks. The following command will show much shorter output and it still helps seeing the OS disk:
```
df -h
```

Run only that one and post the image...

---

### Post by david472 on 2016-03-11
Sorry it takes me so long, I have to take a pic, upload it to google drive, download it, resize it, put it to tinypic.com and then here.
[IMG]http://i68.tinypic.com/2h66d0n.jpg[/IMG]

You were right the super user stuff was very long, but I can show that too if you want,

---

### Post by darkod on 2016-03-11
Looking at this I assume you used the guided option with LVM, not manual partitioning... One thing I don't like about that guided method is that it creates separate /boot partition, and very small. So in the future you will have to be careful not to use up all space on /boot leaving it with no free space.

Anyway, it looks like your OS disk is /dev/sdb. To install the bootloader to it, simply do:
```
sudo grub-install /dev/sdb
```

Then unplug the stick. Reboot with:
```
sudo reboot
```

Now the server should boot correctly without the stick connected...

---

### Post by david472 on 2016-03-11
HEre is the longer version, can't take a great pic, just too small.
[IMG]http://i64.tinypic.com/riyv5l.jpg[/IMG]

Ok, that rebooted ok.  
1) Same thing as before, it does not give me any time to change anything from the GRUB menu - but if go quickly and use the arrow keys, I can pick different options- it is booting to the 250 gig hard drive since the usb is now out! success!
2) I am at the shell of ubuntu server - login and password work!
3) I am assuming at this point, there is no desktop version of this server, it is will be all command prompts?
4) The raid installation is next?  Is this command line driven to install the raid?

---

### Post by darkod on 2016-03-11
Yes, ubuntu server like all linux servers by default comes with only command line. People add desktops GUI to it, but it is not really recommended and in such case you could have installed the desktop version instead of server.

During installation did you install the OpenSSH Server? If you did, you can access your server remotely by ssh from any computer in the same network. It is usually more comfortable than working in front of the server all the time. And you can copy/paste output and commands easier.

A server is not meant to be dual booted, that's why the grub boot menu has no great significance and by default it set to continue booting after only 3 seconds. Imagine if it's 60 seconds by default. When you are rebooting your server it just sits there without continuing and the users can't use the services longer. That's why the time is very short to allow for faster booting.

Yes, you can continue with the raid now. I see one 1TB disk is sda and the other is probably sdc. You want to install raid1 yes? A single array of 1TB? Or you want to split it into smaller arrays?

Show me this also:
```
sudo parted /dev/sda unit MiB print
```

---

### Post by david472 on 2016-03-11
I brought the computer home with me this weekend so I could work on it, I hope it won't effect me installing the rest of the software RAID on it because it won't be hooked up to the network while here.
1) I have 2x1TB hard drive.  Both are exactly the same Blue Western Digitals, bought about 1 month apart.
2) I am hope that "sda" and "sdc" are just naming conventions because both drives are the same.
3) I want to install the RAID on the 2x1TB drives, each as a redundancy to the other.  If one goes down, the other will take over so I don't lose the files.

Here is the image from the commands:
[IMG]http://i67.tinypic.com/28k4gi9.jpg[/IMG]

---

### Post by darkod on 2016-03-12
OK, assuming you want one big 1TB raid1 array, here is what you need to do to create the partitions on sda and sdc, and create the array:
```
sudo parted /dev/sda (that will open the parted prompt)
unit MiB
mklabel msdos (create new msdos partition table)
mkpart primary 1 953850 (create one big primary partition)
set 1 raid on (set raid flag on it)
select /dev/sdc (change to sdc and do the same)
mklabel msdos
mkpart primary 1 953850
set 1 raid on
quit (close parted prompt)
```

Now you should have two identical big partitions on sda and sdc. To create the raid1:
```
sudo mdadm --create /dev/md0 --level=raid1 --raid-devices=2 --verbose /dev/sda1 /dev/sdc1
```

After that you should have the /dev/md0 SW raid device. You can check its status with:
```
cat /proc/mdstat
```

After it finishes the initial sync, we will continue (you can continue right away but no need to rush)... Let us know how it goes.

---

### Post by david472 on 2016-03-12
I am on the 3rd line and it says "partitions on the /dev/sda are being used Ignore/Cancel"?

---

### Post by darkod on 2016-03-12
You have an old swap on /dev/sda6 and it is probably using it automatically. It is safe to select Ignore. Or if you cancelled it, try running first outside of parted:
```
sudo swapoff /dev/sda6
```

Then start with the commands from the start.

---

### Post by david472 on 2016-03-12
Ok, I completed the swap.  And went through the commands on the PARTED prompt.  That seemed to work.
It also said that I might need to update etc/fstab

Next I tried the
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo mdadm --create /dev/md0 --level=raid1 --raid-devices=2 --verbose /dev/sda1 /dev/sdc1[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
And it says 
```
sudo: mdadm: command not found
```

Here is the pic of the last few things I have done :
[/FONT][/COLOR][IMG]http://i66.tinypic.com/neatyt.jpg[/IMG]

---

### Post by darkod on 2016-03-12
OK, the package is not installed. I thought the server version includes it by default but it seems it doesn't. You need to install it but the machine has to be connected to the internet for that. Is it?

If it is, simply do:
```
sudo apt-get update
sudo apt-get install mdadm
```

If that finishes successfully, then run the create command.

If you configured dhcp addressing during install, just plugging it into your home router should work. If you set manual IP address, it might not match your home network so you might need to modify it.

---

### Post by david472 on 2016-03-12
Ok, I will have to bring the computer down to the basement to use it there (that is where the router is).  Unless of course I can use a wireless connector that I have - but that probably needs drivers etc.

It is asking me what "Mail server configuration best servers my needs?" POSTFIX
I am not at work, so I don't know if this is going to mess things up because it is not the same network.  What should I choose?  This is just a video server, holding videos only.
[IMG]http://i64.tinypic.com/r2st47.jpg[/IMG]

---

### Post by darkod on 2016-03-12
Use No Configuration, you don't need mail services there...

---

### Post by david472 on 2016-03-13
Tried the command line : ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo mdadm --create /dev/md0 --level=raid1 --raid-devices=2 --verbose /dev/sda1 /dev/sdc1[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
and it says
```
You have listed more devices (3) than are in the array(2)
```[/FONT][/COLOR]

---

### Post by darkod on 2016-03-13
Hmm, lets try a small modification in the order of the options, although it shouldn't have mattered. Try this:
```
sudo mdadm --create --verbose /dev/md0 --level=raid1 --raid-devices=2 /dev/sda1 /dev/sdc1
```

That should surely work...

---

### Post by david472 on 2016-03-13
Ok will try it.  
1) Interestingly, there used to be 4 options upon booting, now there are only two (not that it matters for me, I am only using the first one)
2) the command seems to have worked, but I think (and I am not sure here) that is only partitioned one drive
[IMG]http://i66.tinypic.com/sljx1g.jpg[/IMG]

---

### Post by darkod on 2016-03-13
You can check the md0 details with:
```
cat /proc/mdstat
sudo mdadm -D /dev/md0
```

That will show how many members there are. There were raid remains on sda1 from your previous data but lets see how md= looks like now...

---

### Post by david472 on 2016-03-13
Ok here is the result :
Now does this mean that when data is saved on the 1TB drive, it is automatically saving it also on the other 1TB drive?
[IMG]http://i63.tinypic.com/j99hfc.jpg[/IMG]

---

### Post by darkod on 2016-03-13
OK, that looks good. It is still doing the initial resync (creating the array), it reached 73%. But you can continue working, it will keep doing the resync in the background.

Yes, from now on you are working with the array /dev/md0 (not the partitions /dev/sda1 or /dev/sdc1). And it saves the data on both partition automatically. But before you start using it you have to format it and create a mount point for it, for example /data or if you prefer it can be /video. Then you will mount /dev/md0 on that mount point and you use the mount point for your operations. Lets do that:
```
sudo mkfs.ext4 /dev/md0 (to format it)
sudo mkdir /data (to create a mount point of your choice)
sudo mount /dev/md0 /data (to mount the array to the mount point)
```

After you format it, also show me this output:
```
sudo blkid
cat /etc/mdadm/mdadm.conf
```

You will need to set the array to assemble and mount on boot.

---

### Post by david472 on 2016-03-13
Ok, did what you asked.  The first command formatted it, but the other two 
```
 [COLOR=#000000][FONT=Ubuntu Mono]sudo mkdir /data
sudo mount / dev/md0 /data
``` 
did not ask me any queries as to where I wanted to mount.  It seemed to do nothing, just returned the prompt.  Maybe behind the scenes...

The output here:


[/FONT][/COLOR][IMG]http://i68.tinypic.com/2zric6f.jpg[/IMG]

Here is the rest after:
```
[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/mdadm/mdadm.conf
```[/FONT][/COLOR]

I had a feeling it wouldn't all fit, so I did it in stages

[IMG]http://i68.tinypic.com/depjyo.jpg[/IMG]

---

### Post by darkod on 2016-03-13
Very strange. If you look in the blkid output, sda1 is reported as ntfs partition. With the parted commands you did it should have erased the whole partition table and created new single partition without any filesystem.

Otherwise the rest is looking good but this sda1 info is confusing.

Can you post the result of:
```
sudo parted /dev/sda unit MiB print
```

---

### Post by david472 on 2016-03-13
Do you think I should have formatted the drive first?
Anyway, here is the result :

[IMG]http://i63.tinypic.com/j61hz8.jpg[/IMG]

---

### Post by darkod on 2016-03-13
Formatting doesn't help much, it's how windows does things and people think it's the magical solution. The real important thing is repartitioning, which you did with parted. It might not have finished the process correctly because of that message that the disk is in use. But used by what?

Maybe we should have investigated more but I didn't want to complicate things because it all goes too slow doing it step by step over days...

The raid will keep working as it is, but it is unusual to see such ntfs partition on the disk. If you want to, you can try removing the sda1 partition from the raid (you still have no data on it), redo the partitioning again, and join it to the raid... If you do decide to try this, it would go like:
```
sudo umount /data (unmount your array)
sudo mdadm --stop /dev/md0 (stop the array)
sudo mdadm /dev/md0 --fail /dev/sda1 (mark as failed sda1 member)
sudo mdadm /dev/md0 --remove /dev/sda1 (remove it from the raid)
sudo mdadm --zero-superblock /dev/sda1 (delete the superblock info for the existing raid)
```

After that open the disk with parted and create new partition table:
```
sudo parted /dev/sda
unit MiB
mklabel msdos
print
```

That should print out only the basic disk info, not showing any partitions. If that is correct, continue creating the same partition as above. But when you print the layout after that, it should look the same as above only without ntfs in the File system column:
```
mkpart primary 1 953850
set 1 raid on
```

If that looks ok, quit parted and join the new sda1 to the raid:
```
quit
sudo mdadm /dev/md0 --add /dev/sda1
cat /proc/mdstat
```

That should show the array resync again after adding the new sda1.

You don't have to post screens of all of the above, only if you see something unusual. Basically the operation is very simple, you are creating new blank partition table, new partition and joining it to the raid.

If all goes well and /proc/mdstat shows resync, post again the output of:
```
sudo blkid
```

---

### Post by david472 on 2016-03-13
Ok, I am willing to try anything since you are such a patient person! Thank you again and again.
Ok tried two of the first commands and then this one
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo mdadm /dev/md0 --fail /dev/sda1 (mark as failed sda1 member)
```

Here is the error : 

```
mdadm: error opening /dev/md0 : no such file or directory
```
Maybe that is the issue?[/FONT][/COLOR]

---

### Post by darkod on 2016-03-13
Sorry, my mistake. I think the --stop command was supposed to come later. Once the array is stopped it complains it can't find it. Just skip the --fail and --remove, do the zero-superblock for both /dev/sda1 and /dev/sdc1, and after you finish with parted instead of the:
```
sudo mdadm /dev/md0 --add /dev/sda1
```

do the full command to recreate /dev/md0 again like you did earlier:
```
sudo mdadm --create --verbose /dev/md0 --level=raid1 --raid-devices=2 /dev/sda1 /dev/sdc1
```

It was new and empty anyway, we might as well recreate it from scratch.

So, zero the superblocks on both partitions, do the parted procedure for /dev/sda and recreate the array again... Then post the new blkid output...

---

### Post by david472 on 2016-03-13
Im getting a little confused here, so this is what I did for the _**sda1**_:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo umount /data (unmount your array)
[/FONT][/COLOR]sudo mdadm --stop /dev/md0 (stop the array)
sudo mdadm --zero-superblock /dev/sda1 (delete the superblock info for the existing raid)
```

Then I did this :
```


sudo parted /dev/sda
unit MiB
mklabel msdos
print
```

And then finally this :
```

[COLOR=#000000][FONT=Ubuntu Mono]mkpart primary 1 953850
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]set 1 raid on
quit[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

[FONT=arial narrow][SIZE=3]Then I did the exact same things for the _**sdc1 as well**_.  I then quit and now at the prompt.

1) Which POST # in this forum should I start with again.  Is it POST #54?
2) Did you want me to show you the drives ?  What is the command again so you can see where I am at?[/SIZE][/FONT][/FONT][/COLOR]

---

### Post by darkod on 2016-03-13
OK, first now lets check the partition on both disks. What does these show? Identical partitions with NO file system right?
```
sudo parted /dev/sda unit MiB print
sudo parted /dev/sdc unit MiB print
```

If that is so, since you already zeroed the superblocks on both sda1 and sdc1, simply create new array now:
```
sudo mdadm --create --verbose /dev/md0 --level=raid1 --raid-devices=2 /dev/sda1 /dev/sdc1
```

---

### Post by david472 on 2016-03-13
Ok, both are identical EXCEPT, the sdc  does NOT list the File System as NTSF, it does not list anything.  Blank there.
sda, lists as NTSF.
Could that be the issue?

---

### Post by darkod on 2016-03-13
Something is very weird with that disk... The partition table keeps showing that ntfs partition. Try this: create new blank partition table on sda (the mklabel command), then quit parted and reboot. And then after the reboot try creating new partition on it (the mkpart command). Lets see if that helps getting rid of the ntfs partition.

---

### Post by darkod on 2016-03-13
Another idea, if the above doesn't work, you could try to zero the first 512B on the disk. They hold the boot sector and partition table, hopefully that will get rid of this ntfs partition. The idea is after you do the mkpart in parted to have a single big partition on the disk but no file system. That ntfs has no place there, you are working on linux and linux partitions, ntfs is used by windows.

To delete the 512B you would do:
```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```

After that do the standard mklabel and mkpart in parted, and check if the partition created still says ntfs.

---

### Post by david472 on 2016-03-13
Tried what you asked.  
```
sudo parted /dev/sda
unit MiB
mklabel msdos
print
```

Then I quit and rebooted. After that I tried.
```
mkpart primary 1 953850
```
And then I did a sudo parted / dev/dsa unit MiB print 
and it is still NTFS

Tried the ```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```
and then the mklabel msdos, and the mkpart primary 1 953850 and then quit and it still says NTFS

Is formatting this drive in linux out of the question or will that not help?

EDIT : 
ALSO, it tells me (when I quit parted) that I need to update /etc/fstab

Could this be part of the issue?

---

### Post by darkod on 2016-03-14
No, that is not an issue. That message is standard when quitting parted because depending on the changes you do, you might need to update fstab.

Yes, you can try formatting the disk in linux but what is confusing is that the parted procedure is doing exactly that. Deleting the current partition table and creating a new blank one. Then you are creating single partition in it. Without any filesystem, because for raid you don't need filesystem on the partition. But somehow that new partition has ntfs filesystem right after you create it without you doing it at all.

If you have linux desktop at hand, you can connect the disk to it and take a look how it looks with any GUI partitioning tool, like Gparted... It might give you more clues. Plus it will allow you to see how the disk is reported on another machine, as ntfs or not. Because on the server I am still wondering if there are any settings for the raid or leftovers that confuse it... If you can, check on another machine how does the disk look like.

---

### Post by david472 on 2016-03-14
No I don't have another linux desktop on hand.  I bought home this computer trying to fix it here.  Sigh.

1) should I try and load the computer with a knoppix LIVE CD or something else?  I tried to find a LIVE ubuntu desktop, but I thought they were all installers.  That way I can unhook everything but the drive that is giving me the problem and format it from there?
2) Should I try the Fdisk command?  I am not entirely sure how to type it out, but something like  " fdisk /dev/sda "  or "**mkfs /dev/sda****"  (I am learning this from google, so I don't know if I have it right or not)**
2) What other suggestions do you have? (and if you are confused, believe me I am beyond it right now)

---

### Post by darkod on 2016-03-14
You can try fdisk, or any live distro that you are comfortable with (knoppix, ubuntu desktop, etc). Literally I am out of suggestions how to get rid of this strange filesystem... :(

---

### Post by david472 on 2016-03-14
Well this is what the desktop looks like for me using a liveUSB boot.
Since I am used to windows, I am not really getting this
It looks like I have THREE drives attached
1) NEW VOLUME DRIVE  - right clicked and properties - it says 120mb used and 974.4mb free (guessing it is one of the 1TB)
2) 249gig DRIVE - right clicked properties - it says 1gig used, 231.1 free (guessing this is the 250gig boot drive)
3) 255mb is the voume = 184.3mb free, 49.9mb used (usb????) 
4) Missing the the other 1TB drive?!??!?


[IMG]http://i65.tinypic.com/1zbflg1.jpg[/IMG]

And here is trying the Gparted command 
I looked at sdc1 and it says "Unknown file system" is that because of the RAID?

  And the hard drive sda1 is definitely NTSF, not sure if formatting will eliminate this? 
How should I proceed, if you still have the patience!!

Found this : [http://askubuntu.com/questions/134739/i-am-not-able-to-delete-a-corrupt-ntfs-partition-on-my-pen-drive-how-can-i-for](http://askubuntu.com/questions/134739/i-am-not-able-to-delete-a-corrupt-ntfs-partition-on-my-pen-drive-how-can-i-for)

[IMG]http://i63.tinypic.com/16j28mb.jpg[/IMG]

---

### Post by darkod on 2016-03-14
The key symbol means mounted, and you can see the value in the Mount Point column. Right click sda1 and select Unmount. Then right click and delete it. That will leave only unallocated (unpartitioned) space on /dev/sda.

Then right click on the unallocated space and make a partition of 953850MiB leaving 1MiB in front. Try to select RAW or no filesystem for it (you don't want to create a filesystem on it, just the partition).

When that is done click the green Apply tick button in Gparted. No changes are applied until you click it.

After it finishes it will refresh the view and see if sda1 is reported as ntfs again (like it shows right now).

---

### Post by david472 on 2016-03-14
This is strange.  I went for dinner, came back and rebooted.  The Key is no longer there.  Oh well, I then did this:
1) Right click Delete
2) Right click NEW
3) Now, the full disk is 953869 is a full disk - is there a reason to go 953850?
4)  there is no RAW files system.  Here is what is available  btrfs / ext 2 / ext 3 / ext 4 /fat 16 / fat 32 / jfs / linux-swap / ntfs / reisefts / xfs / cleared / unformatted
Which one is closest to RAW?

I went with UNFORMATTED : and applied.  It is still NTSF.  What gives?  This is insane!!  Should I try to format it Fat 32?

Ok, some progress...maybe.
I changed the file system to CLEARED and it seems to have done something.  Also, I used the entire drive which was 953869.  Now it looks to be ok, but how can I test it for sure?

_**sda**_
[IMG]http://i65.tinypic.com/25yzitw.jpg[/IMG]

_**sdc**_ - this one has UNALLOCATED.  Not sure how that is going to factor into everything.
[IMG]http://i67.tinypic.com/23muhwh.jpg[/IMG]

Some success I think (still unsure about the amount of space need for the raid since I used the entire drive I think). 
 The _**sda**_ is not in a RAID yet, but I am not sure of the procedure at this point - do I get rid of the raid from the _**sdc**_ and then add the raid to both the** sdc** and **sda** at the same time?

[IMG]http://i65.tinypic.com/2dre3bl.jpg[/IMG]

Added the RAID to the sda, and this is what I got.  There are different numbers for the end and size, so that has to be fixed.  Not sure how though.

[IMG]http://i65.tinypic.com/2dsk0vp.jpg[/IMG]

---

### Post by darkod on 2016-03-15
That is not the problem, the raid array will have the size of the smaller partition (in this case sda1) but it will work without issues. It seems you solved it by clearing it in Gparted. Now you can see there is no ntfs reported for sda1.

How did you add the raid flag? Repartitioning or just adding the flag? I am asking because sda1 now has different size. Compare with the previous pictura, it was bigger and now it's quite smaller, almost 50GB. The difference with sdc1 is not a problem, but I am curious how would sda1 shrink 50GB. I suggested 953850 because that was the size of sdc1, to make both partitions equal.

Now that you have the ntfs cleared you can try again the parted procedure for /dev/sda, and that will make the partition equal to sdc1. You know, the mklabel to create new table, and the mkpart... You already did that few times. :) The raid flag is only informative, if a partition has it it doesn't mean it's part of a raid. Or vice versa... But tomorrow it helps when looking at partitions you know which ones are expected to be part of raid.

Right now, you can continue as it is (but the array will be about 50GB smaller than the disk max size), or you can redo partitioning of /dev/sda. You already have the commands for both cases.

If you want to create the raid as it is, do the mdadm --create --verbose... command to create the /dev/md0 array.

If you want to redo sda1, first do the parted procedure from before, and then the mdadm --create --verbose...

---

### Post by david472 on 2016-03-15
How I got the RAID on, was by doing this, probably wrongly:
```

sudo parted /dev/sda
unit MiB
mklabel msdos
print
mkpart primary 1 953850
set 1 raid on

```
1) I would really like to recover that 50Gig, I didn't even notice. How can I do that?  Just sda?

2)  Should I go into Gparted (desktop version), and reformat sda again or 
3) Just use your code, that is presented in this post?

I am feeling better and starting to see a light at the end of the tunnel - I think.

_**EDIT**_

Here is what I have just completed and I think it is ok:

Then I did this :
```

sudo parted /dev/sda
unit MiB
mklabel msdos
print 
```
And then finally this :
```

mkpart primary 1 953850
set 1 raid on
quit

```

Again I did the exact same things for the sdc1 as well. I then quit and now at the prompt.

Then a print statement.


[[IMG]http://s10.postimg.org/a5zt5m7h1/serverupdate15.jpg[/IMG]]("http://postimg.org/image/a5zt5m7h1/")

---

### Post by darkod on 2016-03-15
Finally it looks as it should. :)

I see you already created /dev/md0, right?

Now to make sure the array auto-assembles on boot, post the output of:
```
sudo blkid
cat /etc/mdadm/mdadm.conf
cat /etc/fstab
```

If it doesn't fit on one screen, split it. The blkid and /etc/fstab should fit on one, and then mdadm.conf might need new screen. :)

You are almost there... Good work.

PS. I forgot to mention, if you didn't format md0 yet, do it before running the blkid:
```
sudo mkfs.ext4 /dev/md0
```

---

### Post by david472 on 2016-03-15
Ok:

1) I performed the sudo mkfs first 

[[img]http://s12.postimg.org/epjz1tfjt/serverupdate16.jpg[/img]](http://postimg.org/image/epjz1tfjt/)

2) then I completed the sudo blkid second
[[img]http://s13.postimg.org/e19env54z/serverupdate17.jpg[/img]](http://postimg.org/image/e19env54z/)

---

### Post by darkod on 2016-03-15
OK, now you need to....

1. Create an entry for the array in mdadm.conf so it can auto-assemble on boot. In /etc/mdadm/mdadm.conf, below the line "definitions of existing arrays" make a new line like:
```
ARRAY /dev/md0 UUID=fb4b0558:df4c....etc
```

You can see the UUID string in blkid related to /dev/sda1 and /dev/sdc1. Notice how they have identical UUID code as array members, and then have different UUID_SUB as partitions. Use the common UUID and you can group it in four groups of 8 characters separated by :. Yes, the blkid output is not in this format, but the total number of characters is the same, 32. So just retype them carefully to create the ARRAY entry. Without quotes marks. After that save and close the mdadm.conf file. And update initramfs:
```
sudo update-initramfs -k
```

To test, reboot the server and the array should be assembled automatically. You can check basic array info with cat /proc/mdstat.

2. You need to create a line in /etc/fstab to mount the array on boot. For that you use the md0 UUID (not the same as the UUID you used in mdadm.conf!!!):
```
UUID=2be748f2-55ed-....   /data   ext4   defaults   0   0
```

This time you can use the UUID in the same format as blkid outputs it. In my line, the array mounts on /data. If you need it to mount on another mount point, you will need to adjust this line to your needs. And you will need to create that mount point if it doesn't exist.

After you edit and save /etc/fstab, that's it... Test it with:
```
sudo mount /data
```

And it should mount automatically on boot...

---

### Post by david472 on 2016-03-15
Ok I see it looks like you are updating a batch file (in windows terms?), I have the screen captures on my second monitor so I can punch them in exactly, 

Question(s):
You asked me to create an array entry.  Do I do this from the command prompt?  I only ask because some commands were within _**parted**_ and I want to be sure.
1) Here is the line "Definitions of existing arrays..." highlighted.  
[[IMG]http://s11.postimg.org/y5hgo1fjz/serverupdate18.jpg[/IMG]]("http://postimg.org/image/y5hgo1fjz/")

After that I used the cat /fstab command.  

**Would I have to run this first before punching in ARRAY?**
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo blkid
[/FONT][/COLOR]cat /etc/mdadm/mdadm.conf
```

[COLOR=#222222][FONT=Verdana]2) OR do I need to use SUDO 
3) or just start typing ARRAY at the command prompt?[/FONT][/COLOR]

---

### Post by darkod on 2016-03-15
No, you need to edit /etc/mdadm/mdadm.conf. The editor I find most user friendly is nano. And because that's a system file, you need to edit it with:
```
sudo nano /etc/mdadm/mdadm.conf
```

Position the cursor below the #definitions... line (the arrows keys are working to move the cursor) and type a new line as per my previous post. To save changes and exit nano you do: Ctrl+O, Enter, Ctrl+X.

You do the same to edit /etc/fstab:
```
sudo nano /etc/fstab
```

And make a new line as per my post...

---

### Post by david472 on 2016-03-15
Ok I just finished getting a massive headache trying to type that out exactly! lol
Here is what I have and I noticed :

1) That I am _**not**_ identifying _**sda**_ in the entry.  How does it know? 

```
ARRAY /dev/md0 UUID=fb4b0558:df4c2c04:872abcc6:b0a2532b UUID_SUB=d7d27ed6:0bfe6165:1a1796a3:a23ce311 LABEL=commtechserver:0 TYPE=linux_raid_member
```

2) Should the second entry look the same, except for the UUID SUB? :

```
ARRAY /dev/md0 UUID=fb4b0558:df4c2c04:872abcc6:b0a2532b UUID_SUB=6d9c2333:3d8b7fae:1804d468:446e4b30 LABEL=commtechserver:0 TYPE=linux_raid_member
```

3) Also, I did _**NOT**_ put QUOTES in any of it, not the commtech server, not the linux raid etc.  I think that is what you meant.
4) Are the "_**# tags**_" in the editor meant for comments like in programming with python?

And although I am getting ahead of myself, where is this line in the code?
```
[COLOR=#000000][FONT=Ubuntu Mono]UUID=2be748f2-55ed-....   /data   ext4   defaults   0   0[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Ubuntu Mono][SIZE=2][FONT=tahoma]I see the UUID-2be748f2:55ed455b:a1f22ebb:7d0c503f TYPE=ext4      !!!!! I don't see the _**DEFAULTS 000**_[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by darkod on 2016-03-15
This is what happens when posting images instead of text output. I would have been able to cope/paste you exact commands... :) Honestly I was too lazy to retype all of those strings... And we misunderstood each other... Here is what you need:

1. In /etc/mdadm/mdadm.conf you need to add only ONE line, not two. There is only one array. And the line has only the UUID, not the rest of the output blkid shows. It would be like this EXACTLY:
```
ARRAY /dev/md0 UUID=fb4b0558:df4c2c04:872abcc6:b0a2532b
```

That's enough for mdadm to do its job. With the UUID it has everything it needs, you don't need to tell him about sda1 or sdc1 or anything else...

2. In /etc/fstab also, first in the line you put only the UUID, and the rest of the line you type in, not from blkid. It will be exactly this:
```
UUID=2be748f2-55ed-455b-a1f2-2ebb7d0c503f   /data   ext4   defaults   0   0
```

I think I got the strings OK; double check them. The rest should be identical as written, in linux every space matters, every capital or small letter, nothing is coincidence... :)

Yes, usually in config files lines starting with # are comments and used for explanations. So for example in /etc/fstab above the line you will create you can also put something like:
```
# Mount for array /dev/md0 at /data
```

---

### Post by david472 on 2016-03-15
Darko, you have never been lazy - you have been patient and kind.  I appreciate everything you have done, not many people would have done the same!

Ok, I had to go for a walk and clear my head - developing a massive headache, but nevermind, I want to get this done.  
I updated the [COLOR=#000000]/etc/mdadm/mdadm.conf  files and saved it.  Doubled checked it was saved and re-opened it to be sure the line was there.

Now I tried to update the 
[/COLOR]```
sudo update-initramfs -k
```

and it unfortunately give me this error : 
No arg for -k option
Usage: /usr/sbin/update-initramfs [OPTION]
then it lists the options, of which "k" is there, so I am not sure why it didn't like it?

---

### Post by darkod on 2016-03-15
Sorry, try with -u that was the better option... Lets see how that goes.

---

### Post by david472 on 2016-03-15
That worked, now where do I place the next line in the fstab?
1) Am I copying over another line
2) Making a brand new line in the file?
3) Does it matter where it is placed ( like in the previous mdadm.conf)?
4) It looks like 3 spaces between data and ext4 and ext4 and defaults and 0 and 0 - correct?

```
[COLOR=#000000][FONT=Ubuntu Mono]UUID=2be748f2-55ed-455b-a1f2-2ebb7d0c503f   /data   ext4   defaults   0   0[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]


[/FONT][/COLOR]

---

### Post by darkod on 2016-03-15
Any new line is OK, it can be anywhere in the file. As we said, put a comment line above it if you want, starting with # and explaining what that entry is.

Yes, I put 3 spaces but it can be only 1. I put 3 so that the division between the parameters can be seen more easily. When putting spaces in general it doesn't matter how many there are, only to be careful not to forget any and stick two parameters together when they shouldn't be together. :)

---

### Post by david472 on 2016-03-15
I forgot should I reboot before editing the fstab?

---

### Post by darkod on 2016-03-15
> **david472 said:**
> I forgot should I reboot before editing the fstab?

Not necessary. After editing it, you can quickly test if the entry works by:
```
sudo mount /data
```

Using the mount point you used in your entry, it will try to mount it.

But after you finish all that, rebooting will help you test if the raid array is assembled good on reboot and whether fstab mounts it correctly.

---

### Post by david472 on 2016-03-15
I ran the sudo mount /data and there are no errors.  Now a reboot.  Update in a couple of minutes.
Booted and now at command prompt.  There were no errors but also nothing telling me that it was mounted or anything else.  Just booted as normal.
How will I be able to tell?

Here is a screen shot of shorter version: df -h
and the longer version sudo parted -l

[[img]http://s17.postimg.org/z4yzu3ei3/serverupdate20.jpg[/img]](http://postimg.org/image/z4yzu3ei3/)

[[IMG]http://s23.postimg.org/c8ab353iv/serverupdate19.jpg[/IMG]]("http://postimg.org/image/c8ab353iv/")

I am guessing here that you might want to see this.

---

### Post by darkod on 2016-03-15
Well, you answered your own question. In the df -h you can see /dev/md0 mounted at /data, size of 917GB. You can use the array as /data mount point. If you need it to be something else, you need to create different mount point and adjust the line you added in /etc/fstab.

Congrats, you did it...

Now, I don't know how you were (or plan to) using the server, but as far as making the raid and mounting it, you did it... You might need further actions depending on what you expect from this server.

---

### Post by david472 on 2016-03-15
Well, I could never ever ever have done it without you.  Thank you from the bottom of my heart!

This is the hope : 
1) I need people to be able to put video files on it and edit them from the network
2) From their computers, they are going to map to the server, dump the footage and edit it from their own computer via a batch file that was created in windows.

Well, that is what happened before I took over, my hope is that I can get it back and do the exact same thing.  Do that sound doable?

---

### Post by darkod on 2016-03-15
Well, that doesn't sound complicated, but it might be better to mark this as solved and open new thread specific for that. You can mark thread as Solved in Thread Tools above the first post.

That way this thread will remain only for the raid and in future if someone stumbles on it in searches...

You basically need simple file server. If the clients are windows, the usual solution is Samba server. If the clients are linux, you can also use Samba, but also alternatives like simple nfs or even iscsi.

---

### Post by david472 on 2016-03-15
Ok, I just did a quick search : like this?

[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)
And yes after your response, I will close this thread!

---

### Post by darkod on 2016-03-15
Exactly like that. Samba is full of options, so you can configure what ever you need. Of course, the more settings you want to use, the more complex it gets. But for "simple" file sharing samba is very easy to configure. And there is plenty resources and tutorials/blogs on the internet about samba, not just the ubuntu server guide.

---

