---
title: "How stable is 12.04 right now?"
date: 2011-12-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by josephellengar on 2011-12-19
I know the answer is going to be "not stable enough for daily use," but before you answer that, please hear me out.

I need to do a reinstallation of both Ubuntu and Windows and am off from school right now, so was thinking that now would be a good time to do it. My Ubuntu installation is several years old. I'm still using 10.10, and whenever I try to upgrade I get various failures, kernel panics, etc, that nobody has ever been able to solve. So I was thinking that I would switch to the 2 year LTS cycle and reinstall every time so that I didn't have to deal with the painful Ubuntu upgrade process.

So, I guess my question is, could I install 12.04 right now and feasibly use it to browse the web, run a few applications (CodeBlocks, Wine+MSOffice, etc) and manage files? I really don't do much more than that. As I understand it, this release won't have any new features beyond standard package updates, so I don't see why it would be as unstable as a short-term release, even during development. But anyway, what do you think?

Thanks! And cheers to all of the people who put their hard work and many man-hours into making this project possible. And to Mark Shuttleworth, our benevolent dictator-for-life.

---

### Post by jbicha on 2011-12-19
The correct answer is to just install 11.10 and wait at least until Beta 1 or 2 to upgrade to 12.04. 11.10 is definitely more stable than 12.04 currently.

If you want to run the development release, you need to be prepared to reinstall if things go wrong and as always, have backups of your data. And remember than re-installing takes time so it's probably not a good idea to do a system upgrade and reboot 10 minutes before you have to turn in a homework assignment or something. ;-)

I've been running the development release for a few years now but it took me a while to figure out how to do it relatively safely and how to fix things when they break.

---

### Post by josephellengar on 2011-12-19
> **jbicha said:**
> The correct answer is to just install 11.10 and wait at least until Beta 1 or 2 to upgrade to 12.04. 11.10 is definitely more stable than 12.04 currently.

If you want to run the development release, you need to be prepared to reinstall if things go wrong and as always, have backups of your data. And remember than re-installing takes time so it's probably not a good idea to do a system upgrade and reboot 10 minutes before you have to turn in a homework assignment or something. ;-)

I've been running the development release for a few years now but it took me a while to figure out how to do it relatively safely and how to fix things when they break.

