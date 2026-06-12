---
title: "installing Ubuntu Server in UEFI mode"
date: 2016-02-25
forum: Server Platforms
---

### Post by sudodus on 2016-02-25
Has anyone installed Ubuntu Server in UEFI mode?

One of the computers is the Toshiba that I often use for testing, [a Toshiba laptop](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850Edit:-19w/) with Intel i5 and with Intel i3 and Intel 3rd gen core proc graphics controller. It runs the kernel module i915 in Xenial desktop systems. The wifi is RTL8723AE using the kernel module rtl8723ae.

The graphics and wifi work for me without tweaks with all current Ubuntu desktop versions and flavours is UEFI as well as in BIOS mode.

The other one is [a Lenovo X131e](https://shop.lenovo.com/ISS_Static/ww/wci/products/us/laptop/thinkpad/x-series/x131e-intel/X131e-Datasheet-Intel.pdf) with Intel i3 and Intel 2nd gen core proc graphics controller. It runs the kernel module i915 in Xenial desktop systems. The wifi is Broadcom BCM43228 using the kernel module b43.

The graphics works for me without tweaks with all current Ubuntu desktop versions and flavours in UEFI as well as in BIOS mode. The wifi does not create any problems when connected via wired network.
[hr][/hr]
Ubuntu Server amd64 (and its debian installer) works in BIOS mode. But there are problems in UEFI mode. I have tried several 14.04 point versions, 15.10 and Xenial (of course amd64 versions). The computer boots to grub, and ***the grub menu looks good, but after that the screen cannot display anything but some messy lines***. It seems that the graphics driver does not get the correct information to work (which is different from BIOS mode in the same computers). So I cannot see the user dialogue, and cannot run the [debian] installer.
[hr][/hr]
Please help me install Ubuntu Server in UEFI mode :-) Maybe you know some tweaks, for example some boot options or work-arounds, that would fix it.
[hr][/hr]
***Edit 1:*** This is for testing purposes and for the future. I can boot these two computers in both BIOS and UEFI mode, but we can expect that computers in the future will not boot in BIOS mode, so we should be prepared not only with the desktop versions and flavours, but also the server and mini versions of Ubuntu.

***Edit 2:*** A work-around that makes me mark this thread as solved is described at the following posts, [#20](http://ubuntuforums.org/showthread.php?t=2315007&p=13481148#post13481148) and [#21](http://ubuntuforums.org/showthread.php?t=2315007&page=2&p=13501418#post13501418). The original problem is not solved.

---

### Post by oldfred on 2016-02-25
I am surprised that server version does not work, if desktop does.
I thought kernel now was same and would expect default modules like Intel video would also be the same.

I do know Intel has been updating/changing things, mostly for next gen versions, but some of those fixes also apply to older/current chips.

You can try these boot options.
       # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

Some desktops needed this:

 Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
My notes show this for Toshiba desktop: :)
Toshiba laptop C850 Windows 7 with upgrade to 8 version -  sudodus
[http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025](http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025)

---

### Post by sudodus on 2016-02-26
@oldfred,

Thanks for the tips :-)

I have tried them all in both computers, but they do not work (in UEFI mode). I have not tried all combinations of all of them, that would be 'too much'. I think there should be one (possibly two) of them that should solve the problem.

Could you suggest some insmod command or some other command, that should be edited into the grub menu before the linux command line?

@ everybody,

Could it be, that the support for UEFI in the Ubuntu Server iso files is not complete? That is is only by chance, that we can see the grub menu, but nobody has really developed and tested Ubuntu Server for UEFI?

Are there any dedicated server computers, that boot in UEFI mode, or are all servers booting in BIOS mode?

---

### Post by oldfred on 2016-02-26
I have seen Boot-Repair Summary reports from a few servers with the ESP - efi system partition.

But grub also has insmod modules to directly boot into LVM and some types of RAID. But the efi has almost always been a separate partition. 
I believe I have seen a couple of RAID installs with FAT32 ESP inside the RAID which surprised me. Not sure of type of RAID as I do not fully understand that, but it must be one where UEFI/BIOS knows about it or what is fakeRAID.

I am in Fla and main UEFI system is in Ill. I am a snowbird that heads south for Winters. Currently running off my 10 year old laptop.

 But I am changing to Fla for main home and have most of parts for new UEFI system arriving tomorrow. It is 6th Gen Intel and M.2 SSD, so if I can get desktop working I will also try a server install.

---

### Post by sudodus on 2016-02-26
Sounds promising :-P

---

### Post by mastablasta on 2016-02-29
> **sudodus said:**
> @oldfred,

