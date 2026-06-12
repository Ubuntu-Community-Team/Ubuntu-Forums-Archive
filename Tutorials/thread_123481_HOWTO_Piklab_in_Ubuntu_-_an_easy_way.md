---
title: "HOWTO: Piklab in Ubuntu - an easy way"
date: 2006-01-30
forum: Tutorials
---

### Post by louis_nichols on 2006-01-30
Hi! I saw a couple of threads around asking about spftware for engineers. And I was lucky enough to discover how to install Piklab in  a very simple way. Piklab is a neat software for working with Microchip's PIC and dsPic microcontrollers. It's based here:

[http://piklab.sourceforge.net/](http://piklab.sourceforge.net/)

So... the easy way (compiling it under Ubuntu is rather complicated, since it is created for KDE and compilation needs many dev packages, which for me were just too many to install) is to just alien-ate an rpm and then make the necessary adjustments. But... enough blah-blah.

1. Download the binary rpm from
[http://puzzle.dl.sourceforge.net/sourceforge/piklab/piklab-0.3.2-1mdk.i586.rpm](http://puzzle.dl.sourceforge.net/sourceforge/piklab/piklab-0.3.2-1mdk.i586.rpm)

2. Go to the download directory.```
cd <directory where you downloaded the package>
```

3. (Only where needed) Install alien, to convert rpm to deb
```
sudo apt-get install alien
```

4. Alien-ate the rpm:
```
sudo alien piklab-0.3.2-1mdk.i586.rpm
```

5.Install the resulting deb package:
```
sudo dpkg -i piklab_0.3.2-2_i386.deb
```

6. Now this was about installing the package, but it ain't over yet. It needs a couple of dependencies which it won't show at install-time. So...

```
sudo apt-get install gputils libpcre3
```
(If you have ANY kde app installed it is quite likely you will also have libpcre, so maybe you want to check it out before installing, although I think apt-get skips it anyway if it is already installed and goes on to the missing packages).

7. And last step... Make Piklab find libraries it needs

```
 sudo ln -s /usr/lib/libpcreposix.so.3.12.0 /usr/lib/libpcreposix.so.0
 sudo ln -s /usr/lib/libpcre.so.3.12.0 /usr/lib/libpcre.so.0 
```

8. That's it! Now, just run

```
piklab
```

and you're good to go. Oh! It also needs libusb, but it's highly unlikely you don't have it installed, since even hal depends on it.

I must admit I didn't get the chance to really try it out yet, because my hardware setup isn't done yet, for working with dsPic. But maybe someone will tell me how that works out before I get to test it. :D

[COLOR="Red"]Info:[/COLOR] This installation wasn't made on a clean install of Ubuntu (I am using Breezy now, but this should apply to other versions too) so there might be packages on my system which piklab uses without my knowing about it. If you run into any problems please post them here. If you have a solution, all the better, otherwise we can find one together and then improve the howto.

I am open to any kind of feedback and/or suggestions.

Enjoy!

EDIT may 6th 2006: some corrections. Thanks egghead3 for pointing them out!

---

### Post by egghead3 on 2006-05-05
This looks interesting. Have you tried to get any of the c compilers to work, notably the sdcc or the PIC30 toolchain?

edit: in step 4 you have to run alien as fakeroot or sudo, also step 5 should be apt-get install, not update. It seem to be working, thought i dont have a hardware environment at the moment to really test it out. Thanks, I had never heard of this program and would much rather program on linux. Have you ever done anything with avr microcontrollers?

---

### Post by louis_nichols on 2006-05-05
[QUOTE=egghead3]This looks interesting. Have you tried to get any of the c compilers to work, notably the sdcc or the PIC30 toolchain?[/QUOTE]

I gave up trying after a pretty short while, because some things I couldn't control changed so the need for piklab is gone in my case

[QUOTE=egghead3]edit: in step 4 you have to run alien as fakeroot or sudo, also step 5 should be apt-get install, not update. [/QUOTE]
thanks for the heads-up! corrected it.

[QUOTE=egghead3]It seem to be working, thought i dont have a hardware environment at the moment to really test it out. Thanks, I had never heard of this program and would much rather program on linux. [/QUOTE]

You're wellcome! It should continue to run without issues.

[QUOTE=egghead3]Have you ever done anything with avr microcontrollers?[/QUOTE]

You mean in terms of build-environment under Linux? No, I never tried. For that, I've used the Atmel AVR Studio and, even more, Bascom AVR. If you're talking in a general sense, then yes, I've made some projects with avr's as projects for the uni. They are what they use to introduce us to microcontrolers and the like. They are indeed pretty fit for this job, too.

---

### Post by torf on 2006-05-05
Hey, thanks for the great how-to.  I was nearing the point of fetching the KDE libs and compiling this.  Anyway, everything worked fine until I ran piklab for the first time, I received this error:

```
piklab: error while loading shared libraries: libktexteditor.so.0: cannot open shared object file: No such file or directory

```

I checked if it could be solved by a quick symlink, but I didn't even see anything named libktexteditor* in /lib/usr or in the ubuntu repositories.  Could anyone tell me what package(s) I need to fetch to solve this issue?  Thank you very much.

---

### Post by louis_nichols on 2006-05-05
[QUOTE=torf]Hey, thanks for the great how-to.  I was nearing the point of fetching the KDE libs and compiling this.  Anyway, everything worked fine until I ran piklab for the first time, I received this error:

```
piklab: error while loading shared libraries: libktexteditor.so.0: cannot open shared object file: No such file or directory

```

I checked if it could be solved by a quick symlink, but I didn't even see anything named libktexteditor* in /lib/usr or in the ubuntu repositories.  Could anyone tell me what package(s) I need to fetch to solve this issue?  Thank you very much.[/QUOTE]

[This]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libktexteditor&searchmode=searchword&case=insensitive&version=breezy&arch=i386") should sort you out :)

---

### Post by torf on 2006-05-05
Ah, a handy site feature!  Thank you very much for a quick and helpful reply.  I installed kdelibs4c2 and all of the dependencies, and now have a happy, fuctioning piklab.  Now onto some coding! Thanks again. :D

---

### Post by torf on 2006-05-06
It appears I spoke too soon... I'm using PICkit2 with a 16F690 and am having trouble communicating with the device.

It is detected, as shown in dmesg:
```
hiddev96: USB HID v0.01 Device [Microchip Technology Inc. PICkit 2 Microcontroller Programmer] on usb-0000:00:1d.1-2
```

I have set up the program to use my kit with the correct chip, but receive the following error when I try to connect to the device:
```
Connecting Pickit2 on USB Port with device 16F690...
USB Port: Error resetting USB device.
```

Thinking this could be some sort of permissions issue, I tried again using sudo, yielding a different error message:
```
Connecting Pickit2 on USB Port with device 16F690...
USB Port: Error setting USB configuration.
```

I first thought it may be a libusb issue, but I had it installed (libusb 00.01.08 ) as well as libusb-dev and libhid0.  No luck there.  I was thinking of trying the hotplug fix as shown in the support section of the Piklab Homepage.  Any ideas?

Thank you for your time, it's much appreciated.

---

### Post by louis_nichols on 2006-05-06
Sorry! That really requires knowledge beyond mine. I've actually installed dapper recently and didn't install piklab anymore, cause the reason for it disappeared.

I think the best way is to follow any advice on their page, perhaps even contact the developers. I looked on their page and they don't have a forum, but sourceforge has a feature for discussion lists so maybe the've set up one of those. Perhaps report a bug on their [tracker]("http://sourceforge.net/tracker/?group_id=138852")...

---

### Post by torf on 2006-05-07
I've contacted one of the developers, and we've shot a few emails back and forth, no solutions yet, I'm awaiting his next response. I've tried the hotplug script (*Note* I don't have an /etc/hotplug/usb.usermap so I edited the /etc/hotplug/usb.handmap which seemed to be in the same format -- could this be a problem?) without success.  I've also tried loading and unloading usbhid without success. At this point I'm taking any suggestions or advice.

Here are the modules I have loaded:
Module                  Size  Used by
nvram                   8200  0 
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_centrino      7380  1 
cpufreq_userspace       4444  1 
cpufreq_stats           5124  0 
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
pcmcia                 24584  2 
i915                   17920  1 
drm                    58004  2 i915
video                  16004  0 
tc1100_wmi              6916  0 
sony_acpi               5516  0 
pcc_acpi               11392  0 
ibm_acpi               17908  0 
hotkey                  9508  0 
dev_acpi               11396  0 
i2c_acpi_ec             5760  0 
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0 
battery                 9604  0 
container               4608  0 
ac                      4996  0 
ipv6                  217408  6 
af_packet              20232  2 
irtty_sir               7808  0 
sir_dev                17324  1 irtty_sir
irda                  159804  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda
floppy                 52692  0 
rtc                    11832  0 
pcspkr                  3652  0 
ipw2200                92680  0 
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
yenta_socket           22540  1 
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30144  1 
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0 
tpm_nsc                 6528  0 
tpm                     9504  2 tpm_atmel,tpm_nsc
hw_random               5268  0 
shpchp                 80612  0 
pci_hotplug            24628  1 shpchp
intel_agp              21276  1 
agpgart                32328  3 drm,intel_agp
dm_mod                 50364  1 
joydev                  9280  0 
tsdev                   7616  0 
evdev                   9088  1 
psmouse                26116  0 
mousedev               10912  1 
parport_pc             31812  1 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  1 
jbd                    48536  1 ext3
thermal                13192  0 
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0 
usbhid                 30688  0 
e100                   32768  0 
mii                     5248  1 e100
ehci_hcd               29448  0 
uhci_hcd               28048  0 
usbcore               104316  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 36996  0 
cdrom                  33952  1 ide_cd
ide_disk               16128  3 
ide_generic             1664  0 
piix                    9476  1 
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  624 
vesafb                  8088  0 
capability              5000  0 
commoncap               6784  1 capability
vga16fb                12232  1 
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72 
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

---

### Post by louis_nichols on 2006-05-07
Try posting it in a new thread in the forums. This is definitely an issue that goes beyond the particularities of piklab, so someone with more experience might have a solution.

---

### Post by torf on 2006-05-12
I ended up getting it working with the help of Chen Xiao Fan over at pickit-devel:
[http://groups.google.com/group/pickit-devel]("http://groups.google.com/group/pickit-devel")

For the sake of having a solution to the problem I've brought up in this thread, I've copied my "success" post from pickit-devel below.  One major mistake I made early on was that I had the incorrect firmware version.  Since I bought the kit recently, I assumed the firmware was all up to date.  However, this was not the case.  Be sure you're using V1.10:
[http://ww1.microchip.com/downloads/en/DeviceDoc/Pk2V011000.zip]("http://ww1.microchip.com/downloads/en/DeviceDoc/Pk2V011000.zip")
If you update the firmware in Windows, you'll need version 1.12 of the Pickit 2 software to make this firmware upgrade.  According to pickit-devel, a new firmware is going to be released soon, which breaks pk2, pyk and piklab.  If microchip ceases to provice V1.10 for some reason, feel free to contact me for this firmware version.

**How I have hotplug/udev setup:**
```

jon@entropy:/etc/udev/rules.d$ groups
jon adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin pickit <---- This one is the relevant one

jon@entropy:/etc/hotplug/usb$ ls -l
total 172
-rwxr-xr-x  1 root root   220 2005-09-28 09:10 libgphoto2
-rw-r--r--  1 root root 96304 2005-12-11 01:34 libgphoto2.usermap
-rw-r--r--  1 root root 49605 2005-09-27 10:14 libsane.usermap
-rwxr-xr-x  1 root root   885 2005-09-27 10:14 libusbscanner
-rwxr-xr-x  1 root root   223 2006-05-12 17:27 pickit2
-rw-r--r--  1 root root    84 2006-05-12 17:28 pickit2.usermap

jon@entropy:/etc/hotplug/usb$ cat pickit2
#!/bin/bash

if [ "${ACTION}" = "add" ] && [ -f "${DEVICE}" ]
then
  echo "changing ${DEVICE} pickit 1 or 2" >> /tmp/debug-hotplug

      chown root "${DEVICE}"
      chgrp pickit "${DEVICE}"
      chmod 660 "${DEVICE}"
fi

jon@entropy:/etc/hotplug/usb$ cat pickit2.usermap
pickit2 0x0003 0x04d8 0x0033 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00
0x00 0x00000000

jon@entropy:/etc/udev/rules.d$ ls
020_permissions.rules  cd-aliases.rules  udev.rules
z60_alsa-utils.rules
026_pickit.rules       thinkpad.rules    z50_run.rules
z70_hotplugd.rules

jon@entropy:/etc/udev/rules.d$ cat 026_pickit.rules
#PICKit2
SYSFS{idVendor}=="04d8", SYSFS{idProduct}=="0033", MODE="0660",
GROUP="microchip"

After all that, I restarted hotplug and udev, yielding some results
that brought a big old smile across my face:

jon@entropy:/etc/udev/rules.d$ sudo /etc/init.d/hotplug restart; sudo
/etc/init.d/udev restart
 * Stopping hotplug subsystem...
 [ ok ]
 * Starting hotplug subsystem...
 [ ok ]
 * Recreating device nodes...
 [ ok ]
jon@entropy:/etc/udev/rules.d$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 04d8:0033 Microchip Technology, Inc.
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. Optical Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

jon@entropy:/etc/udev/rules.d$ ls -l /proc/bus/usb/002/
total 0
-rw-r--r--  1 root root   43 2006-05-12 17:48 001
-rw-r--r--  1 root root   52 2006-05-12 17:48 003
-rw-rw----  1 root pickit 91 2006-05-12 17:49 004

And there we go - Success!

```

---

### Post by louis_nichols on 2006-05-13
Glad to read this! :) Now, I think this thread offers THE complete solution. :)

---

### Post by fatih on 2007-01-14
even i am executing all steps succesfully, i am getting the error below:

piklab: error while loading shared libraries: libpcreposix.so.0: cannot open shared object file: No such file or directory

how can i solve it?
thanks.

---

### Post by louis_nichols on 2007-01-15
Well, I think the answer lies here:

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libpcreposix&searchmode=searchword&case=insensitive&version=edgy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libpcreposix&searchmode=searchword&case=insensitive&version=edgy&arch=i386)

So what you have to do is install the package libpcre3 and then make a simlink from libpcreposix.so.3 to libpcreposix.so.0.

It should work.

---

### Post by fatih on 2007-01-15
thanks, i have already installed libpcre3. but after installing dev packages and linking, it has worked. 

i am a newbie in linux. 

with "sudo apt-get install gputils libpcre3" command, it did not automatically installed the dev package. i think it should be "sudo apt-get install gputils libpcre3 libpcre3-dev" for the ones like me :)

---

### Post by louis_nichols on 2007-01-15
That sounds strange. I can't think of any reason why you would need the dev packages too. But I guess it might be.

The important thing is it works. It works, right?

---

### Post by fatih on 2007-01-17
yes it works :-D

---

### Post by SnackySmores on 2007-08-10
great post, finally an IDE for my PICs thanks for the HOWTO.
just a little correction when making the links for libpcreposix & libpcre make sure you are linking to the version you're using.  in feisty the version of the files are .12

take care

---

### Post by navaburo on 2007-10-14
Thanks, works great!

I ran into the problem that my PICKit 2 programmer's firmware version was too new.

No problem though, using the tool from Microchip I was able to downgrade the firmware to 1.10 which i can confirm works with piklab 0.14.5

---

### Post by dennis_k85 on 2007-11-13
I am running Gutsy, and have gone through all the steps to install it. But I get this error message:

piklab: error while loading shared libraries: libpcreposix.so.0: cannot open shared object file: No such file or directory
 
Did I miss something? 

I did a find on libpcreposix.so.0, and it is in /usr/lib. Do I need to add a link?

---

### Post by dennis_k85 on 2007-11-13
Ok I got past that. The libpcre stuff was linked to a non existent file. So I am past that now. 
Now I get :

piklab: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

So What package does libpng reside in?

---

### Post by dennis_k85 on 2007-11-13
Never mind. I found it, and all is well now, except that I can't set the programmer. But I'll look into that later.

---

### Post by firefoxdl on 2007-11-13
thanks.
well done!!

---

### Post by pawonfire on 2008-02-21
Thanks for the helpful post.  Since I am using a newer version of Ubuntu, I had to figure out how to link the newer files properly.  This is what I had to do, in case another newbie comes along.

I had gotten to the point of running piklab, when I got an error message that I didn't record.  I think it was something like 'can't find libpcreposix'  I fixed it with this:

  sudo apt-get install libpcreposix

I tried running piklab again and got this:

  error while loading shared libraries: libpcre.so.0: cannot open            
  shared object file: No such file or directory

and fixed it with this:

  sudo ln -s /usr/lib/libpcre.so.3.12.1 /usr/lib/libpcre.so.0

another try yielded this:

  error while loading shared libraries: libpng.so.3: cannot open   
  shared object file: No such file or directory

this was fixed with this:

  sudo ln -s /usr/lib/libpng12.so.0.15.0 /usr/lib/libpng.so.3

Now it works fine.  Here is what I understand is going on (and should help future users if true).  There are library files in /usr/lib/    used for many different programs.  They are regularly updated, with revision numbers increasing at the end of file names.  When piklab was last put together, it was told to look for an older version of the file. The ln -s [new file] [shortcut] allows the program to find the updated file.  To do this properly, you need the file it is looking for in the error message, and the name of the new file ( cd /usr/lib       then ls -m)

It is probably better to check first to see what version you have, because I tried to link to an older one than I had, and had to delete it (sudo rm BADSHORTCUT) before making the proper link)

