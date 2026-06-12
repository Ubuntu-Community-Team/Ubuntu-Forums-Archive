---
title: "poll : Did you upgrade to Dapper or reinstall ? Did you encounter problems?"
date: 2006-06-02
forum: The Cafe
---

### Post by ubuntu_demon on 2006-06-02
Did you upgrade to Dapper or reinstall ?

IMHO in most of the cases update-manager (or another graphical tool) works easy and fine to dist-upgrade.
IMHO in most of the cases in which update-manager (or another graphical tool) doesn't work upgrading by hand is not very hard. Especially if you read these before upgrading :
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

IMHO the amount of people who have big problems is not very high. But it seems high because :
-(let's say) 5% of our users is still more than 1000 people.
-people with problems are naturally more vocale here than people without problems. Because if you don't have problems there isn't much to talk about. So those 5% of users may **seem** to be 10% of our users if you look at the amount of threads about people with problems.

But I could be completely wrong. That's why I started this poll. To get an idea about real percentages.

The choices :

*I installed Dapper from cd and I have encountered big problems.
*I installed Dapper from cd and I have encountered some small problems.
*I installed Dapper from cd and I haven't encountered any problems at all.
*I dist-upgraded Breezy to Dapper using a graphical tool and I **have** encountered big problems.
*I dist-upgraded Breezy to Dapper using a graphical tool and I have encountered some small problems.
*I dist-upgraded Breezy to Dapper using a graphical tool and I haven't encountered any problems at all.
*I dist-upgraded Breezy to Dapper from the terminal and I **have** encountered big problems.
*I dist-upgraded Breezy to Dapper from the terminal and I have encountered some small problems.
*I dist-upgraded Breezy to Dapper from the terminal and I haven't encountered any problems at all.
*Other

Here is a thread which with help :
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

Please post your tips and/or fixes here :
[http://www.ubuntuforums.org/showthread.php?p=1086319](http://www.ubuntuforums.org/showthread.php?p=1086319)

**edit:**
**haven't** encountered big problems should be **have** encountered big problems(twice)

---

### Post by John.Michael.Kane on 2006-06-02
Tried dist-upgrade from earlier flights, and it went fine. also did a fresh install from cd  it went fine. *results not typical* every enduser will exprince something diffrent, from whatever method they use.


Just my thoughts...

---

### Post by Arktis on 2006-06-02
Typicly, a fresh install is better in my experience.  I am downloading the iso right now, and will do that when it's done.  

FYI, been with dapper since flight 3 without any fresh installing, and it's run spectacularly the whole time.

---

### Post by Rikostan on 2006-06-02
dist-upgraded on three different machines. Two of them went without a hitch, the third had an issue with the nvidia drivers that was easily fixed.

---

### Post by AndyCooll on 2006-06-02
I originally upgrade Breezy to Dapper (last weekend), however that made my system unusable. I then used the RC ISO and did a clean install and that has been almost perfect. 

Just had an issue with my ati graphics card. It installed ok, recognises my graphics card ok,  and indeed works ok too ...until I try putting one of my other pc's desktops on to gui's F9-F12. They just topple over and plonk me back on to my F7 desktop again. So I reconfigure my graphics to use vesa and this time there are no problems. 

:cool:

---

### Post by Klaidas on 2006-06-02
I installed Dapper from cd and I haven't encountered any problems at all. ;)
Well, my sound didn't work, but I found that default selected sound device was not correct. So I just selected another device and it worked :)
I don't think that can be counted as a problem.

---

### Post by fuscia on 2006-06-02
the laptop i ordered, with dapper installed, is due to arrive in the next week sometime.

---

### Post by Brunellus on 2006-06-02
I dist-upgraded from breezy to dapper at about feature-freeze time, and encountered some minor problems.  That was in march, though, mind you.

of course, I might not know what i'm missing, since apparently the cool kids are no longer using apt-get dist-upgrade.

---

### Post by ember on 2006-06-02
I was about to try an install - still I cannot boot from the cd without playing around with boot parameters. That's a bit disappointing.
I guess, I'll wait another two weeks or so for switching my production machines.

---

### Post by digitalkarabao on 2006-06-02
I voted other because I am yet to upgrade to Dapper. The reason? I connect via dial-up at home and I cannot upgrade via apt-get dist-upgrade because it will take an eternity. :)  I downloaded the Dapper ISO and tried upgrading to Dapper by adding it as a repo in Synaptic but someone in the forums said this is no longer possible using the Alternate CD (Live and Install CD of Dapper).  Is this really not possible guys? Do I really have to choose either to install a fresh copy of Dapper or upgrade via apt-get dist-upgrade via a broadband connection?

---

### Post by Brunellus on 2006-06-02
[QUOTE=digitalkarabao]I voted other because I am yet to upgrade to Dapper. The reason? I connect via dial-up at home and I cannot upgrade via apt-get dist-upgrade because it will take an eternity. :)  I downloaded the Dapper ISO and tried upgrading to Dapper by adding it as a repo in Synaptic but someone in the forums said this is no longer possible using the Alternate CD (Live and Install CD of Dapper).  Is this really not possible guys? Do I really have to choose either to install a fresh copy of Dapper or upgrade via apt-get dist-upgrade via a broadband connection?[/QUOTE]
it should be possible to dist-upgrade using only the CD as the repository.

---

### Post by digitalkarabao on 2006-06-02
I get it. I have downloaded the Desktop ISO and not the Alternate install ISO. The alternate install ISO allows upgrading from older installations without network access. Will try again tonight. Whew!

---

### Post by Carrots171 on 2006-06-02
I upgraded using the terminal because upgrading using the graphical update manager "wasn't ready yet" when I tried. 

The update had 3 minor problems:
1. It broke X. I had to re-install the Nvidia drivers to get it to work. 
2. It messed up the permissions of my /etc/apt/sources.list, and that broke my update-notifier and "Add/Remove Applications" thing, so I had to change the permissions.
3. OpenOffice was removed, so I had to install it again. 

Besides that, the upgrade worked great!

---

### Post by jamespi on 2006-06-02
[QUOTE=Carrots171]I upgraded using the terminal because upgrading using the graphical update manager "wasn't ready yet" when I tried. 

The update had 3 minor problems:
1. It broke X. I had to re-install the Nvidia drivers to get it to work. 
2. It messed up the permissions of my /etc/apt/sources.list, and that broke my update-notifier and "Add/Remove Applications" thing, so I had to change the permissions.
3. OpenOffice was removed, so I had to install it again. 

Besides that, the upgrade worked great![/QUOTE]

man i have everyone one of those problems too!!! i didnt even know about the sources permission one, but checking its screwed like yours!

the REAL nightmare was dapper broke my ADSL modem. its an alcatel speedtouch 330, which i set up manually using a howto for breezy. dapper doesnt use the hotplug system that breezy has, therefore the firmware files for my modem needed to be moved from /lib/hotplug/firmware to /lib/firmware to get it to work. and possibly my dialing script needs editing down due to dapper automatically initialising the firmware now but i'm not sure yet. its a bloody good job i stil have win2k on my disc for emergencies or i'd be really really pissed off. an inoperational modem is the only insurmoutable obstacle with linux, cos without a modem, you cant look up any solutions.

---

### Post by jamespi on 2006-06-02
for the curious the following command fixes the source.list permissions:

sudo chmod 644 /etc/apt/sources.list

---

### Post by Jucato on 2006-06-02
First used the GUI to dist-upgrade, ran into problems. It wanted to remove 205 packages, most of which were KDE stuff (running Kubuntu). Made a safe upgrade first, rebooted, and couldn't get into KDE anymore. So after that I had to use the CLI. Still asked me to remove 205 packages. I said yes and it upgraded. I then reinstalled kubuntu-desktop to get my KDE stuff back. Lucky for me, that went smoothly. But then I couldn't get into X without doing dpkg-reconfigure xserver-xorg everytime I reboot. I found out after some snooping that it was insisting on setting up X server with settings for wacom tablets, even if I didn't have any. Was able to fix that, and was able to successfully boot into Dapper.

