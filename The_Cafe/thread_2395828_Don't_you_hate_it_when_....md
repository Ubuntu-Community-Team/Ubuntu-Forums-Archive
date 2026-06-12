---
title: "Don't you hate it when ..."
date: 2018-07-07
forum: The Cafe
---

### Post by PaulW2U on 2018-07-07
You're having a good day.
The sun is shining.
You're helping fellow users on the forums.
They're thanking you.
You're thinking how well Ubuntu is working for you.

And then ....

To clear some unwanted files from a directory tree you execute a variation of that command which contains the characters **r**, **m**, **f**, **-** and **/**. You know the one that the forum staff will reprimand you for posting.

And then ...

You realise that you are not in the directory that you thought you were.
All your files have gone.
So you re-install but it doesn't go well so you reinstall again.
And then you realise that all of your settings and customisations are gone.
So you restore important files and settings from a backup.
You try so hard to think what applications you need to install and what PPAs and shell extensions to add but you can't think of anything. Nothing at all.
Then your dual monitor set up doesn't work the way that it should.
You have thoughts about abandoning Ubuntu and buying an iPad or going back to Windows.

And then ...

It all comes together and you realise that you can put back what you foolishly destroyed but it'll just take a little time

Yeah, today I've been there. I've done that. I'm now proudly wearing a tee shirt that says "I am almost a Bionic Beaver". :D

---

### Post by #&amp;thj^% on 2018-07-07
> **PaulW2U said:**
> You're having a good day.
The sun is shining.
You're helping fellow users on the forums.
They're thanking you.
You're thinking how well Ubuntu is working for you.

And then ....

To clear some unwanted files from a directory tree you execute a variation of that command which contains the characters **r**, **m**, **f**, **-** and **/**. You know the one that the forum staff will reprimand you for posting.

And then ...

You realise that you are not in the directory that you thought you were.
All your files have gone.
So you re-install but it doesn't go well so you reinstall again.
And then you realise that all of your settings and customisations are gone.
So you restore important files and settings from a backup.
You try so hard to think what applications you need to install and what PPAs and shell extensions to add but you can't think of anything. Nothing at all.
Then your dual monitor set up doesn't work the way that it should.
You have thoughts about abandoning Ubuntu and buying an iPad or going back to Windows.

And then ...

It all comes together and you realise that you can put back what you foolishly destroyed but it'll just take a little time

Yeah, today I've been there. I've done that. I'm now proudly wearing a tee shirt that says "I am almost a Bionic Beaver". :D

This puts a smile on my face PaulW2U, I too have done this foolishly not paying attention to my current directory when running the command or even having two terminals open and picking the wrong terminal. :(
So I now see I'm in good company "proudly wearing a tee shirt that says "I am almost a Bionic Beaver". 
But I haved learned from this over the years>>> Back Up, Back Up, Back Up. And can quickly fix my errant way.
Thanks for the post. ;)
Kind Regards

---

### Post by PaulW2U on 2018-07-07
> **1fallen said:**
> But I haved learned from this over the years>>> Back Up, Back Up, Back Up. And can quickly fix my errant way.
I'm certainly back to where I can be in record time but I'm sticking with 18.04 for a while before reverting to the development version which was left intact after I destroyed Ubuntu 18.04. I installed 18.04 from the today's daily build to reduce the number of updates that needed to be downloaded since the initial release.

Interestingly, I found a **proposed.list** file in **/etc/apt/sources.list.d**. synaptic shows that I have 96 packages which are local or obsolete. Enabling proposed shows just one package could be upgraded. I recall seeing something on IRC about -proposed being enabled for (new) installs but I can't remember for what reason. As I can't face another re-install today I'm hoping that those proposed packages are stable and will migrate to their intended destination before the release of 18.04.1 on 26th July.

Just when you think you've got it fixed....

---

