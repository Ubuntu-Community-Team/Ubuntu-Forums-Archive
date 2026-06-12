---
title: "Howto: Vector Linux No-CD Install using UNetbootin"
date: 2008-01-03
forum: Slackware and derivatives
---

### Post by tuxcantfly on 2008-01-03
Main Website At [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

**What This Does**

It's an installer for Windows or Linux users that lets you install Vector Linux without a CD. The way it works is that a small (6 MB) installer places the Vector Linux installer on your hard drive, and configures your boot loader, either NTLDR if using Windows, or GRUB if using Linux, to boot from the installer, which uses the packages from an iso file to install Vector Linux to your hard drive.

**Requirements**

You will need to either have a Windows (95-Vista) or Linux (any distro that uses GRUB) install already on your hard drive. You'll also need an internet connection. Apart from that, the requirements are the same as the standard VectorLinux requirements.

If you don't have an exisiting Windows/Linux install, it's also possible to run this from a LiveCD or install to a USB stick and boot from that instead; see the thread at [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540) for instructions

**Instructions**

First, you'll need to download the VectorLinux iso file. You'll want the standard version, NOT the liveCD edition. It can be downloaded from [http://ftp-osl.osuosl.org/pub/vectorlinux/veclinux-5.9/iso-release/VL5.9-STD-Gold.iso](http://ftp-osl.osuosl.org/pub/vectorlinux/veclinux-5.9/iso-release/VL5.9-STD-Gold.iso)

Next, make sure you have a spare partition to place the iso file into (it cannot be the one you aim to shrink during the install, nor the one you want to install Vector Linux into, since it is mounted during installation).

If you have a recovery partition,that'll do; just put the iso there (D:\ or wherever your recovery partition is, make sure it's the top-level directory), then proceed with the instructions.

Otherwise, you'll have to shrink an existing partition using the UNetbootin-PartedMagic Partition Manager and create a new one to store the iso file in, see [http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4) for details (download location is at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) )

Then download the appropriate installer package (UNetbootin VectorLinux) from [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

If using Windows, download the .exe file, if using Fedora or another rpm-based distro, download the .rpm file, if using Ubuntu or another deb-based distro, download the .deb file, and if using a distro that doesn't support rpm or deb, download the sh file.

Then, install the package, and reboot. Select the "Start and install" option, then proceed with the standard Arch install instructions.

**More**

UNetbootin also supports Ubuntu, openSUSE, Mandriva, Slackware, Arch Linux, CentOS, and Debian. Post a reply if you need any help, new features, or another supported distro. The website is located at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