Oh thanks, good advice. I don't really want to install 11.10 since I always have bad luck with upgrades. I can almost never get them to go smoothly and very frequently can't get them to work at all (which is why I'm still on 10.10), so I guess I'll just wait for the beta.

---

### Post by bcschmerker on 2011-12-19
That's the strategy that I've adopted.  Ubuntu® has backports of newer Releases' kernel images and modules for 10.04.4-LTS; however, if ye've need for Restricted X-servers (packages: nvidia-current, nvidia-settings, fglrx, fglrx-amdcccle), I would not advise going newer than Kernel 2.6.38 (package: linux-image-*-lts-backport-natty).  Kernel 3.0.0.14 (package: linux-image-generic-pae-lts-backport-oneiric) forced me back to a Hewlett-Packard® HP2009m  from a Polaroid® TV that I was testing as a display unit, as both [Advance Micro Devices®](http://www.amd.com/) and [nVIDIA®](http://www.nvidia.com/) have yet to catch up with the [LinUX Kernel Project](http://www.kernel.org/) on proper support for Kernel 3.0.

---

### Post by Ibidem on 2011-12-20
I suspect the issue with upgrades might be readily solved.
On the Debian forums, I frequently run across comments about how a dist-upgrade should never be done from X, and claims that that's probably the issue with Ubuntu's upgrades.
If you ever want to try doing it the other way, here's what it would take:
Ctrl+Alt+F1, login, sudo -s
**stop your display manager** (service lightdm stop/service gdm stop)
--while the next two steps can be done before this, be sure not to start the dist-upgrade without this step.
Edit /etc/apt/source.list
apt-get update
apt-get dist-upgrade
And reboot.

---

### Post by fabricator4 on 2011-12-20
> **josephellengar said:**
> So, I guess my question is, could I install 12.04 right now and feasibly use it to browse the web, run a few applications (CodeBlocks, Wine+MSOffice, etc) and manage files? I really don't do much more than that. As I understand it, this release won't have any new features beyond standard package updates, so I don't see why it would be as unstable as a short-term release, even during development. But anyway, what do you think?

Right now, the alpha1 is pretty flaky.  Update manager hangs, there's 39 packages that are being held back waiting for dependencies (probably a new kernel) and various breakage elsewhere also.

Is it stable enough for web browsing?  Sure, at the moment.  Even that could change before the release of alpha2 however.  As for Wine: I wouldn't like to say.  I haven't seen any information on it but you'd have to be pretty brave to run 12.04 if was your only computer and you really just had to have MessyWord running under Wine.

What I would suggest is if you decide you just have to do it set up a separate /home partition.   That way you can reinstall quickly without having to worry about your data.  You could also re-install an earlier version if you had to just as easily.  Just use separate login names for 11.10 and LTS or whatever, since some of the settings may not be compatible between the two (though I've done this too, with very little problems).

With the newer versions you can upgrade from the LiveCD if you want to.  There's several advantages of downloading the ISO and making the LiveCD/USB:

* If anything goes wrong, you've still got the LiveCD to boot off and fix it.  Online upgrades that go wrong leave you only the ancient version on CD...  If the disk is still OK.

* You can check the ISO against the md5sum.  Extra peace of mind.

* You can boot the new LiveCD/USB and test the new OS and read the release notes.  No sudden surprises (you should have heard the squarking when people did an upgrade on their system and suddenly discovered they had Unity...)

* You can re-use the CD at any time to re-install or install the OS on other computers.

* The LiveCD has extra tools like Gparted that can make life easier.

* As stated, you can do an upgrade from the LiveCD now: There's really no reason to do an online upgrade any more.  It just seems way too risky and time consuming to me.

If you do upgrade, do NOT at any time do a partial update if asks you in update manager.  Also expect to get familiar with the command line and fixing things that are broken, or at least using command line alternatives for things that are broken.  At the moment for example, updates are best done with:

sudo apt-get update && sudo apt-get upgrade


Chris

---

### Post by Harry33 on 2011-12-20
> **fabricator4 said:**
> Right now, the alpha1 is pretty flaky.  Update manager hangs, there's 39 packages that are being held back waiting for dependencies (probably a new kernel) and various breakage elsewhere also.
...
Chris

Well I have all the packages installed that are available.
Nothing being held back. The latest installed packages are from today.
Certainly the new kernel (3.2.0-rc6) does not cause any hold backs, it installs just fine.

You may have "a not so ordinary setup", or you are using Update manager to update.
Please try Synaptic. Update manager is not for dev cycles anyway.

---

### Post by sgage on 2011-12-20
> **josephellengar said:**
> I know the answer is going to be "not stable enough for daily use," but before you answer that, please hear me out.

I need to do a reinstallation of both Ubuntu and Windows and am off from school right now, so was thinking that now would be a good time to do it. My Ubuntu installation is several years old. I'm still using 10.10, and whenever I try to upgrade I get various failures, kernel panics, etc, that nobody has ever been able to solve. So I was thinking that I would switch to the 2 year LTS cycle and reinstall every time so that I didn't have to deal with the painful Ubuntu upgrade process.

So, I guess my question is, could I install 12.04 right now and feasibly use it to browse the web, run a few applications (CodeBlocks, Wine+MSOffice, etc) and manage files? I really don't do much more than that. As I understand it, this release won't have any new features beyond standard package updates, so I don't see why it would be as unstable as a short-term release, even during development. But anyway, what do you think?

Thanks! And cheers to all of the people who put their hard work and many man-hours into making this project possible. And to Mark Shuttleworth, our benevolent dictator-for-life.

I am now using 12.04 as my daily workhorse, and find it to be just fine. I do not, however, use Unity - actually, most of the time I'm in Gnome Classic. 

Neither do I use Update Manager - I have always used Synaptic, and still do.

I occasionally use MS Office 2007 under Wine, and it works. There's some simple trick to making Power Point work which you can easily google up.

There may be packages held back now and then. Just don't do the update right then - just wait, and it will be resolved, sometimes very quickly. I have no packages held back at the moment, but again, I don't have Unity installed.

Oh, and one last thing... I back up every day :KS

---

### Post by grahammechanical on 2011-12-20
This section of the forum has a sticky thread called: I am offered a partial upgrade - what should I do? Read this thread and obey it.

If you have space on your hard drive you could install 12.04 into another partition and test it out. This is what I am doing.

I have 11.10 and a separate /home partition (having that is a data saver any old time). Right now I am using 12.04, which I find stable enough to use as my daily working Ubuntu. I access my data and documents on the separate /home partition. I do not store data on this 12.04.

Oh, by the way. I did not upgrade from 11.04 to 11.10. I did a fresh install from a live CD download. Less problems that way. In fact no problems that way. This is why the separate /home partition is most useful.

Regards.

---

### Post by josephellengar on 2011-12-20
> **sgage said:**
> I am now using 12.04 as my daily workhorse, and find it to be just fine. I do not, however, use Unity - actually, most of the time I'm in Gnome Classic. 

Neither do I use Update Manager - I have always used Synaptic, and still do.

Oh, and one last thing... I back up every day :KS

How do you use Synaptic to update, and why?

> **Ibidem said:**
> I suspect the issue with upgrades might be readily solved.
On the Debian forums, I frequently run across comments about how a dist-upgrade should never be done from X, and claims that that's probably the issue with Ubuntu's upgrades.
If you ever want to try doing it the other way, here's what it would take:
Ctrl+Alt+F1, login, sudo -s
**stop your display manager** (service lightdm stop/service gdm stop)
--while the next two steps can be done before this, be sure not to start the dist-upgrade without this step.
Edit /etc/apt/source.list
apt-get update
apt-get dist-upgrade
And reboot.


How do you connect to a wireless hotspot if you don't have X on?

---

### Post by sgage on 2011-12-20
> **josephellengar said:**
> How do you use Synaptic to update, and why?

Run Synaptic, click on Reload, look at list of updates (if any) so you know exactly what's going to happen, then if it looks good (99% of the time) click on Mark All Upgrades, then Apply.

Why? Because I can see what's going on at every stage of the operation. Easy to search for packages. Easy to check out the update history. Etc.

The thread below this one at this moment is "Update Manager Woes".  ;-)

---

### Post by julianb on 2011-12-20
You can use Precise as your day to day OS provided you know it might crash and burn:popcorn: without warning. I recommend you have a good plan for. what to do if yOS fails. Like boot into your lucid lynx or winXP install or use another machine while you sort out what's wrong with this one. Or run off a liveCD that is known to work. but go for it. I did and everything is Fine and dandy

---

### Post by jbicha on 2011-12-20
You don't have to use a separate /home as the Ubuntu installer is smart enough to not wipe the /home directory unless you explicitly tell it to format that partition in the advanced partitioner.

The upgrade option from the Live CD is really great and I wish more people knew about it. It's much faster than downloading hundreds of megabytes of files and installing them one by one. One caveat is that you shouldn't use if it you've customized /var (MySQL databases for instance); I don't know if /etc is kept or not. Except for that caveat, it's safer too.

---

### Post by sammiev on 2011-12-20
I have been lucky so far as 12.04 been great for me and it seems I have had better luck than others. I have been using 12.04 before Alpha1 but likely try a fresh install tomorrow just to see how stable the install is. Must add I really enjoy 12.04 so far. :)

---

### Post by josephellengar on 2011-12-20
> **jbicha said:**
> You don't have to use a separate /home as the Ubuntu installer is smart enough to not wipe the /home directory unless you explicitly tell it to format that partition in the advanced partitioner.

The upgrade option from the Live CD is really great and I wish more people knew about it. It's much faster than downloading hundreds of megabytes of files and installing them one by one. One caveat is that you shouldn't use if it you've customized /var (MySQL databases for instance); I don't know if /etc is kept or not. Except for that caveat, it's safer too.

I currently use a separate /home partition on my 10.10 install. If I were to install 12.04, and kept the /home, would I have problems with the configuration files? For example, I see a config directory for gnome in ~. Would this cause problems since I would be jumping to a much newer version of gnome? Or could I just keep these config files and have most of my configurations stay consistent?

---

### Post by Ibidem on 2011-12-21
The simple way is to turn X off after connecting to the wireless.  That's what I'd recommend in most cases.

I usually just use wpa_supplicant (a CLI tool/daemon) these days, though iwconfig will also work
There's also wicd-cli and the commandline version of networkmanager. 
```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scanning|more
sudo iwconfig wlan0 essid any # connects to any (unencrypted) network
sudo dhclient wlan0 
```

---

### Post by zika on 2011-12-21
> **Harry33 said:**
> Well I have all the packages installed that are available.
Nothing being held back. The latest installed packages are from today.
Certainly the new kernel (3.2.0-rc6) does not cause any hold backs, it installs just fine.

You may have "a not so ordinary setup", or you are using Update manager to update.
Please try Synaptic. Update manager is not for dev cycles anyway.Ditto. You, simply put, need to use dist-upgrade from time to time, to allow erasure of obsolete packages and introduction of a few new...

---

### Post by tlu on 2011-12-21
> **josephellengar said:**
> I currently use a separate /home partition on my 10.10 install. If I were to install 12.04, and kept the /home, would I have problems with the configuration files? For example, I see a config directory for gnome in ~. Would this cause problems since I would be jumping to a much newer version of gnome? Or could I just keep these config files and have most of my configurations stay consistent?

That's a good question. In my experience, you can indeed run into problems if you keep this and other folders in your /home. Thus, **before** performing a release upgrade I always do the following:

1. Logoff.
2. Ctrl+Alt+F1
3. Execute mv .gnome .gnome_old
4. Do the same for .gnome2, .kde (if applicable), .config and .local.

After performing the release upgrade it's very easy to *selectively* copy sub-folders (like the ones under .config) to the newly created folders.

This strategy has served me well in the past.

---

### Post by fabricator4 on 2011-12-21
> **Harry33 said:**
> Well I have all the packages installed that are available.
Nothing being held back. The latest installed packages are from today.
Certainly the new kernel (3.2.0-rc6) does not cause any hold backs, it installs just fine.

You may have "a not so ordinary setup", or you are using Update manager to update.
Please try Synaptic. Update manager is not for dev cycles anyway.

No, the setup is bog standard.  It's offering a partial upgrade, and so is holding back all of those packages waiting for dependancies.  If it doesn't clear in a week or so I may try a new install, or hold off testing until alpha2.  The list of packages in the partial is definitely growing.

```
chris2@chris2-preciseA1:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  brasero brasero-cdrkit cups deja-dup evince file-roller gir1.2-rb-3.0
  gir1.2-totem-1.0 gir1.2-vte-2.90 gnome-disk-utility gnome-orca
  gnome-terminal gnome-terminal-data libbrasero-media3-1 libevince3-3
  libfolks-eds25 libfolks-telepathy25 libfolks25 libgdk-pixbuf2.0-0
  libgssapi-krb5-2 libk5crypto3 libkrb5-3 libkrb5support0 liboauth0
  librhythmbox-core4 libsane libsdl1.2debian libvte-2.90-9 libvte-common
  libvte9 linux-generic linux-headers-generic linux-image-generic lsb-release
  nautilus nautilus-share network-manager poppler-utils python-apt
  python-gobject python-vte rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugins software-center totem totem-common totem-mozilla
  totem-plugins transmission-common transmission-gtk ttf-khmeros-core
  ttf-takao-pgothic ubuntu-desktop ubuntuone-client-gnome vino
  xserver-xorg-video-nouveau
0 upgraded, 0 newly installed, 0 to remove and 57 not upgraded.

```

---

### Post by zika on 2011-12-21
> **fabricator4 said:**
> No, the setup is bog standard.  It's offering a partial upgrade, and so is holding back all of those packages waiting for dependancies.  If it doesn't clear in a week or so I may try a new install, or hold off testing until alpha2.  The list of packages in the partial is definitely growing.

```
chris2@chris2-preciseA1:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  brasero brasero-cdrkit cups deja-dup evince file-roller gir1.2-rb-3.0
  gir1.2-totem-1.0 gir1.2-vte-2.90 gnome-disk-utility gnome-orca
  gnome-terminal gnome-terminal-data libbrasero-media3-1 libevince3-3
  libfolks-eds25 libfolks-telepathy25 libfolks25 libgdk-pixbuf2.0-0
  libgssapi-krb5-2 libk5crypto3 libkrb5-3 libkrb5support0 liboauth0
  librhythmbox-core4 libsane libsdl1.2debian libvte-2.90-9 libvte-common
  libvte9 linux-generic linux-headers-generic linux-image-generic lsb-release
  nautilus nautilus-share network-manager poppler-utils python-apt
  python-gobject python-vte rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugins software-center totem totem-common totem-mozilla
  totem-plugins transmission-common transmission-gtk ttf-khmeros-core
  ttf-takao-pgothic ubuntu-desktop ubuntuone-client-gnome vino
  xserver-xorg-video-nouveau
0 upgraded, 0 newly installed, 0 to remove and 57 not upgraded.

```By all means, there is no need for new install...
That is normal with testing...
Give us otput of ```
sudo apt-get dist-upgrade
```
[COLOR=Red]Carefull[/COLOR], choose &#8222;q&#8220; as the answer to the question, at the end...

---

### Post by MoreOrLess on 2011-12-21
If you don't like the 6 month upgrade dance, you might have better luck with a rolling release distro. Something based off Debian Testing (like Linux Mint Debian Edition) might ultimately make your life easier than running alphas or only using LTS releases. Just a thought...

---

### Post by fabricator4 on 2011-12-21
> **jbicha said:**
> You don't have to use a separate /home as the Ubuntu installer is smart enough to not wipe the /home directory unless you explicitly tell it to format that partition in the advanced partitioner.

I've actually found it a little hit-or-miss for repairing a broken system, especially alphas and betas. A couple of frustrating experiences left me with less than full confidence in it.  I think the problem may be that it doesn't always downgrade a package to the install level, messing up any dependencies in the process.

Having said that, it is a method I recommend on Launchpad and elsewhere for people to try repairing a broken system.  It's had both stunning successes and abject failures, but I think the successes outweigh the failures so far.

Having said all that, the absolute best method is to just format and re-install root if there is a separate /home.  It's faster and you can have full confidence that the system is in good condition with all packages at the correct release level.

> 
The upgrade option from the Live CD is really great and I wish more people knew about it. It's much faster than downloading hundreds of megabytes of files and installing them one by one. One caveat is that you shouldn't use if it you've customized /var (MySQL databases for instance); I don't know if /etc is kept or not. Except for that caveat, it's safer too.

I'm still not a fan, obviously, but yes I'd recommend the CD upgrade over the online one always, for the reasons I previously stated.

Chris

---

### Post by bcschmerker on 2011-12-21
Thanks for keeping me informed on the progress of Precise Pangolin™.  While still running Lucid Lynx™ (10.04.4-LTS with backported Kernel 3.0.0.14 from Oneiric Ocelot™ as of 21 December 2011), I can preplan for a fresh install of 12.02b1-pre, 12.03b2-pre, or 12.04rc as Packages stabilize, on a fresh set of SATA hard drives (as my hybrid Everex® can physically handle four), backdating the optical drive to the stock PATA version for compatibility with likely upgrade sound cards---my current Creative Laboratories® SB0350 is running on borrowed time (failing I/O Drive), and Auzentech® may have a perfect replacement in the new X-Meridian™ 7.1 2G/X-Tension™ DIN™ package (C-Media® CMI8788; ALSA® Driver: snd-oxygen).

---

### Post by sammiev on 2011-12-21
Well all was going good with 12.04 from the pre-alpha update so I decided to try a fresh install from Dec 20 build. Downloaded todays ISO and tried to install both CD and USB. Install went very well and the checksum from the download was perfect. Now that is where it stop. Updates do not work at all. Will play some more and post back later.

---

### Post by fabricator4 on 2011-12-21
> **sammiev said:**
> Now that is where it stop. Updates do not work at all. 

That's what we said. :lolflag:

Chris

---

### Post by sammiev on 2011-12-21
Have updates working again. As soon as I added gnome3 I was good to go again. :)

