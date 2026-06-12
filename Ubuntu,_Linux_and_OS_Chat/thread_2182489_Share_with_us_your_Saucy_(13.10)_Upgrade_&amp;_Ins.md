---
title: "Share with us your Saucy (13.10) Upgrade &amp; Installation Experiences"
date: 2013-10-21
forum: Ubuntu, Linux and OS Chat
---

### Post by cariboo on 2013-10-21
Please tell us about your experience upgrading, or doing a fresh install of Raring RIngtail

Keep in mind that this thread is only for your experience, if you are having problems, please create a thread in the support forums.

Poll and thread for the previous release:

[Raring Installation & Upgrade Experiences]("http://ubuntuforums.org/showthread.php?t=2139055")

---

### Post by craig10x on 2013-10-21
Worked GREAT...used the option to upgrade on iso installer...2nd experience with that and both times results identical!  Everything transferred over perfectly except for Chrome, MS Core Fonts, libdvdcss and Oracle Java...so just had to add those back...all DATA transferred perfectly and most system settings too!  Also, all PERSONAL settings as well...

Really superb experience...plan on using it going forward to "roll" into each new ubuntu version...saves a lot of extra work and time after the install...;)

---

### Post by gerry-liebling on 2013-10-21
Big problems. Upgrade seemed to go smootly, but now get big black X instead of cursor arrow, and it has no effect.  Windows do not have min, max, close buttons.  Menu pulldowns don't work.

---

### Post by verahsa2 on 2013-10-22
Well... This was somewhat interesting, to say the least, not to mention 4 days and ~22 hours of "work" figuring out everything that I could that was going on. I have been using some form of Ubuntu since 10.02 when I first installed it on a laptop due to the fact that it behaved *much* quicker for a note-taking system for school than windows ever did (notably in boot and shutdown times, as well as power consumption). I am a gamer, so I do dual-boot, regardless, but it is what it is.

I am not a linux guru, but neither am I a neophyte. I've been dual booting Linux and Windows since 1996 (back then dual booting for me consisted of swapping out which drive was actually connected to the master bus of the IDE channels), redhat back then, on to OpenSUSE, into Gentoo for a while, and into Ubuntu 7.04. I went away from Ubuntu for quite a while around 8.04, and came back with 10.02. I've learned enough that I'm comfortable in a CLI, and sometimes prefer doing things via CLI over GUI. 

So, this last week, I purchased a new laptop. Clevo w350st / Sager NP7352 (in case someone has similar issues and would like some form of assistnace, maybe this will help). 

I had a metric TON of issues getting the installer to even boot all the way. I ended up after lots of research needing to add these three lines to the boot options of the livecd on a usb flash drive (and I have no clue which one resolved, but one of them did). I was getting, essentially, a divide-by-zero kernel panic error during the livecd boot and/or unable to properly recognize a usb 3 port and usb 3 flash drive for installation. Sometimes it would note the nouveau module, sometimes it wouldn't, but this fixed it. *shrug*

```

acpi_osi=Linux
acpi_backlight=vendor
nomodeset

```

Only Then was I able to boot the livecd, either the x86 or amd64 versions. Fine, I booted into live mode, installed 13.10 amd64. I did NOT have to add acpi_osi=Linux, acpi_backlight=vendor or nomodeset after the installation, it booted properly.

The system has an optimus based video card, the nvidia gtx 765m. Fine, i knew I'd be hitting up bumblebee... that was a nightmare, but boils down to the following couple of sections.

```

apt-add-repository ppa:xorg-edgers/ppa
apt-add-repository ppa:bumblebee/stable
apt-get update

```

It is important to note that it did NOT work until later (I will note where), as I obviously haven't installed anything just yet. I also installed gnome 3.8 via the following commands before everything started to work properly, I am not sure if it is related, I was just head-desking over how I couldn't get a handle on the Unity environment so I decided to avoid it, and went back to gnome.

```

add-apt-repository ppa:gnome3-team/gnome3
apt-get update
apt-get install gnome-shell ubuntu-gnome-desktop

```

I selected the gdm instead of the lightdm for the notification support, obviously. Then, reboot, and install bumblebee. 

