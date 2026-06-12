---
title: "The non-pae mini.iso testing thread"
date: 2012-02-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-02-12
**[COLOR="Red"]NEW[/COLOR]**, I typed a [basic summary regarding the use of the mini.iso]("http://ubuntuforums.org/showpost.php?p=11847760&postcount=103") here to compliment another upcoming thread.

**********************************

*This is quite a preliminary look at the non-pae mini.iso so cut me a lot of slack. I need as much help as possible. Please point out any errors and I'll try my best to sort things out. Since each full installation is quite time consuming I invite anyone interested to join in.*

So, what is this and why is it needed?

Please read:

[http://ubuntuforums.org/showpost.php?p=11661116&postcount=1](http://ubuntuforums.org/showpost.php?p=11661116&postcount=1)

Be sure and check the links and also look at this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447)

I'm referring to the mini.iso image listed here:

[http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

When I initially tried the 20120208 non-pae mini.iso I encountered a problem with networking but that ended up being a BIOS problem that I've since resolved.

Next the 20120208 non-pae mini.iso failed to find kernel modules, but that was resolved with the 20120209 image.

So I moved ahead to begin testing the whole thing. If you're familiar with the Debian installer this will all seem quite straight forward to you. Additionally I found a good guide with screenshots here:

**[COLOR="Red"]This is now a bad link[/COLOR]**:

[http://xbmcmediacenter.com/how-to-install-ubuntu-mini-iso/](http://xbmcmediacenter.com/how-to-install-ubuntu-mini-iso/)

If you're not familiar with the Debian installer I'll try to answer your questions, but the basics are:

* You really need a fast wired ethernet connection. My ethernet speed is 5000kbps+ and the average total installation time is 1 hour and 45 minutes.

* After selecting the installation language you'll be offered 4 choices:

Install
Command-line install
Advanced options
Help

Under advanced options you're offered:

Back
Expert install
Command-line expert install
Rescue mode

For our purposes I'm focusing only on Install ATM so just select Install!

* You'll be asked to select your language & country/territory

* You'll be asked if you want the installer to detect your keyboard layout or proceed with the default (I always just select No when asked and the US keyboard defaults seem fine for me).

* Specify the hostname for your system - this may confuse new users, but I typically use my first name accompanied by some computer ID or location, eg; john-AMD-desktop, or john-INTEL-laptop (this probably needs more specific instruction). This will be how your computer is recognized on your network.

* Choose the proper archive mirror

* HTTP proxy - I'm totally clueless here as I've never dealt with such

* Naturally you'll be asked for your full name, a user name, and a password just as with any installer.

* Encrypt home directory? I've never done so, but this may be helpful to others:

[http://askubuntu.com/questions/37/when-installing-im-given-the-option-of-encrypting-my-home-folder-what-does-t](http://askubuntu.com/questions/37/when-installing-im-given-the-option-of-encrypting-my-home-folder-what-does-t)

* Time zone - should be self explanatory

* Partitioning - this gets rather complex so I'll not get into detail here, any help locating a simple but complete guide would be appreciated. One nice thing here is that the "Use largest continuous free space" option still exists.

* After quite some time you'll be asked about how to handle updates - Select 'No Automatic Updates' (trust me)

* Next you will be offered a lot of installation options, including a lot of different server options. My sole focus is on desktop installations, I've never set up a server anyway, so I'm clueless in regards to that. 

It's a long list, you must use the keyboard arrow keys to scroll down the entire list. Those of interest to me ATM:

Lubuntu minimal install 
Ubuntu LXDE desktop (this is actually Lubuntu desktop)
Ubuntu desktop

But both Xubuntu desktop and Kubuntu desktop are available if someone else wishes to test them. There is a complete list of options here:

[http://ubuntuforums.org/showpost.php?p=11690855&postcount=21](http://ubuntuforums.org/showpost.php?p=11690855&postcount=21)

* When the installation is nearly done you'll be asked if you want to install grub to the mbr, typically you'll want to select yes.

I'm going to try and keep bug report info updated in this post:

[http://ubuntuforums.org/showpost.php?p=11684309&postcount=2](http://ubuntuforums.org/showpost.php?p=11684309&postcount=2)

Great fun ahead :D

---

### Post by kansasnoob on 2012-02-12
I'm going to try and keep bug report info updated in this post as much as humanly possible.

Bugs filed so far:

[Precise non-pae mini.iso offers Ubuntu LXDE desktop rather than Lubuntu desktop]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/931237")

[Precise non-pae mini.iso installation results in incomplete language support warning]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/931191")

And potential bugs not yet filed:

Precise non-pae mini.iso disc is difficult to remove when installation completes

Ain't life a joy :D

---

### Post by jerrylamos on 2012-02-12
Hmmm.  My non-pae non-NX bit IBM Thinkpad T40 (circa 2005) 1.5 gHz Pentium M is running lubuntu precise pangolin daily build 20120207 updated to today just fine.  There have been a couple daily builds that did a check for the pae flag, finding none, quit.  

My opinion, precise pangolin should just keep on booting up and run.  

Yes if I check precise pangolin says pae=y whatever that means, and there's some workaround for the NX bit mentioned in dmesg.  See the thread on pae. 

Jerry

My opinion, don't need a total mini, just small enough to comfortably fit on a 700 MB CD.

---

### Post by kansasnoob on 2012-02-12
> **jerrylamos said:**
> Hmmm.  My non-pae non-NX bit IBM Thinkpad T40 (circa 2005) 1.5 gHz Pentium M is running lubuntu precise pangolin daily build 20120207 updated to today just fine.  There have been a couple daily builds that did a check for the pae flag, finding none, quit.  

My opinion, precise pangolin should just keep on booting up and run.  

Yes if I check precise pangolin says pae=y whatever that means, and there's some workaround for the NX bit mentioned in dmesg.  See the thread on pae. 

Jerry

My opinion, don't need a total mini, just small enough to comfortably fit on a 700 MB CD.

But many people are already encountering problems:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447)

I particularly know that Jan Claeys is reliable:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/24](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/24)

As I said in my previous thread:

> If you have effected hardware please report it!

If your hardware is not effected but you still want to do some testing please test the non-pae mini.iso:

Or install Lucid and/or Oneiric, then upgrade and be sure that non-pae remains non-pae.

I have no effected hardware but I think it's reasonable to expect that very few people will test the non-pae official installation/upgrade procedure so I chose to do so :D

---

### Post by kansasnoob on 2012-02-12
> **jerrylamos said:**
> Hmmm.  My non-pae non-NX bit IBM Thinkpad T40 (circa 2005) 1.5 gHz Pentium M is running lubuntu precise pangolin daily build 20120207 updated to today just fine.  There have been a couple daily builds that did a check for the pae flag, finding none, quit.  

My opinion, precise pangolin should just keep on booting up and run.  

Yes if I check precise pangolin says pae=y whatever that means, and there's some workaround for the NX bit mentioned in dmesg.  See the thread on pae. 

Jerry

My opinion, don't need a total mini, just small enough to comfortably fit on a 700 MB CD.

BTW I specifically asked in my OP:

> **[COLOR="Red"]If you have opinions or questions about pae vs non-pae please post them here[/COLOR]**:

[http://ubuntuforums.org/showthread.php?t=1919647](http://ubuntuforums.org/showthread.php?t=1919647)

**If people persist in taking this thread off topic I will NOT hesitate to ask the mods to jail OT posts!**

If you don't want to test the non-pae mini.iso then just don't do it.

I prefer metacity or openbox over compiz but you don't see me posting to every compiz thread suggesting others just change window managers!

---

### Post by Ibidem on 2012-02-12
This is the netboot install I mentioned in Lucid testing, FWIW. There's a little info in the archives.

---

### Post by nm_geo on 2012-02-12
Just saw the topic.. consider me in kansas.. I will start downloading the non-pae mini.iso again tonight and trying to install tomorrow.  Any additional thing you want me to try to save time let me know.

Like you my hardware will run the pae kernel just fine.. But we might help some users with pae problems.

---

### Post by kansasnoob on 2012-02-13
> **nm_geo said:**
> Just saw the topic.. consider me in kansas.. I will start downloading the non-pae mini.iso again tonight and trying to install tomorrow.  Any additional thing you want me to try to save time let me know.

Like you my hardware will run the pae kernel just fine.. But we might help some users with pae problems.

Welcome aboard :)

It's been so long since I even used the mini.iso I think today I'll try the standard PAE version just to make comparisons.

One of the nice things about using the mini.iso is that you always get the most recently updated packages, and they typically don't rebuild the images frequently.

The standard pae version is here:

[http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/](http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/)

And, for that matter, the non-pae is also listed there. No change since 20120209.

---

### Post by nm_geo on 2012-02-13
> **kansasnoob said:**
> Welcome aboard :)
 
It's been so long since I even used the mini.iso I think today I'll try the standard PAE version just to make comparisons.
 
One of the nice things about using the mini.iso is that you always get the most recently updated packages, and they typically don't rebuild the images frequently.
 
The standard pae version is here:
 
[http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/](http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/)
 
And, for that matter, the non-pae is also listed there. No change since 20120209.
 
I did just exactly what you mentioned there.  Last week I tired to install the non-pae and ended up installing the pae from the mini.iso. I believe they were the 20120206 versions I now have the 20120209 and will try it later.

---

### Post by kansasnoob on 2012-02-13
I'm performing some testing with the standard PAE version of the Precise mini.iso right now, and I've edited my OP quite a bit, but next I'm going to test the Oneiric mini.iso just as a matter of checking for differences in behavior.

The Oneiric version is here:

[http://www.us.archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/current/images/netboot/](http://www.us.archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/current/images/netboot/)

I particularly want to see if the Oneiric version has the same language support issue and if it's equally difficult to eject the CD when installation is complete.

One more thing, I have a spare flash drive and given how seldom the iso is updated I do intend to try using a flash drive ............... not too sure how to accomplish that :confused:

---

### Post by jerrylamos on 2012-02-13
mini.iso, pae version, booted O.K. on my IBM Thinkpad T40 which does not have the pae flag. To do this, I added the following to the file /etc/grub.d/40_custom being careful to leave what was already in the file 

menuentry "pangolin mini" {
set isofile="/boot/iso/minipae.iso"
loopback loop (hd0,1)$isofile
linux (loop)/linux boot=/ iso-scan/filename=$isofile noprompt noeject
initrd (loop)/initrd.gz
}

As you see above, I have the .iso in a folder /boot/iso.  Your option.  sudo update-grub and reboot the mini.

mini booted O.K. directly from the hard drive, no problem with the missing flag.

As it installed, messages were 3.2.0-15-generic-pae however after booting it up O.K. the boot and /proc/version is 3.2.0.15-generic which is running fine.

Well, I'm used to a whole lubuntu (or unity) setup so there's a lot missing.

What's running on the T40 now is (Lucid Lynx of course), three precise pangolins:

One updated from Oneiric, non-pae

One new install from 20120207 which is generic-pae not supposed to run but does.  My opinion, the test for the flag is missing/doesn't work so it goes on and boots and runs O.K.

One mini install from the pae mini but did result in non-pae generic.  A whole lot of accesories & tools missing but did just get synaptic and even firefox up and running.

Oh, they're all lubuntu's.  I've got unity on other test pc's.

Having fun,

Jerry

---

### Post by kansasnoob on 2012-02-13
> **jerrylamos said:**
> mini.iso, pae version, booted O.K. on my IBM Thinkpad T40 which does not have the pae flag. To do this, I added the following to the file /etc/grub.d/40_custom being careful to leave what was already in the file 

menuentry "pangolin mini" {
set isofile="/boot/iso/minipae.iso"
loopback loop (hd0,1)$isofile
linux (loop)/linux boot=/ iso-scan/filename=$isofile noprompt noeject
initrd (loop)/initrd.gz
}

As you see above, I have the .iso in a folder /boot/iso.  Your option.  sudo update-grub and reboot the mini.

mini booted O.K. directly from the hard drive, no problem with the missing flag.

As it installed, messages were 3.2.0-15-generic-pae however after booting it up O.K. the boot and /proc/version is 3.2.0.15-generic which is running fine.

Well, I'm used to a whole lubuntu (or unity) setup so there's a lot missing.

What's running on the T40 now is (Lucid Lynx of course), three precise pangolins:

One updated from Oneiric, non-pae

One new install from 20120207 which is generic-pae not supposed to run but does.  My opinion, the test for the flag is missing/doesn't work so it goes on and boots and runs O.K.

One mini install from the pae mini but did result in non-pae generic.  A whole lot of accesories & tools missing but did just get synaptic and even firefox up and running.

Oh, they're all lubuntu's.  I've got unity on other test pc's.

Having fun,

Jerry

No doubt you've had irregular results with pae running where non-pae should be needed. I applaud your efforts, but my intention here is to test the non-pae mini.iso and provide very simple installation guidelines :)

---

### Post by jerrylamos on 2012-02-13
> **kansasnoob said:**
> No doubt you've had irregular results with pae running where non-pae should be needed. I applaud your efforts, but my intention here is to test the non-pae mini.iso and provide very simple installation guidelines :)

Sure.  My point is the mini.iso pae version did in fact install the generic non-pae version.  If it does that, then why is there another mini.iso non-pae needed?

Just curious.

Jerry

---

### Post by kansasnoob on 2012-02-13
Regarding that language support issue:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/931191](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/931191)

This is what I see, in the order I see it:

[ATTACH]212643[/ATTACH]

Then I click on Run this action now, and get this:

[ATTACH]212644[/ATTACH]

Then I click on Install and get this:

[ATTACH]212645[/ATTACH]

Then I click on close and get this:

[ATTACH]212646[/ATTACH]

It seems that if I click on "apply system wide" that would be appropriate but I still get further warnings on reboot :confused:

Does anyone understand this?

---

### Post by kansasnoob on 2012-02-13
> **jerrylamos said:**
> Sure.  My point is the mini.iso pae version did in fact install the generic non-pae version.  If it does that, then why is there another mini.iso non-pae needed?

Just curious.

Jerry

No freaking idea :mad:

---

### Post by kansasnoob on 2012-02-13
Don't know how I overlooked this as I often visit Aysiu's page:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

BTW, I realize that's for a CLI install whereas I'm going for actual desktop installs, that way there is no need for a lot of commands, but a lot of that applies!

---

### Post by nm_geo on 2012-02-14
> **kansasnoob said:**
> I'm performing some testing with the standard PAE version of the Precise mini.iso right now, and I've edited my OP quite a bit, but next I'm going to test the Oneiric mini.iso just as a matter of checking for differences in behavior.
 
The Oneiric version is here:
 
[http://www.us.archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/current/images/netboot/](http://www.us.archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/current/images/netboot/)
 
I particularly want to see if the Oneiric version has the same language support issue and if it's equally difficult to eject the CD when installation is complete.
 
One more thing, I have a spare flash drive and given how seldom the iso is updated I do intend to try using a flash drive ............... not too sure how to accomplish that :confused:
 
Since Oneric I believe the isos are made bootable from a flash drive. I know the precise isos are as I have installed at least 3 new installs this way. I do make sure the flash drive has no data on it and format/reformat it to FAT 32.. Just like it comes when new.
 
Here is the way I do it.
 
I keep my isos in a folder called isos.. original huh? LOL 
I make sure in terminal that I am in the correct directory run a ls command to see my isos listed.
 
[COLOR=red]_**Important**_[/COLOR]
Your flash drive might not be sdb mine is (check first)
 
then 
 
sudo dd if=mini.iso of=/dev/sdb
 
I change mini.iso to whatever iso I am working with in Ubuntu. The process is pretty fast and your terminal will show nothing while the process is going on. You might see the flash drive flashing and the HD working. After the process is complete it will tell you how many bytes were copied to the flash drive.
 
I have done this with the mini.iso trying to get a clean non-pae kernel in Lubuntu i386. No luck yet but the flash drive boots well.
 
Others recommenmd netbootin or cd-creator but I find the dd method simpler and faster. The process works for me with the Live CD isos and Alternate isos too.
 
As many warn you need to be careful with the dd command if you get the wrong sdx you will write to whatever device you select.
 
Needless to say my BIOS is setup to boot from USB so I just reboot and Bingo the flash drive loads the iso.
 
Here is the conversation in the Archived Oneric Forum.
 
[http://ubuntuforums.org/showthread.php?t=1783752&highlight=dd+flash+drive](http://ubuntuforums.org/showthread.php?t=1783752&highlight=dd+flash+drive)

---

### Post by nm_geo on 2012-02-14
Ok sorry kansas..

I did load up the 20120209 non-pae mini.iso..
I used the install option .. wish I had tried command line I think
The taskel on the 20120209 version had no Lubuntu or Ubuntu LXDE
I picked manual software option..
Eventually everything installed except for a UI (desktop) 
I tried lubuntu-desktop not available.. bummer.. (Should have sudo apt-get update first I bet)
So I typed in Ubuntu-desktop and watched for nearly an hour (maybe 30 min really)
Well after I got the Ubuntu straight running I load the lubuntu-desktop and I will be uninstalling things for awhile
if I keep this install.  It be running pretty well considering.

I will try the 20120214 non-pae mini.iso tonight or tomorrow..

---

### Post by kansasnoob on 2012-02-14
I didn't see all of the UI options the first time around. It's a long list, you have to use the up and down keyboard arrow keys to scroll the entire list of options.

I may try the new build later tonight. I got side tracked this morning with 10.04.4 iso-testing, and then got wrapped up in a nagging hardware issue that's been haunting me for weeks :(

---

### Post by jerrylamos on 2012-02-15
> **nm_geo said:**
> 
Needless to say my BIOS is setup to boot from USB so I just reboot and Bingo the flash drive loads the iso.

I have a couple testing pc's that won't boot from bios.  To test out an iso I just download it in a folder, preferably in partition /dev/sda1 although I have used /dev/sda.  In this example the folder is /boot/iso.  For larger .iso's I use zsync.

Then I sudo leafpad (or gedit) /etc/grub.d/40_custom and add the following lines to the existing lines, for a mini iso in this case:

```
menuentry "pangolin mini" {
set isofile="/boot/iso/mini.iso"
loopback loop (hd0,1)$isofile
linux (loop)/linux boot=/ iso-scan/filename=$isofile noprompt noeject
initrd (loop)/initrd.gz
}
```

Then do a sudo update-grub

Reboot, select the mini, see how it goes.

After messing around for a while, should I decide to try an install, I boot the mini.iso again, un-mount the isofile as follows 
sudo umount -r -l /dev/sda1
then install.  I prefer to prepare a partition ahead of time with gparted.

I see there's a Feb 15 update to mini.iso.  Let me give it a try, minimal fuss just download the .iso and reboot since grub is already set up.

Jerry

p.s. An actual install over the net is slow here, we have the cheapest i.e. slowest broadband that our carrier offers.

---

### Post by kansasnoob on 2012-02-15
Just BTW the mini.iso lists available installation options named just like they appear in 'tasksel':

```
lance@lance-desktop:~$ tasksel --list-task
u server	Basic Ubuntu server
u openssh-server	OpenSSH server
u dns-server	DNS server
u lamp-server	LAMP server
u mail-server	Mail server
u openstack	Openstack
u postgresql-server	PostgreSQL database
i print-server	Print server
u samba-server	Samba file server
u tomcat-server	Tomcat Java server
u cloud-image	Ubuntu Cloud Image (instance)
u virt-host	Virtual Machine host
u ubuntustudio-graphics	2D/3D creation and editing suite
u ubuntustudio-recording	Audio recording and editing suite
u edubuntu-desktop-kde	Edubuntu KDE desktop (unsupported)
u edubuntu-desktop-gnome	Edubuntu desktop
**[COLOR="Red"]u kubuntu-desktop	Kubuntu desktop[/COLOR]**
u kubuntu-full	Kubuntu full
u kubuntu-mobile	Kubuntu mobile
u ubuntustudio-audio-plugins	LADSPA/LV2/DSSI audio plugins
u ubuntustudio-font-meta	Large selection of font packages
**[COLOR="Red"]u lubuntu-core	Lubuntu minimal installation[/COLOR]**
u mythbuntu-desktop	Mythbuntu additional roles
u mythbuntu-frontend	Mythbuntu frontend
u mythbuntu-backend-master	Mythbuntu master backend
u mythbuntu-backend-slave	Mythbuntu slave backend
u ubuntustudio-generation	Tone generation and editing suite
**[COLOR="Red"]u lubuntu-desktop	Ubuntu LXDE Desktop[/COLOR]**
**[COLOR="Red"]i ubuntu-desktop	Ubuntu desktop[/COLOR]**
u ubuntu-usb	Ubuntu desktop USB
u ubuntustudio-video	Video creation and editing suite
**[COLOR="Red"]u xubuntu-desktop	Xubuntu desktop[/COLOR]**
u edubuntu-dvd-live	Edubuntu live DVD
u kubuntu-mobile-live	Kubuntu Mobile Remix live CD
u kubuntu-live	Kubuntu live CD
u kubuntu-dvd-live	Kubuntu live DVD
u lubuntu-live	Lubuntu live CD
u ubuntustudio-dvd-live	Ubuntu Studio live DVD
u ubuntu-live	Ubuntu live CD
u ubuntu-dvd-live	Ubuntu live DVD
u ubuntu-usb-live	Ubuntu live USB
u xubuntu-live	Xubuntu live CD
**[COLOR="Red"]u manual	Manual package selection[/COLOR]**

```

---

### Post by kansasnoob on 2012-02-15
Found another link with some good screenshots:

[http://xbmcmediacenter.com/how-to-install-ubuntu-mini-iso/](http://xbmcmediacenter.com/how-to-install-ubuntu-mini-iso/)

Having a load of trouble creating a bootable usb flash drive though :(

I personally don't care about wasting CD's, the cost is low, but I imagine some are going to need to use usb.

---

### Post by nm_geo on 2012-02-15
> **kansasnoob said:**
> Found another link with some good screenshots:
 
[http://xbmcmediacenter.com/how-to-install-ubuntu-mini-iso/](http://xbmcmediacenter.com/how-to-install-ubuntu-mini-iso/)
 
Having a load of trouble creating a bootable usb flash drive though :(
 
I personally don't care about wasting CD's, the cost is low, but I imagine some are going to need to use usb.
 
I never use CDs anymore but the dd method works well for me and has since OO.  Colin W made the isos hybrids/bootable... it is so slick.  
 
The mini.iso will show up as CDROM I think but it will work (at least it does for me).

---

### Post by kansasnoob on 2012-02-15
> **nm_geo said:**
> I never use CDs anymore but the dd method works well for me and has since OO.  Colin W made the isos hybrids/bootable... it is so slick.  
 
The mini.iso will show up as CDROM I think but it will work (at least it does for me).

Not sure why, but what I've found following [your guide]("http://ubuntuforums.org/showpost.php?p=11688262&postcount=17") is that it works perfect if I use the whole flash drive, but not if I partition the flash drive and use only the 1st partition to dd to.

I'm guessing because doing so installs isolinux to a pbr rather than an mbr, but I'm purely guessing there :confused:

I wonder why our usb-creator can't create a bootable mini.iso?

I do want to be sure to create a fairly safe, "noob freindly" guide for creating a usb bootable mini.iso before we're done :)

BTW, thanks again for helping out, it really is appreciated.

---

### Post by nm_geo on 2012-02-15
> **kansasnoob said:**
> Not sure why, but what I've found following [your guide]("http://ubuntuforums.org/showpost.php?p=11688262&postcount=17") is that it works perfect if I use the whole flash drive, but not if I partition the flash drive and use only the 1st partition to dd to.
 
I'm guessing because doing so installs isolinux to a pbr rather than an mbr, but I'm purely guessing there :confused:
 
I wonder why our usb-creator can't create a bootable mini.iso?
 
I do want to be sure to create a fairly safe, "noob freindly" guide for creating a usb bootable mini.iso before we're done :)
 
BTW, thanks again for helping out, it really is appreciated.
 
Yes sir, you do need to use the whole flash drive. We found that out when first testing them with Oneiric.  I just keep using the same 4GB flash drive and reformatting it to Fat32 and put whatever I am wanting to install on it. I have more trouble getting it reformatted than anything else.  I find that I can put the mini.iso on in seconds and a full desktop iso on in under 4 minutes.. Slick.. slick it saves me mucho time and of course I use zsync to keep my desktop and alternate isos up to date.

---

### Post by kansasnoob on 2012-02-15
Totally 110% OT, but man-oh-man I'm cold :(

I got chilled yesterday, stayed outside too long, and I just can't get warm. I'm thinking I need some of those silly looking gloves w/o fingers so I can still type :D

Sorry to go OT ;)

---

### Post by nm_geo on 2012-02-15
> **kansasnoob said:**
> Totally 110% OT, but man-oh-man I'm cold :(
 
I got chilled yesterday, stayed outside too long, and I just can't get warm. I'm thinking I need some of those silly looking gloves w/o fingers so I can still type :D
 
Sorry to go OT ;)
 
NP it is your topic. I am trapped in a warm utility system operation control room with no linux available pity me... Well the SCADAs that I administer run Unix it is close enough. 
 
I guess to do every sort of testing I will burn some mini.isos' on CD as well. Hmmmm where are those CDs?
 
I will keep trying the mini.iso installs as many ways as possible confining my attempts to non-pae kernels and Lubuntu Core and Desktop for now. 
 
I might even assist you during the next beta cycle testing but as I still a working man, my time is limited but I am fast :P

---

### Post by kansasnoob on 2012-02-15
Well we need to test both USB and CD installs and ATM I'm looking into the issue of the CD being difficult to eject.

I changed a lot of stuff on that bug report about renaming Ubuntu LXDE to Lubuntu.

---

### Post by kansasnoob on 2012-02-15
Wow, an updated image on the 14th and again on the 15th :D

That's odd for a netboot image.

I may wait until Friday before testing again.

---

### Post by nm_geo on 2012-02-15
> **kansasnoob said:**
> Wow, an updated image on the 14th and again on the 15th :D

That's odd for a netboot image.

I may wait until Friday before testing again.

I am trying the non-pae mini.iso 20120214 right now and might try the 20120215 tomorrow.  I am going to select the lubuntu-core from taskel and save time.. maybe?  Will let you know how well the non-pae pays ;)

Okay, I got another clean non-pae installation using the 20120214 non-pae mini.iso and installed lubuntu-minimal. Installed Synaptic then firefox, network manager to get wireless, firmware-b43-installer from my wireless, a few others...  Used my trusty USB drive to put the mini.iso on using the "dd" method.  Here is a pix of the kernel.
and pix of the System Tools LOL probably need more if I keep this partition alive.

---

### Post by jerrylamos on 2012-02-16
Yay!  mini.iso installed & working fine! (took 3 tries, fumble finger..)

DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux Thinkpad-T40 3.2.0-16-generic #25-Ubuntu SMP Tue Feb 14 02:48:46 UTC 2012 i686 i686 i386 GNU/Linux

Sure enough, 
grep PAE /boot/config-3.2.0-16-generic
did not find PAE=Y.

So I got what I wanted.

Curio, as mini was loading, the messages said "...generic-pae-di"
I don't have a clue what "pae-di" is, I just know I got what I intended since this pc doesn't have the pae flag.

I did make a feeble attempt to look at the debian site but that's way beyond me.

Good go.  Jerry

p.s. This note may not be on topic on this thread, since the mini.iso used was the regular one and not the non-pae one, all I know is I got the non-pae kernel.

Oh, one of the fumble fingers, I selected lubutnu but didn't select print server and/or samba server, so I didn't get any network.  I've go the book but no clue how to install anything with no network.  Re-install working fine.

---

### Post by kansasnoob on 2012-02-16
> **jerrylamos said:**
> Yay!  mini.iso installed & working fine! (took 3 tries, fumble finger..)

DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux Thinkpad-T40 3.2.0-16-generic #25-Ubuntu SMP Tue Feb 14 02:48:46 UTC 2012 i686 i686 i386 GNU/Linux

Sure enough, 
grep PAE /boot/config-3.2.0-16-generic
did not find PAE=Y.

So I got what I wanted.

Curio, as mini was loading, the messages said "...generic-pae-di"
I don't have a clue what "pae-di" is, I just know I got what I intended since this pc doesn't have the pae flag.

I did make a feeble attempt to look at the debian site but that's way beyond me.

Good go.  Jerry

p.s. This note may not be on topic on this thread, since the mini.iso used was the regular one and not the non-pae one, all I know is I got the non-pae kernel.

Oh, one of the fumble fingers, I selected lubutnu but didn't select print server and/or samba server, so I didn't get any network.  I've go the book but no clue how to install anything with no network.  Re-install working fine.

I certainly think it's OT enough. I just wish we could figure why your hardware has generally unusual results :confused:

As I've said, I'm clueless :)

---

### Post by kansasnoob on 2012-02-16
Has anyone else used an actual CD to install using a mini.iso? I find it quite difficult to remove the CD, particularly so on one set of testing hardware.

On my old VIA hardware with an IDE CD/DVD writer when I reboot I can pretty easily eject the disc during reboot, that is the drive tray remains open until I close it.

But on my Intel box with a super great SATA ASUS CD/DVD writer trying to eject the disc is tricky because the BIOS screen passes quickly and the drive tray retracts almost too quickly for my arthritic old hand to handle ;)

I just wonder if it's worth filing a bug report over????

---

### Post by jerrylamos on 2012-02-16
> **kansasnoob said:**
> I certainly think it's OT enough. I just wish we could figure why your hardware has generally unusual results :confused:

As I've said, I'm clueless :)
Well, I'd appreciate more results from more people posted here....looking at one bug report, I forget the #, there reports on Thinkpad T42 Pentium R.  I don't know if they are continuing to try things or just gave up.

Jerry

---

### Post by kansasnoob on 2012-02-16
> **jerrylamos said:**
> Well, I'd appreciate more results from more people posted here....looking at one bug report, I forget the #, there reports on Thinkpad T42 Pentium R.  I don't know if they are continuing to try things or just gave up.

Jerry

Sort of laughing at myself ATM. I meant you're on topic, not off topic. I guess it's time to trash the abbreviation "OT" :D

I agree about the need for additional testers. I have no effected hardware and I'd love to see more of those with non-pae hardware do some testing.

But even if nothing gets fixed/changed with the mini.iso's we could explain our way around it :)

---

### Post by nm_geo on 2012-02-16
> **kansasnoob said:**
> Sort of laughing at myself ATM. I meant you're on topic, not off topic. I guess it's time to trash the abbreviation "OT" :D

I agree about the need for additional testers. I have no effected hardware and I'd love to see more of those with non-pae hardware do some testing.

But even if nothing gets fixed/changed with the mini.iso's we could explain our way around it :)

Yes i was wondering how Jerry was off topic there??!!  

My last minimal install non-pae does have one minor problem that I am researching,  When i boot it waits 

for the network configuration ...then waits 60 seconds ...then boots without network configuration.. takes a 

few minutes to boot this partition..  After I log in No Problem.. 

Network Configuration wireless is working fine..

But we do have some working non-pae kernels running Lubuntu

I am still going to test the CD installs this weekend..

---

### Post by nm_geo on 2012-02-17
Resolved my slow booting by commenting out references to the auto eth0..
 
in etc/network/interfaces.  Now my mini.iso install takes only a few seconds from boot 
 
to working. Super fast start up I may run some tests to see just how fast it is 
 
compared to my other versions.  Of course it is very light and if I did not add dropbox 
 
and others that I think I must have it would be even faster.

---

### Post by kansasnoob on 2012-02-17
> **nm_geo said:**
> Resolved my slow booting by commenting out references to the auto eth0..
 
in etc/network/interfaces.  Now my mini.iso install takes only a few seconds from boot 
 
to working. Super fast start up I may run some tests to see just how fast it is 
 
compared to my other versions.  Of course it is very light and if I did not add dropbox 
 
and others that I think I must have it would be even faster.

My previous network problem ended up being BIOS related, and for some reason I don't understand my new TP-LINK router works better (maybe should say easier) than my older TrendNet router.

Before retirement I worked with telecom/data cable manufacturing and I even did some LAN wiring, but I never had to deal with "delivery" from WAN to LAN, nor anything regarding home networks, so I get lost when it comes to home networking problems :(

---

### Post by nm_geo on 2012-02-17
> **kansasnoob said:**
> My previous network problem ended up being BIOS related, and for some reason I don't understand my new TP-LINK router works better (maybe should say easier) than my older TrendNet router.
 
Before retirement I worked with telecom/data cable manufacturing and I even did some LAN wiring, but I never had to deal with "delivery" from WAN to LAN, nor anything regarding home networks, so I get lost when it comes to home networking problems :(
 
I have decided today that I am going to get bootchart running on all my versions just for comparison sake.  That mini.iso install running Lubuntu 12.04 that I got working is fast as lightning on my Dell D620 and I want to know what that lightning time is...:D
 
Besides, I might find some start-up bloat on my others versions that can be removed.

---

### Post by jerrylamos on 2012-02-18
BTW. mini.iso booted (from hard drive as above) accessed wireless just fine and installed fine over wireless.  Well, it took a while.........  

Resulting precise pangolin also got wireless, do note that I checked off print server and samba server - we have a home network - and lubuntu.  I tried installing without the servers and didn't get any network at all.

From time to time ubuntu distros of late when booting is looking for eth0 which isn't attached.  Wireless came up as eth1.

There wasn't any network applet, so I did a sudo apt-get install network-manager (my opinion, notwork-mangler) which put the applet on the panel working fine.

Jerry

---

### Post by Ibidem on 2012-02-18
[http://ubuntuforums.org/showthread.php?t=1376336](http://ubuntuforums.org/showthread.php?t=1376336) was my Lucid netboot install.
Netboot does tend to be fast.
(BTW, these days I usually use debootstrap--which is even worse for the first-timer.
It's a script that installs a deb-based distro in a chroot, which you then configure to boot.)

For networking, I use wpa_supplicant and /etc/network/interfaces.

---

### Post by jerrylamos on 2012-02-18
> **nm_geo said:**
> Resolved my slow booting by commenting out references to the auto eth0..
 
in etc/network/interfaces.  Now my mini.iso install takes only a few seconds from boot 
 
to working. Super fast start up I may run some tests to see just how fast it is 
 
compared to my other versions.  Of course it is very light and if I did not add dropbox 
 
and others that I think I must have it would be even faster.?
I looked at /etc/network/interfaces no mention of wired eth0.  See below. 
There is no wired ethernet attached.

Why does mini-iso lubuntu wait and wait for the network, then say it is waiting for 60 seconds more??  What is telling it to do that?  Sure doesn't look like /etc/network/interfaces to me?

```
# This file describes the network interfaces available on your system

# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid any
```

After bootup, lubuntu desktop, some seconds later wireless connects.

Thanks for any ideas.

Jerry

---

### Post by nm_geo on 2012-02-18
> **jerrylamos said:**
> ?
I looked at /etc/network/interfaces no mention of wired eth0.  See below. 
There is no wired ethernet attached.

Why does mini-iso lubuntu wait and wait for the network, then say it is waiting for 60 seconds more??  What is telling it to do that?  Sure doesn't look like /etc/network/interfaces to me?

```
# This file describes the network interfaces available on your system

# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
    # wireless-* options are implemented by the wireless-tools package
    wireless-mode managed
    wireless-essid any
```After bootup, lubuntu desktop, some seconds later wireless connects.

Thanks for any ideas.

Jerry

All good questions.. Here is what mine looks like and it boots wireless before login now.. No delays anymore on this end boot time 11 seconds crazy fast.

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet dhcp

---

### Post by jerrylamos on 2012-02-18
nm_geo,

Could well be the differences in the /etc/network/interfaces is that I installed network-manager, primarily to get the panel applet.

Based on your posting, I commented out just one line:

# auto eth1

and left all the rest.

It worked!  Booted right up, no wait, wireless and all!?

Well, thanks for the suggestion!

Jerry

---

### Post by nm_geo on 2012-02-18
> **jerrylamos said:**
> nm_geo,

Could well be the differences in the /etc/network/interfaces is that I installed network-manager, primarily to get the panel applet.

Based on your posting, I commented out just one line:

# auto eth1

and left all the rest.

It worked!  Booted right up, no wait, wireless and all!?

Well, thanks for the suggestion!

Jerry

NP glad you got it figured out.. Some users will probably be glad to see all these little issues we are resolving with the non-pae min.. That is if they are patient enough to go through the process.

---

### Post by jerrylamos on 2012-02-19
I don't know how to feed some of these results back to development.  The slow boot up is, do you think, back in Debian?  Not sure it's worth while writing a bug on slow boot up since Debian & Ubuntu development are concentrating on the very latest fastest huge memory exotic architecture $$ pc's that will run lots of overhead like Unity-3D, revolving windows, ...

So anyhow I appreciate these forums where us users can trade hints.

Jerry

---

### Post by kansasnoob on 2012-02-19
> **jerrylamos said:**
> I don't know how to feed some of these results back to development.  The slow boot up is, do you think, back in Debian?  Not sure it's worth while writing a bug on slow boot up since Debian & Ubuntu development are concentrating on the very latest fastest huge memory exotic architecture $$ pc's that will run lots of overhead like Unity-3D, revolving windows, ...

So anyhow I appreciate these forums where us users can trade hints.

Jerry

If the slow boot is due to searching for a network I've recently encountered that with even live installs. I was doing some testing this AM and I think we're just in a major borkage stage of development.

I mean feature freeze just passed and UI freeze comes on the 23rd, then we have just a week to squash huge bugs before Beta 1. So I think a lot of things are just in a state of flux right now :)

I'm personally waiting for 'tasksel' to be updated in the repos, and a new netboot/mini image to follow ............... we're gaining ;)

---

### Post by nm_geo on 2012-02-19
> **kansasnoob said:**
> If the slow boot is due to searching for a network I've recently encountered that with even live installs. I was doing some testing this AM and I think we're just in a major borkage stage of development.

I mean feature freeze just passed and UI freeze comes on the 23rd, then we have just a week to squash huge bugs before Beta 1. So I think a lot of things are just in a state of flux right now :)

I'm personally waiting for 'tasksel' to be updated in the repos, and a new netboot/mini image to follow ............... we're gaining ;)

I think the slow boot is certainly due to network searching and would be common to all Ubuntu mini.iso versions.

I am just glad that we do have a answer to the user whose hardware 

will not run a pae kernel and I think we do. Lots more testing coming 

soon. I am in the process of getting my hard drives cloned and ready..

---

### Post by Catharsis on 2012-02-22
Oh cool, I've been waiting since December for this to become a big deal, haha.

I had to stop testing my Pentium M laptop back in December when they switched the kernel in the LiveCD. I'll start testing the mini iso this weekend and help out. Thanks for the heads up on this install method.

I hear talk about documentation for non-pae computers. I'd be willing to help with this. Had to do it already for the i8xx fiasco back in Lucid :)

---

### Post by kansasnoob on 2012-02-22
> **Catharsis said:**
> Oh cool, I've been waiting since December for this to become a big deal, haha.

I had to stop testing my Pentium M laptop back in December when they switched the kernel in the LiveCD. I'll start testing the mini iso this weekend and help out. Thanks for the heads up on this install method.

I hear talk about documentation for non-pae computers. I'd be willing to help with this. Had to do it already for the i8xx fiasco back in Lucid :)

Thanks, I really do need all the help I can get ............ seriously :D

It seems like every time I turn around either me or my hardware have some health problem :lolflag:

Hardware problems have just been biting me in the rear end lately, not expensive failures, just annoying :)

---

### Post by nm_geo on 2012-02-22
> **Catharsis said:**
> Oh cool, I've been waiting since December for this to become a big deal, haha.
 
I had to stop testing my Pentium M laptop back in December when they switched the kernel in the LiveCD. I'll start testing the mini iso this weekend and help out. Thanks for the heads up on this install method.
 
I hear talk about documentation for non-pae computers. I'd be willing to help with this. Had to do it already for the i8xx fiasco back in Lucid :)
 
Let us know how the non-pae mini.iso works for you we will keep this topic as current as possible for those that have the Pentium M and other 
 
processors that are not pae compatible. Kansas are you planning on a wiki page or thread with instructions?

---

### Post by jerrylamos on 2012-02-22
> **nm_geo said:**
> Let us know how the non-pae mini.iso works for you we will keep this topic as current as possible for those that have the Pentium M and other
I'm finding this thread very useful - keep it up.  Actually this is a notebook with Pentium M with no pae flag, running non-pae 3.2.0-17-generic which was actually installed with the regular mini.iso.  Messages said generic-pae-di was being installed but what it actually did was install the generic exactly what I wanted.  Runs fine (for an Alpha).  Fun installing just what I want and not all the other packages I'll never use.

On my fast tower I've got full boat Unity-3D for testing purposes, and Unity-2D on my netbook.

Keep up the good work.

Jerry

---

### Post by kansasnoob on 2012-02-23
> Kansas are you planning on a wiki page or thread with instructions?

I won't do a wiki page, but I plan on submitting a how-to here:

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

I think Lubuntu will want to update their wiki:

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

If you look at my OP I pointed to this guide:

[http://xbmcmediacenter.com/how-to-install-ubuntu-mini-iso/](http://xbmcmediacenter.com/how-to-install-ubuntu-mini-iso/)

I think that's pretty good with a few exceptions (I'd really appreciate some feedback and suggestions here):

* Step seven involves the "host-name". This may confuse some users. The best way I can explain this is:

> This is the name used to identify the computer on your network, if you're used to using the live installer it's simply called "computer name" there and it's created for you when you enter your full name and user name, eg;

If your full name is "John Smith", and you keep the user name "john" your computer name will typically be something like "john-desktop".

* Step ten involves an HTTP proxy. I think the explanation there is generally sufficient, what do you think? I've never had to set up an HTTP proxy so I don't know what to say :confused:

* Step twelve involves partitioning and that's always a scary thing, I find it reckless to just say, "Leave it as it is and hit Enter, if you’re not familiar with partitioning disks." No doubt the debian installer does a pretty good job but I think I'll say something like:

> Partitioning can be a complex issue so unless you plan on erasing everything on your hard drive(s) please ask for some guidance here before even beginning:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)


