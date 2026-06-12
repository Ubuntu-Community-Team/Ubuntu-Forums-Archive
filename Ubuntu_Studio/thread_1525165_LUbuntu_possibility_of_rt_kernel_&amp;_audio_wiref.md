---
title: "LUbuntu: possibility of rt kernel &amp; audio wirefire ?"
date: 2010-07-06
forum: Ubuntu Studio
---

### Post by JC Cheloven on 2010-07-06
Hi, I post in this forum because I think I've got better chances of having an answer. 

What I did so far: 

[INDENT]I'm trying out LUbuntu in an old crappy (but with 4-pin fw port!) toshiba A50 laptop. It refuses to get installed anything newer than jaunty. Even to install Lubuntu 10.04 I had to start in secure graphics mode, and then the vesa driver is used at installation. Tried also to install both regular & UbStudio lucid with combinations of xdrvr=vesa, noapic, nolapic, acpi=off, and others, but no success. So let's focus in LUbuntu.

Lubuntu is nice itself, but what I expect finally is to access the firewire port to connect a fw audio interface. I installed the ffado driver, set the memlock and nice parameters, added my user to audio & video groups, and such. I've also installed the "rt" kernel, the "realtime" kernel, and still another one (pae kernel?). None of them boots the system. Only the regular kernel does. AFAIK, the rt kernel is needed for audio firewire ¿am I wrong?

Nevertheless, I tried (just in case) to start jack with the firewire driver, unticking the realtime box. It doesn't start, as expected LOL.[/INDENT]

Hence my question:
[INDENT]Anyone can give me a clue on how to setup LUbuntu so that I can use the firewire port for audio?[/INDENT]

---

### Post by AutoStatic on 2010-07-06
> **JC Cheloven said:**
> Lubuntu is nice itself, but what I expect finally is to access the firewire port to connect a fw audio interface. I installed the ffado driver, set the memlock and nice parameters, added my user to audio & video groups, and such. I've also installed the "rt" kernel, the "realtime" kernel, and still another one (pae kernel?). None of them boots the system. Only the regular kernel does. AFAIK, the rt kernel is needed for audio firewire ¿am I wrong?You don't need a RT kernel to work with Firewire audio cards. PAE kernel is a 32-bits kernel that can address RAM bigger than 4 Gb. And you don't need to set nice settings: [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf)
You do need to allow normal users to set priorities (rtprio).

> **JC Cheloven said:**
> Anyone can give me a clue on how to setup LUbuntu so that I can use the firewire port for audio?Did you try the Alternate Ubuntu CD: [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)
This CD allows to install Ubuntu in text-mode.

And what kind of Firewire controller does the notebook have?

---

### Post by trulan on 2010-07-06
You're using Jaunty, correct?  I hope I got that right - or a lot of this post is irrelevant...

The RT kernel is a big help for low-latency firewire audio but it is not strictly necessary.  And the RT kernel from Jaunty isn't exactly stable.  If it were mine, I'd probably compile the 2.6.31-rt kernel (the one used in Karmic) but base the config off the generic Jaunty kernel that actually boots up on the machine - but that's getting a bit involved I realize.

But if firewire audio is going work on the RT kernel, it should also work on the generic kernel at higher latency.  Oh, and un-ticking the 'Real Time' box isn't necessary on the generic kernel either - though having it selected may not do any good, I'm not sure.

Is raw1394 assigned to the 'video' or 'audio' group?  Even if you used Ubuntu Studio Controls to enable raw1394 access, there's a bug in it in Jaunty and you have to do some manual editing:
> - run sudo gedit /lib/udev/rules.d/50-udev-default.rules
- add this line anywhere in that file (though under the #Firewire line  is probably nicest) KERNEL=="raw1394",              GROUP="video"
- save the file and close the program
Again, that only applies to Jaunty.

---

### Post by JC Cheloven on 2010-07-09
Hi, thanks for your answers.

@Autostatic:

a) I'm a bit confused about the need of rt kernel for firewire. I think currently there is (in ubuntu) although normally it shouldn't(?) From [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) :
> With the new Firewire stack in Ubuntu Kernel, at the moment, it is not possible to run FFADO sound cards nor use Firewire for DV capture with -generic and -lowlatency kernels. Please see instructions on this page to install -rt kernel on this page, wich has old working stack (...) 

