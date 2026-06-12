---
title: "How do I start testing and upgrade to Hardy Heron Testing?"
date: 2007-10-23
forum: The Cafe
---

### Post by RAV TUX on 2007-10-23
I love the Gutsy Gibbon but I am ready to start testing the Hardy Heron.

Any HowTo's or links on how to do this yet?

---

### Post by -grubby on 2007-10-23
what are you? crazy! Gutsy was just released. DO YOU really think that they have a testing version of Hardy Heron available yet?

---

### Post by RAV TUX on 2007-10-23
> **nathangrubb said:**
> what are you? crazy! Gutsy was just released. DO YOU really think that they have a testing version of Hardy Heron available yet?I certainly hope so. ;)

---

### Post by Paul820 on 2007-10-23
Just keep checking the development( Hardy Heron ) section RAV. I don't think it will be until november though, not until they have their next meeting on what they want to do with it.

---

### Post by LaRoza on 2007-10-23
> **RAV TUX said:**
> I love the Gutsy Gibbon but I am ready to start testing the Hardy Heron.


You have interesting relationships....

When you do get it, let us all know what you think! 

MS must be grinding their teeth, they haven't gotten the first SP out yet, and Linux chugs on forward. At least they know what to (poorly) copy.

---

### Post by FuturePilot on 2007-10-23
Repos are already open.
Do it the same way you upgraded to Gutsy
update-manager -d

Not much will be different at this point. They haven't started rolling out new packages yet.

---

### Post by p_quarles on 2007-10-23
Open up sources.list and change everything from gutsy to hardy. The repos are up, but I don't think there's anything new in them yet. 

And, obviously, keep a fire extinguisher and a bottle of ibuprofen within arm's reach at all times. :)

---

### Post by Paul820 on 2007-10-23
I hope you have a testing machine :-k

---

### Post by Paul820 on 2007-10-23
> And, obviously, keep a fire extinguisher and a bottle of ibuprofen within arm's reach at all times. 

:lolflag:

---

### Post by FuturePilot on 2007-10-23
> **p_quarles said:**
> 

And, obviously, keep a fire extinguisher and a bottle of ibuprofen within arm's reach at all times. :)

I get the bottle of ibuprofen but why the fire extinguisher?:-s :lolflag:

---

### Post by p_quarles on 2007-10-23
> **FuturePilot said:**
> but why the fire extinguisher?
Just trust me on this one. ;)

---

### Post by FuturePilot on 2007-10-23
> **p_quarles said:**
> Just trust me on this one. ;)

:lolflag:
Does Hardy catch on fire? :o

---

### Post by RAV TUX on 2007-10-23
> **FuturePilot said:**
> Repos are already open.
Do it the same way you upgraded to Gutsy
update-manager -d

Not much will be different at this point. They haven't started rolling out new packages yet.

Thanks for the 411...updating now ;)

---

### Post by Frak on 2007-10-23
Just tried Hardy, not much different than Gutsy. i.e. Nothing is different. (It just started too, so I expected that)

---

### Post by FuturePilot on 2007-10-23
> **RAV TUX said:**
> Thanks for the 411...updating now ;)

Enjoy!
Better keep that fire extinguisher around I guess;)

---

### Post by motang on 2007-10-23
> **nathangrubb said:**
> what are you? crazy! Gutsy was just released. DO YOU really think that they have a testing version of Hardy Heron available yet?

I agree 100% it way to early for Hardy Heron, I would enjoy Gutsy for now.  I am more than sure in about a couple of months you will be able to see some type of snapshot which you can test.

---

### Post by southernman on 2007-10-24
Hardy shouldn't really have anything new until November. Until then though, now is a perfect time for those who like to write howto docs, to start drafting and editing before the true rush for hardy dev/testing comes online.

I am looking forward to Hardy myself... plan to get involved with alpha testing...

---

### Post by RAV TUX on 2007-10-24
> **southernman said:**
> Hardy shouldn't really have anything new until November. Until then though, now is a perfect time for those who like to write howto docs, to start drafting and editing before the true rush for hardy dev/testing comes online.

I am looking forward to Hardy myself... plan to get involved with alpha testing...Cool to know.

---

### Post by Vibys on 2007-10-27
Dates for your calender, glad to see your so keen.

