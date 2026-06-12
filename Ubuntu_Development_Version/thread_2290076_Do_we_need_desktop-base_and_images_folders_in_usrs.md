---
title: "Do we need desktop-base and images folders in /usr/share?"
date: 2015-08-09
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-08-09
Do we really need the desktop-base and images folders in /usr/share, the contents of which are not needed at all for Ubuntu based distros? In /etc/alternatives, the desktop-background etc are pointing to non-Ubuntu files. Shouldn't Ubuntu-based distros should come without these apps/folders? This is about Wily and the future releases.

---

### Post by grahammechanical on 2015-08-09
The /etc/alternatives/ that you mentioned may be a Debian thing.

[https://wiki.debian.org/DebianAlternatives](https://wiki.debian.org/DebianAlternatives)

[http://manpages.ubuntu.com/manpages/hardy/man8/update-alternatives.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/update-alternatives.8.html)

Regards.


[URL="https://wiki.debian.org/DebianAlternatives"]

[/URL]

---

### Post by Chanath on 2015-08-09
I noticed this /usr/share/desktop-base folder quite a long time ago (maybe in precise) and I always purge it, which also uninstall the /usr/share/images folder, and those links in /etc/alternatives directing to those two folders. Ubuntu keeps its wallpapers in /usr/share/backgrounds, not in the the /usr/share/images folder. I think these folders are just leftovers from Debian, just like those in the /usr/share/python-apt/templates.

---

### Post by harry332 on 2015-08-09
The package desktop-base is in universe, not in main, so it does not belong to an original Ubuntu installation (Unity desktop).

---

### Post by grahammechanical on 2015-08-09
I have installed on my system (Unity) some Grub2 background images. I use the Software Centre and those images were downloaded to /usr/share/grub/ So it seems that there is some usefulness to /usr/share/images folder.

Regards.

---

### Post by mc4man on 2015-08-09
> **Chanath said:**
> I noticed this /usr/share/desktop-base folder quite a long time ago (maybe in precise) and I always purge it, which also uninstall the /usr/share/images folder, and those links in /etc/alternatives directing to those two folders. Ubuntu keeps its wallpapers in /usr/share/backgrounds, not in the the /usr/share/images folder. I think these folders are just leftovers from Debian, just like those in the /usr/share/python-apt/templates.
Don't know what you're installing but those folders do not exist here in any Ubuntu install from 14.04 > 15.10

---

### Post by dino99 on 2015-08-09
i also checked my install after reading that thread, and found desktop-base also installed: its a 'suggested' package for some ubu packages, so i suppose it has been 'recommended' then set to 'suggested' on some rolling flavours (indeed i've purged it as it makes no sense to get it installed)

---

### Post by Bashing-om on 2015-08-09
et all;

I recon the paths are inplace to augment the installation of different DEs ??
On this box I run xfce and the files are required:
```

sysop@1404mini:~$ ls -al /usr/share/desktop-base
total 24
drwxr-xr-x   3 root root 4096 May 19  2013 .
drwxr-xr-x 154 root root 4096 Jun 20 14:55 ..
-rw-r--r--   1 root root  208 Nov 13  2012 debian-homepage.desktop
-rw-r--r--   1 root root  242 Nov 13  2012 debian-reference.desktop
-rw-r--r--   1 root root  197 Nov 13  2012 debian-security.desktop
drwxr-xr-x   4 root root 4096 May 19  2013 profiles
sysop@1404mini:~$

bk

sysop@1404mini:~$ ls -al /usr/share/desktop-base/profiles/xdg-config/xfce4/xfconf/xfce-perchannel-xml
total 16
drwxr-xr-x 2 root root 4096 May 19  2013 .
drwxr-xr-x 3 root root 4096 May 19  2013 ..
-rw-r--r-- 1 root root 1252 Nov 13  2012 xfce4-desktop.xml
-rw-r--r-- 1 root root  622 Nov 13  2012 xfce4-session.xml
sysop@1404mini:~$

```
Not to say there is no harm in removing those 'debian-' files. As likely there will be no value in them for a ubuntu install .

[INDENT][INDENT]complexities of a multi-function system
[/INDENT][/INDENT]

---

### Post by mc4man on 2015-08-09
lightdm-gtk-greeter & xfce4 still have it as a recommend, may be others? (likely most of below have as suggests
> ~$ apt-cache rdepends desktop-base
desktop-base
Reverse Depends:
  lightdm-gtk-greeter
  gnome-session-flashback
  grub-pc-bin
  grub-common
  gnome-session
  xfce4
  wmaker
  sabily-grub-artwork
  lightdm-gtk-greeter
  gnome-session-flashback
  gnome
  libgnome2-common
  grub-pc-bin
  grub-common
  gnome-session

---

### Post by Chanath on 2015-08-09
These folders were there in aby Ubuntu flavor and some links in /etc/alternatives are directed to these 2 folders. Che&#263;k your installation, whether it is trusty or wily. And those links are not needed in ang Ubuntu flavor.

---

### Post by cariboo on 2015-08-09
> **Chanath said:**
> These folders were there in aby Ubuntu flavor and some links in /etc/alternatives are directed to these 2 folders. Che&#263;k your installation, whether it is trusty or wily. And those links are not needed in ang Ubuntu flavor.

They aren't added, my Utopic->Vivid->Wily install doesn't have the directories, as mc4man stated.

---

### Post by mc4man on 2015-08-09
> **Chanath said:**
> These folders were there in aby Ubuntu flavor and some links in /etc/alternatives are directed to these 2 folders. Che&#263;k your installation, whether it is trusty or wily. And those links are not needed in ang Ubuntu flavor.
Ubuntu - [not included]("http://cdimage.ubuntu.com/daily-live/current/wily-desktop-amd64.manifest")
Ubuntu Gnome - [not included]("http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/pending/wily-desktop-amd64.manifest")
Kubuntu - [not included]("http://cdimage.ubuntu.com/kubuntu/daily-live/current/wily-desktop-amd64.manifest")
Lubuntu - [not included]("http://cdimage.ubuntu.com/lubuntu/daily-live/current/wily-desktop-amd64.manifest")
Xubuntu - [included]("http://cdimage.ubuntu.com/xubuntu/daily-live/20150808/wily-desktop-amd64.manifest")
Ubuntu Studio - [URL="http://cdimage.ubuntu.com/ubuntustudio/dvd/pending/wily-dvd-amd64.manifest"]included
[/URL]
(provided by [desktop-base package]("http://packages.ubuntu.com/wily/desktop-base/filelist")

---

### Post by Chanath on 2015-08-10
> **mc4man said:**
> Ubuntu - [not included]("http://cdimage.ubuntu.com/daily-live/current/wily-desktop-amd64.manifest")
Ubuntu Gnome - [not included]("http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/pending/wily-desktop-amd64.manifest")
Kubuntu - [not included]("http://cdimage.ubuntu.com/kubuntu/daily-live/current/wily-desktop-amd64.manifest")
Lubuntu - [not included]("http://cdimage.ubuntu.com/lubuntu/daily-live/current/wily-desktop-amd64.manifest")
Xubuntu - [included]("http://cdimage.ubuntu.com/xubuntu/daily-live/20150808/wily-desktop-amd64.manifest")
Ubuntu Studio - [URL="http://cdimage.ubuntu.com/ubuntustudio/dvd/pending/wily-dvd-amd64.manifest"]included
[/URL]
(provided by [desktop-base package]("http://packages.ubuntu.com/wily/desktop-base/filelist")
Thanks mc4man. Now I know I was right by uninstalling those folders.

---

### Post by sgage on 2015-08-10
> **mc4man said:**
> Don't know what you're installing but those folders do not exist here in any Ubuntu install from 14.04 > 15.10

They're not installed on my Ubuntu Gnome 15.10 either.

---