So basically those were the problems I encountered. Took me about 14 hours to upgrade everything that had to be upgraded, which was around 1000 packages/libs. That was on a 256kbps broadband connection. :p

---

### Post by papangul on 2006-06-02
My latest dapper install is a hd-media based reinstall. While something seemed to be broken during install (see [http://ubuntuforums.org/showthread.php?t=172631](http://ubuntuforums.org/showthread.php?t=172631) ), I have no problem whatsoever with the installation.

In fact, today, for the first time in history of my current Dapper installation , something crashed - the update manager crashed while it was working a little while ago.

---

### Post by FredSambo on 2006-06-02
i just yesterday upgraded my test web server from breezy to dapper using dist-upgrade in putty from my home windows machine.  if all goes well in the next few weeks i'll upgrade my other servers!

so far so good!

---

### Post by BoneKracker on 2006-06-02
Other:

On my 686, I did both, without problems.
I had upgraded to the beta, and the reinstalled when it went final - no problems.

On my PowerPC, I did both, without problems.
Same as above.

On my AMD64 dual-core raid0, I did both.
Upgrade - kernel panic - upgrade choked on my dmraid setup
Install, crashed.  No dmraid support, had to manually debootstrap and configure.

---

### Post by MrChips on 2006-06-03
No probs as of yet.  

And I am still updating the BETA.  Dapper has been the most trouble free open source distro that I have tried to date. :KS

---

### Post by RavenOfOdin on 2006-06-03
(EDIT: Never mind, I take that all back :) Still voted #4 though.)

---

### Post by K.Mandla on 2006-06-03
- I did one *dist-upgrade* and it worked fine, although I wasn't thrilled with the amount of leftover crud I had from the Breezy installation, so I started over from scratch.

- I installed a 6.06 server, then installed xubuntu-desktop. No problems there, either.

- I installed Xubuntu straight from CD and it went very cleanly. I think this might be my preferred method, only because of the amount of time it takes to download a *dist-upgrade*. I can just blank the partition and start from scratch in about a third of the time it takes to *apt-get* it all. But that should go without saying. :)

---

### Post by confused57 on 2006-06-03
I had no problem with dist-upgrade of a Breezy server install:

changed sources.list to "dapper"
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by wmcbrine on 2006-06-03
I started out using Update Manager... it got about two-thirds of the way through, then errored out. I finished via a combination of apt-get and Synaptic. I had a hard time getting past an error about coreutils, which I resolved by removing md5sum.textutils.1.gz. (WTF?)

On that note... does anyone know what package provides ldd? (And for future reference -- how would I find out?) I also had to remove it, to be able to upgrade ia32-libs (I'm running AMD64), but unlike the md5sum man page, it didn't come back.

Despite a rocky process, everything seems to be working OK now.

Edit: Spoke too soon... I also had to reinstall OpenOffice.

---

### Post by vertigo on 2006-06-03
I dist-upgraded Breezy to Dapper from the terminal and I have encountered big problems. It keprt saying i had problems with xconfig, ive never looked at that and couldnt get on the internet to try and solve it. luckily I'd already burnt the dapper disk and installed from there with no problems at all

---

### Post by isotonic on 2006-06-03
i used the update manager on two machines and had no problems at all - even with a ton of other apps running.:D

---

### Post by PatrickMay16 on 2006-06-03
I dist-upgraded from breezy to dapper yesterday using the terminal and encountered a small depencency problem. Some old package I had installed that had been around since I had Hoary was causing it.

Because of that problem it seemed the upgrade process stopped halfway through, so I ran
"sudo apt-get install -f"
then again:
"sudo apt-get dist-upgrade"
to make sure, but I dunno if that second command was needed or if it did anything at all.

Then I used synaptic to remove the package which was causing problems, and everything now seems to be working great. Apart from that, there were no problems at all.

Ya know... in case anyone's wondering.

Just FYI

---

### Post by angkor on 2006-06-03
I actually did both.

I dist-upgraded my breezy, but since I got my new hardware yesterday I reinstalled dapper fresh and clean.

I dist-upgraded using apt and I only encountered small problems during the upgrade. (one dpkg installed .deb needed to be removed to be able to continue). After the upgrade everything just worked except for gdm.

I reinstalled the graphical way. It was completely painless. Really no problems at all. The partitioning was confusing at first since I'd never used gparted before but after having a look at aysiu's installation guide that was easy as well.

I'm happily running my new dapper install now. :)

---

### Post by wmcbrine on 2006-06-03
[QUOTE=wmcbrine]On that note... does anyone know what package provides ldd?[/QUOTE]To answer my own question: It's in libc6. I still don't know how to search the database for a provided file, though (I just looked at some likely packages). I know how to do it for RPM, but that doesn't help me here. :)

---

### Post by angkor on 2006-06-03
[QUOTE=wmcbrine]To answer my own question: It's in libc6. I still don't know how to search the database for a provided file, though (I just looked at some likely packages). I know how to do it for RPM, but that doesn't help me here. :)[/QUOTE]

You can install 'apt-file'. 

```
sudo apt-get install apt-file
```

You can search the packages for a filename after you've updated apt-file:

```
sudo apt-file update
```

```
apt-file search {filename}
```

---

### Post by basketcase on 2006-06-03
I installed one of the betas, and just kept updating.  

NO issues what so ever!  Couldn't be happier!

---

### Post by sophtpaw on 2006-06-03
Upgraded from Breezy bringing my much like customization and configuration and data over, using alt+F2 and something update manager.

Things seems fine. Played with networking my wireless and my computer went into a loop.

Had to get my live cd (Slax killbill edition) get in there and download a Dapper cd and do a fresh install. Managed to save my data by again accessing through live cd and saving it to a partition. 

So, all was not lost but i wasn't happy for quite a while. Still a bit moody about it in fact, but my system is coming back together again. 

You see i get attched to my customization. Over time my system becomes something worn in like a favourite pair of shoes or something. I like the familiarity.

I felt let down by Dapper. I did nothing evil and was punished

---

### Post by mrcowcow on 2006-06-03
I did an apt-get dist-upgrade on my server, and it went almost perfectly. The only problems I encountered was that the sources were not recognised at first, and the connection to security.ubuntu.com was lost with 144kb of packages left to get. Other than that, it went great and it works great now.

---

### Post by Kimm on 2006-06-03
I voted "I dist-upgraded Breezy to Dapper from the terminal and I have encountered some small problems."

But I think "small problems" is a quite relative term (I doubt a "noob" could handle them, but I could). My dist-upgrade took about 6 hours (I've got a fast fiberoptical connection) and I had several package issues, mostly caused by me building and installing non-standard packages, so I mostly fixed the problems by making empty dummy packages and replacing the "trubblemakers".

My custom kernel stoped working aswell (primarily the NVIDIA drivers stooped working, reinstall didnt work), but the Dapper kernel was fairly up-to-date anyway, so I didnt care much about that.

---

### Post by _Graven on 2006-06-03
I dist-upgraded Breezy to Dapper using a graphical tool and I have encountered big problems.

Ok, so it's not that much of a big problem, except I'm kinda new at this... have to reinstall the nvidia drivers. Too sleepy to look for tseliot's howto on installing the nvidia, so I'll do it in the morning.

---

### Post by grsing on 2006-06-03
Both.  Upgraded with terminal on the desktop, worked mostly fine, minor video problems that were easily fixed.  New install on the laptop (old one was pretty mangled from my noobness and trying to make WPA work), worked perfectly.

---

### Post by xmastree on 2006-06-03
Major problems here...

I followed what it said in the wiki, but...
```
chris@xmastree:~$ sudo gedit /etc/apt/sources.list
Password:
chris@xmastree:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [abb8ee312168787d4a47f14506173a25-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
Found label 'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
This disc is called:
'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
Copying package lists...gpgv: Signature made Wed 31 May 2006 11:06:22 PHT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu .com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main re stricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
chris@xmastree:~$ sudo apt-get update && sudo apt-get dist-upgrade
Ign http://wine.sourceforge.net binary/ Release.gpg
Ign http://deb.opera.com etch Release.gpg
Hit http://wine.sourceforge.net binary/ Release
Ign http://wine.sourceforge.net binary/ Packages
Ign http://deb.opera.com etch Release
Ign http://deb.opera.com etch/non-free Packages
Hit http://wine.sourceforge.net binary/ Packages
Hit http://deb.opera.com etch/non-free Packages
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:4 http://security.ubuntu.com dapper-security Release [19.6kB]
Get:5 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Get:6 http://archive.ubuntu.com dapper Release [34.8kB]
Get:7 http://security.ubuntu.com dapper-security/main Packages [14B]
Get:8 http://archive.ubuntu.com dapper-updates Release [23.4kB]
Ign http://packages.freecontrib.org dapper Release.gpg
Get:9 http://security.ubuntu.com dapper-security/restricted Packages [14B]
Get:10 http://security.ubuntu.com dapper-security/main Sources [14B]
Get:11 http://security.ubuntu.com dapper-security/restricted Sources [14B]
Get:12 http://security.ubuntu.com dapper-security/universe Packages [14B]
Get:13 http://security.ubuntu.com dapper-security/universe Sources [14B]
Ign http://packages.freecontrib.org dapper Release
Get:14 http://archive.ubuntu.com dapper-backports Release [19.6kB]
Ign http://packages.freecontrib.org dapper/free Packages
Ign http://packages.freecontrib.org dapper/non-free Packages
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://packages.freecontrib.org dapper/non-free Sources
Ign http://kubuntu.org dapper Release.gpg
Get:15 http://archive.ubuntu.com dapper/main Sources [255kB]
Get:16 http://packages.freecontrib.org dapper/free Packages [550B]
Get:17 http://packages.freecontrib.org dapper/non-free Packages [2342B]
Ign http://kubuntu.org dapper Release
Get:18 http://packages.freecontrib.org dapper/free Sources [321B]
Ign http://kubuntu.org dapper/main Packages
Get:19 http://packages.freecontrib.org dapper/non-free Sources [478B]
Err http://kubuntu.org dapper/main Packages
  404 Not Found
Get:20 http://archive.ubuntu.com dapper/restricted Sources [1478B]
Get:21 http://archive.ubuntu.com dapper/universe Sources [975kB]
Get:22 http://archive.ubuntu.com dapper/universe Packages [2458kB]
Get:23 http://archive.ubuntu.com dapper/main Packages [619kB]
Get:24 http://archive.ubuntu.com dapper/restricted Packages [4571B]
Get:25 http://archive.ubuntu.com dapper/multiverse Packages [95.2kB]
Ign http://archive.ubuntu.com dapper/multiverse Packages
Get:26 http://archive.ubuntu.com dapper-updates/main Packages [6196B]
Get:27 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:28 http://archive.ubuntu.com dapper-updates/main Sources [3947B]
Get:29 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:30 http://archive.ubuntu.com dapper-backports/main Packages [14B]
Get:31 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:32 http://archive.ubuntu.com dapper-backports/universe Packages [14B]
Get:33 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Get:34 http://archive.ubuntu.com dapper/multiverse Packages [121kB]
97% [34 Packages gzip 0]                                             17.4kB/s 5s
[COLOR="Red"]gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Fetched 4541kB in 3m55s (19.3kB/s)
Failed to fetch http://kubuntu.org/packages/kde351/dists/dapper/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)[/COLOR]
Reading package lists... Done
[COLOR="Red"]E: Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR]
chris@xmastree:~$


```
So, I'm back at the prompt. :confused:

---

### Post by Rumor on 2006-06-03
I installed from the CD so that I am currently dual booting breezy/dapper. I wanted to make sure I could share my printer so that the rest of my family can print to it and get the nvidia drivers working (I was not able to with flight 6).

So far, everything has gone very smoothly. Today I backed up my home directoy and will wipe both hard disks tomorrow and do a fresh, new install.

---

### Post by ubuntoy on 2006-06-04
I was excited about dapper like it is when warty >to> breezy. but it was different this time. the live boot first before install dapper is brilliant, and the installation is now in dapper desktop live. some problems i encountered:

Partitioning:
i have one hdd with important file with it and a non-working dapper partition(thanks to nvidia installation). now removing that non-working partition is hard, you cant select "partition the largest free space" because there is no free space. so you have to select "manual partition", so i just delete the non-working partition there, the problem is the "auto partition the selected free space" in the "manual partition" is gone. so you have to manually allocate the ext3 and swap partition which since warty i dont manually allocate but use the "auto partition the selected free space". so what i did is delete the non-working partition then press back and select "partition the largest free space", the problem is the deletion of the non-working partition is undone. so it wont work there is no free space. and no additional information on which partition to be created/formatted and how much space, it just says "Warning the selected partition will be deleted and important files might be erased".

Nvidia drivers:
The old driver which i always used no longer works nvidia-glx (7667) and nvidia settings. there is a guide that lets you install (8762) but my system hangs after 10 seconds when the desktop loads. i;ve installed nvidia and messed up my system and reinstall dapper 5 times now. i need to install it so the the screen will go in the middle by default instead of fixing it with the monitor settings.

My breezy was a complete working desktop, now with dapper im back to zero. good thing its LTS. probably i'll wait for a month

---

### Post by eqisow on 2006-06-04
I've been running my current install since Hoary (that's 2 upgrades) with no problems. :)

---

### Post by TrendyDark on 2006-06-04
Other:

I had installed Ubuntu Dapper Drake RC1 and upgraded flawlessly.

---

### Post by dada1958 on 2006-06-04
I installed Dapper on three machines without problems; my desktop, my web server and yesterday night on my new secondhand laptop. I used the text based installer on the alternate CD though...

---

### Post by Xilon on 2006-06-04
I kinda did two actually...
I was dist-upgrading from breezy into one of the earlier flights and dist-upgrading to the TLS since then, but at that stage I thought that my install was a bit bloated and had heaps of crap that I didn't need or use (was my first time with ubuntu and pretty much with linux) so I reinstalled from scratch... works a hell of a lot faster than when upgrading from breezy :P

Edit: Didn't encouter any problems with either.

Congratulations and thank you for this fantastic Distro :D

---

### Post by MaX on 2006-06-04
Two actually, I apt-get dist-upgraded my 64-bit system from dapper alpha/beta and that worked fine.

Now I wanted to switch my system to a 32-bit one... gparted can't find the partitions on one of my disks, specificaly the one that ubuntu currently resides in. if I do a  new partition table on it will delete the 147GB partition that's NTFS and I don't want that.

fdisk finds the partitions alright but not gparted.

---

### Post by ComplexNumber on 2006-06-04
last night i downloaded and burnt the Desktop CD to disk. all went well untill  just after the partitioning(i resized my home partiotion and allocated the free 10GB to dapper)  when the installer crashed all  of the 3 times that i tried, and wouldn't go any further. since then, my home directory has been wiped out and i can't log into any terminal in my fedora installation - it keeps on saying "failed to load child process"....so i can't run any terminal. not even xterm. i even tried failsafe, but it wouldn't have it. looks like a fedora core 5 reinstall if i can't sort out the mess that dapper has created.

conclusion: i hate dapper! if the can't even get as far as installing the packages, then it gets a 1/10.

---

### Post by nejode on 2006-06-04
Did a fresh install using the Live CD and evrything worked out OK (this time... the beta Live install didn't work!).  The only drawback is that it took about 3 hours to download the spanish language packs.  I can understand the servers are overwelmed, so there should be a way you could download the language packs, burn them to a CD and tell the installer to look for them locally.  It would save a lot of time  if you had to setup many machines.  The other way around is to install in Inglish and later install the missing language debs on each machine one by one... that would be a pain and a waste of bandwith,  not to mention the higher download server usage.  Any sugestions??  By the way, would the DVD have those language packs?

---

### Post by paul cooke on 2006-06-04
I used the update manager tool... but not without taking some precautions first:

1 ) took the opportunity to prune my mail then copied the Mail folder to another partition
2 ) backed up my entire .KDE folder to that same partition
3 ) reverted my graphics driver to the Ubuntu supplied nv rather than the self installed one from nvidia
4 ) unpinned my kernel and sources and did a normal breezy update to get everything correctly up to date
5 ) rebooted to get the kernel into memory