---

### Post by IsraeliHawk on 2012-01-21
> **sammiev said:**
> Have updates working again. As soon as I added gnome3 I was good to go again. :)

so, through your perspective, is it ok to try running the 12.04 LTS as a main machine? (dell inspiron 1525 laptop)

cheers

---

### Post by zika on 2012-01-21
> **IsraeliHawk said:**
> so, through your perspective, is it ok to try running the 12.04 LTS as a main machine? (dell inspiron 1525 laptop)

cheersFrom my experience in Testing there is no clear answer to question of Yours until the release. And (even) after that... That is (solely) Your decision. I made mine years ago...

---

### Post by jbicha on 2012-01-21
> **IsraeliHawk said:**
> so, through your perspective, is it ok to try running the 12.04 LTS as a main machine? (dell inspiron 1525 laptop)

cheers

The short, simple answer is "no". Ubuntu 12.04 is still Alpha. Just last development cycle, there was a nasty bug that broke networking for people unfortunate enough to have upgraded at just the wrong time and rebooted before they upgraded again to get the fix. Broken networking made it especially "fun" to try to upgrade or downgrade to a working state. That bug was just before Beta 2 was released. If you're running the development version, be prepared to have your operating system fail at some point, which could be bad if you depend on your computer working for school, job, or whatever.

