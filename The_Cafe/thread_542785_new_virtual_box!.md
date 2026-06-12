---
title: "new virtual box!"
date: 2007-09-04
forum: The Cafe
---

### Post by vexorian on 2007-09-04
[http://virtualbox.org/wiki/Changelog](http://virtualbox.org/wiki/Changelog)

Have not tried seamless windows yet, but must say that the shared clipboard has been fixed! That's all in one a great improvement.

I use virtualbox to develop and test windows apps, yes I have moved to Linux but still need to continue the development of some applications.

Please note that if you update virtualbox to 1.5 you also have to update your virtual OS' guest additions by reinstalling them.

---

### Post by ssam on 2007-09-04
just days after 1.4 gets include in gutsy universe
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=virtualbox&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=virtualbox&searchon=names&subword=1&version=all&release=all)

---

### Post by PartisanEntity on 2007-09-04
Seamless WIndows? Is that what I think it is? Like having a window open from Win XP on the Ubuntu desktop fro example?

Shared clipboard, excellent. Looking forward to trying this out.

---

### Post by EndPerform on 2007-09-04
> **ssam said:**
> just days after 1.4 gets include in gutsy universe
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=virtualbox&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=virtualbox&searchon=names&subword=1&version=all&release=all)

The 1.5 Feisty .deb on their site installs just fine on Gutsy.  I'm using it now and I haven't seen any problems.

---

### Post by popch on 2007-09-04
> **PartisanEntity said:**
> Seamless WIndows? Is that what I think it is? Like having a window open from Win XP on the Ubuntu desktop fro example?

Shared clipboard, excellent. Looking forward to trying this out.