### Post by #&amp;thj^% on 2018-07-07
If it makes you feel any better I always have proposed enabled from Development to release:
```
 apt list --installed | grep proposed

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

bluez/bionic-proposed,now 5.48-0ubuntu3.1 amd64 [installed]
bluez-cups/bionic-proposed,now 5.48-0ubuntu3.1 amd64 [installed]
bluez-obexd/bionic-proposed,now 5.48-0ubuntu3.1 amd64 [installed]
gir1.2-gnomedesktop-3.0/bionic-proposed,now 3.28.2-0ubuntu1 amd64 [installed,automatic]
gir1.2-packagekitglib-1.0/bionic-proposed,now 1.1.9-1ubuntu2.18.04.1 amd64 [installed]
gir1.2-snapd-1/bionic-proposed,now 1.41-0ubuntu0.18.04.1 amd64 [installed]
gnome-desktop3-data/bionic-proposed,bionic-proposed,now 3.28.2-0ubuntu1 all [installed]
grub-common/bionic-proposed,now 2.02-2ubuntu8.1 amd64 [installed]
grub-emu/bionic-proposed,now 2.02-2ubuntu8.1 amd64 [installed]
grub-pc/bionic-proposed,now 2.02-2ubuntu8.1 amd64 [installed]
grub-pc-bin/bionic-proposed,now 2.02-2ubuntu8.1 amd64 [installed]
grub2-common/bionic-proposed,now 2.02-2ubuntu8.1 amd64 [installed]
initramfs-tools/bionic-proposed,bionic-proposed,now 0.130ubuntu3.2 all [installed]
initramfs-tools-bin/bionic-proposed,now 0.130ubuntu3.2 amd64 [installed]
initramfs-tools-core/bionic-proposed,bionic-proposed,now 0.130ubuntu3.2 all [installed]
intel-microcode/bionic-proposed,now 3.20180425.1~ubuntu0.18.04.2 amd64 [installed]
libbluetooth3/bionic-proposed,now 5.48-0ubuntu3.1 amd64 [installed]
libegl-mesa0/bionic-proposed,now 18.0.5-0ubuntu0~18.04.1 amd64 [installed]
libegl1/bionic-proposed,now 1.0.0-2ubuntu2.1 amd64 [installed]
libegl1-mesa/bionic-proposed,now 18.0.5-0ubuntu0~18.04.1 amd64 [installed]
libgbm1/bionic-proposed,now 18.0.5-0ubuntu0~18.04.1 amd64 [installed]
libgl1/bionic-proposed,now 1.0.0-2ubuntu2.1 amd64 [installed]
libgl1-mesa-dri/bionic-proposed,now 18.0.5-0ubuntu0~18.04.1 amd64 [installed]
libgl1-mesa-glx/bionic-proposed,now 18.0.5-0ubuntu0~18.04.1 amd64 [installed]
libglapi-mesa/bionic-proposed,now 18.0.5-0ubuntu0~18.04.1 amd64 [installed]
libgles2/bionic-proposed,now 1.0.0-2ubuntu2.1 amd64 [installed,automatic]
libglvnd0/bionic-proposed,now 1.0.0-2ubuntu2.1 amd64 [installed]
libglx-mesa0/bionic-proposed,now 18.0.5-0ubuntu0~18.04.1 amd64 [installed]
libglx0/bionic-proposed,now 1.0.0-2ubuntu2.1 amd64 [installed]
libgnome-desktop-3-17/bionic-proposed,now 3.28.2-0ubuntu1 amd64 [installed]
libnss-systemd/bionic-proposed,now 237-3ubuntu10.2 amd64 [installed]
libpackagekit-glib2-18/bionic-proposed,now 1.1.9-1ubuntu2.18.04.1 amd64 [installed]
libpam-systemd/bionic-proposed,now 237-3ubuntu10.2 amd64 [installed]
libpython3-stdlib/bionic-proposed,now 3.6.5-3ubuntu1 amd64 [installed]
libsnapd-glib1/bionic-proposed,now 1.41-0ubuntu0.18.04.1 amd64 [installed]
libsystemd0/bionic-proposed,now 237-3ubuntu10.2 amd64 [installed]
libudev1/bionic-proposed,now 237-3ubuntu10.2 amd64 [installed]
libwayland-egl1-mesa/bionic-proposed,now 18.0.5-0ubuntu0~18.04.1 amd64 [installed]
libxatracker2/bionic-proposed,now 18.0.5-0ubuntu0~18.04.1 amd64 [installed]
linux-headers-4.15.0-26/bionic-proposed,bionic-proposed,now 4.15.0-26.28 all [installed,automatic]
linux-headers-4.15.0-26-generic/bionic-proposed,now 4.15.0-26.28 amd64 [installed,automatic]
linux-headers-generic/bionic-proposed,now 4.15.0.26.28 amd64 [installed,automatic]
linux-libc-dev/bionic-proposed,now 4.15.0-26.28 amd64 [installed,automatic]
mesa-va-drivers/bionic-proposed,now 18.0.5-0ubuntu0~18.04.1 amd64 [installed]
mesa-vdpau-drivers/bionic-proposed,now 18.0.5-0ubuntu0~18.04.1 amd64 [installed]
packagekit/bionic-proposed,now 1.1.9-1ubuntu2.18.04.1 amd64 [installed]
packagekit-tools/bionic-proposed,now 1.1.9-1ubuntu2.18.04.1 amd64 [installed]
python3/bionic-proposed,now 3.6.5-3ubuntu1 amd64 [installed]
python3-minimal/bionic-proposed,now 3.6.5-3ubuntu1 amd64 [installed]
python3-update-manager/bionic-proposed,bionic-proposed,now 1:18.04.11.3 all [installed]
systemd/bionic-proposed,now 237-3ubuntu10.2 amd64 [installed]
systemd-sysv/bionic-proposed,now 237-3ubuntu10.2 amd64 [installed]
udev/bionic-proposed,now 237-3ubuntu10.2 amd64 [installed]
unattended-upgrades/bionic-proposed,bionic-proposed,now 1.1ubuntu1.18.04.1 all [installed]
update-manager/bionic-proposed,bionic-proposed,now 1:18.04.11.3 all [installed]
update-manager-core/bionic-proposed,bionic-proposed,now 1:18.04.11.3 all [installed]
update-notifier/bionic-proposed,now 3.192.1.3 amd64 [installed]
update-notifier-common/bionic-proposed,bionic-proposed,now 3.192.1.3 all [installed]

```
There is a way to revert from proposed if you wish to do so, but probally not here in the Cafe.

---

### Post by PaulW2U on 2018-07-08
> **1fallen said:**
> There is a way to revert from proposed if you wish to do so, but probally not here in the Cafe.
Thanks for the offer 1fallen but it's all academic now. I had to do a second reinstall as both 18.04 and my development installation suddenly stopped booting. :confused:

Anyway, I'm back with just a little customisation left to do. Two lessons learned:

[LIST]
[*]Do even more backups than I already do
[*]Be extra careful when using terminal commands that delete files
[/LIST]
If the heat doesn't finish me off then I'm sure my computer will. ;)

---