That being said, most of the people that post in this subforum are running Ubuntu 12.04. I've been running the development release for years. It just depends on how well you can fix things when they go wrong and how many problems you're willing to put up with. My wife's computer is still on Ubuntu 11.10 if that says anything. :)

---

### Post by VinDSL on 2012-01-21
> **jbicha said:**
> Just last development cycle, there was a nasty bug that broke networking for people unfortunate enough to have upgraded at just the wrong time and rebooted before they upgraded again to get the fix. Broken networking made it especially "fun" to try to upgrade or downgrade to a working state.[...]
I might mention...

In this dev cycle, I have yet to get network-manger working on this desktop box (under Linux 3.2). ;)

I see Linux 3.3rc1 is available in mainline.  I might try that, in a few minutes.

---

### Post by fabricator4 on 2012-01-21
> **IsraeliHawk said:**
> so, through your perspective, is it ok to try running the 12.04 LTS as a main machine? (dell inspiron 1525 laptop)

cheers

No.

Not unless you like the challenge of fixing broken things.  It's certainly a learning experience, but not always enjoyable, or at least not all of the time.  The recent 3.2.0-10 kernel update broke Xorg for me last night with the recommended nvidia driver module, and I couldn't get any res over 1024x768...  only just fixed it this morning.  Come to think of it, the previous upgrade to 3.2.0-9 also broke Xorg on my machine, taking several hours to fix by eventually getting nvidia to write an xorg.conf file and then editing it so it made sense.

Testing is great; it's mostly fun, you get to see the changes and potential problems well before others, and you do learn something.  I don't recommend it for your main machine however.  Run it on a spare machine, or at least a VM if you don't have the extra hardware.  I certainly don't recommend it for an _only_ machine.

Chris

---

### Post by keithpeter on 2012-01-21
> **fabricator4 said:**
> I certainly don't recommend it for an _only_ machine.

Hello fabricator4 and all

I agree certainly, but just one idea...

How useful to the community is testing on an installation that boots from an external hard drive, or from a live USB stick with persistent storage?

Then the OP could boot into the removable storage to try and report on 12.04 but revert to a stable system for work.

---

### Post by fabricator4 on 2012-01-21
> **keithpeter said:**
> 
Then the OP could boot into the removable storage to try and report on 12.04 but revert to a stable system for work.

Yes, certainly.  I guess my post was assuming that the OP would be replacing their only boot partition with 12.04.  Having an external drive set up would work well, however if it's using USB it will by necessity be much slower.  I can certainly recommend having a testing partition on the hard drive however.  My testing machine actually has three boot partitions and one massive /home partition.  I have several 'buntu flavours on it testing whichever I need at the time.  It's interesting because it's possible compare results between release flavours if necessary.  At the moment I have 12.04 ubuntu, 12.40 Lubuntu, and 11.10 Ubuntu for comparison.

One of the testing methods I've played with is using an 8GB USB thumb drive and doing a full install on it.  This has the advantage that it's a real full install that can be used on any machine at all, but it does run quite slowly.  If you want to be able to boot it on any machine you need to make sure that grub2 gets installed to the thumb drive, but apart from that I recommend updating the grub on the main hard drive on the machine so that it can control booting off the thumb drive.  You can do it both ways of course.

Chris

---

### Post by Baldrick_NZ on 2012-01-22
For what it's worth, I have installed 12.04 Alpha 1 onto an 8g flashdrive (from USB iso, as I would have if I were installing on a PC HDD), and have found it about 95% stable so far.

It's far better than 10.04 installed the same way. Doesn't hang or take ages to load apps.

I can perform multiple tasks at the same time without it missing a beat. The only thing it doesn't respond too well atm is changing compiz settings - resulting in a complete reboot after each setting change. Not good. 

The OS took about 4g, which leaves 4g for pretty much anything I need it for. Music, pics, vids, docs, all play well.

Being installed on USB, it's a much slower boot, but if pretty snappy once booted.

What I'm leading to is, maybe, whilst waiting for the final stable version, install to a flash drive and boot directly from that. That way you can see what it does, save files, play music, browse the web, etc... without installing to your HDD until you're ready.

---

### Post by pajn on 2012-01-22
I do use 12.04 as my main (and only) OS.
So far it haven't been so much of a hassle, some bugs of course. Sometimes u have to use Unity 2D and sometimes Unity 3D is fine.

However I wouldn't recommend it to anyone that asks because you never know what happens. But if you are confident that you can fix most things I can't disrecommend it anyways.

Do whatever you want, worst thing that can happen is that you will have to reinstall but I don't think it will be necessary.

---

### Post by philinux on 2012-01-22
For a home user the bottom line with all this is that it's your machine to do with as you see fit.

As long as your personal data is backed up effectively you've nothing to loose. If it gets messed up reinstall.

Me, I have 2 internal hard drives. One has 11.10 the other 12.04. Thus I have no problem at all. I just chroot from 11.10 to fix it if it goes belly up.

---

### Post by PaulW2U on 2012-01-22
> **tom_hanks said:**
> As I understand it, this release won’t have any new features  beyond standard package updates, so I don’t see why it would be as  unstable as a short-term release, even during development.

It's some of those updates, during the alpha period especially, that can and do cause problems. Most of the time you'll be fine but take care if you're prompted to _remove_ anything.

---

### Post by ronacc on 2012-01-22
there are reasons other than the introduction of completely new packages that things can get unstable during the development cycle , it is normal and expected . For me this dev cycle so far has been quite tame , not so for some others . Take a few minutes and check  the threads in this forum and consider are you willing to risk that you may have a system that may refuse to boot to desktop at any time , not just into Ubuntu but maybe not Windows either ( I am assuming you would be dual booting using grub ). If you feel you can handle any glitches that come along and remember to keep a backup of important work on a cd/dvd or usb stick , join the fun .

---

### Post by collisionystm on 2012-01-22
Im running 12.04

Software Center is broken

Kernel Crashes randomly every few minutes

other than that, GOOD

lol

---

### Post by collisionystm on 2012-01-22
> **collisionystm said:**
> Im running 12.04

Software Center is broken

Kernel Crashes randomly every few minutes

other than that, GOOD

lol

Correction..

Software center is fixed now

---

### Post by shuttleworthwannabe on 2012-01-22
Software Centre and Kernel Crashes for me too--but that was like 3 days ago; i have since moved back to 11.10. Will catch-up proly closer to RC.

---

### Post by kevpan815 on 2012-01-22
My Reply to your Question is: I am getting Linux Kernel Panics on my Dell Inspiron 1012 Netbook! My only workaround is to use the Guest Account at the moment! Hope that answers your question! Better wait until Beta 1 if you are not experienced in testing Pre-Release Software. Just fyi.

---

