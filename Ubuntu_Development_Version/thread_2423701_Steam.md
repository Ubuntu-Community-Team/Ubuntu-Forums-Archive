---
title: "Steam"
date: 2019-07-27
forum: Ubuntu Development Version
---

### Post by P-I H on 2019-07-27
I tried to install steam-installer, but this didn't work. Got this error message
"steam-installer: Depends: steam (=1:1.0.0.54+repack-5ubuntu1) but it is not installable".
There is however another alternative
Enable support of flatpak and install the flathub version.
I installed CIV6 and Torchlite 2. To make them run you have to set the Launch Option **LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libfreetype.so.6 %command%**
I haven't played much, but the performance seem to be about the same as in a "normal" installation.

I checked with the AI benchmark in CIV6 and there is no difference compared to the installation with steam-installer.
During installation of the flathub version there is an error message about a missing package, but that don't doesn't impact the launch of Steam.

---

### Post by sevendogs1337 on 2019-07-27
How did you attempt to install Steam, using apt or Ubuntu software? I just installed steam yesterday, works perfectly. This is on an 18.04 LTS install.

---

### Post by #&amp;thj^% on 2019-07-27
> **sevendogs1337 said:**
> How did you attempt to install Steam, using apt or Ubuntu software? I just installed steam yesterday, works perfectly. This is on an 18.04 LTS install.

This is development release, not the same as LTS versions.
@P-I H this is not very encouraging but, [https://www.reddit.com/r/Steam/comments/c41zu4/steam_wont_support_ubuntu_1910_and_future_releases/](https://www.reddit.com/r/Steam/comments/c41zu4/steam_wont_support_ubuntu_1910_and_future_releases/)
Will have to wait and see how this pans out i guess.
[https://www.zdnet.com/article/valve-to-continue-steam-gaming-on-ubuntu-linux/](https://www.zdnet.com/article/valve-to-continue-steam-gaming-on-ubuntu-linux/)

---

### Post by P-I H on 2019-07-27
The first article is before Canonical announced to keep some 32-bit libs.
I installed the daily iso today and hoped that it should be possible to install Steam as usual by use of the steam-installer.
Actually I installed fedora 30 some weeks back to test with Steam and fedora, and it's not straight forward to install Steam in fedora either. To make CIV6 work you have to set a Launch Option in fedora too.
To install the flatpack version is quit OK. It's comparable to the installation by use of the steam-installer and performance seems to be OK.

---

### Post by cruzer001 on 2019-07-27
The gimp flatpack will complain of missing depends when being installed and I resolve this problem before first run by running:
```
sudo apt configure -a ;; sudo apt -f install
```
But you probably already tried that.

IMO, in the long run 32bit will be phased out but 32bit steam will be here for the next LTS release.  Here's a updated article.

[https://itsfoss.com/ubuntu-19-10-drops-32-bit-support/](https://itsfoss.com/ubuntu-19-10-drops-32-bit-support/)

---

