---
title: "plymouth-themes going in loop-plugin ubuntu-gnome-text.so is missing"
date: 2015-12-10
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-12-10
I have an install of ubuntu-gnome with proposed open. I was reading up on another bug and then seemed to get a new one.

```

update-initramfs: Generating /boot/initrd.img-4.3.0-2-generic
W: plymouth: The plugin ubuntu-gnome-text.so is missing, the selected theme might not work as expected.
W: plymouth: You might want to install the plymouth-themes package to fix this.
ventrical@ventrical-MS-7850:~$ sudo apt-get install plymouth-themes
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpoppler56 libvte-2.90-9 libvte-2.90-common linux-headers-4.2.0-16
  linux-headers-4.2.0-16-generic linux-headers-4.2.0-19
  linux-headers-4.2.0-19-generic linux-image-4.2.0-16-generic
  linux-image-4.2.0-19-generic linux-image-extra-4.2.0-16-generic
  linux-image-extra-4.2.0-19-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  plymouth-themes
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 650 kB of archives.
After this operation, 969 kB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 plymouth-themes amd64 0.9.2-3ubuntu3 [650 kB]
Fetched 650 kB in 1s (371 kB/s)          
Selecting previously unselected package plymouth-themes.
(Reading database ... 252917 files and directories currently installed.)
Preparing to unpack .../plymouth-themes_0.9.2-3ubuntu3_amd64.deb ...
Unpacking plymouth-themes (0.9.2-3ubuntu3) ...
Setting up plymouth-themes (0.9.2-3ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.120ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-4.3.0-2-generic
W: plymouth: The plugin ubuntu-gnome-text.so is missing, the selected theme might not work as expected.
W: plymouth: You might want to install the plymouth-themes package to fix this.
ventrical@ventrical-MS-7850:~$ 

```

regards..

---

### Post by flocculant on 2015-12-10
There were some rather massive changes to plymouth recently. I did check Ubuntu and Lubuntu after I saw an issue with Xubuntu. Don't do gnome though. Someone is looking at xubuntu tomorrow(ish).

What happens with a gnome daily? does it boot? They'll not be very interested in a install with -proposed obviously. 

If you get chance to look at a daily I'll pass that along.

---

### Post by flocculant on 2015-12-10
actually - just run into that on an install and upgrade of a daily in a vm


[lpbug]1524937[/lpbug]

---

### Post by ventrical on 2015-12-10
+1

Confirmed.

thanks

Regards..

---

### Post by ventrical on 2015-12-10
Changed to [all variants].

---

### Post by ventrical on 2015-12-10
Here is the other part.. (from xubuntu install)

```

Setting up plymouth-theme-ubuntu-text (0.9.2-3ubuntu3) ...
update-alternatives: warning: alternative /lib/plymouth/themes/ubuntu-text/ubuntu-text.plymouth (part of link group text.plymouth) doesn't exist; removing from list of alternatives
update-alternatives: warning: alternative /lib/plymouth/themes/xubuntu-text/xubuntu-text.plymouth (part of link group text.plymouth) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/text.plymouth is dangling; it will be updated with best choice
update-alternatives: renaming text.plymouth link from /lib/plymouth/themes/text.plymouth to /usr/share/plymouth/themes/text.plymouth
update-alternatives: using /usr/share/plymouth/themes/ubuntu-text/ubuntu-text.plymouth to provide /usr/share/plymouth/themes/text.plymouth (text.plymouth) in auto mode
update-initramfs: deferring update (trigger activated)
Setting up libpython3.5:amd64 (3.5.1-1) ...
Setting up plymouth-theme-xubuntu-logo (15.12.1) ...
update-alternatives: warning: alternative /lib/plymouth/themes/ubuntu-logo/ubuntu-logo-scale-2.plymouth (part of link group default.plymouth) doesn't exist; removing from list of alternatives
update-alternatives: warning: alternative /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth (part of link group default.plymouth) doesn't exist; removing from list of alternatives
update-alternatives: warning: alternative /lib/plymouth/themes/xubuntu-logo/xubuntu-logo.plymouth (part of link group default.plymouth) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/default.plymouth is dangling; it will be updated with best choice
update-alternatives: renaming default.plymouth link from /lib/plymouth/themes/default.plymouth to /usr/share/plymouth/themes/default.plymouth
update-alternatives: using /usr/share/plymouth/themes/xubuntu-logo/xubuntu-logo.plymouth to provide /usr/share/plymouth/themes/default.plymouth (default.plymouth) in auto mode
update-initramfs: deferring update (trigger activated)
Setting up libwayland-egl1-mesa:amd64 (11.0.7-1ubuntu1) ...
Setting up g++-4.9 (4.9.3-9ubuntu1) ...
Setting up qtdeclarative5-localstorage-plugin:amd64 (5.5.1-2ubuntu2) ...
Setting up g++-5 (5.3.1-3ubuntu1) ...
Setting up plymouth-theme-xubuntu-text (15.12.1) ...
update-alternatives: using /usr/share/plymouth/themes/xubuntu-text/xubuntu-text.plymouth to provide /usr/share/plymouth/themes/text.plymouth (text.plymouth) in auto mode
update-initramfs: deferring update (trigger activated)
Setting up plymouth-theme-ubuntu-logo (0.9.2-3ubuntu3) ...
update-initramfs: deferring update (trigger activated)

```

---

### Post by anca-emanuel on 2015-12-11
Not exactly all versions. For me is working (Ubuntu default, unity 7)
Didier just posted an new version: [https://lists.ubuntu.com/archives/xenial-changes/2015-December/003024.html](https://lists.ubuntu.com/archives/xenial-changes/2015-December/003024.html)

---

### Post by valereguerin on 2015-12-15
+1

Confirmed.

thanks

Regards...first install with unity-desktop crash de gdm/lightdm i don't know i install ubuntu gnome desktop, gdm3, ... reboot and.....Nice !  Great JOB TEAM !

Xénial Xérus ubuntu-gnome-desktop 4.3.0-2-generic 64 Bits gdm3 full-upgrade google-earth steam thunar eiciel blender pitivi audacious tor ....marvellous !\\:D/

---