6 ) then ran update manager and accepted the upgrade option...

7 ) came back some 4 hours later (had gone out for a meal with friends. They were amazed when I said my OS was quietly upgrading itself as we ate)

8 ) found it had stopped on some scripts that were different and I went and copied the diffs to text files for later perusal (one was hdparm and the other was gdm conf) Must put my changes back into those.

9 ) went to sleep on it as I'd forgotten to comment out the prelink that runs after every update or install using synaptic...

10 ) woke up the next morning and rebooted it into dapper... 8) 

the other two boxes were already on dapper as they'd been on the bleeding edge from when dapper had opened up. They're waiting for the off with Edgy...

---

### Post by futz on 2006-06-04
Just for fun, I dist-upgraded from Breezy to Dapper and it started out ok, but soon went bad with a screwy error. Attempts to fix the problem made things worse and worse until soon I couldn't go back or forward or even reboot.

I stupidly hadn't backed up my home dir, so I had to boot to a recovery terminal and backup my files from the command line. Of course I tried doing it with a live disk, but couldn't remember how, so I did it the slow, painful way with mkdir, mv *.* and such.

Then a quick format/full install, put the files back, fix the file ownerships and an automatix run later and it all works great now. So back up your files BEFORE you upgrade, or you may be sorry! :mrgreen:

---

### Post by whatrucrazy on 2006-06-04
i tried both install/updates. first i changed the 'breezy' to 'dapper' in my sources.list then after apt-get updating ran the update manager. unfortunately i had a few issues: the dowload speed was slow, it looked as though it was going to take at least 6 hrs to update the system, so i ran it overnight but found - like others - that the update stopped to confirm replacement of some config files, which meant the process actually took something like 12 hours. that was bearable though.
the real issue came when i rebooted and found the system didn't look like the 6.06 installs i had seen on my testing box, that kinda worried me...
so i ended up copying my /home dir to my other hard drive, wiping the root dir and running a clean install from the iso. results - fantastic. those programs that i didn't want to waste ages re configuring i simply copied the cfg from the backup /home dir (ie thunderbird, including emails), and they were perfect. once i had run bumps and automatix, the system was good to go.

given all this i'd recomend a clean install, not to say an update wouldn't be fine (maybe it's a matter of to many years of paranoid MS use), but i just feel more comfortable like that - especially if you can do a backup to another partition.

good work on dapper developer crew, cheers.

---

### Post by neoflight on 2006-06-04
[QUOTE=ubuntu_demon]
IMHO the amount of people who have big problems is not very high. But it seems high because :
-(let's say) 5% of our users is still more than 1000 people.
[/QUOTE]

****...fresh install ....****

problems? not significant ... reason for them is myself trying to tweak...esp...xgl/compiz stuff, emacs, fonts etc....this is the 3rd time i am reinstalling the LTS since the release... i will do it once again and then will probably stop for sometime.... my hard drive has seen so many formats since i started using linux from oct 2005..

BUT, LTS helped me help some of my friends convert from suse. 
thts because of the minimalistic problem density. (on both time and usage scale) ...
the happy curve is going up...with ocational downgrades due to tweaking, inexperience etc....:mrgreen:

---

### Post by MLX on 2006-06-04
I dist-upgraded using the graphical tool and everything went well except for Mplayer not working. I uninstalled Mplayer and followed this
[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")
Now I am using totem Xine and all is working well

---

### Post by gray-squirrel on 2006-06-05
I installed Dapper side-by-side with a previous version of Kubuntu and Windows ME (currently corrupted) with the Desktop CD.

I had a hard time deciding whether to use that or the Alternate CD (especially with the reported problems posted).

One minor problem during installation.  I planned to create a 1.5G swap partition out of the remaining space on the Kubuntu 5.04 partition and have both versions share it.  As that space was sitting on hda, I couldn't do the partitioning within Kubuntu 5.04.  So, I decided to deal with that from the Desktop CD, during installation.  For some reason, though, QtParted refused to see  hda partitions, so I just 

```
sudo aptitude install gparted
```

to install, run, and fortunately repartition so as to allow for a swap partition.  Then I went to do the install from the Desktop CD.  Surprisingly, it only took just under 10 minutes.

I was able to reboot, but I need to figure out how to skip the checking of my FAT32 partitions (I would like to handle that stuff in Windows using Norton Systemworks' boot CD).

More good news after booting: it was very fast, the display was easier on my eyes, and. . . it detected the VIA KM400 graphics and put me into 1024x768 without any intervention on my part.  (It didn't happen with Kubuntu 5.04 and after weeks of trying to get things set right as far as 3D and DRM went on this VIA chip, I didn't want to do anything to mess it up again and decided not to install 5.10)

The only problem, post-installation (so far) is that while my sound cards (Sound Blaster Live 24 bit and Audigy 2 NX) have been detected, I have no sound.  That was the case even when I booted from the Desktop CD.  That's not a big deal at the moment, I should have a solution discovered within a week.

---

### Post by aysiu on 2006-06-05
As of this post, it appears that about 70% of upgraders had either some small problems or no problems.

---

### Post by xmastree on 2006-06-05
Pick any two options and 2/3 of us will be in that group though...

So 2/3 had problems...

---

### Post by seshomaru samma on 2006-06-05
I tried to install several times
I downloaded the alternate torrent which suppose to allow upgrading , i checked the CD for errors and started upgrading but half way through it said that it can't mount the CD - very strange. I tried several times. I then tried on a different machine but if kept freezing after 32% 
I concluded that the CD is currupt somehow though I used it to boot into Ubuntu live version and downloaded the desktop torrent . Checked the new CD for errors and started reinstalling , this time after about 80% the screen went black. It happened several times.
I then downloaded the desktop version directly from the ubuntu website
The installation went smoothly and I think it was worth it.
Dapper is excellent, I am especially satisfied with its CJK language support which I never really managed to work out in Breezy but worked out of the box in Dapper.
It took about 12 hours

---

### Post by Stryker777 on 2006-06-05
The only issue I had with the upgrade from a remote ssh session was the following:
I have dual eth interfaces.  After upgrade, eth0 became eth4.  I changed /etc/network/interfaces from eth0 to eth4 and rebooted.  All is well now.  

Pretty good to only have that small issue on a remote upgrade.
Thanks
Stryker777

---

### Post by Gijith on 2006-06-05
I upgraded to the beta in terminal. Then, after having major problems getting xgl/compiz to install, did a clean reinstall on 6/1. With the graphical installer, the whole reinstall took 10 minutes. Sweet.

---

### Post by bonzodog on 2006-06-05
I did a clean reinstall at flight 4 to server level, then added xubuntu-desktop. I have however downloaded the final ISO install only disc, and will do a completely clean install of that to rid my system of the older stuff, and excess progs that I am not using. I will also fine tune the boot on it, and only add what I think I need.

---

### Post by spira_mirabilis on 2006-06-06
I had Dapper Milestone 7, with minor issues, and then fresh-installed to the official 6.06 Kubuntu.

The major problem is that xine related playback (mplayer, kaffeine, xine-ui) is all messed up now (maybe a codec package issue?), extremely contrasted and unwatchable and I cannot fix it, the regular contrast/brightness options don't help...With the testing versions I never had this problem.](*,) 

Other than that, everything that was working before works great! (Still waiting for Intel 950 graphics support in xorg so I can get full resolution on my Inspiron 9400 laptop..915resolution does NOT work at all... O_o).

Overall a good transition, and great distro. :cool:

---

### Post by terminatorkobold on 2006-06-07
I upgraded using the graphical tool and encountered some small problems:

1) It broke my x-server and I had to reinstall the nvidia drivers to get it to work

2) My printer stopped working (lexmark Z32)

3) The gui for firestarter refused to load. I solved it by using xgl. :D 

4) It set my webcam instead of my soundcard as the default sound device. I was mystified for some times about my broken sound until I found the source of the problem

Else everyting is fine and I even installed compiz using the guide in the wiki. I like it a lot!!!

---

### Post by Stormy Eyes on 2006-06-07
I upgraded from Breezy to Dapper months ago using "apt-get dselect-upgrade", and continued to upgrade every few days using the same command. I never had any problems.

