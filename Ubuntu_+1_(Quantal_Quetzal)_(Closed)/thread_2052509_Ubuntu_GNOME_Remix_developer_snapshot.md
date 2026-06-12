---
title: "Ubuntu GNOME Remix developer snapshot"
date: 2012-09-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-09-03
Yesterday Jeremy Bicha made the first alpha Ubuntu GNOME Remix 12.10 images available via torrent:

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes)

The MD5SUM's are here:

[http://people.ubuntu.com/~jbicha/gnomebuntu/MD5SUMS](http://people.ubuntu.com/~jbicha/gnomebuntu/MD5SUMS)

Remember:

> The Quantal Quetzal Alpha Release of Ubuntu GNOME Remix 12.10 is a developer snapshot to give you a **very early glance** at the next version of Ubuntu GNOME Remix. 

I thought it'd be helpful to have a thread specifically dedicated to testing these images, have fun :D

**[COLOR="Red"]Update[/COLOR]**: Jeremy posted some notes here:

[http://ubuntuforums.org/showpost.php?p=12224136&postcount=53](http://ubuntuforums.org/showpost.php?p=12224136&postcount=53)

Among those is a link to the new mailing list:

[https://lists.launchpad.net/ubuntu-gnome/](https://lists.launchpad.net/ubuntu-gnome/)

I suspect that newer versions of the GNOME Remix images will be announced there :D

**[COLOR="Red"]Update #2[/COLOR]**:

Something worth taking note of at the mailing list:

[https://lists.launchpad.net/ubuntu-gnome/msg00002.html](https://lists.launchpad.net/ubuntu-gnome/msg00002.html)

> It's a bit tricky to install the Ubuntu Gnome Remix 20120902, but not
impossible.
Here is how I did:

   - Boot the live CD / USB into a live session
   - Launch a Terminal and use the following commands:
   - sudo apt-get update
   - sudo apt-get upgrade ubiquity

Now you can proceed with your installation routine.

If you, like me, use the manual partitioner, please be sure you install the
boot loader on your hard drive (sda) , ubiquity likes to install it to your
USB-drive, a known bug:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418)

**New Info**

Kansasnoob, asked me to edit this post, but I'll just add his new info here:

Jeremy Bicha recently announced ongoing development of Ubuntu GNOME Remix 12.10 which will hopefully become an official Ubuntu flavor at some point in time.

The project is currently at Alpha 2 for the Quantal cycle:

[https://wiki.ubuntu.com/UbuntuGNOME/...2FReleaseNotes](https://wiki.ubuntu.com/UbuntuGNOME/...2FReleaseNotes)

And there is a mailing list that I strongly suggest subscribing to if you're interested in the project:

[https://lists.launchpad.net/ubuntu-gnome/](https://lists.launchpad.net/ubuntu-gnome/)

And maybe since the release notes don't include md5sum's we should include a link to this post:

[http://ubuntuforums.org/showpost.php...4&postcount=82](http://ubuntuforums.org/showpost.php...4&postcount=82)

---

### Post by sammiev on 2012-09-03
Thanks for the links. ):P

---

### Post by sgage on 2012-09-03
I decided to give it a try. No go. First of all, I had to boot the installer with the nomodeset option to get it to boot intelligibly. The first couple of screens were more or less the usual. When it got to the screen to select where to install, nothing really worked. If I picked “something else” the way I usually do, the partitioner just crashed. If I picked “install alongside Windows”, and then went to select the drive to install on, everything froze. So that’s as far as I got – I’ll try again next time.

---

### Post by kansasnoob on 2012-09-03
> **sgage said:**
> I decided to give it a try. No go. First of all, I had to boot the installer with the nomodeset option to get it to boot intelligibly. The first couple of screens were more or less the usual. When it got to the screen to select where to install, nothing really worked. If I picked “something else” the way I usually do, the partitioner just crashed. If I picked “install alongside Windows”, and then went to select the drive to install on, everything froze. So that’s as far as I got – I’ll try again next time.

There is no doubt since this is based solely on the Ubuntu repos that any bug that exists in Ubuntu will also exist in this ;)

And I don't expect Quantal Beta 1 to be anywhere near stable :(

The last image I had work even half-way decent was August 15th. But I've seen the devs pull off some truly impossible stuff in the past :lolflag:

---

### Post by sgage on 2012-09-03
> **kansasnoob said:**
> There is no doubt since this is based solely on the Ubuntu repos that any bug that exists in Ubuntu will also exist in this ;)

And I don't expect Quantal Beta 1 to be anywhere near stable :(

The last image I had work even half-way decent was August 15th. But I've seen the devs pull off some truly impossible stuff in the past :lolflag:

It HAS been sometimes amazing how things come together at the last minute!

I thought there was a workaround for the partitioner crash (this behavior is nothing new), but I can't for the life of me remember what it was. Oh well!

---

### Post by mc4man on 2012-09-03
We'll see about that that.. (in regards to the live iso's
Last night was actually able to once get the GNOME Remix  to boot to the live session without nomodeset (going adv. options > enter > enter

Today back to garbage screens unless using nomodeset. The issue with nomodeset here is it goes to a fallback live session & the installer fails.
These problems are also seen on the the Ubuntu live images since Aug. 15 -17 on a decent amount of hardware (nvidia here), the current Ubuntu position seems to be - 
use nomodeset or don't use 12.10

---

### Post by stoneguy on 2012-09-03
Today must be one of my lucky days. I actually got into into the system in a VM, loaded FF and TB and a few other necessities. Couple of stumbling blocks along the way (which were noted in Launchpad). Hope these somehow get to Jeremy - right now he's probably the only one who'd be looking at this version's problems. Would be nice to settle on a name so that there could be a version to report against...

I too am a bit nervous about the readiness of QQBeta1. 4 builds during the same 24-hour period this close to release makes me a bit queasy.

---

### Post by ventrical on 2012-09-03
> **sgage said:**
> It HAS been sometimes amazing how things come together at the last minute!

I thought there was a workaround for the partitioner crash (this behavior is nothing new), but I can't for the life of me remember what it was. Oh well!


The workaround I used for Precise was that I had to boot into live, then I had to choose the Installer from the Unity sidebar panel for it to install correctly .  Is there a live option for gnome?

---

### Post by stoneguy on 2012-09-03
> **ventrical said:**
> Is there a live option for gnome?

Yes. Before building a VDI, it's a good way to find out whether there's even a snowball's chance of things working.

---

### Post by sgage on 2012-09-03
> **ventrical said:**
> The workaround I used for Precise was that I had to boot into live, then I had to choose the Installer from the Unity sidebar panel for it to install correctly .  Is there a live option for gnome?

Ah yes, I vaguely remembered something like that, so I tried something similar. The problem is, the only way I can boot to the live desktop (or straight to the installer) is by using the modeset option. That forces Gnome into a fallback session. I found the installer in the application menus, but it didn't work from there, either. :(

---

### Post by mc4man on 2012-09-03
Na

---

### Post by Stinger on 2012-09-03
> **sgage said:**
>  When it got to the screen to select where to install, nothing really worked. If I picked “something else” the way I usually do, the partitioner just crashed.

I tried it to same bug as you and many others
[Bug #1044545]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1044545")

Seems to be fixed in the package ubiquity - 2.11.27
If we are lucky Jeremy will soon release another image that we'll be able to install.
Cheers !

---

### Post by Stinger on 2012-09-03
I'll try to manually install [ubiquity 2.11.28]("https://launchpad.net/ubuntu/quantal/amd64/ubiquity/2.11.28") after booting the live cd and report back.

---

### Post by sgage on 2012-09-03
> **Stinger said:**
> I'll try to manually install [ubiquity 2.11.28]("https://launchpad.net/ubuntu/quantal/amd64/ubiquity/2.11.28") after booting the live cd and report back.

Yes, by all means do! I'd like to see this thing really work...

---

### Post by Stinger on 2012-09-03
Sorry but it won't install, it gives this error:
```
GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._pk_5ftransaction_5ferror.
Code4: SimulateInstallFiles not supported by backend
```

So I guess we'll just have to wait.

---

### Post by sgage on 2012-09-03
> **Stinger said:**
> Sorry but it won't install, it gives this error:
```
GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._pk_5ftransaction_5ferror.
Code4: SimulateInstallFiles not supported by backend
```

So I guess we'll just have to wait.

I've gotten pretty good at waiting. :KS

---

### Post by mc4man on 2012-09-03
installs here so will give an install a try (still having to use the bs nomodest
```

Setting up ubiquity-ubuntu-artwork (2.11.28) ...
Setting up ubiquity-frontend-gtk (2.11.28) ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up ubiquity (2.11.28) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
```

---

### Post by Stinger on 2012-09-03
OK I Got it working now :D
Did this from a terminal from the live CD:
```
sudo apt-get update
```
and then:
```
sudo apt-get upgrade ubiquity
```

It will upgrade the following packages:
caribou gir1.2-caribou-1.0 gir1.2-messagingmenu-1.0 indicator-messages
  indicator-session libcaribou-common libcaribou0 libmessaging-menu0
  printer-driver-c2esp python-cupshelpers system-config-printer-common
  system-config-printer-udev ubiquity ubiquity-frontend-gtk
  ubiquity-ubuntu-artwork.

I'm posting this from my Ubuntu Gnome Remix installation. :guitar:

---

### Post by sgage on 2012-09-03
> **Stinger said:**
> OK I Got it working now :D
Did this from a terminal from the live CD:
```
sudo apt-get update
```
and then:
```
sudo apt-get upgrade ubiquity
```

It will upgrade the following packages:
caribou gir1.2-caribou-1.0 gir1.2-messagingmenu-1.0 indicator-messages
  indicator-session libcaribou-common libcaribou0 libmessaging-menu0
  printer-driver-c2esp python-cupshelpers system-config-printer-common
  system-config-printer-udev ubiquity ubiquity-frontend-gtk
  ubiquity-ubuntu-artwork.

I'm posting this from my Ubuntu Gnome Remix installation. :guitar:

Very cool! I will give it try tomorrow...

---

### Post by mc4man on 2012-09-03
Install went ok here also though (maybe from nomodeset?
The installer window is black with text that's hard to see.

From try me there will be no install icon because of the default of nautilus not managing the desktop - no big deal to find though

generically - the installer defaults  to installing grub on the usb drive - nice

Don't know this default web browser at all - don't think I want to..

Going to put in the current .91 naut, new GS, totem, Rb, glib, gstreamer, ect. & see how that works.

Edit; getting current only took a few min., works pretty well, need a better theme as naut looks blah

---

### Post by Stinger on 2012-09-03
> **mc4man said:**
> 
generically - the installer defaults  to installing grub on the usb drive - nice
Yeah I know Precise does that too ;)

> Going to put in the current .91 naut, new GS, totem, Rb, glib, gstreamer, ect. & see how that works.
Please report back. I'm currently struggeling with package-kit,  would have been nice to have synaptic untill package-kit can take over.

---

### Post by jerrylamos on 2012-09-03
Ubiquity crashed - remix live, install to USB, manual partition, gets to selecting which partition and Ubiquity crashes.  Tried 3 times.  

Not successful on getting wireless WPA connected so I couldn't update nor could I post an apport.

I'm on the remix mailing list and will keep listening.

---

### Post by mc4man on 2012-09-03
> **Stinger said:**
> Yeah I know Precise does that too ;)


Please report back. I'm currently struggeling with package-kit,  would have been nice to have synaptic untill package-kit can take over.
Well I did install synaptic, just haven't found anything as good.

While in my Ubnutu install built some of the newer, for here just took the quick & easy
Added the ricotz staging & testing ppa's (staging for naut, testing the rest.
No issues to report, (yet),  though if doing so disable the lock screen or read up on current status (I don't use lock screen

Will have to see if any issue with the new glib as far as other sources (there was also a gtk* upgrade, did it though didn't look at & not sure if needed 

Activities looks/works better - you'll see..
The new totem (Videos) looks good,  - dark themed though the rest isn't.
 I've never used GS much so have to look into avail. themes
(I wouldn't mind ambiance but have yet in my Ubuntu install figured out how to get the new device symbolic icons to be used in Ambiance - they fall back to 'folder-remote', the rest are fine.

As far a nautilus - Myself aren't quite as interested in pure as function so will rebuild & add back a few things

Open with on dir.  - easy & while survive from now to 3.6 release
Add an up(parent) button to toolbar - easy, &  will ..
Put back display of real owner - no big deal but easy, ect.
Have a list tree view - was easy, with commits of last couple of days has become hard though still doable - the nails are being pounded into the coffin.

The one thing I miss is quicklists, too bad GS doesn't support Desktop Actions in their launcher, so I may do something different there. (unless someone did an ext..

> ~$ gnome-shell --version
GNOME Shell 3.5.90
doug@doug-XPS-M1330:~$ nautilus --version
GNOME nautilus 3.5.90 #basically .91
doug@doug-XPS-M1330:~$ totem --version
totem 3.5.90

---

### Post by Stinger on 2012-09-03
Got it all together now.
Gnome3 ppa and ricoz testing ppa

Got some nice screenies from my working gnome 3.6 desktop :D

The Shell-extensions are not working yet.

---

### Post by ventrical on 2012-09-03
@jbicha

Seamless install here!  I thought it was suppossed to be gnome-classic but it's gnome-shell! :) It works just as good as it does on Fedora.

  There was not even one glitch during install.  A notice "press any key for advanced options" was the first thing I saw. I actually thought I was booting into my harddrive!

Congradulations!

---

### Post by ventrical on 2012-09-03
My system:

```


ventrical@ventrical-P4M266A-8237:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)
ventrical@ventrical-P4M266A-8237:~$ 

```

---

### Post by ventrical on 2012-09-03
Screenies here with my  Nokia:

Don't mind fuzzy images :)

  Just wanted to note to the flawlessness of the installation process. I hope they are listening at Canonical.

---

### Post by floydsp on 2012-09-03
Just wanted to add I did the update to nvidia last night and this morning did the live install(Did not use nomodest) booted just fine and installed without a glich..using it now:D

floydsp

---

### Post by kansasnoob on 2012-09-04
> generically - the installer defaults to installing grub on the usb drive - nice

That one smokes me too :mad:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418)

I've worn out a couple of hammers pounding away at that bug ](*,)

That just can't be impossible to fix!

---

### Post by Stinger on 2012-09-04
> **kansasnoob said:**
> That one smokes me too :mad:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418)

I've worn out a couple of hammers pounding away at that bug ](*,)

That just can't be impossible to fix!

As a workaround, use the manual partitioner, you can switch to install the bootloader to your harddrive ( sda ) from there.

---

### Post by jerrylamos on 2012-09-04
> **Stinger said:**
> As a workaround, use the manual partitioner, you can switch to install the bootloader to your harddrive ( sda ) from there.
Testing unstable development code I invariably use manual install.  There's a bunch of partitions of quantal and precise and archive of stuff I carry forth from install to install.

With relatively big (for me) hard drives I'm not about to let Ubiquity pick and choose risking trashing what I have installed already.

Somebody else can test all those lvm's and stuff.  Frankly, someone else can test the depths of Unity/Compiz.  I'm trying a variety of desktops.

I've gotten a glimpse of remix with live.  Ubiquity crashes when I select a partition.  And yes, you can pick the boot drive I pick the USB hard drive since that's where my shakiest new installs are, the more stable stuff (including Windoze...7) is on the hard drive.

---

### Post by sgage on 2012-09-04
> **Stinger said:**
> OK I Got it working now :D
Did this from a terminal from the live CD:
```
sudo apt-get update
```
and then:
```
sudo apt-get upgrade ubiquity
```

It will upgrade the following packages:
caribou gir1.2-caribou-1.0 gir1.2-messagingmenu-1.0 indicator-messages
  indicator-session libcaribou-common libcaribou0 libmessaging-menu0
  printer-driver-c2esp python-cupshelpers system-config-printer-common
  system-config-printer-udev ubiquity ubiquity-frontend-gtk
  ubiquity-ubuntu-artwork.

I'm posting this from my Ubuntu Gnome Remix installation. :guitar:

It worked for me just now! Coming to you from Ubuntu Gnome Remix! :KS

---

### Post by sgage on 2012-09-04
> **jerrylamos said:**
> Testing unstable development code I invariably use manual install.  There's a bunch of partitions of quantal and precise and archive of stuff I carry forth from install to install.

With relatively big (for me) hard drives I'm not about to let Ubiquity pick and choose risking trashing what I have installed already.

Somebody else can test all those lvm's and stuff.  Frankly, someone else can test the depths of Unity/Compiz.  I'm trying a variety of desktops.

I've gotten a glimpse of remix with live.  Ubiquity crashes when I select a partition.  And yes, you can pick the boot drive I pick the USB hard drive since that's where my shakiest new installs are, the more stable stuff (including Windoze...7) is on the hard drive.

Jerry, as Stinger pointed out, you can update Ubuiquity from the Live session. I had the exact same problem as you (partioner crashing). Upgraded Ubiquity, and it worked perfectly!

sudo apt-get update
sudo apt-get upgrade ubiquity

That's all it took!

---

### Post by Cypher2 on 2012-09-04
In regards to the 'pure gnome experience' discussion (Gnobuntu Thread), I do have to agree that it would be kind of irrelevant to provide all the effort, if in the long run, we do not end up with the real thing. KDE, LXDE, XFCE all beneficiate of such a privilege, which was most probably attributed later on in the dev cycle, but we must not let this project become a half-baked attempt at what a lot of fervent users were waiting for.

Can we argue with Canonical on how to fork the packaging tree for gnome and have the true default 'vanilla' be built and hosted for this? If the aim is to become an official spin-off, the attempt is worthwhile IMHO.

Who's with me on this?

Great work on the alpha btw!

---

### Post by sgage on 2012-09-04
First impressions of the Remix:

Perhaps make the plymouth screen and grub menu screens a different color ;)

I was surprised that Gnome Tweak Tool was not installed by default - perhaps it ought to be?

I see the overlay taskbar stuff is not installed (good!), but the appmenu stuff all is installed - perhaps it should not be? It is somewhat superfluous to a Gnome install.

Those are simply things I've noticed in about 15 minutes of using the thing. No doubt more things will come up, but things seem pretty solid. It is so refreshing to have that first boot come up into Gnome!

I think you're onto something, jbicha :KS

---

### Post by Cypher2 on 2012-09-04
> **sgage said:**
> First impressions of the Remix:

Perhaps make the plymouth screen and grub menu screens a different color ;)



Um, I had already spoken on the 'unification' of the color scheme to jbicha on the other thread. we can use the guidelines and the plymouth logo to 'melt' grub, plymouth, gdm and the desktop with the same background and logo placement. It would be lovely.

---

### Post by jbicha on 2012-09-04
For those of you who want even more bleeding edge, you can use the [script]("https://code.launchpad.net/~ubuntu-gnome-dev/+junk/iso-build-script") to build the remix yourself. It uses the latest Ubuntu nightly image to seed all of the files except for the live filesystem. It takes a few hours, more or less.

---

### Post by kansasnoob on 2012-09-04
> **Stinger said:**
> As a workaround, use the manual partitioner, you can switch to install the bootloader to your harddrive ( sda ) from there.

In deed. In the real world I always use the manual partitioning option, but for iso-testing I must also test the other installation options ;)

---

### Post by jbicha on 2012-09-04
> **sgage said:**
> First impressions of the Remix:
I see the overlay taskbar stuff is not installed (good!), but the  appmenu stuff all is installed - perhaps it should not be? It is  somewhat superfluous to a Gnome install.


That is intentional. The Remix also currently includes GNOME Classic. The indicators make GNOME Classic much more usable and they are what I believe the typical GNOME Classic user wants.

Although maybe we don't need indicator-appmenu since it's not enabled by default anyway.

---

### Post by Cypher2 on 2012-09-04
> **jbicha said:**
> That is intentional. The Remix also currently includes GNOME Classic. The indicators make GNOME Classic much more usable and they are what I believe the typical GNOME Classic user wants.

Although maybe we don't need indicator-appmenu since it's not enabled by default anyway.

Will the gnome-shell global menu package and extension system be available through repo?

---

### Post by mc4man on 2012-09-04
Curious about Web (epiphany) - is there supposed to be a view menu or anyway to set a home page, get a toolbar, ect.?

---

### Post by Cypher2 on 2012-09-04
> **mc4man said:**
> Curious about Web (epiphany) - is there supposed to be a view menu or anyway to set a home page, get a toolbar, ect.?

If I am not mistaken, it is still in very early 'stable' stage. There is lots left to implement to Epiphany for future releases... though it does boast some long awaited features such as native global menu and such.

---

### Post by sgage on 2012-09-04
Is there some way we can arrive at a single name for this effort? I've seen Gnomebuntu, Gnobuntu, Gubuntu, and Ubuntu Gnome Remix. I think we really ought to nip this in the bud and come up with a single name. I kinda like Gnobuntu myself, but whatever - let's see if we can agree on something...

---

### Post by Cypher2 on 2012-09-04
> **sgage said:**
> Is there some way we can arrive at a single name for this effort? I've seen Gnomebuntu, Gnobuntu, Gubuntu, and Ubuntu Gnome Remix. I think we really ought to nip this in the bud and come up with a single name. I kinda like Gnobuntu myself, but whatever - let's see if we can agree on something...

+1 - Ubuntu GSR (Gnome Shell Remix)

---

### Post by kansasnoob on 2012-09-04
> **sgage said:**
> Is there some way we can arrive at a single name for this effort? I've seen Gnomebuntu, Gnobuntu, Gubuntu, and Ubuntu Gnome Remix. I think we really ought to nip this in the bud and come up with a single name. I kinda like Gnobuntu myself, but whatever - let's see if we can agree on something...

My simple guess is Gubuntu ;)

But having followed Lubuntu's dev days before becoming "official" this could take a while.

I simply have a lot of faith in Jeremy Bicha and, if I recall correctly, even Sebastien Bacher may be on-board with this idea :)

---

### Post by Stinger on 2012-09-04
> **Cypher2 said:**
> +1 - Ubuntu GSR (Gnome Shell Remix)
I'm afraid that one is already taken ;) [Ubuntu GNOME Shell Remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/")

But "Ubuntu Gnome Remix" or short UbuntuGR or UGR is ok to use I think.

---

### Post by mc4man on 2012-09-04
After some time with both as supplied & then upgrading GS/gstreamer/totem, ect. 
Certainly like the newer GS better
Nautilus is fine 
The newer gstreamer fixes some issues Ubuntu/Debian will not address in 0.10
Totem (Videos) is better with the older version, totem-mozilla is broken even worse than 3.4.3

In the past have had no use for totem other than totem-mozilla though have found the grilo plugins interesting & useful.(there are certainly alt.'s for some of them
 So in that area grilo-0.2 is of no current use while 0.1 works fine,  0.2 looks like it will be very good at some point.

---

### Post by sgage on 2012-09-07
> **jbicha said:**
> For those of you who want even more bleeding edge, you can use the [script]("https://code.launchpad.net/~ubuntu-gnome-dev/+junk/iso-build-script") to build the remix yourself. It uses the latest Ubuntu nightly image to seed all of the files except for the live filesystem. It takes a few hours, more or less.

I was trying to make a go of this script, but it's not working properly. I end up with an iso file of about 108 MB. 

I installed the packages mentioned at the beginning of the script, so that's not it.

Do you have any tips for making this thing work? Or plans to make an installer from yesterdays Quantal Beta release?

---

### Post by jbicha on 2012-09-07
Yeah, the ISO's should be about 800 MB. I need a bit more information about what exactly you did.

Short instructions (likely leaving out some details)
Only needs to be done the first time
```

bzr branch lp:~ubuntu-gnome-dev/+junk/iso-build-script

```Do this every time
```

cd iso-build-script
bzr pull
./livecd-script.sh clean i386
./livecd-script.sh customize i386 ../Downloads/quantal-desktop-i386.iso

```Of course, the build process is a WIP; I did a build this morning that pulled in Unity  :shock: . That problem should be fixed now but I haven't done another rebuild yet. Each build takes quite a while.

The next scheduled release of the remix was Beta 2 later this month. I am considering doing another alpha though. Before I do that, I'm waiting on the next ubiquity release which should fix most of the installer theming problems and hopefully the manual mount point entry [bug]("http://pad.lv/1047275") as well. Also, Wednesday & Thursday were great days for stability; today's a bit rockier as beta freeze ended.

By the way, gnome-shell 3.5.91 is available in Ubuntu now.

---

### Post by ventrical on 2012-09-07
yep.. running 3.5.91 now !

 This is a great work. The only bug I can find is that the screens are sort of white, ie terminal, firefox .. etc.. how to I get colours or themes? Thanks.

---

### Post by Stinger on 2012-09-07
> **jbicha said:**
> 
By the way, gnome-shell 3.5.91 is available in Ubuntu now.

Great !
What about GDM, Nautilus and Gstreamer ?
Any good news ?

---

### Post by sgage on 2012-09-07
> **jbicha said:**
> Yeah, the ISO's should be about 800 MB. I need a bit more information about what exactly you did.

...

By the way, gnome-shell 3.5.91 is available in Ubuntu now.

I'll tell you exactly what I did - I got in a bit over my head :KS  I'll just wait until your next build.

Yes, I see 3.5.91 in the repos... guess I'll be losing my extensions for a while...

---

### Post by jbicha on 2012-09-07
> **Stinger said:**
> Great !
What about GDM, Nautilus and Gstreamer ?
Any good news ?

Lots of good news...

[LIST]
[*]GDM 3.5.91 arrived yesterday.
[*]Nautilus 3.5.91 should be in the PPA this weekend.
[*]Nothing significant has happened with gstreamer.
[*]There's a new mini-app named [gnome-clocks]("http://ubuntuforums.org/todoentiempo.wordpress.com/2012/08/18/gsoc-final-report-gnome-clocks") available. There's already a bugfix update for it which I plan to upload this weekend.
[*]I made gnome-tweak-tool a dependency of ubuntu-gnome-desktop. I mean if OpenSUSE is shipping it, why shouldn't we do so too?
[*]We have an IRC channel (#ubuntu-gnome) and a [mailing list]("https://lists.launchpad.net/ubuntu-gnome") but we need a QA team.
[/LIST]

---

### Post by sgage on 2012-09-07
> **jbicha said:**
> Lots of good news...

[LIST]
[*]GDM 3.5.91 arrived yesterday.
[*]Nautilus 3.5.91 should be in the PPA this weekend.
[*]Nothing significant has happened with gstreamer.
[*]There's a new mini-app named [gnome-clocks]("http://ubuntuforums.org/todoentiempo.wordpress.com/2012/08/18/gsoc-final-report-gnome-clocks") available. There's already a bugfix update for it which I plan to upload this weekend.
[*]I made gnome-tweak-tool a dependency of ubuntu-gnome-desktop. I mean if OpenSUSE is shipping it, why shouldn't we do so too?
[*]We have an IRC channel (#ubuntu-gnome) and a [mailing list]("https://lists.launchpad.net/ubuntu-gnome") but we need a QA team.
[/LIST]

GS 3.5.91 running very well here. I still have the 2 most important (to me) extensions working - icon overlays, and window animation disabled.

Yes, I think gnome-tweak-tool should be a dependency - good move.

---

### Post by mips on 2012-09-07
They should have guide on how to add this to a base install and I'' try it out.

---

### Post by jbicha on 2012-09-07
mips, you can install ubuntu-gnome-desktop if you want. It won't have quite the same effect as a fresh install though. Firefox will still be default and I think you'll still have Ambiance as your default theme for instance.

---

### Post by mips on 2012-09-07
> **jbicha said:**
> mips, you can install ubuntu-gnome-desktop if you want. It won't have quite the same effect as a fresh install though. Firefox will still be default and I think you'll still have Ambiance as your default theme for instance.

Surely they should have a meta packages where you can install everything that comes with it?

---

### Post by jbicha on 2012-09-07
Right, that's what ubuntu-gnome-desktop does but it won't remove Unity and Firefox and all of the other ubuntu-desktop dependencies.

---

### Post by Stinger on 2012-09-07
> **jbicha said:**
> Lots of good news...

[LIST]
[*]GDM 3.5.91 arrived yesterday.
[*]Nautilus 3.5.91 should be in the PPA this weekend.
[*]Nothing significant has happened with gstreamer.
[*]There's a new mini-app named [gnome-clocks]("http://ubuntuforums.org/todoentiempo.wordpress.com/2012/08/18/gsoc-final-report-gnome-clocks") available. There's already a bugfix update for it which I plan to upload this weekend.
[*]I made gnome-tweak-tool a dependency of ubuntu-gnome-desktop. I mean if OpenSUSE is shipping it, why shouldn't we do so too?
[*]We have an IRC channel (#ubuntu-gnome) and a [mailing list]("https://lists.launchpad.net/ubuntu-gnome") but we need a QA team.
[/LIST]
Ay ay Captain, all systems ready and go. 
LET'S PUT THIS GNOME INTO HYPERDRIVE :guitar:

Brilliant work !

BTW it's me posting at the mail list ;)

Psst. Jeremy.. You need to fix the link to [GNOME Clocks]("http://todoentiempo.wordpress.com/2012/08/18/gsoc-final-report-gnome-clocks/") :-$
Cheers !

---

### Post by kansasnoob on 2012-09-07
> **jbicha said:**
> Lots of good news...

[LIST]
[*]GDM 3.5.91 arrived yesterday.
[*]Nautilus 3.5.91 should be in the PPA this weekend.
[*]Nothing significant has happened with gstreamer.
[*]There's a new mini-app named [gnome-clocks]("http://ubuntuforums.org/todoentiempo.wordpress.com/2012/08/18/gsoc-final-report-gnome-clocks") available. There's already a bugfix update for it which I plan to upload this weekend.
[*]I made gnome-tweak-tool a dependency of ubuntu-gnome-desktop. I mean if OpenSUSE is shipping it, why shouldn't we do so too?
[*]We have an IRC channel (#ubuntu-gnome) and a [mailing list]("https://lists.launchpad.net/ubuntu-gnome") but we need a QA team.
[/LIST]

I made some changes to my OP:

[http://ubuntuforums.org/showpost.php?p=12214945&postcount=1](http://ubuntuforums.org/showpost.php?p=12214945&postcount=1)

Am I correct in assuming that you'll announce new builds on the mailing list?

Regardless I think all of the mods know they have my full permission to edit any of my posts w/o warning ;)

---

### Post by Mr.JJ on 2012-09-08
> **jbicha said:**
> We're splitting Ubuntu customizations into separate packages so that it's easier to get a purer GNOME for those that want it. 
 Is there any progress on this area? I see from Stinger's screenshots that the customisations remain in the system settings. Also, do we have 'ubuntu online accounts' installed by default or only the gnome one?   
Can someone comment on the organisation of packages etc., is there any separate packages for ubuntu customisations, yet? Did anyone try removing the ubuntu customisations? 
> **ventrical said:**
> It works just as good as it does on Fedora.
  Is it fast and smooth (with default graphics drivers)? If it is anywhere comparable to the fedora implementations, then this is great news. My internet connection do not allow me the luxury to download and test these images....

---

### Post by smartboyhw on 2012-09-08
> **jbicha said:**
> Lots of good news...

[LIST]
[*]GDM 3.5.91 arrived yesterday.
[*]Nautilus 3.5.91 should be in the PPA this weekend.
[*]Nothing significant has happened with gstreamer.
[*]There's a new mini-app named [gnome-clocks]("http://ubuntuforums.org/todoentiempo.wordpress.com/2012/08/18/gsoc-final-report-gnome-clocks") available. There's already a bugfix update for it which I plan to upload this weekend.
[*]I made gnome-tweak-tool a dependency of ubuntu-gnome-desktop. I mean if OpenSUSE is shipping it, why shouldn't we do so too?
[*]We have an IRC channel (#ubuntu-gnome) and a [mailing list]("https://lists.launchpad.net/ubuntu-gnome") but we need a QA team.
[/LIST]

Oh yeah get me in the QA Team:)

---

### Post by Stinger on 2012-09-08
I just tried to purge 'ppa:ricotz/testing', Totem/Videos is reverted back to version 3.4 and Gstreamer back to version 0.10 only.

[Gstreamer 1.0 is avaiable from 'Universe']("http://packages.ubuntu.com/search?keywords=gstreamer&searchon=names&suite=quantal&section=all") ( scroll down and you'll see it )

If I add 'ppa:ricotz/testing' I get Totem/Videos 3.6 and the new Gstreamer 1.0 ( from Universe ), but Gstreamer is not upgraded and therefore I have both Gstreamer 0.10 and Gstreamer 1.0 installed at the same time ( what a mess )
Any explanation to, why Gstreamer is not upgraded ? :confused: 

Would it be possible to make the 'ubuntu-gnome' meta package depend or allow upgrading to the new Gstreamer 1.0 ?
That would allow us to use Totem/Videos 3.6

---

### Post by mc4man on 2012-09-08
While may be better to inc. the 1.0 gstreamer as it fixes some things  it also appears to be broken in some area's atm.
In that case users should have a choice..

There is really no reason why you can't have both gstreamer0.10 & 1.0 installed, there is no particular conflict.
If you've installed the 3.[COLOR="Blue"]6[/COLOR] totem then it will use the 1.0 gstreamer packages, if you have 3.4 it will use the 0.10 as will any other source not built to use 1.0 that uses gstreamer.

Same would apply to Rb

---

### Post by mips on 2012-09-08
> **jbicha said:**
> Right, that's what ubuntu-gnome-desktop does but it won't remove Unity and Firefox and all of the other ubuntu-desktop dependencies.

I'm talking about a clean base/cli install so I wont have any of those components/clutter.

---

### Post by Stinger on 2012-09-08
> **mc4man said:**
> While may be better to inc. the 1.0 gstreamer as it fixes some things  it also appears to be broken in some area's atm.
In that case users should have a choice..

There is really no reason why you can't have both gstreamer0.10 & 1.0 installed, there is no particular conflict.
If you've installed the 3.[COLOR="Blue"]6[/COLOR] totem then it will use the 1.0 gstreamer packages, if you have 3.4 it will use the 0.10 as will any other source not built to use 1.0 that uses gstreamer.

Same would apply to Rb
I get it, we are in a transition to the newer Gstreamer and until all apps are build with Gstreamer 1.0 I'll have to install both versions.

Still it could be nice to have Totem/Videos 3.6 along with Nautilus 3.6 as stable versions in the ppa:gnome3-team/gnome3 ;)

---

### Post by mc4man on 2012-09-08
> **Stinger said:**
> I get it, we are in a transition to the newer Gstreamer and until all apps are build with Gstreamer 1.0 I'll have to install both versions.

Still it could be nice to have Totem/Videos 3.6 along with Nautilus 3.6 as stable versions in the ppa:gnome3-team/gnome3 ;)
I've no real idea how that ppa works but I'd assume it will have naut 3.6
As far as adding the 1.0 bad plugin, (or any other newer 1.0 package), the 3.6 totem, RB, ect.  no idea.

I do see that the ppa has added sound-juicer though it currently is somewhat flawed as it has no support for gstreamer presets
(& gnome lowered the built-in defaults to almost junk for mp3 & ogg
I still rip cd's but use rubyripper, still there may be some people...

Side note: at least here the current repo gnome-sushi does not work though local builds of 3.5.90 & the current bzr do (using the 1.0 libav plugin

---

### Post by Stinger on 2012-09-08
> **mc4man said:**
> 
I do see that the ppa has added sound-juicer though it currently is somewhat flawed as it has no support for gstreamer presets
(& gnome lowered the built-in defaults to almost junk for mp3 & ogg
I still rip cd's but use rubyripper, still there may be some people...

off topic
I rip CD's too but as you can see in my signature I use  [Asunder]("http://littlesvr.ca/asunder/"). It uses LAME for mp3 and [cdparanoia]("http://www.xiph.org/paranoia/") for reading, encodes in vbr too, and I'm a bit paranoid myself when it comes to CD-ripping ;)

---

### Post by Stinger on 2012-09-08
I'm having a strange behavior when launching Nautilus from the launcher, the 'timer' is spinning for a long time in the panel before it disappears and Nautilus seems a bit sluggish until it does.
When launching the command 'nautilus' from a terminal, Nautilus instantly springs into action without being sluggish.

I noticed that, in the menu, Nautilus is launched with the parameter %U, "nautilus %U", so I made my own launcher without the %U parameter. It works !

According to [the free desktop standards]("http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#exec-variables"):

> %U =     A list of URLs. Each URL is passed as a separate argument to the executable program. Local files may either be passed as file: URLs or as file path.

But I don't get why the %U-parameter is there in the first place ?
Anyone else plagued by this strange behavior ?

---

### Post by mc4man on 2012-09-08
> **Stinger said:**
> I'm having a strange behavior when launching Nautilus from the launcher, the 'timer' is spinning for a long time in the panel before it disappears and Nautilus seems a bit sluggish until it does.
When launching the command 'nautilus' from a terminal, Nautilus instantly springs into action without being sluggish.

I noticed that, in the menu, Nautilus is launched with the parameter %U, "nautilus %U", so I made my own launcher without the %U parameter. It works !

According to [the free desktop standards]("http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#exec-variables"):
Only seen here on the 1st use of nautilus 
But I don't get why the %U-parameter is there in the first place ?
Anyone else plagued by this strange behavior ?

Only seen here on the 1st use of nautilus from a fresh boot or log out/in and only if opening a large dir. like home. 
The amount of time spinning (working) would depend on the contents, (amount of)
So if I create a new user, login & open home it spins considerably less than the same on my main user.

After first use nautilus opens promptly no matter what the dir. size

---

### Post by shadedpixel on 2012-09-08
This looks interesting, Ill keep and eye on it. ;)

---

### Post by Cypher2 on 2012-09-09
Good work here. Though, not to seem negative and all but it seems you guys are working backwards on all the 'back to stock' dependency things. Again, why not start from a fresh ubuntu core image and build onto it, with GNOME only?

It works very well with a server image... and there obviously are the standard meta-packages which drag the required components into the install process.. so why not?

---

### Post by ventrical on 2012-09-09
> **Mr.JJ said:**
> Is there any progress on this area? I see from Stinger's screenshots that the customisations remain in the system settings. Also, do we have 'ubuntu online accounts' installed by default or only the gnome one?   
Can someone comment on the organisation of packages etc., is there any separate packages for ubuntu customisations, yet? Did anyone try removing the ubuntu customisations? 

  Is it fast and smooth (with default graphics drivers)? If it is anywhere comparable to the fedora implementations, then this is great news. My internet connection do not allow me the luxury to download and test these images....


 I've already done a full update. The .iso worked great from scratch. haven't had to adjust any settings. I admit I haven't tried it on a nvidia adpater yet. For the most part I  like UnityDE as a whole but I like to experiment to help others. This is a good idea for a singularity of GNOME .

---

### Post by cariboo on 2012-09-09
I tried installing it last night, and ran into two problems, the first was corrupted graphics, which was easy enough to fix by using nomodeset, the second problem was with the partition. I tried it twice, and both times it crashed while trying to create new partitions on empty space I created using gparted.

I'll try again after creating partitions before doing the installation.

At least now I can say I finally experienced some breakage during this cycle. :-D

---

### Post by sgage on 2012-09-09
> **cariboo907 said:**
> I tried installing it last night, and ran into two problems, the first was corrupted graphics, which was easy enough to fix by using nomodeset, the second problem was with the partition. I tried it twice, and both times it crashed while trying to create new partitions on empty space I created using gparted.

I'll try again after creating partitions before doing the installation.

At least now I can say I finally experienced some breakage during this cycle. :-D

After booting to a live desktop using nomodeset, try updating ubiquity from a command line.

Don't forget to 'sudo apt-get update' first, then upgrade ubitquity.

Then run the installer. This is what I had to do to get it to use "something else" in the partitioner. After that all was well...

---

### Post by Stinger on 2012-09-10
@cariboo907 (and others)
It's a bit tricky to install the Ubuntu Gnome Remix 20120902 because of a bug in ubiquity, but not impossible.
Seems to affect the manual partitioner but I would reccomend you do it in any case.

Here is how I did:
[LIST]
[*]Boot the live CD / USB into a live session
[*]Launch a Terminal and use the following commands:
[*]sudo apt-get update
[*]sudo apt-get upgrade ubiquity
[/LIST]
Now you can proceed with your installation routine.

If you, like me, use the manual partitioner, please be sure you install the boot loader on your hard drive (sda) , ubiquity likes to install it to your USB-drive, a known bug:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/987418)

---

### Post by neokod on 2012-09-11
EDIT: Fixed by removing the 2 others HardDrives !

Hello everybody !

Good works for this Gnome Ubuntu Remix, it's exactly what I need :D

I want to install it on my 2 x SSD in RAID-1 (Hardware, from the BIOS)

I known it's not supported yet with the Alpha release, and when I try this doesn't works (the installation of grub on the bootloader failed).

But, the solution explained, is to install first on one harddrive, and then to install the RAID-1.

Excepted this doesn't works for me, my BIOS delete all data on the both harddrive to create the RAID-1 volume.

So, I have tried to create the RAID-1 volume before, to launch the live version, and upgrade ubiquity to 2.11.31 but this doesn't solve the problem.

May be I need to install another packages ?

Any ideas to help me please ?

(I prefer to uses a hardware RAID1, to not waste bus bandwidth and CPU ressources with a software RAID1).

---

### Post by ventrical on 2012-09-12
Just updated again .. still working awesomely here.

---

### Post by smartboyhw on 2012-09-13
Now guys please follow jbicha's instructions in [http://ubuntuforums.org/showpost.php?p=12224048&postcount=49 ]("http://ubuntuforums.org/showpost.php?p=12224048&postcount=49")

Since the autologin issue has been fixed, the build is now in its best form.

I do recommend you all to build it using the newest daily build.

It now works perfectly and I absolutely like it. :)

---

### Post by sgage on 2012-09-13
> **smartboyhw said:**
> Now guys please follow jbicha's instructions in [http://ubuntuforums.org/showpost.php?p=12224048&postcount=49 ]("http://ubuntuforums.org/showpost.php?p=12224048&postcount=49")

Since the autologin issue has been fixed, the build is now in its best form.

I do recommend you all to build it using the newest daily build.

It now works perfectly and I absolutely like it. :)

Those instructions are not working. The bzr pull command doesn't seem to find anything...

---

### Post by smartboyhw on 2012-09-13
> **sgage said:**
> Those instructions are not working. The bzr pull command doesn't seem to find anything...
Did you install bzr?
It should be possible since I used it. Use the first command (the bzr branch first), download the daily build iso into the Downloads folder.

It may be possible that bzr pull doesn't have any new revisions, they will only update if jbicha or darkxst had added sth in it.

If you want I can provide the latest daily build to ya all.

---

### Post by smartboyhw on 2012-09-13
News updates for everybody:

Ubuntu GNOME Remix 12.10 (Quantal Quetzal) Alpha 2 is out!

Go to [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2) to find out about the details.

The download links are
64-bit: [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2?action=AttachFile&do=view&target=quantal-ubuntu-gnome-amd64-20120913.iso.torrent](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2?action=AttachFile&do=view&target=quantal-ubuntu-gnome-amd64-20120913.iso.torrent)
32-bit: [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2?action=AttachFile&do=view&target=quantal-ubuntu-gnome-i386-20120913.iso.torrent](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2?action=AttachFile&do=view&target=quantal-ubuntu-gnome-i386-20120913.iso.torrent)

MD5SUMS:
32-bit: a3fa2bfff9a65acec4d376b3b187f271
64-bit: b03d1db5859c3ae2b3f036ed51832a55

Thank you jbicha and darkxst.

Also I have added instructions in the Ubuntu Wiki on how to build the iso script. The link is
[https://wiki.ubuntu.com/UbuntuGNOME/ISOBuildScript](https://wiki.ubuntu.com/UbuntuGNOME/ISOBuildScript)

---

### Post by Stinger on 2012-09-13
@smartboyhw
Thank you for the info 
Downloading right now, will seed for a while. 
Happy testing all you faithful Gnome fans ;)

---

### Post by kansasnoob on 2012-09-13
> **smartboyhw said:**
> News updates for everybody:

Ubuntu GNOME Remix 12.10 (Quantal Quetzal) Alpha 2 is out!

Go to [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2) to find out about the details.

The download links are
64-bit: [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2?action=AttachFile&do=view&target=quantal-ubuntu-gnome-amd64-20120913.iso.torrent](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2?action=AttachFile&do=view&target=quantal-ubuntu-gnome-amd64-20120913.iso.torrent)
32-bit: [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2?action=AttachFile&do=view&target=quantal-ubuntu-gnome-i386-20120913.iso.torrent](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2?action=AttachFile&do=view&target=quantal-ubuntu-gnome-i386-20120913.iso.torrent)

MD5SUMS:
32-bit: a3fa2bfff9a65acec4d376b3b187f271
64-bit: b03d1db5859c3ae2b3f036ed51832a55

Thank you jbicha and darkxst.

Also I have added instructions in the Ubuntu Wiki on how to build the iso script. The link is
[https://wiki.ubuntu.com/UbuntuGNOME/ISOBuildScript](https://wiki.ubuntu.com/UbuntuGNOME/ISOBuildScript)

Thanks for the info. I see the release notes now include 2 additional download locations:

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2)

I'll ask one of the mods to edit my OP soon but I'm curious where you found the MD5SUM's?

BTW, you're doing great for only 14 :guitar:

I'm getting too old and tired to keep up with everything so it's reassuring to know that we're generating interest among younger *buntu enthusiasts :D

---

### Post by sgage on 2012-09-13
> **smartboyhw said:**
> Did you install bzr?
It should be possible since I used it. Use the first command (the bzr branch first), download the daily build iso into the Downloads folder.

It may be possible that bzr pull doesn't have any new revisions, they will only update if jbicha or darkxst had added sth in it.

If you want I can provide the latest daily build to ya all.

Yes, I had installed bzr, and the other packages that are listed in the beginning of the script.

Anyway, I don't know what I was doing wrong earlier, but it's working fine now. In fact, I made an install from my own build just now - works great!

I do still have to use nomodeset...

Other than that, the installation was very smooth.

---

### Post by smartboyhw on 2012-09-13
> **kansasnoob said:**
> Thanks for the info. I see the release notes now include 2 additional download locations:

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2)

I'll ask one of the mods to edit my OP soon but I'm curious where you found the MD5SUM's?

BTW, you're doing great for only 14 :guitar:

I'm getting too old and tired to keep up with everything so it's reassuring to know that we're generating interest among younger *buntu enthusiasts :D

Ah hum, I got it from jbicha through IRC lol....

Now I'm thinking about how to make a mirror myself...

Anyway jbicha decided to make his own mirror and that's great:)

I even thought if that the "Undefined video error" can ve solved and that more artwork can come in then that's Beta 1:)

---

### Post by Stinger on 2012-09-15
Reporting back from my **Ubuntu GNOME Remix 12.10Alpha2 20120913** install (installed yesterday).
First. The live CD/USB, once booted, has no option to power off or reboot the system, you have to do it from a terminal.
```
sudo poweroff 
or
sudo reboot
```
Se my screenshot from the live CD/USB.

The installer looks fine now (still missing the artwork) and the manual partitioner now installs the bootloader to my hard disc as default (sda).
When the installation routine is finished and I'm asked to reboot, nothing happens, I have to reboot from a terminal.
Once rebooted, the poweroff and reboot options are available from the GS-menu.
I have to change the software sources in the system settings to use the mainserver instead of the server from Denmark (it's not up to date)
I have added the &#8220;GNOME3 Team&#8221; ppa to get an upstream Gnome experience.

When the system is fully updated It's extremely fast an snappy :D

I am still struggeling with packagekit though it's getting better.
The main issues are:
[LIST]
[*]I get an error when I try to install a package manually (google-chrome).
[*]I cannot reinstall a package from package-kit.
[*]I cannot switch server from within package-kit (has to be done in software sources)
[*]I cannot re-size the UI or the update dialog, the are to big.
[/LIST]
Guess I'll have to file a bug against it soon.
Cheers !

PS.
Installed google-chrome with:
```
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

---

### Post by smartboyhw on 2012-09-15
> **Stinger said:**
> Reporting back from my **Ubuntu GNOME Remix 12.10Alpha2 20120913** install (installed yesterday).
First. The live CD/USB, once booted, has no option to power off or reboot the system, you have to do it from a terminal.
```
sudo poweroff 
or
sudo reboot
```Se my screenshot from the live CD/USB.

The installer looks fine now (still missing the artwork) and the manual partitioner now installs the bootloader to my hard disc as default (sda).
When the installation routine is finished and I'm asked to reboot, nothing happens, I have to reboot from a terminal.
Once rebooted, the poweroff and reboot options are available from the GS-menu.
I have to change the software sources in the system settings to use the mainserver instead of the server from Denmark (it's not up to date)
I have added the “GNOME3 Team” ppa to get an upstream Gnome experience.

When the system is fully updated It's extremely fast an snappy :D

I am still struggeling with packagekit though it's getting better.
The main issues are:
[LIST]
[*]I get an error when I try to install a package manually (google-chrome).
[*]I cannot reinstall a package from package-kit.
[*]I cannot switch server from within package-kit (has to be done in software sources)
[*]I cannot re-size the UI or the update dialog, the are to big.
[/LIST]
Guess I'll have to file a bug against it soon.
Cheers !

PS.
Installed google-chrome with:
```
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

Hmm weird...In my build (daily build 20120914 I DO get the shut down and restart buttons...
 Also weird that you can't reboot since I can after installation (at least I can shut down, but then in a VM Ubuntu (ALL distros) can't reboot)...

package-kit...Hmm... Dunno.

Good that you are happy:)

---

### Post by sgage on 2012-09-15
> **smartboyhw said:**
> Hmm weird...In my build (daily build 20120914 I DO get the shut down and restart buttons...
 Also weird that you can't reboot since I can after installation (at least I can shut down, but then in a VM Ubuntu (ALL distros) can't reboot)...

package-kit...Hmm... Dunno.

Good that you are happy:)

Even weirder... In MY daily build (20120914) I DON'T get the shutdown option after installation. :confused:

---

### Post by smartboyhw on 2012-09-15
> **sgage said:**
> Even weirder... In MY daily build (20120914) I DON'T get the shutdown option after installation. :confused:
OMG I am surprised!!!!!! Let me compile the new daily build (20120915) to try:)

