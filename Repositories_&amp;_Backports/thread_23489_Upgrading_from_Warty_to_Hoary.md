---
title: "Upgrading from Warty to Hoary"
date: 2005-04-02
forum: Repositories &amp; Backports
---

### Post by deviant03 on 2005-04-02
I changed everything thats Warty to Hoary in sources and did the upgrade. Some packages installed but now everytime I open Synaptic it keeps saying I have 22 packages held back. I have tried again:

from Synaptic: both default and smart upgrade
apt-get upgrade, apt-get dist-upgrade

but I still cant get the rest of the packages installed. Any help would be appreciated. Heres my sources list:

# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

# deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe 

#deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-backports main universe multiverse restricted 
#deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras main universe multiverse restricted

---

### Post by ubuntu_demon on 2005-04-02
first read these sites :
[http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)
[http://www.ubuntulinux.org/wiki/GuideToHoary](http://www.ubuntulinux.org/wiki/GuideToHoary)

do this :

sudo apt-get update
sudo apt-get install ubuntu-base ubuntu-desktop -f
sudo apt-get install xserver-xorg -f (this most likely won't be necessary but won't hurt)
sudo apt-get dist-upgrade
sudo dpkg-reconfigure locales

and if your xserserver-xorg doesn't work (you can't login graphically) do this :
sudo dpkg-reconfigure xserver-xorg

---

### Post by deviant03 on 2005-04-02
ubuntu-base is already the newest version.
Package ubuntu-desktop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-desktop has no installation candidate

---

### Post by ubuntu_demon on 2005-04-02
[QUOTE=deviant03]ubuntu-base is already the newest version.
Package ubuntu-desktop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-desktop has no installation candidate[/QUOTE]
 Don't forget to read this thread :
[http://www.ubuntuforums.org/showthread.php?t=12174](http://www.ubuntuforums.org/showthread.php?t=12174)

Because you have to first remove all installed warty-backports.

Also your sources.list is not correct. 

this lines should be kept commented because hoary isn't released yet :

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

If you had read [http://www.ubuntulinux.org/wiki/GuideToHoary](http://www.ubuntulinux.org/wiki/GuideToHoary)
you would know that you have to replace your sources.list with theirs (and adding marillat if you use that).

After this do once again what I just said  :

sudo apt-get update
sudo apt-get install ubuntu-base ubuntu-desktop -f
sudo apt-get install xserver-xorg -f (this most likely won't be necessary but won't hurt)
sudo apt-get dist-upgrade
sudo dpkg-reconfigure locales

and if your xserserver-xorg doesn't work (you can't login graphically) do this :
sudo dpkg-reconfigure xserver-xorg

---

### Post by deviant03 on 2005-04-02
I googled and everywhere I looked said to just change in my sources list all instances of Warty to Hoary, I did read the GuideToHoary but didnt use that specific list. The only  thing I can see wrong comparing the two lists is mines has:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 

but the right way should be:

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse

Everything is updating now, thanks for your help demon666_nl  8)

---

### Post by ubuntu_demon on 2005-04-02
[QUOTE=deviant03]I googled and everywhere I looked said to just change in my sources list all instances of Warty to Hoary, I did read the GuideToHoary but didnt use that specific list. The only  thing I can see wrong comparing the two lists is mines has:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 

but the right way should be:

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse

Everything is updating now, thanks for your help demon666_nl  8)[/QUOTE]
 np :)

easiest if you use that specific list just to be sure you don't overlook something.

---