### Post by bcschmerker on 2012-01-30
> **kevpan815 said:**
> My Reply to your Question is: I am getting Linux Kernel Panics on my Dell Inspiron 1012 Netbook! My only workaround is to use the Guest Account at the moment! Hope that answers your question! Better wait until Beta 1 if you are not experienced in testing Pre-Release Software. Just fyi.**Smart move!** ;-) I'm currently biding my time getting parts for a clean install of 12.04, while [Advance Micro Devices®](http://www.amd.com/) and [nVIDIA®](http://www.nvidia.com/) catch up with the [LinUX Kernel Project](http://www.kernel.org/) on support of their respective GPU's through at least Kernel 3.2.12; my hybrid Everex® (which started life as a stock TC2502 running a now-orphaned distro based on XUbuntu® 7.10 Gutsy) will handle up to four SATA hard drives in its case (the current Gigabyte® GA-MA78GM-S2HP packs five SATA ports plus one PATA header).

---

### Post by friTTe81 on 2012-02-01
Im running a clean install as of today, no big problems really..some popups and stuff like that.

Recently my computer just powered off but that is probably some hardware glitch hehe.

Looking forward to rolling up to Alpha 2 and Beta and Final ;)

---

### Post by kiwited on 2012-02-01
I have used 12.04 on my trial install partition literally since day one of alpha one. It was a trouble-free upgrade from 11.10 and I have not had a crash. I do not use the update manager, instead using the terminal. There have been very few error messages on startup. I have installed Gnome which I am trying as an alternative to my everyday install of 11.10 which has Unity. (Our office machine (11.10) now has Gnome Classic after very loud complaints from it's user, who couldn't get to grips with Unity). The splash screens still say 11.10 which makes me hope that something special is being planned for this part of the system.
No complaints from me!
Theo

---

### Post by OGpmpdog on 2012-02-01
Hi,

For those with older Nvidia cards, PP is a horrible mess...kernels 3.2.11 & 3.2.12 have CURSED my bulletproof T61/Quadro.

I had to reinstall the original A1 build (dated 12-1-11), and use the portis25 & Xorg edge PPAs, to bypass the problems I previously had with Nvidia drivers. (Thanks Paul in London!!)

Performed a massive update last night, and things seem OK...However, gtk is broken, making it hard to read the panels.

Also, with kernel 3.2.12, it seems that Unity runs snappier than Gnome 3/Cinnamon.

My answer: Precise is boringly stable on newer hardware, and true Alpha software on older hardware...

On a side note, can someone provide quick info on installing kernel 3.3 RC2 tar file?  The deb files just hang on my system.

Peace.

---

### Post by deonis on 2012-02-01
I am using it now on my netbook ... works like a charm ... :)

---

### Post by Salane on 2012-02-01
There is a bug in fglrx right now. Xvideo causes xserver to crash.

[https://bugs.launchpad.net/bugs/923421](https://bugs.launchpad.net/bugs/923421)

---

### Post by Krabby.Linux on 2012-02-10
How is the development of Precise Pangolin at the moment? Is it still very unstable and are there Nvidia Graphic Cards Driver out? I remember the Last time where i couldnt install any Graphics Drivers....

---

### Post by dino99 on 2012-02-10
did you read the other threads here before opening yours ? you might get the answer i beleive :)

---

### Post by prusswan on 2012-02-10
Unity aside, it seems no more or less stable compared to 10.10 or 11.04 at similar stages of development. Most of the problems I personally encountered were not introduced in 12.04 anyway, except for the alsa no sound issue.

---

### Post by Krabby.Linux on 2012-02-10
I did read some announcements from PP. Now i am scared ;-).

Seems that there are lots of Nvidia Problems ....

---

### Post by varunpr97 on 2012-02-10
try a live or a virtualbox session...  I recommend you dont this on a production machiene... i generally upgrade a week before the final release as after the release the servers are too busy to updating is a bit slow.... Switch to pangolin after the beta release as thts the tim when the dust settles a bit....

---

### Post by philinux on 2012-02-10
Threads Merged.

---

### Post by jorpoveda on 2012-02-10
Are there any new issues on 12.04 LTS, and I mean something to be scare of? I just hope that with the new 12.04 the touchpad of my samsung series 3 laptop works better. It is real hard to properly configure the right click on a modern one button touchpad.

---

### Post by SemiExpert on 2012-02-10
Alpha 2 was very stable - no problems that I have noticed.  However, I've stopped testing 12.04 due to some of the controversial new changes to Unity, namely the decision to delete Dodge Windows Feature, something that apparently can't be discussed on this forum.  I'm done with Unity, at least for the moment.

---

### Post by cariboo on 2012-02-10
> **jorpoveda said:**
> Are there any new issues on 12.04 LTS, and I mean something to be scare of? I just hope that with the new 12.04 the touchpad of my samsung series 3 laptop works better. It is real hard to properly configure the right click on a modern one button touchpad.

There is a problem on i386+Nvidia systems, a work around has been created for the time being, but the developers are working with Nvidia developers to solve the problem:

> On Thu, Feb 09, 2012 at 09:15:29AM -0600, Kate Stewart wrote:
> An issue has been noticed due to interaction between a recent libc
> upgrade and the nvidia graphics driver.   If you have nvidia hardware,
> please avoid upgrading until this has been resolved. Investigation is
> ongoing.
>
> Details will be found and tracked in: 
> [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/929384](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/929384)
>
> Thanks,  Kate
Resolved.

Worked around with patches to libc.  I've tested the workaround locally
and several people have confirmed it solves the issue on their own HW.

We will be working with NVIDIA for a proper fix to their driver for the
root issue.

Bryce


---

### Post by dnewkirk on 2012-02-10
> **SemiExpert said:**
> Alpha 2 was very stable - no problems that I have noticed.  However, I've stopped testing 12.04 due to some of the controversial new changes to Unity, namely the decision to delete Dodge Windows Feature, something that apparently can't be discussed on this forum.  I'm done with Unity, at least for the moment.

There are changes that happen in any distro that not everyone agrees with, but there are many distros, so there is plenty of opportunity to find one that suits one's needs. Discussing displeasure with a change isn't bad, but can be counter-productive particularly as (in this instance) it isn't going to change. Mark made that clear. Sorry it isn't to your liking, but perhaps helping to debug things anyway from time to time is still possible. At the end of the day, sometimes we can help make a release the best it can be for others, even if it isn't everything we ever dreamed of.

---

### Post by effenberg0x0 on 2012-02-10
IMHO, it's not stable. A couple hours ago a simple problem was enough to bork PCs seriously, in a way an unprepared user could never fix. It can look stable for one hour, one day, one week and then it breaks in an update. We can't really predict that. 

So, if stability is a concern, one shouldn't install PP Alpha. At least wait for a more advanced release or the final one. 

If the goal is testing, stability wouldn't be a concern.

Regards,
Effenberg

---

### Post by jorpoveda on 2012-02-11
> **cariboo907 said:**
> There is a problem on i386+Nvidia systems, a work around has been created for the time being, but the developers are working with Nvidia developers to solve the problem:

Well in that case I wont have problems with the laptop I am going to buy since it is X86-64 and an Intel based graphic card.

---

### Post by screaminj3sus on 2012-02-11
No matter how stable it is "now" alpha releases can and will break horribly.

---

### Post by wolfen69 on 2012-02-12
> **jorpoveda said:**
> Well in that case I wont have problems with the laptop I am going to buy since it is X86-64 and an Intel based graphic card.

