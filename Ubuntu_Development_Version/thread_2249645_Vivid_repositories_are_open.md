---
title: "Vivid repositories are open"
date: 2014-10-23
forum: Ubuntu Development Version
---

### Post by PaulW2U on 2014-10-23
From the #ubuntu-release channel on IRC

```
22:13:56        -- | Notice(queuebot): Unapproved: base-files (vivid-proposed/main) [7.2ubuntu7 => 7.2ubuntu8] (core)    
```

Package uploads have commenced. No break between releases then. ;)

---

### Post by ventrical on 2014-10-23
Thnx. I mentioned that in another forum .. but better to be here . I have an hdd  sources.list already set for vivid.

Regards.

---

### Post by cariboo on 2014-10-23
The[ vivid-changes mailing list]("https://lists.ubuntu.com/mailman/listinfo/Vivid-changes") is up and ready to go.

---

### Post by zika on 2014-10-24
+1 on workplace machine. My home machine (where most of work is done) is still under consideration.

---

### Post by slickymaster on 2014-10-24
And so it begins :p

```
slickymaster@VirtualBox:~$ sudo sed -i 's/utopic/vivid/g' /etc/apt/sources.list
[sudo] password for slickymaster: 
slickymaster@VirtualBox:~$ sudo apt-get update 
Ign http://dl.google.com stable InRelease
Ign http://security.ubuntu.com vivid-security InRelease                        
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Get:1 http://security.ubuntu.com vivid-security Release.gpg [933 B]            
Hit http://dl.google.com stable/main i386 Packages                             
Get:2 http://security.ubuntu.com vivid-security Release [59,7 kB]              
Get:3 http://security.ubuntu.com vivid-security/main Sources [14 B]            
Get:4 http://security.ubuntu.com vivid-security/restricted Sources [14 B]      
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Get:5 http://security.ubuntu.com vivid-security/universe Sources [14 B]        
Get:6 http://security.ubuntu.com vivid-security/multiverse Sources [14 B]      
Get:7 http://security.ubuntu.com vivid-security/main i386 Packages [14 B]      
Get:8 http://security.ubuntu.com vivid-security/restricted i386 Packages [14 B]
Get:9 http://security.ubuntu.com vivid-security/universe i386 Packages [14 B]  
Get:10 http://security.ubuntu.com vivid-security/multiverse i386 Packages [14 B]
Get:11 http://security.ubuntu.com vivid-security/main Translation-en [14 B]    
Get:12 http://security.ubuntu.com vivid-security/multiverse Translation-en [14 B]
Get:13 http://security.ubuntu.com vivid-security/restricted Translation-en [14 B]
Ign http://pt.archive.ubuntu.com vivid InRelease                               
Get:14 http://security.ubuntu.com vivid-security/universe Translation-en [14 B]
Ign http://pt.archive.ubuntu.com vivid-updates InRelease              
Ign http://pt.archive.ubuntu.com vivid-backports InRelease  
Ign http://extras.ubuntu.com vivid InRelease                
Get:15 http://pt.archive.ubuntu.com vivid Release.gpg [933 B]                  
Ign http://extras.ubuntu.com vivid Release.gpg                                 
Ign http://extras.ubuntu.com vivid Release                                     
Get:16 http://pt.archive.ubuntu.com vivid-updates Release.gpg [933 B]          
Get:17 http://pt.archive.ubuntu.com vivid-backports Release.gpg [933 B]        
Get:18 http://pt.archive.ubuntu.com vivid Release [112 kB]                     
Get:19 http://pt.archive.ubuntu.com vivid-updates Release [59,7 kB]            
Get:20 http://pt.archive.ubuntu.com vivid-backports Release [59,7 kB]          
Err http://extras.ubuntu.com vivid/main Sources                                
  404  Not Found
Err http://extras.ubuntu.com vivid/main i386 Packages                          
  404  Not Found
Ign http://extras.ubuntu.com vivid/main Translation-en_US                      
Get:21 http://pt.archive.ubuntu.com vivid/main Sources [1046 kB]               
Ign http://extras.ubuntu.com vivid/main Translation-en                         
Get:22 http://pt.archive.ubuntu.com vivid/restricted Sources [5115 B]          
Get:23 http://pt.archive.ubuntu.com vivid/universe Sources [6738 kB]           
Get:24 http://pt.archive.ubuntu.com vivid/multiverse Sources [171 kB]          
Get:25 http://pt.archive.ubuntu.com vivid/main i386 Packages [1326 kB]         
Get:26 http://pt.archive.ubuntu.com vivid/restricted i386 Packages [12,6 kB]   
Get:27 http://pt.archive.ubuntu.com vivid/universe i386 Packages [6185 kB]     
Get:28 http://pt.archive.ubuntu.com vivid/multiverse i386 Packages [133 kB]    
Get:29 http://pt.archive.ubuntu.com vivid/main Translation-en [769 kB]         
Get:30 http://pt.archive.ubuntu.com vivid/multiverse Translation-en [101 kB]   
Get:31 http://pt.archive.ubuntu.com vivid/restricted Translation-en [3315 B]   
Get:32 http://pt.archive.ubuntu.com vivid/universe Translation-en [4265 kB]    
Get:33 http://pt.archive.ubuntu.com vivid-updates/main Sources [14 B]          
Get:34 http://pt.archive.ubuntu.com vivid-updates/restricted Sources [14 B]    
Get:35 http://pt.archive.ubuntu.com vivid-updates/universe Sources [14 B]      
Get:36 http://pt.archive.ubuntu.com vivid-updates/multiverse Sources [14 B]    
Get:37 http://pt.archive.ubuntu.com vivid-updates/main i386 Packages [14 B]    
Get:38 http://pt.archive.ubuntu.com vivid-updates/restricted i386 Packages [14 B]
Get:39 http://pt.archive.ubuntu.com vivid-updates/universe i386 Packages [14 B]
Get:40 http://pt.archive.ubuntu.com vivid-updates/multiverse i386 Packages [14 B]
Get:41 http://pt.archive.ubuntu.com vivid-updates/main Translation-en [14 B]   
Get:42 http://pt.archive.ubuntu.com vivid-updates/multiverse Translation-en [14 B]
Get:43 http://pt.archive.ubuntu.com vivid-updates/restricted Translation-en [14 B]
Get:44 http://pt.archive.ubuntu.com vivid-updates/universe Translation-en [14 B]
Get:45 http://pt.archive.ubuntu.com vivid-backports/main Sources [14 B]        
Get:46 http://pt.archive.ubuntu.com vivid-backports/restricted Sources [14 B]  
Get:47 http://pt.archive.ubuntu.com vivid-backports/universe Sources [14 B]    
Get:48 http://pt.archive.ubuntu.com vivid-backports/multiverse Sources [14 B]  
Get:49 http://pt.archive.ubuntu.com vivid-backports/main i386 Packages [14 B]  
Get:50 http://pt.archive.ubuntu.com vivid-backports/restricted i386 Packages [14 B]
Get:51 http://pt.archive.ubuntu.com vivid-backports/universe i386 Packages [14 B]
Get:52 http://pt.archive.ubuntu.com vivid-backports/multiverse i386 Packages [14 B]
Get:53 http://pt.archive.ubuntu.com vivid-backports/main Translation-en [14 B] 
Get:54 http://pt.archive.ubuntu.com vivid-backports/multiverse Translation-en [14 B]
Get:55 http://pt.archive.ubuntu.com vivid-backports/restricted Translation-en [14 B]
Get:56 http://pt.archive.ubuntu.com vivid-backports/universe Translation-en [14 B]
Fetched 21,1 MB in 2min 15s (155 kB/s)                                         
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/vivid/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/vivid/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
slickymaster@VirtualBox:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  base-files libltdl7 tzdata
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 287 kB of archives.
After this operation, 2048 B disk space will be freed.
Do you want to continue? [Y/n] y 
Get:1 http://pt.archive.ubuntu.com/ubuntu/ vivid/main base-files i386 7.2ubuntu8 [68,5 kB]
Get:2 http://pt.archive.ubuntu.com/ubuntu/ vivid/main libltdl7 i386 2.4.2-1.11 [36,8 kB]
Get:3 http://pt.archive.ubuntu.com/ubuntu/ vivid/main tzdata all 2014i-1 [182 kB]
Fetched 287 kB in 3s (93,6 kB/s) 
Preconfiguring packages ...
(Reading database ... 179297 files and directories currently installed.)
Preparing to unpack .../base-files_7.2ubuntu8_i386.deb ...
Unpacking base-files (7.2ubuntu8) over (7.2ubuntu7) ...
Processing triggers for man-db (2.7.0.2-2) ...
Processing triggers for install-info (5.2.0.dfsg.1-4) ...
Processing triggers for plymouth-theme-ubuntu-text (0.9.0-0ubuntu7) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-23-generic
Setting up base-files (7.2ubuntu8) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
Installing new version of config file /etc/os-release ...
Processing triggers for plymouth-theme-ubuntu-text (0.9.0-0ubuntu7) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-23-generic
(Reading database ... 179297 files and directories currently installed.)
Preparing to unpack .../libltdl7_2.4.2-1.11_i386.deb ...
Unpacking libltdl7:i386 (2.4.2-1.11) over (2.4.2-1.10ubuntu1) ...
Preparing to unpack .../tzdata_2014i-1_all.deb ...
Unpacking tzdata (2014i-1) over (2014i-0ubuntu0.14.10) ...
Setting up tzdata (2014i-1) ...

Current default time zone: 'Europe/Lisbon'
Local time is now:      Sex Out 24 10:25:30 WEST 2014.
Universal Time is now:  Fri Oct 24 09:25:30 UTC 2014.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

Setting up libltdl7:i386 (2.4.2-1.11) ...
Processing triggers for libc-bin (2.19-10ubuntu2) ...
```