```

apt-get install bumblebee bumblebee-nvidia

```

It installed as a dependency nvidia-304 and its dependencies. It still didn't work. 

The first 'next-step' was to edit the bumblebee.conf in /etc/bumblebee to reflect the nvidia driver I was using and the second was I found advice to install the latest nvidia driver from xorg edgers, instead of the normally installed versions (nvidia-304 in this case). In bumblebee.conf, the KernelDriver was set to "nvidia-current." I set that line to KernelDriver=nvidia-304. It still didn't work. So, on to the latest nvidia drivers. 

```

apt-get --purge remove nvidia-304 nvidia-settings-304 bumblebee bumblebee-nvidia
apt-get install nvidia-331 nvidia-settings-331 nvidia-persistenced
apt-get install bumblebee bumblebee-nvidia
apt-get update
apt-get upgrade

```

I also of course changed the bumblebee.conf kerneldriver line to nvidia-331 Only *after* the "apt-get upgrade" and a reboot did everything actually behave. I can turn the video card on and off at my leisure, it boots nice and swift, runs the things it needs to just fine, and can turn the video card to power saving mode when I'm simply taking notes, which is one of the reasons I love linux in general so much. Optirun doesn't even remotely complain.

I am still sitting on one last minor issue. I'm hooked up via HDMI to a larger monitor when I'm at home working on this instead of out and about (I do my projects on the laptop rather than deal with moving files around constantly or putting them on the cloud somewhere). When I *am* at home and am hooked up via HDMI, I like to listen to music through the monitor's semi-decent speakers... I now have the strangest problem. 

Fire up youtube (or ANY other audio source / audio-video source) and have the sound settings window open, play the video. It plays at double speed, in sync, no static, just double speed both audio and video. Click on "Speakers - Built-in Audio" and it IMMEDIATELY slows back to normal speed, and audio output changes from HDMI to the built in speakers, video remains on the HDMI connected monitor. Select "HDMI / DisplayPort 3 - Build-in Audio" and again immediately it speeds back up to 2x both audio and video. 

Heck, the "test speakers" section plays double speed over HDMI and single speed when over the built-in speakers. I've yet to figure it out. It's the last thing I've got to deal with. 

I have to say that I'm not impressed with Ubuntu's installation on 'newer' hardware... but then that's been an ongoing problem for Linux in general for the past 16 years that I personally know of and have had to deal with. This was probably the second worst I've had to deal with, ever. (The first being an ATI gentoo build back in, oh, 2004/2005 or so). 

This took, as I said, about 22 actual work-hours to get installed to be stable and make use of my hardware properly. I will say that I was surprised that the Killer-1202 wifi and bluetooth combo was picked up both in livecd and installation with absolutely zero issues and runs like a champ, and really the only issue was (and is) some part of the video subsystem.

I have NOT tried to tinker with the Fingerprint Reader built into this system, so I have no idea if that will / would be difficult to get cooperative. 

Hopefully this helps someone else not have to do quite as much work / searching. If I end up resolving the HDMI issue or getting the fingerprint reader setup, I'll update this post with appropriate information.

---

### Post by Frogs Hair on 2013-10-23
As usual no no installation problems . The only exception of a final release being my first Ubuntu installation via Wubi 9.10 . All Ubuntu installations  have been installed on my home build  Asus Nvidia based mobo with AMD processer , Nvidia graphics card, WD Hard-drive. Kingston memory,  and Sony monitor.

---

### Post by The Cog on 2013-10-23
This post is about Xubuntu, not Ubuntu.

As usual, I did a fresh install of 13.10, not an upgrade. I use manual partitioning so that I can multiboot with the previous release.
Everything went pretty smoothly, but I have seen 3 problems.

