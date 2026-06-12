---
title: "Nothing is coming up"
date: 2017-11-06
forum: Virtualisation
---

### Post by GirishSharma on 2017-11-06
[COLOR=#111111][FONT=Ubuntu]I am not able to configure Virtualbox in Ubuntu 16.04 LTS on my brand new 64 bit PC. Here are some info : I downloaded and tried by :[/FONT][/COLOR]
sudo dpkg -i virtualbox-5.2_5.2.0-118431~Ubuntu~xenial_amd64.deb 
[COLOR=#111111][FONT=Ubuntu]It got installed, no error. Rebooted the PC.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Tried by giving virtualbox in command prompt. No error, no message, but nothing is coming up.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have written the same issue at [this link]("https://forums.virtualbox.org/viewtopic.php?f=7&t=85356") too and came to know that I have to disable secure boot. I tried same but same issue.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Virtualbox forum says that I should write here. 

I have tried by installing Ubuntu Software Center option, it got installed but same issue; no error, no message, nothing is coming up.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]How do I access Virtualbox?[/FONT][/COLOR]

---

### Post by ajgreeny on 2017-11-06
It is much easier to add the VBox repos to your sources by following the info here, copied from the VBox site and install the version you want in the normal manner.

> **Debian-based Linux distributions**

<snip>

Combine downloading and registering the sources info with these two commands:
```
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
```
I had some problems with the 5.2 version and therefore downgraded to 5.1 which works brilliantly for me; both versions will appear in the repos after you run those two commands

---

### Post by GirishSharma on 2017-11-06
Thanks for your reply. I again removed all virtualbox files by :
```
sudo apt-get remove --purge virtualbox*
```

and ran your commands like this :

```
girish@girish-System-Product-Name:~$ wget -q [https://www.virtualbox.org/download/oracle_vbox_2016.asc](https://www.virtualbox.org/download/oracle_vbox_2016.asc) -O- | sudo apt-key add -
OK
girish@girish-System-Product-Name:~$ wget -q [https://www.virtualbox.org/download/oracle_vbox.asc](https://www.virtualbox.org/download/oracle_vbox.asc) -O- | sudo apt-key add -
OK
girish@girish-System-Product-Name:~$ 
```

Now, what to do please. I am new to linux please.

---

### Post by SeijiSensei on 2017-11-06
```

sudo apt-get update
sudo apt-get install virtualbox-5.1

```

Like ajgreeny I'm still using version 5.1 everywhere without incident.

---

### Post by GirishSharma on 2017-11-06
Ok, I will try with 5.1, but just want to know that are you running 5.1 on 64 bit Ubuntu 16.04 LTS please, because I have tired on many tries. I think either it is secure boot or something security keys issue. Even, I am remembering that I once tried with 5.1 but probably it did not come up. I will retry and post here.

---

### Post by ajgreeny on 2017-11-06
As you have a 64bit system and will presumably want to run 64bit guests, you will need to make sure that Intel or AMD hardware acceleration is enabled, so ensure that you have enabled VT-x/AMD-V in your BIOS/UEFI settings.

Check that at next boot by hitting the right key to get into the system setup; might be Del or F2 but a screen message usually flashes up quickly then disappears.

---

### Post by GirishSharma on 2017-11-06
Still no luck after Intel or AMD hardware acceleration enabled and sudo apt-get install virtualbox-5.1 (It said something package not found etc.
Tried by downloading fresh another .deb from Virtualbox site virtualbox-5.1_5.1.30-118389~Ubuntu~xenial_amd64
```

girish@girish-System-Product-Name:~/Downloads$ sudo dpkg -i virtualbox-5.1_5.1.30-118389~Ubuntu~xenial_amd64.deb
Selecting previously unselected package virtualbox-5.1.
(Reading database ... 175209 files and directories currently installed.)
Preparing to unpack virtualbox-5.1_5.1.30-118389~Ubuntu~xenial_amd64.deb ...
Unpacking virtualbox-5.1 (5.1.30-118389~Ubuntu~xenial) ...
dpkg: dependency problems prevent configuration of virtualbox-5.1:
 virtualbox-5.1 depends on libqt5x11extras5 (>= 5.1.0); however:
  Package libqt5x11extras5 is not installed.

dpkg: error processing package virtualbox-5.1 (--install):
 dependency problems - leaving unconfigured
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Errors were encountered while processing:
 virtualbox-5.1
girish@girish-System-Product-Name:~/Downloads$ 

```

---

### Post by ian-weisser on 2017-11-06
> **GirishSharma said:**
> It said something package not found etc.
That's the important part. Pay attention to it.

> **GirishSharma said:**
> dpkg: dependency problems prevent configuration of virtualbox-5.1:
 virtualbox-5.1 depends on libqt5x11extras5 (>= 5.1.0); however:
  Package libqt5x11extras5 is not installed.

Install this package.
Or, rather, read the error message carefully when it refuses to install. You must learn *why*&#8203; it refuses to install.

---

### Post by SeijiSensei on 2017-11-06
> **GirishSharma said:**
> Still no luck after Intel or AMD hardware acceleration enabled and sudo apt-get install virtualbox-5.1 (It said something package not found etc.

Did you run "sudo apt-get update" before running "sudo apt-get install"?  The update step retrieves the package lists from the repositories in /etc/apt/sources.list and /etc/apt/sources.list.d/.  That's the only way your system would know where to get virtualbox-5.1.

> Tried by downloading fresh another .deb from Virtualbox site virtualbox-5.1_5.1.30-118389~Ubuntu~xenial_amd64

Simply trying to install a single package may leave you with unresolved "dependencies."  These are other programs, or software libraries, on which the newly-installed package relies.  Installing from the Oracle repository will also trigger downloads for any needed companion software, particularly the gcc compiler and dkms, which are used to compile the VirtualBox kernel module to match your particular installation.

---

### Post by ajgreeny on 2017-11-06
That unavailable package **libqt5x11extras5** is in the universe repos so make sure they are enabled on your system and you ought to be good to go.

---

### Post by GirishSharma on 2017-11-06
Please see how I am doing :
```

girish@girish-System-Product-Name:~$ sudo apt-get update
[sudo] password for girish: 
Hit:1 http://security.ubuntu.com/ubuntu xenial-security InRelease            
Hit:2 http://in.archive.ubuntu.com/ubuntu xenial InRelease                   
Hit:3 http://in.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:4 http://in.archive.ubuntu.com/ubuntu xenial-backports InRelease
Reading package lists... Done
girish@girish-System-Product-Name:~$ sudo apt-get install virtualbox-5.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-5.1 is already the newest version (5.1.30-118389~Ubuntu~xenial).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 virtualbox-5.1 : Depends: libqt5x11extras5 (>= 5.1.0) but it is not going to be installed
                  Recommends: libsdl-ttf2.0-0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
girish@girish-System-Product-Name:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
girish@girish-System-Product-Name:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  dkms gcc-5-base:i386 libasn1-8-heimdal:i386 libasound2:i386 libasyncns0:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libboost-filesystem1.58.0:i386 libboost-system1.58.0:i386 libbsd0:i386
  libcaca0:i386 libcapnp-0.5.3:i386 libcups2:i386 libcurl3:i386
  libdbus-1-3:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libegl1-mesa:i386
  libelf1:i386 libevdev2:i386 libexpat1:i386 libffi6:i386 libflac8:i386
  libfontconfig1:i386 libfreetype6:i386 libgbm1:i386 libgl1-mesa-dri:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libglib2.0-0:i386 libgmp10:i386
  libgnutls30:i386 libgraphite2-3:i386 libgsoap8 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhogweed4:i386 libhx509-5-heimdal:i386 libice6:i386 libicu55:i386
  libidn11:i386 libinput10:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libjson-c2:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386
  libkrb5-3:i386 libkrb5support0:i386 libldap-2.4-2:i386 libllvm4.0:i386
  libmirclient9:i386 libmircommon7:i386 libmircore1:i386 libmirprotobuf3:i386
  libmtdev1:i386 libnettle6:i386 libogg0:i386 libp11-kit0:i386
  libpciaccess0:i386 libpcre16-3:i386 libpng12-0:i386 libpng16-16:i386
  libprotobuf-lite9v5:i386 libproxy1v5:i386 libpulse0:i386 libqt4-opengl
  libqt5core5a:i386 libqt5dbus5:i386 libqt5gui5:i386 libqt5network5:i386
  libqt5opengl5:i386 libqt5printsupport5:i386 libqt5svg5:i386
  libqt5widgets5:i386 libroken18-heimdal:i386 librtmp1:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsdl1.2debian:i386
  libsensors4:i386 libslang2:i386 libsm6:i386 libsndfile1:i386
  libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-6:i386
  libtxc-dxtn-s2tc0:i386 libvncserver1 libvorbis0a:i386 libvorbisenc2:i386
  libvpx3:i386 libwacom2:i386 libwayland-client0:i386 libwayland-server0:i386
  libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-icccm4:i386 libxcb-image0:i386 libxcb-keysyms1:i386
  libxcb-present0:i386 libxcb-randr0:i386 libxcb-render-util0:i386
  libxcb-render0:i386 libxcb-shape0:i386 libxcb-shm0:i386 libxcb-sync1:i386
  libxcb-util1:i386 libxcb-xfixes0:i386 libxcb-xkb1:i386 libxcb1:i386
  libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386
  libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxkbcommon-x11-0:i386
  libxkbcommon0:i386 libxml2:i386 libxmu6:i386 libxrender1:i386
  libxshmfence1:i386 libxt6:i386 libxxf86vm1:i386
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libqt5x11extras5
The following NEW packages will be installed:
  libqt5x11extras5
0 upgraded, 1 newly installed, 0 to remove and 334 not upgraded.
1 not fully installed or removed.
Need to get 7,876 B of archives.
After this operation, 35.8 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://in.archive.ubuntu.com/ubuntu xenial/universe amd64 libqt5x11extras5 amd64 5.5.1-3build1 [7,876 B]
Fetched 7,876 B in 0s (13.9 kB/s)           
Selecting previously unselected package libqt5x11extras5:amd64.
(Reading database ... 176002 files and directories currently installed.)
Preparing to unpack .../libqt5x11extras5_5.5.1-3build1_amd64.deb ...
Unpacking libqt5x11extras5:amd64 (5.5.1-3build1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Setting up libqt5x11extras5:amd64 (5.5.1-3build1) ...
Setting up virtualbox-5.1 (5.1.30-118389~Ubuntu~xenial) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
Processing triggers for libc-bin (2.23-0ubuntu5) ...
girish@girish-System-Product-Name:~$ sudo apt-get install virtualbox-5.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-5.1 is already the newest version (5.1.30-118389~Ubuntu~xenial).
The following packages were automatically installed and are no longer required:
  dkms gcc-5-base:i386 libasn1-8-heimdal:i386 libasound2:i386 libasyncns0:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libboost-filesystem1.58.0:i386 libboost-system1.58.0:i386 libbsd0:i386
  libcaca0:i386 libcapnp-0.5.3:i386 libcups2:i386 libcurl3:i386
  libdbus-1-3:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libegl1-mesa:i386
  libelf1:i386 libevdev2:i386 libexpat1:i386 libffi6:i386 libflac8:i386
  libfontconfig1:i386 libfreetype6:i386 libgbm1:i386 libgl1-mesa-dri:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libglib2.0-0:i386 libgmp10:i386
  libgnutls30:i386 libgraphite2-3:i386 libgsoap8 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhogweed4:i386 libhx509-5-heimdal:i386 libice6:i386 libicu55:i386
  libidn11:i386 libinput10:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libjson-c2:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386
  libkrb5-3:i386 libkrb5support0:i386 libldap-2.4-2:i386 libllvm4.0:i386
  libmirclient9:i386 libmircommon7:i386 libmircore1:i386 libmirprotobuf3:i386
  libmtdev1:i386 libnettle6:i386 libogg0:i386 libp11-kit0:i386
  libpciaccess0:i386 libpcre16-3:i386 libpng12-0:i386 libpng16-16:i386
  libprotobuf-lite9v5:i386 libproxy1v5:i386 libpulse0:i386 libqt4-opengl
  libqt5core5a:i386 libqt5dbus5:i386 libqt5gui5:i386 libqt5network5:i386
  libqt5opengl5:i386 libqt5printsupport5:i386 libqt5svg5:i386
  libqt5widgets5:i386 libroken18-heimdal:i386 librtmp1:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsdl1.2debian:i386
  libsensors4:i386 libslang2:i386 libsm6:i386 libsndfile1:i386
  libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-6:i386
  libtxc-dxtn-s2tc0:i386 libvncserver1 libvorbis0a:i386 libvorbisenc2:i386
  libvpx3:i386 libwacom2:i386 libwayland-client0:i386 libwayland-server0:i386
  libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-icccm4:i386 libxcb-image0:i386 libxcb-keysyms1:i386
  libxcb-present0:i386 libxcb-randr0:i386 libxcb-render-util0:i386
  libxcb-render0:i386 libxcb-shape0:i386 libxcb-shm0:i386 libxcb-sync1:i386
  libxcb-util1:i386 libxcb-xfixes0:i386 libxcb-xkb1:i386 libxcb1:i386
  libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386
  libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxkbcommon-x11-0:i386
  libxkbcommon0:i386 libxml2:i386 libxmu6:i386 libxrender1:i386
  libxshmfence1:i386 libxt6:i386 libxxf86vm1:i386
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 334 not upgraded.
girish@girish-System-Product-Name:~$ virtualbox 
girish@girish-System-Product-Name:~$ 

```

Nothing happening, no error, no message...

---

### Post by GirishSharma on 2017-11-06
Or, should I go like this ?

```

sudo apt-get remove --purge virtualbox*
Again disable secure boot. At this moment, I have enabled secure boot, because disabling did not worked, so I enabled it.
sudo apt-get update
sudo apt-get install virtualbox-5.1
sudo apt-get -f install
sudo apt-get install virtualbox-5.1
restart
virtualbox


```

---

### Post by GirishSharma on 2017-11-07
I am having a brand new 64 bit PC with **disabled secure boot** and this is basic info :
```

**girish@girish-System-Product-Name:~$ uname -a**
Linux girish-System-Product-Name 4.10.0-38-generic #42~16.04.1-Ubuntu  SMP Tue Oct 10 16:32:20 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
**girish@girish-System-Product-Name:~$ uname -i**
x86_64

```

I am struggling with configuration of Virtualbox since last 2 days and this is how it is responding :
```


First I removed all different versions by :
sudo apt-get remove --purge virtualbox*

sudo gedit /etc/apt/sources.list
deb http://download.virtualbox.org/virtualbox/debian xenial contrib

wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -

**girish@girish-System-Product-Name:~$ sudo apt-get update**
Get:1 http://download.virtualbox.org/virtualbox/debian xenial InRelease [7,883 B]
Hit:2 http://security.ubuntu.com/ubuntu xenial-security InRelease                                                                            
Hit:3 http://in.archive.ubuntu.com/ubuntu xenial InRelease              
Hit:4 http://in.archive.ubuntu.com/ubuntu xenial-updates InRelease      
Get:5 http://download.virtualbox.org/virtualbox/debian xenial/contrib amd64 Packages [1,755 B]
Hit:6 http://in.archive.ubuntu.com/ubuntu xenial-backports InRelease 
Get:7 http://download.virtualbox.org/virtualbox/debian xenial/contrib i386 Packages [1,781 B]
Fetched 11.4 kB in 2s (4,250 B/s)
Reading package lists... Done
**girish@girish-System-Product-Name:~$ sudo apt-get install virtualbox-5.1**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libsdl-ttf2.0-0
The following NEW packages will be installed:
  libsdl-ttf2.0-0 virtualbox-5.1
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 65.8 MB of archives.
After this operation, 162 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://in.archive.ubuntu.com/ubuntu xenial/universe amd64 libsdl-ttf2.0-0 amd64 2.0.11-3 [15.0 kB]
Get:2 http://download.virtualbox.org/virtualbox/debian xenial/contrib  amd64 virtualbox-5.1 amd64 5.1.30-118389~Ubuntu~xenial [65.8 MB]
Fetched 65.8 MB in 2min 11s (503 kB/s)                                                                                                         
Preconfiguring packages ...
Selecting previously unselected package libsdl-ttf2.0-0:amd64.
(Reading database ... 209266 files and directories currently installed.)
Preparing to unpack .../libsdl-ttf2.0-0_2.0.11-3_amd64.deb ...
Unpacking libsdl-ttf2.0-0:amd64 (2.0.11-3) ...
Selecting previously unselected package virtualbox-5.1.
Preparing to unpack .../virtualbox-5.1_5.1.30-118389~Ubuntu~xenial_amd64.deb ...
Unpacking virtualbox-5.1 (5.1.30-118389~Ubuntu~xenial) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up libsdl-ttf2.0-0:amd64 (2.0.11-3) ...
Setting up virtualbox-5.1 (5.1.30-118389~Ubuntu~xenial) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
Processing triggers for libc-bin (2.23-0ubuntu9) ...
[B]girish@girish-System-Product-Name:~$ I reboot the pc.
girish@girish-System-Product-Name:~$ virtualbox
[/B]
```

No response, no error, nothing is coming up.  Screen becomes like this   image. (I don't know how do I attach the image here, but Title bar of   command prompt disappears, an icon of virtualbox appears in the left   hand icon panel and cursor turns into a white rectangular shape)

So, I am not able to configure virtualbox.

Kindly help me, I am writing here with a great hope.

---

### Post by mastablasta on 2017-11-07
what happens if you start virtual box from GUI shortcut?

---

### Post by GirishSharma on 2017-11-07
It just shows the icon in left hand sided icons tray and when I right clicks on it there are these options :
Oracle VM Manager
Oracle VM VirtualBox
Lock to Launcher
Quit

Only Quit option works, rest no error, no response, nothing.

---

### Post by GirishSharma on 2017-11-07
Are there are chances of display issue something related to xterm etc. ?

---

### Post by ian-weisser on 2017-11-07
> **GirishSharma said:**
> 
0 upgraded, 1 newly installed, 0 to remove and **334 not upgraded**.
1 not fully installed or removed.

Stop everything.
334 packages not upgraded? This means that your system has been broken for a long time.
This is MORE IMPORTANT than your virtualbox problem.
You are not recievng security upgrades, and your system may be vulnerable to published exploits.
Solve this first.

There is a high likelihood that this will also solve your virtualbox problem.

---

### Post by slickymaster on 2017-11-07
Threads merged.

Please do not create duplicate threads, it dilutes the community&#8217;s efforts to provide support and causes confusion.

---

### Post by GirishSharma on 2017-11-07
Thanks for reply. I have purchased this PC before 2 days and since then I am struggling to get working virtualbox, so I guess all these 334 packages have been installed or not upgraded. I have tested that I am getting security updates without any issue. I ran [COLOR=#333333]sudo apt autoremove to remove them.

Kindly see my previous message in which I have followed correct steps for installing virtualbox box, but it is not coming up. I doubt it may be xterm issue. Kindly help me what I am doing wrong.[/COLOR]

---

### Post by ian-weisser on 2017-11-07
> **GirishSharma said:**
> [COLOR=#333333]Kindly help me what I am doing wrong.[/COLOR]

What you are doing wrong is unsafe computing, and focusing on the immediate problem instead of the important problem.

I am unwilling to help you further with installing Virtualbox until the more important and fundamental problem of 334 uninstalled updates is resolved.
It is foolish to try to install software on an obviously broken system.

Since you seem to have purchased an obviously broken system, whomever you purchased the system from is suspect...and that raises security concerns.
How do you know that whomever you purchased the system from did not install malware or a backdoor?
How do you know that your broken system is not already otherwise compromised?

My usual advice with any system after a sale is to do a clean install...which will also incidentally solve your Virtualbox problem.

There are many different experts in this forum, and some of them may be willing to help you install Virtualbox first.

---

### Post by GirishSharma on 2017-11-07
Ok. I am ready to follow you. Please tell me how do I proceed to have a unbroken/clean install of Ubuntu 16.04 on my this 64 bit PC. Kindly explain all steps and links, so that I can follow your way.

---

### Post by ian-weisser on 2017-11-07
The easiest and safest way to reinstall is by following instructions at [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop) and [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu)

Back up _all_ your data before starting onto some other trustworthy media. The install process may wipe your disk.

You have a choice of Ubuntu 16.04.3 LTS, which has older software, but is supported until 2021,
Or Ubuntu 17.10, which has much newer software but is supported for only nine months - in mid-2018 you must spend an hour or two upgrading to Ubuntu 18.04.

Depending upon the speed of your network connection, the full backup-and-install process takes between 30-120 minutes. The installer asks several questions soon after starting, so don't walk away. Unless you have special needs (like dual-booting or encryption), it is generally best for most general-purpose users to stick to the installer defaults...but we admittedly do not know your needs.

Read each installer question carefully. Stop if you have a question. You can always start the installer over after we have answered it.

---

### Post by GirishSharma on 2017-11-08
This is a fresh installation. Kindly tell me what info you want to know and please tell me how do I proceed for virtualbox please.
This is first command after installation and I did not found any error while installation. There was a successful installation message at the end. I clicked on Reboot now button, there was some messages on command window. I powered off the PC. Went to BIOS and changed Boot sequence. Now it is a fresh installation.
```

girish@gk:~$ uname -a
Linux gk 4.10.0-28-generic #32~16.04.2-Ubuntu SMP Thu Jul 20 10:19:48 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
girish@gk:~$ 

```

I am bit confused. I downloaded ubuntu-16.04.3-desktop-amd64.iso.  Matched Check sum. Burn iso on a blank DVD, but uname-a is showing me  16.04.2. Is it a normal or I am missing something, Anyway, it is not a  big issue, I request you to please tell me how do I proceed for  virtualbox installation, so that it may not broke the system and/or any  security compromise.

---

### Post by vasa1 on 2017-11-08
Please first run ```
sudo apt-get update
``` and, if there are no errors, run ```
sudo apt-get dist-upgrade
```If anything in the output from the second command worries you, press "N" to abort and then post the entire output here.

If you run the second command successfully, try ```
uname -a
```again.

---

### Post by GirishSharma on 2017-11-08
I wish to post here the whole output of screen of above 3 commands. I don't know how to attach in a text file not able to paste in code tages too.
```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

**girish@gk:~$ sudo apt-get update**
[sudo] password for girish: 
Hit:1 http://in.archive.ubuntu.com/ubuntu xenial InRelease                                                  
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]              
Get:4 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [381 kB]
Get:5 http://in.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]     
Get:6  http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages  [652 kB]                                                         
Get:7  http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages  [353 kB]                                                           
Get:8  http://in.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages  [617 kB]                                                          
Get:9  http://security.ubuntu.com/ubuntu xenial-security/main Translation-en  [168 kB]                                                          
Get:10  http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11  Metadata [60.3 kB]                                                 
Get:11  http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64  Icons [62.6 kB]                                                    
Get:12  http://in.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en  [273 kB]                                                        
Get:13  http://security.ubuntu.com/ubuntu xenial-security/universe amd64  Packages [178 kB]                                                     
Get:14  http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11  Metadata [308 kB]                                                 
Get:15  http://security.ubuntu.com/ubuntu xenial-security/universe i386  Packages [153 kB]                                                      
Get:16  http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11  Metadata [51.5 kB]                                             
Get:17  http://in.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64  Icons [217 kB]                                                    
Get:18  http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64  Icons [85.1 kB]                                                
Get:19  http://in.archive.ubuntu.com/ubuntu xenial-updates/universe amd64  Packages [543 kB]                                                    
Get:20  http://in.archive.ubuntu.com/ubuntu xenial-updates/universe i386  Packages [517 kB]                                                     
Get:21  http://in.archive.ubuntu.com/ubuntu xenial-updates/universe amd64  DEP-11 Metadata [174 kB]                                             
Get:22  http://in.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11  64x64 Icons [237 kB]                                                
Get:23  http://in.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64  DEP-11 Metadata [5,888 B]                                          
Get:24  http://in.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11  Metadata [3,324 B]                                              
Get:25  http://in.archive.ubuntu.com/ubuntu xenial-backports/universe amd64  DEP-11 Metadata [4,584 B]                                          
Fetched  5,351 kB in 57s (93.3  kB/s)                                                                                                            
Reading package lists... Done
**girish@gk:~$ sudo apt-get dist-upgrade**
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
**girish@gk:~$ sudo apt-get dist-upgrade**
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
**girish@gk:~$ sudo apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-4.10.0-38 linux-headers-4.10.0-38-generic linux-image-4.10.0-38-generic linux-image-extra-4.10.0-38-generic
The following packages will be upgraded:
   apparmor bind9-host binutils bluez bluez-cups bluez-obexd  ca-certificates cpp-5 cracklib-runtime cups cups-bsd cups-client  cups-common
  cups-core-drivers cups-daemon cups-ppdc  cups-server-common distro-info-data dnsmasq-base dnsutils evince  evince-common firefox g++-5 gcc-5
  gcc-5-base ghostscript  ghostscript-x gir1.2-gdkpixbuf-2.0 gir1.2-javascriptcoregtk-4.0  gir1.2-packagekitglib-1.0 gir1.2-soup-2.4
  gir1.2-webkit2-4.0  gnome-software gnome-software-common grub-common grub-pc grub-pc-bin  grub2-common gvfs gvfs-backends gvfs-bin
  gvfs-common gvfs-daemons  gvfs-fuse gvfs-libs initramfs-tools initramfs-tools-bin  initramfs-tools-core iproute2 libapparmor-perl
  libapparmor1 libasan2 libatomic1 libbind9-140 libbluetooth3 libcc1-0 libcilkrts5 libcrack2 libcryptsetup4 libcups2 libcupscgi1
   libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls  libdns-export162 libdns162 libegl1-mesa libevdocument3-4 libevview3-3
  libfreerdp-cache1.1 libfreerdp-client1.1 libfreerdp-codec1.1 libfreerdp-common1.1.0 libfreerdp-core1.1 libfreerdp-crypto1.1
   libfreerdp-gdi1.1 libfreerdp-locale1.1 libfreerdp-plugins-standard  libfreerdp-primitives1.1 libfreerdp-utils1.1 libgail-common libgail18
   libgbm1 libgcc-5-dev libgd3 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgnutls-openssl27
   libgnutls30 libgomp1 libgraphite2-3 libgs9 libgs9-common libgtk2.0-0  libgtk2.0-bin libgtk2.0-common libicu55 libidn11 libisc-export160
  libisc160 libisccc140 libisccfg140 libitm1 libjavascriptcoregtk-4.0-18 libllvm4.0 liblouis-data liblouis9 liblsan0 liblwres141
   libmirclient9 libmircommon7 libmircore1 libmirprotobuf3 libmpx0 libnss3  libnss3-nssdb libpackagekit-glib2-16 libpam-systemd libplist3
  libplymouth4 libpoppler-glib8 libpoppler58 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpython3.5 libpython3.5-minimal
   libpython3.5-stdlib libquadmath0 libsmbclient libsnapd-glib1  libsoup-gnome2.4-1 libsoup2.4-1 libssl1.0.0 libstdc++-5-dev libstdc++6
   libsystemd0 libtsan0 libubsan0 libudev1 libwayland-client0  libwayland-cursor0 libwayland-egl1-mesa libwayland-server0 libwbclient0
  libwebkit2gtk-4.0-37 libwebkit2gtk-4.0-37-gtk2 libwinpr-crt0.1 libwinpr-dsparse0.1 libwinpr-environment0.1 libwinpr-file0.1
   libwinpr-handle0.1 libwinpr-heap0.1 libwinpr-input0.1  libwinpr-interlocked0.1 libwinpr-library0.1 libwinpr-path0.1  libwinpr-pool0.1
  libwinpr-registry0.1 libwinpr-rpc0.1  libwinpr-sspi0.1 libwinpr-synch0.1 libwinpr-sysinfo0.1  libwinpr-thread0.1 libwinpr-utils0.1
  libxatracker2 libxfont1 libxfont2 libxml2 linux-firmware linux-generic-hwe-16.04 linux-headers-generic-hwe-16.04
  linux-image-generic-hwe-16.04 linux-libc-dev logrotate lshw openssl plymouth plymouth-label plymouth-theme-ubuntu-logo
   plymouth-theme-ubuntu-text poppler-utils pulseaudio  pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils  python3-distupgrade
  python3-jwt python3-louis  python3-update-manager python3.5 python3.5-minimal resolvconf samba-libs  shotwell shotwell-common snapd
  snapd-login-service systemd systemd-sysv tcpdump ubuntu-core-launcher ubuntu-drivers-common ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk ubuntu-software udev unattended-upgrades update-manager update-manager-core update-notifier
   update-notifier-common wget wpasupplicant xserver-common  xserver-xorg-core-hwe-16.04 xserver-xorg-legacy-hwe-16.04 xul-ext-ubufox
224 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 176 MB/298 MB of archives.
After this operation, 418 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgl1-mesa-dri amd64 17.0.7-0ubuntu0.16.04.2 [5,216 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libapparmor1 amd64 2.10.95-0ubuntu2.7 [31.2 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libcryptsetup4 amd64 2:1.6.6-5ubuntu2.1 [73.3 kB]

Output Trimmed

Get:144  http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 liblouis9  amd64 2.6.4-2ubuntu0.1 [59.5 kB]                              
Get:145  http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64  python3-louis all 2.6.4-2ubuntu0.1 [7,384 B]                            
Fetched  168 MB in 6min 9s (455  kB/s)                                                                                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
setting xserver-xorg-legacy/xwrapper/allowed_users from configuration file
(Reading database ... 175107 files and directories currently installed.)
Preparing to unpack .../bluez_5.37-0ubuntu5.1_amd64.deb ...
Unpacking bluez (5.37-0ubuntu5.1) over (5.37-0ubuntu5) ...
Preparing to unpack .../libsystemd0_229-4ubuntu21_amd64.deb ...

Output Trimmed

Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for initramfs-tools (0.122ubuntu8.9) ...
update-initramfs: Generating /boot/initrd.img-4.10.0-38-generic
Processing triggers for ca-certificates (20170717~16.04.1) ...
Updating certificates in /etc/ssl/certs...
17 added, 42 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.
Processing triggers for resolvconf (1.78ubuntu5) ...
**girish@gk:~$ uname -a**
Linux gk 4.10.0-28-generic #32~16.04.2-Ubuntu SMP Thu Jul 20 10:19:48 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
girish@gk:~$ 

```

---

### Post by vasa1 on 2017-11-08
Based on "To run a command as administrator (user "root"), use "sudo <command>".", are you using a live USB/DVD as opposed to a full installation?

---

### Post by deadflowr on 2017-11-08
>  I don't know how to attach in a text file not able to paste in code tages too.
For extremely long outputs we prefer posting those to a pastebin site and posting a link.

How to pastebinit on Ubuntu: [https://help.ubuntu.com/community/Pastebinit]("https://help.ubuntu.com/community/Pastebinit")


But from the output all seems up-to-date at this point (No errors at least). You would need to reboot in order to be using the newly install 4.10-0.38 linux kernel.

---

### Post by GirishSharma on 2017-11-08
But my main question is virtualbox, keeping in view of a fresh installation, I wish to start installation of virtualbox box, so that there should not be anything which compromise any security issue.

---

### Post by ian-weisser on 2017-11-08
Try:
```
sudo apt install virtualbox
```

---

### Post by GirishSharma on 2017-11-08
```

girish@gk:~$ sudo apt install virtualbox
[sudo] password for girish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  dkms libgsoap8 libqt4-opengl libsdl1.2debian libvncserver1 virtualbox-dkms virtualbox-qt
Suggested packages:
  vde2 virtualbox-guest-additions-iso
The following NEW packages will be installed:
  dkms libgsoap8 libqt4-opengl libsdl1.2debian libvncserver1 virtualbox virtualbox-dkms virtualbox-qt
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.0 MB of archives.
After this operation, 99.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 dkms all 2.2.0.3-2ubuntu11.5 [66.3 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu xenial/universe amd64 libgsoap8 amd64 2.8.28-1 [216 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu xenial/main amd64 libqt4-opengl amd64 4:4.8.7+dfsg-5ubuntu2 [301 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu xenial/main amd64 libsdl1.2debian amd64 1.2.15+dfsg1-3 [168 kB]
Get:5 http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libvncserver1 amd64 0.9.10+dfsg-3ubuntu0.16.04.1 [122 kB]
Get:6 http://in.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 virtualbox-dkms all 5.0.40-dfsg-0ubuntu1.16.04.1 [623 kB]
Get:7 http://in.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 virtualbox amd64 5.0.40-dfsg-0ubuntu1.16.04.1 [14.3 MB]
Get:8 http://in.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 virtualbox-qt amd64 5.0.40-dfsg-0ubuntu1.16.04.1 [7,195 kB]         
Fetched 23.0 MB in 25s (905 kB/s)                                                                                                             
Selecting previously unselected package dkms.
(Reading database ... 209342 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-2ubuntu11.5_all.deb ...
Unpacking dkms (2.2.0.3-2ubuntu11.5) ...
Selecting previously unselected package libgsoap8:amd64.
Preparing to unpack .../libgsoap8_2.8.28-1_amd64.deb ...
Unpacking libgsoap8:amd64 (2.8.28-1) ...
Selecting previously unselected package libqt4-opengl:amd64.
Preparing to unpack .../libqt4-opengl_4%3a4.8.7+dfsg-5ubuntu2_amd64.deb ...
Unpacking libqt4-opengl:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Selecting previously unselected package libsdl1.2debian:amd64.
Preparing to unpack .../libsdl1.2debian_1.2.15+dfsg1-3_amd64.deb ...
Unpacking libsdl1.2debian:amd64 (1.2.15+dfsg1-3) ...
Selecting previously unselected package libvncserver1:amd64.
Preparing to unpack .../libvncserver1_0.9.10+dfsg-3ubuntu0.16.04.1_amd64.deb ...
Unpacking libvncserver1:amd64 (0.9.10+dfsg-3ubuntu0.16.04.1) ...
Selecting previously unselected package virtualbox-dkms.
Preparing to unpack .../virtualbox-dkms_5.0.40-dfsg-0ubuntu1.16.04.1_all.deb ...
Unpacking virtualbox-dkms (5.0.40-dfsg-0ubuntu1.16.04.1) ...
Selecting previously unselected package virtualbox.
Preparing to unpack .../virtualbox_5.0.40-dfsg-0ubuntu1.16.04.1_amd64.deb ...
Unpacking virtualbox (5.0.40-dfsg-0ubuntu1.16.04.1) ...
Selecting previously unselected package virtualbox-qt.
Preparing to unpack .../virtualbox-qt_5.0.40-dfsg-0ubuntu1.16.04.1_amd64.deb ...
Unpacking virtualbox-qt (5.0.40-dfsg-0ubuntu1.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up dkms (2.2.0.3-2ubuntu11.5) ...
Setting up libgsoap8:amd64 (2.8.28-1) ...
Setting up libqt4-opengl:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libsdl1.2debian:amd64 (1.2.15+dfsg1-3) ...
Setting up libvncserver1:amd64 (0.9.10+dfsg-3ubuntu0.16.04.1) ...
Setting up virtualbox-dkms (5.0.40-dfsg-0ubuntu1.16.04.1) ...
Loading new virtualbox-5.0.40 DKMS files...
First Installation: checking all kernels...
Building only for 4.10.0-38-generic
Building initial module for 4.10.0-38-generic
Done.

vboxdrv:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.10.0-38-generic/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.10.0-38-generic/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.10.0-38-generic/updates/dkms/

vboxpci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.10.0-38-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up virtualbox (5.0.40-dfsg-0ubuntu1.16.04.1) ...
vboxweb.service is a disabled or a static unit, not starting it.
Setting up virtualbox-qt (5.0.40-dfsg-0ubuntu1.16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...
girish@gk:~$ virtualbox 
girish@gk:~$ 


[sudo] password for girish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  dkms libgsoap8 libqt4-opengl libsdl1.2debian libvncserver1 virtualbox-dkms virtualbox-qt
Suggested packages:
  vde2 virtualbox-guest-additions-iso
The following NEW packages will be installed:
  dkms libgsoap8 libqt4-opengl libsdl1.2debian libvncserver1 virtualbox virtualbox-dkms virtualbox-qt
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.0 MB of archives.
After this operation, 99.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 dkms all 2.2.0.3-2ubuntu11.5 [66.3 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu xenial/universe amd64 libgsoap8 amd64 2.8.28-1 [216 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu xenial/main amd64 libqt4-opengl amd64 4:4.8.7+dfsg-5ubuntu2 [301 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu xenial/main amd64 libsdl1.2debian amd64 1.2.15+dfsg1-3 [168 kB]
Get:5 http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libvncserver1 amd64 0.9.10+dfsg-3ubuntu0.16.04.1 [122 kB]
Get:6 http://in.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 virtualbox-dkms all 5.0.40-dfsg-0ubuntu1.16.04.1 [623 kB]
Get:7 http://in.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 virtualbox amd64 5.0.40-dfsg-0ubuntu1.16.04.1 [14.3 MB]
Get:8 http://in.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 virtualbox-qt amd64 5.0.40-dfsg-0ubuntu1.16.04.1 [7,195 kB]         
Fetched 23.0 MB in 25s (905 kB/s)                                                                                                             
Selecting previously unselected package dkms.
(Reading database ... 209342 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-2ubuntu11.5_all.deb ...
Unpacking dkms (2.2.0.3-2ubuntu11.5) ...
Selecting previously unselected package libgsoap8:amd64.
Preparing to unpack .../libgsoap8_2.8.28-1_amd64.deb ...
Unpacking libgsoap8:amd64 (2.8.28-1) ...
Selecting previously unselected package libqt4-opengl:amd64.
Preparing to unpack .../libqt4-opengl_4%3a4.8.7+dfsg-5ubuntu2_amd64.deb ...
Unpacking libqt4-opengl:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Selecting previously unselected package libsdl1.2debian:amd64.
Preparing to unpack .../libsdl1.2debian_1.2.15+dfsg1-3_amd64.deb ...
Unpacking libsdl1.2debian:amd64 (1.2.15+dfsg1-3) ...
Selecting previously unselected package libvncserver1:amd64.
Preparing to unpack .../libvncserver1_0.9.10+dfsg-3ubuntu0.16.04.1_amd64.deb ...
Unpacking libvncserver1:amd64 (0.9.10+dfsg-3ubuntu0.16.04.1) ...
Selecting previously unselected package virtualbox-dkms.
Preparing to unpack .../virtualbox-dkms_5.0.40-dfsg-0ubuntu1.16.04.1_all.deb ...
Unpacking virtualbox-dkms (5.0.40-dfsg-0ubuntu1.16.04.1) ...
Selecting previously unselected package virtualbox.
Preparing to unpack .../virtualbox_5.0.40-dfsg-0ubuntu1.16.04.1_amd64.deb ...
Unpacking virtualbox (5.0.40-dfsg-0ubuntu1.16.04.1) ...
Selecting previously unselected package virtualbox-qt.
Preparing to unpack .../virtualbox-qt_5.0.40-dfsg-0ubuntu1.16.04.1_amd64.deb ...
Unpacking virtualbox-qt (5.0.40-dfsg-0ubuntu1.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up dkms (2.2.0.3-2ubuntu11.5) ...
Setting up libgsoap8:amd64 (2.8.28-1) ...
Setting up libqt4-opengl:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libsdl1.2debian:amd64 (1.2.15+dfsg1-3) ...
Setting up libvncserver1:amd64 (0.9.10+dfsg-3ubuntu0.16.04.1) ...
Setting up virtualbox-dkms (5.0.40-dfsg-0ubuntu1.16.04.1) ...
Loading new virtualbox-5.0.40 DKMS files...
First Installation: checking all kernels...
Building only for 4.10.0-38-generic
Building initial module for 4.10.0-38-generic
Done.

vboxdrv:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.10.0-38-generic/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.10.0-38-generic/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.10.0-38-generic/updates/dkms/

vboxpci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.10.0-38-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up virtualbox (5.0.40-dfsg-0ubuntu1.16.04.1) ...
vboxweb.service is a disabled or a static unit, not starting it.
Setting up virtualbox-qt (5.0.40-dfsg-0ubuntu1.16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...
girish@gk:~$ virtualbox 
girish@gk:~$ nothing happened, same as previous.... Ok let me reboot, then see what happens.

girish@gk:~$ virtualbox 
girish@gk:~$ 

```
No luck, same error as it was earlier. Terminal title disappears, virtualbox icon appears in launcher and thats all. Nothing is coming up to configure and/or install Virtual Machine.

---

### Post by vasa1 on 2017-11-08
Please post:```
df -h
```and```
sudo fdisk -l
```

---

### Post by GirishSharma on 2017-11-08
```

girish@gk:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.5M  1.6G   1% /run
/dev/sda1       205G  4.7G  190G   3% /
tmpfs           7.8G   12M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs           1.6G   52K  1.6G   1% /run/user/1000
girish@gk:~$ sudo fdisk -l
[sudo] password for girish: 
Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5475bcda

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 435589119 435587072 207.7G 83 Linux
/dev/sda2       435591166 468860927  33269762  15.9G  5 Extended
/dev/sda5       435591168 468860927  33269760  15.9G 82 Linux swap / Solaris


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x2052474d

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1          6579571 1924427647 1917848077 914.5G 70 DiskSecure Multi-Boot
/dev/sdb2       1953251627 3771827541 1818575915 867.2G 43 unknown
/dev/sdb3        225735265  225735274         10     5K 72 unknown
/dev/sdb4       2642411520 2642463409      51890  25.3M  0 Empty

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.
Partition table entries are not in disk order.


girish@gk:~$ 

```

---

### Post by GirishSharma on 2017-11-10
Issue resolved. Setting > Display and I turn off dual display. Now all is well.

Thanks to all of you who participated in my question.

---

