---
title: "An Error Occurred When Checking For Live Patch Updates"
date: 2019-06-14
forum: Ubuntu/Debian BASED
---

### Post by aoandres on 2019-06-14
[IMG]http://i.imgur.com/P7sADpJ.png[/IMG]

i'mgetting this error message i  tryied refreshing snaps,turning off and on,changed TOKENS, watched some youtube videos(there was only 2),followed the links yet the problem remains...and nothing seem to work...maybe there is someone smarter than me and could help me out? 
Here are some inputs i itryied....



```
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo apt update
[sudo] password for andres: 
Ign:1 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic InRelease
Err:2 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit:3 [https://installer.id.ee/media/ubuntu](https://installer.id.ee/media/ubuntu) bionic InRelease
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease            
Hit:5 [http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu](http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu) bionic InRelease
Ign:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease          
Ign:7 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease           
Hit:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release            
Hit:9 [http://repo.yandex.ru/yandex-disk/deb](http://repo.yandex.ru/yandex-disk/deb) stable InRelease          
Hit:10 [http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu](http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu) bionic InRelease
Hit:11 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release            
Hit:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease              
Hit:13 [http://ppa.launchpad.net/papirus/papirus/ubuntu](http://ppa.launchpad.net/papirus/papirus/ubuntu) bionic InRelease
Hit:14 [http://packages.microsoft.com/repos/vscode](http://packages.microsoft.com/repos/vscode) stable InRelease    
Hit:15 [http://ppa.launchpad.net/peterlevi/ppa/ubuntu](http://ppa.launchpad.net/peterlevi/ppa/ubuntu) bionic InRelease 
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]
Hit:17 [http://ppa.launchpad.net/slytomcat/ppa/ubuntu](http://ppa.launchpad.net/slytomcat/ppa/ubuntu) bionic InRelease 
Hit:18 [https://packages.microsoft.com/ubuntu/18.04/prod](https://packages.microsoft.com/ubuntu/18.04/prod) bionic InRelease
Hit:19 [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) bionic InRelease
Hit:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease    
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]
Hit:21 [https://packagecloud.io/slacktechnologies/slack/debian](https://packagecloud.io/slacktechnologies/slack/debian) jessie InRelease
Reading package lists... Done                    
E: The repository 'cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/earth/deb stable InRelease' doesn't support architecture 'i386'
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo apt autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del google-chrome-stable 75.0.3770.80-1 [58.9 MB]
Del firefox 67.0.1+build1-0ubuntu0.18.04.1 [48.7 MB]
Del firefox-locale-en 67.0.1+build1-0ubuntu0.18.04.1 [956 kB]
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ uname -a
Linux andres-HP-Pavilion-Laptop-15-cd0xx 4.15.0-23-generic #25-Ubuntu SMP Wed May 23 18:02:16 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo snap refresh
Automatically connect eligible plugs and slots of snap "gnome-system-monitor"            Automatically connect eligible plugs and slots of snap "gnome-system-monitor"          Automatically connect eligible plugs and slots of snap "gnome-system-monitor"        Automatically connect eligible plugs and slots of snap "gnome-system-monitor"      code c7d83e57 from Visual Studio Code (vscode&#10003;) refreshed
gnome-characters v3.32.1+git2.3367201 from Canonical&#10003; refreshed
gnome-system-monitor 3.32.1-2-ga7c19eaeff from Canonical&#10003; refreshed
gnome-3-28-1804 3.28.0-10-gaa70833.aa70833 from Canonical&#10003; refreshed
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ snap list
Name                  Version                     Rev   Tracking  Publisher     Notes
canonical-livepatch   9.3.0                       77    stable    canonical&#10003;    -
cloudtag              0.9.1                       7     stable    fedegratti    -
code                  c7d83e57                    9     stable    vscode&#10003;       classic
communitheme          0.1                         1768  stable    didrocks      -
core                  16-2.39                     6964  stable    canonical&#10003;    core
core18                20190508                    970   stable    canonical&#10003;    base
gnome-3-26-1604       3.26.0.20190606             86    stable    canonical&#10003;    -
gnome-3-28-1804       3.28.0-10-gaa70833.aa70833  55    stable    canonical&#10003;    -
gnome-calculator      3.32.1                      406   stable/&#8230;  canonical&#10003;    -
gnome-characters      v3.32.1+git2.3367201        284   stable/&#8230;  canonical&#10003;    -
gnome-logs            3.32.0-4-ge8f3f37ca8        61    stable/&#8230;  canonical&#10003;    -
gnome-system-monitor  3.32.1-2-ga7c19eaeff        87    stable/&#8230;  canonical&#10003;    -
gtk-common-themes     0.1-16-g2287c87             1198  stable    canonical&#10003;    -
simplescreenrecorder  0.1                         1     stable    xiaoguo       -
sublime-text          3207                        58    stable    snapcrafters  classic
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo snap refresh canonical-livepatch
snap "canonical-livepatch" has no updates available
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo snap info canonical-livepatch
name:      canonical-livepatch
summary:   Canonical Livepatch Client
publisher: Canonical&#10003;
contact:   [email]snaps@canonical.com[/email]
license:   unset
description: |
  Canonical Livepatch Client
commands:
  - canonical-livepatch
services:
  canonical-livepatch.canonical-livepatchd: simple, enabled, active
snap-id:      b96UJ4vttpNhpbaCWctVzfduQcPwQ5wn
tracking:     stable
refresh-date: 22 days ago, at 12:33 EEST
channels:
  stable:    9.3.0 2019-05-06 (77) 8MB -
  candidate: 9.3.0 2019-05-06 (77) 8MB -
  beta:      9.3.0 2019-05-06 (77) 8MB -
  edge:      9.4.1 2019-06-13 (81) 8MB -
installed:   9.3.0            (77) 8MB -
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ df -
df: -: No such file or directory
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ df-

Command 'df-' not found, did you mean:

  command 'df' from deb coreutils
  command 'dfc' from deb dfc

Try: sudo apt install <deb name>

andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ df- -h

Command 'df-' not found, did you mean:

  command 'dfc' from deb dfc
  command 'df' from deb coreutils

Try: sudo apt install <deb name>

andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ df/ -h
bash: df/: No such file or directory
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo canonical-livepatch disable
Successfully disabled device. Removed machine-token: 68941dbd184443519e9df1b089718e6a
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo canonical-livepatch enable
2019/06/14 16:22:40 error executing enable: No key provided.
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo canonical-livepatch enable 68941dbd184443519e9df1b089718e6a
2019/06/14 16:23:17 error executing enable: cannot enable machine: bad server status 403 (URL: [https://livepatch.canonical.com/api/machine-tokens):](https://livepatch.canonical.com/api/machine-tokens):) {"error": "Unknown Auth-Token"}
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo canonical-livepatch enable <hash>
bash: syntax error near unexpected token `newline'
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo canonical-livepatch enable
2019/06/14 16:32:06 error executing enable: No key provided.
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo canonical-livepatch enable 68941dbd184443519e9df1b089718e6a
2019/06/14 16:32:20 error executing enable: Machine-token already exists! Please use 'disable' to delete existing machine-token.
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ 
```

```
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo canonical-livepatch disable
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo snap install canonical-livepatch
snap "canonical-livepatch" is already installed, see 'snap help refresh'
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo canonical-livepatch enable
2019/06/14 17:01:13 error executing enable: No key provided.
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ sudo canonical-livepatch enable a8d88e04bea34da089e3c13a968f51f0
Successfully enabled device. Using machine-token: dfd64bc42cbb4424b8d919f449b11b68
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ canonical-livepatch --version
canonical-livepatch version 9.3.0
andres@andres-HP-Pavilion-Laptop-15-cd0xx:~$ 
```

STILL SHOWING ERROR
 
Here are some

---

### Post by PaulW2U on 2019-06-14
aoandes, the Livepatch service is only available to **Ubuntu** users but I note that you have posted in the 'Ubuntu/Debian Based' sub-forum.

Please confirm whether you are using Ubuntu or a derivative that uses the Ubuntu repositories. Your post may need to be moved to a more appropriate forum if you are actually using Ubuntu 18.04.

By the way, it would be very helpful if you could edit your post so that the terminal output is enclosed in [CODE] tags. They help to make such output easier to read.

---