```
slickymaster@VirtualBox:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid
3.18.0-031800rc1-generic
```

---

### Post by Elfy on 2014-10-24
had to muck about with /usr/share/python-apt/templates/Ubuntu.info wasn't liking ppa's just yet

---

### Post by grahammechanical on 2014-10-24
I am in. Made the change over some hours ago when I read this post. After starting the new day I run updates as usual and there was plenty to come down. Some of them are likely leftovers from Utopic but I think that g++ is pure vivid.

viva vivid!

---

### Post by slickymaster on 2014-10-24
A few hours later, updates start to pile up:```
dnsmasq-base:i386 (2.71-1, 2.72-2), fonts-tlwg-waree:i386 (0.6.1-1, 0.6.1-2), fonts-tlwg-purisa:i386 (0.6.1-1, 0.6.1-2), iw:i386 (3.14-1, 3.17-1), fonts-tlwg-umpush:i386 (0.6.1-1, 0.6.1-2), libgssdp-1.0-3:i386 (0.14.8-2, 0.14.10-1), libgcr-base-3-1:i386 (3.12.2-1, 3.14.0-2), geoip-database:i386 (20140908-1, 20141009-1), fonts-nanum:i386 (20131007-4, 20140930-1), libjte1:i386 (1.19-2, 1.20-1), libclutter-gtk-1.0-0:i386 (1.5.2-2, 1.6.0-1), hwdata:i386 (0.249-1, 0.267-1), fonts-tlwg-laksaman:i386 (0.6.1-1, 0.6.1-2), grep:i386 (2.20-3, 2.20-4), dialog:i386 (1.2-20140219-1, 1.2-20140911-1), fonts-tlwg-mono:i386 (0.6.1-1, 0.6.1-2), ethtool:i386 (3.13-1, 3.16-1), fonts-tlwg-loma:i386 (0.6.1-1, 0.6.1-2), fonts-tlwg-kinnari:i386 (0.6.1-1, 0.6.1-2), libfribidi0:i386 (0.19.6-1, 0.19.6-2), libgcr-ui-3-1:i386 (3.12.2-1, 3.14.0-2), less:i386 (458-2, 458-3), dosfstools:i386 (3.0.26-3, 3.0.26-4), fonts-tlwg-typewriter:i386 (0.6.1-1, 0.6.1-2), gcr:i386 (3.12.2-1, 3.14.0-2), fonts-tlwg-typo:i386 (0.6.1-1, 0.6.1-2), fonts-tlwg-typist:i386 (0.6.1-1, 0.6.1-2), python-chardet:i386 (2.2.1-2, 2.3.0-1), fonts-tlwg-sawasdee:i386 (0.6.1-1, 0.6.1-2), gnome-user-guide:i386 (3.12.2-1, 3.14.1-1), libgcr-3-common:i386 (3.12.2-1, 3.14.0-2), acl:i386 (2.2.52-1.1, 2.2.52-2), libacl1:i386 (2.2.52-1.1, 2.2.52-2), fonts-tlwg-norasi:i386 (0.6.1-1, 0.6.1-2), foomatic-db-compressed-ppds:i386 (20140730-1, 20141016-1), libgck-1-0:i386 (3.12.2-1, 3.14.0-2), fonts-tlwg-garuda:i386 (0.6.1-1, 0.6.1-2), fonts-thai-tlwg:i386 (0.6.1-1, 0.6.1-2), openprinting-ppds:i386 (20140730-1, 20141016-1), dictionaries-common:i386 (1.23.11, 1.23.14), aspell-en:i386 (7.1-0-1, 7.1-0-1.1)
```