---

### Post by direk_ on 2008-03-29
Hi guys. If you have problems with your USB programmers, you probably don't have priviliges to write data to USB port. The easiest way is to add your user name to "root" group.

In my case I had to change line:
```
root:x:0:
```
to:
```
root:x:0:direk
```
in file **/etc/group**

and i can use my USB stuff with piklab :-)

---

### Post by Chaoser on 2008-12-09
Who is using Intrepid may face additional problems:

**Problem:**
```
piklab: error while loading shared libraries: libldap-2.3.so.0: cannot open shared object file: No such file or directory
```

**Solutions:**
```
sudo ln -s /usr/lib/libldap-2.4.so.2 /usr/lib/libldap-2.3.so.0
```

**Problem:**
```
piklab: error while loading shared libraries: liblber-2.3.so.0: cannot open shared object file: No such file or directory
```

**Solution:**
```
sudo ln -s /usr/lib/liblber-2.4.so.2 /usr/lib/liblber-2.3.so.0
```


**And also you need to install "konsole":**

```
sudo apt-get install konsole
```

P.S also I have problem with libpcre3 package, it didn't have needed libs. So in case you have to reinstall libpcre: 

```
sudo aptitude reinstall libpcre3
```

I hope this will help :)

---

### Post by gogo2520 on 2009-03-07
Hello 
 I realize this is old post but I got a question about hotplug, and was hoping that some one could help.
   I am trying to set up a pickit 2 and use piklab for it also..
 I have ubuntu 8.10 installed (nice) 
 But all the info I have read refer to the hotplug being in the etc dir. I did a locate and I have hotplug listed in several different dirs but not in the etc dir. Is there something wrong with my install? or Can I fix this?
                         thanks for any info
                          gogo

