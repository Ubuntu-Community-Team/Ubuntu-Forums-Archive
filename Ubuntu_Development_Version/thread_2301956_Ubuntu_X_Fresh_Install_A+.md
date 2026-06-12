---
title: "Ubuntu X Fresh Install: A+"
date: 2015-11-06
forum: Ubuntu Development Version
---

### Post by MikeMecanic on 2015-11-06
Just made a fresh install of Ubuntu 16.04 November 5th build.  It seems to be possible now to install Xenial a long side Windows but I scratch the previous installation (10586 buggy release).  Choose LVM instead that is for me the best way to clean the HDD.  

Took me 5 minutes to install Xenial and was not ask to removed the media at the end.  Because I loaded the Xenial installer directlly in the boot sequence (Lexar) it didn't restart a second installation.  This bug was there in my last fresh install of Wily when I pass by the BIOS.

Push Ubuntu Software Center into full saturation: 5 apps at the same time.  Got only one bug: Google Chrome was not shown in the dash board, had to restart to see it or open it.  Bugs of the pass (first installation) are now part of history with Opera stable 33.


Version:    33.0.1990.58 - Opera is up to date
Update stream:    Stable
System:    Ubuntu 16.04 (x86_64; Unity)


Trying to import profile into GUFW gave a not 600 error.  This bug if it's one is there since Wily.  Got the solution that way:

```
xenial@hp:~$ sudo chmod 600 /home/xenial/Desktop/firewall17.profile
[sudo] password for xenial: 
xenial@hp:~$ uname -r
4.2.0-16-generic
xenial@hp:~$ grub-install --version
grub-install (GRUB) 2.02~beta2-29
xenial@hp:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial
xenial@hp:~$ exit

```

My global appreciation of this new installer is positive:  Everything seems to run faster.


A+

---

### Post by MikeMecanic on 2015-11-06
Enable Proposed and there was about 200 files hided:

```
xenial@hp:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Xenial Xerus (development branch)
Release:	16.04
Codename:	xenial
xenial@hp:~$ grub-install --version
grub-install (GRUB) 2.02~beta2-31
xenial@hp:~$ uname -r
4.2.0-17-generic
xenial@hp:~$ tty
/dev/pts/2
xenial@hp:~$ sudo last
[sudo] password for xenial: 
xenial   :0           :0               Fri Nov  6 17:54    gone - no logout
reboot   system boot  4.2.0-17-generic Fri Nov  6 17:53   still running
xenial   :0           :0               Fri Nov  6 17:31 - crash  (00:22)
reboot   system boot  4.2.0-16-generic Fri Nov  6 17:31   still running
xenial   :0           :0               Fri Nov  6 11:59 - down   (01:20)
reboot   system boot  4.2.0-16-generic Fri Nov  6 11:59 - 13:19  (01:20)
xenial   :0           :0               Fri Nov  6 11:45 - down   (00:13)
reboot   system boot  4.2.0-16-generic Fri Nov  6 11:45 - 11:58  (00:13)
xenial   :0           :0               Fri Nov  6 11:32 - crash  (00:12)
reboot   system boot  4.2.0-16-generic Fri Nov  6 11:32 - 11:58  (00:26)


wtmp begins Fri Nov  6 11:32:35 2015
xenial@hp:~$ bash --version
GNU bash, version 4.3.42(1)-release (x86_64-pc-linux-gnu)
Copyright (C) 2013 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>


This is free software; you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
xenial@hp:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME                  FSTYPE        SIZE MOUNTPOINT LABEL
sda                               698.7G            
&#9500;&#9472;sda1                ext2          243M /boot      
&#9500;&#9472;sda2                                1K            
&#9492;&#9472;sda5                LVM2_member 698.4G            
  &#9500;&#9472;ubuntu--vg-root   ext4        694.5G /          
  &#9492;&#9472;ubuntu--vg-swap_1 swap          3.9G [SWAP]     
sr0                                1024M            
xenial@hp:~$ 

```

---

