---
title: "Ubuntu 9.04 Jaunty...stability and performance."
date: 2009-06-04
forum: The Cafe
---

### Post by adam.ec on 2009-06-04
What have Canonical done? I've been using Ubuntu since Hoary and the only problem was the stupid Intel HDA sound (which incidently still hasn't been fixed by the looks and also occurs on almost every distro).

I've been running the stable (keeping face straight) release of Jaunty for three weeks and the problems are mounting up. The only extra I have installed is Bluefish and an attempted Skype install. Strangely, I've had none of the direct problems related to video and boot up with my Intel D945 mainboard.

Applications like Transmission and Pidgin are freezing up and disappearing but still running in the background. File permissions are going crazy on my USB key which I have changed twice since having 'read only' errors. I'm getting big white blocks all over Gimp making it unusable. Evince opens a PDF and shuts down immediately. Firefox keeps turning greyscale and locking me out for 8 minutes at a time.

It's all well and good providing the many solutions but this release should never have been made. Just at a time when MS were screwing up their own products and gave mainstream Linux a chance and we get Ubuntu Jaunty.

Does anybody else have any of the same problems? It's going to take me a week to fill out bug reports for these things. I can't understand why Canonical can't fix the known problems in an update and instead expect all of their users to be able to correct them with 'basic' user skills. I'm fortunate as I run Arch and Slack as well but I'm just trying to picture my 63 year old mother trying to change her video driver.

---

### Post by rookcifer on 2009-06-04
> **adam.ec said:**
> Does anybody else have any of the same problems? 

No.

---

### Post by H2SO_four on 2009-06-04
> **adam.ec said:**
> Does anybody else have any of the same problems? It's going to take me a week to fill out bug reports for these things. I can't understand why Canonical can't fix the known problems in an update and instead expect all of their users to be able to correct them with 'basic' user skills. I'm fortunate as I run Arch and Slack as well but I'm just trying to picture my 63 year old mother trying to change her video driver.

Sadly, those reasons are why I can't recommend it to my non-tech savvy friends and family.  They want everything to "just work".  no tweaking, no fixing.  No changing video drivers or fussing with terminal. 

I also have experienced some issues and makes me wonder why some machines are plagued by troubles and others are virtually problem free?  My only guess could be the hardware involved.  My mobo seems to be problematic for this flavor of linux. 

I know about the rolling release schedule and that has to be partly the issue, but if 9.04 doesn't work without too much fuss I would just go to a previous version.  Or Debian or such.

Best of luck.

---

### Post by Viva on 2009-06-04
Jaunty is by far the most stable and user friendly OS I've used.

---

### Post by Dysphoria on 2009-06-04
My 9.04 Jaunty 64-bit is up 24/7 for 12 days now (since install) and is ridiculously stable. In fact, I'm kinda disappointed I can't seem to crash it... normally I'm very good at that. Still got to see if I can beat the 437 days uptime I once had with Fedora 7, but it looks promising so far.

No issues with any application either. 

Maybe consider a clean install if you haven't done that? Always better then upgrades.

---

### Post by lovinglinux on 2009-06-04
Jaunty is by far the most stable OS I've used too. I'm experiencing some performance issues, but my computer is not a high-end machine and the hardware is kind of old (P4 3.06 GHz, 2Gb DDR2 RAM, nVidia 7300GT, 160 Gb SATA HDD, 80 Gb IDE HDD). Nevertheless, performance has been improved with recent updates and out-of-the-box hardware support is excellent for my specs.

---

### Post by HappyFeet on 2009-06-04
> **Dysphoria said:**
> My 9.04 Jaunty 64-bit is up 24/7 for 12 days now (since install) and is ridiculously stable. In fact, I'm kinda disappointed I can't seem to crash it...

Same here. Except mine has been on for about 2 months. Best OS I've ever used. And I do recommend ubuntu to other people because it is so stable. I have a few friends that use it with no problems. If they were using windows still, I would be getting constant phone calls from them. 

> **H2SO_four said:**
> They want everything to "just work".  no tweaking, no fixing.  No changing video drivers or fussing with terminal. 


You can't recommend ubuntu to other people because of problems on ***your*** hardware? You're simply denying other people the joy of using a good OS. And no, windows does not always "just work". If windows is so much better, why am I always getting phone calls for me to come over and fix it for them?

And if setup is the problem, why can't you install it for them?

---