Of course any installation guide should begin by warning of potential data loss :)

* Step nineteen regards encryption, I never do so. What do you think the appropriate thing to say here is?

* Step twenty one involves what DE to install, I just tried the 20120221 non-pae mini.iso and lubuntu-desktop is still called "Ubuntu LXDE desktop" :(

* Step twenty three mentions the UTC clock settings and that step no longer exists in the current images.

But we also need to provide a fairly foolproof method of creating a bootable USB, your method is OK but using "dd" can be inherently risky for complete noobs. I wonder why our USB creator won't work with the mini.iso?

---

### Post by jerrylamos on 2012-02-23
> But we also need to provide a fairly foolproof method of creating a bootable USB, your method is OK but using "dd" can be inherently risky for complete noobs. I wonder why our USB creator won't work with the mini.iso?
I've had erratic success with USB - what level of what stick on what pc which ubuntu to use for usb create (they're different!) inetbootin, et. al.

Primitive (!) dd could work but dangerous, and and my experience very very fussy about the USB format.

Given I'm using more than one partition for development testing, I've got a ubuntu up so no problem, download the mini.iso, gparted to create a partition, create a grub2 entry, boot the .iso direct, sudo umount -r -l isodevice, and away I go on install.  Much less fuss than fiddling with USB.

Same technique works for oversized .iso images media size no issue.  zsync an existing .iso and install much faster than mini.iso over network. 