EDIT: I do get ALL of the shutdown options in MY build compiled just now..

---

### Post by cariboo on 2012-09-15
Just to add my two bits, I did an install using the torrented iso yesterday, I'm just using it as the developer intended with only chromium-browser, mc and aptitude added, and I get the power-off selection in the menu.

---

### Post by Stinger on 2012-09-15
> **cariboo907 said:**
> Just to add my two bits, I did an install using the torrented iso yesterday, I'm just using it as the developer intended with only chromium-browser, mc and aptitude added, and I get the power-off selection in the menu.
Maybe Jeremy can shed some light on this odd behavior ? Seems to only affect some systems, mine included.
Haven't a clue where to look for the common denominator ?

---

### Post by sgage on 2012-09-15
> **Stinger said:**
> Maybe Jeremy can shed some light on this odd behavior ? Seems to only affect some systems, mine included.
Haven't a clue where to look for the common denominator ?

I think there might be a bit of confusion. When I say that "after the install", there is no shutdown item in the menu, I mean in the Live session. The installed system works just fine in that regard.

---

### Post by Stinger on 2012-09-15
Yes it's only the live session that's affected, once installed, shutdown is available again.

---

### Post by jbicha on 2012-09-15
Ok, we set the live session to disable log out which is what happens in the Unity live session. But it looks like that setting actually disables Power Off from the menu too. I reported a [GNOME bug]("https://bugzilla.gnome.org/show_bug.cgi?id=684118") explaining what we want. I guess we'll end up not using that setting so you'll still be able to log out, power off, and restart.

