---
title: "Error during install &quot;Please insert disc labeled...&quot;"
date: 2010-05-01
forum: Server Platforms
---

### Post by josh_moore on 2010-05-01
Having difficulties installing 10.04 AND 9.10 versions of Ubuntu Server
After reaching Installing Base, after retrieving, unpacking and configuring many files, at 75% the install stops and states
Please insert disc labeled Ubuntu-server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)
or
Please insert disc labeled Ubuntu-server 9.10 _Karmic Koala) - Release amd64 (20091027.2)

If I press Alt+F2 and active that console, I can see the contents of the disc on /cdrom/

This has become very frustrating to fight with so if anyone has suggestions it would be appreciated.

---

### Post by ShadowRavenNC on 2010-05-01
having the same problem :confused:

---

### Post by ezens on 2010-05-01
i have something like it 
shows there is no cdrom but as you said /cdrom/ 
kinda works only when entered in console it flips back to setup menu (any version) other server type linux based os detects cdrom as hard drive because hard drives are SCSI as i got told and that's like :lolflag: is there a server not having hdd's designed for them or what

---

### Post by josh_moore on 2010-05-03
Does no one have any thoughts on this?
9.04 installed without this issue, cannot install 9.10 or 10.04
I am going to upgrade from 9.04 to 10.04 but I would prefer not to have something like this go unexplained/resolved

---

### Post by SaturnusDJ on 2010-05-03
Same here. (10.04LTS Desktop Alternate AMD64).