First, the volume control applet didn't work. This is a well known problem and the fix is already documented.
[http://ubuntuforums.org/showthread.php?t=2182038&p=12822062#post12822062](http://ubuntuforums.org/showthread.php?t=2182038&p=12822062#post12822062)

Second, I run a script that installs all my favourite software. This repeatedly calls "aptitude -y install $package" and I run it unattended. Well the first time I did this, when it got to installing wine, it decided to remove pretty-much the entire system. By the time I returned from TV and saw what was happening, so much of the system had gone that it wasn't really usable, even trying to reboot gave a message "init: command not found". I have a suspicion that it happened because I didn't do an update/upgrade immediately before installing the new packages, and perhaps something the script wanted to install depended on later versions of something else that hadn't been upgraded. Anyway, after reinstalling, I was careful to update and upgrade before running my installer script again, and it went OK this time. This may not be a specific issue with 13.10, but just a product of my not upgrading before installing new packages. I've modified my script. 

Thirdly, I have had a few instances of getting a black screen when I power on. The PC looks dead - no flashing cursor, optical mouse doesn't light up, and the keyboard lock keys don't toggle the lights. After waiting until I'm sure it's not going to boot, I find that although it looks dead, Ctrl-Alt-SysRq-B causes it to reboot, so there must be some spark of life in there. After a couple of reboots, it boots properly. I replaced the nvidia-319-updates driver with nvidia-319 yesterday and it booted first time this evening. Time will tell if it's fully fixed now.

---

### Post by declanL on 2013-10-23
I had a great install and it recognised my hybrid laptop video card perfectly. Brilliant update!:p

---

### Post by su:bhatta on 2013-10-24
Install Worked like a charm. Used Ubuntu Gnome 13.10 amd64 iso. As ususal had to choose 'nomodeset'. Thats all.

 I installed UbuntuStudio meta's on top. That also worked great.

---

### Post by Jerry_Sanford on 2013-10-24
I upgraded two system yesterday and wouldn't you know it, one success and one failure.  I started the successful upgrade in console mode and other than it taken 2 to 3 hours, it work without a glitch.  On the other hand, the system that failed demonstrated problems at reboot and did not boot or indicated the system drive was not mounted.  The system booted to ROOT and allowed me to fix the system.  I remounted the drive and issued a configure command and the upgrade process resumed. After about 15 minutes the process completed and booted successfully.

---

### Post by iamthedreamer-cp on 2013-10-25
upgrade was a piece of cake. just some minor settings changed which needed fixing, but that's a non issue really

---

### Post by rrnbtter on 2013-10-25
Greetings,
I upgraded my Raring Disk to Saucy Final but used the last Saucy Daily iso. On this one I had to reinstall my non default software which is no big deal. I use separate partitions for boot, root, usr, and home. I only formated the boot and root so I retained all of my settings and my Claws mail came back just like the original. Good experience. In addition I upgraded my Saucy Disk to Trusty by changing the repos. I actually like Trusty so much that I think I will use it as my main distro and keep the Saucy for backup.

---

### Post by craig10x on 2013-10-25
@rrnbtter: yeah, that is what i have been using (the upgrade option from the iso installer) and been getting much the same results as you...and so did a friend of mine that used same...seems to be that method is quite reliable at this point in time...highly recommended! ;)

---

### Post by dr_saaron on 2013-10-25
Well, the upgrade process crashed but on a reboot 13.10 came up though with many messages about connecting to HAL.  Rebooting after removing HAL and reinstalling it went smoothly.  Logging in the first time to each user account gave lots of error messages but unity/gnome-shell/KDE still came up and logging in the second time was smooth.  So I think it's all running OK.

---

### Post by rrnbtter on 2013-10-25
Greetings,
Well, I now have two installs of Trusty.  I copied /var/cache/apt/archives from my Trusty installation over to the Saucy disk that I had upgraded from Raring just to save internet bandwidth. Then I installed the Trusty repos and did the dist-upgrade and now have Trusty on both drives. I don't know what I gain from this unless perhaps a dev update crashes. This seems unlikely since Canonical now supports running dev as a main OS and plus Trusty is an LTS. Just for safety's sake I'm keeping pre-release off line. FYI
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=869825")
@craig10x - Yes, the upgrade process works better but I suggest the anyone planning to run upgrades avoid a single partition install. Also a separate boot partition for a Win/Ubuntu setup works well since I can upgrade and even reinstall without tampering with the boot partition that is home for the Windows MBR. I use boot/400Meg root/7gig usr/15gig and all the rest for /home. I don't have a clue how this would work with the later UEFI chipsets.

