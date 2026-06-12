---
title: "Kernel requires pae, unable to boot - now what?"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-04-16
If you're reading this you probably tried to run a 12.04 live session or install 12.04 and were presented with this warning, "**This kernel requires the following features not present on the CPU: pae. Unable to boot - please use a kernel appropriate for you CPU**." 

So what's up and what are your options?

In November 2011 the kernel devs seemed to have [doomed the non-pae kernel]("http://www.phoronix.com/scan.php?page=news_item&px=MTAxMzU") but in December 2011 [things began to look up]("http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM"), however when Precise Beta 1 was released the only real options to install a non-pae kernel were to upgrade from either Lucid or Oneiric or to use the [netboot non-pae mini.iso]("http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/").

But after some [complaining on my part]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/50") and requests from [Xubuntu]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/955009") and [Lubuntu]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/958866") the options have improved somewhat. Both the Xubuntu and Lubuntu 12.04 images now use the non-pae kernel by default. You should however consider that Lubuntu 12.04 is only supported for 18 months, and Xubuntu 12.04 is supported for 3 years, whereas Ubuntu 12.04 LTS itself is supported for 5 years.

The Ubuntu, Kubuntu, Edubuntu, and Mythbuntu i386 images all now use the PAE kernel by default but, as previously mentioned, upgrades from either 10.04 or 11.10 will remain non-pae. Please refer to the [release notes]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes") or your distros official documentation regarding the proper upgrade methods and options.

And it's also quite possible to install 'ubuntu-desktop' on top of an Xubuntu or Lubuntu installation and still remain non-pae. Shortly after the final release of Precise I do plan on collaborating with the author of [Psychocats]("http://www.psychocats.net/ubuntu/index") on a full conversion method from either Xubuntu or Lubuntu to Ubuntu.

Remember when making a decision here that 12.04 is the end of the road for the non-pae kernel in Ubuntu so I'd personally think a 5 year LTS would be a good choice, but that's totally up to you, and the aforementioned non-pae mini.iso is a reasonable choice if you have a fast wired internet connection. You can read more about that in [this forum post]("http://ubuntuforums.org/showpost.php?p=11847760&postcount=103").

I should however also note that those with only wireless may (or may not) find that performing a CLI installation using an Lubuntu or Xubuntu alternate CD provides wireless modules not available on the mini.iso. To perform a CLI mode installation using an alternate CD you must press F4 and select CLI mode, then the rest of the installation is quite similar to performing a CLI install using the mini.iso.

There is now also an unofficial Ubuntu non-pae live image available here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/84](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/84)

---

### Post by VinDSL on 2012-04-16
The "classic" 32-bit mobo, in this machine, supports pae, but...

I often run mainline kernels (I'm currently running Linux 3.4rc2), and they still offer "generic" builds, e.g. non-pae.

So, if worse-comes-to-worse, you can always go that route...  ;)

---

### Post by 3rdalbum on 2012-04-16
I can't believe PAE and non-PAE code can't co-exist in the same kernel. Surely the real solution is for the same kernel to support PAE and non-PAE operation. It starts in non-PAE mode, checks if PAE is available, and if so automatically starts the PAE mode (unless the orrect boot option has been set from GRUB).

There must be a reason why it can't be done.

---

### Post by kansasnoob on 2012-04-16
Not to be rude, but the only opinions I'm concerned with are those regarding the accuracy and content of my post ;)

I based this on what I know. I deliberately left out some things, like a non-official Ubuntu Beta 1 build, because it's now too old.

I'll make changes if I can verify the **facts**.

---

### Post by nm_geo on 2012-04-16
> **kansasnoob said:**
> Not to be rude, but the only opinions I'm concerned with are those regarding the accuracy and content of my post ;)

I based this on what I know. I deliberately left out some things, like a non-official Ubuntu Beta 1 build, because it's now too old.

I'll make changes if I can verify the **facts**.

kansas I admit I have not been responding to the forum much recently. Iso-Testing has been my main focus and finding bugs.