---

### Post by VinDSL on 2014-10-24
A little noisy on start-up, as expected, but it's working here...  


[INDENT][[img]http://vindsl.com/images/vindsl-desktop-24-oct-2014-1(650x520).png[/img]]("http://vindsl.com/images/vindsl-desktop-24-oct-2014-1.png")[/INDENT]


```
~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Fri Oct 24 19:11:14 UTC 2014
Distro Release: Ubuntu Vivid Vervet (development branch)
Kernel Release: Linux 3.17.1-031701-generic
Gnome Release: GNOME Shell 3.12.2
Unity Release: unity 7.3.1

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.123

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
Installed-Size: 119
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.2.0-1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.3.0-0ubuntu3

Package: xserver-xorg-core
  Installed: 2:1.16.0-1ubuntu1

Package: xserver-common
  Installed: 2:1.16.0-1ubuntu1

Package: xserver-xephyr
  Installed: 2:1.16.0-1ubuntu1

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
 lcd monitor: Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```


BTW, don't forget to add 'PROPOSED' to your 'sources.list. [[1]]("http://askubuntu.com/questions/49691/what-is-the-proposed-repository/49693#49693")

Example:
```
## Bring on the flying monkeys and winged baboons - 15.04 PROPOSED repository.
deb http://mirror.hmc.edu/ubuntu/ vivid-proposed restricted main multiverse universe
```

---

### Post by ventrical on 2014-10-24
> **VinDSL said:**
> ## Bring on the flying monkeys and winged baboons - 15.04 PROPOSED repository.



:)

  I just had one of those 'Oz' moments. I could actually see the wicked witch waiving her broom yelling, "Fly my lovelies .. Fly !! Fly !!!" :)