[https://wiki.ubuntu.com/HardyReleaseSchedule](https://wiki.ubuntu.com/HardyReleaseSchedule)

---

### Post by RAV TUX on 2007-10-27
> **Vibys said:**
> Dates for your calender, glad to see your so keen.

[https://wiki.ubuntu.com/HardyReleaseSchedule](https://wiki.ubuntu.com/HardyReleaseSchedule)

ahh...so soon!

Thanks for the 411! ;)

---

### Post by Frak on 2007-10-27
> **Vibys said:**
> Dates for your calender, glad to see your so keen.

[https://wiki.ubuntu.com/HardyReleaseSchedule](https://wiki.ubuntu.com/HardyReleaseSchedule)
Thanks :)

---

### Post by davidshere on 2007-10-30
My results:

```
david@sabre:~$ sudo update-manager -d
[sudo] password for david:
warning: could not initiate dbus
david@sabre:~$ 

```

I seem to remember this dbus thing being a problem last time.  Anyway, the window comes up, firmly declares that my machine is up to date, and then laughs -- cackles, really -- at me.

---

### Post by misfitpierce on 2007-10-30
Nov. 29th I believe is Alpha 1 testing and is when it should be pushed into gear. Thats when I plan to look into next version anyway. Till then im sufficient with Gutsy.

---

### Post by urukrama on 2007-10-30
> **RAV TUX said:**
> Thanks for the 411! ;)

What are the 411 you keep mentioning?

---

### Post by RAV TUX on 2007-10-30
> **urukrama said:**
> What are the 411 you keep mentioning?

411 is the phone # in the US that you dial for information.

411=information

---

### Post by urukrama on 2007-10-30
Oh, I see.

---

### Post by davidshere on 2007-11-02
I'm getting updates on hardy!

