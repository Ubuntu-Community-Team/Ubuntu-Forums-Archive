---
title: "New Ubuntu mini-iso file available"
date: 2023-04-13
forum: Ubuntu Development Version
---

### Post by sudodus on 2023-04-13
Have you noticed that there is **a new Ubuntu Mini iso-file** at

[cdimages.ubuntu.com/ubuntu-mini-iso/daily-live/current/](https://cdimages.ubuntu.com/ubuntu-mini-iso/daily-live/current/)

I noticed that the following shellscript can get/upgrade the file using zsync (notice that it uses http (not https),

```

#!/bin/bash

if [ $# -eq 1 ]
then
 zsync http://cdimages.ubuntu.com/ubuntu-mini-iso/daily-live/current/"${1%%-*}"-mini-iso-amd64.iso.zsync
else
 echo "Usage:   $0 <nickname>
Example: $0 lunar"
fi

```

When booting into the current daily Lunar file 2023-04-13,

- I noticed that it wants an internet connection

- the first real choice is between

Ubuntu Server 22.04.2 LTS
Ubuntu Server 22.10
Ubuntu Desktop 22.04.2 LTS
Ubuntu Desktop 22.10

so the iso file isnot yet upgraded to show 23.04.

- When trying to install Ubuntu Server, it complained that there was not enough RAM in my old Toshiba with 4GB, so this is not a suitable tool for older computers. It passed this hurdle in a Dell Latitude E7240 with 8 GB RAM.

- I did not want to install into the internal drive, but into an SSD connected via a USB adapter. This drive was recognized, but there was an error that stopped further installation (and I could not identify what caused this error).

So I would still recommend using a compressed image file. Let us hope that in the future this kind of mini iso file will be a good alternative.

Edit 1: - I tried in UEFI mode to install into the internal drive in the Latitude and the installation was complete. I could log into the Ubuntu Server and it seems to work. That's good, but I think it should also be able to install into an external SSD.

---

### Post by #&amp;thj^% on 2023-04-13
> **sudodus said:**
> Have you noticed that there is **a new Ubuntu Mini iso-file** at

[cdimages.ubuntu.com/ubuntu-mini-iso/daily-live/current/](https://cdimages.ubuntu.com/ubuntu-mini-iso/daily-live/current/)



Thanks sudodus, I see just arrived today, and already D-Loading it...;)

---

### Post by mIk3_08 on 2023-04-13
> **sudodus said:**
> Have you noticed that there is **a new Ubuntu Mini iso-file** at

[cdimages.ubuntu.com/ubuntu-mini-iso/daily-live/current/]("https://cdimages.ubuntu.com/ubuntu-mini-iso/daily-live/current/")

Thanks a lot sudodus for sharing and thanks for the Info thread. Regards and cheers

---

### Post by jbicha on 2023-04-13
Could you please start a new thread for the mini ISO? It's a very different topic than a bug that was fixed over 2 months ago!

---

### Post by Irihapeti on 2023-04-13
*Relevant posts moved to new thread.*

---

### Post by sudodus on 2023-04-14
I had asked the admins/moderators to move the post about the new mini-iso to another thread, but it was better to put it into a separate thread.

Thanks jbicha and Irihapeti :-)

---

### Post by jbicha on 2023-04-14
The only storage a live ISO has is RAM. So for Ubuntu 23.04, you need about 4.5 GB to store the Ubuntu Desktop ISO and at least 3GB to run that ISO. That comes out to about 8GB of RAM needed.

(Speaking about the non-mini ISO) I found that it was possible to install the Legacy Ubuntu Desktop 23.04 (using Ubiquity) with only 2GB of RAM but the new Ubuntu Desktop 23.04 (using Subiquity + Flutter as a snap) failed with 2GB but worked with 3GB. I would recommend 4GB though.

The new mini ISO is interesting. It is very different than how the old one worked (or the current Debian one). The new one basically just downloads the ISO for the release into RAM and then boots into that ISO. The old one downloaded individual .deb packages and installed them one by one.

Individually installing .deb files takes a long time; applying a disk image with .deb's preinstalled is much faster. The Ubiquity ISOs used that same disk image for the live environment and for the installed environment. At the end of the install, Ubiquity would then uninstall unneeded packages like support for additional languages and the installer itself.

Subiquity is the next generation. Instead of a single disk image, it has multiple images overlaid on each other. Each language is its own image. Therefore, the installer only needs to apply the images to the hard drive that it needs instead of uninstalling .debs. Ironically, Ubiquity was slower for installing the "minimal" option since it had to remove so many additional packages, but the new installer can just install "minimal" directly.

You can see the component disk images in either the old or new installers by looking inside the ISO (you can use Archive Manager) in the [FONT=courier new]casper[/FONT] folder. The images use the squashfs file format.

---

### Post by sudodus on 2023-04-14
@jbicha,

Please notice that 4 GB RAM is not enough to install *Ubuntu Server*.

I think this is too bad because some people want to

- use old computers as servers and/or
- create light-weight custom Ubuntu based systems via Ubuntu Server.

At this moment I would recommend getting the Ubuntu server via for example

- [ubuntu-22.04.2-live-server-amd64.iso.zsync](http://releases.ubuntu.com/jammy/ubuntu-22.04.2-live-server-amd64.iso.zsync)
or
- [jammy-preinstalled-server-amd64.img.xz.zsync](http://cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/jammy-preinstalled-server-amd64.img.xz.zsync)

---

### Post by jbicha on 2023-04-14
Right, if you already know that you want to install Ubuntu Server 22.04 LTS, it is much faster and more efficient to just use the Server ISO directly.

The mini ISO requires more RAM and a reasonable Internet connection.

---