Could it be, that the support for UEFI in the Ubuntu Server iso files is not complete? That is is only by chance, that we can see the grub menu, but nobody has really developed and tested Ubuntu Server for UEFI?

Are there any dedicated server computers, that boot in UEFI mode, or are all servers booting in BIOS mode?

an interesting question. however, it doesn't look like it should have an issue with UEFI. for example HP Gen 9 server: [http://www.ubuntu.com/certification/hardware/201511-20296/](http://www.ubuntu.com/certification/hardware/201511-20296/)

uses BIOS HP: U21 (UEFI)

and this is certified server hardware. it doesn't say that installation would require a disabling of secure boot.

furthermore as for the UEFI itself - Linux was one of the first to support it anyway. so the software running the mobo itself should not be an issue.

I might be wrong here, but once control is transferred to GRUB it shouldn't have much to do with BIOS/UEFI. so I am not sure how the server installer would be interfered by UEFI.

---

### Post by sudodus on 2016-02-29
I agree, mastablasta. It *should* work be like you describe.

Maybe there is simply a bug, so that the preparation for the graphics does not work properly with the Ubuntu Server installer in UEFI mode: Some step that is tested and works in BIOS mode is missing.

The funny thing is that is happens to affect both my computers with UEFI, and they are rather different (but both use Intel graphics). Ubuntu Server works in these computers in BIOS mode, and the desktop flavours work in both modes, BIOS and UEFI. I can even boot 32-bit desktop versions ín UEFI mode, when I make persistent live systems with mkusb.

---

### Post by sudodus on 2016-03-01
I tried the ***text mode installer*** of the following ***debian*** iso file, which corresponds to the Ubuntu mini.iso and Ubuntu Server iso files.

[http://cdimage.debian.org/debian-cd/8.3.0/amd64/iso-cd/debian-8.3.0-amd64-netinst.iso](http://cdimage.debian.org/debian-cd/8.3.0/amd64/iso-cd/debian-8.3.0-amd64-netinst.iso)

**Install:** works (of course) in BIOS mode. It suffers from the same problems with graphics in UEFI mode (in my two computers) as the Ubuntu Server.

But that iso file contains also the options

**Graphical install:** works in BIOS mode but defaults to text screen (which is faulty) in UEFI mode.

**Install with speech synthesis:** might work also in UEFI mode after training in BIOS mode :-P

---

### Post by darkod on 2016-03-01
After following this thread I have to ask: Is this just to see if you can make it work, or your machines do not allow booting in bios mode?

Because most (I thought all) machines that have uefi allow boot in bios mode too. And since linux supports bios boot and gpt tables on large disks, I see no benefit of uefi boot. I have to admit I haven't even researched it much, mainly because of what I just said. I have my server in bios mode with gpt tables, nice and easy.

It's a different thing with windows that needs uefi with gpt tables.

So there's probably something I'm not aware of, some benefit. Why would you insist on uefi so much?

---

### Post by sudodus on 2016-03-01
This is for testing purposes and for the future. I can boot these two computers in both BIOS and UEFI mode :-) But we can expect that computers in the future will not boot in BIOS mode, so we should be prepared not only with the desktop versions and flavours, but also the server and mini versions of Ubuntu.

The Lubuntu developers were discussing problems to keep the iso file within CD size (700 Mibibytes). We have already lost the battle for the desktop iso files, but we have alternate iso files within CD size. There are big problems to keep the alternate iso files working at all. For that reason there are no Lubuntu alternate iso files for the point releases 14.04.{2,3,4}. (The Lubuntul alternate files with the debian installer are also failing in UEFI mode.)

But it is possible to install Lubuntu via the mini.iso and Ubuntu Server iso files, so there is a workaround. The mini.iso does not boot in UEFI mode. I have noticed that Ubuntu Server boots into a grub menu in UEFI mode, but at least in my two computers, the text screen will not work after leaving grub, so this debian based installer (in text mode) does not work.

So while we were looking for a workaround for Lubuntu, we found this problem with Ubuntu Server. I would say that it is either a bug, or it has never been intended to use the Ubuntu Server in UEFI mode. I don't know, and now I am asking if you know if anybody runs Ubuntu Server in UEFI mode. In that case, how was it installed?

---

### Post by sudodus on 2016-03-01
The corresponding ***OpenSuse mini.iso (85 MiB) works in UEFI mode*** in my two laptops (specified in the opening post).