Just don't expect it to be problem free. The purpose for using 12.04 at this point is for testing and bug reporting.

---

### Post by Elfy on 2012-02-12
> **wolfen69 said:**
> Just don't expect it to be problem free. The purpose for using 12.04 at this point is for testing and bug reporting.

Easily forgotten until it's too late :)

---

### Post by bcschmerker on 2012-03-13
> **cariboo907 said:**
> There is a problem on i386+Nvidia systems, a work around has been created for the time being, but the developers are working with Nvidia developers to solve the problem....Thanks for the heads up on the regression.  I am beginning the process of preparing to rebuild my hybrid Everex® for 12.04.0-LTS when it is released to market; my first priority is a quartet of SATA hard drives, but I am also considering a new Asus® mobo for Micro-ATX:  the P8Z68-M PRO with an Intel® Core&#8482; i7&#8482; (LPGA 1155), due to known issues with previous real-time desktop kernels on AMD® hardware.  My upgrade plans are for an Advance Micro Devices® Radeon&#8482; HD&#8482; 6000 Series-based PCI-Express x16 VDA, which shouldn't be affected by the libc6-induced regression in the nVIDIA® drivers and settings app(s); I would thus have the option of custom-compiling a modified Kernel 3.2 with the i7's&#8482; internal graphics subsystem running as a real-time-preemptable multimedia coprocessor.

Do keep us up to date on the progress of Kernel 3.2-n-realtime, which I understand uses different preemption code from Kernel 2.6.31-11-rt; I'm shooting for an audio/video live-streaming set-up in LinUX to back up my existing Windows box, viz., an Asus® CM1630-06 with EAH6850DC video and XONAR® Essence&#8482; STX audio plus 750W Antec® PSU.

---

### Post by dcstar on 2012-03-13
The only real answer to this question is:

"Nowhere near as stable as it will probably be about **one month after official release**, when anyone with any sense will finally start to install it on production systems".

---

### Post by OGpmpdog on 2012-03-13
Hi all,

Milestone: I was finally able to do clean install to my T61 laptop, from flash drive.  Also, Nvidia graphics card was auto recognized and latest drivers were automatically downloaded - AWESOME.

Also, PAE kernel is recognized, even though I only have 2GB of RAM:D

As far as older machines, PP is not quite stable.

1)Gnome3shell search still doesnt work - and still crashes system.
2)Suspend doesnt work after closing laptop lid. a WTF moment.
3)System sometimes inexplicably reboots to login screen...this has happened several times since kernel 3.2.18 was downloaded - BIG frustration.
4)Sloppy graphics and themes can make it hard to read displays.

Peace.

---

### Post by Nordicruler on 2012-03-13
Is it time to upgrade to 12.04? Is it worth that?

---

### Post by PaulW2U on 2012-03-13
> **Nordicruler said:**
> Is it time to upgrade to 12.04? Is it worth that?

It may well depend on your hardware. Some users like myself are perfectly happy with their installation of 12.04.

I'm running Kubuntu and Ubuntu (Gnome Shell) with very few problems. Unity has several bugs that I'm about to report that for me makes it unusable over long periods with multiple applications open. Don't expect a stable and bug-free release just yet. ;)

---

### Post by Nordicruler on 2012-03-13
I dont expect it to be perfect just yet :) 
I have a laptop: emachines e732 
Intel core i3 4gb ram Intel hd graphics

---

### Post by emeraldgirl08 on 2012-03-13
I'm on Spring Break and very tempted to take the daily build out for a run :D

I'm wondering if anyone has tried it out on a ThinkPad R/T60 series w/ATI graphics? If not then I'll download and report back with some thoughts once I get it going :cool:

**UPDATE:**

So far downloaded and burned to DVD. It appeared to work fine then froze. I gave it a couple of minutes and nothing happened. I was able to move the cursor around the screen but could not interact with anything on the screen. I will give it a try again later.

---

### Post by RememberWhenItRained on 2012-03-13
running 12.04 on a Dell Innspiron 1440 500GB HDD, 4GB RAM, intel Pentium dual core.

Counted about 10 crashes in close to two weeks. GNOME shell seems fine, Unity is pretty buggy.

---

### Post by Peripheral Visionary on 2012-03-13
**X**ubuntu has been solid for a day - just dared to try it out yesterday. The installer balked on the first attempt, but went ahead on the second. Once installed and updated, it has been as solid for me as 10.04 was. Only faster and prettier. But to be fair, I've only had it on for 24 hours.

One thing I'm delighted with is that PulseAudio doesn't get in my way. The previous owner had Xubuntu Lucid on it and warned me to avoid (as in - completely remove if installed) PulseAudio in future versions of Xubu. The new Xubuntu 12.04 works wonderfully out of the box - even with PulseAudio installed. :mad:

I was told, as a newcomer to Linux, to stay *one release behind the current* one for better stability. Far be it from a newcomer to install a Beta! But so far it has been flawless and I'm enjoying it - and learning a thing or two as well.

---

### Post by jerrylamos on 2012-03-13
Been installing Beta level O.K.  Still getting potfuls of crashes some reported already by 100 or 200 people.

No success installing proprietery ATI and Broadcom drivers.

Jerry

---

### Post by RememberWhenItRained on 2012-03-13
> **jerrylamos said:**
> Been installing Beta level O.K.  Still getting potfuls of crashes some reported already by 100 or 200 people.

No success installing proprietery ATI and Broadcom drivers.

Jerry

strange, i had no problem with broadcom drivers

---

### Post by x-shaney-x on 2012-03-13
Not really noticed much in the way of crashes but do have odd problems here and there.
I'm seeing a fair few mentions of problems with HUD and keyboard shortcuts, though I haven't noticed any such issues.

Biggest problem (for me) is chromium browser, takes several attempts to start and find often that pages appear to be loading and everything and the window title changes but the page content doesn't change.
Example:  I am on ubuntuforums, I click on my gmail bookmark and the window title and tab title changes but the page is still showing ubuntforums.

Totem crashes with some files but fine with others.

Touchpad "disable touchpad while typing" does not appear to be working at all.

---

### Post by kaldor on 2012-03-13
Apart from some minor issues (and some Unity instabilities), 12.04 is more stable than 11.10 and 11.04 were for me. I've been using 12.04 as my primary OS for almost a week without any notable hassles. That said, I wouldn't recommend using it for important tasks.

---

### Post by bcschmerker on 2012-03-14
> **jerrylamos said:**
> Been installing Beta level O.K.  Still getting potfuls of crashes some reported already by 100 or 200 people.

No success installing proprietery ATI and Broadcom drivers.

JerryThanks for the heads up on the FGLRX situation.  My hybrid Everex® (Gigabyte® GA-MA78GM-S2HP mobo, Advance Micro Devices® Athlon X2 5600+) has run just fine with the X.org open-source ATi, Radeon and Radeon HD on its planar Radeon® HD 3200, except with unusual display units (such as televisions) that pack undersize LCDs for the scan rates, on 10.04.4-LTS with the Kernel 3.0 upgrade (package: linux-image-generic-pae-lts-backport-oneiric); I expect that also to be the case upon installation of 12.04.0-LTS, at least with Kernel 3.2 (package: linux-image-generic-pae) and hopefully with the new-generation real-time-preemptable desktop kernel (package: linux-image-realtime).

