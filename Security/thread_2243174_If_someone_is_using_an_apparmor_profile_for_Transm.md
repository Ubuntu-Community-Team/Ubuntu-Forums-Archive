---
title: "If someone is using an apparmor profile for Transmission-gtk please share"
date: 2014-09-06
forum: Security
---

### Post by linuxyogi on 2014-09-06
Hi,

I have tried a lot in the past but apparmor is something I just cant learn.

I just want an apparmor profile for Transmission-gtk. I seached a lot but can't find any.

I want to restict Transmission to only those places of the filesystem without which it

cannot function and other than that to ~/Downloads. 

Some years back I was trying to create a apparmor profile for FF but couldnt do it and 

finally bodhi.zazen completed the profile. 

^^ When applied Firefox could not even read the other files or folders in my home. It 

could only read  and write to ~/Downloads and its own profile.

^^ This is what I want to implement.

I dont know why nobody has created a ppa for atleast the LTS.

---

### Post by vasa1 on 2014-09-07
[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1293525](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1293525)

---

### Post by uRock on 2014-09-07
It'd be nice to see it as being in the defaults in the future. Thanks for linking the bug report.

---

### Post by linuxyogi on 2014-09-07
I am in trouble now. Actually some wierd things happened in the past few days. 

1) My Internet banking account password got changed. I had to reset it.

2) The system was runnig really slow sometimes.

3) The most distrubing thing, I found that I coundn't modify /etc/resolv.conf as root. I went to an IRC channel they gave thelsatter command which showed that the file had an "i" flag.

I am not completely sure if the system was reall hacked but if it was then I see tw possible causes. The first can be running standalone Tor outside a chroot and the second 

and most probable cause I guess is torrenting coz I had done port forwarding.

I hardly used Tor so installing it was a mistake. If there's an apparmor profile for any other torrent client I will use that client. I hope its not Ktorrent coz its really bloated.

The next best is Qbittorrent.

---

### Post by uRock on 2014-09-07
If you think your system got cracked, then it may be time for a reinstall.

---

### Post by linuxyogi on 2014-09-07
> **uRock said:**
> If you think your system got cracked, then it may be time for a reinstall.

Done that and thats why dont want to take any more risks. No random PPAs, only those mainted by devs of the app themselves.

---

### Post by linuxyogi on 2014-09-07
Profile found. It was given to me when I was using 12.04 but the profile was created on 14.04 beta. Forgot to enforce after upgrading to 14.04.

[old thread]("http://ubuntuforums.org/showthread.php?t=2211444&p=12959708#post12959708")


> **Lars Noodén said:**
> Here's what I got for Ubuntu 14.04 beta.  It probably works for 12.04.

```

#include <tunables/global>

/usr/bin/transmission-gtk {
  #include <abstractions/base>
  #include <abstractions/gnome>
  #include <abstractions/lightdm>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  network inet stream,
  network inet6 stream,

  owner /.Trash-*/ w,

  owner @{HOME}/.Xauthority r,
  owner @{HOME}/.cache/transmission/ w,
  owner @{HOME}/.cache/transmission/** rw,
  owner @{HOME}/.config/dconf/user r,
  owner @{HOME}/.config/gtk-3.0/bookmarks r,
  owner @{HOME}/.config/transmission/ w,
  owner @{HOME}/.config/transmission/** rw,
  owner @{HOME}/.config/user-dirs.dirs r,
  owner @{HOME}/.local/share/Trash/files/* w,
  owner @{HOME}/.local/share/Trash/info/* rw,
  owner @{HOME}/.local/share/applications/ r,
  owner @{HOME}/.local/share/applications/mimeapps.list r,
  owner @{HOME}/.local/share/applications/mimeinfo.cache r,
  owner @{HOME}/.local/share/gvfs-metadata/home r,
  owner @{HOME}/.local/share/gvfs-metadata/home-*.log r,
  owner @{HOME}/.local/share/gvfs-metadata/root r,
  owner @{HOME}/.local/share/gvfs-metadata/root-*.log r,
  owner @{HOME}/.local/share/mime/mime.cache r,
  owner @{HOME}/.local/share/recently-used.xbel rw,
  owner @{HOME}/.local/share/recently-used.xbel.* rw,
  owner @{HOME}/Downloads/** r, 
  owner @{HOME}/Downloads/** rw,

  @{PROC}/*/fd/ r,
  @{PROC}/*/mountinfo r,
  @{PROC}/[0-9]*/net/dev r,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/wireless r,
  @{PROC}/net/ipv6_route r,
  @{PROC}/net/route r,
  @{PROC}/sys/kernel/random/uuid r,

}

```



---