At [http://forum.ubuntu-nl.org/server-en-netwerk/%28karmic-koala-installtie%29-insert-disk-die-er-al-in-zit/msg510495/?PHPSESSID=499f25847d52b59cf05fa5b3262798b8#msg510495](http://forum.ubuntu-nl.org/server-en-netwerk/%28karmic-koala-installtie%29-insert-disk-die-er-al-in-zit/msg510495/?PHPSESSID=499f25847d52b59cf05fa5b3262798b8#msg510495) a dutch user explains to move the cdrom content to a sub dir in a dir called '/target' when setup is around partitioning part. Then umount the cdromdrive (/dev/sr0), remove mountdir (/cdrom) and create a link to the cdrom content (ln -s /target/cdrom_copy /cdrom/)...however, this for me **is not working also.**

Playing with [http://www.question-defense.com/2010/04/02/media-change-please-insert-the-disc-labelled-ubuntu-9-10-karmic-koala](http://www.question-defense.com/2010/04/02/media-change-please-insert-the-disc-labelled-ubuntu-9-10-karmic-koala) is worth some time. I can try again in about 12 hours. I already expected something being wrong with the apt-get stuff, because right after that the error appears.

[http://ubuntuforums.org/showthread.php?t=1137319&page=4](http://ubuntuforums.org/showthread.php?t=1137319&page=4) also interesting but not a general solution also.

More clearly: [https://answers.launchpad.net/ubuntu/+question/26453](https://answers.launchpad.net/ubuntu/+question/26453)

Even more stuff to read: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/360460](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/360460)


And ofcourse: Shame for the Ubuntu team not having fixed this.

---

### Post by cariboo on 2010-05-03
Has anyone tried a different cd-rom drive, as the bug seems to point to a problem with Sony/NEC cd-rom drives.

---

### Post by benplowman on 2010-05-03
I also experienced this issue and saw it looks similar to what is found [here.]("http://ubuntuforums.org/showthread.php?t=427864%7Chere")

To solve this, the link proposes you follow these steps:

[LIST=1]
[*]Boot into the cd-rom.
[*]Choose the option "Rescue a broken system" from the start menu
[*]Choose the image you wish to mount and then open a shell for that image.
[*]cd /etc/apt/
[*]edit sources.list and comment out the first line by putting a # in front of it.
[/LIST]
So "deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/  feist$"

Should turn into "#deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64  (20100427)]/  feist$"

What I don't understand is how to make the sources.list changes stick. I can't figure out how to tell Ubuntu to pick up where it left off after I make the file change.

---

### Post by BetterSense on 2010-05-03
This is just a total shame. I literally cannot install Ubuntu, and there's nothing I can do. I tried reburning disks, checking the disk integrity. I used unnetbootin to create a bootable flash drive from the Ubuntu alternate CD. Same exact thing in any case. It says I need to install the CD, about halfway through the "installing the base system'. Even when I'm using a flash drive.

---

### Post by SaturnusDJ on 2010-05-04
> **benplowman said:**
> I also experienced this issue and saw it looks similar to what is found [here.]("http://ubuntuforums.org/showthread.php?t=427864%7Chere")

To solve this, the link proposes you follow these steps:

[LIST=1]
[*]Boot into the cd-rom.
[*]Choose the option "Rescue a broken system" from the start menu
[*]Choose the image you wish to mount and then open a shell for that image.
[*]cd /etc/apt/
[*]edit sources.list and comment out the first line by putting a # in front of it.
[/LIST]
So "deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/  feist$"

Should turn into "#deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64  (20100427)]/  feist$"

What I don't understand is how to make the sources.list changes stick. I can't figure out how to tell Ubuntu to pick up where it left off after I make the file change.
Yes this is good to try if you don't have another cd/dvd drive.
Give this a try:
At the moment of error, comment out exacly as you described above, then do "apt-get update". Then try to continue. I read about this in one of the links I posted.

Now what is really strange: I was about to test what I just said but when I came back to check the installation progress, it was beyond the error part.:o

---

### Post by josh_moore on 2010-05-05
> **cariboo907 said:**
> Has anyone tried a different cd-rom drive, as the bug seems to point to a problem with Sony/NEC cd-rom drives.

I do not buy this because the fact that I can install 9.04 ok, or any version of Windows on that drive.

---

### Post by ghost_ryder35 on 2010-05-05
i know its not what everyone wants to hear but you could install 9.10 and then dist upgrade to 10.04.  you could also put the install cd onto a bootable thumb drive and install that way.

---

### Post by chillbeast on 2010-05-05
just want to confirm I was having the same issue with 9.10, 10.04 Beta2 and 10.04 LTS release. 

Sony DVD-RW drive.

Swapped out the Sony with a Lite-on after reading this thread and the install completed without any issues.

---

### Post by ilynx on 2010-05-06
Just adding that I, too, am having the exact same problem.  My drive is a Magicspin DVDRW, showing its cheapness!

Also, how do you get out of this situation?  My install is stuck at the screen "Please insert the disc labeled:  ..."  Do I have to turn off the power to get out of there?

---

### Post by josh_moore on 2010-05-06
> **ghost_ryder35 said:**
> i know its not what everyone wants to hear but you could install 9.10 and then dist upgrade to 10.04.  you could also put the install cd onto a bootable thumb drive and install that way.

As indicated in my original post, I cannot install 9.10 or 10.04.

And when I create a bootable thumb drive with 9.10 or 10.04, it fails out even earlier with a different error and retry to search for CD

---

### Post by ilynx on 2010-05-07
UPDATE:

I turned my machine on this morning and tried again.  I didn't do anything different than I had done before, but it worked this time.  Well, kinda.  I got the message indicating a successful installation, but when I reboot the machine, it does not boot into Ubuntu.  It just stops at the "Hardware Monitor" screen.

ilynx

---

### Post by BlueDevil63 on 2010-05-09
I will support the connection to DVD player brand.  I had this exact problem with a NEC DVD/RW drive.  Switched to Lite-On drive (both IDE drives, no other changes made at all) and no problems.

---

### Post by CharlesA on 2010-05-09
I had a problem like this with 9.10 when I was running Vista, but I don't know what the root cause of the problem was since I just burned the same ISO on a different machine and it worked fine.

I was using an LG drive at the time with Sony media.

Could try that.

---

### Post by Vegan on 2010-05-09
I suspect a bunch of dodgy DVD burners. I can burn disks for anyone who wants one on one of 3 differrent new drives I have.

Go to my site and click contact if you want some fresh CDs.

---

### Post by John_T on 2010-05-09
I had a similar issue.

I'm using an i386 alternate CD to do the upgrade.  I received the "insert disc labelled..." message, and thought "that's odd".  I tried putting in the regular desktop CD, which didn't help, so I put the original (alternate) disc back in, and it recognised it again and worked from that point onwards.

For what it's worth, it's an LG optical drive.

Try ejecting and reloading the disc a few times until the OS recognises it and pops up the file browser, assuming your system normally does so.

Edit:

It happened again, and a third time.  Perhaps it's random, but each time I had to repeat this sequence:
1. Get error message
2. Insert different CD (In my case the standard live CD)
3. Click continue and get error message again.
4. Insert the disc I was using and continue.

At present I'm supposedly at the "Installing the upgrades" stage, although the system continued to download the last 300 packages or so after ticking the "Getting new packages" option and moving on.  

All seems well now, we shall see.

---

### Post by rogimenez on 2010-05-14
Hello, has anybody solve this? I'm trying to install Ubuntu Server 10.04 64 bit edition on IBM server with Raid0 from IDE Sony DVD writer drive, and I get the same error.

---

### Post by drinkleadsoup on 2010-05-16
Same problem here.

[http://ubuntuforums.org/showthread.php?p=9307778#post9307778](http://ubuntuforums.org/showthread.php?p=9307778#post9307778)

---

### Post by Toison on 2010-05-21
I tried to burn iso on CD instead DVD (my drive is sony) and that work for me.

---

### Post by aszovathy on 2010-05-28
Hi there :)
I just tried to install Ubuntu-server 10.04 and I ran into the problem above. Luckily I had an LG DVD drive at hand and the system installed without a problem :)

---

### Post by _Mark_ on 2010-06-01
Have had the same problem server image burnt with Sony DVD Writer and on install failed at 75% with the error, changed to an LG burner I had spare used the same CD and all is well

---

### Post by xftwitch on 2010-09-30
Had the same problem, swapped a NEC for a Toshiba and it worked. I'm staggered that there's some bug that causes this based on the burner you're using to install the system... wow.

---

### Post by CharlesA on 2010-09-30
> **xftwitch said:**
> Had the same problem, swapped a NEC for a Toshiba and it worked. I'm staggered that there's some bug that causes this based on the burner you're using to install the system... wow.

Some burners are touchier then others, I guess.

You can always install via USB if you really need to.

---

### Post by cookie58z on 2010-12-17
> **benplowman said:**
> I also experienced this issue and saw it looks similar to what is found [here.]("http://ubuntuforums.org/showthread.php?t=427864%7Chere")

To solve this, the link proposes you follow these steps:

[LIST=1]
[*]Boot into the cd-rom.
[*]Choose the option "Rescue a broken system" from the start menu
[*]Choose the image you wish to mount and then open a shell for that image.
[*]cd /etc/apt/
[*]edit sources.list and comment out the first line by putting a # in front of it.
[/LIST]
So "deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/  feist$"

Should turn into "#deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64  (20100427)]/  feist$"

What I don't understand is how to make the sources.list changes stick. I can't figure out how to tell Ubuntu to pick up where it left off after I make the file change.

After many tries, it worked. Though I'm not sure if this works for other cases, I describe what I did.

1-1. Do the normal installation
1-2. The error appears

2-1. Reboot with the installation CD
2-2. Choose "Rescue a broken system"
2-3. At the end of the recovery process, select "/dev/sda1" and then "execute a shell in /dev/sda1" (in my case "/dev/sda1" was my target partition)
2-4. cd /etc/apt
2-5. vi sources.list
2-6. Comment as described in the above quote

3-1. Reboot with the installation CD
3-2. Do the normal installation
3-3. When you need to choose a target partition, select the option "don't format" (selecting "format it" seems to delete the fix you made at the step 2-6)

Hope it may help.

p.s.
As I misconfigured some settings, I reinstalled the os according to the above process. This time it worked after 3 tries. So please try this when there is no alternative.

However after the reinstallation, I found that the entry in the /etc/apt/sources.list is commented as I did at the step 2-6. So it seems to work but you may have some failures before a success.

---

### Post by Vegan on 2010-12-17
First off, do not bother with a software RAID, its not worth the hastle.

Next, make sure the install CD is OK by using the check CD tool.

Then install from CD to a single disk and you can then mount other disks under other directories when you are done.

---

### Post by LiLoather on 2011-03-17
Have just struck the same problem with a freshly downloaded .iso image and a brand new writable CD blank which was verified by the burner and cleared the check CD test - and I'm really, really unimpressed.

> **Vegan said:**
> First off, do not bother with a software RAID, its not worth the hastle.

That's your opinion.  There are very good reasons for having RAID that have nothing to do with speed.

> **Vegan said:**
> Next, make sure the install CD is OK by using the check CD tool.

Did that.

> **Vegan said:**
> Then install from CD to a single disk and you can then mount other disks under other directories when you are done.

So the bug is that you can't install from the official iso onto a RAID array?

I'm really, really unimpressed.

---

### Post by LiLoather on 2011-03-17
> **LiLoather said:**
> 

So the bug is that you can't install from the official iso onto a RAID array?

I'm really, really unimpressed.

No, that isn't the bug.  I followed the advice to amend the sources.list file, rebooted and the installation hung with just a flashing cursor on my hitting the button to install from the CD.  So I powered down, left it a minute, powered up again and the installation with the same CD in the same drive completed without a problem.

So my best guess is it's some conflict in the installation code re version numbers or some such - which is pretty amateurish.

So I'm still really really unimpressed.

---

### Post by Rackz on 2011-03-17
This I faced when i was installing ubuntu 10.10.

I got the error bcz after the installation i removed the cd. It should be kept loaded even after the installation completes, bcz it loads certain files in the initial stage which are already present in the live cd.


just try it out. The cd mentioned in the  error is the livecd using which the installation is completed.

---

### Post by Rackz on 2011-03-17
> **josh_moore said:**
> Having difficulties installing 10.04 AND 9.10 versions of Ubuntu Server
After reaching Installing Base, after retrieving, unpacking and configuring many files, at 75% the install stops and states
Please insert disc labeled Ubuntu-server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)
or
Please insert disc labeled Ubuntu-server 9.10 _Karmic Koala) - Release amd64 (20091027.2)