---

### Post by hawthornso23 on 2012-03-14
Stability isn't my main concern. I know that is something that if not perfect initially will quickly be fixed. My main concern is worry about what features I'm going to lose if I update. 

I can remember when upgrades used to be about the joy of discovering cool new features and functionality. Recent upgrades have been mostly about the pain of losing features and functionality and the struggle to get them back. What I mostly want to know before I decide whether or not to upgrade is what features have been broken or removed this time. I need to decide whether those are things I can live without - look into how much trouble it will be to get them back if I decide I don't want to lose them - and so on.

---

### Post by cariboo on 2012-03-14
> **hawthornso23 said:**
> Stability isn't my main concern. I know that is something that if not perfect initially will quickly be fixed. My main concern is worry about what features I'm going to lose if I update. 

I can remember when upgrades used to be about the joy of discovering cool new features and functionality. Recent upgrades have been mostly about the pain of losing features and functionality and the struggle to get them back. What I mostly want to know before I decide whether or not to upgrade is what features have been broken or removed this time. I need to decide whether those are things I can live without - look into how much trouble it will be to get them back if I decide I don't want to lose them - and so on.

Gnome has removed most of the customization options that were available using GTK-2. What features are you looking for?

---

### Post by screaminj3sus on 2012-03-15
I'm no longer getting random crash reports popping up, and the system seems quite "stable", but there's still a few obvious bugs around (mainly caused by the gtk3 updates. The gtk 3.3.18 update introduced some really annoying behaviour with touchpads, menus dont highlight when I mouse over them, I cant grab the overlay scrollbar etc..)

---

### Post by sameer.india on 2012-03-17
Gnome-shell freezes randomly

---

### Post by fabricator4 on 2012-03-17
> **sameer.india said:**
> Gnome-shell freezes randomly

I'm not seeing that, but I am getting segfault crash reports for Nautilus and Plymouth  (!).

This has been going on for some time now.

Chris

---

### Post by jppr on 2012-03-18
I'm not interested in how stable 12.04 is, I'm interested in how fast it is = )

---

### Post by VinDSL on 2012-03-18
> **jppr said:**
> I'm not interested in how stable 12.04 is, I'm interested in how fast it is = )
Well... it's rather slow and lumbering on this machine (see sig).

Takes (like) 2 minutes to boot.  Banshee is tortuously slow.  Flash games are choppy, blah, blah, blah.

If I was running a modern machine, say an Intel i9 w/16GB RAM & SSD, I'm sure it would be a whole different experience.

Really, the fastest OS I've ever run on this PC is Puppy Linux.  LoL!

If you're interested strictly in speed, I doubt that Ubu 12.04, in its current state, is going to impress you.

I have Ubu 10.10 installed on another partition (dual boot) and it runs circles around 12.04!  ;)

---

### Post by Gregory Lee on 2012-03-18
I'm getting about one crash per day.  It seems very snappy, but it should, since I bought it a nice new quad core computer to work on. I think my desktop (using Gnome 3) is starting to look very stylish.

---

### Post by Luffield on 2012-03-18
What are the problems nvidia users are experiencing? On my computer (with a 9500GT card) it works reasonably okay, except very long log-in an log-out times, and total freezes when I try to use Virtualbox. Other than these issues everything is great. Are other people having more serious issues with nvidia cards on Precise?

---

### Post by jerrylamos on 2012-03-18
Stable?? 12.04 couldn't print a 16 page document.  Fired up Lucid Lynx 10.04, always have a stable partition!, and printed right off.

Lucid apparent feel a lot faster handling the document with Open Office than Pangolin with Libre Office.  No measurements tho.

Still running Pangolin mostly looking for and finding bugs even though the "old stuff" is apparently faster.

Enjoy.

Jerry

---

### Post by sameer.india on 2012-03-19
> **fabricator4 said:**
> I'm not seeing that, but I am getting segfault crash reports for Nautilus and Plymouth  (!).

This has been going on for some time now.

Chris

So is it just me?
it worked fine before the upgrade.

---

### Post by kaldor on 2012-03-19
> **Luffield said:**
> What are the problems nvidia users are experiencing? On my computer (with a 9500GT card) it works reasonably okay, except very long log-in an log-out times, and total freezes when I try to use Virtualbox. Other than these issues everything is great. Are other people having more serious issues with nvidia cards on Precise?

I am running the open source Nouveau driver without any graphical problems apart from known Plymouth and Lightdm corruption (not NVIDIA specific). The only issue I'm having is overheating, though I think that might just be specific to my 8400m according to a few searches I've made.

---

### Post by Luffield on 2012-03-19
Thanks kaldor. I'll try Nouveau.

---

### Post by eeBus on 2012-03-21
No sameer.india I get hangs too, but I don't know how to find out the cause or where to look. Can't even get the log file viewer to work. I'm on PP Beta 1 and have to resort to holding the power button until the system powers down. Hangs about twice a day.

---

### Post by SemiExpert on 2012-03-21
Gnome-panel caused 100% utilization of a single core, not just in Gnome Classic mode, but in Unity.  Weird.  The bottom application bar in Gnome Classic crashed repeatedly as well.  Solution?  I removed gnome-panel and the CPU utilization issue disappeared.  One crash of Software Center, but that's apparently a known issue.  Other than that, 12.04 seems stable.  I don't plan on reinstalling gnome-panel any time soon.

---

### Post by jerrylamos on 2012-03-22
Stable?? Just look at the posts here in this forum and anticipate how you'd be with the troubles they are reporting.

Jerry

---

### Post by Guardian978 on 2012-03-22
Given the rate of change in the repos. I would say that it is pretty unstable. My user experience has been generally pretty good with the odd breakage due to package updates. But (fingers crossed) this has not led me to a totally borked system yet.

However, this is definitely not in a production state just yet. But getting close.

---

### Post by dharmavir on 2012-03-24
I am using Ubuntu 12.04 beta-1 (both Desktop and Server but now more on server) build since more than 2 weeks now and have been updating frequently using apt-get update/upgrade command and it works just fine. I did not had much trouble except a time when GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text" did not work as expected, which actually worked once and for another vm-node it did not but once I changed that to  GRUB_CMDLINE_LINUX_DEFAULT="text" it worked well. 

I have also installed optional xfce4 and supporting packages using my own necessity and selection and found no problem so far.

So I would say it can be used for day to day operations and I could not find anything show stopper.

P.S: I am not on a more of a GUI user side and actually only need commandline tools, so your experience may vary.

Regards,
Dharmavirsinh Jhala

---

### Post by PhilFox on 2012-04-23
i've got it running on 3 machines, all using Gnome Classic (forget Unity it is still too hungry).  Two work on Gnome Classic with no crashes but a few error reports - but one has a persistent crash of gnome-panel which I cannot get fixed yet.

---

### Post by EgoGratis on 2012-04-23
[LEFT]> forget Unity it is still too hungry

Not true. It works fast here and i don't notice problems with it that would cause my system to slow down.
[/LEFT]