---

### Post by cariboo on 2012-09-15
If you select ***switch session***, on the login screen, there is a power icon in the upper right corner, that allows you to shutdown, or restart. This looks more like a holdover from when Live CD's first started appearing, rather than the problem Jeremy mentioned.

---

### Post by Mr.JJ on 2012-09-17
Do anyone has issues with gnome sushi and the preview?  It gets displayed only when tab is pressed twice (not once). This is not consistent, sometime it gets displayed with one click. The animation is also not working properly. Sushi never worked properly in ubuntu, AFAIK.  Software sources starts after a long delay. Is it also with ubuntu/unity?

---

### Post by Stinger on 2012-09-17
> **Mr.JJ said:**
> Do anyone has issues with gnome sushi and the preview?  It gets displayed only when tab is pressed twice (not once).
Yeah I noticed that too, tab has to be pressed twice but not quickly, slow and easy does it ;)
Dunno if it's meant to behave like this or it's a bug though ?

---

### Post by ybytyruzu on 2012-09-17
Hi, Empathy don't notify new messages...only one at the bottom right notification bar, but without pop-up...

---

### Post by Mr.JJ on 2012-09-17
> **Stinger said:**
> Dunno if it's meant to behave like this or it's a bug though ?

 It is a  bug for sure. It should work with one click. Not sure if its upstream one, but my guess is it is ubuntu one.

