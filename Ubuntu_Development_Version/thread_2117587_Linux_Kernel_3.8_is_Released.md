---
title: "Linux Kernel 3.8 is Released"
date: 2013-02-18
forum: Ubuntu Development Version
---

### Post by VinDSL on 2013-02-18
SOURCE:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-raring/)

---

### Post by zika on 2013-02-19
> **VinDSL said:**
> SOURCE:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-raring/)
Seems [img]http://www.sherv.net/cm/emoticons/yes/cool-check-mark-symbol-and-ok-smiley-emoticon.gif[/img]

---

### Post by rrnbtter on 2013-02-19
Greetings,

~ rrnbtter ~
Current Date/Time: Tue Feb 19 09:54:02 EST 2013
Distro Release: Ubuntu Raring Ringtail (development branch)
Linux 3.8.0-030800-generic
Linux version 3.8.0-030800-generic (root@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201302181935 SMP Tue Feb 19 00:46:09 UTC 2013

Interesting! My broken Pulse Audio is now working. Wonder what else?

---

### Post by rrnbtter on 2013-02-19
Greetings,
P.S. I saw the Pulse Audio update in yesterdays downstream.  It didn't work however until I installed the new kernel.
Edit: Sound is working with the new kernel.

---

### Post by Harry33 on 2013-02-19
Well the Linux 3.8 is building ATM in launchpad.
Soon in RR repos.

Here:
[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-7.14](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-7.14)

---

### Post by offgridguy on 2013-02-19
Since i have never done a kernel update {upgrade}?.  i am wondering
what is involved and what comes with it?

---

### Post by craig10x on 2013-02-19
Why bother? It would be coming down automatically in your 13.04 update manager within the next few days anyway...these guys just like to jump on these things right away ;)

Or are you planning on adding it on to a previous version of ubuntu such as 12.04 or 12.10 and want to get the 3.8 kernel? If that's the case, i am sure someone here can outline how to add it... :)

---

### Post by offgridguy on 2013-02-19
> **craig10x said:**
> Why bother? It would be coming down automatically in your 13.04 update manager within the next few days anyway...these guys just like to jump on these things right away ;)

Or are you planning on adding it on to a previous version of ubuntu such as 12.04 or 12.10 and want to get the 3.8 kernel? If that's the case, i am sure someone here can outline how to add it... :)
Thanks for the reply, I suspected that might be the case.
As to adding it on to a previous ubuntu, I have 12.04 and would be
interested  in updating the kernel.  I have read a lot of posts
that resulted in problems from doing that, so some guidance would
be gratefully appreciated.:)

I do plan on installing 13.04 when it is released, so it may be 
better to wait?

---

### Post by dino99 on 2013-02-19
> 
Or are you planning on adding it on to a previous version of ubuntu such as 12.04 or 12.10 and want to get the 3.8 kernel? If that's the case, i am sure someone here can outline how to add it... :)

there is already the ubuntu-x-swat/r-lts-backport ppa to get it in a few days  ):P

---

### Post by offgridguy on 2013-02-19
> **dino99 said:**
> there is already the ubuntu-x-swat/r-lts-backport ppa to get it in a few days  ):P
Thank you, dino99

---

### Post by rrnbtter on 2013-02-19
> **craig10x said:**
> Why bother? It would be coming down automatically in your 13.04 update manager within the next few days anyway...these guys just like to jump on these things right away ;)

Or are you planning on adding it on to a previous version of ubuntu such as 12.04 or 12.10 and want to get the 3.8 kernel? If that's the case, i am sure someone here can outline how to add it... :)

1. It seems to me that there has been more breakage with the repos versions.
2. I like to do things that involve interaction from myself at the command line.  Just a hold over from the old MS Dos days revisited in Linux.  I've found that when trouble arrives it pays to know how to do a few things.
3. You do ask some good questions though!

---

### Post by rrnbtter on 2013-02-19
Greetings,
If you want to try out the kernel you can go to the link at the beginning of this thread.
1. Download either the three I386 files or the three AMD64 files depending on which applies to your system. Also download the file ending with "all.deb". 
2. Copy these files into your Home directory. This will be the directory with Documents and your other working directories. 
3. Open a terminal and enter this command.  sudo dpkg -i linux*.deb
4. The kernel will be installed. 