b) Nice to know this about "nice" LOL. I wasn't aware. Thanks.

c) Didn't try the lucid alternate cd, but tried the UbStudio installation disk, which is "alternate" itself. It installed but failed to boot.

d) From lspci, the firewire controller is:
01.07.0 FireWire (IEEE 1394): Texas Instruments TSB43Ab21 IEEE-1394a-2000 Controller (PHY/Link)


@Trulan:

Not using Jaunty, trying to use lucid for the lts feature (wich would cover the probable life of this pc). But some of your pointings were of interest for me. Now I recall that the recommended UbStudio version has been Hardy 8.04, until the times of Karmic 9.10, due to rt problems in between. 
Perhaps I should consider installing 8.04.4, still with some months of support, and if I manage to make things work (mainly firewire), use it this way forever. Probably better than using ?Ubuntu lucid in safe graphics mode. The idea came to me reading your post ;-)

---

### Post by trulan on 2010-07-10
You could use Hardy - although that adds a whole new set of problems because ffado (the firewire drivers) is not included by default.  There was a ppa that had a build of ffado for Hardy - it's probably still active

But when you say it fails to boot, is it a graphics issue or does the cpu not like the kernel?  If you can actually boot one of the newer RT kernels into safe graphics mode (xforcevesa), there may yet be hope.

They say TI firewire chips are the best, so all good there.  What's the CPU, and what kind of graphics chip does it have?

---

### Post by AutoStatic on 2010-07-10
> **JC Cheloven said:**
> @Autostatic:

a) I'm a bit confused about the need of rt kernel for firewire. I think currently there is (in ubuntu) although normally it shouldn't(?) From [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) :


Oh yeah, the UbuntuStudioPreparation wiki page. Check the [discuss page]("https://help.ubuntu.com/community/UbuntuStudioPreparation/Discuss"), a non-native speaker messed it up a little bit. But for 10.04 you indeed need the older 2.6.31 rt kernel because the 2.6.32 kernels only have the new stack afaik. Another possibility would be to use the new kernel and install FFADO from svn, the latest release has support for the "juju" firewire stack now.