[http://download.opensuse.org/distribution/leap/42.1/iso/openSUSE-Leap-42.1-NET-x86_64.iso](http://download.opensuse.org/distribution/leap/42.1/iso/openSUSE-Leap-42.1-NET-x86_64.iso)

The installer works in graphics mode all the time (not text screen). And ***I could install a working minimal text-only system in a pendrive in UEFI mode***!

---

### Post by mastablasta on 2016-03-02
so it's a bug then. :(

would still be interested to see installers behaviour on UEFI Ubuntu certified systems.

---

### Post by oldfred on 2016-03-02
I just tried installing server version in UEFI mode, I had just set up 16.04 desktop on sda, and tried server install to sdb.

It booted and took me all the way to installing software and failed. I could see folders, but no files in folders in new install.

---

### Post by sudodus on 2016-03-02
Interesting :-) So you were affected by another bug - the graphics worked, but no files were installed. I guess it *should* work to install into sdb.

I suspect that nobody has really tested Ubuntu Server in UEFI mode, or at least it is not tested enough.

What computer did you use for the test?

---

### Post by oldfred on 2016-03-02
Standard Intel graphics. Brand new small desktop build to replace 10 year old laptop:
Since new hardware only installed 16.04, so far.

```
fred@Z170N:~$ inxi -Fxz
System:    Host: Z170N Kernel: 4.4.0-8-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: Gnome  (Gtk 3.18.8-1ubuntu1) Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: Z170N-Gaming 5 v: x.x
           Bios: American Megatrends v: F3 date: 10/20/2015
CPU:       Quad core Intel Core i5-6500 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 25535
           clock speeds: max: 3600 MHz 1: 800 MHz 2: 800 MHz 3: 1067 MHz
           4: 999 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics bus-ID: 00:02.0
           Display Server: X.Org 1.17.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           GLX Version: 3.0 Mesa 11.1.2 Direct Rendering: Yes
Audio:     Card Intel Sunrise Point-H HD Audio
           driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.4.0-8-generic
Network:   Card-1: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller
           driver: alx port: e000 bus-ID: 08:00.0
           IF: enp8s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Intel Wireless 8260 driver: iwlwifi bus-ID: 09:00.0
           IF: wlp9s0 state: down mac: <filter>
Drives:    HDD Total Size: 1250.3GB (3.7% used)
           ID-1: /dev/sda model: Samsung_SSD_850 size: 250.1GB temp: 0C
           ID-2: /dev/sdb model: HGST_HTS721010A9 size: 1000.2GB temp: 41C

```

---

### Post by sudodus on 2016-03-02
Do you think we should file a bug report (or bug reports)? In that case against which packages?

---

### Post by sudodus on 2016-03-02
I have reported it to Launchpad now:

['Installing Ubuntu Server fails in UEFI mode' Bug #1552365](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1552365)

@oldfred, Please mark 'affects me too'

---

### Post by oldfred on 2016-03-02
Done, but want to try again.
I only have Intel Video in Florida and will not be back to Ill for a couple of months. Or when it warms up there. :)

---

### Post by sudodus on 2016-03-02
Thanks, oldfred!

Let us hope that other people will get 'enrolled' in this project before it warms up in Illinois :-)

---

### Post by sudodus on 2016-05-01
I have found no solution to this problem yet, but a *workaround*. A new computer, Intel [NUC6i3SYH](http://www.intel.se/content/www/se/sv/nuc/nuc-kit-nuc6i3syh.html), manages to display the text of the installer in UEFI mode, so I could install Ubuntu Server 16.04 LTS in UEFI mode. In other words, the signed kernel was installed, and it works with secure boot. The installed system is portable and the text mode works in UEFI mode in my two computers, that do not like the text mode installer.

I used my method to create a portable system, that boots in both UEFI and BIOS mode. It is a minimal system with text mode menus to help creating an Ubuntu flavour including Ubuntu Server. There is also a menu entry to create an ultra-light system with the Fluxbox window manager.

It is convenient to set the font (size) of the text console, to make it fit the screen resolution. See the following link,

[A new compressed image file is uploaded: 'dd_text_16.04-UEFI-n-BIOS-4-pendrive-7.8GB.img.xz'](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13481136#post13481136)

I think this system can be quite useful, when you want to make a portable installed system.

---

### Post by sudodus on 2016-06-09
*Oldfred* taught me to use ***tasksel*** to make it convenient to install all the metapackages that are available from the Ubuntu Server iso file. So I made a new version of the ***compressed image files of an installed system that works in both UEFI and BIOS mode***. (I also added a menu entry for htop, while I was modifying the systems.)

[Two updated compressed image files are uploaded](http://ubuntuforums.org/showthread.php?t=2213631&page=8&p=13495646#post13495646)

Alongside with improvements of [mkusb](https://help.ubuntu.com/community/mkusb) (version 10.6.6) it is rather convenient to use this method to install Ubuntu Server into laptops or other computers, where the debian installer does not work. So I mark this thread as SOLVED.

See also [Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

