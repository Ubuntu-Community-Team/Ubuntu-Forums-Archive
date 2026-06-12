---
title: "Speed tests"
date: 2006-08-29
forum: The Cafe
---

### Post by K.Mandla on 2006-08-29
I spent my weekend distro-hopping, and finished off the revelry with a few speed tests. [This post]("http://www.ubuntuforums.org/showthread.php?t=241393") had me thinking for most of the week about how Ubuntu and Windows really compare, and what could be done about it.

The standard disclaimers include a nod toward individual hardware differences, individual installation differences and other factors. I'm willing to admit that these numbers might not be identical after every installation. However, for my own purposes and edification, they will serve.

[This]("http://www.ubuntuforums.org/showthread.php?t=237148") is the test machine. Specs are as follows.

[INDENT]**Dell Optiplex GX150**, service tag [6DNXL01]("http://support.dell.com/support/topics/global.aspx/support/en/product_support?c=us&l=en&s=gen")
BIOS version A11
Intel 1Ghz Pentium III Coppermine
Viking 512Mb PC133 Memory
Western Digital 9Gb 7200rpm hard drive
24x TEAC 224E CD-ROM
Integrated Intel 815 Series Video
Integrated 10/100 3Com Remote Wake-up NIC[/INDENT]
Nothing fancy. No hardware tweaks or cheats. These are everyday improvements to a stock machine. In other words, I have nothing up my sleeve. ;)

I picked Xubuntu 6.06.1 and Windows 2000 SP1. Xubuntu is a good match for this box, and the original machine shipped with Win2K SP1 ... about five years ago. 

Installations were written to blank, unpartitioned drives. Defaults were used wherever possible. The watch started at the press of the power button and stopped when the hard drive stopped spinning.

[INDENT]**Default Xubuntu 6.06.1 installation**
**Installation time: **00:28:30
**File system: **default ext3 partitions
**Cold boot startup time: **00:01:04
**Shutdown time: **0:01:29
**Abiword 2.4.4 startup time: **0:00:04.0
**Gimp 2.2.11 startup time: **0:00:13.1
**Firefox 1.5.0.6 startup time: **0:00:08.8 seconds
**[Net speed test]("http://www.bandwidthplace.com/speedtest"): **1.7 megabits per second (average of 3 tests)[/INDENT]
The shutdown time is the worst point. Xubuntu takes a full minute and a half to close down shop. And nine seconds seems like an eternity for Firefox to open. 