gogo@gogo-desktop:/$ cd etc
gogo@gogo-desktop:/etc$ locate hotplug
/lib/modules/2.6.27-11-generic/kernel/drivers/pci/hotplug
/lib/modules/2.6.27-11-generic/kernel/drivers/pci/hotplug/acpiphp.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/pci/hotplug/acpiphp_ibm.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/pci/hotplug/cpcihp_generic.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/pci/hotplug/cpcihp_zt5550.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/pci/hotplug/cpqphp.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/pci/hotplug/fakephp.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/pci/hotplug/ibmphp.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/pci/hotplug/pci_hotplug.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/pci/hotplug/pciehp.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/pci/hotplug/shpchp.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/pci/hotplug
/lib/modules/2.6.27-7-generic/kernel/drivers/pci/hotplug/acpiphp.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/pci/hotplug/acpiphp_ibm.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/pci/hotplug/cpcihp_generic.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/pci/hotplug/cpcihp_zt5550.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/pci/hotplug/cpqphp.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/pci/hotplug/fakephp.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/pci/hotplug/ibmphp.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/pci/hotplug/pci_hotplug.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/pci/hotplug/pciehp.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/pci/hotplug/shpchp.ko
/usr/share/doc/libgphoto2-2/linux-hotplug
/usr/share/doc/libgphoto2-2/linux-hotplug/usbcam.console
/usr/share/doc/libgphoto2-2/linux-hotplug/usbcam.group
/usr/share/doc/libgphoto2-2/linux-hotplug/usbcam.user
/usr/share/doc/libgphoto2-2/linux-hotplug/usbcam.x11-app
/usr/share/ifupdown/upgrade-from-hotplug.pl
/usr/src/linux-headers-2.6.27-11/drivers/pci/hotplug
/usr/src/linux-headers-2.6.27-11/drivers/pci/hotplug/Kconfig
/usr/src/linux-headers-2.6.27-11/drivers/pci/hotplug/Makefile
/usr/src/linux-headers-2.6.27-11/include/linux/memory_hotplug.h
/usr/src/linux-headers-2.6.27-11/include/linux/pci_hotplug.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/acpi/hotplug
/usr/src/linux-headers-2.6.27-11-generic/include/config/acpi/hotplug/cpu.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/arch/enable/memory/hotplug.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/cpu.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/acpi
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/acpi.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/compaq
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/compaq.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/cpci
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/cpci.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/fake.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/ibm.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/pcie.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/shpc.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/acpi/ibm.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/compaq/nvram.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/cpci/generic.h
/usr/src/linux-headers-2.6.27-11-generic/include/config/hotplug/pci/cpci/zt5550.h
/usr/src/linux-headers-2.6.27-11-generic/include/linux/memory_hotplug.h
/usr/src/linux-headers-2.6.27-11-generic/include/linux/pci_hotplug.h
/usr/src/linux-headers-2.6.27-7/drivers/pci/hotplug
/usr/src/linux-headers-2.6.27-7/drivers/pci/hotplug/Kconfig
/usr/src/linux-headers-2.6.27-7/drivers/pci/hotplug/Makefile
/usr/src/linux-headers-2.6.27-7/include/linux/memory_hotplug.h
/usr/src/linux-headers-2.6.27-7/include/linux/pci_hotplug.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/acpi/hotplug
/usr/src/linux-headers-2.6.27-7-generic/include/config/acpi/hotplug/cpu.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/arch/enable/memory/hotplug.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/cpu.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/acpi
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/acpi.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/compaq
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/compaq.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/cpci
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/cpci.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/fake.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/ibm.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/pcie.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/shpc.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/acpi/ibm.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/compaq/nvram.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/cpci/generic.h
/usr/src/linux-headers-2.6.27-7-generic/include/config/hotplug/pci/cpci/zt5550.h
/usr/src/linux-headers-2.6.27-7-generic/include/linux/memory_hotplug.h
/usr/src/linux-headers-2.6.27-7-generic/include/linux/pci_hotplug.h
gogo@gogo-desktop:/etc$ 

