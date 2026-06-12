---
title: "Cant Instal gksu / gparted"
date: 2014-11-04
forum: Server Platforms
---

### Post by iDeals on 2014-11-04
I get the following when I try to install gparted using ```
sudo apt-get install gparted
```

> Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gparted : Depends: libatkmm-1.6-1 (>= 2.22.1) but it is not going to be installed
           Depends: libglibmm-2.4-1c2a (>= 2.30.0) but it is not going to be installed
           Depends: libgtk2.0-0 (>= 2.14.0) but it is not going to be installed
           Depends: libgtkmm-2.4-1c2a (>= 1:2.24.0) but it is not going to be installed
           Depends: libpangomm-1.4-1 (>= 2.27.1) but it is not going to be installed
 linux-server : Depends: linux-headers-server (= 3.2.0.44.53) but 3.2.0.70.84 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

and this when I try to install gksu using: ```
sudo apt-get install gksu
```

> Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gksu : Depends: libgksu2-0 (>= 2.0.8) but it is not going to be installed
        Depends: libgtk2.0-0 (>= 2.8.0) but it is not going to be installed
        Recommends: gnome-keyring but it is not going to be installed
 linux-server : Depends: linux-headers-server (= 3.2.0.44.53) but 3.2.0.70.84 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I tried running apt-get -f install as it suggest to no avail. Any ideas?

---

### Post by Bashing-om on 2014-11-04
iDeals; Humm .....

Are you running an End-Of-Life release ?
as:
> 
You have searched for packages that names contain libgtk in suite(s) precise-updates, all sections, and all architectures. Found 14 matching packages.
Package libgtk-[color=green]3-0[/color]

And searches on " libatkmm" and "libglibmm" have no returns.

indicate no support in that release.

[INDENT][INDENT]past time to move on up ?
[/INDENT][/INDENT]

---

### Post by iDeals on 2014-11-04
quite likely I'm on 12.04.... and still a newbie to Ubuntu. Have no idea how to update OS especially with a mounted RAID array

---

### Post by ian-weisser on 2014-11-05
> **iDeals said:**
> ```
Reading package lists... Done
linux-server : Depends: linux-headers-server (= 3.2.0.44.53) but 3.2.0.70.84 is to be installed
```

Let's see what version of Ubuntu you are running:
```
$ rmadison -u ubuntu linux-headers-server | grep precise
 linux-headers-server | 3.2.0.23.25  | precise          | amd64, i386
 linux-headers-server | 3.2.0.70.84  | precise-security | amd64, i386
 linux-headers-server | 3.2.0.70.84  | precise-updates  | amd64, i386
```

So you are running 12.04 (precise-updates), 3.2.0.70.84 .
But, sometime in the past, you installed software that demands 3.2.0.44.53 .
That's the problem. You seem to have a package conflict.

You must uninstall whatever software requires the old versions. Usually a PPA or other non-Ubuntu software.
Then do an autoremove to eliminate any non-Ubuntu dependencies.
Then disable or delete that repository.
(Optional) Then install the Ubuntu version of the software to prevent it from happening again.


Do you remember what you installed that might be the culprit? It's much faster to fix if you do. Did you install anything where you needed to look up instructions on some website? Or enter unfamiliar commands into the terminal? Or download a .deb file from someplace?

Look through your software Sources to see which non-Ubuntu repositories you have added. That may help spur your memory.

---

### Post by iDeals on 2014-11-05
::sigh::

is there a way to search dependencies to see what it is that is demanding 3.2.0.44.53?  I have no idea what may be causing the conflict since I havent done really any installing of anything since I originally set up the system some years ago.  Softwares I am running:

webmin
mdadm
sabnzbd
sickbeard
couchpotato

---

### Post by Bucky Ball on 2014-11-05
Perhaps run through an update/upgrade routine and post any and all errors. Might give some clues:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Any errors? Anything noticeable? Perhaps reboot if no issues. 

No problem with the release. 12.04 is supported until April 2017. ;)

---

### Post by ian-weisser on 2014-11-05
> **iDeals said:**
> The following packages have unmet dependencies:
 gksu : Depends: libgksu2-0 (>= 2.0.8) but it is not going to be installed
        Depends: libgtk2.0-0 (>= 2.8.0) but it is not going to be installed
        Recommends: gnome-keyring but it is not going to be installed
 linux-server : Depends: linux-headers-server (= 3.2.0.44.53) but 3.2.0.70.84 is to be installed

is there a way to search dependencies to see what it is that is demanding 3.2.0.44.53?


Sort of. Poke some of those is-not-going-to-be-installed packages and find exact reasons why. Example:

```
sudo apt-get install libgtk2.0-0
```

---

### Post by gordintoronto on 2014-11-06
The packages you are trying to install require a graphical user interface. Do you have one installed on top of Ubuntu Server?

---