(I should note here that I disabled the login window for the purposes of the startup time. It wouldn't be fair to count the time it takes me to type, correct, retype and finally enter my name and password. :) )

The only corrections I had to make to the Xubuntu installation were to knock down the color depth, and that's something I think is unique to [my hardware]("http://www.ubuntuforums.org/showthread.php?t=245275").

Now Windows:

[INDENT]**Default Windows 2000 SP1 installation**
**Installation time: **00:34:00
**File system: **default NTFS partition
**Cold boot startup time: **00:01:03
**Shutdown time: **00:00:21
**Abiword 2.4.1 startup time: **00:00:05.1
**Gimp 2.2.9 startup time: **00:00:11.1
**Firefox 1.5.0.6 startup time: **00:00:09.5
**[Net speed test]("http://www.bandwidthplace.com/speedtest"): **1.1 megabits per second (average of 3 tests)[/INDENT]
Installation took longer, and that includes the time it takes Win2K to reformat an already blank hard drive to NTFS. Sure, that adds to the time, but if you want a faster installation, you have to add the option for a quick format (which XP has). 

What's interesting though, is the startup time from a cold boot and the start time for Firefox. In both cases, it's nearly the same. I seemed to remember Firefox starting much faster than that, but I tried it a couple of times, and each time it was just as long as its Xubuntu counterpart.

Well, Abiword takes a little longer to start in Windows, but not by a noticeable amount. The Gimp starts up quite a bit faster (once you've done the initial configuration, of course). By the way, the Gimp and Abiword were installed off the OpenCD v3.1. Firefox was downloaded fresh.

I can't account for the difference in Internet speed tests. I'm not sure why I included that test, but I have a feeling the results may have been skewed by traffic at different parts of the day. 

So overall, with the exception of Xubuntu's dreadful shutdown time, the two OSes are more or less neck-and-neck. At least from my vantage point.

Oh yes, I almost forgot one thing.

It always surprises me to hear people say that it's easier to install Windows, or that things just work for them in Windows.

Let me tell you what didn't work for me after installing Windows 2000.

[LIST=1]
[*]**No internet access** until I had finished the configuration wizard (remember the "Connect me to the Internet" shortcut?);
[*]No video drivers, which means **no native resolution** and **an unusable color depth**;
[*]and **no sound**.
[/LIST]
So really, when I look at the difference between the two, I have to add on even more time to the Windows installation because *_it's not done yet_*. I'll need another hour of my life to install service packs, install DirectX, and install sound and video drivers -- and I still have all the antivirus and spyware and firewall software needed just to make the Internet safe for my new, virgin system. :rolleyes: 

That's about it. Next stop, if I have time tomorrow, is to rebuild an Ubuntu XFCE desktop with all the speed tweaks I can find.

Cheers! :mrgreen: 

P.S.: If you want more details, you can find them [here]("http://kmandla.wordpress.com/2006/08/29/preliminary-speed-test-results/").

---

### Post by funchords on 2006-08-29
The reason your speed tests were different is because the default TCP/IP parameters in Windows are very conservative.  

For example, the default maximum TCP window size (RWIN) is 17520 in Windows 2000/XP.  Last I checked, it was about 130K in Dapper.  This means Dapper users enjoy a lot less overhead and better performance on broadband.  

When Windows 2000/XP was being developed, the average user was not on Broadband.  If the link is noisy or slow, Windows users might get better performance than Dapper users.

---

### Post by funchords on 2006-08-29
Perhaps you already considered this, but in any of these tests, you should throw away the first result.  The first time a user logs on, the first time a system shuts down, the first time Firefox is started for a particular user ...

All of these 'firsts' are likely to have extra tasks that will not need to be done on subsequent executions.

Thank you for doing this.  It's interesting and probably valuable!

---

### Post by Jeroen Vernooij on 2006-08-29
Interesting, thanks for posting this. 
Something to keep in memory: 
Every new Ubuntu release shows speed improvements, every Windows-release is slower and more bloated.

Edgy has faster Nautilus startup thanks to GNOME 2.16, and faster shutdown, thanks to this spec:
[https://launchpad.net/distros/ubuntu/+spec/teardown](https://launchpad.net/distros/ubuntu/+spec/teardown)

---

### Post by funchords on 2006-08-29
From the **Let's Be Fair** department... 

> **Jeroen Vernooij said:**
> every Windows-release is slower

[-(   The opposite is true, Jeroen.  Each Windows release has held faster boot-up and faster app-loading as a feature, and testing has shown that each release has met that goal.

The last few releases have included and improved upon pre-fetching (application accelleration), caching, and holding off starting certain system services until a useable UI is presented.

> **Jeroen Vernooij said:**
> and more bloated.

Are you talking about the size of the files installed on the disk or are you talking about the number and size of the default processes at run time?  

There was significant installation and process growth between the 95/98/SE/ME family and the NT/2K/XP/2K3 family, that's true.  But they are also very different architectures.  Across these families, there has not been significant growth.  NT to 2K3 ... all fit on a mostly filled CD with room to spare.  

As for daemon bloat, Windows is shrinking in the number of processes over time.  Compare Windows XP and Windows XP SP2, which has about ten fewer running services.  This is due to a shift of thinking in Redmond.  Microsoft used to run most daemons by default.  Shortly after XP was released, the threat landscape changed and they ultimately changed this tactic and disabled several daemons.

I haven't seen Vista yet.  My plan is to complete my move to Ubuntu before then.

Linux installations between installations intended for systems with 32 MB of memory and 256 MB of memory are comparably smaller and larger, both in installation and process numbers/sizes.  Further, the desktop software (e.g. Gnome/KDE) has certainly grown along with the Microsoft Windows desktop as more features and eye candy get added over time.

Let's not pretend that Ubuntu is a stripped-down operating system.  It certainly is not, nor do we want it to be.  Both Windows and Ubuntu are aiming for the same user base, ranging from the new user to the server administrator.  The users want ease-of-use. To accomplish this effectively, a certain amount of "bloat" is acceptable.  And while it would be fun to point and laugh at Windows for allowing the bloat to spin out of control, 1) it's not true, and 2) we have some bloat, too.

---

### Post by K.Mandla on 2006-08-29
> **funchords said:**
> The reason your speed tests were different is because the default TCP/IP parameters in Windows are very conservative.
Aha! Thank you! I had forgotten all about those settings. That does explain the speed differences. It's been so long since I used Win2K on a regular basis that I forgot about all the tweaks I used to employ to speed things up. Thanks for reminding me.

To be honest, I don't know why I even bothered with a "net speed test." I think my original thought was there might be a driver tweak or default setup that would impede one or another. I guess, in a way, I was right. I don't think I would include it in future tests, though. It's too abstract, in my opinion.

[QUOTE=funchords]Perhaps you already considered this, but in any of these tests, you should throw away the first result. ... All of these 'firsts' are likely to have extra tasks that will not need to be done on subsequent executions.[/quote]
Yes, I made a point of letting the program initialize before trying it with the watch. I knew the Gimp was going to ask about first-time user configurations, and Firefox always wants to import bookmarks and whatnot. So yes, the numbers you see aren't first-run times, but second- or even third-runs.

That being said, the cold boot time is a second or third boot, but the installation time includes that first setup boot. Windows has that network setup login thing that pops up on "first" boot, and I considered that to be part of the installation process.

[quote=Jeroen Vernooij]
Edgy has faster Nautilus startup thanks to GNOME 2.16, and faster shutdown, thanks to this spec:
[https://launchpad.net/distros/ubuntu/+spec/teardown](https://launchpad.net/distros/ubuntu/+spec/teardown)[/quote]
That would be a welcome improvement. I like their rationale as well: I would agree that a lot of those shutdown activities are unnecessary if the power is going out in a minute or so. Trimming the shutdown time would be wise. Thanks for the link.

---

### Post by K.Mandla on 2006-08-30
One last rebuild, this time tuning for speed. Again, the hardware is the same, but the entire construction is designed to reduce the unnecessary and tweak for fastest results.

[INDENT]**Custom Ubuntu-XFCE 6.06.1 installation**
**Installation time:** See below
**File system: **
[INDENT]/dev/hda1 96Mb boot - ext2
/dev/hda2 4Gb root - ext3 with dir_index, journal_data_writeback and noatime
/dev/hda5 512Mb swap (logical)
/dev/hda4 4.3Gb home - ext3 with dir_index, journal_data_writeback and noatime[/INDENT]
**Cold boot startup time:** 00:00:52.5 
**Shutdown time: **00:00:11.3
**Abiword 2.4.4 startup time:** 00:00:01.6
**Gimp 2.2.11 startup time: **00:00:05
**Swiftfox 1.5.0.6 startup time:** 00:00:04.9
**Net speed test:** See below[/INDENT]
As you can see, I got some drastic improvements in this round. Here's what I did.

First, as you probably noticed, I repartitioned with a separate /boot and /home, and set the root and /home partitions to ext3 with dir_index, journal_data_writeback and noatime. Since I'm working with a 1Ghz machine it's probably wise to stick to the less-processor-intense ext3 file system, then go on to tweak it for fastest performance. 

On top of that, I have a server installation with some packages yanked out. To be specific: ubuntu-minimal, jfsutils, pcmciautils, reiser4progs reiserfsprogs, vim, wirelesstools, wpasupplicant and xfsprogs. Since this is a desktop machine, some of those are irrelevant; others I just don't need, or for that matter, want. I know some of them wouldn't even be noticed, but unneeded is unneeded, and so out it goes.

Next, I installed the linux-686 kernel, then added prelink and preload, and disabled IPv6. I used sysv-rc-conf to disable any services I didn't need, and filtered through /etc/rc0.d and /etc/rc6.d to streamline the startup and shutdown sequences. I also set vm.swappiness to 0, since 512Mb is more than enough memory.

I installed a working X system with *sudo aptitude install x-window-system-core xfce4*. Out of sheer vanity I added xfce4-terminal, thunar and the Tango icon themes. (What can I say? I was feeling crazy. :rolleyes: )

And finally, for the *pièce de résistance*, I downloaded the Ubuntu deb for Swiftfox for Pentium 3's.

As you can see, there's a drastic improvement in almost every category -- and if you consider a 10-second decrease in boot times substantial, that one is quite good too. And five seconds to load Swiftfox is the best reason of all to use it. The Gimp and Abiword were installed from the repos, and likewise performed faster this time.

The downside is that all these tweaks and twitches can take an hour or two to put together. Editing sysv-rc-conf doesn't take long, but finding their corresponding startup and shutdown entries in rc0.d and rc6.d is a real pain. Other parts of it, like setting the file system and then installing in two separate sessions, are very time-consuming.

But you win that all back in performance. Starting Abiword in less than two seconds is immensely gratifying on a 1Ghz machine. ;)

One last note: I threw out the net speed test for the reasons I mentioned earlier, but also because I was getting ungodly results this morning, when I timed it (like 3.3 megabits per second). I didn't trust it any longer.

I have a better explanation of the setup [here]("http://kmandla.wordpress.com/"). If anyone has any more speed tweaks they can share, I'd be happy to hear them.

---