---

### Post by Download Descendent on 2012-04-23
Using the daily build from a few nights ago, and in Classic.

As above, the only problem I've noticed is the occasional error reports but no crashes.

---

### Post by wacky_sung on 2012-04-23
Still getting lot of crashes & errors.:frown:

---

### Post by jerrylamos on 2012-04-23
> **EgoGratis said:**
> [LEFT]

Not true. It works fast here and i don't notice problems with it that would cause my system to slow down.
[/LEFT]
Check "system monitor" and notice how much % processor cycles are being used by Compiz, even when you're in full screen applications and nothing Compiz is doing is even visible.  Classic Microsoft solution is to require ever faster processors to keep up with the "eye candy" overhead.  Another path is "Raspberry Pi" minimalist hardware to expand market penetration.   

All about choices.  On my processors which are fast enough I use Unity-2D (I don't like -3D huge hieroglyphic icons fuzzy out of focus foggy windows) and this Thinkpad is quite responsive with lubuntu (or linux mint LXDE) - just for fun right now, I'm using Lucid Lynx on it because Precise doesn't support its Aironet wireless.

Choices.  Have fun...  Jerry

---

### Post by Frogs Hair on 2012-04-23
Both Unities, Classic, and the Gnome Shell are running fine with a Nvidia 8 series video card and the current driver. The major updates stopped last Thursday.

---

### Post by vasa1 on 2012-04-23
> **Frogs Hair said:**
> Both Unities, Classic, and the Gnome Shell are running fine with a Nvidia 8 series video card and the current driver. The major updates stopped last Thursday.
I've just tried the 3D flavor of Unity and it's going pretty well. It's been about 8 hours of installing and configuring various things and I must say I'm impressed :)

---

### Post by Mathor on 2012-04-23
> **jerrylamos said:**
> Check "system monitor" and notice how much % processor cycles are being used by Compiz, even when you're in full screen applications and nothing Compiz is doing is even visible.  Classic Microsoft solution is to require ever faster processors to keep up with the "eye candy" overhead.  Another path is "Raspberry Pi" minimalist hardware to expand market penetration.   

All about choices.  On my processors which are fast enough I use Unity-2D (I don't like -3D huge hieroglyphic icons fuzzy out of focus foggy windows) and this Thinkpad is quite responsive with lubuntu (or linux mint LXDE) - just for fun right now, I'm using Lucid Lynx on it because Precise doesn't support its Aironet wireless.

Choices.  Have fun...  Jerry

well certainly you don't have the system requirements to run unity or gnome-shell or any high-performing OS, but how can you call that a bug?  I have a quad core processor and compiz uses about 10-15 percent. I've had mac for the past 10 years, and recently my laptop died on me, so I am forced to buy a new laptop. New laptops have fast processors, and I think you will find a lot of people who are in the same boat. As it gets cheaper to make faster processors, it doesn't really make sense not to upgrade your hardware. Even with LXDE, your hardware will not last forever.

---

### Post by EgoGratis on 2012-04-23
> Check "system monitor" and notice how much % processor cycles are being  used by Compiz, even when you're in full screen applications and nothing  Compiz is doing is even visible.Yes i do monitor this occasionally. When in idle CPU consumptions for Compiz is very low and when doing something that is "Compiz related" it goes up but it does not affect my work or make Unity work slow. Probably on slower hardware user could see the difference but i guess that is why Unity 2D is for? I guess on average hardware Unity 3D should work quite good in Ubuntu 12.04 but if it does not there still is Unity 2D option yes or if somebody prefers Unity 2D over Unity 3D it has that option too.

---

### Post by treesurf on 2012-04-23
I found Unity 3D to really bog down my laptop.  When running multiple programs some of the windows were becoming unresponsive.  I have not had this problem with previous versions of Unity.  I've got a Pentium Dual-core 2.0ghz, with 2GB of RAM.  This became so annoying that I upgraded to 4GB of RAM and now everything runs smoothly.  It was a cheap fix for me, but a good reminder that Unity 3D is really designed to run on modern hardware.  That's why they include 2D as an alternative.

As for the original question: aside from a very few minor bugs, this release has been totally stable for me.  I'd actually have to say that from beta it's been more stable than previous "stable" releases.

---

### Post by jerrylamos on 2012-04-23
> **treesurf said:**
> I found Unity 3D to really bog down my laptop.  When running multiple programs some of the windows were becoming unresponsive.  I have not had this problem with previous versions of Unity.  I've got a Pentium Dual-core 2.0ghz, with 2GB of RAM.  This became so annoying that I upgraded to 4GB of RAM and now everything runs smoothly.  It was a cheap fix for me, but a good reminder that Unity 3D is really designed to run on modern hardware.  That's why they include 2D as an alternative.
That's exactly the desired direction of ubuntu development, buy more hardware to keep up with more overhead.  Just like Microsoft.

But with linux you do have more choices to get the linux version that fits your hardware without a big software budget.  I do run lubuntu on the systems with less memory (regression - precise doesn't install on Thinkpad R31, bugs written).

Have fun exploring.

Jerry

---

### Post by Gyokuro on 2012-04-23
Hi,

using the daily builds 12.04 runs stable on my test laptop.
CPU: i5, 8GB RAM, Intel HD3000 - dual monitor setup - I'm really surprised how well Unity works now - Thanks to all for who helped to get a stable base!!!

---

### Post by BigSilly on 2012-04-23
I've recently been running Ubuntu 12.04 with Unity 3D (spec below), and have found it to be not really as quick as the last release. 11.10 was very speedy on my system. I hope 12.04 gets there, but at the moment, for me anyway, after a promising start I had some performance issues. Personally I do feel Compiz is very demanding. Noticeably, when installing Gnome Shell and using that, the problems are not as pronounced. I have no doubt that the devs will give us another great release though.

> **jerrylamos said:**
> That's exactly the desired direction of ubuntu development, buy more hardware to keep up with more overhead.  Just like Microsoft.

I don't really honestly feel that Ubuntu is pushing for its users to go and buy new hardware. Rather it's meeting what is nowadays a fairly common minimum spec. If you have lower specs there are great lightweight Ubuntu versions available. Again personally, if I have the hardware why shouldn't I use something like Unity, Gnome Shell or KDE?

---

### Post by Mathor on 2012-04-23
> **jerrylamos said:**
> That's exactly the desired direction of ubuntu development, buy more hardware to keep up with more overhead.  Just like Microsoft.

But with linux you do have more choices to get the linux version that fits your hardware without a big software budget.  I do run lubuntu on the systems with less memory (regression - precise doesn't install on Thinkpad R31, bugs written).

Have fun exploring.

Jerry

Yeah, but whether it's conservative on memory or not (though I don't feel that it is, as my system isn't noticeably slower than XFCE or LXDE and the differences are minute), that doesn't make it unstable.

I really love XFCE so I appreciate your choices and will probably switch to one of them when this testing cycle is over, but Unity is certainly stable, and it's much much faster than 11.10. 

I might also add that Unity 2D is very laggy and slow for me, so most likely your difference of opinion is in testing Unity 2D on old hardware vs Unity 3d on new hardware, so it's sort of an unfair comparison. Apples and Oranges.

---