After you reboot open a terminal and enter "uname -r", you should see the new kernel loaded. 
It is possible that grub will not put the new kernel at the top of the boot list. If this happens hold down the shift key on boot and goto the Advanced Options and choose the new kernel to boot. 

5. If you have a problem you can boot back to an older kernel using the same method. 

6. If you want to uninstall the kernel there are instructions available.

I have loaded these new kernels with systems as old as Lucid so you should not have a problem with the 12 series.

If you want to mess with the development versions it doesn't hurt to get your feet wet on other things.  That just my opinion.

---

### Post by The Spectre on 2013-02-19
This makes it very easy to update...
 
[http://www.upubuntu.com/2013/02/installupgrade-to-linux-kernel-38.html](http://www.upubuntu.com/2013/02/installupgrade-to-linux-kernel-38.html)

---

### Post by zika on 2013-02-19
> **The Spectre said:**
> This makes it very easy to update...
 
[http://www.upubuntu.com/2013/02/installupgrade-to-linux-kernel-38.html](http://www.upubuntu.com/2013/02/installupgrade-to-linux-kernel-38.html)Be careful about using scripts from such places... At least read them before using them. But, if You do understand what is in the script, You really do not need it... Conundrum...

---

### Post by The Spectre on 2013-02-19
> **zika said:**
> Be careful about using scripts from such places... At least read them before using them. But, if You do understand what is in the script, You really do not need it... Conundrum...
Thanks for the Heads Up.
 
This sites Kernel Updates have never let me down and I have probably done over a Dozen Kernel Updates on several different systems.
 
When I first discovered this site I did the Kernel Update to Ubuntu that I have setup in VirtualBox that I use for testing such things as this first. (Just In-case)

---

### Post by nomenkultur on 2013-02-20
will it be possible now that 3.8 is done to continue to update the kernels (like outlined in that site) in 13.04

 I would like the 3.9 kernel and so on just to stay on the wave

---

### Post by Harry33 on 2013-02-20
> **nomenkultur said:**
> will it be possible now that 3.8 is done to continue to update the kernels (like outlined in that site) in 13.04

 I would like the 3.9 kernel and so on just to stay on the wave

I suppose 13.04 will not have 3.9 branch at all. There is no time for that any more.
However, 3.8 branch is by no means done yet.
We may have 3.8.0 now, but there will definitely be 3.8.1 and 3.8.2 ... for bug fixing.

---

### Post by zika on 2013-02-20
> **nomenkultur said:**
> will it be possible now that 3.8 is done to continue to update the kernels (like outlined in that site) in 13.04

 I would like the 3.9 kernel and so on just to stay on the waveJust follow [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and You can have newest kernel every day ([http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/))...

---

### Post by nomenkultur on 2013-02-21
kernel 3.8 has been hard on my intel wireless and gfx


 that's why I wanna see if intel put in some effort in 3.9

---

### Post by JiuJitsu500 on 2013-02-21
Man.... I've heard some bad juju about every point-released-kernel since 3.0 came out! Even Android took forever to switch to 3.x :) That is, if you see android more as linux than java... hybrids always think they have the best of both worlds! Kinda like a java-based OS with a linux kernel, or something :)

I suppose complaints go down often just because the newer versions are so unstable with newer hardware... well no crizznap sherlock!

I've been stuck on 3.2 for the longest until 3.5 decided to break stuff... I'm safer with old kernels on my hardware, and virtualizing new ones, like my ArchBang w/3.6, or my daily raring with 3.8 (which needs work, or my box sucks lol).

I wonder if precise will get it fully integrated by 12.04.3 this August? I've heard those rumors, and I don't see much improvement in newer kernels anyway since my laptop's a year old.

Or maybe 3.9 by the 3rd point release of the new* LTS.... hmmm.....

I wonder what 4.0 will hold in store for planet earth.

---

### Post by Harry33 on 2013-02-22
> **JiuJitsu500 said:**
> 
...

Or maybe 3.9 by the 3rd point release of the new* LTS.... hmmm.....

I wonder what 4.0 will hold in store for planet earth.

Well at least 3.10, 3.11 ... or even 3.30 may appear before 4 branch.

---

### Post by jerrylamos on 2013-02-22
"-7" on today's daily build.  No problem with that, but Unity "de-provements" are still popping up.  This forum is a big help.

For whatever reason lately about half my attempts at Ubuntu install have frozen or crashed, try again, then worked.  Both Pangolin and Ringtail.  I do have 1 or 2 hard drives + USB hard drives and multiple partitions, multiple Ubuntu's, Linux Mint10, etc.

Not show stoppers.

---

### Post by lucazade on 2013-02-23
sound is choppy with 3.8.0-7 (haven't tried previous releases).
anyone else get the same? known issue?

---

### Post by dino99 on 2013-02-23
> **lucazade said:**
> sound is choppy with 3.8.0-7 (haven't tried previous releases).
anyone else get the same? known issue?

a few days ago, after having upgraded to 7 and recently got the latest pulseaudio, on the next boot i got no more sound. Reviewing the sound settings, i've needing to select the good output (analog here) to get the sound back. Now i cant complaint about quality.

---

### Post by jerrylamos on 2013-02-23
> **lucazade said:**
> sound is choppy with 3.8.0-7 (haven't tried previous releases).
anyone else get the same? known issue?

We sure do.  As more and more overhead (Unity?  Eye candy?) is added, audio and video is getting more and more choppy.  Even my fastest 3.33 gHz tower is affected.  In "top" "plugin-containe" is showing up at the top.  What's that?

Microsoft solution, get customers to buy ever faster hardware.  Do note I've got Android running here side by side, and for videos, booting, etc. blazes faster than ubuntu - and ubuntu has the advantage of faster hardware, more memory.  For my level of Android expertise, I can do a whole lot more on ubuntu.

I'm interested in seeing ubuntu on tablets for a side to side comparison, and then can we get that version of ubuntu on pc's?

---

### Post by pqwoerituytrueiwoq on 2013-02-24
> **jerrylamos said:**
> We sure do.  As more and more overhead (Unity?  Eye candy?) is added, audio and video is getting more and more choppy.  Even my fastest 3.33 gHz tower is affected.  In "top" "plugin-containe" is showing up at the top.  What's that?

that is adobe flash

---

### Post by zika on 2013-02-26
It took couple of hours today before trip to local dealer to get another device and an hour after to realize that 3.9-996 (drm-next) produced today does not work with AX88772A USB NIC...
So, to save some other considerable amount of time...
It worked yesterday as a charm... ;) 999 works as usual...

---

### Post by philinux on 2013-02-26
[http://support.acer.com/acerpanam/notebook/2009/acer/aspire/Aspire1410-11.6/Aspire1410sp9.shtm](http://support.acer.com/acerpanam/notebook/2009/acer/aspire/Aspire1410-11.6/Aspire1410sp9.shtm)

My acer 1410 2gig ram is running very smooth flash even full screen. Both audio and video are spot on.

---

### Post by tinsami1 on 2013-02-27
Installed 3.8.0 in 2 machines: an HP G42 laptop and an HP desktop.  In both cases I experience problems with connecting to a wifi hotspot using WPA/WPA2 -- the laptop to our office wifi and the desktop to my home wifi.

Kernel 3.7.9 works ok, though.  I will check the daily builds every now and then to see if this will get fixed eventually.

---

### Post by jerrylamos on 2013-02-27
> **pqwoerituytrueiwoq said:**
> that is adobe flash

Using "top", there's a whole lot of other raring stuff running besides flash when viewing the choppy videos.  I haven't done a print out comparison against, say, Meerkat.  No point wasting my time, Ubuntu's going to do what they want to do.  Not sure what Ubuntu uses for feedback.  Some of us on this forum are pretty convinced it is not us.  Real value of the forum I get is interaction with other forum users and a lot of real help.  As is stated in this forum, the developers don't pay attention to the forum.

---

### Post by jerrylamos on 2013-02-27
> **tinsami1 said:**
> Installed 3.8.0 in 2 machines: an HP G42 laptop and an HP desktop.  In both cases I experience problems with connecting to a wifi hotspot using WPA/WPA2 -- the laptop to our office wifi and the desktop to my home wifi.

Kernel 3.7.9 works ok, though.  I will check the daily builds every now and then to see if this will get fixed eventually.

I've been fighting WPA/WPA2 encrypted network connection problems with both intel and broadcom.  The kernel is just fine.  The problems are all with Network Manager.  NM will see the network.  NM recognizes that "secrets" as they call it are required.  NM has the "secrets".  Then NM decides to disconnect instead of connect, even though it has everything it needs and "enable wireless" is enabled.

Seems to me it's a conscious policy change by Network Manager in Raring.  Precise works just fine, as does Linux Mint 14.  And of course Android is very much faster at connecting than Ubuntu, even though my Androids have slower hardware.

One of my several launchpad bug entries is #1097002.  No interest from development.

---

### Post by tinsami1 on 2013-02-27
> **jerrylamos said:**
> I've been fighting WPA/WPA2 encrypted network connection problems with both intel and broadcom.  The kernel is just fine.  The problems are all with Network Manager.  NM will see the network.  NM recognizes that "secrets" as they call it are required.  NM has the "secrets".  Then NM decides to disconnect instead of connect, even though it has everything it needs and "enable wireless" is enabled.

Seems to me it's a conscious policy change by Network Manager in Raring.  Precise works just fine, as does Linux Mint 14.  And of course Android is very much faster at connecting than Ubuntu, even though my Androids have slower hardware.

One of my several launchpad bug entries is #1097002.  No interest from development.

It could well possibly an incompatibility between NM and kernel 3.8 due to a change in the kernel from v3.7 that NM devs still has to address.  I would imagine that they'll get to it once RR enters beta next month.  I would probably file a bug then (or +1 an already filed bug) if it hasn't been fixed by then.

---

### Post by screaminj3sus on 2013-02-28
Has anyone else had trouble getting 5ghz channel bonding working with intel wireless + kernel 3.8? Works fine for me with quantal's kernel, but not in raring: [http://ubuntuforums.org/showthread.php?t=2121042](http://ubuntuforums.org/showthread.php?t=2121042)

---

### Post by jerrylamos on 2013-02-28
> **tinsami1 said:**
> It could well possibly an incompatibility between NM and kernel 3.8 due to a change in the kernel from v3.7 that NM devs still has to address.  I would imagine that they'll get to it once RR enters beta next month.  I would probably file a bug then (or +1 an already filed bug) if it hasn't been fixed by then.
I've tried several different kernels.  It's the NM problem.  Once NM finally gets around to "authenticate" the network logs in normally.  Looking at the syslogs, all along from the start of Raring, NM does not automatically log in to a hidden wireless network while Pangolin does.  It's not the kernel.  As posted in the bug, NM quits.  On both netbook and notebook, two different sets of network hardware.

Looking back at the postings from whoever, Network Manager types never look at the bug.

Kernels all along have been fine, once NM gets around to issuing the authenticate it does connect.  The kernel works fine when it is given the commands to do so.  

Sometimes the Network Manager tries to connect to the network without using the WPA key that NM has already, doesn't get a response of course, and posts "Out of Range".  It isn't.  NM didn't use the key.  I go to systems settings network, click on other, there's the network.  Select it.  Seconds go by, then NM shows the password, I click on the drop down, and it connects.  Finally.  Using all the info NM already has.

Same network, same hardware, Pangolin and Linux Mint 14 no problem.

---

### Post by zika on 2013-03-02
[http://kernel.ubuntu.com/~kernel-ppa/mainline/linux-3.5.y.z-review/](http://kernel.ubuntu.com/~kernel-ppa/mainline/linux-3.5.y.z-review/)  (amd_64) works surprisingly well for 3.5 ...
I wonder what is inside...

---

### Post by VinDSL on 2013-03-02
> **zika said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/linux-3.5.y.z-review/](http://kernel.ubuntu.com/~kernel-ppa/mainline/linux-3.5.y.z-review/)  (amd_64) works surprisingly well for 3.5 ...
3.8.1 mainline kernel (i686) seems to be working well, too. ;)

SOURCE:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.1-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.1-raring/)

---

### Post by zika on 2013-03-02
> **VinDSL said:**
> 3.8.1 mainline kernel (i686) seems to be working well, too. ;)

SOURCE:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.1-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.1-raring/)Waiting for 3.9 in a (literally) couple of days...

---

### Post by pqwoerituytrueiwoq on 2013-03-02
anyone had any issues with 3.8.1 mainline 64bit and nvidia (gtx 550 ti) hdmi audio?
i transplanted a raring install and it is arguing with me, it warrants further testing (i rebooted to it after i had it working on a older kernel and it worked, but after another reboot it quit again)
i normally just rig it to use analog audio since it just works and never argues, but this is testing
all open source drivers in use
hdmi audio worked as of ubuntu 11.04 for my gpu

---

### Post by tinsami1 on 2013-03-11
> **jerrylamos said:**
> I've tried several different kernels.  It's the NM problem.  Once NM finally gets around to "authenticate" the network logs in normally.  Looking at the syslogs, all along from the start of Raring, NM does not automatically log in to a hidden wireless network while Pangolin does.  It's not the kernel.  As posted in the bug, NM quits.  On both netbook and notebook, two different sets of network hardware.

Looking back at the postings from whoever, Network Manager types never look at the bug.

Kernels all along have been fine, once NM gets around to issuing the authenticate it does connect.  The kernel works fine when it is given the commands to do so.  

Sometimes the Network Manager tries to connect to the network without using the WPA key that NM has already, doesn't get a response of course, and posts "Out of Range".  It isn't.  NM didn't use the key.  I go to systems settings network, click on other, there's the network.  Select it.  Seconds go by, then NM shows the password, I click on the drop down, and it connects.  Finally.  Using all the info NM already has.

Same network, same hardware, Pangolin and Linux Mint 14 no problem.

SOLVED my WiFi with Precise + Kernel 3.8/3.9 by backporting the libnl-3 and NM packages from quantal.  Haven't gotten to testing it out fully, but it now connects.

I backported just NM from quantal first, but it still won't connect.  To backport NM from raring, I had to backport libnl-3 too.  But after finishing libnl-3 backport, I tested it out and it now connects.

---

### Post by tinsami1 on 2013-03-11
> **tinsami1 said:**
> SOLVED my WiFi with Precise + Kernel 3.8/3.9 by backporting the libnl-3 and NM packages from quantal.  Haven't gotten to testing it out fully, but it now connects.

I backported just NM from quantal first, but it still won't connect.  To backport NM from raring, I had to backport libnl-3 too.  But after finishing libnl-3 backport, I tested it out and it now connects.

Crap!  Turned off the laptop overnight and now it won't connect again.  Last night must have been a fluke.

[EDIT: after a few minutes]  It works again!  After NM gave up, I reconnected again and voila!  I will proceed to backport raring's version of NM and see how that goes.

---

### Post by zika on 2013-03-15
3.8.3 is [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.3-raring/)...

---

### Post by The Spectre on 2013-03-15
> **zika said:**
> 3.8.3 is [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.3-raring/")...

Working Beautifully...

[ATTACH=CONFIG]240202[/ATTACH]

Thanks!

---

### Post by denis-korzun on 2013-08-24
sudo apt-get install linux-image-generic-lts-raring
sudo apt-get install linux-headers-generic-lts-raring

---

### Post by cariboo on 2013-08-24
> **denis-korzun said:**
> sudo apt-get install linux-image-generic-lts-raring
sudo apt-get install linux-headers-generic-lts-raring

When coming in from a google search, I'd suggest you check what sub-forum you are in. This is the U+1 sub-forum, we are currently test Saucy, which just updated the kernel to 3.11.0-3.8

---