---

### Post by VinDSL on 2014-10-24
> **ventrical said:**
> :) I just had one of those 'Oz' moments. I could actually see the **[COLOR="#FF0000"]wicked witch[/COLOR]** waiving her broom yelling, "Fly my lovelies .. Fly !! Fly !!!" :)

WoW, Vent!  I *think* you just came up with the release code name for Ubu 15.10  :D

---

### Post by Hazzabin on 2014-10-24
What's this 'OZ' moments??? thought you was from Canada :lolflag:

---

### Post by DogMatix on 2014-10-24
> **VinDSL said:**
> WoW, Vent!  I *think* you just came up with the release code name for Ubu 15.10  :D

I thought it would be Worried Womble.

```
Distributor ID:	Ubuntu
Description:	Ubuntu Vivid Vervet (development branch)
Release:	15.04
Codename:	vivid

```

+1

---

### Post by Elfy on 2014-10-24
Wilful Wodin

---

### Post by ventrical on 2014-10-24
> **Hazzabin said:**
> What's this 'OZ' moments??? thought you was from Canada :lolflag:

Southern most part. Actually the only part of Canada that is south of the American border. Can you believe that ?
:)

Kansas is only a stone throw away. We're the place where the Good Witch of the North came from.
 :)

lol

---

### Post by ventrical on 2014-10-24
> **VinDSL said:**
> WoW, Vent!  I *think* you just came up with the release code name for Ubu 15.10  :D