See what I mean.
I did a ls in the etc dir and it showed a lot of files but no hotplug.
gogo

---

### Post by anshul vohra on 2009-05-20
hello? does the piklab have a stopwatch function like mplab ide to measure the time delay in the execution of commands when gpsim is the debugger? if yes where please?

thankyou
anshul

---

### Post by anshul vohra on 2009-05-20
would be appreciated if any one could suggest any other means to do so?

---

### Post by blz93 on 2010-10-03
[SIZE=2]I installed piklab on Ubuntu just with sudo apt-get install piklab :)..
It works perfect..[/SIZE][SIZE=1]for now[/SIZE]

---

### Post by brawd on 2010-10-13
Hi all,

I don't know if this thread is still alive or what but it didn't show itself when I did a search of the forums, I found it via google. I have started another thread but no replies forthcoming.


My problem(s) shows itself like this message in Piklab when I try to connect my Pickit2.

Connecting PICkit2 Firmware 1.x on USB Port with device 16F690... 
Firmware version is 2.32.0 
The firmware version (2.32.0) is higher than the version tested with piklab (1.20.0). You may experience problems. 
set Vdd = 5 V and Vpp = 12 V 
USB Port: Error receiving data (ep=0x81 res=-110) (err=could not get bound driver: No data available). 