And [Khashayar's PPA]("https://launchpad.net/~khashayar/+archive/ppa") still has the FFADO drivers for 8.04.

But I'm quite confident that Lucid should run on your machine. If you could provide more specs, thanks in advance.

---

### Post by angelsguitar on 2010-07-11
Hi JC Cheloven!

Lubuntu as an audio distro seems like a great idea; AV Linux uses LXDE too, and works great, so my guess is that Lubuntu should do great too, once it is properly configured.  Let us know how it works for you.

Also, you may want to try Alessio's 2.6.33 rt kernel.  You can find it on his ppa:

[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/~abogani/+archive/ppa")

Or, if you prefer a "vanilla" 2.6.33 kernel with rt patches, try this one:

[https://launchpad.net/~bojo42/+archive/rt]("https://launchpad.net/~bojo42/+archive/rt")

Also, check Linux Musicians wiki for some pointers on setting up an audio distro:

[http://wiki.linuxmusicians.com/doku.php?id=system_configuration]("http://wiki.linuxmusicians.com/doku.php?id=system_configuration")

---

### Post by JC Cheloven on 2010-07-18
Hi all,

That Toshiba A50 laptop had installation problems since gutsy (all its life). And the newer Ubuntus (karmic onwards) didn't work at all, either live or installed. I always suspected from a graphics card problem, which could probably be overcome by some "magic words".

I've found by hazard those magic words browsing a recent post in this forums. Instead of "quiet splash", [COLOR="Red"]"i915.modeset=1"[/COLOR] is to be passed to the kernel. This way, the crappy intel integrated graphics behaves well.
 
- From live this is done by pressing F6 to make the grub boot command line show up.

- If the system is installed in HD, it won't boot, as for some reason the kernel mode setting is not inherited from the live session. So, still from live, the file etc/default/grub (in the hard disc!) has to be edited so that the appropriate line reads GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1"
[INDENT]EDIT: Oops, I forgot to say: grub needs to be updated after that. In fact, what I did was reinstalling grub2 in the usual way (still from live cd, and assuming sda1 as the lucid partition) :
[INDENT] mount /dev/sda1 /mnt
 mount --bind /dev /mnt/dev
 chroot /mnt
 grub-install --recheck /dev/sda
 reboot [/INDENT]
In a second thought, I'm not sure if this grub install would suffice by itself, and/or if the grub-install line could have been substituted by a simpler update-grub. Anyway, the process above has proved to work.
[/INDENT]

Now this pc has a regular Lucid installation with compiz enabled, and with the firewire port working for audio (after configuration and 2.6.31 rt kernel installation). 
I tried out also LUbuntu & XUbuntu in live, and the trick worked equally well. So I guess I could install UbuntuStudio or any "alternate cd" in the same way. But in fact, LUbuntu piqued my interest, and this machine will probably end up with an Lubuntu installation if I manage to get the firewire working. I'll go back if I have any success on this (mmm... looking at the title, the thread would certainly benefit from this).

@ Autostatic, Trulan, Angelsguitar: thanks for your valuable help.
JC

---

### Post by trulan on 2010-07-19
Glad it's working!  Gotta love those magic words!  While my Intel i915 chip actually behaves very well for everything but Wine and Virtualbox (where it is painfully slow), to boot my desktop on Lucid or newer (onboard NVidia GPU) I have to use xforcevesa or when gdm starts, it powers off the monitor.

I've never used LUbuntu, but I use AVLinux extensively.  It's a Debian-based distro that also uses LXDE.  Except for the lack of a good menu editor like Gnome has, I like it better than regular Ubuntu with Gnome.  And I can actually boot to a working desktop with less than 90Mb ram used - talk about lightweight!  Gnome, by comparison, uses around 340Mb.  (I could put the Win-Vista DVD/frisbee in that came with the machine and install that again, where trying to run with anything under 1Gb is just useless.)

Enjoy your 'new' computer!

---

### Post by JC Cheloven on 2010-07-19
Yes, AVlinux looks great, and made me discover those interesting non-daw and non-mixer applications. Unfortunately, as for the machine in question, there is no possibility of using avlinux: the cpu does not support the pae kernel (or vice-versa LOL).

BTW, I've just made the "serious proof": connecting my Helix Board 18 FW to the 4 pin firewire, and recording to 6 independent channels at 24bit/48kHz. Used jack (of course) with Ardour & Traverso in turn. No xruns in the ~5 min of the test. It's awesome what can be still achieved with a 1-core 1.6 GHz pc. Here is the lspci, just in case someone is interested:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)


Again, I will come back if I happen to have any success with LUbuntu & firewire in this "new" (trulan: LOL) machine.

JC

---

### Post by JC Cheloven on 2010-07-30
Well, once done, I feel like bringing evident news. A properly configured LUbuntu works nicely with a rt kernel (2.6.31.11 for now), and a firewire audio device. I achieved roughly the same functionality than with a regular ubuntu or ubuntustudio. The basic steps are the same that can be found in [popular sources]("https://help.ubuntu.com/community/UbuntuStudioPreparation"). To sum up, this is what I did in particular:

- Installed the 2.6.31 rt kernel image and headers (are in the repos)

- Edited /etc/security/limits.d/audio.conf, and /etc/security/limits.conf. I believe it's only necessary to edit one of them, but (being unsure) I edited both. Added these lines to both:
@audio   -  rtprio     99
@audio   -  memlock    650000   # I've got 1Gb ram, u may want to scale this accordingly

- Added my user to the audio and video groups

- Created the file /etc/udev/rules.d/65-permission-raw.rules and edited it to contain this line:
[INDENT]KERNEL=="raw1394", OWNER="root", GROUP="video", MODE="660"[/INDENT]

- Rebooted.

- Installed the ffado apps for firewire access: sudo apt-get install ffado-dbus-server ffado-mixer-qt4 ffado-tools libffado2


... well, I think that's it. I recorded to 6 independent tracks using Lubuntu and a firewire devide. Nice.

JC

---