:) lol


 I think it is going to be Wiley Wallaby :)  Got to keep the folks down-under appy eh! :)

---

### Post by jerrylamos on 2014-10-24
Changed /etc/apt/sources.list utopic to vivid, did apt-get update and apt-get dist-upgrade.
After a lot of messages did run.
I do get some oddities:

sudo synaptic, settings, repositories gets a bunch of conflicts.

Also got:
```
sudo software-properties-gtk
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 98, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 109, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 599, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 89, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Ubuntu/vivid

```

Not sure what I have but it's running at the moment.....

DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu Vivid Vervet (development branch)"
Linux Aspire-5253 3.16.0-23-generic #31-Ubuntu SMP Tue Oct 21 17:56:17 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
model name	: AMD E-350 Processor
model name	: AMD E-350 Processor
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6310]

---

### Post by VinDSL on 2014-10-24
There are many ways of upgrading, but here's my method (feel free to post your own):


Let's start with...

```
sudo apt-get update; sudo apt-get dist-upgrade 
```
Then...

```
 sudo sed -i 's/utopic/vivid/g' /etc/apt/sources.list
```
Then...

```
sudo gedit /etc/apt/sources.list
```
Make sure any third party repos are #commented out, such as:

```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu vivid main
# deb-src http://extras.ubuntu.com/ubuntu vivid main
# deb http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
```

Save **[COLOR="#FF0000"]**[/COLOR]**, then...

```
sudo sh -c "echo 'deb http://archive.ubuntu.com/ubuntu/ vivid-proposed restricted main multiverse universe' >> /etc/apt/sources.list"

```
Then...

```
sudo apt-get update; sudo apt-get dist-upgrade
```
Reboot/restart.


**[COLOR="#FF0000"]**[/COLOR]** It might go without saying, but [all the usual rules apply after upgrading]("http://ubuntuforums.org/showthread.php?t=2249680") (partial upgrades, etc.)

Don't forget to un-tick Pre-released updates (vivid-proposed) in 'Software and Updates' or your system will bust.

'Proposed' repos should NOT be left enabled, on subsequent updates/upgrades.  Do so at your own peril.

YOU'VE BEEN WARNED...  :)

---

### Post by Hazzabin on 2014-10-24
Yup they do needs too :lolflag:

---

### Post by ventrical on 2014-10-25
> **VinDSL said:**
> There are many ways of upgrading, but here's my method (feel free to post your own):


Let's start with...

```
sudo apt-get update; sudo apt-get dist-upgrade 
```
Then...

```
 sudo sed -i 's/utopic/vivid/g' /etc/apt/sources.list
```
Then...

```
sudo gedit /etc/apt/sources.list
```
Make sure any third party repos are #commented out, such as:

```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu vivid main
# deb-src http://extras.ubuntu.com/ubuntu vivid main
# deb http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
```

Save, then...

```
sudo sh -c "echo 'deb http://archive.ubuntu.com/ubuntu/ vivid-proposed restricted main multiverse universe' >> /etc/apt/sources.list"

```
Then...