The Pickit2 itself shows the green Power light and that is all.
The Pickit2 was bought last week and I have never used one of these micros before. It came with a small demo board with 16f690 on board, 4 leds, switch and pot.

I have installed the microchip software that came with it on an XP webbook and the little leds started flashing. The Target light on the Pickit2 was also on.

So it works fine in XP.

Any suggestions please?.

regards,

brawd

---

### Post by brawd on 2010-10-16
Well just to answer myself for the sake of any other hopefuls that come along.

I had to give up on Piklab.

I was running Lucid 64 bit when I started on this and then added in the KDE stuff. Still nothing doing.
I wiped the hard drive completely using Hiren's boot disc and installed i386 just in case Piklab was 32 bit and still nothing.
I've made up a new group in Users and Groups called microchip and added myself into that. Nope
I've searched the depositories - as they are the recommended place to download from - and failed to find Libusb which seems to be necessary to Piklab.
I've followed links from Ubuntu forums where I copy and paste into different files to see if that helps, but it doesn't.
I've installed pk2cdm, which turned out to be a command line programmer (I think) and for the life of me I won't use that. (The command line is where I came from in the days before windows and I intend going forward not back).
I scoured the web - or at least I googled - in search of a setup for Pickit2 but failed.

So that's my experience, no luck whatsoever because Piklab won't communicate with my Pickit 2.