---

### Post by mc4man on 2012-09-17
> **Stinger said:**
> Yeah I noticed that too, tab has to be pressed twice but not quickly, slow and easy does it ;)
Dunno if it's meant to behave like this or it's a bug though ?
Feels like a bug though one never knows, does somewhat prevent unintentional use.

Otherwise seems ok in GS & even unity.
Does suffer from a bug where when clicking on the little icon in a text preview.
If gedit is open no issue
If not open then the docu is opened on every other attempt.

The audio file preview is good with adwaita but needs some help with ambiance, have semi-fixed that here.
(though I'd suspect most Gs users won't be using ambiance..

---

### Post by ybytyruzu on 2012-09-18
Hi, anybody is with problem with empathy notifications?

---

### Post by jbicha on 2012-09-18
Maybe take a look at org.gnome.Empathy.notifications in dconf-editor.

---

### Post by Mr.JJ on 2012-09-19
Web (epiphany) causes gnome shell to fail/break. When I access gnome bugzilla and tries to do a search (specifically when selecting a product from the combobox), gnome shell closes itself. Gnome shell do not respawn/restart itself. Firefox works just fine.

64 bit, installed to hardware with gnome3 team ppa. (I had this behaviour even on the live media. I thought it has something to do with the memory, but looks like its a bug). 

Can someone confirm this bug, so that I can report it.  Also the sushi bug, is it only ubuntu or gnome, anyone?

---

### Post by ybytyruzu on 2012-09-19
> **jbicha said:**
> Maybe take a look at org.gnome.Empathy.notifications in dconf-editor.

Thank jbicha, I will see there later...

---

### Post by Mr.JJ on 2012-09-19
> **Mr.JJ said:**
> Web (epiphany) causes gnome shell to fail/break.


 Is an upstream bug. See bug reports below. 
[https://bugzilla.gnome.org/show_bug.cgi?id=683806](https://bugzilla.gnome.org/show_bug.cgi?id=683806) 
[https://bugzilla.gnome.org/show_bug.cgi?id=684374](https://bugzilla.gnome.org/show_bug.cgi?id=684374)

---

### Post by ubiquitin.jf on 2012-09-19
Has anybody managed to get gnome shell to automatically lock the screen after x minutes? I have mine set to 5 minutes in the settings dialog but it will only lock if I do so manually.

---

### Post by semperfried76 on 2012-09-19
> **kansasnoob said:**
> 
And I don't expect Quantal Beta 1 to be anywhere near stable :(

It's so not.

---

### Post by cariboo on 2012-09-19
Removed double post by request.

---

### Post by ventrical on 2012-09-21
The last update I did killed the Desktop. All I get is the Ubuntu plymouth screen loading and then it  quits, but I can get to terminal.

---

### Post by kansasnoob on 2012-09-21
> **ventrical said:**
> The last update I did killed the Desktop. All I get is the Ubuntu plymouth screen loading and then it  quits, but I can get to terminal.

Ditto; I can now only boot into the fall-back session.

---

### Post by sgage on 2012-09-21
> **kansasnoob said:**
> Ditto; I can now only boot into the fall-back session.

Strange, everything is working fine here. I am running the nvidia-current drivers... maybe a nouveau thing?

---

### Post by Stinger on 2012-09-21
> **ventrical said:**
> The last update I did killed the Desktop. All I get is the Ubuntu plymouth screen loading and then it  quits, but I can get to terminal.
> **kansasnoob said:**
> Ditto; I can now only boot into the fall-back session.
Are you both using an AMD/ATI graphics card ? because I noticed an update to 'X-server AMD/ATI display driver wrapper' and 'X-server AMD/ATI radeon display driver' packages, 

I don't wanna hose my install (using the radeon driver myself) If I can wait it out till the next update

---

### Post by Stinger on 2012-09-21
I have now done a full update and I'm going to reboot my system, I'll be back editing this post if I'm lucky.
I'm back and the radeon driver works too, this has nothing to do with X-server AMD/ATI display driver, sorry

---

### Post by Mr.JJ on 2012-09-22
Can someone test this bug?  

Searching within nautilus 3.6 do not search within subfolders. (If you have some pictures within Pictures folder, do you get it when searching in Home?) 
[https://bugzilla.gnome.org/show_bug.cgi?id=684521](https://bugzilla.gnome.org/show_bug.cgi?id=684521) 

This seems to be an ubuntu bug. Please confirm it.

---

### Post by kansasnoob on 2012-09-22
I can boot a standard gnome-shell session here again with both Intel i945 and VIA P4M800. The VIA chip is sloooow, but I'm sure it just always will be slow with mutter.

My guess is that the latest xserver package updates fixed this. My real interest ATM is the fallback session anyway. 

I haven't had a great deal of time to spend playing with this, but so far it seems like installing Jeremy's respin is a much easier way to achieve a classic-like DE than starting with Unity.

---

### Post by sgage on 2012-09-24
> **kansasnoob said:**
> I can boot a standard gnome-shell session here again with both Intel i945 and VIA P4M800. The VIA chip is sloooow, but I'm sure it just always will be slow with mutter.

My guess is that the latest xserver package updates fixed this. My real interest ATM is the fallback session anyway. 

I haven't had a great deal of time to spend playing with this, but so far it seems like installing Jeremy's respin is a much easier way to achieve a classic-like DE than starting with Unity.

I agree. I move between Gnome Shell and Gnome Classic (no effects). Gnome Classic (the fallback session) is working very nicely now. A few glitches I'd been having with video artefacts seem to have been eliminated somewhere along the line. It's just as fast as could be. 

I like Gnome Shell as well. So glad I don't have to decide between them - I just use both as the mood hits me.  :KS

---

### Post by Stinger on 2012-09-24
If you haven't noticed, the Gnome 3.6.0 packages are beginning to arrive in the updates :-D

---

### Post by sgage on 2012-09-24
> **Stinger said:**
> If you haven't noticed, the Gnome 3.6.0 packages are beginning to arrive in the updates :-D

Yes indeed, just noticed that this afternoon...

---

### Post by Stinger on 2012-09-24
> **sgage said:**
> Yes indeed, just noticed that this afternoon...
Afternoon... That would be late evening here in Denmark, approximately 6 hours ahead of you ;)

---

### Post by sgage on 2012-09-24
> **Stinger said:**
> Afternoon... That would be late evening here in Denmark, approximately 6 hours ahead of you ;)

One of the really fun things about having a global community is that it just rolls along, 24 hours a day... The sun never sets on the Ubuntu Empire, or something like that ;)

---

### Post by Stinger on 2012-09-25
> **sgage said:**
> One of the really fun things about having a global community is that it just rolls along, 24 hours a day... The sun never sets on the Ubuntu Empire, or something like that ;)
Well I'll rather use the term " The sun never sets on the Ubuntu community", Empire sounds like we are trying to dominate the world :grin: 
I just tried the Fedora 18 alpha live CD, and compared to that we are missing the [Gnome-Boxes]("https://live.gnome.org/Boxes/"), but we are having the most updated Gnome / Gnome-Shell version :D
There is one thing I would like to have an updated version of though, that's Web / Epiphany, I know Jeremy has been working to make this possible [but it's still blocked]("https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/1033909") by a [webkit bug]("https://bugs.launchpad.net/ubuntu/+source/webkit/+bug/1005682") :(

---

### Post by Stinger on 2012-09-25
This extension is a must have in Gnome-Shell 3.6:
['Apps On Top']("https://extensions.gnome.org/extension/472/apps-on-top/") ;)

