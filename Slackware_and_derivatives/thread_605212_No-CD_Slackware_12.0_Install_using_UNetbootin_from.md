---
title: "No-CD Slackware 12.0 Install using UNetbootin from Windows"
date: 2007-11-06
forum: Slackware and derivatives
---

### Post by tuxcantfly on 2007-11-06
**Main Site is at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)**

First, if you haven't yet prepared/shrunk your partitions, download the appropriate Partition Manager package at [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240127](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240127) for your OS (exe for Windows, deb for Ubuntu/Debian, rpm for Fedora/Suse, sh for other Linux distros), install the package, reboot, and start GParted. More detailed instructions are available at [http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4)

Then, unless you plan on doing an NFS install, recursively download (wget -r or a similar approach) the contents of the following directory, or its equivalent on your slackware mirror:
[ftp://ftp.slackware.com/pub/slackware/slackware-12.0/slackware](ftp://ftp.slackware.com/pub/slackware/slackware-12.0/slackware)
To a directory on your hard drive, like C:\slackware. Make sure the directory you download to isn't on the same partition that ou plan to use for slackware.

Then, download the appropriate UNetbootin Slackware installer for your OS at [http://sourceforge.net/project/showfiles.php?group_id=19882](http://sourceforge.net/project/showfiles.php?group_id=19882) and reboot, then select the "UNetbootin" option to start the Slackware installer.

First, login as "root"
If you're using NFS or some other network-based install, then, when the prompt shows up, type in "network" and press enter at the next prompt to set up networking.
Then, create your new partitions using "cfdisk" or "fdisk" unless you've already done so in GParted, in which case you can skip this step.
Then, type in "setup" to begin the actual installation process.
When you get to "source", select the "Install from hard drive partition" option, enter the hard drive it's on, then type in /slackware when asked for the directory.
Then, select your packages and proceed with the standard install approach.

Also, UNetbootin supports installing a variety of other distros as well, such as Fedora, Ubuntu, openSUSE, Mandriva, Arch Linux, and Debian; instructions for those are at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

Also note that I posted this thread at the Slackware Forums at [http://slackwarehelp.org/viewtopic.php?p=6427](http://slackwarehelp.org/viewtopic.php?p=6427) and the main Ubuntu UNetbootin thread is at [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)

---