### Post by Dragonbite on 2009-06-04
Jaunty is stable for me, but not perfect.

I cannot believe that after installing Jaunty on my laptop and my desktop that I was unable to print to the shared printer on the desktop until I opened Port 631 (CUPS) on BOTH SYSTEMS! ```
ufw allow 631
``` I can't believe a consumer-orientated distro would allow the system to not automatically open these ports when trying to set it up!

Plus I cannot "see" my server in my network but can still connect to it by manually putting smb://192.168.1.10 in the address bar!

Plus I did a clean install on both systems.


For your problems, I suggest doing a full installation. If you have your /home directory on a separate partition then you just make sure you don't format that partition during installation and you'll be able to keep your settings (including bookmarks, cookies, email settings, etc).

---

### Post by speedwell68 on 2009-06-04
I had a whole myriad of problems when I upgraded from Intrepid to Jaunty.  I have recently done a fresh install and I have to say it is the best Ubuntu yet, by far.

---

### Post by jbruced on 2009-06-04
> **rookcifer said:**
> no.

+1

---

### Post by Sealbhach on 2009-06-04
Jaunty's been really solid and stable for me - a big improvement from Intrepid - much faster and smoother. I'm sorry you're having problems - maybe attempt a re-install?

.

---

### Post by pookiebear on 2009-06-04
running jaunty (xubuntu flavor) on a p3 1gz intel. Rock solid. not even a hiccup. Been running the hydrogen drum simulator on it too to make beats (I suck at it, but it is fun)

---

### Post by don_quixote on 2009-06-04
I had a constant crashing that turned out to be an issue with Intel 965 integrated.  Since fixing that problem, things have been smooth.

---

### Post by cariboo on 2009-06-04
Jaunty is so stable, I find it boring. I'm running Karmic, just for some excitment.

---

### Post by overdrank on 2009-06-04
> **cariboo907 said:**
> Jaunty is so stable, I find it boring. I'm running Karmic, just for some excitment.

:lolflag:

---

### Post by markharding557 on 2009-06-05
i have always had trouble with the upgrade in ubuntu so i always do fresh installs much less bother

---

### Post by adam.ec on 2009-07-14
I have never upgraded from version to version directly, always a fresh install. To be honest I'm having more problems with Jaunty now and I'm definitely not the only one. Try looking at the USB issues, sound issues.... again, problems with Python versions, white blocks all over Gimp, machines freezing up.....

The thing is that these problems existed before in one form or another and there were fast, easy to implement solutions on the forums. Now I've even seen with the USB problem a guy in the bug reports denying that the problem exists.

I got slammed down for speaking my mind in another thread about similar issues. Ubuntu 9.04 was a bad release. Congratulations to all of those that have had zero errors with it, but Canonical even knew that there were BIG bugs in this release and I merely said that if there were bugs causing such serious issues with such common hardware that they shouldn't have released it.

---

### Post by Jimleko211 on 2009-07-14
I'm not going to deny that you're having problems with this release, as everyone has different hardware and configurations.  Since you're having problems, why not downgrade to the LTS release?

---

### Post by gjtoth on 2009-07-14
Stable as in doesn't randomly lock up/freeze for no apparent reason?  Yup.  I fixed it though.  I dropped back to Intrepid.  No more lock-ups.

---

### Post by Dragonbite on 2009-07-14
> **Jimleko211 said:**
> I'm not going to deny that you're having problems with this release, as everyone has different hardware and configurations.  Since you're having problems, why not downgrade to the LTS release?

Heck, I was about to from all of the wireless trouble until I was recommended to install WICD on another thread. Works like a charm now (so far).

Downgrading to 8.04 LTS or even 8.10 may be an option if your hardware doesn't play nice with Ubuntu.

I would also recommend trying other distros as since they are in different stages of development and updates what doesn't work with one may work with another.

For example the computer club has a server. We tried to install CentOS (Red Hat clone) but CentOS didn't like something with the RAID.  So we tried Ubuntu, but that has some other issue that kept it from being installed. Last we tried openSUSE and it ran with no problems what-so-ever.

Or I have a webcam, but 8.04 LTS couldn't detect it. I was bummed. Fedora 10 came out and I installed it on a spare machine. Fedora 10 could detect it! Woo Hoo!  Then when I installed and tried it with 9.04 it not only was detected but I had more options in Cheese than I did under Fedora.=D>

---