---

### Post by kansasnoob on 2012-09-25
> **Stinger said:**
> This extension is a must have in Gnome-Shell 3.6:
['Apps On Top']("https://extensions.gnome.org/extension/472/apps-on-top/") ;)

This actually highlights one of my biggest problems with either gnome-shell or unity. I'm old and I wear tri-focal lens glasses, actually "multi-focal", but even those with bi-focal lenses should be able to relate. Basically a top panel of any kind that's frequently used is a true "pain-in-the-neck" ;)

BTW even Xfce and Gnome-classic had/have this wrong by default. IMHO only LXDE and KDE get close to having the DE "panel" set correctly for those with less than perfect vision :)

---

### Post by sgage on 2012-09-25
> **kansasnoob said:**
> This actually highlights one of my biggest problems with either gnome-shell or unity. I'm old and I wear tri-focal lens glasses, actually "multi-focal", but even those with bi-focal lenses should be able to relate. Basically a top panel of any kind that's frequently used is a true "pain-in-the-neck" ;)

BTW even Xfce and Gnome-classic had/have this wrong by default. IMHO only LXDE and KDE get close to having the DE "panel" set correctly for those with less than perfect vision :)

I essentially only use the top panel for launching programs - I have a set of launchers up there (speaking now of Gnome Classic). I upped the size of the lower panel a bit. I kind of like it, because I have all the utility of the upper panel, but it doesn't distract me. I am really liking Gnome Classic. Don't care for LXDE or KDE at all.

