---
title: "Ubuntu 14.04 trusty alpha?"
date: 2013-10-23
forum: Ubuntu Development Version
---

### Post by Redalien0304 on 2013-10-23
Want to try out Ubuntu 14.04 alpha. Tried here [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) the daily Build put on usb stick with unetbootin checked the details says 13.10?? So is this Right or wrong?? or just the way an aplha starts out??

---

### Post by sudodus on 2013-10-23
I think it was like that when 13.10 started out too. This new version will get more and more features showing '14.04 properties' ...

---

### Post by grahammechanical on 2013-10-23
Ubuntu 14.04 will not have any Alpha releases and only one beta release. The flavours of Ubuntu may have 2 Alpha releases and 2 beta releases if the developers so choose. For those flavours that opt-in Alpha 1 will be released on Thursday 19th December according to the official schedule.

Each development release is built very much upon the last released version. The best place to get ISO images of the development branch is here

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

But as you notice, at present there are no ISO images for Trusty Tahr. It will take a few days before we see them. An important factor to consider if you install that image is the repositories. Are saucy repositories or trusty repositories?

Regards

---

### Post by Redalien0304 on 2013-10-23
What is Repos list for 14.04 trusty? what to change?

---

### Post by grahammechanical on 2013-10-23
@redalien0304

Have a look through this thread

[http://ubuntuforums.org/showthread.php?t=2183074](http://ubuntuforums.org/showthread.php?t=2183074)

If you download one of those trusty ISO images, install and then update you should find that things are working fine. I have just done it. It will look exaclty like 13.10 but if you run

```
lsb_release -a
```

you should see this

> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty

And you are on the beginning of a journey. This seems to be happening a lot quicker than previous development cycles. Two things to remember. 1) Don't ever accept the offer of a partial upgrade. 2) The Extras repositories are not open so expect to get an error out of Update Manager. Just OK and the update will take place as normal.



Regards.

---

### Post by zika on 2013-10-23
> **grahammechanical said:**
> 1) Don't ever accept the offer of a partial upgrade.So no kernel upgrades, no new packages etc... ?
Partial upgrade is a must in many cases but it should be performed with caution and full understanding...
Did not we have sticky about that?

---

### Post by Redalien0304 on 2013-10-23
ok ty grammechanial. already did that when i found that. I came across the thread. Thanks

---

### Post by cariboo on 2013-10-23
> **zika said:**
> So no kernel upgrades, no new packages etc... ?
Partial upgrade is a must in many cases but it should be performed with caution and full understanding...
Did not we have sticky about that?

I agree with you in part, but we shouldn't recommend partial upgrades unless the user is an experienced Ubuntu development release tester. Doing a partial upgrade can get a new tester in a whole heap of trouble, so for the most part I will still recommend against doing a partial upgrade.

Yes there is a sticky [here]("http://ubuntuforums.org/showthread.php?t=2181769"), look at the common problems link.

---

### Post by zika on 2013-10-24
> **cariboo907 said:**
> I agree with you in part, but we shouldn't recommend partial upgrades unless the user is an experienced Ubuntu development release tester. Doing a partial upgrade can get a new tester in a whole heap of trouble, so for the most part I will still recommend against doing a partial upgrade.

Yes there is a sticky [here]("http://ubuntuforums.org/showthread.php?t=2181769"), look at the common problems link.I do think that we agree in each and every part. I (certainly and easily checked) do not recommend PU. But, also, I'm aware that it is needed in many situations.. Especially in U+1Testing. So, as far as I can see we do not have any disagreement...

---

### Post by xc3RnbFO8P on 2013-10-24
To do, or not to do partical upgrades...