I think your idea of write-up with [Psychocats]("http://www.psychocats.net/ubuntu/index") would be very handy as well.  

Since the non-pae kernel has been included in Lubuntu and Xubuntu precise,  I admit I have not put much thought into the issue.  However, having a write-up explaining how to change the DE to Ubuntu and maintaining a non-pae kernel would be very useful.

---

### Post by kansasnoob on 2012-04-16
> **nm_geo said:**
> kansas I admit I have not been responding to the forum much recently. Iso-Testing has been my main focus and finding bugs.

I think you idea of write-up with [Psychocats]("http://www.psychocats.net/ubuntu/index") would very handy as well.  

Since the non-pae kernel has been included in Lubuntu and Xubuntu precise,  I admit I have not put much thought into the issue.  However, having a write-up explaining how to change the DE to Ubuntu and maintaining a non-pae kernel would be very useful.

Trust me on the Psychocats thing:

[http://ubuntuforums.org/showpost.php?p=11828083&postcount=501](http://ubuntuforums.org/showpost.php?p=11828083&postcount=501)

Unless I drop dead I'll be trying to help aysiu ;)

---

### Post by nm_geo on 2012-04-16
> **kansasnoob said:**
> Trust me on the Psychocats thing:

[http://ubuntuforums.org/showpost.php?p=11828083&postcount=501](http://ubuntuforums.org/showpost.php?p=11828083&postcount=501)

Unless I drop dead I'll be trying to help aysiu ;)

I absolutely trust you kansas, and I have had Psychocats bookmarked for quite awhile.  Lots of good information there.

---

### Post by xyzzyman on 2012-04-16
> **3rdalbum said:**
> I can't believe PAE and non-PAE code can't co-exist in the same kernel. Surely the real solution is for the same kernel to support PAE and non-PAE operation. It starts in non-PAE mode, checks if PAE is available, and if so automatically starts the PAE mode (unless the orrect boot option has been set from GRUB).

There must be a reason why it can't be done.

It would double the size of the kernel which is already pretty bloated.

---

### Post by jerrylamos on 2012-04-17
> **xyzzyman said:**
> It would double the size of the kernel which is already pretty bloated.

Hey, what's the development resistance to the obvious solution??  Install has the capability of loading updates from the internet: "this CD image has -pae kernel, your hardware does not have the pae flag, do you want to load the non-pae kernel from the internet?"

???!

Jerry

p.s. My opinion, the kernel is MUCH smaller than many of the MASSIVE ubuntu updates.

---

### Post by kansasnoob on 2012-04-17
> **jerrylamos said:**
> Hey, what's the development resistance to the obvious solution??  Install has the capability of loading updates from the internet: "this CD image has -pae kernel, your hardware does not have the pae flag, do you want to load the non-pae kernel from the internet?"

???!

Jerry

p.s. My opinion, the kernel is MUCH smaller than many of the MASSIVE ubuntu updates.

And you'll now contact Canonical and express that opinion, huh?

Can we please just stick to the facts?

---

### Post by xyzzyman on 2012-04-17
> **jerrylamos said:**
> Hey, what's the development resistance to the obvious solution??  Install has the capability of loading updates from the internet: "this CD image has -pae kernel, your hardware does not have the pae flag, do you want to load the non-pae kernel from the internet?"

???!

Jerry

p.s. My opinion, the kernel is MUCH smaller than many of the MASSIVE ubuntu updates.

The size of updates aren't any more than RPM based distributions such as Fedora. When I referred to the kernel being bloated, I wasn't talking about download size but just the extreme amount of code in it, which even Linus has been harping on for 3-4 years now. 

[http://www.theregister.co.uk/2009/09/22/linus_torvalds_linux_bloated_huge/](http://www.theregister.co.uk/2009/09/22/linus_torvalds_linux_bloated_huge/)

All it takes is spending 20 minutes stripping down a kernel config for just your hardware to realize just how much is in the kernel.

As far as which kernel to pull in, that is best left to the alternate CD, as the Live CD doesn't install packages from the DEB's but instead expands out the live image onto the hard drive. Seeing as lubuntu and xubuntu are now shipping with non-pae, what is even left to discuss on this? Ubuntu held out longer than most everyone else on requiring PAE/NXbit support. Be mad at Intel for releasing hardware missing something that had been standard for almost a decade at that point.

---

### Post by jwbrase on 2012-04-17
> **xyzzyman said:**
> It would double the size of the kernel which is already pretty bloated.

It wouldn't double it, but it would increase it. If the possibility is not already implemented, though, it might be a fair bit of work to modify the kernel to be capable of it.

> **jerrylamos said:**
> Hey, what's the development resistance to the obvious solution??  Install has the capability of loading updates from the internet: "this CD image has -pae kernel, your hardware does not have the pae flag, do you want to load the non-pae kernel from the internet?"

If your processor doesn't support the kernel, you can't even boot, which means the installer doesn't even get to start, let alone download anything.

---

### Post by kansasnoob on 2012-04-17
> **xyzzyman said:**
> The size of updates aren't any more than RPM based distributions such as Fedora. When I referred to the kernel being bloated, I wasn't talking about download size but just the extreme amount of code in it, which even Linus has been harping on for 3-4 years now. 

[http://www.theregister.co.uk/2009/09/22/linus_torvalds_linux_bloated_huge/](http://www.theregister.co.uk/2009/09/22/linus_torvalds_linux_bloated_huge/)

All it takes is spending 20 minutes stripping down a kernel config for just your hardware to realize just how much is in the kernel.

As far as which kernel to pull in, that is best left to the alternate CD, as the Live CD doesn't install packages from the DEB's but instead expands out the live image onto the hard drive. Seeing as lubuntu and xubuntu are now shipping with non-pae, what is even left to discuss on this? Ubuntu held out longer than most everyone else on requiring PAE/NXbit support. Be mad at Intel for releasing hardware missing something that had been standard for almost a decade at that point.

You made me think of something here that I hadn't considered. The alternate CD's offer a CLI install if you press F4 at the boot screen.

So now I need to test either an Lubuntu or Xubuntu alternate image using the CLI mode just to see what happens. I haven't done such an install in probably 4 years so I'll have to be wearing my thinking cap :)

---

### Post by xyzzyman on 2012-04-17
The alternate CD's actually install from DEB's which is why they take so much longer as it extracts everything individually, so it might be possible to have all alternate CD's be non-pae and then just install the best kernel... It's my understanding that the alternate CD's are based off the stock debian installer so I you'd have to find someone to modify that code as I don't see Ubuntu doing that sort of work that won't be recognized upstream.

That also requires alot more testing which I don't see wanting to be added in any official capacity either.

---

### Post by kansasnoob on 2012-04-17
> **xyzzyman said:**
> The alternate CD's actually install from DEB's which is why they take so much longer as it extracts everything individually, so it might be possible to have all alternate CD's be non-pae and then just install the best kernel... It's my understanding that the alternate CD's are based off the stock debian installer so I you'd have to find someone to modify that code as I don't see Ubuntu doing that sort of work that won't be recognized upstream.

That also requires alot more testing which I don't see wanting to be added in any official capacity either.

We're not going to get Ubuntu to change anymore at this point. I just wonder if performing a CLI install with the alternate Lubuntu or Xubuntu discs would provide any actual benefit over using a mini.iso?

One of the biggest problems with the mini.iso's is the nearly absolute need for a wired connection. But I'll have to do some testing and check some options.

---

### Post by jerrylamos on 2012-04-17
> **kansasnoob said:**
> You made me think of something here that I hadn't considered. The alternate CD's offer a CLI install if you press F4 at the boot screen.

So now I need to test either an Lubuntu or Xubuntu alternate image using the CLI mode just to see what happens. I haven't done such an install in probably 4 years so I'll have to be wearing my thinking cap :)
Pushed F4 at Lubuntu alternate.  
Opened a little window with a choice of:

Normal
OEM Install (for manufacturers)
Install a command-line system

So I highlighted the Install a command-line system and
pushed space bar.  Nothing happens.
pushed enter key little window disappears.

Gave up, now doing "check disk for defects".  Oops, failed at 50%.  Only the 2nd time this R/W has been used.

Jerry

---

### Post by xyzzyman on 2012-04-17
> **kansasnoob said:**
> We're not going to get Ubuntu to change anymore at this point. I just wonder if performing a CLI install with the alternate Lubuntu or Xubuntu discs would provide any actual benefit over using a mini.iso?

One of the biggest problems with the mini.iso's is the nearly absolute need for a wired connection. But I'll have to do some testing and check some options.

You can't connect to wifi at the CLI like you can while installing arch linux?

---

### Post by kansasnoob on 2012-04-18
> **xyzzyman said:**
> You can't connect to wifi at the CLI like you can while installing arch linux?

Not at all easily with the mini.iso, but I'm wondering about CLI installs with an alternate image :confused:

I need to do some testing, but I think it's conceivable that the initial CLI installation from an alternate image can be completed with no connection at all ......... I can try that by just disconnecting my ethernet cable.

Then once that step is complete it may be possible to install 'ubuntu-desktop' from an existing Ubuntu image (or even an "apt-on-cd" created for that purpose).

I just hadn't even thought about the CLI option in the alternate images, I last used it during probably Gutsy or Hardy when I was trying some super-lite builds on ancient hardware.

---

### Post by kansasnoob on 2012-04-18
Well, I was wrong about being able to use the alt image with no connection. Regardless I'm performing some additional tests with the Lubuntu i386 20120417 alt image since I burned one :)

But regardless of whether an alt image or a mini.iso is used to complete a CLI install I do know it's possible to install packages using a CD (or USB). In that regard it gets to be like old-school Debian installation, but it's not my intention to write an entire installation guide ;)

---

### Post by kansasnoob on 2012-04-18
Oh, I did add a brief mention of that in my OP. If, as intended, I copy that to the install & upgrade section of the forums I'll subscribe to that thread so I can provide additional help as requested.

---

### Post by Irihapeti on 2012-04-19
> **kansasnoob said:**
> Well, I was wrong about being able to use the alt image with no connection.

Not quite sure which alt image you're referring to, but it's definitely possible with the Xubuntu one.

---

### Post by kansasnoob on 2012-04-19
> **Irihapeti said:**
> Not quite sure which alt image you're referring to, but it's definitely possible with the Xubuntu one.

I was using an Lubuntu alternate image. Do the Xubuntu alternate images work with no connection?

I know the live images will (or should) work with no connection.

I'd actually forgotten earlier that the alternate images offer a CLI install and then a light bulb went on.

That said I'm quite sure that I have a serious bit of senility setting in :(

That's not a joke!

---

### Post by Irihapeti on 2012-04-19
Xubuntu alternate images definitely work without an internet connection. The machine I tested on has no wireless card and I disconnected the ethernet cable.

Interestingly, when I booted into the install and ran "uname -a", it reported itself as "Ubuntu" (not Xubuntu), with the non-pae kernel.

Back in the days when I had limited bandwidth, I had various tricks to minimise downloads, and using the alternate CD w/o a net connection was one of them. (I have some other tricks as well, but they may not be beginner-friendly.)

> **kansasnoob said:**
> 

That said I'm quite sure that I have a serious bit of senility setting in :(

That's not a joke!

Before you jump to that conclusion, consider that stress can do this to people. I've seen many people who've not realised how much stress can mess up cognitive functioning. E.g. when my mother died late last year, I found myself forgetting all sorts of things, and losing my motivation as well. (I'm not saying this to seek sympathy, but to illustrate a point. The same thing happened to a friend of mine whose father died at about the same time.)

All the beta testing, plus all the weather-related stuff in your region, could add up to a fairly high stress load.

I hope that's a bit reassuring - it's meant to be.

---

### Post by kansasnoob on 2012-04-19
> **Irihapeti said:**
> Xubuntu alternate images definitely work without an internet connection. The machine I tested on has no wireless card and I disconnected the ethernet cable.

Interestingly, when I booted into the install and ran "uname -a", it reported itself as "Ubuntu" (not Xubuntu), with the non-pae kernel.

Back in the days when I had limited bandwidth, I had various tricks to minimise downloads, and using the alternate CD w/o a net connection was one of them. (I have some other tricks as well, but they may not be beginner-friendly.)



Before you jump to that conclusion, consider that stress can do this to people. I've seen many people who've not realised how much stress can mess up cognitive functioning. E.g. when my mother died late last year, I found myself forgetting all sorts of things, and losing my motivation as well. (I'm not saying this to seek sympathy, but to illustrate a point. The same thing happened to a friend of mine whose father died at about the same time.)

All the beta testing, plus all the weather-related stuff in your region, could add up to a fairly high stress load.

I hope that's a bit reassuring - it's meant to be.

Regarding the senility I've been tested. A couple of years after having meningo-encephalitis in 2001 I was diagnosed with mild neurocognitive disorder. I just got the results of my latest testing and it's now dementia :(

So, when I start running naked through the forums you'll know why :lolflag:

---

### Post by Irihapeti on 2012-04-19
> **kansasnoob said:**
> Regarding the senility I've been tested. A couple of years after having meningo-encephalitis in 2001 I was diagnosed with mild neurocognitive disorder. I just got the results of my latest testing and it's now dementia :(

I am  soooooooooo sorry to hear that.... :sad: 

(Somehow that seems so inadequate. But anything else I can think of sounds like a platitude of the worst kind.)

---

### Post by patricearnal on 2012-04-21
Many thanks for your mini.iso method of installation.
I have jus a regret regaring Canonical's USB creator : it did not recognize it as a valid system ISO, so I had to go to a Microsoft machine to create a bootable USB

---

### Post by jerrylamos on 2012-04-21
> **kansasnoob said:**
> And you'll now contact Canonical and express that opinion, huh?

Can we please just stick to the facts?
Fact, Precise won't install on my Thinkpad R31, fails in the copy step, on Lubuntu, Xubuntu, Ubuntu.  Bugs written.  That's a way to contact Canonical.  

Fact, another partition on the R31 has Lubuntu Precise Alpha running - thousands of updates by now, a bit sluggish.

Fact, Linux Mint LXDE just installed like a breeze on the R31 and is running fine, nice and fast for a 1 GHz 512 MB.

Jerry

Fact, by the way, this is a bit off topic since the R31 has a pae flag.  I run generic LXDE on it because it's a lightweight desktop.  The R31 will run ubuntu Unity-2D generic-pae slowly.  Not an option for me.

---

### Post by bubbajunk on 2012-04-22
I am one of those out of luck chaps that has a Thinkpad T42 with a Pentium M without PAE support. When I create a Live CD on my flash drive (Live USB) with the Precise ISO (from daily build 4/20), I get the dreaded "the following features not present on the CPU: pae. Unable to boot" message. That's why I filed the bug report #930447. 

I finally got around to trying to figure out how to boot an iso file from the hard drive. I used the daily build from Friday, 4/20, added the following menu entry to the 40_custom file, and ran sudo update-grub. After rebooting, entering the grub menu and selecting the new entry, guess what. It booted just fine and uname -a showed the pae kernel. 

So I'm totally confused. Why do I get the "no pae" error using the same iso to create a Live USB, but the same iso boots fine from the hard drive. I don't get it. How can that be, how can it run on my Pentium M that doesn't support pae? More importantly how do I get the live USB to act the same way as booting the iso from the hard drive? 

menuentry "Pangolin Daily Build ISO" {
set isofile="/home/bubba/downloads/precise-desktop-i386.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject splash
initrd (loop)/casper/initrd.lz
}

---

### Post by xyzzyman on 2012-04-22
I believe when you use casper to boot to RAM from an ISO it skips ahead further in the kernel boot process than booting fresh. Which is why on alot of systems it goes straight to live cd mode instead of giving you the option to install or 'try live mode'.

---

### Post by kansasnoob on 2012-04-22
> **bubbajunk said:**
> I am one of those out of luck chaps that has a Thinkpad T42 with a Pentium M without PAE support. When I create a Live CD on my flash drive (Live USB) with the Precise ISO (from daily build 4/20), I get the dreaded "the following features not present on the CPU: pae. Unable to boot" message. That's why I filed the bug report #930447. 

I finally got around to trying to figure out how to boot an iso file from the hard drive. I used the daily build from Friday, 4/20, added the following menu entry to the 40_custom file, and ran sudo update-grub. After rebooting, entering the grub menu and selecting the new entry, guess what. It booted just fine and uname -a showed the pae kernel. 

So I'm totally confused. Why do I get the "no pae" error using the same iso to create a Live USB, but the same iso boots fine from the hard drive. I don't get it. How can that be, how can it run on my Pentium M that doesn't support pae? More importantly how do I get the live USB to act the same way as booting the iso from the hard drive? 

menuentry "Pangolin Daily Build ISO" {
set isofile="/home/bubba/downloads/precise-desktop-i386.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject splash
initrd (loop)/casper/initrd.lz
}

This sounds very much like what Jerry Lamos has encountered and I'm pretty sure he also boots the isos using grub ............. but I'm totally clueless as to why or how it works :confused:

---

### Post by kansasnoob on 2012-04-22
Something that would be helpful:

Since bubbajunk has reported the same results as jerrylamos using grub2 to boot an iso it would be great if one of you would do a how-to and I could add that link to my post :D

Just as I did, it's fine to use existing links and add only what you feel is necessary beyond that. Hopefully we're all here to help each other.

---

### Post by Trespasser on 2012-04-22
Actually, Gnome Fallback really isn't that bad as a choice other than Unity. If I had a better menu to use, like gnome-main-menu (slab) or Gnomenu, and a window-list applet like talika or dockbarx, I'd be quite satisfied.

As far as that non-pae thing goes, I'm hoping David Henningsson will come through for us and release a Final 32bit version shortly after 12.04 goes live this coming Thursday.

BTW, I have a Sony Vaio S360 non-pae laptop (1.7 ghz, 1 gig ram) that I still use...so I'm affected by this silly decision to stop supporting older hardware. The least Ubuntu could do, IMHO, would be to offer a non-pae version as a separate download.

Later...

---

### Post by kansasnoob on 2012-04-22
> **Trespasser said:**
> Actually, Gnome Fallback really isn't that bad as a choice other than Unity. If I had a better menu to use, like gnome-main-menu (slab) or Gnomenu, and a window-list applet like talika or dockbarx, I'd be quite satisfied.

As far as that non-pae thing goes, I'm hoping David Henningsson will come through for us and release a Final 32bit version shortly after 12.04 goes live this coming Thursday.

BTW, I have a Sony Vaio S360 non-pae laptop (1.7 ghz, 1 gig ram) that I still use...so I'm affected by this silly decision to stop supporting older hardware. The least Ubuntu could do, IMHO, would be to offer a non-pae version as a separate download.

Later...

Regarding the "gnome-main-menu (slab) or Gnomenu, and a window-list applet like talika or dockbarx" thing you might enjoy this:

[http://ubuntuforums.org/showpost.php?p=11835822&postcount=389](http://ubuntuforums.org/showpost.php?p=11835822&postcount=389)

It's based on my Oneiric guide:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

I happen to like Unity on screens smaller than 19" but sometimes only a classic menu will do :)

---

### Post by cariboo on 2012-04-22
I jailed 3 very off topic posts.

---

### Post by jerrylamos on 2012-04-22
> **kansasnoob said:**
> Something that would be helpful:

Since bubbajunk has reported the same results as jerrylamos using grub2 to boot an iso it would be great if one of you would do a how-to and I could add that link to my post :D

Just as I did, it's fine to use existing links and add only what you feel is necessary beyond that. Hopefully we're all here to help each other.
Here's what I use successfully (most of the time, this is a testing forum!)

zsync a ubuntu  iso or download it into a handy directory.  I use either / or /iso on some partition

In times past, there have been problems if there were two .iso of the same ubuntu in the partition even in different folders, so don't do that.  Just rename the .iso you're not using.

Prepare a target partition with gparted.  I don't trust "unstable" ubuntu install partitioning - let someone else test that.

Make a 40_custom file as follows, putting in your chosen partition and folder here it's /iso on /dev/sda which is hd(0,1) to grub:
```

sudo gedit /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
menuentry "Pangolin ISO sda1 /iso" {
set isofile="/iso/precise-desktop-i386.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```
save it then just in case it's not marked executable
sudo chmod 777 /etc/grub.d/40_custom 
sudo update-grub
to whatever hard disk boots first:
sudo grub-install /dev/sda
reboot and choose the entry you made from grub
For me boots faster than USB and a LOT faster than CD
You can run live for a while if you like, then do a 
df
to see where the isofile is mounted, then in this example
sudo umount -r -l /dev/sda
best umount any other /dev partitions you've been using, and then select install.

Testing I do a LOT of installs to flush out bugs and I've got 3 laptops, a netbook, and a tower of varying ages so that's even more installs.

Enjoy.

Jerry

---

### Post by xyzzyman on 2012-04-23
Does it boot straight to the live environment or is it asking whether you want to try ubuntu or install it?

---

### Post by EgoGratis on 2012-04-23
If somebody ask me in the future what to do, because he/she can't install Ubuntu 12.04 because of PAE what is the best option to get Ubuntu 12.04 installed? Install Ubuntu 11.10 and then upgrade to Ubuntu 12.04? End result would be Ubuntu 12.04 without PAE and available kernel upgrades without PAE would still be available? This is still true?

---

### Post by Irihapeti on 2012-04-23
> If somebody ask me in the future what to do, because he/she can't install Ubuntu 12.04 because of PAE what is the best option to get Ubuntu 12.04 installed? Install Ubuntu 11.10 and then upgrade to Ubuntu 12.04? End result would be Ubuntu 12.04 without PAE and available kernel upgrades without PAE would still be available? This is still true? 

This option ought to work, especially if the upgrade is done straight away, before customising.

A trick I tried yesterday:
Do a command line install from the Xubuntu alternate CD. This gives a basic system with no graphics and with a non-pae kernel.

Then reboot and login and run the following commands:
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

Reboot again, and you have a standard Ubuntu install with a non-pae kernel.

---

### Post by kansasnoob on 2012-04-23
> **Irihapeti said:**
> This option ought to work, especially if the upgrade is done straight away, before customising.

A trick I tried yesterday:
Do a command line install from the Xubuntu alternate CD. This gives a basic system with no graphics and with a non-pae kernel.

Then reboot and login and run the following commands:
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

Reboot again, and you have a standard Ubuntu install with a non-pae kernel.

+1! I hadn't finished testing yet but while iso-testing I checked to be sure CLI installs worked with the Lubuntu alt image and all seemed well :D

And I'd hope that the alt images have better wireless support than the mini.iso, but I have no way of testing for that.

---

### Post by Irihapeti on 2012-04-23
The alternate CD recognises the wireless on my EeePC 900, but I've not tried installing that way - mainly because I've got a 63 character password that I don't trust myself to type correctly!

---

### Post by EgoGratis on 2012-04-23
Thanks for the answer.

---

### Post by kansasnoob on 2012-04-23
> **Irihapeti said:**
> The alternate CD recognises the wireless on my EeePC 900, but I've not tried installing that way - mainly because I've got a 63 character password that I don't trust myself to type correctly!

I hardly trust myself not to put my drawers on backwards :lolflag:

---

### Post by VinDSL on 2012-04-23
> **kansasnoob said:**
> I hardly trust myself not to put my drawers on backwards :lolflag:
I thought I was the only one that did that...  :D

Ever get both legs in the same side?!?!?

---

### Post by Irihapeti on 2012-04-23
> **VinDSL said:**
> 
Ever get both legs in the same side?!?!?

One of my brothers did that when he was a little kid. We gave him a very hard time about it... poor kid!

---