### Post by NightwishFan on 2009-07-14
Experiencing many issues such as crashes and lockups that were not around in an earlier version makes me thing that there may be a singular reason why all the problems are occurring. I would advise running a live cd and seeing if all the problems are still there. If not, then it might be an installation/upgrade issue.

Personally the biggest problem I ever had using Ubuntu was the original Intrepid kernel did not detect the disk drive on a laptop I was using. So after the upgrade the machine refused to boot without using a Hardy kernel. Although the problem was related to some annoying bios setting that was reset, the patched Intrepid kernel was able to deal with it being incorrect.

My point is for any problem that seems abnormal there might be a simple solution, which may even be fixed with an update (my disk problem was).

---

### Post by xx58 on 2009-07-15
:rolleyes:First time I download 9.04 on 23rd April and it has many problems and I had to go back to 8.10. Month later I made upgrade from 8.10 to 9.04 and it was not work out again. On June I made again upgrade from 8.10 to 9.04 and everything was worked out. So Yesterday I did clean installation to another computer and I reformat it with Ext4. It works and it is very fast, but time to time something like Icons just loose from Desktop. Also today I have problems with printer. IT SAY:"CUPS server error

The CUPS scheduler is not running." If somebody knows how to fix this problem, please help!!!):P

---

### Post by frodon on 2009-07-15
> **adam.ec said:**
> The thing is that these problems existed before in one form or another and there were fast, easy to implement solutions on the forums. Now I've even seen with the USB problem a guy in the bug reports denying that the problem exists.

I got slammed down for speaking my mind in another thread about similar issues. Ubuntu 9.04 was a bad release. Congratulations to all of those that have had zero errors with it, but Canonical even knew that there were BIG bugs in this release and I merely said that if there were bugs causing such serious issues with such common hardware that they shouldn't have released it.Any common hardware can surffer from this kind of bug and not only with linux, think to update your BIOS, it's the first thing i would do when having recurrent USB and kernel freezing issues.

One thing ubuntu can't fix for you is your BIOS, it is possible however than some release plays better than others but this is not predictable.

So my personnal advice is to update your BIOS and i assume you are not using ext4 which is known to have issues for the moment on jaunty.

---

### Post by xx58 on 2009-07-15
I resolve all problems with 9.04 now and I have Ext4. I am happy, but it is not easy to work out all become problems. I still have only left one tiny problem and it is [COLOR=Red]Pokerstars.com[/COLOR] Problem, when I move cursor over players before I am not sign in, I can see where they are from, but when I sign in like player and I move cursor over players, I cannot anymore see where they are from. Information don't pop up! Anybody knows and can help?):P

---

### Post by Zlatan on 2009-07-15
my advise in this case would be- stick with Intrepid until Karmic. you don't have to use latest version of ubuntu even if it does not work for you.
hardy heron is LTS, btw.

> **adam.ec said:**
> What have Canonical done? I've been using Ubuntu since Hoary and the only problem was the stupid Intel HDA sound (which incidently still hasn't been fixed by the looks and also occurs on almost every distro).

I've been running the stable (keeping face straight) release of Jaunty for three weeks and the problems are mounting up. The only extra I have installed is Bluefish and an attempted Skype install. Strangely, I've had none of the direct problems related to video and boot up with my Intel D945 mainboard.

Applications like Transmission and Pidgin are freezing up and disappearing but still running in the background. File permissions are going crazy on my USB key which I have changed twice since having 'read only' errors. I'm getting big white blocks all over Gimp making it unusable. Evince opens a PDF and shuts down immediately. Firefox keeps turning greyscale and locking me out for 8 minutes at a time.

It's all well and good providing the many solutions but this release should never have been made. Just at a time when MS were screwing up their own products and gave mainstream Linux a chance and we get Ubuntu Jaunty.

Does anybody else have any of the same problems? It's going to take me a week to fill out bug reports for these things. I can't understand why Canonical can't fix the known problems in an update and instead expect all of their users to be able to correct them with 'basic' user skills. I'm fortunate as I run Arch and Slack as well but I'm just trying to picture my 63 year old mother trying to change her video driver.

---

### Post by spoons on 2009-07-15
The problems I have had with Jaunty are PulseAudio and ATI Driver problems. Sadly Canocial would rather me boot 10 seconds faster than fix these.

---

### Post by headflux on 2009-07-15
I've certainly found jaunty to be the most stable release of Ubuntu yet (I started on 7.04), but it's by no means perfect.  I do get the occasional freeze which requires a hard reboot, but otherwise it's pretty much there.