If I press Alt+F2 and active that console, I can see the contents of the disc on /cdrom/

This has become very frustrating to fight with so if anyone has suggestions it would be appreciated.
This I faced when i was installing ubuntu 10.10.

I got the error bcz after the installation i removed the cd. It should  be kept loaded even after the installation completes, bcz it loads  certain files in the initial stage which are already present in the live  cd.

its nothing to do with drive i think. 
just try it out. The cd mentioned in the  error is the livecd using which the installation is completed.

---

### Post by chartof on 2011-03-17
Hello, after three different situations (pcs), different version of ubuntu (32, 64) and lot of burned disks....

I tried to install the 10 lts version of ubuntu 32bit x86 server. The above message came over and over again.

1. removed some memory sticks. Same Message, same place.
2. removed all unesessary cards, dissable onboard nics and soundcards and whatever. Same Message, same place.
3. Re download - re burn - re try. Same Message, same place.
4. From the second console unmount /cdrom/ remount , changed disks. Same Message same place.
5. Setup Dvdrom single master. Same Message same place.

**Solution**: I changed the **_DVDROM _**with one simple old no name **_CDROM _**and the installation took place with no problem from the first cd!!!

I believe there must be some incompatibility between devices. 

Or DVDROM reading CD :confused:

---

### Post by c-check on 2011-04-02
I can confirm that, after trying both 10.04 and 10.10 server from various burners and various images, both CD and DVD, on my NEC drive--they all failed.

Switched to a Lite-On drive that I borrowed from work, 10.10 image/CD installed flawlessly the first time.

---

### Post by danstinebaugh on 2011-09-27
I too will confirm that at least in my case it was due to a NEC drive. Strange when I installed debian it worked fine. None the less, an external usb drive I have for my netbook worked just fine and I'm very happy with my install of 11.04

---

### Post by wstrong714 on 2012-03-18
Just adding my 2 cents, for what they are worth....

I tried burning a new disk at the slowest speed possible...No change.

I tried the rescue disk method mentioned above...No luck, as I could not edit the file mentioned.

I tried the trick of removing and reinserting the disk....No luck.

I found an old LG 52x CD drive (Not DVD)... And BINGO.

I am rebooting the system now after finishing the install.

BTW, used the original disk.

10.04 LTS server

---