---

### Post by odrop on 2006-06-07
I did a fresh install on another harddrive in my comp from the cd live/installer. Major problems ensued.

The harddrive was a new'ish 250 gig that I prepared earlier for the new Dapper.  I ghosted the windows partition on there, setup a media partition and left some space over for linux.  All was going good in the install, until the installer decided to crash writing something to the partition info I assume.  I ended up with my partition information corrupted/wiped out.  Luckily this was only copies of all my other data on the other two drives.  I tried a partition recovery software that took *7 HOURS* to do nothing.  I was going out of my mind waiting for that thing to finish.

So anyway, I reformatted the drive, re-ghosted windows (another 3 hours, ugh).  Setup the other partitions and this time setup the partitions how I like in a different program off a different boot-cd.  The installer worked great that time.  Now I'm just fighting with the complete lack of compile tools on the CD to get my winmodem drivers compiling.  I think I'm just gonna give up on that and do a dist-upgrade on my breezy.

---

### Post by brt on 2006-06-07
+ one "update-manager -d"
+ one clean install from CD
+ one apt-get dist-upgrade after changing breezy->dapper in sources.list (also using apt-cacher)

everything went absolutely smooth no problems at all :D

bis shoutouts to all the magic ubunutu hands ! good work !

---

### Post by oyvindaa on 2006-06-07
I installed Dapper from cd and I haven't encountered any problems at all.

I always like to do it the "cd-way" :D

---

### Post by timczer on 2006-06-07
I was concerned with this upgrade as I had done a lot of customization to my Breezy install.  I was also running a server for work related files for my company and was concerned that if I dist-upgraded and it fried my system I would be in trouble.  So, I did a fresh install on an newly purchased slave hard drive (needed more memory anyway).  The installation was amazingly smooth with everything working right from the start.  As I have started to work to get the new installation up to speed with my breezy install, it was worked amazingly well.

---

### Post by sup on 2006-06-07
I dist-upgraded via graphical tool just a while ago and I encountered big problems. Well, it depends, it took me about twenty minutes to resolve them. My xserver would not start, so I had to alternate xorg.conf manually and then reinstall proprietary ati-drivers. It was not that hard for me, but for someone not comfortable with command line, it could be a horror.

---

### Post by SlugO on 2006-06-09
I tried to upgrade with the graphical tool first (around flight 7) but that didn't work so I did it from the command line. Borked my X cos it didn't install a new nvidia-glx after removing the old one.

It's been mostly working well but I do get some weird stuff sometimes. For example my mic has stopped working and I can't unmute/change the volume on it anymore. Can't burn data cd's anymore (audio cd's and data dvd's don't give problems though) and sometimes when i put a data dvd in the drive it only shows a few of the files there and they all have names like ?????? which is **really** weird. Also my system seems to always freeze after I unmount my Nokia 6131 that has been in data transfer mode and handled as a USB drive. Also all my variations of the Human icon theme show blue Tango folders and there's no way of changing that, annoying...

I guess I'll do a clean install later.

---

### Post by senn on 2006-06-09
hi, this is my very first posting so if im in the wrong thread please dont bite my head off. i received my triple cd pack 2-3 weeks ago, but only installed last sunday. i was running xp pro and thought i would give ubuntu a go. first thing i did thou was slot in my d ban nuke floppy and ran that twice. this gave me a"like new" hd with which to install ubu onto. 5.10 installed without any problems, almost straight away i.e. first time on i received a update message that 6.06 was ready and would i like to install. i did and still no problems,:D  this os rocks. did any one else run d ban nuke before they loaded ubuntu.

---

### Post by chickengirl on 2006-06-09
I dist-upgraded using the update manager and had one small but significant problem: I have two hard drives, one for Windows (which is SATA) and one for Linux (which is IDE). For some reason after the upgrade was finished and the computer rebooted, the Linux drive's location had changed from hdc to hda and the kernel couldn't find the root filesystem anymore. I had to fix GRUB in order to get the system running again. (Windows was unaffected.)

---

### Post by RRS on 2006-06-09
Originally had only added a couple Dapper repositories in order to install Fuse and ended up breaking X in Breezy.

After a few unsuccessful attempts @ repair I changed the rest of my repositories and dist-upgrad'd. Still had a broken x but easily fixed it.

This was back in flight 5(?) and problems since have been minor. A few still exist but haven't spent much time on them, they're only occasional anoyances.

I've never had a problem with internet, sound, or some of the other things that appear to be common. Lucky?

BTW, running on a low end e-machines, dual boot with a broken windows, (was broke before installing Breezy). I just copy files into my fat partition as needed so fixing boot problem with windows is low priority.

---

### Post by Juzz on 2006-06-10
I dist-upgraded from the terminal and I have had BIG problems getting it up again :-(

First of all it stopped with a bang with an error about xorg-driver-fglx - but I haven't had that installed I used the drivers from NVidia... The dist-upgrade had already upgraded quite a few packages, so somehow I had to get the process finished. So I moved the xorg-driver files from the apt-cache.
Then the dist-upgrade could continue, and then the process halted with a bang while trying to reconfigure pcmcia services, but I could abort the reconfiguration and the process continued without help from me.
When it was done I tried rebooting, and the kernel halted with an error about PCIC - even the rescue kernel stopped at the same error and so did the other two backup kernels I had installed (so what's the use of backup-kernels then?) :-(

Then I grabbed the SuSE liveCD from the Linux Magazine booted it up and got a chroot up and running in a terminal and I could continue the upgrade after a repair of the cache.
But now X server halts completely stating that it can't start up GLX and NVidia modules :-(
I have now tried both installing the community drivers AND the closed source from NVidia, but no luck.

What can I do now?

---

### Post by Juzz on 2006-06-10
I got it up and running now - however unfortunately without OpenGL...

I followed the advise in another thread about running the install of ubuntu minimal, base and desktop (and all the other commands) and after a couple more apt-get update and apt-get dist-upgrade things seemed to have run better, so I rebooted from the SuSE liveCD to see if it had helped, and I could do some stuff to get X up and running again.

---

### Post by GrumpyBob on 2006-06-11
Yesterday I upgraded my Thinkpad R52 from Breezy to Dapper using dist-upgrade via Update Manager.  This went perfectly and all seems to be fine.  Before I upgraded I changed my sources.list to a stock Dapper sources.list

Very pleased with this!

Robert

---

### Post by manicka on 2006-06-11
I voted other

I did a clean install from the Dapper Desktop CD which gave me the 'hanging at mounting root file system' error. 

I then completed a text-based install from the alternate image without any issues.

The problems with the Desktop CD are a major problem for this release and not really good enough for a LTS version

---

### Post by nuvo on 2006-06-11
I moved to Dapper while it was still in Beta using the terminal, though I usually use the GUI tools for convenience.

The only issue I have had is that Dapper didn't seem to like using the drive labels I had under Breezy.
I set up mounting points for two NTFS partitions under Breezy in etc/fstab so they'd show as XP and Stuff, and this worked like a charm with Breezy, but Dapper seems to prefer to use HP_PAVILION (I'm not using a pav, though the drive is from one) and storage.
It didn't bother me that USB drives show up as usbdisk-<number> as they are only used when needed, so they aren't permanently there, but I'd rather have HDD partitions named as I specified.

---

### Post by Stew2 on 2006-06-11
I voted other as well.

I had done a clean install of the Dapper flight 6 beta a while back and then I simply dist-upgraded that. No problems whatsoever. I love Dapper! :)

---

### Post by charles woodward on 2006-06-11
I've put down other - why - because I tried them all - I tried to istall from a Live CD - but it went completely haywire (this was still a beta around early/mid March).

Then I did a live Cd - had numerous problems with wireless network - re-installed breezy and did upgrade - still have problems with wireless network - and a whole host of errors for all sorts of things kept popping up in logs - I think the upgrade may have been relying on software/dependencies that I might have removed or modified.

Anyway I gave up for a couple of weeks, then around beginning of May I re-installed from Live CD (by this time I had reconfigured my system so that all sytem files, etc were on one small disk, while my stuff was on the larger disk) - worked like a charm (apart from the fact that I had something like 500 updates the first day).

Still had problems with wireless network - but have now sorted that out - all I've got to do now is get my scanner and webcam to work (but they didn't on Breezy either - only reason I've still got a windows box)

---

### Post by skirkpatrick on 2006-06-11
Well, I could only vote once but I've done two upgrades.

I upgraded my laptop from Breezy to Dapper using the graphical tool and had absolutely no problems.

I upgraded my desktop from Breezy to Dapper using the graphical tool and everything seemed to be fine but the upgrade froze at trying to update the Ubuntu docs.  I waited an hour before I killed it and tried to reboot but of course everything was only partly upgraded so the system wouldn't do anything.  Luckily, I had backed up everything and I did a clean install from the Live CD.

---

### Post by isobel on 2006-06-11
last weekend i dist-upgraded using update manager, but i forgot to disable the screensaver (?) and the process froze. after (manual) reboot, the system did not start up!

after hours of web searches beginning from ubuntuforums and link after link i was directed to this useful page:

[https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/32123](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/32123)

the post by Anders Karlsson helped me to access my system, update the repositories (adding the ALTERNATE ubuntu - ISO image downloaded from the internet), and recover my upgrade, usind apt-get method, this time.
since then everything works fine, and i've made my decision not to use graphical tools to update/upgrade anymore!

thank you everybody for the help you give us newbies

---

### Post by weasel fierce on 2006-06-11
I was going to dist-upgrade (which I did from hoary to breezy, and it worked fine), but I wanted to clean up the box a bit anyways, so I figured I'd burn a new CD and install from scratch.

Working like a charm, too :)