```
sudo apt-get update; sudo apt-get dist-upgrade
```
Reboot/restart.

Thanks Vin.

Regards..

EDIT!

Adding that repo and then updating busted my system. Don't forget to tell  to untic Pre-released updates (vivid proposed) in Software and Updates or system (desktop) will bust.:) lol

---

### Post by VinDSL on 2014-10-25
> **ventrical said:**
> Adding that repo and then updating busted my system. Don't forget to tell  to untic Pre-released updates (vivid proposed) in Software and Updates or system (desktop) will bust.:) lol

Good idea!

Thx ;)

---

### Post by mc4man on 2014-10-25
> **VinDSL said:**
> 

BTW, don't forget to add 'PROPOSED' to your 'sources.list. [[1]]("http://askubuntu.com/questions/49691/what-is-the-proposed-repository/49693#49693")

Example:
```
## Bring on the flying monkeys and winged baboons - 15.04 PROPOSED repository.
deb http://mirror.hmc.edu/ubuntu/ vivid-proposed restricted main multiverse universe
```

Have you done a full upgrade with -proposed yet?

Edit: missed you 'recanted', I enable here but 'pick & choose'

---

### Post by DogMatix on 2014-10-25
> **ventrical said:**
> Thanks Vin.

Regards..

EDIT!

Adding that repo and then updating busted my system. Don't forget to tell  to untic Pre-released updates (vivid proposed) in Software and Updates or system (desktop) will bust.:) lol
 
Oh dear! Thanks for the warnings but unfortunately they came a little too late for me. I added vivid-proposed last night then updated today. It seems to have had a very detrimental effect on  my system. Wireless is toast, some very bizarre changes to my Lubuntu DE have occurred and I get loads of PIDs not available for this session dialogues. I'll grab an ethernet cable tomorrow and see if I can revive anything but its not looking good. I may end up re-installing a vanilla utopic and changing the sources.list again.

---

### Post by VinDSL on 2014-10-25
> **mc4man said:**
> Have you done a full upgrade with -proposed yet?

Edit: missed you 'recanted', I enable here but 'pick & choose'

Exactly.  Vent brought it to my attention.  

To be clear, I used '-proposed' for the initial upgrade only.

'-proposed' should be used like salt n' pepper.  It's not the main course, so to speak.

I don't mean to appear smug, but I thought everyone was on the same page.

My bad.  I should have explained that up front... in retrospect.

---

### Post by mc4man on 2014-10-25
> **VinDSL said:**
> Exactly.  Vent brought it to my attention.  

To be clear, I used '-proposed' for the initial upgrade only.

'-proposed' should be used like salt n' pepper.  It's not the main course, so to speak.

I don't mean to appear smug, but I thought everyone was on the same page.

My bad.  I should have explained that up front... in retrospect.
It's probably not uncommon for people to use cli to upgrade & not pay attention..
Here it's usually synaptic though occasionally it has some issues depending on order of packages picked, mesa source upgrades can be one ex. 
(though synaptic is ok with shift + enables which can alleviate the above

---

### Post by DogMatix on 2014-10-25
> **VinDSL said:**
> Exactly.  Vent brought it to my attention.  

To be clear, I used '-proposed' for the initial upgrade only.

'-proposed' should be used like salt n' pepper.  It's not the main course, so to speak.

I don't mean to appear smug, but I thought everyone was on the same page.

My bad.  I should have explained that up front... in retrospect.


That would explain why the initial upgrade after adding proposed went OK. On your page now.

No worries, all part of the learning curve. I thought some of the updates looked dodgy. I could have always pressed 'n' instead of 'y'.

I guess curiosity killed the vervet

---

### Post by VinDSL on 2014-10-25
> **mc4man said:**
> It's probably not uncommon for people to use cli to upgrade & not pay attention..
I just re-enabled '-proposed' to see how it looks.  OMG!

It wants to strip the core system files back to bare bones, plus do a partial upgrade.

Hrm...

---

### Post by VinDSL on 2014-10-25
> **DogMatix said:**
> I guess curiosity killed the vervet

LoL!  Thanks, for being a good sport about it.  :)