---

### Post by eyTkT7Y on 2013-10-26
I had Fedora 19 dual-booting with Windows 8.1 on my uEFI machine. Fedora understood uEFI well enough to at least function. Then I thought I would try Debian. Fail! Debian's support of uEFI is buggy and non-functional. The community had a lot of "work-around" tips. My work-around solution was to try Ubuntu 13.10. Yay!

I'm happy to say that 13.10 handled my uEFI dual-boot with Windows 8.1 with no problem. I did disable the secure boot. But other than that... very nice!

---

### Post by higltypig-e on 2013-10-29
I tried the upgrade,- it failed. couldn't boot up and I eventually found out after some digging that I needed to run Boot Repair to get everything working again. (after reinstalling/ reupgrading, and eventually formatting the partition).

Bit of a crappy experience I have to say, especially as 13.04 was working great. You'da thought the upgrade would have just left settings like Grub alone.

---

### Post by craig10x on 2013-10-29
> **higltypig-e said:**
> I tried the upgrade,- it failed. couldn't boot up and I eventually found out after some digging that I needed to run Boot Repair to get everything working again. (after reinstalling/ reupgrading, and eventually formatting the partition).

Bit of a crappy experience I have to say, especially as 13.04 was working great. You'da thought the upgrade would have just left settings like Grub alone.

Just out of curiousity...which upgrade method did you use?  The software updater option to upgrade or the live iso cd installer's option to upgrade?

The reason i am asking is because i use the option to upgrade on the iso installer...and my experiences have been very good...but i know most use the software updater upgrade method and my impression is that THAT method is very hit and miss...

---

### Post by john_ferrier on 2013-10-30
I tried both upgarde and fresh installation. Both were smooth but I did expereince problems after that. The new version of Unity is buggy. I have rolled back to 13.04 as I think it is more stable.

---

### Post by zteam2 on 2013-10-30
Then I first attempted to upgrade from 13.04, the update-manager crashed.

But after many attempts it worked.

Other than that, this upgrade seems to be working extremly fine.

I have not encountered any errors at all, so far :-)

---

### Post by david98 on 2013-10-30
Since upgrading from 13.04 to 13.10 i am happy to report that i have had no problems except i could not upgrade i had to do a fresh install which is recommended  so am a happy chappy nothing to complain about and i hope it stays that way thank you canonical (ubuntu team another excellent distro)

---

### Post by hunterrjh on 2013-11-28
I installed 13.10 immediately it became available. I have been running Ubuntu for a number of years and find it a great system. However, I had many problems with 13.10. to the extent that I reformatted my computer, and reloaded 13.04, which is again running just fine.

This experience hasn't put me off Ubuntu, but I am reluctant to try 13.10 again, just yet.

---

### Post by d-cosner on 2013-12-01
I just upgraded 13.04 to 13.10 on an Intel desktop for my wife Amanda to use. When I logged on the machine I was presented with the option to upgrade and I thought what the heck might as well go with the current release. So far everything seems in perfect working order and the new release is noticeably faster. The refinements to Unity in 13.10 are nice too. This is the first time I have ever gone with an upgrade like this. Normally I would have went with a clean install but I did not have any disks and I have read a few posts about successful upgrades and thought why not give it a try.

I have not gone through and checked everything yet because Amanda was really wanting on the computer, she destroyed both our laptops.... Amanda is a Windows 7 user but the machine I put a clean install of Windows 7 install on was giving her nothing but grief. Windows kept freezing up constantly and the machine was more than powerful enough to run Windows 7. I figured maybe she would be happy with the latest Ubuntu release rather than the 12.04 install my desktop has because it looks more refined and it is pretty quick.

This is my first look at 13.10 and I like it but I am waiting for 14.04 to upgrade my desktop. I have a lot of data on my machine, 12.04 has been very reliable and I have not had any real issues with it worth mentioning. Everything works and I have the current versions of the apps I use most thanks to ppa repos so I am content to wait for the new LTS to come out in April. Anyway, my upgrade experience was very good and hopefully my wife will be happy running Linux this time around.

