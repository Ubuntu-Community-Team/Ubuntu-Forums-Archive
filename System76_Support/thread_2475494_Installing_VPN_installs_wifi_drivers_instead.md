---
title: "Installing VPN installs wifi drivers instead"
date: 2022-05-29
forum: System76 Support
---

### Post by defenestrator-go-yeet on 2022-05-29
I recently upgraded to the most recent version of Pop!_OS. Somehow downloading the update got rid of my install of NordVPN. I tried to reinstall it but all the files, except the .config file, were gone. Did a fresh download of the installer, but whenever I try to set it up my system tries to update my wifi adapter drivers, crashes, and then doesn't get to the VPN. Any ideas?

Terminal below; the rtl8812au-dkms package are my wifi adapter drivers.
```

user@pop-os:~$ sh <(wget -qO - https://downloads.nordcdn.com/apps/linux/install.sh)
/usr/bin/apt-get
[sudo] password for user: 
Hit:1 http://us.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu jammy-security InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:4 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease 
Hit:5 http://apt.pop-os.org/proprietary jammy InRelease             
Hit:6 http://apt.pop-os.org/release jammy InRelease
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
apt-transport-https is already the newest version (2.4.5).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu15) ...
Removing old rtl8812au-4.3.8.12175.20140902+dfsg DKMS files...
Deleting module rtl8812au-4.3.8.12175.20140902+dfsg completely from the DKMS tree.
Loading new rtl8812au-4.3.8.12175.20140902+dfsg DKMS files...
Building for 5.17.5-76051705-generic
Building initial module for 5.17.5-76051705-generic
ERROR (dkms apport): kernel package linux-headers-5.17.5-76051705-generic is not supported
Error! Bad return status for module build on kernel: 5.17.5-76051705-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/make.log for more information.
dpkg: error processing package rtl8812au-dkms (--configure):
 installed rtl8812au-dkms package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 rtl8812au-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by #&amp;thj^% on 2022-05-29
Can you show this please:
```
apt policy rtl8812*

apt policy rtl8812au-dkms

```

---

### Post by defenestrator-go-yeet on 2022-05-29
Both return the same.

```

apt policy rtl8812au-dkms
rtl8812au-dkms:
  Installed: 4.3.8.12175.20140902+dfsg-0ubuntu15
  Candidate: 4.3.8.12175.20140902+dfsg-0ubuntu15
  Version table:
 *** 4.3.8.12175.20140902+dfsg-0ubuntu15 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe i386 Packages
        100 /var/lib/dpkg/status

```

---