---

### Post by jpkotta on 2006-06-11
I dist-upgraded, using the command-line method in the wiki page.  I read about the pcmcia bug, and updated my sources.list as per the wiki, but it didn't work.  The manual workaround (moving the start up scripts) worked just fine.  

I had installed the latest NVidia driver using NVidia's installation script prior to upgrading, and this caused problems.  After installing Dapper, I re-installed using NVidia installer, but it wouldn't work.  I installed the Ubuntu driver packager, and it didn't work, because there was a conflict between what the kernel was loading and what the X server was loading.  After uninstalling and re-installing the Ubuntu package, it worked, as it must have removed anything from NVidia installer.

I said "dist-upgraded using CLI, minor problems".  I think that if I had less experience, it would have been major problems.  I thought Hoary->Breezy was much smoother.  I still haven't updated my [laptop]("http://ubuntuforums.org/showthread.php?t=162997"). I want to back it up first, and my external HD is far away from me at the moment (I had enough confidence in Linux on desktops to not bother backing that up).

---

### Post by Gtaylor on 2006-06-11
I usually err on the side of caution and just do a clean install. Rarely ever see problems.

---

### Post by rts on 2006-06-11
On one machine, a command-line dist-upgrade which was running flight 5 went very well.

On a laptop, which was running Breezy, a dist-upgrade went fairly poorly:

- I could not boot, and had to drop to recovery mode to run dpkg-configure dmraid in order to get my raid1 working again
- Wireless adapter stopped working (and still doesn't work).
- Suspend is closer to working, but still no cigar.

---

### Post by Monamogolo on 2006-06-11
I tried to up-grade from Hoary to Breezy, and was only partially successful. I have therefore not even tried to go on to Dapper, in case I lose even more functionality. In the first upgrade i felt the instructions were not adequately clear.

---

### Post by jchau on 2006-06-11
I somewhat upgraded from Breezy to Dapper and I'm not sure if I have big or small problems yet, so I voted, that I upgraded from Breezy to Dapper and I had small problems.

One problem was that the install never finished. Sometime through the upgrade, [Samba install has an error which causes the install to abort later]("http://ubuntuforums.org/showthread.php?t=190613").  Although I fixed the problem with some help post-partial-install, I suspect that my system is not fully upgraded yet.

Another minor problem is a driver problem.  I need to compile a new driver to fix it (does anyone remember which package I need to compile drivers (kernel modules)? Is it linux-headers or kernel-headers? I don't want to download the entire kernel source.  Also, do I need to apply the ubuntu patch to the header sources?)

Yet another minor problem is that X seems to be taking a lot of the CPU.  On average, it takes about 50% of the CPU. I remember that X (Gnome) did not use the processor so intensely on Breezy.  I'm running powenowd on my laptop and the processor runs at full speed even when I'm running nothing but Gnome.  Does anyone know what's causing this? Is it a faulty config?

The options to update the configs were also a pain.  The update-manager update GUI will show me the old config and the new config and asked me which one I wanted to keep without giving me an option to take lines from each (since I modified the configs of Breezy, I wanted to keep some of those modifications while taking some but not all of the new config files).  Since the forum warned that running other programs during the update might cause programs, kept a few of my old configs (one of which caused errors to pop up after I type in my user name in the console (text terminal) while logging in.  (/etc/login.defs was causing the this problem I later found /etc/login.defs.dpkg-dist and replaced /etc/login.defs with it to fix the problem)  I wonder if any of the old configs are silently causing problems

The command "startx" is also giving a few erros, although X appears to start fine.  
Some of the errors are:
> dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)

But these errors may have existed before the upgrade. I've noticed X errors in Breezy.

---

### Post by djsroknrol on 2006-06-11
I dist-upgraded from the terminal...very few problems, nothing major.....I want to do a clean install here very soon

BTW, it sounds like the majority of problems on CD's come from bad .iso burns...

---

### Post by manicka on 2006-06-11
[QUOTE=djsroknrol]
BTW, it sounds like the majority of problems on CD's come from bad .iso burns...[/QUOTE]

disagree... while some people have this problem, most of the issues with Dapper come from using the Desktop CD and the Graphical install method. My advice is to use the alternate image and do a text-based install.

---

### Post by newbie2 on 2006-06-11
here they had also some problems 
[http://lxer.com/module/forums/t/22866/](http://lxer.com/module/forums/t/22866/)
:rolleyes:

---

### Post by blindpete on 2006-06-26
Well I used the graphical update and it downloaded and began the install w/o any trouble but then about 90% in I started getting popup after popup saying varios things failed... but w/o any opportunity to do anything to do anything about it except cancel or ok.  To be honest the messages were so technical that after the first few I stopped reading them (admittedly my bad) but they were meaningless to me anyhow.

Now Dapper is installed and runs fine except I have no sound (which I had before) and presumable one of those or all of those messages was related to that.

---

### Post by Kvark on 2006-06-26
This should be a multichoice poll. It took me 3 tries to install Dapper:
1. The Dapper Live CD. It displayed a menu but when I choose to start dapper it failed to boot so I couldn't do anything with it. I couldn't even check it's integrity because when I choose integrity check in the menu that failed to boot too.
2. The alternative Dapper CD. It booted and everything seemed fine until it froze halfway through the install.
3. Did a server install with a breezy CD, dist upgraded and then installed ubuntu-desktop. It worked perfectly, not a single problem, not even a small one.

I blame it on my CD burner. It is the cheapest junk I could find in a hurry when my old burner started smoking and I was short on cash atm.

---

### Post by MethodOne on 2006-06-26
I did a fresh install of Dapper from a beta and upgraded to the final version.  I didn't have any problems, except with a few applications that were broken and later fixed.

---

### Post by george_apan on 2006-06-26
Dapper is completely unusable for me. I'm having major problems and i've tried every installation method there is.

1. I've dist-upgraded my original breezy installation
2. Clean install with the ubuntu live CD
3. Clean install with the xubuntu live CD
4. Clean install with the ubuntu alternative CD
5. I've reinstalled breezy and used the update manager to upgrade to Dapper.

All of the above lead to these problems:

1. I can't mount my USB hard drive and USB DVD-recorder in Dapper. The system completely hangs in the process. This is really **BIG**. Looking at the forums this problem mostly remains unsolved for everyone having it.
2. I have to disable framebuffer in order to view the boot process. Graphical boot does not work in any way. This is not important but it's a bug nonetheless.

Dapper works fine for a lot of people but for me it just is totally unusable. I've now reverted back to breezy which works perfectly on my PC but I'll be looking at other distros when I'll have the time. Ubuntu lost me as a user with Dapper and I've stopped recommending ubuntu, whereas I advertised breezy everywhere. Pity...:(

---

### Post by Iandefor on 2006-06-26
[quote=george_apan]Dapper works fine for a lot of people but for me it just is totally unusable. I've now reverted back to breezy which works perfectly on my PC but I'll be looking at other distros when I'll have the time. Ubuntu lost me as a user with Dapper and I've stopped recommending ubuntu, whereas I advertised breezy everywhere. Pity...:([/quote] So, based on your *single* experience with Dapper, a *single* revision of Ubuntu, you're not going to recommend Edgy, Edgy+1, Edgy+2, etc to anyone? I agree that you shouldn't bother trying to use Dapper if it's so badly broken on your system, but it's a little silly to shun Ubuntu based on a single release.

---

### Post by george_apan on 2006-06-26
[QUOTE=Iandefor]So, based on your *single* experience with Dapper, a *single* revision of Ubuntu, you're not going to recommend Edgy, Edgy+1, Edgy+2, etc to anyone? I agree that you shouldn't bother trying to use Dapper if it's so badly broken on your system, but it's a little silly to shun Ubuntu based on a single release.[/QUOTE]
No, I'm not recommending Dapper to anyone. Edgy might be a different beast but by then I will probably have moved to another distro and probably recommending that instead. If I try Edgy when it comes out and if I see that I have no problems with it I'll start recommending it alright. But I might not try Edgy at all if I like my next distro...

---

### Post by Iandefor on 2006-06-26
[quote=george_apan]No, I'm not recommending Dapper to anyone. Edgy might be a different beast but by then I will probably have moved to another distro and probably recommending that instead. If I try Edgy when it comes out and if I see that I have no problems with it I'll start recommending it alright. But I might not try Edgy at all if I like my next distro...[/quote]Oh, okay. Just sounded like you were going to back off from using Ubuntu at all, not just Dapper.

Might I recommend Fedora Core 5 if you want a good distro? I, personally, had issues with package management, but that's just because I'm used to dpkg.

---

### Post by george_apan on 2006-06-26
[QUOTE=Iandefor]Oh, okay. Just sounded like you were going to back off from using Ubuntu at all, not just Dapper.

Might I recommend Fedora Core 5 if you want a good distro? I, personally, had issues with package management, but that's just because I'm used to dpkg.[/QUOTE]
Yeah, thanks for the recommendation. I was considering FC5 as well as Zenwalk which from a preliminary test seems really fast (it boots at 1/3 of the time it takes breezy to boot!). But Fedora has so many more packages... Ahh, decisions... decisions... :-k I'll probably try both and see which one makes me feel better.

---

### Post by chestnut1969 on 2006-06-26
Daily dist-upgrade for my laptop from 5.10 during testing period

CD install final 6.06 LTS on desktop 

Both ended up in the same place; no problems with either :)

---

### Post by basketcase on 2006-06-27
A little update...
On my notebook, I started with a beta, and just upgraded til it was LTS
I kept reading how people were having problems with the install, so I grabbed an ISO, booted into a Live CD and used the defaults for the installer.  Successful w/o issue
And to further the cause, my local file server/mythtv (test) box had 5.10, and I just dist-upgrade with it.  Successful w/o issue (though uncertain how Mythtv likes it).
 
Over all, no issues.  
 
Notebook is a Dell Inspiron 6000.  File Server/Mythtv box is a PIII 766 with 256MB and small 10gb gdd (Old Gateway Computer)

---

### Post by dahli.llama on 2006-06-29
I have actually tried both an upgrade using the graphical tool and a completely fresh install using the downloaded CD image.

In both cases, shortly after booting into Ubuntu my computer locks up and if I am in the command line, I get a bunch of errors that end in a kernel panic.  Everything was working perfectly fine in 5.10

---

### Post by Iandefor on 2006-06-30
[quote=george_apan]Yeah, thanks for the recommendation. I was considering FC5 as well as Zenwalk which from a preliminary test seems really fast (it boots at 1/3 of the time it takes breezy to boot!). But Fedora has so many more packages... Ahh, decisions... decisions... :-k I'll probably try both and see which one makes me feel better.[/quote] You could also try something like plain old Debian. I know I had major problems with Zenwalk.

---

### Post by user1397 on 2006-06-30
I had _**absolutely no problems**_ with installing dapper.  I popped in the i386 desktop cd, went straight to the graphical install, partitioned my hard drive, and installed the system.  I don't think it took me more than 20 minutes.  No bugs, ever.  Plus, I installed the release candidate version, and then just downloaded all the updates.  

GREAT JOB DAPPER DEVS!

---

### Post by warjowuch on 2006-06-30
I did encounter some small problems when dist-upgrading to dapper.
Mplayer did not work, gnomebaker did ont encode mp3's anymore. I fixed them, but should not be nescecary (?). (Fixed them by installing other packages, reïnstalling, trying different options).

---

### Post by wislon on 2006-06-30
I dist-upgraded using the terminal and a 6.06 DVD image (I'm on dialup, so over the net wasn't an option). Upgrade went off without a hitch. It killed the nvidia driver, so I had to drop back to 'nv' and download and install the new one (for the newer kernel), tho I must say this wasn't unexpected. 

The only problem I've had is that automounting of USB removable drives no longer works (flash and HDD). I have to plug the device in and then do a 'sudo mount -a' to get the drive to pop up. Not a **major** issue, but mildly irritating. Still haven't been able to find a fix after a month. If someone HAS fixed this, please drop me a line? I've checked the other forums and topics and haven't come across any that work.

---

### Post by Mirko on 2006-07-02
I dist-upgraded three machines from Breezy to Dapper using apt-get and the alternate CD (and the Internet).

Machine 1: IBM ThinkPad T42 laptop.  No big problems.  XGL won't work with the damn ATI board, and now my Gnome settings are buggered up a bit: it takes several minutes for Gnome to load after logging in (panel, etc.), and windows aren't positioned on the screen correctly.  The new Network Manager works great with WPA-- no more fiddling with wpa_supplicant!  I like how the hardware volume buttons now adjust the master volume, but dislike how the brightness and other OSDs have disappeared (too lazy to debug this).

Machine 2: Athlon 64 desktop (32-bit Ubuntu).  No problems.  XGL works fine (nVidia hardware).

Machine 3: small form factor, headless: I dist-upgraded over a VNC session (which was very nice).  After rebooting, vncserver, mysql-server, k3b, and kaudiocreator were no longer installed.  The upgrade also destroyed rc.local and a file I put in /etc/init.d!  Having some compatibility problems with MySQL 5, but those aren't Ubuntu's fault.

All in all, a fairly smooth transition.  When I dist-upgraded my laptop from Hoary to Breezy, everything got broken and I had to install it fresh, which cost me nearly a full day and almost sent me back to Gentoo or (perish the thought) Fedora.

---

### Post by B0rsuk on 2006-07-03
I upgraded via terminal. There were some very annoying problems, but I managed to fix it.

I made sure I have kubuntu-desktop installed, then started upgrading.

First, there were some seemingly  broken dependencies with one of 'twisted' packages. I use them to run Galaxy Mage. I had to uninstall twisted, and reinstall it later, after upgrade. It worked allright at that point.

Most of packages were downloaded, but I had to install KDE manually. I installed ubuntu-base and kde-desktop.
KDE launched, but it was broken. I couldn't run any app, and there were errors about no mime types installed etc. Basically KDE was totally broken. However, I was able to  run wolfenstein:enemy territory from a konsole open since breezy (session restored), and it worked fine.
This led me to believe it was just KDE improperly installed. So I installed some random packages with kde name in them, especially kde-core. Still nothing.
Then I got angry and installed whole kde metapackage. Now it works great, except I got a lot of unwanted software along with KDE metapackage.

---

### Post by guine on 2006-07-03
I originally upgraded through the terminal.  That worked fine for a little while until things started falling apart with firefox crashing all the time and eventually being unalbe to boot.  So I gave the fresh install from cd a try and I was never able to get internet working, I got kicked off the internet once I did one thing online despite having no internet problems with breezy, my earlier upgrade to dapper, or running off the dapper cd, so Im reinstalling breezy right now and am hoping that I can get the next release to work better.

---

### Post by dashnak on 2006-07-07
I reinstalled, and actually everything works great now, much better than Breezey. The problem was that ubuntu didn't use the biggest free space like I told it to, instead, it decided that it was a good idea to eat 30 GB of music by formatting the whole disk. 
Anyway... Sigh....

---

### Post by george_apan on 2006-07-08
> **dashnak said:**
> I reinstalled, and actually everything works great now, much better than Breezey. The problem was that ubuntu didn't use the biggest free space like I told it to, instead, it decided that it was a good idea to eat 30 GB of music by formatting the whole disk. 
Anyway... Sigh....
And you consider this not a problem? ](*,)

---

### Post by dashnak on 2006-07-08
Actually I answered "[I]I installed Dapper from cd and I have encountered big problems." Of course I consider this a VERY BIG problem, and me as well as my sis were royally pissed off at this....
But hey, what can I do now? I had no backup save for the complete discography of David Bowie and some tribute albums...
So hey, what the hell.... I can always get everyhting again.... I was thinking that it was time to renew my library actually....
[/I]

---

### Post by george_apan on 2006-07-08
> **dashnak said:**
> Actually I answered "[I]I installed Dapper from cd and I have encountered big problems." Of course I consider this a VERY BIG problem, and me as well as my sis were royally pissed off at this....
But hey, what can I do now? I had no backup save for the complete discography of David Bowie and some tribute albums...
So hey, what the hell.... I can always get everyhting again.... I was thinking that it was time to renew my library actually....
[/I]
I would be devastated if that happened to me. My data are more important than any OS and most of them I can't find anywhere else, so I always keep a synced backup on a second PC.

So... with 476 votes about 26% of the installations resulted to big problems and another 38% resulted to small problems. I wish there were more answers but this certainly doesn't look good for dapper. :(

---

### Post by druvoid on 2006-07-10
I updgraded to Dapper from Breezy using a terminal and had big problems.  Had to re-install the nvidia drivers; Open Office will not work at all; got messages during the installation that a number of things failed and have not yet tracked down what all of it means.

Forgot to add: I also cannot get Firestarter to work.

---

### Post by eriqk on 2006-07-10
I dist-upgraded from a server install, which seems to have gone OK. I'm now building a desktop but I get intermittent freezes when I use FTP. Very annoying. Not sure what causes this, I've experienced this once before on Breezy so it might be something unrelated. Dapper seems to be a bit more susceptible, maybe. We'll see, I guess.
Over the whle, Dapper is much more responsive on my Tecra 8000 (PII-300/256MB). Firefox seems to be a bit of poo, though- scrolling is incredibly slow. On Breezy, I used Mozilla's own 1.5.0.x which was a lot faster. 
I'm not sure if any of this was caused by the upgrade.

Groet, Erik

---

### Post by ginapi on 2006-07-14
I dist-upgraded to Dapper my HP nx6110 Laptop with the graphical tool without any problem. Apt is absolutely great!! :mrgreen:

---

### Post by Compucore on 2006-07-14
When Dapper came out initially I went from Breezy to dapper that way via package manager at the time. But once my cd's came in I did a fresh install then since I wanted to make sure I got rid of any leftovers from the upgrade. ANd its working fine for me over here on my Dell GX150.

Compucore

---

### Post by gratefultux on 2006-07-14
My experimental partition i dist-upgraded to dapper during the end of the beta period and didn't experience any problems.
My main partition I dist-upgraded after the release and sound stopped working.  I wouldn't call it a major issue, but it took a while to fix.

---

### Post by pepolez on 2006-07-15
Tried upgrading to dapper from breezy with a normal dist upgrade. Totally raped my networking config (randomly switched around interface numbers...wtf?) and various preferences.

Worked after formatting / and reinstalling from dapper install disk.

---

### Post by sagarhshah on 2006-07-18
I upgraded to Dapper from Breezy using the alternate cd.
Didnt encounter any major problems although a few of my programs broke. All I had to do was recompile them on the upgraded system.

---

### Post by zxee on 2006-07-26
> **george_apan said:**
> Yeah, thanks for the recommendation. I was considering FC5 as well as Zenwalk which from a preliminary test seems really fast (it boots at 1/3 of the time it takes breezy to boot!). But Fedora has so many more packages... Ahh, decisions... decisions... :-k I'll probably try both and see which one makes me feel better.

From reading through your 1st post-this thread I can relate to having problems with dapper. Networking & internet were unbelievably problem filled.
I like ubuntu though having used it since hoary, and edgy, for me, has none of the irritations that dapper did, and this is just the 1st iso release. So perhaps edgy will make up for dapper's shortcomings. 
One of the things about fedora I never warmed up to was the package manager, but hey maybe you'll like it.

---

### Post by bensexson on 2006-07-26
I tried to upgrade with the CD.  My / partition was not big enough and I managed to bork it while trying to make more room.  I hd backed up so it was all good.  Also I had first installed with Hoary and had to do some ugly kludges to get nvidia and my alps synaptics touchpad working.  The fresh install I did on Dapper went flawlessly except NM did not work correctly.  I just fell back to my custom script and a lot of work.  Now it all works.  I am concerned about the graphical installer and it handling of partitions.  It seemed to crash alot.  I am not the only one to mention this so I assume the devs are looking into it.

---

### Post by yellowtuesday on 2006-07-27
I installed it right away because when i picked up the breezy badger disk from a internet cafe drapper was already out. after my install using the graphical tool i haven't really encountoured any problems because I hadn't previously installed anything, the only thing I noted is that I have no log out button at the top right hand corner of my screen and the help is still in the panel, anybody know how I can get the log out button?

---

### Post by Derek Djons on 2006-07-27
I couldn't use the Live-CD to install Dapper Drake. While navigating through the installatin screen the install always got frozen. So I downloaded the Text-CD I was always used and installed Drapper Drake. But since Dapper Drake I have this issue turning my portable off. At the end it keeps saying 'unregister_netdevice' and keeps repeating that message. So I have to shutdown manually. But I didn't searched for a solution to fix this problem. For me, it's just a minor bug / problem.

---

### Post by geco on 2006-07-27
I tried to dist-upgrade but I had so big problems that I had to install from the live-CD... anyway I would rather have preferred a non-graphical installation.

---

### Post by Dural on 2006-07-27
I tried to reinstall Kubuntu Dapper Drake and it froze at 64% when it copied the files. In fact, everytime I have used the graphical installer, whether I burnt the CD myself or if I used the ship it CD, it has frozen before it could finish. As a result, now I can not even boot into Windows or Kubuntu because GRUB is screwed up.

---

### Post by beercz on 2006-07-28
After dual booting with Windows XP (for work purposes) since Warty days, I recently finally was able to remove XP completely (I run XP on another pc in the office).  Therefore I decided to reformat my hard disk and reinstall dapper only.  Had only one problem, it took me ages to recover my data from my backup - I seem to have tons of the stuff!!!!

Until my recent reformat I had just continuously upgraded from Warty, Hoary, Breezy and then Dapper.

It is such a nice feeling being Windows free - like swimming naked :-)

---

### Post by Christopher on 2006-07-28
> **beercz said:**
> It is such a nice feeling being Windows free - like swimming naked :-)

I agree...lol

---

### Post by Christopher on 2006-07-28
> **Derek Djons said:**
> I couldn't use the Live-CD to install Dapper Drake. While navigating through the installatin screen the install always got frozen. So I downloaded the Text-CD I was always used and installed Drapper Drake. But since Dapper Drake I have this issue turning my portable off. At the end it keeps saying 'unregister_netdevice' and keeps repeating that message. So I have to shutdown manually. But I didn't searched for a solution to fix this problem. For me, it's just a minor bug / problem.

Mine also is freezing at like 69%, weird. Whats the difference between the Text-CD and using the live-cd? :confused:

I installed it on my other PC with no issues at all.

---