But there's no way I'm going back to windows, I'll just install MPlab on my wife's little webbook and use that until someone, somewhere, sometime sorts out this little problem.

I might build a serial port burner, but I don't know. There isn't much future in doing the burning through the serial port it's not readily available anymore.

I'll still keep an eye on the forums and the Microchip site, you never know!

regards,

brawd

---

### Post by phollands on 2010-11-08
I did once manage to get my picklab to program a dspic30F4000 using an Olimex compatible ICD2.  I found that it was vital in that case, that the dsPic was running with a VCC of 5Volts. Initially my board was running at 4.5 volts, and the dsPic got locked up. I had to erase it with a power supply of 5Volts, and then when I re-programmed it I was successful.

This would have been under ubuntu10.04.

In general, there seem to be a very small number of people trying to get a development architecture working under Ubuntu for Microchip. Just getting the C30 compiler working alone, seem to be very difficult.

---

### Post by rtalcott on 2011-06-04
I had to do this....
[http://sourceforge.net/apps/mediawiki/piklab/index.php?title=USB_Port_Problems](http://sourceforge.net/apps/mediawiki/piklab/index.php?title=USB_Port_Problems)

rt

---

### Post by brawd on 2011-12-12
Thanks rtalcott,

been there, did that, no joy!

I've been hearing about MPLabX from microchip which (some say) works on most systems including Linux - which I take to mean Ubuntu. I haven't found a free download, not even on their own site, or  anywhere else but I'll keep going.

regards,

---

### Post by jovin555 on 2013-04-25
I got this error while installing piklab.> 
piklab: error while loading shared libraries: libktexteditor.so.0: cannot open shared object file: No such file or directory

how to solve this?

---