I wonder if there is an image which is mini.iso plus the base system up to the tasksel point?  Would save me a lot of time since zsync is faster than repeat network loading. 

Fun,

Jerry

---

### Post by kansasnoob on 2012-02-23
> I wonder if there is an image which is mini.iso plus the base system up to the tasksel point? Would save me a lot of time since zsync is faster than repeat network loading. 

Not that I'm aware of, but the actual installer is basically the same as the alternate installer.

---

### Post by cariboo on 2012-02-23
This is a little off-topic, but the Debian netinstall iso is about 165MiB if I remember correctly, I don't have a copy available at the moment, but I wonder what is included on it, to make it so much larger.

I pay for a 7.5Mbps internet connection here, I don't find that it takes that much more time to do a full installation using the mini.iso.

[[IMG]http://www.speedtest.net/result/1792393562.png[/IMG]](http://www.speedtest.net)

The above results show way better speeds than I pay for. :D

---

### Post by kansasnoob on 2012-02-23
> **cariboo907 said:**
> This is a little off-topic, but the Debian netinstall iso is about 165MiB if I remember correctly, I don't have a copy available at the moment, but I wonder what is included on it, to make it so much larger.

I pay for a 7.5Mbps internet connection here, I don't find that it takes that much more time to do a full installation using the mini.iso.

[[IMG]http://www.speedtest.net/result/1792393562.png[/IMG]](http://www.speedtest.net)

The above results show way better speeds than I pay for. :D

Wow, that's almost 4X the speed I have :o

---

### Post by kansasnoob on 2012-02-23
About my own "how-to", I think I'll go this direction:

Name it something like "How to install a 12.04 (Precise) non-pae system".

Then give a brief explanation of Canonicals decision regarding pae by default, not supporting non-pae beyond 12.04, etc.

Next get into the three options:

#1: Upgrade from 11.10. This should work for Ubuntu, Kubuntu, Xubuntu, and Lubuntu ..... but I need to check out upgrades from fresh, NOT updated, installations of each.

#2: Upgrade from 10.04. This will NOT work for Lubuntu! But it should work for Ubuntu, Kubuntu, and Xubuntu. Again I need to test upgrades from fresh, NOT updated, installations of each.

#3: Using the mini.iso. I will NOT offer any option other than burning a CD! With the new Feb 23 mini.iso I once again encountered significant problems creating a bootable USB ....... not sure why, but I won't offer an option that I'm not totally confident in :)

All thoughts and help are welcome :guitar:

---

### Post by kansasnoob on 2012-02-23
Now they broke tasksel and the mini.iso's:

[https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/931237/comments/5](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/931237/comments/5)

Really does make me mad :mad:

There's nothing mentioned in the tasksel changelog so I can't even place blame!

---

### Post by cariboo on 2012-02-23
That's the only choice I had when I installed it last week.

---

### Post by jerrylamos on 2012-02-23
I don't know how to take a sceenshot with this mini iso lubuntu, so the speedtest.net results were 85 ms ping, 1.45 mbs download, .46 mbps upload.

I think that's the cheapest service from my internet provider.

mini install zzzzzz.

Jerry

---

### Post by kansasnoob on 2012-02-23
> **cariboo907 said:**
> That's the only choice I had when I installed it last week.

That's one of the reasons I've been checking the 'tasksel' changelog from the Ubuntu main server. At this point I really must say that the entire mini.iso installation process can be extremely problematic. In other words it kind of sucks :(

I'm going to step away from testing the mini.iso until Beta 1 iso-testing is over. It's just too time consuming and it seems obvious that the devs don't even take it serious :(

IMHO the devs should seriously reconsider this whole PAE by default, but non-pae supported debacle! I mean how many people have more than 3 or 4 GB of RAM that can't run the 64 bit version?

I think sometimes the devs are totally out of touch with reality :(

End-of-rant, sorry, like I said ............ time to walk away and calm down :)

---

### Post by kansasnoob on 2012-02-23
> **jerrylamos said:**
> I don't know how to take a sceenshot with this mini iso lubuntu, so the speedtest.net results were 85 ms ping, 1.45 mbs download, .46 mbps upload.

I think that's the cheapest service from my internet provider.

mini install zzzzzz.

Jerry

You'd have to be running the mini.iso/net-install in a VM to be able to take a screenshot :)

---

### Post by jerrylamos on 2012-02-24
> **kansasnoob said:**
> 
IMHO the devs should seriously reconsider this whole PAE by default, but non-pae supported debacle! I mean how many people have more than 3 or 4 GB of RAM that can't run the 64 bit version?

I think sometimes the devs are totally out of touch with reality :(

End-of-rant, sorry, like I said ............ time to walk away and calm down :)
We started out in 1982 with an original 64 kb IBM pc and 5 1/4 floppy's.  Over the years, yes, memory has increased and so has disk space.

Over the life of Pangolin LTS 5 years or whatever, no way there's going to be a preponderance of ubuntu users that just absolutely have to address more than 3.2 GB of ram.  My prediction anyway.

One more telling example that Ubuntu management isn't listening.  Ubuntu's not the only fish in the ocean, we'll see.  

I'm back to updating & testing whatever distro will run on my pc's esp. with good forums. 

Jerry

---

### Post by cariboo on 2012-02-24
> **jerrylamos said:**
> We started out in 1982 with an original 64 kb IBM pc and 5 1/4 floppy's.  Over the years, yes, memory has increased and so has disk space.

Over the life of Pangolin LTS 5 years or whatever, no way there's going to be a preponderance of ubuntu users that just absolutely have to address more than 3.2 GB of ram.  My prediction anyway.

One more telling example that Ubuntu management isn't listening.  Ubuntu's not the only fish in the ocean, we'll see.  

I'm back to updating & testing whatever distro will run on my pc's esp. with good forums. 

Jerry


I not sure where you live, but around here most new computer systems, especially those with Windows 7 pre-installed come standard with 4GiB of ram, and as most new users are coming from Windows, 4GiB ram will be the norm, for most computer enthusiasts, 4GiB may not be enough for what they want to do, so we will see more and more users with well over 4GiB of ram.

As you say Ubuntu isn't the only distribution, and even if it doesn't support older non-pae capable cpu's, there will always be other distribution that do. I would venture to guess that older non-pae cpu's will have a hard a time running the latest release of Ubuntu as they would running the latest version of Windows.

2017 seems to be a long ways away, but whose to say that the majority of non-pae cpu's will even be running by the time Precise eol's. Also keep in mind that even though Precise will be supported for 5 years, I haven't seen anything about dropping new LTS releases every 2 years, so it won't be possible at all to run the next Ubuntu release on non-pae cpu's.

---

### Post by nm_geo on 2012-02-24
> **kansasnoob said:**
> That's one of the reasons I've been checking the 'tasksel' changelog from the Ubuntu main server. At this point I really must say that the entire mini.iso installation process can be extremely problematic. In other words it kind of sucks :(
 
I'm going to step away from testing the mini.iso until Beta 1 iso-testing is over. It's just too time consuming and it seems obvious that the devs don't even take it serious :(
 
IMHO the devs should seriously reconsider this whole PAE by default, but non-pae supported debacle! I mean how many people have more than 3 or 4 GB of RAM that can't run the 64 bit version?
 
I think sometimes the devs are totally out of touch with reality :(
 
End-of-rant, sorry, like I said ............ time to walk away and calm down :)
 
Me too on mini.iso installation kinda sucks..  
Me too on stepping away from mini.iso for Beta iso testing..
Me too ...
Me too..
Me too..
Me too.. rant over..
 
Now considering the freeze went on while I was sleeping last night ):Pand they forgot to tell me.
 
Will Lubuntu Desktop isos get to fix that black/Dark grey installation issue on the screens?
 
Just trying to plan on how close to the laptop screen I need to get to actually read the instructions.. :p

---

### Post by kansasnoob on 2012-02-24
> **cariboo907 said:**
> I not sure where you live, but around here most new computer systems, especially those with Windows 7 pre-installed come standard with 4GiB of ram, and as most new users are coming from Windows, 4GiB ram will be the norm, for most computer enthusiasts, 4GiB may not be enough for what they want to do, so we will see more and more users with well over 4GiB of ram.

As you say Ubuntu isn't the only distribution, and even if it doesn't support older non-pae capable cpu's, there will always be other distribution that do. I would venture to guess that older non-pae cpu's will have a hard a time running the latest release of Ubuntu as they would running the latest version of Windows.

2017 seems to be a long ways away, but whose to say that the majority of non-pae cpu's will even be running by the time Precise eol's. Also keep in mind that even though Precise will be supported for 5 years, I haven't seen anything about dropping new LTS releases every 2 years, so it won't be possible at all to run the next Ubuntu release on non-pae cpu's.

But how many of those same "new computer systems" won't support 64 bit :confused:

I totally did not understand the whole pae thing in the beginning, that's why I started a thread asking about it, but I've studied enough now to understand the general reasoning behind the creation of a pae kernel.

But making pae the default is IMHO a bad mistake based on misjudgment. Those with more than 4GB of RAM could have easily installed a non-pae system and then upgraded to pae, but we've now created a dilemma for a small but still significant number of Ubuntu devotee's who will find it difficult to do a fresh install of Ubuntu (or try the live DE) :(

Since I put up that question at "Answers" I've had a few people contact me via PM, plus those who did so publicly there, or at the subsequent bug report, and some of them have multiple machines effected by this.

It really is just like the live-installer devs deciding nobody really used the option "use largest continuous free space" ........ wrong, wrong, wrong! Or the nonsense about a cat being more likely to hit Ctrl+Alt+Bkspc than Alt+SysReq+K ............. just total BS :mad:

Regardless we end users always have to clean up the mess!

I'm just taking a day or two off to calm down. I get particularly angry when a bug is marked "fix released" but the "fix" results in total borkage.

---

### Post by A_T on 2012-02-25
> **cariboo907 said:**
> This is a little off-topic, but the Debian netinstall iso is about 165MiB if I remember correctly, I don't have a copy available at the moment, but I wonder what is included on it, to make it so much larger.

I pay for a 7.5Mbps internet connection here, I don't find that it takes that much more time to do a full installation using the mini.iso.

[[IMG]http://www.speedtest.net/result/1792393562.png[/IMG]](http://www.speedtest.net)

The above results show way better speeds than I pay for. :D

The Debian mini.iso is only 16MB. It also works with my wireless adapter which the Ubuntu one never has.

---

### Post by kansasnoob on 2012-02-27
BTW I'm not done testing this, I'm just busy ;)

---

### Post by Catharsis on 2012-02-27
Well I finally got the mini.iso to boot, but it turns out it doesn't include the b43 kernel module for some godforsaken reason so I can't get my internet up despite having the firmware.

This whole non-pae mini.iso nonsense is such a mess. It's stuff like this that made me start using Arch. If Ubuntu is doing everything they can to make sure I don't use their OS then I sometimes wonder why I'm trying so hard to use it.

---

### Post by cariboo on 2012-02-27
> **A_T said:**
> The Debian mini.iso is only 16MB. It also works with my wireless adapter which the Ubuntu one never has.

If you look at this [page]("http://www.debian.org/CD/netinst/"), right in the middle of the page it says:

> netinst CD image (generally 135-175 MB)

Even the business card iso is bigger than the Ubuntu/Lubuntu etc mini.iso.

As far as working with your wireless adapter, I have two that work with the Ubuntu mini.iso, and one that doesn't, so it depends on the adapter.

---

### Post by A_T on 2012-02-27
> **cariboo907 said:**
> If you look at this [page]("http://www.debian.org/CD/netinst/"), right in the middle of the page it says:



Even the business card iso is bigger than the Ubuntu/Lubuntu etc mini.iso.

As far as working with your wireless adapter, I have two that work with the Ubuntu mini.iso, and one that doesn't, so it depends on the adapter.

Debian has the business card and netinstall cds - but also a 16MB mini.iso

[http://ftp.debian.org/debian/dists/squeeze/main/installer-amd64/current/images/netboot/](http://ftp.debian.org/debian/dists/squeeze/main/installer-amd64/current/images/netboot/)

There is also one for Wheezy

[http://ftp.debian.org/debian/dists/wheezy/main/installer-amd64/current/images/netboot/](http://ftp.debian.org/debian/dists/wheezy/main/installer-amd64/current/images/netboot/)

---

### Post by jerrylamos on 2012-02-27
Cariboo07,> netinst CD image (generally 135-175 MB) 
I wonder if something like that would get around the 
"too big to fit on a CD" hopefully installing to the hard disk from the CD/USB up to tasksel and use the net after that.
Jerry

---

### Post by cariboo on 2012-02-27
Removed duplicate post. 

@jerrylamos, I hope you don't expect new users to use tasksel. :) Keep in mind, we won't know if the Precise final iso will be over 700MiB until at the earliest Beta 2 which will be released at the end of March.

---

### Post by kansasnoob on 2012-02-28
It looks like 'tasksel' is back where it was before I requested a change so when Beta 1 testing is complete I'll be giving this a fresh try :D

We can live with "lubuntu-desktop' being called Ubuntu LXDE desktop ;)

---

### Post by kansasnoob on 2012-03-02
OK, vacation's over ;)

Thought I'd get back to this while the pressure's off, and I notice that there have been no changes in the non-pae mini.iso since Feb 27th. 

Current tasksel functions:

```
lance@lance-desktop:~$ tasksel --list-task
u server	Basic Ubuntu server
u openssh-server	OpenSSH server
u dns-server	DNS server
u lamp-server	LAMP server
u mail-server	Mail server
u openstack	Openstack
u postgresql-server	PostgreSQL database
i print-server	Print server
u samba-server	Samba file server
u tomcat-server	Tomcat Java server
u cloud-image	Ubuntu Cloud Image (instance)
u virt-host	Virtual Machine host
u ubuntustudio-graphics	2D/3D creation and editing suite
u ubuntustudio-recording	Audio recording and editing suite
u edubuntu-desktop-kde	Edubuntu KDE desktop (unsupported)
u edubuntu-desktop-gnome	Edubuntu desktop
u kubuntu-desktop	Kubuntu desktop
u kubuntu-full	Kubuntu full
u kubuntu-mobile	Kubuntu mobile
u ubuntustudio-audio-plugins	LADSPA/LV2/DSSI audio plugins
u ubuntustudio-font-meta	Large selection of font packages
u lubuntu-core	Lubuntu minimal installation
u mythbuntu-desktop	Mythbuntu additional roles
u mythbuntu-frontend	Mythbuntu frontend
u mythbuntu-backend-master	Mythbuntu master backend
u mythbuntu-backend-slave	Mythbuntu slave backend
u ubuntustudio-generation	Tone generation and editing suite
u lubuntu-desktop	Ubuntu LXDE Desktop
i ubuntu-desktop	Ubuntu desktop
u ubuntu-usb	Ubuntu desktop USB
u ubuntustudio-video	Video creation and editing suite
u xubuntu-desktop	Xubuntu desktop
u edubuntu-dvd-live	Edubuntu live DVD
u kubuntu-mobile-live	Kubuntu Mobile Remix live CD
u kubuntu-live	Kubuntu live CD
u kubuntu-dvd-live	Kubuntu live DVD
u lubuntu-live	Lubuntu live CD
u ubuntustudio-dvd-live	Ubuntu Studio live DVD
u ubuntu-live	Ubuntu live CD
u ubuntu-dvd-live	Ubuntu live DVD
u ubuntu-usb-live	Ubuntu live USB
u xubuntu-live	Xubuntu live CD
u manual	Manual package selection

```

I plan on testing:

Lubuntu minimal installation, which is 'lubuntu-core'.

Ubuntu LXDE Desktop, which is 'lubuntu-desktop'.

Ubuntu desktop, which is 'ubuntu-desktop'.

But it would be super cool if folks that are familiar with Kubuntu and Xubuntu would test:

Kubuntu desktop, which is 'kubuntu-desktop'.

Xubuntu desktop, which is 'xubuntu-desktop'.

But testing is the easy part, the hard part is producing a guide that any noob can understand .......... it's fairly easy for me to play the noob because I'm intellectually challenged :tongue:

I still think we can largely depend on this guide:

[http://xbmcmediacenter.com/how-to-install-ubuntu-mini-iso/](http://xbmcmediacenter.com/how-to-install-ubuntu-mini-iso/)

As explained in post #53 I do think we need to more properly explain the "hostname", HTTP proxy, and a little bit about partitioning. Any thoughts?

Also I'd really like a fairly reliable and safe way to set up a USB flash drive for installation. Remember we want to be noob friendly. I think this should be doable using a small flash drive:

[https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet](https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet)

I know it's written for use with an actual hard drive, but I'm thinking someone should be able to create a bootable usb drive using any version of grub from any installed Ubuntu, installing grub to the mbr of that flash drive, etc. But the "etc'" is killing me.

Really any thoughts at all are welcome. Sometimes a robust discussion awakens otherwise sleeping brain cells :D

---

### Post by kansasnoob on 2012-03-02
Update on the bootable USB :D

It appears that unetbootin will work :guitar:

Even it's a bit funky if you're not used to file structure but I tried it and it works. But I've only been able to try it on the same box I created the USB on due to hardware failure.

So right now I'm going to concentrate on what happened to the PSU that Fedex says they delivered on Wednesday but I never saw .............. I already know what happened! My low-life neighbors stole the damn thing :(

Sad to have crappy neighbors :cry:

But the previous builds of the netboot image show up on the unetbootin menu so I'll fire a message off to their dev(s) asking if they'll make both standard and non-pae available so noobs don't have to fiddle around much.

---

### Post by Catharsis on 2012-03-02
For anyone keeping track, I filed a bug report for the lack of the b43 wireless driver in the mini.iso as Bug [lpbug]945053[/lpbug].

---

### Post by kansasnoob on 2012-03-02
> **Catharsis said:**
> For anyone keeping track, I filed a bug report for the lack of the b43 wireless driver in the mini.iso as Bug [lpbug]945053[/lpbug].

Thank you!

But I'd always understood that a wired connection was needed for netboot. Am I wrong?

---

### Post by Catharsis on 2012-03-02
> **kansasnoob said:**
> Thank you!

But I'd always understood that a wired connection was needed for netboot. Am I wrong?

I have no idea, I'd never even heard of it until you started this thread :)

If that's the case then it probably will just get marked Invalid.

---

### Post by nm_geo on 2012-03-02
> **Catharsis said:**
> I have no idea, I'd never even heard of it until you started this thread :)

If that's the case then it probably will just get marked Invalid.

I guess the question is can you connect to an ethernet cable wired?  I also have the b43 wireless driver and I can get mine working after installing the mini.iso.

We really need your hard ware to be tested and get the non-pae kernel working it would be great.

---

### Post by Catharsis on 2012-03-03
> **nm_geo said:**
> I guess the question is can you connect to an ethernet cable wired?  I also have the b43 wireless driver and I can get mine working after installing the mini.iso.

We really need your hard ware to be tested and get the non-pae kernel working it would be great.

I don't have access to a wired internet connection, that's the problem. I could probably find one, but I wouldn't have reliable access to it if I needed to keep testing the mini.iso install.

I'm looking into upgrading through an Oneiric install, which is much easier but presents its own bugs, which I'm working through now too.

---

### Post by kansasnoob on 2012-03-03
Now that I know UNetbootin works fairly easily to create a bootable mini.iso flash drive something I need to look into for those who do not have easy access to a fast wired connection is the possibility of performing a CLI mini.iso installation and then installing the desired desktop environment from an external source, such as a CD or USB created using 'aptoncd' or something similar.

Clear back around Hardy I actually used 'aptoncd' to work on computers in environments that had only dial-up. I live in a rural area and sometimes dial-up is still the only option :(

I no longer do that, I just use a loaner PC, bring their PC to my home and do the maintenance here. That way I don't have to cart around a bunch of crap. Also better because I can no longer drive due to vision loss :)

So I think that's possible, challenging but possible.

Any thoughts at all regarding that are welcome.

---

### Post by jerrylamos on 2012-03-03
> **kansasnoob said:**
> Now that I know UNetbootin works fairly easily to create a bootable mini.iso flash drive something I need to look into for those who do not have easy access to a fast wired connection is the possibility of performing a CLI mini.iso installation and then installing the desired desktop environment from an external source, such as a CD or USB 

Any thoughts at all regarding that are welcome.
Note, the CD alternate install will still fit on a CD (or USB) find the selection at:
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)
I'm visiting our daughter on a borrowed Thinkpad T60 (Pentium R, no pae flag) so I can't try using the alternate to see which kernel - pae or non-pae - would be installed.  Next week at home maybe.  Do note in my previous replies I prefer downloading the .iso and booting it directly from hard drive so size doesn't matter.

The Thinkpad T series are still quite responsive and fast,so I'm interested in keeping Ubuntu running on them.

Jerry

---

### Post by kansasnoob on 2012-03-03
> **jerrylamos said:**
> Note, the CD alternate install will still fit on a CD (or USB) find the selection at:
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)
I'm visiting our daughter on a borrowed Thinkpad T60 (Pentium R, no pae flag) so I can't try using the alternate to see which kernel - pae or non-pae - would be installed.  Next week at home maybe.  Do note in my previous replies I prefer downloading the .iso and booting it directly from hard drive so size doesn't matter.

The Thinkpad T series are still quite responsive and fast,so I'm interested in keeping Ubuntu running on them.

Jerry

The alternate images use the PAE kernel just like the live images. The only Precise installation media that can be used to install non-pae is the correct mini.iso.

---

### Post by nm_geo on 2012-03-04
> **kansasnoob said:**
> The alternate images use the PAE kernel just like the live images. The only Precise installation media that can be used to install non-pae is the correct mini.iso.

Yes sir the only way right now..

I did another non-pae build yesterday and it works but I sure got it confused,  Still using the unity-greeter for login and running the LXDE desktop versus straight Lubuntu.  Looks cool though I like the icons.

---

### Post by Catharsis on 2012-03-05
Found myself a wired internet connection. Unfortunately, I also found Bug [lpbug]946856[/lpbug].

---

### Post by kansasnoob on 2012-03-06
> **Catharsis said:**
> Found myself a wired internet connection. Unfortunately, I also found Bug [lpbug]946856[/lpbug].

Sorry I haven't had time to check out the Mar 3rd mini.iso yet. I finally got the parts to hopefully deal with my hardware issues. I got one box rebuilt yesterday and I'm going to tackle the second one today :D

The greatest challenge is finding a way to deal with wireless access only situations. Not sure yet how to deal with that :(

---

### Post by dino99 on 2012-03-06
> **Catharsis said:**
> Found myself a wired internet connection. Unfortunately, I also found Bug [lpbug]946856[/lpbug].

ubuntu//dists/precise/ might be  ubuntu/dists/precise/    i suppose (double / ?)

---

### Post by verymadpip on 2012-03-08
Hi folks.
Feel free to kick me out of here if this is off topic.

Today I managed to install to a Compaq TC1000 tablet (Transmeta T5800 Crusoe 1GHz CPU) using the non-PAE mini iso from March 3rd.  It all went pretty smoothly, even to the point of being able to use a USB wireless adaptor (WPA PSK encryption) for the install.  Now I just need to cobble together the UI.  

I've sacrificed the touch & stylus functions as there are some issues with them for 'everyday use', but that's another story.

---

### Post by kansasnoob on 2012-03-08
> **verymadpip said:**
> Hi folks.
Feel free to kick me out of here if this is off topic.

Today I managed to install to a Compaq TC1000 tablet (Transmeta T5800 Crusoe 1GHz CPU) using the non-PAE mini iso from March 3rd.  It all went pretty smoothly, even to the point of being able to use a USB wireless adaptor (WPA PSK encryption) for the install.  Now I just need to cobble together the UI.  

I've sacrificed the touch & stylus functions as there are some issues with them for 'everyday use', but that's another story.

Not off-topic at all. Hope to hear the whole story, especially regarding wireless :D

---

### Post by nm_geo on 2012-03-10
Started with the non-pae mini.iso..20120303
installed the lubuntu-core (minimal)
Got a clean install then proceed to apt-get synaptic then used it to lubuntu-desktop
Added to many of my choice things.. :D

Then decided I would just see about the remastersys creates a distribution custom.iso..  So I did..
It worked as liveCD and had an install icon for custom.iso
SOOOOo.. just did that too.

Only thing that went wrong I have no option where to install the grub so it obviously in my MBR ...
I will fix that not a problem back to my Lucid partition.

Secondly the custom.iso is really to large about 803MB at this point so i will trim off the LXDE and other stuff i plugged in on the next attempt.. Anyway I am pleased as puddin.. :P

---

### Post by bubbajunk on 2012-03-12
Most of the steps seem pretty straight forward, up to the point of the selection of the desktop. If my goal is to replicate the installation that would be produced from the Ubuntu CD iso image, I assume I'd choose Ubuntu Desktop. 

What is not clear to me is whether or not this includes all applications and packages contained in the standard cd image file, e.g. LibreOffice, Firefox, Gedit, Network Manager, etc. Will these packages need to be added after the Unity Desktop package completes? Forgive me if this is an obvious question, but I've never completed an install from the mini.iso.

---

### Post by cariboo on 2012-03-12
> **bubbajunk said:**
> Most of the steps seem pretty straight forward, up to the point of the selection of the desktop. If my goal is to replicate the installation that would be produced from the Ubuntu CD iso image, I assume I'd choose Ubuntu Desktop. 

What is not clear to me is whether or not this includes all applications and packages contained in the standard cd image file, e.g. LibreOffice, Firefox, Gedit, Network Manager, etc. Will these packages need to be added after the Unity Desktop package completes? Forgive me if this is an obvious question, but I've never completed an install from the mini.iso.

If you go to [packages.ubuntu.com]("http://packages.ubuntu.com/"), and search for ubuntu-desktop, you get a listing of all the packages that are a part of the ubuntu-desktop meta-package.

---

### Post by nm_geo on 2012-03-13
> **bubbajunk said:**
> Most of the steps seem pretty straight forward, up to the point of the selection of the desktop. If my goal is to replicate the installation that would be produced from the Ubuntu CD iso image, I assume I'd choose Ubuntu Desktop. 

What is not clear to me is whether or not this includes all applications and packages contained in the standard cd image file, e.g. LibreOffice, Firefox, Gedit, Network Manager, etc. Will these packages need to be added after the Unity Desktop package completes? Forgive me if this is an obvious question, but I've never completed an install from the mini.iso.

The short answer is yes.  It will take typically an hour or more to get all the packages automatically downloaded and installed.  But when you think about it, if you do not have the full regular desktop-iso and you download it that takes quite awhile to do as well.

The beauty of the mini.iso is that you can customize the install the way you want it particularly if you do the ubuntu-core or the lubuntu-core first then boot the install.  Then build from that install and get exactly what you want. 

Of course, when you are not sure exactly how you want it the ubuntu-desktop would be a good choice.  Just be very patient it takes awhile for sure.

---

### Post by kansasnoob on 2012-03-14
I see there's a new March 14th image. I have a doctors appointment today but maybe this evening I can check it out :)

---

### Post by verymadpip on 2012-03-14
> **kansasnoob said:**
> I see there's a new March 14th image. I have a doctors appointment today but maybe this evening I can check it out :)

Now that's tempting.

On the other hand the TC1000 is working quite well.  I even managed to install ndiswrapper from a tar.gz - which was a first for me.  (That was to get a ***different*** USB wireless adaptor working).

Decisions, decisions...

---

### Post by nm_geo on 2012-03-14
> **kansasnoob said:**
> I see there's a new March 14th image. I have a doctors appointment today but maybe this evening I can check it out :)

Got it.. will dd to a Flash drive & check later..

---

### Post by nm_geo on 2012-03-15
Notice there was a new mini.iso dated 20120315 today... Never got the 20120314 iso tested but at least the new one worked okay.  Mine was built to the Lubuntu-desktop non-pae kernel and it is doing just fine so far.  Well i did get a apport bug right after booting the install.. 

Here is the link for the non-pae mini.iso

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

Just in case you need it or want to test a mini.iso build with the non-pae kernel.

Out

---

### Post by nm_geo on 2012-03-19
Lubuntu 12.04 desktop has a non-pae kernel as of last spin

Linux tester-Latitude-D620 3.2.0-19-generic #30-Ubuntu SMP Fri Mar 16 16:26:45 UTC 2012 i686 i686 i386 GNU/Linux
 
Not sure why the Mar 16 date this was zsynced today 20120319.

Anyway got a clean install and updated the qa-tracker.

---

### Post by kansasnoob on 2012-03-20
> **nm_geo said:**
> Lubuntu 12.04 desktop has a non-pae kernel as of last spin

Linux tester-Latitude-D620 3.2.0-19-generic #30-Ubuntu SMP Fri Mar 16 16:26:45 UTC 2012 i686 i686 i386 GNU/Linux
 
Not sure why the Mar 16 date this was zsynced today 20120319.

Anyway got a clean install and updated the qa-tracker.

Woo-hoo!!!!!!!!!!

This basically puts the mini.iso testing on the back burner ;)

I still think I'll type up some brief notes regarding mini.iso installs before Precise final hits.

It's never a waste of time testing this stuff, I learned that UNetbootin works quite easily for creating a bootable mini.iso thumb drive.

Also, something I plan on trying soon is a cli install followed by installing only 'gnome-session-fallback' just to see how complete (or incomplete) the installation is and how much 'unity' is pulled in with it - just for fun.

---

### Post by jerrylamos on 2012-03-20
Just zsync'd lubuntu today.  Booted the .iso directly from hard disk and installed on Pentium M which does not have a pae flag.

jerry@ThinkPad-T40:~$ cat /proc/version
Linux version 3.2.0-19-generic (buildd@vernadsky) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu3) ) #30-Ubuntu SMP Fri Mar 16 16:26:45 UTC 2012

Note it's generic with no pae in sight.  

Installed. put in firefox instead of chromium, added flashplayer and aptitude, updated, put in my own wallpaper, and it's 1889800 bytes.

pcmanfm hasn't crashed yet ???

Running well.

Jerry

---

### Post by kansasnoob on 2012-04-16
Using the [netboot mini.iso]("http://cdimage.ubuntu.com/netboot/") is considerably reliant on a fast wired internet connection. My ethernet speed is 5000kbps+ and the average total installation time is 1 hour and 45 minutes, but on a positive note you're getting the latest packages so you'll have little or no updates to install after the installation is complete.

The images are quite small, typically under 30MB, and they can either be burned to disc or you can create a [bootable USB using Unetbootin]("http://www.psychocats.net/ubuntu/usb"). If you're familiar with the Debian installer or the Ubuntu alternate installer this will all seem quite straight forward to you. If not there is a [good guide here]("http://www.psychocats.net/ubuntu/minimal") for using the mini.iso to perform a Command-Line Install.

That should give you a good idea of what the installation screens look like but **for our purpose most users will be fine just choosing "Install"** from the boot options and then '[tasksel]("https://help.ubuntu.com/community/Tasksel")' will offer a list of options at the end of the installation (It's a long list and you must use the keyboard arrow keys to scroll through the entire list - I've highlighted those of interest):

```
u server	Basic Ubuntu server
u openssh-server	OpenSSH server
u dns-server	DNS server
u lamp-server	LAMP server
u mail-server	Mail server
u openstack	Openstack
u postgresql-server	PostgreSQL database
i print-server	Print server
u samba-server	Samba file server
u tomcat-server	Tomcat Java server
u cloud-image	Ubuntu Cloud Image (instance)
u virt-host	Virtual Machine host
u ubuntustudio-graphics	2D/3D creation and editing suite
u ubuntustudio-recording	Audio recording and editing suite
u edubuntu-desktop-kde	Edubuntu KDE desktop (unsupported)
u **edubuntu-desktop-gnome	Edubuntu desktop**
u **kubuntu-desktop	Kubuntu desktop**
u kubuntu-full	Kubuntu full
u kubuntu-mobile	Kubuntu mobile
u ubuntustudio-audio-plugins	LADSPA/LV2/DSSI audio plugins
u ubuntustudio-font-meta	Large selection of font packages
u lubuntu-core	Lubuntu minimal installation
u **mythbuntu-desktop	Mythbuntu additional roles**
u mythbuntu-frontend	Mythbuntu frontend
u mythbuntu-backend-master	Mythbuntu master backend
u mythbuntu-backend-slave	Mythbuntu slave backend
u ubuntustudio-generation	Tone generation and editing suite
u **lubuntu-desktop	Ubuntu LXDE Desktop**
i **ubuntu-desktop	Ubuntu desktop**
u ubuntu-usb	Ubuntu desktop USB
u ubuntustudio-video	Video creation and editing suite
u **xubuntu-desktop	Xubuntu desktop**
u edubuntu-dvd-live	Edubuntu live DVD
u kubuntu-mobile-live	Kubuntu Mobile Remix live CD
u kubuntu-live	Kubuntu live CD
u kubuntu-dvd-live	Kubuntu live DVD
u lubuntu-live	Lubuntu live CD
u ubuntustudio-dvd-live	Ubuntu Studio live DVD
u ubuntu-live	Ubuntu live CD
u ubuntu-dvd-live	Ubuntu live DVD
u ubuntu-usb-live	Ubuntu live USB
u xubuntu-live	Xubuntu live CD
u manual	Manual package selection

```

I've personally only tested 'ubuntu-desktop', 'lubuntu-desktop', and 'xubuntu desktop' so I can't comment on the rest but my experience has been generally good. I would however point out the following things to consider during installation:

* You'll be asked if you want the installer to detect your keyboard layout or proceed with the default (I always just select No when asked and the US keyboard defaults seem fine for me).

* Specify the hostname for your system - this may confuse new users, but I typically use my first name accompanied by some computer ID or location, eg; john-AMD-desktop, or john-INTEL-laptop. This will be how your computer is recognized on your network.

* HTTP proxy - I'm totally clueless here as I've never dealt with such

* Encrypt home directory? I've never done so, but [this]("http://askubuntu.com/questions/37/when-installing-im-given-the-option-of-encrypting-my-home-folder-what-does-t") may be helpful to others.

* Partitioning gets rather complex so I'll not get into detail here, but one nice thing is that the "Use largest continuous free space" option still exists.

* After quite some time you'll be asked about how to handle updates - Select 'No Automatic Updates' (trust me).

As with any installation if you have questions please ask them in [this forum subsection]("http://ubuntuforums.org/forumdisplay.php?f=333").

---

