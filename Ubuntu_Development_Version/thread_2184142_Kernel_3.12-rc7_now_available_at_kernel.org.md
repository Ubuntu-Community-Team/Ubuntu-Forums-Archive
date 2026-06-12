---
title: "Kernel 3.12-rc7 now available at kernel.org"
date: 2013-10-27
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2013-10-27
[https://www.kernel.org/pub/linux/kernel/v3.x/testing/](https://www.kernel.org/pub/linux/kernel/v3.x/testing/)

---

### Post by rtalcott on 2013-10-27
ppa has it too

---

### Post by sammiev on 2013-10-27
Deb files [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc7-saucy/").

---

### Post by VinDSL on 2013-10-27
> **paul_in_london said:**
> [https://www.kernel.org/pub/linux/kernel/v3.x/testing/](https://www.kernel.org/pub/linux/kernel/v3.x/testing/)
Heh!  Nice.

I was getting bored, watching Netflix on the telly.

Okay, here goes...

---

### Post by sammiev on 2013-10-27
Been running it for an hour now. Do not notice anything new or broken so far. :)

---

### Post by VinDSL on 2013-10-27
Working fine on the box.

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~" && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/  /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Mon Oct 28 03:01:08 UTC 2013
Distro Release: Ubuntu Trusty Tahr (development branch)
Kernel Release: Linux 3.12.0-rc7-vindsl-p4ee-ver.01
Gnome Release: GNOME Shell 3.10.1
Unity Release: unity 7.1.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.88

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 115
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.1.0-2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
  Version: 9.2.2-1ubuntu1

Package: xserver-xorg-core
  Installed: 2:1.14.3-3ubuntu3

Package: xserver-common
  Installed: 2:1.14.3-3ubuntu3

Package: xserver-xephyr
  Installed: 2:1.14.3-3ubuntu3

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-03.0-[02]----01.0  Intel Corporation 82547EI Gigabit Ethernet Controller
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[03]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$
```

Compiling on the lappy, as I type...  ;)

---

### Post by pqwoerituytrueiwoq on 2013-10-28
now available in mainline
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc7-saucy](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc7-saucy)
Kernel Version: 3.12.0-031200rc7
Release Date: 2013/10/27 @ 19:35 (YYYY/MM/DD @ HH:MM)
edit seems someone beat me to it

---

### Post by QDR06VV9 on 2013-10-28
This one is a keeper!!

---

### Post by ventrical on 2013-10-29
It booted one of my Core2Duos a lot faster and it got rid of that double-dutching lightdm log-on screen. (mabey that was a seperate bug.)

---

### Post by VinDSL on 2013-10-29
> **ventrical said:**
> It booted one of my Core2Duos a lot faster...
Speaking of Core2Duos'...

Only you could appreciate this, Vent:

[Disco.Ubuntu.com]("http://test.ubuntu-discourse.org/t/what-are-you-listening-to/334/80") (toward the bottom)  :D

Working great on my Latitude D620!

---

### Post by su:bhatta on 2013-10-29
Can anyone please tell me if I can get 3.12.x-lowlatency kernel?

Preferrably don't have to compile myself.

Thanks.

---

### Post by QDR06VV9 on 2013-10-29
> **VinDSL said:**
> Speaking of Core2Duos'...

Only you could appreciate this, Vent:

[Disco.Ubuntu.com]("http://test.ubuntu-discourse.org/t/what-are-you-listening-to/334/80") (toward the bottom)  :D

Working great on my Latitude D620!
This one.
```
Takes the same amount of time to listen to a Mozart piano concerto and compile Linux 
```;)

---

### Post by ventrical on 2013-10-29
> **VinDSL said:**
> Speaking of Core2Duos'...

Only you could appreciate this, Vent:

[Disco.Ubuntu.com]("http://test.ubuntu-discourse.org/t/what-are-you-listening-to/334/80") (toward the bottom)  :D

Working great on my Latitude D620!

Just love Margret Argerich.  Maria .. ?? tortured genius of course :) lol

'the flute player just about knocked me out of my chair' - lol :)


[http://www.youtube.com/watch?v=1PdcmFvZvuI](http://www.youtube.com/watch?v=1PdcmFvZvuI)

---

### Post by VinDSL on 2013-10-30
I was having fits, trying to compile a custom Linux 3.12-rc7 kernel on my Peppermint Four powered Latitude.  Used to be no problem, but all of a sudden, it decided that it had unmet dependencies, when I tried to install the kernel -- which were actually being met.

Put another way, the kernel compiled just fine, but refused to install over bogus unmet dependencies.

Had to compile the kernel, then dissect the debs, edit the control file, remove the bogus dependencies, save, then repack the debs.  Sheesh!

Anyway, all's well that ends well.

```
vindsl@Gorgar ~ $  inxi -F
System:    Host: Gorgar Kernel: 3.12.0-rc7-vindsl-latitude.001 x86_64 (64 bit) Desktop: N/A Distro: Peppermint Four
Machine:   System: Dell product: Latitude D620
           Mobo: Dell model: 0FT292 Bios: Dell version: A10 date: 05/16/2008
CPU:       Dual core Intel Core2 CPU T5500 (-MCP-) cache: 2048 KB flags: (lm nx sse sse2 sse3 ssse3 vmx) 
           Clock Speeds: 1: 1000.00 MHz 2: 1000.00 MHz
Graphics:  Card: Intel Mobile 945GM/GMS 943/940GML Express Integrated Graphics Controller 
           X.Org: 1.13.3 drivers: intel (unloaded: fbdev,vesa) Resolution: 1440x900@60.0hz 
           GLX Renderer: Mesa DRI Intel 945GM GLX Version: 1.4 Mesa 9.1.4
Audio:     Card: Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture ver: k3.12.0-rc7-vindsl-latitude.001
Network:   Card-1: Broadcom BCM4311 802.11b/g WLAN driver: b43-pci-bridge 
           IF: wlan0 state: up mac: 00:19:7e:67:0f:11
           Card-2: Broadcom NetXtreme BCM5752 Gigabit Ethernet PCI Express driver: tg3 
           IF: eth0 state: down mac: 00:18:8b:d0:9b:ac
Drives:    HDD Total Size: 80.0GB (12.4% used) 1: id: /dev/sda model: HTS721080G9SA00 size: 80.0GB 
Partition: ID: / size: 11G used: 4.0G (42%) fs: ext4 ID: /home size: 26G used: 5.3G (23%) fs: ext4 
           ID: swap-1 size: 2.15GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 45.5C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 143 Uptime: 27 min Memory: 489.6/1992.9MB Client: Shell inxi: 1.8.4 
vindsl@Gorgar ~ $ 

```

Here's a screenie of me stripping bogus dependencies out of the control file...

[[img]http://vindsl.com/images/vindsl-desktop-29-oct-2013-1(650x520).png[/img]](http://vindsl.com/images/vindsl-desktop-29-oct-2013-1.png)

** As seen on the Ubuntu Disco Test Site

---

### Post by VinDSL on 2013-10-30
> **ventrical said:**
> Just love Margret Argerich.[..].
Bwahahaha!

Did you see the jerk that was telling Margret how to play a piano?  LoL!  :D

---

### Post by VinDSL on 2013-10-30
> **runrickus said:**
> This one.
> Takes the same amount of time to listen to a Mozart piano concerto and compile Linux ;)
True!

It takes around 30 minutes to do both.

I can use Mozart piano concertos for a timer.  When the applause stops, the kernel is cooked...  ;)

---

### Post by ventrical on 2013-10-30
> **VinDSL said:**
> Bwahahaha!

Did you see the jerk that was telling Margret how to play a piano?  LoL!  :D


  Yeah .. and she's playing coy .. like .. "oh really" and when she went to sit down (had to adjust the seat) and she tied to wipe the hair out of her face and made this awful, sourpuss face and grimace.. I mean .. hasn't she ever hear of a  bret or one of those hair clippy things ... but .. back on topic .. I noticed ..

```


CPU:       Dual core Intel Core2 CPU T5500 (-MCP-) cache: 2048 KB flags: (lm nx sse sse2 sse3 ssse3 vmx) 
           Clock Speeds: 1: 1000.00 MHz 2: 1000.00 MHz


```

does that processor scale back and forth?  .. I thought it was 1.6 GHz.

[http://ark.intel.com/products/27253/Intel-Core2-Duo-Processor-T5500-2M-Cache-1_66-GHz-667-MHz-FSB](http://ark.intel.com/products/27253/Intel-Core2-Duo-Processor-T5500-2M-Cache-1_66-GHz-667-MHz-FSB)

edit .. whoops .. EISST  ;)

---

### Post by VinDSL on 2013-10-30
> **ventrical said:**
> Yeah .. and she's playing coy .. like .. "oh really" and when she went to sit down (had to adjust the seat) and she tied to wipe the hair out of her face and made this awful, sourpuss face and grimace.. I mean .. hasn't she ever hear of a  bret or one of those hair clippy things ... but .. back on topic .. I noticed ..
These top-tier women pianists know how to play the game.  Any guy that's slumped over in his seat, at rehearsal, twisting his eyebrows is going to be trouble, but he holds the pocketbook -- so, Martha just placated him -- that's all.

When she had her fill of him, she dispatched him with a belch...

I love how the women pianists come out on concert night in perfect makeup, adorned with beautiful, flowing, off_the_shoulder gowns and crepe-black wraps, but if you watch their feet, you'll see they are wearing sensible, clumpy shoes (to work the pedals).  LoL! 


> **ventrical said:**
> 
```


CPU:       Dual core Intel Core2 CPU T5500 (-MCP-) cache: 2048 KB flags: (lm nx sse sse2 sse3 ssse3 vmx) 
           Clock Speeds: 1: 1000.00 MHz 2: 1000.00 MHz


```

does that processor scale back and forth?  .. I thought it was 1.6 GHz.

[http://ark.intel.com/products/27253/Intel-Core2-Duo-Processor-T5500-2M-Cache-1_66-GHz-667-MHz-FSB](http://ark.intel.com/products/27253/Intel-Core2-Duo-Processor-T5500-2M-Cache-1_66-GHz-667-MHz-FSB)

edit .. whoops .. EISST  ;)
Yep, the Dell Latitude D620 auto-scales back n' forth.  BTW, reportedly, it was the best selling Dell notebook of all time.

It's fun to watch Conky, during a session.  Most of the time the CPU runs at 1GHz, but when you fire up Synaptic (for instance) it ratchets up to 1.6MHz for awhile, then simmers back down to 1GHz.

Amazing notebook, really.  It's still perfectly usable, and speedy, especially on Peppermint 64-bit (Lubuntu fork).  

It's my primary road warrior these days -- lugged it all over the country, with confidence.  ;)

---

### Post by QDR06VV9 on 2013-10-30
> **VinDSL said:**
> True!

It takes around 30 minutes to do both.

I can use Mozart piano concertos for a timer.  When the applause stops, the kernel is cooked...  ;)

Sorry Vin I did not mean to butt in on your conversation with Vent, Sometimes I feel so familiar with you two,
I may overstep my bounds.:rolleyes:
But the vids kept me entertained for the rest of the evening Great Stuff!

---

### Post by VinDSL on 2013-10-30
> **runrickus said:**
> Sorry Vin I did not mean to butt in on your conversation with Vent, Sometimes I feel so familiar with you two [...]
No problem.  We're all friends in +1.  Consider us as 'Dutch Uncles'. We won't bite you... LoL!  :D

BTW, that custom 3.12-rc7 kernel worked a treat on my lappy -- flying like the wind.

Peppermint dev indicated that several users have told him, the 3.11 kernel solved a lot of bugs -- peeked his interest IMO.

I *think* 3.12 is even better. It solved a problem I was having on_the_road with the AT&T wifi system, at the Hilton Palacio Del Rio where I was staying.

---

### Post by QDR06VV9 on 2013-10-30
> **VinDSL said:**
> No problem.  We're all friends in +1.  Consider us as 'Dutch Uncles'. We won't bite you... LoL!  :D


Thanks!! Maybe great uncle for me!(age) :D
```

BTW, that custom 3.12-rc7 kernel worked a treat on my lappy -- flying like the wind.

Peppermint dev indicated that several users have told him, the 3.11 kernel solved a lot of bugs -- peeked his interest IMO.

I *think* 3.12 is even better. It solved a problem I was having  on_the_road with the AT&T wifi system, 
at the Hilton Palacio Del Rio  where I was staying.
``` 
Could not agree more I have a Hp DV2700Se with the dreaded broadcom wireless adapter but kernel 3.12 installed it out the box.(Yeah:D)

---

### Post by ventrical on 2013-10-30
@ runrickus

You are a great encourager. :)  Much needed in these forums. Compiling a kernel is somewhat like composing a symphony (or actually performing one). It's about timing, structure, forms, colours, syncopation, multitasking and building a carousell of sound from beginning to ending. Using a works by Mozart, Beethoven, Greig or whomever, is a good way to contrast descriptions when paralleling them to compiling kernel formats. Although we are working with machines that may not allow us to improvise in the same way, let's say, on a piano for instance, the kernel can still be modified to perform as if it had been improvised - because improvised music, discordant, consonant or disonant is always perfectly beautiful and unified by it's point and counterpoint and such then as a programmer interjects to experiements with an alternate set of code, even though it has to follow a strickter set of rules, can still bring it to discovery of new colours , functions and processes that echo structures of the musical form.

:)

regards..

---

### Post by ventrical on 2013-10-30
> **runrickus said:**
> Thanks!! Maybe great uncle for me!(age) :D
```

BTW, that custom 3.12-rc7 kernel worked a treat on my lappy -- flying like the wind.

Peppermint dev indicated that several users have told him, the 3.11 kernel solved a lot of bugs -- peeked his interest IMO.

I *think* 3.12 is even better. It solved a problem I was having  on_the_road with the AT&T wifi system, 
at the Hilton Palacio Del Rio  where I was staying.
``` 
Could not agree more I have a Hp DV2700Se with the dreaded broadcom wireless adapter but kernel 3.12 installed it out the box.(Yeah:D)

Same here on my Acer Extensa 4420.   What a pain. I am doing a fresh install now of trusty - soon to install the new kernel .

---

### Post by QDR06VV9 on 2013-10-30
> **ventrical said:**
> @ runrickus

You are a great encourager. :)  Much needed in these forums. Compiling a kernel is somewhat like composing a symphony (or actually performing one). It's about timing, structure, forms, colours, syncopation, multitasking and building a carousell of sound from beginning to ending. Using a works by Mozart, Beethoven, Greig or whomever, is a good way to contrast descriptions when paralleling them to compiling kernel formats. Although we are working with machines that may not allow us to improvise in the same way, let's say, on a piano for instance, the kernel can still be modified to perform as if it had been improvised - because improvised music, discordant, consonant or disonant is always perfectly beautiful and unified by it's point and counterpoint and such then as a programmer interjects to experiements with an alternate set of code, even though it has to follow a strickter set of rules, can still bring it to discovery of new colours , functions and processes that echo structures of the musical form.

:)

regards..
Thanks Ventrical! Very that's very Gracious of you.
I was so burnt out on testing, since 2005 Novel Suse, But I did get free hardware though: any who you and VinDSL have changed my perspective.
Having fun again.
Not trying to get all sappy here, But you two just Enhance my experience in the process..
My Heart Felt Thanks to the both of ya!
Regards:popcorn:

---

### Post by ventrical on 2013-10-31
> **runrickus said:**
> Thanks!! Maybe great uncle for me!(age) :D
```

BTW, that custom 3.12-rc7 kernel worked a treat on my lappy -- flying like the wind.

Peppermint dev indicated that several users have told him, the 3.11 kernel solved a lot of bugs -- peeked his interest IMO.

I *think* 3.12 is even better. It solved a problem I was having  on_the_road with the AT&T wifi system, 
at the Hilton Palacio Del Rio  where I was staying.
``` 
Could not agree more I have a Hp DV2700Se with the dreaded broadcom wireless adapter but kernel 3.12 installed it out the box.(Yeah:D)

Actually the old method worked fine after this fresh install:

```

sudo apt-get install bcmwl-kernel-source


```
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by QDR06VV9 on 2013-10-31
> **ventrical said:**
> Actually the old method worked fine after this fresh install:

```

sudo apt-get install bcmwl-kernel-source


```
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Ventrical I used to just install linux-nonfree-firmware worked straight away for me bcm4312

---

### Post by ventrical on 2013-10-31
> **runrickus said:**
> Ventrical I used to just install linux-nonfree-firmware worked straight away for me bcm4312

Oh.... :)  So installing the 3.12 rc pulls in a free-source driver to make that work then without bcmwl-kernel-source?

---

### Post by QDR06VV9 on 2013-10-31
> **ventrical said:**
> Oh.... :)  So installing the 3.12 rc pulls in a free-source driver to make that work then without bcmwl-kernel-source?

Thats been the case for me recently!:o

---

### Post by VinDSL on 2013-11-01
Hrm...

Think we got a regression going on here (I've experienced this problem in the past, with other RCs).

Anybody else having problems with their USB flash drives?!?!?

I've got 3.12-rc7 installed on my Latitude and desktop box.  USB sticks work on neither.

Both of them recognize USB flash drives as being plugged-in, but neither will mount them -- automount nor allow a manual mount.

EXAMPLE:

```
vindsl@Zuul:~$ tail -f /var/log/syslog
Nov  1 12:57:17 Zuul kernel: [ 2992.624035] usb 1-2: new high-speed USB device number 5 using ehci-pci
Nov  1 12:57:17 Zuul kernel: [ 2992.760835] usb 1-2: New USB device found, idVendor=0930, idProduct=6545
Nov  1 12:57:17 Zuul kernel: [ 2992.760839] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov  1 12:57:17 Zuul kernel: [ 2992.760843] usb 1-2: Product: USB Flash Memory
Nov  1 12:57:17 Zuul kernel: [ 2992.760846] usb 1-2: Manufacturer:         
Nov  1 12:57:17 Zuul kernel: [ 2992.760849] usb 1-2: SerialNumber: 0013729B6607EAC0D57A01E6
Nov  1 12:57:17 Zuul mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Nov  1 12:57:17 Zuul mtp-probe: bus: 1, device: 5 was not an MTP device

```

```
vindsl@Zuul:~$ lsusb
Bus 001 Device 005: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

NADA...

```
vindsl@Zuul:~$ ls -laR /dev/disk
/dev/disk:
total 0
drwxr-xr-x  5 root root  100 Nov  1 12:07 .
drwxr-xr-x 14 root root 4140 Nov  1 12:09 ..
drwxr-xr-x  2 root root  220 Nov  1 12:07 by-id
drwxr-xr-x  2 root root   80 Nov  1 12:07 by-label
drwxr-xr-x  2 root root  160 Nov  1 12:07 by-uuid

/dev/disk/by-id:
total 0
drwxr-xr-x 2 root root 220 Nov  1 12:07 .
drwxr-xr-x 5 root root 100 Nov  1 12:07 ..
lrwxrwxrwx 1 root root   9 Nov  1 12:07 ata-HP_DVD_Writer_1040r -> ../../sr0
lrwxrwxrwx 1 root root   9 Nov  1 12:07 ata-MAXTOR_STM3160812AS_5LSBRTN4 -> ../../sda
lrwxrwxrwx 1 root root  10 Nov  1 12:07 ata-MAXTOR_STM3160812AS_5LSBRTN4-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 Nov  1 12:07 ata-MAXTOR_STM3160812AS_5LSBRTN4-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 Nov  1 12:07 ata-MAXTOR_STM3160812AS_5LSBRTN4-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 Nov  1 12:07 ata-MAXTOR_STM3160812AS_5LSBRTN4-part4 -> ../../sda4
lrwxrwxrwx 1 root root  10 Nov  1 12:07 ata-MAXTOR_STM3160812AS_5LSBRTN4-part5 -> ../../sda5
lrwxrwxrwx 1 root root  10 Nov  1 12:07 ata-MAXTOR_STM3160812AS_5LSBRTN4-part6 -> ../../sda6
lrwxrwxrwx 1 root root  10 Nov  1 12:07 ata-MAXTOR_STM3160812AS_5LSBRTN4-part7 -> ../../sda7

/dev/disk/by-label:
total 0
drwxr-xr-x 2 root root  80 Nov  1 12:07 .
drwxr-xr-x 5 root root 100 Nov  1 12:07 ..
lrwxrwxrwx 1 root root  10 Nov  1 12:07 Ubuntu\x2010.10 -> ../../sda1
lrwxrwxrwx 1 root root  10 Nov  1 12:07 Ubuntu\x2013.10 -> ../../sda5

/dev/disk/by-uuid:
total 0
drwxr-xr-x 2 root root 160 Nov  1 12:07 .
drwxr-xr-x 5 root root 100 Nov  1 12:07 ..
lrwxrwxrwx 1 root root  10 Nov  1 12:07 17887ede-93ff-469f-8bda-a29be0cc03c5 -> ../../sda4
lrwxrwxrwx 1 root root  10 Nov  1 12:07 1835824f-9aba-48ba-874b-6955be247395 -> ../../sda7
lrwxrwxrwx 1 root root  10 Nov  1 12:07 28a17342-3d9b-4306-96cf-3bd092645ce7 -> ../../sda5
lrwxrwxrwx 1 root root  10 Nov  1 12:07 5a139fb5-0664-4150-b65a-d73852369ae8 -> ../../sda1
lrwxrwxrwx 1 root root  10 Nov  1 12:07 ba01bbc8-e888-4891-ade4-923ec2d29946 -> ../../sda6
lrwxrwxrwx 1 root root  10 Nov  1 12:07 d75f3ee2-ce9d-4408-b39a-8e8b7bab8ae6 -> ../../sda3

```

Seems to be a kernel issue.  Everything works fine when I boot into older kernels...

---

### Post by sammiev on 2013-11-01
> **VinDSL said:**
> Hrm...

Think we got a regression going on.

Anybody else having problems with their USB flash drives?!?!?

I've got 3.12-rc7 installed on my Latitude and desktop box.  USB sticks work on neither.

Both of them recognize USB flash drives as being plugged-in, but neither will mount them, automount or manual mount.

EXAMPLE:

```
vindsl@Zuul:~$ tail -f /var/log/syslog
Nov  1 12:57:17 Zuul kernel: [ 2992.624035] usb 1-2: new high-speed USB device number 5 using ehci-pci
Nov  1 12:57:17 Zuul kernel: [ 2992.760835] usb 1-2: New USB device found, idVendor=0930, idProduct=6545
Nov  1 12:57:17 Zuul kernel: [ 2992.760839] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov  1 12:57:17 Zuul kernel: [ 2992.760843] usb 1-2: Product: USB Flash Memory
Nov  1 12:57:17 Zuul kernel: [ 2992.760846] usb 1-2: Manufacturer:         
Nov  1 12:57:17 Zuul kernel: [ 2992.760849] usb 1-2: SerialNumber: 0013729B6607EAC0D57A01E6
Nov  1 12:57:17 Zuul mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Nov  1 12:57:17 Zuul mtp-probe: bus: 1, device: 5 was not an MTP device

```

```
vindsl@Zuul:~$ lsusb
Bus 001 Device 005: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Hi VinDSL, 

All seems to work good here.

```
sam@sam--L650:~$ lsusb
Bus 002 Device 003: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 002 Device 004: ID 1e3d:6025 Chipsbank Microelectronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 10f1:1a2a Importek Laptop Integrated Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sam@sam--L650:~$ 

```

---

### Post by VinDSL on 2013-11-01
> **sammiev said:**
> Hi VinDSL, 

All seems to work good here.

```
sam@sam--L650:~$ lsusb
Bus 002 Device 003: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 002 Device 004: ID 1e3d:6025 Chipsbank Microelectronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 10f1:1a2a Importek Laptop Integrated Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sam@sam--L650:~$ 

```
Thanks for the reply.

Yeah, my systems see the flash drive(s)...

```
vindsl@Zuul:~$ lsusb
Bus 001 Device 005: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I just cannot /mnt them.

Have you tried plugging-in a flash drive?

---

### Post by sammiev on 2013-11-01
> **VinDSL said:**
> Thanks for the reply.

Yeah, my systems see the flash drive(s)...

```
vindsl@Zuul:~$ lsusb
Bus 001 Device 005: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I just cannot /mnt them.

Have you tried plugging-in a flash drive?

The pic I posted was my flash drive and on the foreground was an open cfg file from the flash drive.

---

### Post by VinDSL on 2013-11-01
> **sammiev said:**
> The pic I posted was my flash drive and on the foreground was an open cfg file from the flash drive.
Okay, well...

Maybe I'm missing a module or something, when I'm compiling them.

I'll check it out, after I update my FB and linkedin pages.  :D

 Thanks!

---

### Post by ventrical on 2013-11-01
It is working here but SDC it absolutely useless. I can copy , move .. etc.. but no SDC. It starts up ok  but it reports an error , not enough space, when trying to erase it.. then it goes on like it is installing and then just drops right off the screen. (whoops .. another story for another thread )  :) lol



```

ventrical@ventrical-desktop:~$ ls -laR /dev/disk
/dev/disk:
total 0
drwxr-xr-x  5 root root  100 Nov  1 17:50 .
drwxr-xr-x 15 root root 4220 Nov  1 17:50 ..
drwxr-xr-x  2 root root  180 Nov  1 17:50 by-id
drwxr-xr-x  2 root root   80 Nov  1 17:50 by-path
drwxr-xr-x  2 root root  100 Nov  1 17:50 by-uuid

/dev/disk/by-id:
total 0
drwxr-xr-x 2 root root 180 Nov  1 17:50 .
drwxr-xr-x 5 root root 100 Nov  1 17:50 ..
lrwxrwxrwx 1 root root   9 Nov  1 11:37 ata-HL-DT-STDVD-RAM_GSA-H55N -> ../../sr0
lrwxrwxrwx 1 root root   9 Nov  1 11:37 ata-ST3250410AS_6RY05DL0 -> ../../sda
lrwxrwxrwx 1 root root  10 Nov  1 11:37 ata-ST3250410AS_6RY05DL0-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 Nov  1 11:37 ata-ST3250410AS_6RY05DL0-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 Nov  1 11:37 ata-ST3250410AS_6RY05DL0-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 Nov  1 17:50 usb-Kingston_DataTraveler_C10_001CC0EC34B1EA5120000004-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 Nov  1 17:50 usb-Kingston_DataTraveler_C10_001CC0EC34B1EA5120000004-0:0-part1 -> ../../sdb1

/dev/disk/by-path:
total 0
drwxr-xr-x 2 root root  80 Nov  1 17:50 .
drwxr-xr-x 5 root root 100 Nov  1 17:50 ..
lrwxrwxrwx 1 root root   9 Nov  1 17:50 pci-0000:00:1d.7-usb-0:6:1.0-scsi-0:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 Nov  1 17:50 pci-0000:00:1d.7-usb-0:6:1.0-scsi-0:0:0:0-part1 -> ../../sdb1

/dev/disk/by-uuid:
total 0
drwxr-xr-x 2 root root 100 Nov  1 17:50 .
drwxr-xr-x 5 root root 100 Nov  1 17:50 ..
lrwxrwxrwx 1 root root  10 Nov  1 17:50 23E1-397F -> ../../sdb1
lrwxrwxrwx 1 root root  10 Nov  1 11:37 acbc3776-e736-4d04-9707-344a2a2f8dc4 -> ../../sda1
lrwxrwxrwx 1 root root  10 Nov  1 11:37 e823ca64-707d-41f7-b3ec-50fc569b4080 -> ../../sda5
ventrical@ventrical-desktop:~$ 

```

---

### Post by fooman on 2013-11-01
vindsl, i have had issues with mounting usb flash drives and even dvds after compiling my own kernels (via paul's method).  my work-around is to make sure i have usb flash drives already mounted (i put one in a rear usb port and one in a front usb port just to cover all bases),  i also load a dvd in my drive....then i proceed to compile.

worked for me on 2 laptops and 2 desktops here.

---

### Post by VinDSL on 2013-11-01
> **fooman said:**
> i have had issues with mounting usb flash drives and even dvds [...] my work-around is to make sure i have usb flash drives already mounted [...] i also load a dvd in my drive....then i proceed to compile.
Thanks.

I'll try that right now...  ;)

---

### Post by sammiev on 2013-11-01
> **fooman said:**
> vindsl, i have had issues with mounting usb flash drives and even dvds after compiling my own kernels (via paul's method).  my work-around is to make sure i have usb flash drives already mounted (i put one in a rear usb port and one in a front usb port just to cover all bases),  i also load a dvd in my drive....then i proceed to compile.

worked for me on 2 laptops and 2 desktops here.

I was wondering about that. I used the deb files.

---

### Post by QDR06VV9 on 2013-11-01
> **sammiev said:**
> I was wondering about that. I used the deb files.

This has been going on from kernels 3.10 and newer.
Many many posts on this they are aware!
(No problem with this usb stick on kernels before 3.10.3 -- 3.9.x, 3.10.2)
foomans post #35 also works for me..
From Here [http://distrowatch.com/weekly.php?issue=20130826](http://distrowatch.com/weekly.php?issue=20130826)
```
Do you have USB devices which regularly disconnect when they are plugged  into your Linux-powered computer? 
If so it may not be a fault of the  device as some people have long thought. Sarah Sharp, who has been  working on USB drivers
 in the Linux kernel for eight years and who was  at the forefront of bringing USB 3.0 support to the kernel, has made an [interesting discovery]("https://plus.google.com/116960357493251979546/posts/RZpndv4BCCD")
. Namely, it seems that the core USB system does not give USB devices long enough to wake up which can cause disconnects. 
"If  the USB core attempts to access those ports while the device is still  coming out of resume, such as issuing transfers to the device, 
or  resetting the port, the device will disconnect, or transfer errors will  occur.  This causes the USB core to mark the device as disconnected.
" No doubt we will soon see a fix for this issue arriving in future kernel updates.
```

---

### Post by VinDSL on 2013-11-01
Hrm...

I'm getting closer:

```
vindsl@Zuul:~$ ls -laR /dev/disk
/dev/disk:
total 0
drwxr-xr-x  6 root root  120 Nov  1 17:11 .
drwxr-xr-x 14 root root 4200 Nov  1 17:13 ..
drwxr-xr-x  2 root root  260 Nov  1 17:11 by-id
drwxr-xr-x  2 root root  100 Nov  1 17:11 by-label
drwxr-xr-x  2 root root   80 Nov  1 17:11 by-path
drwxr-xr-x  2 root root  180 Nov  1 17:11 by-uuid

/dev/disk/by-id:
total 0
drwxr-xr-x 2 root root 260 Nov  1 17:11 .
drwxr-xr-x 6 root root 120 Nov  1 17:11 ..
lrwxrwxrwx 1 root root   9 Nov  1 17:11 ata-HP_DVD_Writer_1040r -> ../../sr0
lrwxrwxrwx 1 root root   9 Nov  1 17:11 ata-MAXTOR_STM3160812AS_5LSBRTN4 -> ../../sda
lrwxrwxrwx 1 root root  10 Nov  1 17:11 ata-MAXTOR_STM3160812AS_5LSBRTN4-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 Nov  1 17:11 ata-MAXTOR_STM3160812AS_5LSBRTN4-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 Nov  1 17:11 ata-MAXTOR_STM3160812AS_5LSBRTN4-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 Nov  1 17:11 ata-MAXTOR_STM3160812AS_5LSBRTN4-part4 -> ../../sda4
lrwxrwxrwx 1 root root  10 Nov  1 17:11 ata-MAXTOR_STM3160812AS_5LSBRTN4-part5 -> ../../sda5
lrwxrwxrwx 1 root root  10 Nov  1 17:11 ata-MAXTOR_STM3160812AS_5LSBRTN4-part6 -> ../../sda6
lrwxrwxrwx 1 root root  10 Nov  1 17:11 ata-MAXTOR_STM3160812AS_5LSBRTN4-part7 -> ../../sda7
lrwxrwxrwx 1 root root   9 Nov  1 17:11 usb-_USB_Flash_Memory_0013729B6607EAC0D57A01E6-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 Nov  1 17:11 usb-_USB_Flash_Memory_0013729B6607EAC0D57A01E6-0:0-part1 -> ../../sdb1

/dev/disk/by-label:
total 0
drwxr-xr-x 2 root root 100 Nov  1 17:11 .
drwxr-xr-x 6 root root 120 Nov  1 17:11 ..
lrwxrwxrwx 1 root root   9 Nov  1 17:11 DRTHING -> ../../sr0
lrwxrwxrwx 1 root root  10 Nov  1 17:11 Ubuntu\x2010.10 -> ../../sda1
lrwxrwxrwx 1 root root  10 Nov  1 17:11 Ubuntu\x2013.10 -> ../../sda5

/dev/disk/by-path:
total 0
drwxr-xr-x 2 root root  80 Nov  1 17:11 .
drwxr-xr-x 6 root root 120 Nov  1 17:11 ..
lrwxrwxrwx 1 root root   9 Nov  1 17:11 pci-0000:00:1d.7-usb-0:2:1.0-scsi-0:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 Nov  1 17:11 pci-0000:00:1d.7-usb-0:2:1.0-scsi-0:0:0:0-part1 -> ../../sdb1

/dev/disk/by-uuid:
total 0
drwxr-xr-x 2 root root 180 Nov  1 17:11 .
drwxr-xr-x 6 root root 120 Nov  1 17:11 ..
lrwxrwxrwx 1 root root  10 Nov  1 17:11 17887ede-93ff-469f-8bda-a29be0cc03c5 -> ../../sda4
lrwxrwxrwx 1 root root  10 Nov  1 17:11 1835824f-9aba-48ba-874b-6955be247395 -> ../../sda7
lrwxrwxrwx 1 root root  10 Nov  1 17:11 28a17342-3d9b-4306-96cf-3bd092645ce7 -> ../../sda5
lrwxrwxrwx 1 root root  10 Nov  1 17:11 5a139fb5-0664-4150-b65a-d73852369ae8 -> ../../sda1
lrwxrwxrwx 1 root root  10 Nov  1 17:11 64F2-B57F -> ../../sdb1
lrwxrwxrwx 1 root root  10 Nov  1 17:11 ba01bbc8-e888-4891-ade4-923ec2d29946 -> ../../sda6
lrwxrwxrwx 1 root root  10 Nov  1 17:11 d75f3ee2-ce9d-4408-b39a-8e8b7bab8ae6 -> ../../sda3
vindsl@Zuul:~$ 

```

I found a usb mass storage option that wasn't enabled.  So, I made sure scsi support was enabled (it was), and added usb mass storage to the mix.

It finds the usb flash and dvd drive now, but when I try to /mnt them, I'm getting a superblock error.  Guess I should have enabled that option too.  LoL!

Continuing...

---

### Post by VinDSL on 2013-11-01
Whoops!

```
vindsl@Zuul:~$ sudo mkdir /mnt/VinDSL

```

```
vindsl@Zuul:~$ sudo mount /dev/sdb1 /mnt/VinDSL
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```
vindsl@Zuul:~$ dmesg | tail -n15

<SNIP>

[   84.757957] FAT-fs (sdb1): **[COLOR="#0000CD"]IO charset iso8859-1 not found[/COLOR]**
[  108.024660] FAT-fs (sdb1): **[COLOR="#0000CD"]IO charset iso8859-1 not found[/COLOR]**
[  117.435884] FAT-fs (sdb1): **[COLOR="#0000CD"]IO charset iso8859-1 not found[/COLOR]**
[ 1051.425708] FAT-fs (sdb1): **[COLOR="#0000CD"]IO charset iso8859-1 not found[/COLOR]**

```

Guess I better go fix that...  :D

---

### Post by QDR06VV9 on 2013-11-01
> **VinDSL said:**
> Whoops!

```
vindsl@Zuul:~$ sudo mkdir /mnt/VinDSL

```

```
vindsl@Zuul:~$ sudo mount /dev/sdb1 /mnt/VinDSL
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```
vindsl@Zuul:~$ dmesg | tail -n15

<SNIP>

[   84.757957] FAT-fs (sdb1): **[COLOR=#0000CD]IO charset iso8859-1 not found[/COLOR]**
[  108.024660] FAT-fs (sdb1): **[COLOR=#0000CD]IO charset iso8859-1 not found[/COLOR]**
[  117.435884] FAT-fs (sdb1): **[COLOR=#0000CD]IO charset iso8859-1 not found[/COLOR]**
[ 1051.425708] FAT-fs (sdb1): **[COLOR=#0000CD]IO charset iso8859-1 not found[/COLOR]**

```

Guess I better go fix that...  :D

Ah Vin I'm just setting here smiling:D

---

### Post by VinDSL on 2013-11-01
Heh!  Think I finally found the little booger.  :)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-1-nov-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-nov-2013-1.png")[/INDENT]


Continuing...

---

### Post by cariboo on 2013-11-01
Looking at my current kernel config file, this is what the DOS/FAT/NT Filesystem section looks like:

```
#
# DOS/FAT/NT Filesystems
#
CONFIG_FAT_FS=y
CONFIG_MSDOS_FS=m
CONFIG_VFAT_FS=y
CONFIG_FAT_DEFAULT_CODEPAGE=437
CONFIG_FAT_DEFAULT_IOCHARSET="iso8859-1"
CONFIG_NTFS_FS=m
# CONFIG_NTFS_DEBUG is not set
# CONFIG_NTFS_RW is not set
```

BTW, this is for one of  the default 3.11.0-12 Ubuntu kernels.

---

### Post by VinDSL on 2013-11-01
> **cariboo907 said:**
> Looking at my current kernel config file, this is what the DOS/FAT/NT Filesystem section looks like [...]
Thanks.

Funny you should post that.

I double-checked my .config file before compiling the kernel, and it looks the same as yours now, but my ISP connection is motorboating up n' down.

Compile went well, and now my usb stick is mounted and working properly.

Now, I need to fix the dvd drive.  LoL!

When I try to mount it, it says:

```
vindsl@Zuul:~$ sudo mount /dev/sr0 /mnt/VinDSL
mount: unknown filesystem type 'udf'
```

Sheesh! :)

---

### Post by VinDSL on 2013-11-01
```
filesystem type 'udf'
```

That was a piece_of_cake to find.

I'll add that, and all the <new> types too.

Okay, here goes nothing...  ;)

EDIT

Here's how it ended up in .config

```
#
# CD-ROM/DVD Filesystems
#
CONFIG_ISO9660_FS=y
CONFIG_JOLIET=y
CONFIG_ZISOFS=y
CONFIG_UDF_FS=y
CONFIG_UDF_NLS=y
```

---

### Post by VinDSL on 2013-11-02
Perfecto!

```
indsl@Zuul:~$ sudo fdisk -l
[sudo] password for vindsl:         

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20964824    10482381   83  Linux
/dev/sda2       156296446   312575999    78139777    5  Extended
/dev/sda3        20965376   154189823    66612224   83  Linux
/dev/sda4       154189824   156295167     1052672   82  Linux swap / Solaris
/dev/sda5       156296448   177268735    10486144   83  Linux
/dev/sda6       310474752   312575999     1050624   82  Linux swap / Solaris
/dev/sda7       177270784   310472703    66600960   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 3926 MB, 3926949888 bytes
121 heads, 62 sectors/track, 1022 cylinders, total 7669824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00010d8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7667043     3833491    c  W95 FAT32 (LBA)
vindsl@Zuul:~$ lsusb
Bus 001 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
vindsl@Zuul:~$ ls -laR /dev/disk
/dev/disk:
total 0
drwxr-xr-x  6 root root  120 Nov  1 21:38 .
drwxr-xr-x 14 root root 4200 Nov  1 21:41 ..
drwxr-xr-x  2 root root  260 Nov  1 21:38 by-id
drwxr-xr-x  2 root root  100 Nov  1 21:39 by-label
drwxr-xr-x  2 root root   80 Nov  1 21:38 by-path
drwxr-xr-x  2 root root  180 Nov  1 21:38 by-uuid

/dev/disk/by-id:
total 0
drwxr-xr-x 2 root root 260 Nov  1 21:38 .
drwxr-xr-x 6 root root 120 Nov  1 21:38 ..
lrwxrwxrwx 1 root root   9 Nov  1 21:39 ata-HP_DVD_Writer_1040r -> ../../sr0
lrwxrwxrwx 1 root root   9 Nov  1 21:39 ata-MAXTOR_STM3160812AS_5LSBRTN4 -> ../../sda
lrwxrwxrwx 1 root root  10 Nov  1 21:39 ata-MAXTOR_STM3160812AS_5LSBRTN4-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 Nov  1 21:39 ata-MAXTOR_STM3160812AS_5LSBRTN4-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 Nov  1 21:39 ata-MAXTOR_STM3160812AS_5LSBRTN4-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 Nov  1 21:39 ata-MAXTOR_STM3160812AS_5LSBRTN4-part4 -> ../../sda4
lrwxrwxrwx 1 root root  10 Nov  1 21:39 ata-MAXTOR_STM3160812AS_5LSBRTN4-part5 -> ../../sda5
lrwxrwxrwx 1 root root  10 Nov  1 21:39 ata-MAXTOR_STM3160812AS_5LSBRTN4-part6 -> ../../sda6
lrwxrwxrwx 1 root root  10 Nov  1 21:39 ata-MAXTOR_STM3160812AS_5LSBRTN4-part7 -> ../../sda7
lrwxrwxrwx 1 root root   9 Nov  1 21:39 usb-_USB_Flash_Memory_0013729B6607EAC0D57A01E6-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 Nov  1 21:39 usb-_USB_Flash_Memory_0013729B6607EAC0D57A01E6-0:0-part1 -> ../../sdb1

/dev/disk/by-label:
total 0
drwxr-xr-x 2 root root 100 Nov  1 21:39 .
drwxr-xr-x 6 root root 120 Nov  1 21:38 ..
lrwxrwxrwx 1 root root   9 Nov  1 21:39 DRTHING -> ../../sr0
lrwxrwxrwx 1 root root  10 Nov  1 21:39 Ubuntu\x2010.10 -> ../../sda1
lrwxrwxrwx 1 root root  10 Nov  1 21:39 Ubuntu\x2013.10 -> ../../sda5

/dev/disk/by-path:
total 0
drwxr-xr-x 2 root root  80 Nov  1 21:38 .
drwxr-xr-x 6 root root 120 Nov  1 21:38 ..
lrwxrwxrwx 1 root root   9 Nov  1 21:39 pci-0000:00:1d.7-usb-0:2:1.0-scsi-0:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 Nov  1 21:39 pci-0000:00:1d.7-usb-0:2:1.0-scsi-0:0:0:0-part1 -> ../../sdb1

/dev/disk/by-uuid:
total 0
drwxr-xr-x 2 root root 180 Nov  1 21:38 .
drwxr-xr-x 6 root root 120 Nov  1 21:38 ..
lrwxrwxrwx 1 root root  10 Nov  1 21:39 17887ede-93ff-469f-8bda-a29be0cc03c5 -> ../../sda4
lrwxrwxrwx 1 root root  10 Nov  1 21:39 1835824f-9aba-48ba-874b-6955be247395 -> ../../sda7
lrwxrwxrwx 1 root root  10 Nov  1 21:39 28a17342-3d9b-4306-96cf-3bd092645ce7 -> ../../sda5
lrwxrwxrwx 1 root root  10 Nov  1 21:39 5a139fb5-0664-4150-b65a-d73852369ae8 -> ../../sda1
lrwxrwxrwx 1 root root  10 Nov  1 21:39 64F2-B57F -> ../../sdb1
lrwxrwxrwx 1 root root  10 Nov  1 21:39 ba01bbc8-e888-4891-ade4-923ec2d29946 -> ../../sda6
lrwxrwxrwx 1 root root  10 Nov  1 21:39 d75f3ee2-ce9d-4408-b39a-8e8b7bab8ae6 -> ../../sda3
vindsl@Zuul:~$
```

---

### Post by QDR06VV9 on 2013-11-02
> **VinDSL said:**
> Perfecto!



Nice Job Bud!
There is a real sense of accomplishment from that! 
After All isn't it that what keeps us here.LOL

---

### Post by VinDSL on 2013-11-02
> **runrickus said:**
> [...] isn't it that what keeps us here.LOL
You bet!

I hate it when things just work.

That said...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-1-nov-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-nov-2013-2.png")[/INDENT]


Think I'll kick back, watch a movie, and delete some kernels...  :D

---

### Post by QDR06VV9 on 2013-11-02
> **VinDSL said:**
> You bet!

I hate it when things just work.  :D
I seriously just feel out of my chair!!!
Still laughing.:D

---

### Post by cariboo on 2013-11-02
@VinDsl, I don't have an entry in /dev for DVD, but it works without a problem:

```
cariboo@alexis:/dev$ ls -l dvd
ls: cannot access dvd: No such file or directory
```

when I insert a dvd, it just works:

```
dmesg | tail -n 1
[ 3599.620789] UDF-fs: INFO Mounting volume 'PACIFIC_RIM', timestamp 2013/08/30 10:33 (1e5c)
```

---

### Post by VinDSL on 2013-11-02
> **cariboo907 said:**
> ```
dmesg | tail -n 1
[ 3599.620789] UDF-fs: INFO Mounting volume 'PACIFIC_RIM', timestamp 2013/08/30 10:33 (1e5c)
```
Watching [adult venue], are we?!?!?  LoL!  :D

---

### Post by VinDSL on 2013-11-02
> **cariboo907 said:**
> @VinDsl, I don't have an entry in /dev for DVD, but it works without a problem:

```
cariboo@alexis:/dev$ ls -l dvd
ls: cannot access dvd: No such file or directory
```

when I insert a dvd, it just works[...]
I'm as lazy as the next guy.  I let menuconfig do the work.

When I found the section with the 'udf' filesystem type (and several <new> ones) I clicked them all and saved the .config file.

Before taking the time to compile the kernel, I do a cursory examination of .config -- and that section was in there.

I didn't look at .config before I ran menuconfig, so I don't know if that dvd section was already there, or menuconfig added it.

Regardless, my dvd drive is playing movies like a charm, sooo...

All's well that ends well, yes?  ;)

---