Oh, BTW... I have "progressive" lenses - newfangled bifocals. Took some getting used to, but they work really well for me.

---

### Post by Stinger on 2012-09-25
> **sgage said:**
> 
Oh, BTW... I have "progressive" lenses - newfangled bifocals. Took some getting used to, but they work really well for me.

Hey, that could be an idea for a whole new concept of lenses in Unity, "progressive lenses" for people having trouble with their eyes :biggrin: 
( Having a bit trouble  with the eyes myself but im NOT wearing any Unity lenses ;) )

---

### Post by sgage on 2012-09-25
> **Stinger said:**
> Hey, that could be an idea for a whole new concept of lenses in Unity, "progressive lenses" for people having trouble with their eyes :biggrin: 
( Having a bit trouble  with the eyes myself but im NOT wearing any Unity lenses ;) )

That's a good one! I'm trying to think how you'd implement it... :KS

---

### Post by ventrical on 2012-09-26
> **Stinger said:**
> Are you both using an AMD/ATI graphics card ? because I noticed an update to 'X-server AMD/ATI display driver wrapper' and 'X-server AMD/ATI radeon display driver' packages, 

I don't wanna hose my install (using the radeon driver myself) If I can wait it out till the next update


Yep !!

Sorry it took so long to get back.

---

### Post by Mr.JJ on 2012-09-26
See the gnome 3.6 release notes, in case you didn't already. Wonderful and detailed description of the major new features. 

