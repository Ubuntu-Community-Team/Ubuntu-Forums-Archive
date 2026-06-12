---
title: "Grub Breaks with Updates From Mays .iso"
date: 2017-05-28
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2017-05-28
Woot Breakage :D...Installing Image dated 5-24-17 latest .iso, UbuntuGnome.
Running first update and upgrade ran into this:
```
Errors were encountered while processing:
 grub-common
 grub-pc-bin
 grub-pc
 grub2-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Tried the normal -f install...now it gets fun:
```
May 28 17:51:57 me-750-417c systemd[1]: Starting LSB: Record successful boot&#8230;...
May 28 17:56:58 me-750-417c systemd[1]: grub-common.service: Start operation&#8230;ng.
May 28 17:56:58 me-750-417c systemd[1]: Failed to start LSB: Record successf&#8230;UB.
May 28 17:56:58 me-750-417c systemd[1]: grub-common.service: Unit entered fa&#8230;te.
May 28 17:56:58 me-750-417c systemd[1]: grub-common.service: Failed with res&#8230;t'.
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package grub-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of grub-pc-bin:
 grub-pc-bin depends on grub-common (= 2.02~beta3-4ubuntu4); however:
  Package grub-common is not configured yet.

```
Humm? :confused: New to me...so being the Wild Man I am, started to think nuclear. :D
```
sudo mv /var/lib/dpkg/info/grub-pc.postinst /var/lib/dpkg/info/grub-pc.postinst-bad
sudo apt-get -f install

```
Yikes :o....went like:

```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-common (2.02~beta3-4ubuntu4) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults

Job for grub-common.service failed because a timeout was exceeded.
See "systemctl  status grub-common.service" and "journalctl  -xe" for details.
invoke-rc.d: initscript grub-common, action "start" failed.
&#9679; grub-common.service - LSB: Record successful boot for GRUB
   Loaded: loaded (/etc/init.d/grub-common; generated; vendor preset: enabled)
   Active: failed (Result: timeout) since Sun 2017-05-28 17:56:58 MDT; 12ms ago
     Docs: man:systemd-sysv-generator(8)
  Process: 11704 ExecStart=/etc/init.d/grub-common start (code=killed, signal=TERM)
    Tasks: 5 (limit: 4915)
   CGroup: /system.slice/grub-common.service
           &#9500;&#9472; 3841 plymouth --ping
           &#9500;&#9472;10891 plymouth --ping
           &#9500;&#9472;11335 plymouth --ping
           &#9492;&#9472;11708 plymouth --ping

May 28 17:51:57 me-750-417c systemd[1]: Starting LSB: Record successful boot&#8230;...
May 28 17:56:58 me-750-417c systemd[1]: grub-common.service: Start operation&#8230;ng.
May 28 17:56:58 me-750-417c systemd[1]: Failed to start LSB: Record successf&#8230;UB.
May 28 17:56:58 me-750-417c systemd[1]: grub-common.service: Unit entered fa&#8230;te.
May 28 17:56:58 me-750-417c systemd[1]: grub-common.service: Failed with res&#8230;t'.
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package grub-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of grub-pc-bin:
 grub-pc-bin depends on grub-common (= 2.02~beta3-4ubuntu4); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub-pc-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common (= 2.02~beta3-4ubuntu4); however:
  Package grub-common is not configured yet.
 grub-pc depends on grub-pc-bin (= 2.02~beta3-4ubuntu4); however:
  Package grub-pc-bin is not configured yet.

dpkg: error processing package grub-pc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.02~beta3-4ubuntu4); however:
  Package grub-common is not configured yet.

dpkg: error processing paNo apport report written because the error message indicates its a followup error from a previous failure.
                                                   No apport report written because the error message indicates its a followup error from a previous failure.
                                                                             No apport report written because MaxReports is reached already
                                                           ckage grub2-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-common
 grub-pc-bin
 grub-pc
 grub2-common
E: Sub-process /usr/bin/dpkg returned an error code (1) 

```
I sat there with pure confusion all over me.
Well what the heck fresh install no worries, Right? ;)
Well I'm not bulit that way, i just have to solve this problem no matter what.
So I rebooted...in this condtion:
```
sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-pc-bin grub2-common
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 4,174 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 131175 files and directories currently installed.)
Removing grub-pc-bin (2.02~beta3-4ubuntu4) ...
Removing grub2-common (2.02~beta3-4ubuntu4) ...
Processing triggers for install-info (6.3.0.dfsg.1-1) ...
Processing triggers for man-db (2.7.6.1-2) ...