Quote from [http://www.virtualbox.org/wiki/News]("http://www.virtualbox.org/wiki/News")
> Among the major features is the seamless windowing mode where the windows of a VM directly integrate with your Linux or Windows desktop -- making VirtualBox the first product to offer this support on the Windows and Linux platforms.

---

### Post by ssam on 2007-09-04
> **EndPerform said:**
> The 1.5 Feisty .deb on their site installs just fine on Gutsy.  I'm using it now and I haven't seen any problems.

yes they seem to be good at supporting ubuntu with packages.

its nicer though when you can just grab it with Applications->Add/Remove

---

### Post by starcraft.man on 2007-09-04
Just a note but I've had VirtualBox 1.5 for at least 3 days now I think, prior to it's official launch. It's been in the Feisty VirtualBox repo for at least that time. I was curious why the binary wasn't up for download, maybe fixing a few final bugs? Anyway, another win for the repo... so much better than downloading debs.

---

### Post by bash on 2007-09-04
Nice one. Didn't notice. Just testing it now. But props to Virtualbox. Finally a company not focused on just bringing the VM eye-candy to the Mac. Now they just need to add dx 8 support like parallels or vmware has and I would be completly happy.

---

### Post by PatrickMay16 on 2007-09-04
Does virtualbox support dual processors?

---

### Post by vexorian on 2007-09-04
> **vexorian said:**
> [http://virtualbox.org/wiki/Changelog](http://virtualbox.org/wiki/Changelog)

Have not tried seamless windows yet, but must say that the shared clipboard has been fixed! That's all in one a great improvement.

I use virtualbox to develop and test windows apps, yes I have moved to Linux but still need to continue the development of some applications.

Please note that if you update virtualbox to 1.5 you also have to update your virtual OS' guest additions by reinstalling them.
looks like the shared clipboard is still causing gnome's clipboard to bug out. So disabling it once again.

Just tried seamless windows and they work really well, you only need guest additions and then it is an option in the virtual machine's top menu. It just makes the windows and taskbar out of the virtual machine kind of makes things less of a mess, very cool.

> # VRDP: fixed sporadic client disconnects This one is cool, I actually did most of the work of the virtual machine in a share and sometimes the shared folder (on the host) got disconnected and the programs in the virtual machine had errors, haven't experienced this issue again today.

---

### Post by n3tfury on 2007-09-04
how much RAM are you guys packing to run an OS in virtualbox smoothly?

---

### Post by nonewmsgs on 2007-09-04
hopefully this one wont freeze explorer from mounting/unmounting cds.

---

### Post by AnRa on 2007-09-04
Great! :D

---

### Post by starcraft.man on 2007-09-04
> **n3tfury said:**
> how much RAM are you guys packing to run an OS in virtualbox smoothly?
I got 1 GB of old DDR (it's an old PC). I give my VM 384 dedicated RAM and 64MB video (both XP and Linux distros run well with this) and it runs pretty smooth. I can also of course do other things though obviously not rendering or some other super intensive thing. It's not as bad as most people think.

> **nonewmsgs said:**
> hopefully this one wont freeze explorer from mounting/unmounting cds.

Never happened to me with 1.4.

---

### Post by n3tfury on 2007-09-04
> **starcraft.man said:**
> I got 1 GB of old DDR (it's an old PC). I give my VM 384 dedicated RAM and 64MB video (both XP and Linux distros run well with this) and it runs pretty smooth. I can also of course do other things though obviously not rendering or some other super intensive thing. It's not as bad as most people think.





Excellent, exactly what i wanted to hear.  My box is a little older also and currently run 512MB, but will pick up a 1GB stick tomorrow.  Thanks!

---

### Post by starcraft.man on 2007-09-04
> **n3tfury said:**
> Excellent, exactly what i wanted to hear.  My box is a little older also and currently run 512MB, but will pick up a 1GB stick tomorrow.  Thanks!

No problem. Oh and btw when you install virtual box use the repository (it's below the binary download list). Makes things really easy to upgrade/install.

Also, you can just pick up another 512 stick, it's best to have paired memory (most reasonably old boards support dual channel I think).

---

### Post by n3tfury on 2007-09-04
Thanks for the repo tip.  I was thinking I'd get one 1GB stick then another later.  no good?

---

### Post by igknighted on 2007-09-04
> **n3tfury said:**
> Thanks for the repo tip.  I was thinking I'd get one 1GB stick then another later.  no good?

It'll certainly work.  I have found that after about 512mb of ram, the speed is more important than how much memory there actually is.  So you might actually see more improvement if you can match the current 512 stick, but either would be nice.

Where in upstate, out of curiosity?  I'm from Syracuse originally, and spend a lot of my time now between Syracuse, Utica and Rochester.

---

### Post by n3tfury on 2007-09-04
actually just moved to ALB from PHX a few months ago :)

---

### Post by regomodo on 2007-09-05
awesome. I just added vbox to my sources.list so that i don't miss updates again.

Seamless mode is very good. I am liking innotek more and more and i am impressed by their steady development.

> **n3tfury said:**
> how much RAM are you guys packing to run an OS in virtualbox smoothly?

I have 1.75GB (swapped a 256 for a 512 with my bro) and i use ~600MB with VBox'd xp home (set at 192MB)

---

### Post by triptoe on 2007-09-05
is there a way to get a resolution larger than 1074 by 768 ? and also... is it using OSS to output sound? Can you make it use alsa?

Also sometimes it crashes on me

---

### Post by regomodo on 2007-09-05
> **triptoe said:**
> is there a way to get a resolution larger than 1074 by 768 ? and also... is it using OSS to output sound? Can you make it use alsa?

Also sometimes it crashes on me

Are you using XP? if so have you installed the guest additions?

---

### Post by triptoe on 2007-09-05
yes im using xp.. when i click install guest additions nothing happens

---

### Post by mips on 2007-09-05
Hi,

Slightly off topic. I have never used virtualbox (only vmware) but I would like to install:

1. Windows XP in vb from a original install cd.
2. Install a linux dsitro in openbox from an ISO

Anyone got liks to guides on the above ?
Will all external ports be supported in vb when running XP in vb, this is for a friend thats new to ubuntu and would like it as a default OS and have XP running inside it.

---

### Post by tigerpants on 2007-09-05
Most useful piece of kit I have ever used on linux. I love virtualbox. Just thought I'd share the love.

---

### Post by triptoe on 2007-09-05
I followed this guide but it still doesn't work:

> 4.2.1.1. Mounting the Additions ISO file In the "Devices" menu in the virtual machine's menu bar, VirtualBox has a handy menu item named "Install guest additions", which will automatically bring up the Additions in your VM window. If the menu item does not work, you can perform the following steps manually:

1. Start the virtual machine where you have installed a Windows guest operating system.

2. Select "Mount CD/DVD-ROM" from the "Devices" menu in the virtual machine's menu bar and then "CD/DVD-ROM image". This brings up the Virtual Disk Manager described in Section

3.5, “The Virtual Disk Manager”.

3. In the Virtual Disk Manager, press the "Add" button and browse your host file system for the VBoxGuestAdditions.iso file: • On a Windows host, you can find this file in the VirtualBox installation directory (usually under C:\Program files\InnoTek VirtualBox). • On a Linux host, you can find this file in the additions folder under where you installed VirtualBox (usually /opt/VirtualBox-xxx).

4. Back in the Virtual Disk Manager, **select that ISO file and press the "Select" button. This will mount the ISO file and present it to your Windows guest as a CD-ROM.**

After all I changed the settings to True Collor (32 Bit). The I was able to change in the fullscreen mode without any problems.

I think it isn't such a nice way to manual mount the image. It would be much easier to just click the entry in the menue. 

i put in bold the part that doesn't work. When i select the iso nothing happens.

---

### Post by triptoe on 2007-09-05
[IMG]http://www.teslam.net/Screenshote.png[/IMG]

---

### Post by n3tfury on 2007-09-05
that's awesome.  can't wait to get more RAM today!

---

### Post by regomodo on 2007-09-05
@ triptoe

are you sure nothing is mounting? Check in "My Computer". My XP install does not automatically autoload CDs so check that

---

### Post by triptoe on 2007-09-05
> **regomodo said:**
> @ triptoe

are you sure nothing is mounting? Check in "My Computer". My XP install does not automatically autoload CDs so check that

hey you were right... whoops.

Wow now it works... if you look at the resources when you put it on pause it pretty much drops the cpu completely and just stores itself in some ram somewhere... i can leave it on pause in one of my virtual desktops and switch to it if i need to use windows. that is pretty sweet.

---

### Post by regomodo on 2007-09-05
glad you got yours going triptoe. There is always something easy to miss with computers.

Here's a pic of my XP-pro setup with my favourite music player. Wish it was ported to linux

---

### Post by n3tfury on 2007-09-05
> **regomodo said:**
> glad you got yours going triptoe. There is always something easy to miss with computers.

Here's a pic of my XP-pro setup with my favourite music player. Wish it was ported to linux

yeah, i can't handle not having Foobar around.  one of a super short list of why i won't give up my windows box just yet.

[IMG]http://img486.imageshack.us/img486/8459/foobarie2.jpg[/IMG]

---

### Post by KCPokes on 2007-09-05
Regomod, what app is running on the right side of your desktop, showing stats and logging?  I spend so much of my time just using CLI Unix and Linux that I don't spend enough time discovering the slick little apps such as that.  I could definitely go for something like that.

---

### Post by regomodo on 2007-09-05
> **KCPokes said:**
> Regomod, what app is running on the right side of your desktop, showing stats and logging?  I spend so much of my time just using CLI Unix and Linux that I don't spend enough time discovering the slick little apps such as that.  I could definitely go for something like that.

its called Conky

[http://ubuntuforums.org/showthread.php?t=205865&highlight=howto+conky](http://ubuntuforums.org/showthread.php?t=205865&highlight=howto+conky)

follow that and ignore step 2.

Mine is almost identical to the one in this guide but i've had to change things like network device and partitions. Also, i don't like percentages of things so i've added some numbers to memory and swap.

---

### Post by KCPokes on 2007-09-05
Thanks!  I'll check it out.

---

### Post by vexorian on 2007-09-05
I see no reason to think foobar wouldn't work in a virtual machine, unless it is dependant on 3d accel. I guess with seamless windows you will be able to run it nicely on Linux without booting native windows.

---

### Post by n3tfury on 2007-09-05
> **vexorian said:**
> I see no reason to think foobar wouldn't work in a virtual machine, unless it is dependant on 3d accel. I guess with seamless windows you will be able to run it nicely on Linux without booting native windows.

which is exactly why i'm going virtualbox and getting more RAM today :)

---

### Post by regomodo on 2007-09-05
> **vexorian said:**
> I see no reason to think foobar wouldn't work in a virtual machine, unless it is dependant on 3d accel. I guess with seamless windows you will be able to run it nicely on Linux without booting native windows.

i have tried but i think i had issues with foobar properly detecting the filesystem. I'll try again now

[update] just installed via WINE and i found my music folder no problems. I can't think what the issue was when i first tried it. I think i must have gave up when i 1st tried due to newbitis
[update2] i got it working (winecfg the sound) but it is terribly glitchy. Starting songs creates a loud piercing screech. Switching between apps (or min/maximizing foobar) causes foobar to pause for a moment. Plus, the sound is a bit waffly. Yeah, i want foobar ported to linux

---

### Post by xl_cheese on 2007-09-05
I just upgraded from 1.4 to 1.5.  Is there a how to on how to do the seamless thing within virtual box?

I don't see any options within vb to do it.

---

### Post by regomodo on 2007-09-05
> **xl_cheese said:**
> I just upgraded from 1.4 to 1.5.  Is there a how to on how to do the seamless thing within virtual box?

I don't see any options within vb to do it.

you have to reinstall the vbox guest additions, reboot xp and then look in the menus at the top for seamless mode. Done.

---

### Post by xl_cheese on 2007-09-05
didn't realize I needed to also install new guest addons. 

Now the option for seamless shows up.  Works great.  Much faster than the old method using Rdesktop.

---

### Post by teet on 2007-09-05
Hmmm.

My shared folder quit working when I upgrade to 1.5

I searched the vbox forums and it seems others are experiencing my same problem.

-teet

---

### Post by starcraft.man on 2007-09-05
> **teet said:**
> Hmmm.

My shared folder quit working when I upgrade to 1.5

I searched the vbox forums and it seems others are experiencing my same problem.

-teet

Mine work fine. Reinstall the guest additions, then remount the share. If it doesn't work, not sure... I know on my clean install worked flawless.

---

### Post by teet on 2007-09-05
> **starcraft.man said:**
> Mine work fine. Reinstall the guest additions, then remount the share. If it doesn't work, not sure... I know on my clean install worked flawless.

I did reinstall the guest additions.  The weird thing is that my shared folder worked for about 30 minutes after I upgraded to 1.5.  Then my virtual machine crashed.  When I opened it back up, *poof* no more shared folder.

Others are having my same problem.  I'll get it sorted out sooner or later.

-teet

---

### Post by mips on 2007-09-06
VB 1.5 is just great, can't believe how cool the seamless windows are!

Only issue I have so far is getting my USB to work. I followed the howto on the VB site but still no go.

Do I have to install drivers in windows or does it just use the VB ones ?

Any ideas on the USB ?

---

### Post by tech9 on 2007-09-06
Excellent, I will try this today:guitar:

---

### Post by onero on 2007-09-06
Oh wow, I love version 1.5. Yay Virtualbox! Seamless Desktop is awesome, but it doesn't work that well with Compiz Fusion. Ah well, I can live with that :D

Just a note, for the guy that asked whether you could use the ALSA drivers, yes you can; I use ALSA. I think it uses OSS by default but you can change it in the Machine Settings, under Audio.

---

### Post by n3tfury on 2007-09-06
> **onero said:**
> Oh wow, I love version 1.5. Yay Virtualbox! Seamless Desktop is awesome, but it doesn't work that well with Compiz Fusion. Ah well, I can live with that :D

Just a note, for the guy that asked whether you could use the ALSA drivers, yes you can; I use ALSA. I think it uses OSS by default but you can change it in the Machine Settings, under Audio.

can you elaborate on how seamless desktop doesn't work well with c-f?

---

### Post by Calash on 2007-09-06
I like the seamless setup, but it throws fits with Compiz Fusion...going to wait and hope they get that worked out.

Been trying to get the bridged network setup, but so far that is not working :(

Another night of google and following instructions ;)

---

### Post by regomodo on 2007-09-06
> **n3tfury said:**
> can you elaborate on how seamless desktop doesn't work well with c-f?

i don't know if it's anything like Beryl but with beryl the XP background covers your desktop, minus the panels.

At the poster above, after setting up the shared folders in virtualbox, go to your "my network places" in XP. From here go up 1 or 2 levels and a virtualbox network should be present

---

### Post by notwen on 2007-09-06
> **regomodo said:**
> At the poster above, after setting up the shared folders in virtualbox, go to your "my network places" in XP. From here go up 1 or 2 levels and a virtualbox network should be present

Thank you for this.

---

### Post by n3tfury on 2007-09-06
@calash and regomodo, thanks for your replies

---

### Post by onero on 2007-09-07
> **n3tfury said:**
> can you elaborate on how seamless desktop doesn't work well with c-f?

When you have any program / window open in the VM, it looks ok, but if you close everything either the background turns black or becomes the XP background. It's actually still kinda usable, but it's very distracting (and thus unproductive :D).

Also, I'd love if the VM could utilize the multiple workspaces; it seems to just stay in one desktop. I didn't use it extensively, but I seem to recall that the old solution (with rdesktop and beryl, etc.), you could move program windows across desktops, and they would also respond to beryl effects :D It would be awesome if they could do something similar, but in any case, it's not really a priority, so it's fine :D 

Easier networking is also on my wishlist though ... I've followed the tutorials for giving the VM its own IP address (in your network), and I can do it manually, but it's terminal-heavy and somehow I never got it to work so that it would happen on startup :(

---

