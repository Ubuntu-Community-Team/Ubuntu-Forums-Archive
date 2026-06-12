---
title: "apt-get update and automatic security repo switch"
date: 2020-01-28
forum: Security
---

### Post by t0p on 2020-01-28
I'm running lubuntu with some kali repos - sources.list attached.  I've been doing this for a couple of months, on another computer before this one.  The repos were added by Katoolin, a script that provides software from Kali Linux, tools for bug bounty hunting.  No problems until this morning: first I got an error saying that somehow an entry in sources.list was duplicated.  After I deleted the duplicate and tried to run apt-get update, I got this output:   
> 
t0p@pluto:~$ sudo apt update
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan InRelease
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates InRelease [97.5 kB]
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease [97.5 kB]   
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-backports InRelease [88.8 kB]   
Get:5 [http://ftp.hands.com/kali](http://ftp.hands.com/kali) kali-rolling InRelease [30.5 kB]            
Err:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates InRelease               
  Splitting up /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_eoan-updates_InRelease into data and signature failed
Get:6 [http://ftp.hands.com/kali](http://ftp.hands.com/kali) kali-rolling/main amd64 Packages [16.4 MB]  
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-backports/universe amd64 DEP-11 Metadata [7,744 B]
E: Repository 'http://security.ubuntu.com/ubuntu eoan-security InRelease' changed its 'Origin' value from 'Kali' to 'Ubuntu'
E: Repository 'http://security.ubuntu.com/ubuntu eoan-security InRelease' changed its 'Label' value from '' to 'Ubuntu'
N: Repository 'http://security.ubuntu.com/ubuntu eoan-security InRelease' changed its 'Version' value from '' to '19.10'
E: Repository 'http://security.ubuntu.com/ubuntu eoan-security InRelease' changed its 'Suite' value from 'kali-rolling' to 'eoan-security'
E: Repository 'http://security.ubuntu.com/ubuntu eoan-security InRelease' changed its 'Codename' value from 'kali-rolling' to 'eoan'
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.
Do you want to accept these changes and continue updating from this repository? [y/N] 


I don't know why I'm being asked this, and I don't know what the effect will be if I accept the changes or not.  Has anyone got any insight on this?

---

### Post by EuclideanCoffee on 2020-02-13
You have a few duplicates.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) eoan-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security multiverse

Simply add 'multiverse' to the previous eoan-updates and eoan-security.... actually, I think I see eoan-updates three times.

Try this and then do apt update.

---

### Post by deadflowr on 2020-02-14
The only duplicate is for kali
Here's a breakdown of the sources.list with all commented out lines removed:
```
deb http://archive.ubuntu.com/ubuntu/ eoan main restricted

deb http://archive.ubuntu.com/ubuntu/ eoan-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ eoan universe
deb http://archive.ubuntu.com/ubuntu/ eoan-updates universe

deb http://archive.ubuntu.com/ubuntu/ eoan multiverse
deb http://archive.ubuntu.com/ubuntu/ eoan-updates multiverse

deb http://security.ubuntu.com/ubuntu eoan-security main restricted
deb http://security.ubuntu.com/ubuntu eoan-security universe
deb http://security.ubuntu.com/ubuntu eoan-security multiverse

deb http://archive.ubuntu.com/ubuntu/ eoan-backports main restricted universe multiverse

deb http://http.kali.org/kali kali-rolling main contrib non-free

deb http://http.kali.org/kali kali-rolling main contrib non-free
```
(For those who don't wish to download a random file)

I think this really stems from the fact that the kali repos are meant to be added and discarded after you install whatever kali packages you are going to use.
Kali warns of this (sort of)
From [https://www.kali.org/docs/general-use/kali-linux-sources-list-repositories/]("https://www.kali.org/docs/general-use/kali-linux-sources-list-repositories/")
> Any additional repositories added to the Kali sources.list file will most likely BREAK YOUR KALI LINUX INSTALL.
I believe that works in reverse as well, so adding kali to another distros repo lists breaks the other system too.
Also katoolin warns to remove the kali repos before ever doing any system updating
From [https://github.com/LionSec/katoolin#warning]("https://github.com/LionSec/katoolin#warning")

A possible fix is to remove the lists files from /var/lib/apt/lists and disable the kali repos (as well as remove one of the duplicate entries.)
Once you remove the lists files they get regenerated when you run an apt update.

Unfortunately, I'm not sure what happens if by chance you have done an update with the repos enabled, but I don't think it can be good.

---

