---
title: "How To Set the XFCE Panel Back To Orginal Settings"
date: 2016-10-26
forum: Ubuntu/Debian BASED
---

### Post by UltimateCat on 2016-10-26
I'm running Voyager which was Ubuntu 14.04. VLC and other programs and things became unstable so  I upgraded to Ubuntu 16.04.
The Upgrade took about 4 hours.

```
cat /etc/os-release
NAME="Ubuntu"
VERSION="16.04.1 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.1 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
UBUNTU_CODENAME=xenial

```

The Terminal Emulator used to be in my Panel among, Back Up, Synapse, The American Flag and other Icons.
After playing with the settings in the XFCE Panel Switch somehow I choose the wrong thing didn't know I should of saved the configuration and now all the Icons that were there are gone.

Here's what the Panel looked like before I made a mess with the XFCE Panel Swich:
[http://i1052.photobucket.com/albums/s447/Ultimatecat/Voyager%20Panel.png](http://i1052.photobucket.com/albums/s447/Ultimatecat/Voyager%20Panel.png)

I tried right clicking on the Panel> Add new item but Terminal Emulator isn't in the list and using the search bar it doesn't come up.
I tried XFCE Terminal as well in the Search and no dice.

How do I get the configuration that I had back?

---

### Post by vasa1 on 2016-10-27
> **UltimateCat said:**
> I'm running Voyager which was Ubuntu 14.04. VLC and other programs and things became unstable so  I upgraded to Ubuntu 16.04.
...
So you upgraded Voyager to Ubuntu?

---

### Post by Bucky Ball on 2016-10-27
> **vasa1 said:**
> So you upgraded Voyager to Ubuntu?

Judging by this signature:

[QUOTE=UltimateCat]-:- Slackware & Voyager Xubuntu 16.04 -:-[/QUOTE]

I'd say OP is using Voyager 16.04. Not sure why 'Voyager Xubuntu'. It's either Voyager, which is based on Xubuntu, or Xubuntu. There isn't a 'Voyager Xubuntu 16.04'. :-k

@UltimateCat: As vasa1 has requested. Please confirm the OS you are currently using and that you want support with.

---

### Post by alexjpowell on 2016-10-27
Hi
Try logging into another GUI or boot into the command line.

Remove XFCE then install it again:
sudo apt-get -f install
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get purge xfce4
sudo apt-get purge  '~n^libxfce4.*' '~n^libexo.*' '~n^libgarcon.*'

Before running the above, please make sure that you understand what it is doing.
sudo apt-get install xfce4

---

### Post by vasa1 on 2016-10-27
Duplicate here: [https://ubuntuforums.org/showthread.php?t=2341380](https://ubuntuforums.org/showthread.php?t=2341380)

Please don't make duplicate threads even if they are in different subforums.

Please be clear about the distro you are using. Ubuntu-based isn't the same as Ubuntu.

---