```
david@nighthawk:~$ sudo sed -e 's/\sgutsy/ hardy/g' -i /etc/apt/sources.list
[sudo] password for david:
david@nighthawk:~$ su
Password: 
root@nighthawk:/home/david# apt-get update
Get:1 http://us.archive.ubuntu.com hardy Release.gpg [191B]                                               
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Get:2 http://security.ubuntu.com hardy-security Release.gpg [191B]
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Get:3 http://us.archive.ubuntu.com hardy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Get:4 http://security.ubuntu.com hardy-security Release [37.1kB]
Get:5 http://us.archive.ubuntu.com hardy Release [65.9kB]
Get:6 http://security.ubuntu.com hardy-security/main Packages [14B]
Get:7 http://us.archive.ubuntu.com hardy-updates Release [37.0kB]          
Get:8 http://security.ubuntu.com hardy-security/restricted Packages [14B] 
Get:9 http://security.ubuntu.com hardy-security/main Sources [14B]        
Get:10 http://security.ubuntu.com hardy-security/restricted Sources [14B] 
Get:11 http://us.archive.ubuntu.com hardy/main Packages [1079kB]                                                                                            
Get:12 http://us.archive.ubuntu.com hardy/restricted Packages [7628B]                                                                                       
Get:13 http://us.archive.ubuntu.com hardy/main Sources [308kB]                                                                                              
Get:14 http://us.archive.ubuntu.com hardy/restricted Sources [2107B]                                                                                        
Get:15 http://us.archive.ubuntu.com hardy-updates/main Packages [14B]                                                                                       
Get:16 http://us.archive.ubuntu.com hardy-updates/restricted Packages [14B]                                                                                 
Get:17 http://us.archive.ubuntu.com hardy-updates/main Sources [14B]                                                                                        
Get:18 http://us.archive.ubuntu.com hardy-updates/restricted Sources [14B]                                                                                  
Fetched 1538kB in 31s (48.3kB/s)                                                                                                                            
Reading package lists... Done
root@nighthawk:/home/david# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  ubuntu-desktop xorg xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-cyrix
  xserver-xorg-video-dummy xserver-xorg-video-fbdev xserver-xorg-video-i740 xserver-xorg-video-i810 xserver-xorg-video-imstt xserver-xorg-video-intel
  xserver-xorg-video-neomagic xserver-xorg-video-newport xserver-xorg-video-nv xserver-xorg-video-s3virge xserver-xorg-video-sis xserver-xorg-video-sisusb
  xserver-xorg-video-tdfx xserver-xorg-video-tga xserver-xorg-video-trident xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vga
The following NEW packages will be installed:
  cpp-4.2 gcc-4.2 libgomp1 libpixman-1-0 libsmbios1
The following packages have been kept back:
  gnome-orca hal xserver-xorg-core xserver-xorg-input-elographics xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-video-amd xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-glint xserver-xorg-video-i128 xserver-xorg-video-mga
  xserver-xorg-video-nsc xserver-xorg-video-rendition xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-tseng xserver-xorg-video-via xserver-xorg-video-vmware xserver-xorg-video-voodoo
The following packages will be upgraded:
  adduser apport apport-gtk apturl base-files base-passwd binutils binutils-static bittorrent bluez-cups bluez-utils bsdmainutils bsdutils compiz
  compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins console-terminus cpp cpp-4.1 cupsys cupsys-bsd
  cupsys-client cupsys-common debconf debconf-i18n debianutils dhcdbd dictionaries-common doc-base docbook-xml dosfstools eject ethtool file firefox
  firefox-gnome-support gcc gcc-4.1 gcc-4.1-base gcc-4.2-base gcj-4.2-base ghostscript ghostscript-x gij-4.2 gnome-btdownload grep groff-base gs-esp-x
  hpijs hplip hplip-data iso-codes java-gcj-compat less lftp libao2 libasound2 libattr1 libaudio2 libbcel-java libbluetooth2 libc6 libc6-i686 libcaca0
  libcairo-perl libcairomm-1.0-1 libcucul0 libcupsimage2 libcupsys2 libdatrie0 libdecoration0 libedit2 libestools1.2 libexif12 libgcc1 libgcj-bc
  libgcj-common libgcj8-1 libgcj8-jar libgcrypt11 libgdl-1-0 libgdl-1-common libgdl-gnome-1-0 libglib-perl libgnome2-vfs-perl libgpg-error0 libgpod2 libgs8
  libgsf-1-114 libgsf-1-common libgtk2-perl libgtop2-7 libgtop2-common libhal-storage1 libhal1 libhunspell-1.1-0 libice6 libicu36 libidn11 libieee1284-3
  libjaxp1.3-java libkeyutils1 libkpathsea4 libkrb53 libldap2 liblircclient0 libmagic1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon26
  libnet-dbus-perl libnl1-pre6 libnspr4-0d libnss-mdns libnss3-0d libpcap0.8 libpcre3 libpcrecpp0 libpng12-0 libpq5 librarian0 libscim8c2a
  libservlet2.3-java libslang2 libsoup2.2-8 libsqlite0 libsqlite3-0 libstdc++6 libtasn1-3 libvorbis0a libvorbisenc2 libvorbisfile3 libxcursor1 libxi6
  libxklavier11 libxpm4 libxrandr2 libxrender1 libxxf86dga1 login lsof man-db manpages mktemp module-init-tools mount notification-daemon passwd
  pcmciautils procps python-apport python-apt python-bittorrent python-epydoc python-launchpad-bugs python-problem-report python-software-properties
  python-support rdesktop scim scim-gtk2-immodule scim-modules-socket screen sed software-properties-gtk startup-tasks system-services tcl8.4 tcpdump
  ttf-arabeyes tzdata ucf update-inetd upstart upstart-compat-sysv upstart-logd util-linux util-linux-locales vim vim-common vim-runtime vim-tiny wamerican
  wbritish whois xauth xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings xinit xpmutils
195 upgraded, 5 newly installed, 25 to remove and 22 not upgraded.
Need to get 117MB of archives.
After unpacking 4997kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

### Post by puppy on 2007-11-02
you people are :-\"   

I mean I like a bit of excitement but upgrading to Hardy days after the repos open? Even Chuck Norris isn't hard enough to try that... 

just keep [-o<, and you never know it might not crash and burn lol

---

### Post by Phil Airtime on 2007-11-02
Or worse... your computer could start speaking to you in Welsh. That'd show you early upgraders.

---

### Post by ZebCarnell on 2007-11-02
I'd be more woried if my computer started speaking to me in an Australian accent :P

---

### Post by Majorix on 2007-12-07
Is it time I shall upgrade to Hardy? Alpha 1 is already out like for 10 days or so, and I always want to have the latest version of software. Do you think I should upgrade now?

---

### Post by ssam on 2007-12-07
read the Sticky, How To Test Hardy in the dev forum before atempting to upgrade to hardy.

---

### Post by jeffus_il on 2008-01-04
I have been running it for about a month with no special problems, everything works, compiz and NetworkManager are a but of a nuisance but I don't need them.
 Not it doesn't blow up after you install it ...

---

### Post by johndoe32102002 on 2008-03-25
> **p_quarles said:**
> Open up sources.list and change everything from gutsy to hardy. The repos are up, but I don't think there's anything new in them yet. 

And, obviously, keep a fire extinguisher and a bottle of ibuprofen within arm's reach at all times. :)

There is a more stable version of KDE4 and the newest version of Ktorrent, which is not available in Gusty.

---

### Post by p_quarles on 2008-03-25
> **johndoe32102002 said:**
> There is a more stable version of KDE4 and the newest version of Ktorrent, which is not available in Gusty.
I'm sure there is. You'll note, however, that you are quoting a post that was made when the first Hardy Heron images had just been released. Five months later, we have a Beta release. 

Just one of the many risks of thread necromancy.

---

### Post by LaRoza on 2008-03-25
> **p_quarles said:**
> I'm sure there is. You'll note, however, that you are quoting a post that was made when the first Hardy Heron images had just been released. Five months later, we have a Beta release. 

Just one of the many risks of thread necromancy.


[img]http://img181.imageshack.us/img181/8060/necromancingsv7.jpg[/img]

---