---

### Post by craig10x on 2013-12-01
@ d-cosner: using the upgrade option on the live iso is also an excellent way to upgrade...i have used it several times and i find it very reliable...
You can read about my experience with that here:
[http://ubuntuforums.org/showthread.php?t=2181643&highlight=wow+great+upgrade](http://ubuntuforums.org/showthread.php?t=2181643&highlight=wow+great+upgrade)

Glad to hear you had an excellent experience with the update manager way of doing it...sounds like that is also becoming more reliable as well...:D

---

### Post by Bashing-om on 2013-12-01
update manager to 13.10. smooth as silk, not a problem.
Just remember to update the system prior, disable the 3rd party repos and disable the screen saver.

[INDENT][INDENT]piece of cake
[/INDENT][/INDENT]

---

### Post by Copper Bezel on 2013-12-03
I did a straight upgrade on my second machine, and by the time it rebooted into my desktop, it was like nothing had changed. Very pleased with this experience. I took it from 13.04 to 13.10 running Gnome 3.10 without having to so much as reconfigure startup applications - including the ones coming from third-party sources. = )

---

### Post by suhongdoan on 2013-12-03
I upgraded from 13.04 to 13.10 without any major issues. Everything seems to work fine except VMware workstation 9.0.2 failed to compiled, but no problem now since there was an update 9.0.3 came out and fixed it. Sometimes when first login I got an apport error and ask me to send bug report and I did, but it's not a biggie. I get my work done the way I wanted and I'm a happy camper.
shd

---

### Post by craig10x on 2013-12-03
I have been using the upgrade option on the live session iso installer for upgrading to the next version of ubuntu and it has worked really well...however, i am considering doing it using the Update Manager when 14.04 is final released next April....

Two questions:

1) How soon after a final release does it usually pop up on Update Manager?

2) I do have my software sources set to notify me when a new version is available but i was just wondering, in case it doesn't come up automatically in the update manager, what is the terminal command you use to prompt it to come up in update manager? (i am talking about upgrading to each new final release not into the next development version)...

Hope someone can let me know...i want to make a note of it for when i do my next upgrade ;)
Thanks...

---

### Post by deadflowr on 2013-12-03
> **craig10x said:**
> I have been using the upgrade option on the live session iso installer for upgrading to the next version of ubuntu and it has worked really well...however, i am considering doing it using the Update Manager when 14.04 is final released next April....


Out of my own curiosity, how well does the iso upgrader method do with system running multiple desktops?
(ie gnome, or xfce, along with unity)

I know the networky upgrade method upgrades those as well, but not sure how the disk upgrader does.

For the record, I've successfully net-upgraded two from ringtail to salamander, with no errors.
(Well, at least no errors that are apparent yet)

---

### Post by nabilh on 2013-12-06
Well I tried to install 13.10 32bit on my Dell DXP061 (Dimension 9200 C2D), and it was a disaster...
the install wizard will get stuck at installation of module kernel bcmw...

so I resorted to Mint Petra 16 32bit, and its install went flawless...

nothing more frustating to an end-user than failed installs...

though ubuntu installs (12.04, 13.04 and 13.10 amd64s) went fine on a Tablet, the Acer W500, running off fast mem sticks and sdcards...

---

