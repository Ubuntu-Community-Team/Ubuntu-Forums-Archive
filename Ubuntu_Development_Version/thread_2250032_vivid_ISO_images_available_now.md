---
title: "vivid ISO images available now"
date: 2014-10-26
forum: Ubuntu Development Version
---

### Post by rrnbtter on 2014-10-26
Greetings,
[http://www.cdimage.ubuntu.com/daily-live/20141026/vivid-desktop-i386.iso](http://www.cdimage.ubuntu.com/daily-live/20141026/vivid-desktop-i386.iso)

[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/20141026/vivid-desktop-i386.iso](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/20141026/vivid-desktop-i386.iso)

I zsynced over my Utopic images and only had to download around 20%. 

Going to test the Desktop Next ISO this morning if I get a chance.

---

### Post by fooman on 2014-10-26
[URL="http://www.cdimage.ubuntu.com/daily-live/20141026/"]http://www.cdimage.ubuntu.com/daily-live/20141026/


[/URL]

---

### Post by fooman on 2014-10-26
downloaded 64bit version, loaded onto usb drive.  installed ubuntu onto 250gb samsung ssd.  ran updates, installed nvidia drivers, gnome shell and ubuntu-restricted-extras....all went perfectly smooth,  no issues at all! 

  ```
lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid
3.16.0-23-generic
```

```
Current Date/Time: Sun Oct 26 13:17:59 EDT 2014
Distro Release: Ubuntu Vivid Vervet (development branch)
Kernel Release: Linux 3.16.0-23-generic
Gnome Release: GNOME Shell 3.12.2
Unity Release: unity 7.3.1

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.2.0 NVIDIA 304.123
```

---

### Post by sammiev on 2014-10-26
I can confirm that the 64bit AMD ISO clean install works fine.

---

### Post by rrnbtter on 2014-10-26
Greetings,
I can verify that the Desktop-Next ISO installs. I didn't spend much time with it however.

---

### Post by jerrylamos on 2014-10-26
Installed Vivid from daily .iso.

Synaptic settings repositories crashed.

For that matter, 
sudo software-properties-gtk
crashed.

Also, System Settings > Software & Updates won't start.

Launchpad bug [https://bugs.launchpad.net/bugs/1386017](https://bugs.launchpad.net/bugs/1386017)

---

### Post by cecilpierce on 2014-10-26
Crashed with mine to until I edited out Extra in /etc/apt/sources.list.

---

### Post by fooman on 2014-10-26
> **jerrylamos said:**
> Installed Vivid from daily .iso.

Synaptic settings repositories crashed.

For that matter, 
sudo software-properties-gtk
crashed.

Also, System Settings > Software & Updates won't start.

Launchpad bug [https://bugs.launchpad.net/bugs/1386017](https://bugs.launchpad.net/bugs/1386017)

to fix this issue...do as Ventrical suggests in op of this thread:

[http://ubuntuforums.org/showthread.php?t=2249736](http://ubuntuforums.org/showthread.php?t=2249736)

also here:

[https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work](https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work)

---

