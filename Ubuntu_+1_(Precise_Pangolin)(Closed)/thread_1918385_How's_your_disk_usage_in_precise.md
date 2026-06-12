---
title: "How's your disk usage in precise?"
date: 2012-01-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2012-01-31
Here's mine at the moment:

```
paul@precise-64:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        39G  7.5G   30G  21% /
udev            994M   12K  994M   1% /dev
tmpfs          1002M  2.6M 1000M   1% /tmp
tmpfs           401M  344K  401M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M  384K 1002M   1% /run/shm
tmpfs          1002M     0 1002M   0% /var/tmp
paul@precise-64:~$ 
```

This is a minimal 64 bit install, derived (as far as I remember) during the natty dev cycle from a daily **mini.iso**.

Once I had the CLI-only system installed, I ran something like:
```
aptitude install --without-recommends xorg xserver-xorg-core \
xserver-input-all xserver-utils x11-xserver-utils \
xorg-input-all xserver-xorg-input-all lightdm lightdm-gtk-greeter \
gnome-session gnome-panel gnome-terminal gnome-themes \
gnome-themes-selected gnome-themes-ubuntu ubuntu-artwork \
light-themes
```

```
aptitude install --without-recommends synaptic \
flashplugin-downloader app-install-data gnome-applets gnome-panel-bonobo \
gvfs-backends indicator-applet-appmenu indicator-applet-complete \
indicator-application libasound-plugins libgtk2-perl libpam-ck-connector \
notification-daemon notify-osd nvidia-settings pulseaudio python-gconf \
software-properties-gtk python-software-properties gnome-keyring \
indicator-appmenu indicator-me indicator-messages indicator-session \
indicator-sound notify-osd-icons pulseaudio-esound-compat \
pulseaudio-module-x11 appmenu-gtk indicator-applet-session \
libpam-gnome-keyring python-indicate
```

I added the a couple of things after that like gnome-shell and nvidia-current (can't see those in the initial commands above!) and obviously some packages end up being renamed or superseded, but that was the gist of it

I remove unneeded kernels and run bleachbit periodically, trim the logs with a simplistic script and try to remember to run:

```
sudo aptitude purge $(deborphan)
```

if I remove or purge packages.

Current kernels:

```
paul@precise-64:~$ ls -la /boot/vml*
-rw------- 1 root root 4950800 Jan 26 05:37 /boot/vmlinuz-3.2.0-11-generic
-rw------- 1 root root 4943920 Jan 31 22:40 /boot/vmlinuz-3.2.0-12-generic
-rw------- 1 root root 4906736 Jan 26 01:43 /boot/vmlinuz-3.2.2-030202-generic
-rw------- 1 root root 4951664 Jan 31 22:43 /boot/vmlinuz-3.3.0-030300rc2-generic
paul@precise-64:~$
```

---

### Post by cariboo on 2012-01-31
I just ran:

```
sudo apt get clean
```

my disk usage now looks like this:

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       9.3G  4.8G  4.1G  54% /
udev            994M   12K  994M   1% /dev
tmpfs           401M  1.1M  400M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M  776K 1001M   1% /run/shm
/dev/sda6       161G   81G   72G  53% /home
```

This is a full install upgraded from Oneiric, when the tool chain was uploaded.

---

### Post by sammiev on 2012-01-31
Here's mine.

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       272G   12G  246G   5% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           752M  976K  751M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G   96K  1.9G   1% /run/shm

```

---

### Post by Hreinsi on 2012-01-31
+

---

### Post by VMC on 2012-02-01
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda8        15G  3.0G   11G  22% /
udev            1.8G  4.0K  1.8G   1% /dev
tmpfs           741M  804K  740M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  208K  1.9G   1% /run/shm

```

---

