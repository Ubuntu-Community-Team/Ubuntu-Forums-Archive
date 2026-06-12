---
title: "How to rebuild Ubuntu live ISO files with debroot"
date: 2016-07-08
forum: Tutorials
---

### Post by ruibernardo on 2016-07-08
Debroot ([https://sourceforge.net/projects/debroot/](https://sourceforge.net/projects/debroot/)) is a tool that can create and build debian and ubuntu live isos. It can also rebuild (unsquash, update, upgrade and squash again) a live iso with customizations and with a custom uefi support. Here is an example of its usage with Ubuntu and it's flavours and derivatives.

[INDENT]* Grab the latest version of debroot and install (from [https://github.com/rbern/debroot](https://github.com/rbern/debroot) or [https://sourceforge.net/projects/debroot/](https://sourceforge.net/projects/debroot/)). There are prebuilt debian packages available at [https://sourceforge.net/projects/debroot/:](https://sourceforge.net/projects/debroot/:)

```
sudo gdebi -o "APT::Install-Recommends=0" debroot_0.06_all.deb -nq
```

* Download the desired Ubuntu Live iso from [http://www.ubuntu.com/download](http://www.ubuntu.com/download) or [http://www.ubuntu.com/download/ubuntu-flavours:](http://www.ubuntu.com/download/ubuntu-flavours:)

* start debroot:

```
sudo debroot.pl
```

[IMG]https://a.fsdn.com/con/app/proj/debroot/screenshots/debroot.png[/IMG]

* Type in the "ROOTFS directory" the name of a new directory where the ISO chroot content will be extracted;

* Select the** first tab "Unsquash ISO"** and select the downloaded ISO;

* Press the button "Unsquash ISO" and wait;

[/INDENT]

Now you have the content of the ISO extrated to a directory XXXXX-binary, being XXXXX what you typed in "ROOTFS directory". You have the content of the squashed filesystem in the "ROOTFS directory".

Now we will update the apt repositories in the chroot and then rebuild the ISO with UEFI support. The "apt-get update" is needed so that apt can find the needed packages.
[INDENT]* Click on the **"sources.list/upgrade" tab** and then click the button "Update". Done;

* If you want to add packages to the live ISO (customize) you can now click on the tab "Install" and add packagenames to install and then click the button "Install";

* If you need to execute any command to complete the customization in the chroot click the tab "Chroot" and then run a shell in the chroot;

* If you have installed or upgraded packages then you need to clear the downloaded packages from apt cache to make the live ISO a bit smaller. The commands to be executed in the shell to do this are:
```

apt-get autoremove --purge
apt-get clean
exit

```
* Now all is ready to rebuild the ISO. Click on the** "Build" tab **and then on the "Refresh options" button;

[IMG]https://a.fsdn.com/con/app/proj/debroot/screenshots/debroot2.png[/IMG]
[/INDENT]


NOTE: after the whole process is done you will have a script called XXXXX-builds-script.sh with all the commands that were execcuted. In theory one could repeat the whole process from that script without the need to install debroot.

After the build was completed you can test if the Live ISO boots in UEFI mode in qemu/ovmf or in Virtualbox (with EFI boot).

For qemu/ovmf UEFI testing run:

```
qemu-system-x86_64 -bios /usr/share/ovmf/OVMF.fd -cdrom XXXXX.iso  -m 1024
```

To install from the Live ISO with debian-installer/live-installer, take note of what are the installer options present in XXXXX-binary/isolinux/install.cfg (or live.cfg) file and then, on UEFI boot, in GRUB, edit the options and type the installer boot options. Then press F10 to boot the installer.

Cheers!

---

### Post by ruibernardo on 2016-07-18
Hi all,

just to say that debroot is now in version 0.08. Since I've posted this tutorial serveral bug fixes were fixed and now the app supports debian live iso with installer. Besides this all is working in Ubuntu since version 0.07.

The thread for debroot in debian at debianforums.net: "How to rebuild a debian 7/8/testing live isos with UEFI" [http://forums.debian.net/viewtopic.php?f=16&t=128995](http://forums.debian.net/viewtopic.php?f=16&t=128995)

In that thread I ask for help to test a "rebuilt" and customized debian 8.5 jessie live with installer and UEFI in a Virtual Machine that has an UEFI OS already installed to confirm that a debian live iso with uefi can be installed along other UEFI OS in the same disk.

Please post doubts and problems. Thanks for any feedback.

Cheers.

---

### Post by sudodus on 2016-07-18
Your debroot tool looks very interesting :-)

Unfortunately I have not enough time right now to plunge deeply into new development tasks. But if/when I have the time, I think debroot would/will be worth trying.

---

### Post by Habitual on 2016-07-18
> **sudodus said:**
> Your debroot tool looks very interesting :-)

Unfortunately I have not enough time right now to plunge deeply into new development tasks. But if/when I have the time, I think debroot would/will be worth trying.
What ^ said.
It does look like a "Keeper".

I know a guy who knows a guy who "builds", so I sent him this link.

---