I've been burned a zillion times in +1 testing.  It's like playing with nitroglycerin.

I dual-boot Ubu 10.10 as a backup OS.  Makes it easier putting Humpty Dumpty back together again...

Anyway, sorry for the confusion!

---

### Post by DogMatix on 2014-10-25
> **VinDSL said:**
> I just re-enabled '-proposed' to see how it looks.  OMG!

It wants to strip the core system files back to bare bones, plus do a partial upgrade.

Hrm...

Yes. I guess 'remove Lubuntu desktop' and ' Network manager' changes should have rang some bells for me :-)

---

### Post by zika on 2014-10-26
HeadsUp was issued: [http://ubuntuforums.org/showthread.php?t=2224798&p=13151391#post13151391](http://ubuntuforums.org/showthread.php?t=2224798&p=13151391#post13151391) ;)

---

### Post by zika on 2014-10-26
> **VinDSL said:**
> Don't forget to un-tick Pre-released updates (vivid-proposed) in 'Software and Updates' or your system **will** bust.Again and again... ;) It **might** but it also **might not**. This one did not and did have and still have vivid-proposed on. ;) We did have a thread about dist-upgrade in almost each and every U+1 since proposed was introduced, din not we?
[http://www.youtube.com/watch?v=g7LQS84IL4U](http://www.youtube.com/watch?v=g7LQS84IL4U)

---

### Post by VinDSL on 2014-10-26
> **zika said:**
> Again and again... ;) It **might** but it also **might not**. This one did not and did have and still have vivid-proposed on. ;) 

I think it's a matter of timing -- with a bit of luck tossed in -- especially while they're seeding the new repos.

It's the 'Dirty Harry Dilemma'...
> You've got to ask yourself one question: "Do I feel lucky?"  Well, do ya, punk?

Once, again, I think it's best to disable '-proposed' after the initial install.  Then, pick n' choose wisely later.

---

### Post by ventrical on 2014-10-27
> **VinDSL said:**
> I think it's a matter of timing -- with a bit of luck tossed in -- especially while they're seeding the new repos.

It's the 'Dirty Harry Dilemma'...


Once, again, I think it's best to disable '-proposed' after the initial install.  Then, pick n' choose wisely later.

Not a problem Vin.  Iv'e  bricked a few installs here and there. I was just tired that night.  But there was this weird problem during the cycle crossover. When I unticked proposed in synaptic it would then bounce me back to Utopic. So when I put in your recommend repo I didn't untic it . So it hosed my DE:) lol .. Gee .. that's part of why I'm here :)

Regards..

---

### Post by Hazzabin on 2014-10-27
Well pleased to hear I'm not the only one to 'hose' 'mutilate' 'crash't" now I'm having a beer or 3 to temporary celebrate success, well for now lol :)

---

### Post by ventrical on 2014-10-27
> **Hazzabin said:**
> Well pleased to hear I'm not the only one to 'hose' 'mutilate' 'crash't" now I'm having a beer or 3 to temporary celebrate success, well for now lol :)

Bravo. :)

  I had 4 pieces of pizza. Didn't sleep a wink. Serves me right ! :) (Well maybe one or 2 winks) Ahh there's the alarm. 4.30am Time to wake the Missus and send her off to work  while I get me nap :)

:)

Regards..

---

### Post by Hazzabin on 2014-10-27
> **ventrical said:**
> Bravo. :)

  I had 4 pieces of pizza. Didn't sleep a wink. Serves me right ! :) (Well maybe one or 2 winks) Ahh there's the alarm. 4.30am Time to wake the Missus and send her off to work  while I get me nap :)

:)

Regards..


OH GEE poor Missus  :p

---