```

Well I got into my system Luckily...and the rest went like this:
```

$ apt policy grub-pc
grub-pc:
  Installed: (none)
  Candidate: 2.02~beta3-4ubuntu4
  Version table:
     2.02~beta3-4ubuntu4 500
        500 http://us.archive.ubuntu.com/ubuntu artful/main amd64 Packages
        100 /var/lib/dpkg/status
me@me-750-417c:~$ sudo update-grub
sudo: update-grub: command not found

```
And again ran:
```
 sudo apt upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  grub-pc-bin grub2-common
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  libtasn1-6
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 35.5 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://us.archive.ubuntu.com/ubuntu artful/main amd64 libtasn1-6 amd64 4.10-1.1 [35.5 kB]
Fetched 35.5 kB in 0s (49.8 kB/s)     
(Reading database ... 131176 files and directories currently installed.)
Preparing to unpack .../libtasn1-6_4.10-1.1_amd64.deb ...
Unpacking libtasn1-6:amd64 (4.10-1.1) over (4.10-1) ...
Setting up libtasn1-6:amd64 (4.10-1.1) ...
Processing triggers for libc-bin (2.24-9ubuntu2) ...
Setting up grub-common (2.02~beta3-4ubuntu4) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up grub-pc-bin (2.02~beta3-4ubuntu4) ...
Setting up grub2-common (2.02~beta3-4ubuntu4) ...
Setting up os-prober (1.74ubuntu1) ...
W: APT had planned for dpkg to do more than it reported back (14 vs 18).
   Affected packages: grub-common:amd64

```
Now here we are:
```
sudo apt install grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-common is already the newest version (2.02~beta3-4ubuntu4).
The following additional packages will be installed:
  grub-gfxpayload-lists grub-pc-bin grub2-common
Suggested packages:
  desktop-base
The following NEW packages will be installed:
  grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,622 kB of archives.
After this operation, 4,771 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://us.archive.ubuntu.com/ubuntu artful/main amd64 grub2-common amd64 2.02~beta3-4ubuntu4 [528 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu artful/main amd64 grub-pc-bin amd64 2.02~beta3-4ubuntu4 [897 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu artful/main amd64 grub-gfxpayload-lists amd64 0.7 [3,658 B]
Get:4 http://us.archive.ubuntu.com/ubuntu artful/main amd64 grub-pc amd64 2.02~beta3-4ubuntu4 [192 kB]
Fetched 1,622 kB in 1s (884 kB/s)
Preconfiguring packages ...
Selecting previously unselected package grub2-common.
(Reading database ... 130859 files and directories currently installed.)
Preparing to unpack .../grub2-common_2.02~beta3-4ubuntu4_amd64.deb ...
Unpacking grub2-common (2.02~beta3-4ubuntu4) ...
Selecting previously unselected package grub-pc-bin.
Preparing to unpack .../grub-pc-bin_2.02~beta3-4ubuntu4_amd64.deb ...
Unpacking grub-pc-bin (2.02~beta3-4ubuntu4) ...
Selecting previously unselected package grub-gfxpayload-lists.
Preparing to unpack .../grub-gfxpayload-lists_0.7_amd64.deb ...
Unpacking grub-gfxpayload-lists (0.7) ...
Preparing to unpack .../grub-pc_2.02~beta3-4ubuntu4_amd64.deb ...
Unpacking grub-pc (2.02~beta3-4ubuntu4) ...
Setting up grub-pc-bin (2.02~beta3-4ubuntu4) ...
Processing triggers for install-info (6.3.0.dfsg.1-1) ...
Setting up grub2-common (2.02~beta3-4ubuntu4) ...
Processing triggers for man-db (2.7.6.1-2) ...
Setting up grub-gfxpayload-lists (0.7) ...
Setting up grub-pc (2.02~beta3-4ubuntu4) ...

Creating config file /etc/default/grub with new version
Installing for i386-pc platform.
Installation finished. No error reported.
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.10.0-21-generic
Found initrd image: /boot/initrd.img-4.10.0-21-generic
Found Ubuntu 16.04.2 LTS (16.04) on /dev/sda1
done
```
I love it when a plan comes together.:KS
Whoosh Back in business.
Hope this helps someone else.
Cheers

---