[http://library.gnome.org/misc/release-notes/3.6/](http://library.gnome.org/misc/release-notes/3.6/) 

The new control center is badly missed (even with the gnome 3 ppa). Anyone know the status of this?

---

### Post by jbicha on 2012-09-26
> **Mr.JJ said:**
> 
The new control center is badly missed (even with the gnome 3 ppa). Anyone know the status of this?

I would like to add it to the GNOME3 PPA, but I can't give you an estimated date. For instance, the Appearance panel has been completely redesigned which means that the Ubuntu patches either need to be rewritten or it won't be as nice for Unity users.

---

### Post by Harry33 on 2012-09-27
> **Mr.JJ said:**
> See the gnome 3.6 release notes, in case you didn't already. Wonderful and detailed description of the major new features. 

[http://library.gnome.org/misc/release-notes/3.6/](http://library.gnome.org/misc/release-notes/3.6/) 

The new control center is badly missed (even with the gnome 3 ppa). Anyone know the status of this?

The new control center and gnome-settigs-daemon can be easily downloaded and tested from the Ricotz Staging PPA.
I have installed those on my Gnome-shell setup. There it works just fine.

---

### Post by Mr.JJ on 2012-09-27
> **Harry33 said:**
> The new control center and gnome-settigs-daemon can be easily downloaded and tested from the Ricotz Staging PPA.
I have installed those on my Gnome-shell setup. There it works just fine.

I am not sure what the staging ppa is used for. The testing ppa is supposed to contain the latest development snapshots from git. As soon as they start working on the 3.7 branch we start getting those from that ppa. And we need testing ppa for staging one to work. So, apart from a testing POV, they do not have much relevance.  Though we are still alpha2, I am using remix as my main distro and I am not really confident on using testing ppa on a day to day basis.

> **jbicha said:**
> I would like to add it to the GNOME3 PPA, but I can't give you an estimated date
Fingers crossed!

---

### Post by Harry33 on 2012-09-27
> **Mr.JJ said:**
> I am not sure what the staging ppa is used for. The testing ppa is supposed to contain the latest development snapshots from git. As soon as they start working on the 3.7 branch we start getting those from that ppa. And we need testing ppa for staging one to work. So, apart from a testing POV, they do not have much relevance.  Though we are still alpha2, I am using remix as my main distro and I am not really confident on using testing ppa on a day to day basis.

Fingers crossed!

Ricotz Staging PPA is for testing. There is a warning, however:
> Do not use these packages if you are unexperienced handling problems!
At least you should know how get rid of them if they aren't working as expected!

Ricotz Testing PPA has a focus on Gnome-shell. Gnome-control-center and gnome-settings-daemon do have a universal impact on all Ubuntu sessions.

QQ is not in alpha2 stage.
Beta1 was released on 6th September and we are just about see the Beta2 today.

---

### Post by DisappearingOak on 2012-09-27
Has the name been decided yet? I vote for uGuntu.

---

### Post by Mr.JJ on 2012-09-27
> **Harry33 said:**
> Ricotz Testing PPA has a focus on Gnome-shell. Gnome-control-center and gnome-settings-daemon do have a universal impact on all Ubuntu sessions.

 
Ok, so staging is used for packages with universal impact. Thanks for clarifying. I was wondering why these two ppas.
 > **Harry33 said:**
> QQ is not in alpha2 stage.
Beta1 was released on 6th September and we are just about see the Beta2 today.

I was talking about remix. We did not have any beta release, only alpha2.

---

### Post by arpanaut on 2012-09-27
Is there a Testing iso for the remix that is proposed to be released in conjunction with the Ubuntu Beta2?

Edit: i.e. something new not the Alpha2 image.

---

### Post by Stinger on 2012-09-27
> **arpanaut said:**
> Is there a Testing iso for the remix that is proposed to be released in conjunction with the Ubuntu Beta2?

Edit: i.e. something new not the Alpha2 image.

[Ubuntu GNOME Remix 12.10Alpha2]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/")
"The next planned milestone is Beta, scheduled for the same week as Ubuntu 12.10 Beta 2 (September 27)."
That would be today if everything goes as planned.

And you are right, no beta yet but I think Jeremy is working hard to make this happen :cool:

It will probably appear here eventually:
[Ubuntu GNOME Remix 12.10Beta]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta")

---

### Post by Stinger on 2012-09-27
If you want to test it, the beta is now available.
Lets crank up the torrent ;)

[Get Ubuntu GNOME Remix 12.10Beta ]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta")

---

### Post by arpanaut on 2012-09-27
> Lets crank up the torrent :wink:

i386 I'm on it!
Thanks for the heads Up!

---

### Post by cpatrick08 on 2012-09-28
i found the ubuntu-gnome-remix is available at [http://ftp.acc.umu.se/pub/gnome/misc/ubuntu-gnome-remix/]("http://ftp.acc.umu.se/pub/gnome/misc/ubuntu-gnome-remix/")

---

### Post by cariboo on 2012-09-28
THe same link is available on the [Gnome Remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta") page. Oops I should say UbuntuGNOME wiki page. :-D

---

### Post by Stinger on 2012-09-28
> **cariboo907 said:**
> THe same link is available on the [Gnome Remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta") page. Oops I should say UbuntuGNOME wiki page. :-D
No you should say **uGuntu** :biggrin:

---

### Post by DisappearingOak on 2012-09-28
Can anyone confirm if they have this problem in alpha 2:
Go to Activities overview and click on the calendar on top or the menu which opens when clicking on your username a few times.
Now open the Applications tab in the Overview, again click on the calendar and the name menu a few times.
Close the Application tab so you are in the main overview again. Now click the clock and the name menu a few times again.

Do you experience that when the Applications tab is open, the menus are /slightly/ slower to open and close?

I'm using the open source Radeon driver on Radeon HD 4250 and I'm experiencing that when Applications tab is open, the menus open/close slightly less fluidly.

---

### Post by kansasnoob on 2012-09-28
Has anyone found the MD5SUM's for the beta builds?

---

### Post by smartboyhw on 2012-09-28
> **kansasnoob said:**
> Has anyone found the MD5SUM's for the beta builds?
LOL it will be me again. Actually it can be found in jbicha.net...

You can find it in here:[http://bicha.net/ubuntu-gnome-remix/MD5SUMS](http://bicha.net/ubuntu-gnome-remix/MD5SUMS)

MD5Sums:

```
6a39842c0f99d435f7e7b194848e5bfe  quantal-ubuntu-gnome-amd64-20120927.iso e91051dc0143d3fe7b5360724dd7f85c  quantal-ubuntu-gnome-i386-20120927.iso
```

---

### Post by kansasnoob on 2012-09-28
> **smartboyhw said:**
> LOL it will be me again. Actually it can be found in jbicha.net...

You can find it in here:[http://bicha.net/ubuntu-gnome-remix/MD5SUMS](http://bicha.net/ubuntu-gnome-remix/MD5SUMS)

MD5Sums:

```
6a39842c0f99d435f7e7b194848e5bfe  quantal-ubuntu-gnome-amd64-20120927.iso e91051dc0143d3fe7b5360724dd7f85c  quantal-ubuntu-gnome-i386-20120927.iso
```

Awesome! Many, many thanks :)

---

### Post by EgoGratis on 2012-09-28
What is the correct name of this distribution.

---

### Post by kansasnoob on 2012-09-28
Note to self, this is awesome:

[http://bicha.net/ubuntu-gnome-remix/](http://bicha.net/ubuntu-gnome-remix/)

It even includes a manifest so you can check package versions available :D

---

### Post by DisappearingOak on 2012-09-28
> **kansasnoob said:**
> Note to self, this is awesome:

[http://bicha.net/ubuntu-gnome-remix/](http://bicha.net/ubuntu-gnome-remix/)

It even includes a manifest so you can check package versions available :D

Can anyone tell me, to upgrade alpha 2 to beta, it's just a simple 'apt-get dist-upgrade', right?

---

### Post by jbicha on 2012-09-28
> **cpatrick08 said:**
> i found the ubuntu-gnome-remix is available at [http://ftp.acc.umu.se/pub/gnome/misc/ubuntu-gnome-remix/](http://ftp.acc.umu.se/pub/gnome/misc/ubuntu-gnome-remix/)

Yes, that's mentioned in the release notes, but please use the torrents if you can.

---

### Post by DisappearingOak on 2012-09-28
I have an important question. Those of you who have Radeon HD 4250 or similar cards, are you getting acceptable performance with the radeon driver? I'm getting jerky animations with the scale effect in some apps like Web/Epiphany. Should I install fglrx? I heard that 4250 is no longer supported by fglrx. So do I need fglrx-legacy and how would I install it. Sorry, I'm a noob at this. Any help appreciated.

---

### Post by DisappearingOak on 2012-09-29
When downloading Google Chrome 64-bit .deb from Google's official website, and doing Open with Software Installer, I get

Failed to install file,
unknown error

GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._pk_5ftransaction_5ferror.Code4: SimulateInstallFiles not supported by backend

I seem to be getting this in all downloaded .deb's i try. What is the problem here?

---

### Post by cariboo on 2012-09-29
I used gdebi, it's in the repositories to install google-chrome.

---

