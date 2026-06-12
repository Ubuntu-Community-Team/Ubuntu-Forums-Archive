---
title: "no sound using zorin 9 lite and sony viao vgn-a397xp"
date: 2016-04-01
forum: Ubuntu/Debian BASED
---

### Post by tony117 on 2016-04-01
hello im new to this and am having problems getting any sound from my laptop using zorin have try'd a few things i read here any help would be good thanks again tony. i get sound on the vaio startup then nothing after.

[http://www.alsa-project.org/db/?f=0c28e7d25fbe610d7310cf378bdb6bfb7684f0c6](http://www.alsa-project.org/db/?f=0c28e7d25fbe610d7310cf378bdb6bfb7684f0c6)

```
tony@laptop:~$ cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd; find /lib/modules/`uname -r` | grep snd ;cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; pacmd list-sinks; aplay -l; sudo alsa force-reload;  ubuntu-support-status ; sudo lshw -C sound
Advanced Linux Sound Architecture Driver Version k3.13.0-32-generic.
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 42
  1:        : sequencer
  2: [ 0- 2]: digital audio capture
  3: [ 0- 1]: digital audio playback
  4: [ 0- 1]: digital audio capture
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0- 1]: hardware dependent
  8: [ 0- 0]: hardware dependent
  9: [ 0]   : control
 33:        : timer
00-01: HDA Codec 1
00-00: HDA Codec 0
00-00: ALC260 Analog : ALC260 Analog : playback 1 : capture 1
00-01: ALC260 Digital : ALC260 Digital : playback 1 : capture 1
00-02: ALC260 Alt Analog : ALC260 Alt Analog : capture 1
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
[sudo] password for tony: 
rm: cannot remove &#8216;/etc/asound.conf&#8217;: No such file or directory
rm: cannot remove &#8216;/home/tony/.pulse&#8217;: No such file or directory
rm: cannot remove &#8216;/home/tony/.asound*&#8217;: No such file or directory
rm: cannot remove &#8216;/home/tony/.pulse-cookie&#8217;: No such file or directory
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://deb.opera.com](http://deb.opera.com) stable InRelease [2,590 B]                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [181 B]                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease [15.5 kB]                      
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty InRelease                              
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [1,189 B]                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Err [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed InRelease [65.9 kB]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [1,568 B]             
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Sources [5,352 B]
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [220 B]             
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Sources [271 kB]       
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Sources [151 kB]   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Sources [5,946 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main i386 Packages [713 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B] 
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [110 kB]        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB                     
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe i386 Packages [358 kB]
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.6 kB]
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Translation-en [372 kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [34.7 kB]   
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Translation-en [7,227 B]
Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,699 B]
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Translation-en [186 kB]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,750 B] 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted Sources    
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [422 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe Translation-en      
Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/restricted Sources [28 B]  
Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/main Sources [132 kB]      
Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/universe Sources [18.7 kB] 
Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/multiverse Sources [28 B]  
Get:32 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/restricted i386 Packages [28 B]
Get:33 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/main i386 Packages [135 kB]
Get:34 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/universe i386 Packages [29.4 kB]
Get:35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/multiverse i386 Packages [28 B]
Get:36 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/main Translation-en [55.7 kB]
Get:37 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/multiverse Translation-en [28 B]
Get:38 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/restricted Translation-en [28 B]
Get:39 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/universe Translation-en [19.4 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en_GB                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en_GB      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en         
Get:40 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Get:41 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [126 kB]
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [5,175 B]
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [244 kB]
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [2,570 B]
Get:45 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [3,206 B]
Get:46 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [74.3 kB]
Fetched 3,753 kB in 5s (712 kB/s)                                         
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com](http://deb.opera.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/InRelease](http://deb.opera.com/opera/dists/stable/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cifs-utils kde-l10n-de kde-l10n-engb kde-l10n-es kde-l10n-fr kde-l10n-ru
  localechooser-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apt-xapian-index aptitude-common libboost-iostreams1.54.0
  libclass-accessor-perl libcwidget3 libio-string-perl
  libparse-debianchangelog-perl libsub-name-perl python-xapian
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-template-perl libxml-simple-perl xapian-doc
The following NEW packages will be installed
  apt-xapian-index aptitude aptitude-common libboost-iostreams1.54.0
  libclass-accessor-perl libcwidget3 libio-string-perl
  libparse-debianchangelog-perl libsub-name-perl python-xapian
0 to upgrade, 10 to newly install, 0 to remove and 482 not to upgrade.
Need to get 2,741 kB of archives.
After this operation, 12.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main libboost-iostreams1.54.0 i386 1.54.0-4ubuntu3.1 [29.3 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main python-xapian i386 1.2.16-2ubuntu1 [198 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main apt-xapian-index all 0.45ubuntu4 [56.4 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main aptitude-common all 0.6.8.2-1ubuntu4 [700 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main libcwidget3 i386 0.5.16-3.5ubuntu1 [300 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main aptitude i386 0.6.8.2-1ubuntu4 [1,356 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main libsub-name-perl i386 0.05-1build4 [9,690 B]
Get:8 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main libclass-accessor-perl all 0.34-1 [26.0 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main libio-string-perl all 1.08-3 [11.1 kB]
Get:10 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main libparse-debianchangelog-perl all 1.2.0-1ubuntu1 [54.0 kB]
Fetched 2,741 kB in 1s (1,723 kB/s)                  
Selecting previously unselected package libboost-iostreams1.54.0:i386.
(Reading database ... 172828 files and directories currently installed.)
Preparing to unpack .../libboost-iostreams1.54.0_1.54.0-4ubuntu3.1_i386.deb ...
Unpacking libboost-iostreams1.54.0:i386 (1.54.0-4ubuntu3.1) ...
Selecting previously unselected package python-xapian.
Preparing to unpack .../python-xapian_1.2.16-2ubuntu1_i386.deb ...
Unpacking python-xapian (1.2.16-2ubuntu1) ...
Selecting previously unselected package apt-xapian-index.
Preparing to unpack .../apt-xapian-index_0.45ubuntu4_all.deb ...
Unpacking apt-xapian-index (0.45ubuntu4) ...
Selecting previously unselected package aptitude-common.
Preparing to unpack .../aptitude-common_0.6.8.2-1ubuntu4_all.deb ...
Unpacking aptitude-common (0.6.8.2-1ubuntu4) ...
Selecting previously unselected package libcwidget3.
Preparing to unpack .../libcwidget3_0.5.16-3.5ubuntu1_i386.deb ...
Unpacking libcwidget3 (0.5.16-3.5ubuntu1) ...
Selecting previously unselected package aptitude.
Preparing to unpack .../aptitude_0.6.8.2-1ubuntu4_i386.deb ...
Unpacking aptitude (0.6.8.2-1ubuntu4) ...
Selecting previously unselected package libsub-name-perl.
Preparing to unpack .../libsub-name-perl_0.05-1build4_i386.deb ...
Unpacking libsub-name-perl (0.05-1build4) ...
Selecting previously unselected package libclass-accessor-perl.
Preparing to unpack .../libclass-accessor-perl_0.34-1_all.deb ...
Unpacking libclass-accessor-perl (0.34-1) ...
Selecting previously unselected package libio-string-perl.
Preparing to unpack .../libio-string-perl_1.08-3_all.deb ...
Unpacking libio-string-perl (1.08-3) ...
Selecting previously unselected package libparse-debianchangelog-perl.
Preparing to unpack .../libparse-debianchangelog-perl_1.2.0-1ubuntu1_all.deb ...
Unpacking libparse-debianchangelog-perl (1.2.0-1ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up libboost-iostreams1.54.0:i386 (1.54.0-4ubuntu3.1) ...
Setting up python-xapian (1.2.16-2ubuntu1) ...
Setting up apt-xapian-index (0.45ubuntu4) ...
apt-xapian-index: Building new index in background...
Setting up aptitude-common (0.6.8.2-1ubuntu4) ...
Setting up libcwidget3 (0.5.16-3.5ubuntu1) ...
Setting up aptitude (0.6.8.2-1ubuntu4) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode
Setting up libsub-name-perl (0.05-1build4) ...
Setting up libclass-accessor-perl (0.34-1) ...
Setting up libio-string-perl (1.08-3) ...
Setting up libparse-debianchangelog-perl (1.2.0-1ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.1) ...
No candidate version found for libsdl1.2debian-pulseaudio
No candidate version found for libsdl1.2debian-pulseaudio
The following packages will be REMOVED:
  cifs-utils{u} kde-l10n-de{u} kde-l10n-engb{u} kde-l10n-es{u} 
  kde-l10n-fr{u} kde-l10n-ru{u} localechooser-data{u} 
0 packages upgraded, 0 newly installed, 7 to remove and 478 not upgraded.
Need to get 0 B of archives. After unpacking 209 MB will be freed.
Do you want to continue? [Y/n/?] y
(Reading database ... 173091 files and directories currently installed.)
Removing cifs-utils (2:6.0-1ubuntu2) ...
Removing kde-l10n-de (4:4.13.3-0ubuntu0.1) ...
Removing kde-l10n-engb (4:4.13.0-0ubuntu1) ...
Removing kde-l10n-es (4:4.13.0-0ubuntu1) ...
Removing kde-l10n-fr (4:4.13.0-0ubuntu1) ...
Removing kde-l10n-ru (4:4.13.0-0ubuntu1) ...
Removing localechooser-data (2.49ubuntu5) ...
Processing triggers for man-db (2.6.7.1-1) ...
                                         
Current status: 478 updates [-4].
H/W path        Device      Class       Description
===================================================
                            system      VGN-A397XP
/0                          bus         Motherboard
/0/0                        memory      64KiB BIOS
/0/3                        processor   Intel(R) Pentium(R) M processor 2.00GHz
/0/3/4                      memory      32KiB L1 cache
/0/3/5                      memory      2MiB L2 cache
/0/9                        memory      1536MiB System Memory
/0/9/0                      memory      512MiB SODIMM DDR
/0/9/1                      memory      1GiB SODIMM DDR
/0/100                      bridge      Mobile 915GM/PM/GMS/910GML Express Proce
/0/100/1                    bridge      Mobile 915GM/PM Express PCI Express Root
/0/100/1/0                  display     RV380/M24 [Mobility Radeon X600]
/0/100/1b                   multimedia  82801FB/FBM/FR/FW/FRW (ICH6 Family) High
/0/100/1d                   bus         82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 
/0/100/1d.1                 bus         82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 
/0/100/1d.2                 bus         82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 
/0/100/1d.3                 bus         82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 
/0/100/1d.7                 bus         82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2
/0/100/1e                   bridge      82801 Mobile PCI Bridge
/0/100/1e/1                 bridge      PCI7420 CardBus Controller
/0/100/1e/1.2               bus         PCI7x20 1394a-2000 OHCI Two-Port PHY/Lin
/0/100/1e/1.3               storage     PCI7420/7620 SD/MS-Pro Controller
/0/100/1e/2     eth1        network     PRO/Wireless 2200BG [Calexico2] Network 
/0/100/1e/3     eth0        network     RTL8169 PCI Gigabit Ethernet Controller
/0/100/1f                   bridge      82801FBM (ICH6M) LPC Interface Bridge
/0/100/1f.1                 storage     82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE 
/0/100/1f.2                 storage     82801FBM (ICH6M) SATA Controller
/0/100/1f.3                 bus         82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBu
/0/1            scsi0       storage     
/0/1/0.0.0      /dev/cdrom  disk        DVD RW DW-D56A
/0/2            scsi2       storage     
/0/2/0.0.0      /dev/sda    disk        120GB Hitachi HTS54161
/0/2/0.0.0/1    /dev/sda1   volume      243MiB Linux filesystem partition
/0/2/0.0.0/2    /dev/sda2   volume      111GiB Extended partition
/0/2/0.0.0/2/5  /dev/sda5   volume      111GiB Linux LVM Physical Volume partiti
total 0
crw-rw----+  1 root audio 116, 33 Apr  1 10:51 timer
crw-rw----+  1 root audio 116,  1 Apr  1 10:51 seq
crw-rw----+  1 root audio 116,  2 Apr  1 10:51 pcmC0D2c
crw-rw----+  1 root audio 116,  7 Apr  1 10:51 hwC0D1
crw-rw----+  1 root audio 116,  8 Apr  1 10:51 hwC0D0
crw-rw----+  1 root audio 116,  9 Apr  1 10:51 controlC0
drwxr-xr-x   2 root root       60 Apr  1 10:51 by-path
drwxr-xr-x   3 root root      260 Apr  1 10:51 .
crw-rw----+  1 root audio 116,  3 Apr  1 10:52 pcmC0D1p
crw-rw----+  1 root audio 116,  4 Apr  1 10:52 pcmC0D1c
crw-rw----+  1 root audio 116,  5 Apr  1 10:52 pcmC0D0p
crw-rw----+  1 root audio 116,  6 Apr  1 10:52 pcmC0D0c
drwxr-xr-x  16 root root     4180 Apr  1 11:05 ..
/lib/modules/3.13.0-32-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/3.13.0-32-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/3.13.0-32-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/3.13.0-32-generic/kernel/sound/spi/snd-at73c213.ko
/lib/modules/3.13.0-32-generic/kernel/sound/soc/mid-x86/snd-soc-mfld-machine.ko
/lib/modules/3.13.0-32-generic/kernel/sound/soc/mid-x86/snd-soc-sst-platform.ko
/lib/modules/3.13.0-32-generic/kernel/sound/soc/generic/snd-soc-simple-card.ko
/lib/modules/3.13.0-32-generic/kernel/sound/soc/codecs/snd-soc-sn95031.ko
/lib/modules/3.13.0-32-generic/kernel/sound/soc/codecs/snd-soc-si476x.ko
/lib/modules/3.13.0-32-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/3.13.0-32-generic/kernel/sound/soc/atmel/snd-soc-atmel-pcm.ko
/lib/modules/3.13.0-32-generic/kernel/sound/firewire/snd-dice.ko
/lib/modules/3.13.0-32-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/3.13.0-32-generic/kernel/sound/firewire/snd-firewire-speakers.ko
/lib/modules/3.13.0-32-generic/kernel/sound/firewire/snd-scs1x.ko
/lib/modules/3.13.0-32-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.13.0-32-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/3.13.0-32-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/msnd
/lib/modules/3.13.0-32-generic/kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/msnd/snd-msnd-classic.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/msnd/snd-msnd-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/snd-cmi8328.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/galaxy/snd-azt1605.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/galaxy/snd-azt2316.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/sb/snd-jazz16.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/3.13.0-32-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-compress.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-timer.ko
/lib/modules/3.13.0-32-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/hiface/snd-usb-hiface.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.13.0-32-generic/kernel/sound/usb/snd-usbmidi-lib.ko
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 04)
00:1d.0 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04)
00:1d.1 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04)
00:1d.2 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04)
00:1d.3 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04)
00:1d.7 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 04)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 04)
01:01.0 CardBus bridge [0607]: Texas Instruments PCI7420 CardBus Controller [104c:ac8e]
01:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller [104c:802e]
01:01.3 Mass storage controller [0180]: Texas Instruments PCI7420/7620 SD/MS-Pro Controller [104c:ac8f]
01:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
01:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller [10ec:8169] (rev 10)
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV380/M24 [Mobility Radeon X600] [1002:3150]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 044e:3007 Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGX)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c50a Logitech, Inc. Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
/usr/sbin/alsactl
Specified file name /dev/dsp does not exist.
                     USER PID ACCESS COMMAND
/dev/snd/controlC0:  tony       1796 F.... pulseaudio
dpkg-query: no path found matching pattern *bin/slmodemd*
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [c00ff780]
[    0.097893] ACPI: No dock devices found.
[    0.109297] Found 1 acpi root devices
[    0.132740] pnp: PnP ACPI: found 14 devices
[    0.878457] audit: initializing netlink socket (disabled)
[    0.878476] type=2000 audit(1459504293.876:1): initialized
[    1.408558] libphy: Fixed MDIO Bus: probed
[    1.456467] isapnp: No Plug & Play device found
[    1.456568] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.456713] hub 1-0:1.0: USB hub found
[    1.457195] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.457326] hub 2-0:1.0: USB hub found
[    1.457627] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.457753] hub 3-0:1.0: USB hub found
[    1.458035] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.458164] hub 4-0:1.0: USB hub found
[    1.458453] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.458579] hub 5-0:1.0: USB hub found
[    1.485711] IMA: No TPM chip found, activating TPM-bypass!
[    1.486416] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.446178] usb 2-2: New USB device found, idVendor=046d, idProduct=c50a
[    2.889469] usb 5-2: New USB device found, idVendor=044e, idProduct=3007
[   22.208275] lp: driver loaded but no devices found
[   23.037684] yenta_cardbus 0000:01:01.0: CardBus bridge found [104d:818f]
[   23.052449] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   23.270628] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x9000-0x9fff:
[   23.271627]  excluding 0x9000-0x90ff 0x9400-0x94ff 0x9800-0x98ff
[   23.314467] pcmcia_socket pcmcia_socket0: cs: memory probe 0xfe900000-0xfe9fffff:
[   23.314477]  excluding 0xfe9c0000-0xfe9dffff 0xfe9f0000-0xfe9fffff
[   23.314487] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x63ffffff:
[   23.314500]  excluding 0x60000000-0x63ffffff
[   23.477419] type=1400 audit(1459504317.486:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=460 comm="apparmor_parser"
[   23.477431] type=1400 audit(1459504317.486:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=460 comm="apparmor_parser"
[   23.477439] type=1400 audit(1459504317.486:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=460 comm="apparmor_parser"
[   23.478148] type=1400 audit(1459504317.486:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=460 comm="apparmor_parser"
[   23.478157] type=1400 audit(1459504317.486:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=460 comm="apparmor_parser"
[   23.478521] type=1400 audit(1459504317.486:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=460 comm="apparmor_parser"
[   23.493673] type=1400 audit(1459504317.502:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=475 comm="apparmor_parser"
[   24.891150] snd_hda_intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[   24.972380] input: HDA Intel SPDIF In as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   24.973031] input: HDA Intel SPDIF as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   24.973258] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   24.973461] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   24.973681] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   24.973887] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   31.930374] type=1400 audit(1459504325.938:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=865 comm="apparmor_parser"
[   31.930387] type=1400 audit(1459504325.938:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=865 comm="apparmor_parser"
[   31.931086] type=1400 audit(1459504325.938:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=865 comm="apparmor_parser"
[   32.294707] type=1400 audit(1459504326.302:12): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=936 comm="apparmor_parser"
[   32.294721] type=1400 audit(1459504326.302:13): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=936 comm="apparmor_parser"
[   32.304627] type=1400 audit(1459504326.314:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=936 comm="apparmor_parser"
[   32.312987] type=1400 audit(1459504326.322:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=937 comm="apparmor_parser"
[   32.313002] type=1400 audit(1459504326.322:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=937 comm="apparmor_parser"
[   32.313010] type=1400 audit(1459504326.322:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=937 comm="apparmor_parser"
[   32.313715] type=1400 audit(1459504326.322:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=937 comm="apparmor_parser"
[   62.224086] audit_printk_skb: 84 callbacks suppressed
[   62.224092] type=1400 audit(1459504355.566:47): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2069 comm="apparmor_parser"
[   62.224103] type=1400 audit(1459504355.566:48): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2069 comm="apparmor_parser"
[   62.224835] type=1400 audit(1459504355.566:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2069 comm="apparmor_parser"
sudo: /etc/init.d/sl-modem-daemon: command not found
/etc/modprobe.d/alsa-base.conf:options snd-hda-intel model=vaio
/etc/modprobe.d/alsa-base.conf~:options snd-hda-intel model=vaio
/etc/modprobe.d/alsa-base.conf~:options snd-hda-intel model=vaio
/etc/modprobe.d/alsa-base.conf.save:options snd-hda-intel model=sony
    Release Date: 12/16/2004
    Manufacturer: Sony Corporation
    Product Name: VGN-A397XP
    Serial Number: 28193250-5101192
    Manufacturer: Sony Corporation
    Serial Number: C000722J
    Manufacturer: GenuineIntel
    Serial Number: N/A
snd_seq_dummy          12686  0 
snd_hda_codec_realtek    55125  1 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  3 snd_seq_midi_event,snd_seq_dummy,snd_seq_midi
snd_seq_device         14137  4 snd_seq,snd_rawmidi,snd_seq_dummy,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
btusb                  27580  0 
bluetooth             342206  22 bnep,btusb,rfcomm
snd                    60871  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_dummy,snd_seq_midi
soundcore              12600  1 snd
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
Welcome to PulseAudio! Use "help" for usage information.
>>> 1 sink(s) available.
  * index: 0
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9959
    volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_00_1b.0>
    module: 5
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC260 Analog"
        alsa.id = "ALC260 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel"
        alsa.long_card_name = "HDA Intel at 0xfebf8000 irq 42"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "2668"
        device.product.name = "82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analogue Stereo"
        device.description = "Built-in Audio Analogue Stereo"
        alsa.mixer_name = "Realtek ALC260"
        alsa.components = "HDA:10ec0260,02600000,00100300 HDA:14f12bfa,20030003,00090000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output-headphones>
>>> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC260 Digital [ALC260 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Unloading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.
Traceback (most recent call last):
  File "/usr/bin/ubuntu-support-status", line 133, in <module>
    pkg.name, support_tag)
  File "/usr/bin/ubuntu-support-status", line 49, in get_maintenance_status
    raise Exception("No date tag found")
Exception: No date tag found
  *-multimedia            
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:42 memory:febf8000-febfbfff
tony@laptop:~$
```

---

### Post by howefield on 2016-04-01
Thread moved to the "*Ubuntu/Debian BASED*" forum and code tags added.

---