[[img]http://farm3.staticflickr.com/2872/10457534414_1fa08cb186_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/10457534414/)
[Screenshot from 2013-10-24 15:06:28](http://www.flickr.com/photos/96052779@N07/10457534414/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by xc3RnbFO8P on 2013-10-24
Well, after restart all seems to work.
```
rig@rig-Aspire-R3600:~$ echo && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || echo && cat /proc/version  && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/  /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    LG Flatron W2452T " && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

Current Date/Time: tor okt 24 14:15:01 UTC 2013
Distro Release: Ubuntu Trusty Tahr (development branch)
Kernel Release: Linux version 3.11.0-13-generic (buildd@roseapple) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013
Gnome Release: GNOME Shell 3.8.4
Unity Release: unity 7.1.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: ION/integrated/SSE2
OpenGL version string:  3.3.0 NVIDIA 331.13

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
Installed-Size: 130
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.1.0-2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.14), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: [http://mesa3d.org/](http://mesa3d.org/)

Package: mesa-common-dev
  Version: 9.2.2-1ubuntu1

Package: xserver-xorg-core
  Installed: 2:1.14.3-3ubuntu3

Package: xserver-common
  Installed: 2:1.14.3-3ubuntu3

Package: xserver-xephyr
  Installed: 2:1.14.3-3ubuntu3

Tree Map of PCI Devices:
-[0000:00]-+-00.0  NVIDIA Corporation MCP79 Host Bridge
           +-00.1  NVIDIA Corporation MCP79 Memory Controller
           +-03.0  NVIDIA Corporation MCP79 LPC Bridge
           +-03.1  NVIDIA Corporation MCP79 Memory Controller
           +-03.2  NVIDIA Corporation MCP79 SMBus
           +-03.3  NVIDIA Corporation MCP79 Memory Controller
           +-03.5  NVIDIA Corporation MCP79 Co-processor
           +-04.0  NVIDIA Corporation MCP79 OHCI USB 1.1 Controller
           +-04.1  NVIDIA Corporation MCP79 EHCI USB 2.0 Controller
           +-08.0  NVIDIA Corporation MCP79 High Definition Audio
           +-09.0-[01]--
           +-0a.0  NVIDIA Corporation MCP79 Ethernet
           +-0b.0  NVIDIA Corporation MCP79 AHCI Controller
           +-0c.0-[02]--
           +-10.0-[03]----00.0  NVIDIA Corporation ION VGA
           +-15.0-[04]--
           +-16.0-[05]----00.0  Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express)
           +-17.0-[06]--
           \-18.0-[07]--

Display Properties:
 lcd monitor:    LG Flatron W2452T 
  dimensions:    1920x1200 pixels (508x318 millimeters)
  resolution:    96x96 dots per inch

rig@rig-Aspire-R3600:~$ 

```

---

### Post by philinux on 2013-10-24
> **Ringi said:**
> To do, or not to do partical upgrades...


I don't get partial upgrades as I never use update-manager in development.

---

### Post by xc3RnbFO8P on 2013-10-25
I do partial upgrades because I'm not sure what to do with all these sessions, and it works (I have been upgrading since 12.04, no fresh install)

[[img]http://farm4.staticflickr.com/3671/10462832316_21db12785f_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/10462832316/)
[Lightdm](http://www.flickr.com/photos/96052779@N07/10462832316/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by QDR06VV9 on 2013-10-25
> **philinux said:**
> I don't get partial upgrades as I never use update-manager in development.

+1

---

### Post by kevpan8152 on 2013-10-25
It's Technically Speaking not official Alpha yet. It's Pre-Alpha. And there is another way to install it other than using the Nightly Build as well. All you do is use Ventrical's 3 commands to Edit your Sources List on top of a Saucy Installation. Most of the time that's the better way to go this early in the game.

---

### Post by kevpan8152 on 2013-10-25
Cariboo907 has warned us time and time again NOT to do Partial Upgrades. The best way to update is to do a Sudo Apt-Get Update And Sudo Apt-Get Upgrade from the Command Line while using Development Builds. The Code Line is constantly changing and sometimes the Software Updater Code will change while you are Updating causing a Borked Update if you are the Built In Software Updater while it is being Updated. Bottom Line, Using the Software Updater is a NO-NO while you are on a Development Line of Code.

---

### Post by xc3RnbFO8P on 2013-10-31
> **philinux said:**
> I don't get partial upgrades as I never use update-manager in development.

Then you don't see this?

[[img]http://farm3.staticflickr.com/2860/10591714485_2db9a7bc2f_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/10591714485/)
[Screenshot from 2013-10-31 00:32:43](http://www.flickr.com/photos/96052779@N07/10591714485/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by philinux on 2013-10-31
I use synaptic to look at changelogs. I dont read them all sometimes there are far too many.

---

### Post by Cavsfan on 2013-10-31
> **philinux said:**
> I don't get partial upgrades as I never use update-manager in development.

> **philinux said:**
> I use synaptic to look at changelogs. I dont read them all sometimes there are far too many.

I remember Ranch Hand telling me to use CLI not update manager. As you may recall he called it update mangler. :)

Someone here in this forum showed me how to make it easier than typing in **sudo apt-get update && sudo apt-get upgrade** over and over.

Just put this in .bashrc and logout and back in then enter **ud**, **ud2** or **ud3** in terminal depending on what you need to do.
Of course **ud** first and the others as needed.

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
alias ud3='sudo apt-get autoremove'
```

BTW I broke my Trusty install with todays updates. Not sure what to do. Guess I'll give it some time and see if it straightens out.
I tried to use Synaptic to fix some errors it was getting. I fixed them but broke it. If I would have stuck to the golden rule I probably wouldn't have broken it.

---

### Post by Chanath on 2013-10-31
Ringi, what is your bottom panel in #10? Is it the Cairo dock? :p
Lovely screen!

---

### Post by rrnbtter on 2013-10-31
Greetings,

> **Cavsfan said:**
> 
BTW I broke my Trusty install with todays updates. Not sure what to do. Guess I'll give it some time and see if it straightens out.
I tried to use Synaptic to fix some errors it was getting. I fixed them but broke it. If I would have stuck to the golden rule I probably wouldn't have broken it.

I started getting desktop mis-behavior a few days ago it corrected starting with yesterday's updates. I suppose the degree of breakage would vary with hardware. I will usually wait for updates to correct breakage so long as I can log-in to the system with some useability. In any case the problem did'nt clear with just one update, it was a series over two days.

---

### Post by xc3RnbFO8P on 2013-10-31
After upgrade today:
```
root@rig-Aspire-R3600:/home/rig# echo && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -av && echo -n "Kernel Release: " || echo && cat /proc/version  && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && grep -i memory   /var/log/Xorg.0.log &&  dmidecode --type 17 echo && echo dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/  /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    LG Flatron W2452T " && echo && xdpyinfo | grep -E '(resolution|dimensions)' && sensors && parted /dev/sda print && echo

Current Date/Time: tor okt 31 21:26:40 UTC 2013
Distro Release: No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Trusty Tahr (development branch)
Release:	14.04
Codename:	trusty
Kernel Release: Linux version 3.12.0-1-generic (buildd@roseapple) (gcc version 4.8.2 (Ubuntu/Linaro 4.8.2-1ubuntu2) ) #3-Ubuntu SMP Tue Oct 29 18:41:32 UTC 2013
Gnome Release: GNOME Shell 3.8.4
Unity Release: unity 7.1.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: ION/integrated/SSE2
OpenGL version string:  3.3.0 NVIDIA 331.13

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

[    34.267] (--) NVIDIA(0): Memory: 524288 kBytes
[    34.320] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    34.417] (==) NVIDIA(0): Disabling shared memory pixmaps
# dmidecode 2.12
SMBIOS 2.6 present.

Handle 0x0010, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000E
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 800 MHz
	Manufacturer: Nanya         
	Serial Number: 11365D0B
	Asset Tag: None        
	Part Number: NT2GT64U8HD0BN-AD 

Handle 0x0012, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000E
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM2
	Bank Locator: BANK2
	Type: DDR2
	Type Detail: Synchronous
	Speed: 800 MHz
	Manufacturer: Nanya         
	Serial Number: 14365DAC
	Asset Tag: None        
	Part Number: NT2GT64U8HD0BN-AD 

dpkg -s mesa-utils

Package: mesa-common-dev
  Version: 9.2.2-1ubuntu1

Package: xserver-xorg-core
  Installed: 2:1.14.3-3ubuntu4

Package: xserver-common
  Installed: 2:1.14.3-3ubuntu4

Package: xserver-xephyr
  Installed: 2:1.14.3-3ubuntu4

Tree Map of PCI Devices:
-[0000:00]-+-00.0  NVIDIA Corporation MCP79 Host Bridge
           +-00.1  NVIDIA Corporation MCP79 Memory Controller
           +-03.0  NVIDIA Corporation MCP79 LPC Bridge
           +-03.1  NVIDIA Corporation MCP79 Memory Controller
           +-03.2  NVIDIA Corporation MCP79 SMBus
           +-03.3  NVIDIA Corporation MCP79 Memory Controller
           +-03.5  NVIDIA Corporation MCP79 Co-processor
           +-04.0  NVIDIA Corporation MCP79 OHCI USB 1.1 Controller
           +-04.1  NVIDIA Corporation MCP79 EHCI USB 2.0 Controller
           +-08.0  NVIDIA Corporation MCP79 High Definition Audio
           +-09.0-[01]--
           +-0a.0  NVIDIA Corporation MCP79 Ethernet
           +-0b.0  NVIDIA Corporation MCP79 AHCI Controller
           +-0c.0-[02]--
           +-10.0-[03]----00.0  NVIDIA Corporation ION VGA
           +-15.0-[04]--
           +-16.0-[05]----00.0  Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express)
           +-17.0-[06]--
           \-18.0-[07]--

Display Properties:
 lcd monitor:    LG Flatron W2452T 
  dimensions:    1920x1200 pixels (508x318 millimeters)
  resolution:    96x96 dots per inch
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +83.0°C  (crit = +125.0°C)
Core 1:       +84.0°C  (crit = +125.0°C)

adt7476-i2c-0-2e
Adapter: SMBus nForce2 adapter at 4d00
in0:          +1.83 V  (min =  +0.00 V, max =  +3.31 V)
Vcore:        +1.17 V  (min =  +0.00 V, max =  +2.99 V)
+3.3V:        +3.32 V  (min =  +2.96 V, max =  +3.61 V)
+5V:          +5.07 V  (min =  +4.48 V, max =  +5.50 V)
+12V:         +0.98 V  (min =  +0.00 V, max = +15.69 V)
fan1:        2551 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
fan4:           0 RPM  (min =    0 RPM)
temp1:        +61.5°C  (low  = -127.0°C, high = +127.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)
M/B Temp:     +42.5°C  (low  = -127.0°C, high = +127.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)
temp3:        +51.5°C  (low  = -127.0°C, high = +127.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)
cpu0_vid:    +1.419 V

Model: ATA WDC WD3200BEVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  317GB  317GB   primary   ext4            boot
 2      317GB   320GB  3219MB  extended
 5      317GB   320GB  3219MB  logical   linux-swap(v1)
```

---

### Post by Cavsfan on 2013-11-01
It turned out the be the video driver I had installed - 319.60. I installed the 319.32 driver by getting in through the 3.11 kernel and then everything was fine.
The 3.12 kernel did not like that driver for some reason at least not on my machine.

I opened this thread about it [http://ubuntuforums.org/showthread.php?t=2185004](http://ubuntuforums.org/showthread.php?t=2185004)

```
Current Date/Time: Fri Nov  1 16:41:32 UTC 2013
Distro Release: No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
Kernel Release: Linux version 3.12.0-1-generic (buildd@roseapple) (gcc version 4.8.2 (Ubuntu/Linaro 4.8.2-1ubuntu2) ) #3-Ubuntu SMP Tue Oct 29 18:41:32 UTC 2013
Gnome Release: GNOME Shell 3.8.4
Unity Release: unity 7.1.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9800 GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 319.32

Not software rendered:    [COLOR=#00ff00]yes[/COLOR]
Not blacklisted:          [COLOR=#00ff00]yes[/COLOR]
GLX fbconfig:             [COLOR=#00ff00]yes[/COLOR]
GLX texture from pixmap:  [COLOR=#00ff00]yes[/COLOR]
GL npot or rect textures: [COLOR=#00ff00]yes[/COLOR]
GL vertex program:        [COLOR=#00ff00]yes[/COLOR]
GL fragment program:      [COLOR=#00ff00]yes[/COLOR]
GL vertex buffer object:  [COLOR=#00ff00]yes[/COLOR]
GL framebuffer object:    [COLOR=#00ff00]yes[/COLOR]
GL version is 1.4+:       [COLOR=#00ff00]yes[/COLOR]

Unity 3D supported:       [COLOR=#00ff00]yes[/COLOR]

[    25.048] (--) NVIDIA(0): [COLOR=#ff0000]Memory[/COLOR]: 1048576 kBytes
[    25.151] (II) NVIDIA: Using 768.00 MB of virtual [COLOR=#ff0000]memory[/COLOR] for indirect [COLOR=#ff0000]memory[/COLOR] access.
[    25.292] (==) NVIDIA(0): Disabling shared [COLOR=#ff0000]memory[/COLOR] pixmaps
# dmidecode 2.12
SMBIOS 2.5 present.

Handle 0x0029, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0027
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK0
    Type: SDRAM
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0

Handle 0x002B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0027
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM2
    Bank Locator: BANK1
    Type: SDRAM
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1

dpkg -s mesa-utils

Package: mesa-common-dev
dpkg-query: package 'mesa-common-dev' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

Package: xserver-xorg-core
  [COLOR=#ff0000]Installed[/COLOR]: 2:1.14.3-3ubuntu4

Package: xserver-common
  [COLOR=#ff0000]Installed[/COLOR]: 2:1.14.3-3ubuntu4

Package: xserver-xephyr
  [COLOR=#ff0000]Installed[/COLOR]: 2:1.14.3-3ubuntu4

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller
           +-01.0-[01]----00.0  NVIDIA Corporation G92 [GeForce 9800 GT]
           +-1b.0  Intel Corporation NM10/ICH7 Family High Definition Audio Controller
           +-1c.0-[02]--
           +-1c.1-[03]----00.0  Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller
           +-1d.0  Intel Corporation NM10/ICH7 Family USB UHCI Controller #1
           +-1d.1  Intel Corporation NM10/ICH7 Family USB UHCI Controller #2
           +-1d.2  Intel Corporation NM10/ICH7 Family USB UHCI Controller #3
           +-1d.3  Intel Corporation NM10/ICH7 Family USB UHCI Controller #4
           +-1d.7  Intel Corporation NM10/ICH7 Family USB2 EHCI Controller
           +-1e.0-[04]--
           +-1f.0  Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge
           +-1f.1  Intel Corporation 82801G (ICH7 Family) IDE Controller
           +-1f.2  Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode]
           \-1f.3  Intel Corporation NM10/ICH7 Family SMBus Controller

Display Properties:
 lcd monitor:    Hanns-G HG281 
  [COLOR=#ff0000]dimensions[/COLOR]:    1920x1200 pixels (508x318 millimeters)
  [COLOR=#ff0000]resolution[/COLOR]:    96x96 dots per inch
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +42.0°C  (high = +76.0°C, crit = +100.0°C)
Core 1:       +42.0°C  (high = +76.0°C, crit = +100.0°C)
Core 2:       +40.0°C  (high = +76.0°C, crit = +100.0°C)
Core 3:       +40.0°C  (high = +76.0°C, crit = +100.0°C)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.36 V  
in1:          +1.18 V  (max =  +2.04 V)
in2:          +1.00 V  
in3:          +0.83 V  
in4:          +0.98 V  
in5:          +1.10 V  
in6:          +0.90 V  
3VSB:         +3.36 V  
Vbat:         +3.31 V  
fan1:        2392 RPM
fan2:        1809 RPM
fan3:        2772 RPM
fan4:           0 RPM  ALARM
temp1:        +31.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:        +34.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +95.0°C, hyst = +91.0°C)  sensor = thermistor
temp3:        +31.0°C  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor
```

---

### Post by jerrylamos on 2013-11-01
> **philinux said:**
> I don't get partial upgrades as I never use update-manager in development.
I don't either, or for that matter out of development.  Update manager has screwed me too many times.
I update when I want to

---

### Post by jerrylamos on 2013-11-01
> **sudodus said:**
> I think it was like that when 13.10 started out too. This new version will get more and more features showing '14.04 properties' ...
Very early on I just copy last .iso, example saucy, then rename it trusty, then update.  If it's a little later I edit apt.sources.list for the new name.

Typically nothing much happens until blooey a number of updates that have never seen each other get tangled up.....

---

### Post by BlackMaxPhoto on 2014-02-06
-deleted-

---