### Post by craig10x on 2013-12-06
@deadflowr: I only run Ubuntu (and don't multi boot with either windows or other linux distros) so not sure how the iso installer upgrade does with multiple systems installed...however, i think it only offers the option if you run only 1 ubuntu...if the option is offered, then it will probably do ok...

---

### Post by deadflowr on 2013-12-06
> **craig10x said:**
> @deadflowr: I only run Ubuntu (and don't multi boot with either windows or other linux distros) so not sure how the iso installer upgrade does with multiple systems installed...however, i think it only offers the option if you run only 1 ubuntu...if the option is offered, then it will probably do ok...

No, I get the iso is meant for a single distro based machine.
I mean how does it handle upgrading systems with multiple desktop environments and window managers?
I know it is built to upgrade the default unity, but what about a system which might also have gnome-shell installed?
Or any number of the other DE and WM out there.

---

### Post by Erik1984 on 2013-12-07
I recently upgraded a VirtualBox VM from Ubuntu 13.04 to 13.10 and it really was a flawless experience. I use the Gnome Classic desktop and I didn't notice any visual difference after rebooting. Had to type uname into the terminal to see that I was using the new kernel. The same VM was also upgraded from Quantal to Raring before without any issues. Granted I don't do that much with that particular VM so there is not so much to break.

---

### Post by cooleagel2 on 2013-12-07
I would like to share 2 items here.

1. I installed Ubuntu 13.10 for my Dad on a Thinkpad(The battery is not work any more), and one day, the power was off when updating with "Software Updater", so the system was shutdown suddenly, and when reboot, the touchpad cannot work, and cannot connect to the internet with wireless either.

So I connected it to the internet with wired cable, then re-started the updating process with a USB mouse, when finished, the issue was fixed.

2. I've encounterred several time that system time just disappeared from the top system bar, and will present itself after reboot - Not fixed yet

---

### Post by mantaboo on 2013-12-13
My setup uses UEFI/GPT. The first install froze while installing grub. I booted into the live desktop and installed from there and it worked flawlessly. Go figure.

---

### Post by Copper Bezel on 2013-12-13
I'm absurdly, ludicrously, and pointlessly happy to be able to boot my Ubuntu laptop with Secure Boot enabled. = D

---

### Post by pascalfares on 2013-12-13
[I]Upgrade - worked flawlessly. on 2 desktops and one server. 

But on the laptop (hp realteck wifi) i lost the connection throw wifi[/I]

---

### Post by Random-penguin on 2013-12-14
I must admit I haven't used or even tried Ubuntu for a few years now. Ever since the move to Pulseaudio and it's conrlict with my M-audio sound card. In other distros with a little tweaking ( mostly removing or disabling Pulseaudio) I could get sounds up and running. But Ubuntu only saw it as a digital device with no analogue.

Any way after a protracted break and the fear of the new nasty desktop environment.... "worse than Gnome 3".... I was having issues with my recent flavour (openSUSE) and took the plunge to give 13.10 a go. WOW!!!! what a revelation!!! I love it. My soundcard (very important for me) is configured correctly out of the box! The Unity desktop.... I love it!!! I think it's so much better thought out than either windows 8.1 or Android. I bet it is amazing to use on a touch screen. In fact there are absolutely no complaints at all and I'm a kde man. My beloved Amarok and k3b both look stunning and work well. I'm convinced firefox is faster than on any other distro or windows install I've ever used.

Oh and no-one is paying me to say this :D

---

### Post by hoopia on 2013-12-28
I recently went from 12.10 to 13.04 to 13.10. I hit a huge problem at 13.04 where after the restart all keyboard and mouse input was unresponsive (I believe this has already been logged as a bug). Luckily I was able to download the 13.10 ISO from a different computer and continue the upgrade that way. After that, I had no problems aside from certain applications that were uninstalled.

---

### Post by d-cosner on 2013-12-30
I have upgraded 6 computers now from 13.04 to 13.10 and all but one have been problem free. The computer I had a problem with was not really an upgrade issue, it had NVidea on-board graphics that the open source drivers just did not work well with... I had an NVidea GT 220 just sitting in a drawer so I installed it in the problem machine and everything works great now. I do not play any graphics demanding games and I prefer to use open source drivers because Plymouth always dispays right using tham. Also, I never seem to have any problems with kernel updates messing up the video drivers.

The only bug I have seen on all of these installs was the redundant restart entry in the menu but that is extremely minor and it only takes all of 3 mouse clicks to fix. All of the computers I have upgraded have been problem free and have been in use for quite a while with the exception of the one I had the problem with. I have been on the computer with the GT 220 since last night and have not encountered any problems so far. I did make some changes in the BIOS for the graphics card because I did get a black screen once with nothing but a cursor but I believe the problem is solved now.

I have done the upgrade from the update manager on all of these computers, they all have different graphics cards and all of them boot quick and are running nice and smooth. In the past when I used proprietary graphics drivers my boot time was no where near as quick and I am happy with the quality of the various open source graphics drivers. In the past I always did a clean install of new releases but Canonical and everyone participating in development have done a fine job of testing the upgrade path. Overall quality of Ubuntu releases has improved by leaps and bounds since Canonical set out on their own developing Unity.   

I am really looking forward to 14.04 and the work I have seen so far looks very good!

---

### Post by EnglishElectricAndy on 2014-01-17
Being a complete newbie, having only used Xubuntu 13.04 since the late summer of 2013 and being far from an 'early adopter', I have been putting off upgrading for as long as possible. In part this was due to a sense of impending doom caused by me following the multiplicity of threads generated by users with various matters arising.

With the impending end of support for 13.04 I took the plunge and I am pleased to be able to report that, apart from a couple of minor glitches, all went reasonably smoothly.

The method I used was to create a bootable USB stick using the UnetBootin utility and clicking the upgrade option, i.e leaving my Home folder untouched and not formatting anything. Lo and behold even my Firefox bookmarks and stored passwords survived intact!:)

---

### Post by roofdog on 2014-01-19
My brothers girl, has a Dell inspiron w/ win7 and 4 gig ram. It was really clogged up and I thought the HDD was bad to. I told her, just to show her something new, that I was going to format the drive and install Ubuntu 12.04 on it, and she said do it. I did and she loves it! Like I knew she would. A couple weeks later the Hdd did crash. I installed a ssd hdd along with Ubuntu 13.10.  The first installation done great! It even fixed the Broadcom issue right off the bat! Wireless was working right away! Then it crashed. Not Ubuntu's fault or installation problem. This was an overheating problem in which a cooling pad fixed. I re-installed 2 times. Now the broadcom issue is an issue again.I could'nt get it to work again. I just gave her a usb wi-fi antenna in which has no problems. I just wonder why the Broadcom worked 1 time and quit. Besides the Broadcom prob everything works great! Hail to the guys that put "sausy" out here!

---

### Post by danny.techify on 2014-02-02
It worked fine but if you want to dual boot you have to do it manually so you have to make the partitions manually on Windows 8. On other computers without Windows 8 it gives you a choice to do itself. But it worked perfectly!

---

### Post by marshall-marca on 2014-03-01
**I did a clean install from downloaded image 64 bit on a 2009 white unibody Macbook. The install process worked flawlessly. Once the install was complete and I was booted into the system I just had to install some updates and a couple of restricted drivers for wireless and the Nvidia graphics card. So far everything is working and system has been stable. I installed this operating system about a week ago. :cool:  **

---

### Post by farrinux on 2014-03-01
I was having problems in 12.04 LTS with Thunderbierd.  So I decided to upgrade to 13.10.  It went smoothly, not accounting for those apps that have not been updated to run on 13.10.  I must say that until recently I did not know how "Bullet Proof" Ubuntu was.  The mobo that was in place when I updated, burnt up about 2 weeks ago.  So  I had to upgrade the hardware from a socket 939 mobo to an FM2+mobo and the graphics from and nvidia 8400 to an nvidia 630.  Fearing I would have to reinstall Ubuntu I flip the switch and much to my surprise Ubuntu 13.10 booted right up with no problems.  Yeahhhhhhhhhh!

---

### Post by vadimkolchev on 2014-03-02
I did a fresh install on my machine, created only three partitions - root, home and swap. Ah, no, the fourth one was a small one for efi. The first attempt failed - the installation was stuck for some reason right after checking requirements with tickboxes for choosing to update during installation and to install some of mp3 codecs and so on. However, after reboot everything went well. On first boot I noticed that keyboard layout indicatior is not working properly - it did not change according to layout, however the layout itself changed. After I did full dist-upgrade the issue was gone and now everything works correctly. This is all so far - didn't experience any trouble during installation and update.

---

### Post by Ubi_one_2014 on 2014-03-09
I installed Ubuntu 13.10 a couple of months ago on a dell studio laptop
with 6Gb mem, I3 processor, and shipped with windows 8

everything workd out of the box
wireless, bluetooth, everything

I am now building my own debian files:cool:
Running even kernel 3.13.6 on it


Ubuntu is great

---