### Post by xc3RnbFO8P on 2014-10-27
Well I got problem, 3D doesn't work anymore.
```
Current Date/Time: Mon Oct 27 09:49:55 UTC 2014
Distro Release: Ubuntu Vivid Vervet (development branch)
Kernel Release: Linux 3.16.0-23-generic
Gnome Release: GNOME Shell 3.14.1
Unity Release: unity 7.3.1

libGL error: failed to open drm device: Permission denied
libGL error: failed to load driver: i965
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.5, 256 bits)
OpenGL version string:  3.0 Mesa 10.3.0

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 138
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.2.0-1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.14), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: [http://mesa3d.org/](http://mesa3d.org/)

Package: mesa-common-dev
 Version: 10.3.0-0ubuntu3

Package: xserver-xorg-core
  Installed: 2:1.16.0-1ubuntu1

Package: xserver-common
  Installed: 2:1.16.0-1ubuntu1

Package: xserver-xephyr
  Installed: 2:1.16.0-1ubuntu1

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation Haswell-ULT DRAM Controller
           +-02.0  Intel Corporation Haswell-ULT Integrated Graphics Controller
           +-03.0  Intel Corporation Haswell-ULT HD Audio Controller
           +-14.0  Intel Corporation 8 Series USB xHCI HC
           +-16.0  Intel Corporation 8 Series HECI #0
           +-1b.0  Intel Corporation 8 Series HD Audio Controller
           +-1c.0-[01]----00.0  Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller
           +-1c.2-[02]----00.0  Qualcomm Atheros AR9485 Wireless Network Adapter
           +-1d.0  Intel Corporation 8 Series USB EHCI #1
           +-1f.0  Intel Corporation 8 Series LPC Controller
           +-1f.2  Intel Corporation 8 Series SATA Controller 1 [AHCI mode]
           \-1f.3  Intel Corporation 8 Series SMBus Controller

Display Properties:

  dimensions:    1366x768 pixels (361x203 millimeters)
  resolution:    96x96 dots per inch

ringi@ringi-Lenovo-Ideapad-Flex-15:~$ 

```

False alarm , works after reboot

```
Current Date/Time: Mon Oct 27 10:12:00 UTC 2014
Distro Release: Ubuntu Vivid Vervet (development branch)
Kernel Release: Linux 3.16.0-23-generic
Gnome Release: GNOME Shell 3.14.1
Unity Release: unity 7.3.1

OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
OpenGL version string:  3.0 Mesa 10.3.0

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
Installed-Size: 138
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.2.0-1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.14), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
 Version: 10.3.0-0ubuntu3

Package: xserver-xorg-core
  Installed: 2:1.16.0-1ubuntu1

Package: xserver-common
  Installed: 2:1.16.0-1ubuntu1

Package: xserver-xephyr
  Installed: 2:1.16.0-1ubuntu1

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation Haswell-ULT DRAM Controller
           +-02.0  Intel Corporation Haswell-ULT Integrated Graphics Controller
           +-03.0  Intel Corporation Haswell-ULT HD Audio Controller
           +-14.0  Intel Corporation 8 Series USB xHCI HC
           +-16.0  Intel Corporation 8 Series HECI #0
           +-1b.0  Intel Corporation 8 Series HD Audio Controller
           +-1c.0-[01]----00.0  Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller
           +-1c.2-[02]----00.0  Qualcomm Atheros AR9485 Wireless Network Adapter
           +-1d.0  Intel Corporation 8 Series USB EHCI #1
           +-1f.0  Intel Corporation 8 Series LPC Controller
           +-1f.2  Intel Corporation 8 Series SATA Controller 1 [AHCI mode]
           \-1f.3  Intel Corporation 8 Series SMBus Controller

Display Properties:

  dimensions:    1366x768 pixels (361x203 millimeters)
  resolution:    96x96 dots per inch

ringi@ringi-Lenovo-Ideapad-Flex-15:~$
```

---

### Post by ventrical on 2014-10-27
> **Hazzabin said:**
> OH GEE poor Missus  :p


Yes... thanks for reminding me :)

Regards..

---