I have found though that since Gutsy, I've had to do a fresh install to upgrade, as going through Update Manager always fails for me.

Still love Ubuntu regardless; best OS out there by a mile.

---

### Post by ramnarayan on 2009-07-15
I use 7.10 for stable work and because it runs a piece of hardware that has not worked since (not on 8.04, 8.10 or 9.04)

But 9.04 is largely terrible and am waiting for a better release or update or even an alternate Linux 

but till then 7.10 rules (unsupported or not)

---

### Post by cariboo on 2009-07-15
I have been using Jaunty since the tool chain was uploaded, it was one of the most stable pre-beta distribution I've ever used. Karmic has had a lot more problems. I you want Ubuntu to run with zero problems, make sure your hardware is compatible.

---

### Post by ThisEndlessFall on 2009-07-15
> **cariboo907 said:**
> I have been using Jaunty since the tool chain was uploaded, it was one of the most stable pre-beta distribution I've ever used. Karmic has had a lot more problems. I you want Ubuntu to run with zero problems, make sure your hardware is compatible.

This is a rather strange statement given that Ubuntu is marketed against Windows for the general desktop market. Ubuntu should be compatible with hardware, not the other way around.

---

### Post by Viva on 2009-07-15
> **ThisEndlessFall said:**
> This is a rather strange statement given that Ubuntu is marketed against Windows for the general desktop market. Ubuntu should be compatible with hardware, not the other way around.

That is rubbish. How do you except Ubuntu to support hardware if the manufacturers don't release drivers or offer help? Hardware must support linux, not the other way around. Besides, Ubuntu supports more hardware out of the box than Windows. The problem is with manufacturers who offer little or no support for any non-windows operating systems and hardware that are difficult to reverse engineer.

---

### Post by ThisEndlessFall on 2009-07-15
> **Viva said:**
> That is rubbish. How do you except Ubuntu to support hardware if the manufacturers don't release drivers or offer help? Hardware must support linux, not the other way around. Besides, Ubuntu supports more hardware out of the box than Windows. The problem is with manufacturers who offer little or no support for any non-windows operating systems and hardware that are difficult to reverse engineer.

Linux is built on reverse engineering ...

---

### Post by Dragonbite on 2009-07-16
> **ThisEndlessFall said:**
> This is a rather strange statement given that Ubuntu is marketed against Windows for the general desktop market. Ubuntu should be compatible with hardware, not the other way around.

Easier said than done.  Some day, maybe but not currently.

> **ThisEndlessFall said:**
> Linux is built on reverse engineering ...

Currently, subject to change without notice.

---

### Post by Ms_Angel_D on 2009-07-16
> **adam.ec said:**
> What have Canonical done? I've been using Ubuntu since Hoary and the only problem was the stupid Intel HDA sound (which incidently still hasn't been fixed by the looks and also occurs on almost every distro).

I too have issues with Intel HDA, and have had it since the beginning of using Linux. I opened a [bug on launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/307574"), but I think it's just sitting there...

---

### Post by RandomJoe on 2009-07-16
My Jaunty experiences have been at polar opposites of the spectrum, no middle ground! :)

My first impression was most positive - this was the first time I could get a *fully* functioning system on my various old laptops from first boot, even wireless!  I also recently bought a netbook and it worked perfectly there too.  Even suspend/resume, something else I'd never seen work quite properly before.  Had no stability issues on any of the machines that run it, although they aren't usually on for long stretches.  I haven't gotten around to upgrading my primary machine yet.

Then last weekend I tried to upgrade (fresh install) my getting-old Dell server.  Nothing particularly fancy about the thing, just a P4 system with middle-of-the-road components.  (PowerEdge 600SC)  It has *never* had a problem with *any* version of Linux in the past, and I've tried a couple other distros now without issue.  But Jaunty flat won't boot at all.  It's apparently something in the kernel - if I go textmode to watch the boot process, the kernel gives a single ACPI warning message (which is harmless - I have other computers that show the same thing on every boot and run fine) then a few seconds later locks hard.  Don't get a single line of the usual kernel boot text!

---

### Post by orion1315 on 2009-07-16
I have only had one problem with this release of ubuntu and that is that is does not support my wireless adapter, WN111v2.
had to wire it to the router downstairs and do a bunch of nonsense.
Also didnt come with drivers for my graphics card :D
ATI Drivers now are so bad

---

