---
title: "DELL PowerEdge R410 doesn't boot with Linux 3.2.0-48"
date: 2013-07-02
forum: Server Platforms
---

### Post by jofa on 2013-07-02
We have a production server running **Ubuntu Server 12.04.2** on a **Dell Inc. PowerEdge R410/01V648, BIOS 1.8.2 08/19/2011**. It has **Asterisk 1.8 PBX** installed from the standard repositories and connecting calls via a **Digium, Inc. Wildcard TE121 single-span T1/E1/J1 card (PCI-Express) (rev 11)**. After doing the latest [FONT=monospace]dist-upgrade[/FONT] (to install packages that was held back) the server doesn't boot. After a while of black screen it quickly prints something that looks like a stack trace, and then gets stuck in a loop printing something like [FONT=monospace]udevd[XXX]: timeout: killing '/sbin/modprobe -bv pci:XXXXXXXXXXXXX...[/FONT] over and over, forever.

I'm unable to switch VT and I can't get the "Magic SysRq key" combo working. Had to hard reset the computer. Booting the previously installed kernel (3.2.0-39) manually works and that's how it's running right now. I have searched [FONT=monospace]/var/log/[/FONT] for any useful info, but I'm lost. 

[LIST=1]
[*]Where should I start fixing this? 
[*]How could this have been prevented, e.g. should I not do [FONT=monospace]dist-upgrade[/FONT] on production servers?
[/LIST]

---

### Post by newbie-user on 2013-07-02
It would be best to test dist-upgrades on a test server before doing it on a production server. If the newer kernel doesn't fix a problem you're currently having, then it's probably better to run the older kernel, unless the newer kernel has some security fixes.

---

### Post by SeijiSensei on 2013-07-02
The (n-1)th kernel should still be in /boot and there should be an entry for it in /boot/grub/grub.cfg.  You can force grub to boot a different kernel than the default by changing the entry in "set default".  The proper way to do this is to edit /etc/default/grub and set GRUB_DEFAULT=1, then reboot.  It should automatically select the (n-1)th kernel.

If you have a hardware RAID card, that might be the cause of the problem.  Perhaps the proper driver for the card isn't being loaded.  On the R410 I've worked with (running CentOS 6.2), an lsmod brings up:

```

mptsas                 53746  3 
mptscsih               36828  1 mptsas
mptbase                94037  2 mptsas,mptscsih
scsi_transport_sas     35940  1 mptsas

```

If you boot into recovery mode with the new kernel and drop to a root shell, do you see those entries if you run lsmod?

I never upgrade kernels unless they have a major security flaw that needs immediate fixing.  RedHat/CentOS still run the 2.6.32 kernel with backported upgrades as necessary!

---

### Post by tgalati4 on 2013-07-02
I would research the differences between the 0-48 and 0-39 kernels (hint:  read the changelog for 0-48) and see if anything looks relevant.  File a bug against the 0-48 kernel if a true regression is found--that is something that was working is now no longer working.  It looks like a device driver for hardware connected to the pci bus got tripped up.  Try removing all hardware from the PCI bus and see if the server boots, then add hardware back one at a time.

You have turned your production server into a test server.  I think you have answered the second question.

---

### Post by jofa on 2013-07-03
> **newbie-user said:**
> It would be best to test dist-upgrades on a test server before doing it on a production server. …

I assume we would have to get another server with the exactly the same hardware for this to work? We have another server with a Digium card installed that's planned to act as a redundancy for the production server, but it's not the same DELL model, nor the same card.

> **SeijiSensei said:**
> The (n-1)th kernel should still be in /boot and there should be an entry for it in /boot/grub/grub.cfg.  You can force grub to boot a different kernel than the default by changing the entry in "set default".  The proper way to do this is to edit /etc/default/grub and set GRUB_DEFAULT=1, then reboot.  It should automatically select the (n-1)th kernel.

I'll try this ASAP! Would it be a good idea to also test *dist-upgrade* when a newer kernel emerges and increment GRUB_DEFAULT until I've found another kernel that works? Otherwise, wouldn't it just be easier to uninstall the problematic kernel version and stick with the old one?

> **SeijiSensei said:**
> If you have a hardware RAID card, that might be the cause of the problem.  Perhaps the proper driver for the card isn't being loaded.  On the R410 I've worked with (running CentOS 6.2), an lsmod brings up:

```

mptsas                 53746  3 
mptscsih               36828  1 mptsas
mptbase                94037  2 mptsas,mptscsih
scsi_transport_sas     35940  1 mptsas

```

If you boot into recovery mode with the new kernel and drop to a root shell, do you see those entries if you run lsmod? …

I'll try this tonight outside open hours (swedish time). It seems to have hardware RAID and those modules are loaded now when running the older kernel.

```

$ lspci -nn | grep SCSI
02:00.0 SCSI storage controller [0100]: LSI Logic / Symbios Logic SAS1068E PCI-Express Fusion-MPT SAS [1000:0058] (rev 08)

$ lsmod | grep mpt
mpt2sas               157976  1
raid_class             13554  1 mpt2sas
mptctl                 38982  1
mptsas                 63612  2
mptscsih               44882  1 mptsas
mptbase               103162  3 mptctl,mptsas,mptscsih
scsi_transport_sas     40558  2 mpt2sas,mptsas

```

> **tgalati4 said:**
> I would research the differences between the 0-48 and 0-39 kernels (hint:  read the changelog for 0-48) and see if anything looks relevant.  File a bug against the 0-48 kernel if a true regression is found--that is something that was working is now no longer working.  It looks like a device driver for hardware connected to the pci bus got tripped up.  Try removing all hardware from the PCI bus and see if the server boots, then add hardware back one at a time.

You have turned your production server into a test server.  I think you have answered the second question.

This seems like the right thing to do, but a little out of my league and way too much off-time for our PBX I'm afraid. I will not *dist-upgrade* an Ubuntu production server again, if I haven't tested it first on identical hardware!

Thank you all for your help! I'll come back and let you know how it goes.

---

### Post by tgalati4 on 2013-07-03
As a server administrator, you have to balance the risk of downtime versus the benefit of upgrading.  If you have a working server, and all of your services are up, and they are mission critical, then **any** operating system upgrade will probably not improve that situation.  If there is a virus or other security issue that you read about and you feel that your system is vulnerable and needs to be patched, then upgrading (to apply the security patch) may be justified.

There is also a difference between *upgrade* and *dist-upgrade*; from the man page:  (bold emphasis added)

> 
       upgrade
           upgrade is used to install the newest versions of all packages currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new versions available are retrieved and upgraded;[B] under no circumstances are
           currently installed packages removed[/B], or packages not already installed retrieved and installed. New versions of currently installed packages
           that cannot be upgraded without changing the install status of another package will be left at their current version. An update must be
           performed first so that apt-get knows that new versions of packages are available.

       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of
           packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less
           important ones if necessary. **The dist-upgrade command may therefore remove some packages.** The /etc/apt/sources.list file contains a list of
           locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings fo individual packages.



The removal of packages can break things.  So unless you have a specific reason to use *dist-upgrade*, you want to stick to *upgrade*.

If this server is performing a mission-critical function, then it makes sense to have a hardware backup server ready to go.  That server can also be your test server so that you can test updates before rolling them out in a production environment.  Having identical hardware helps, because the hardware differences can fool you.

---

### Post by jofa on 2013-07-04
Lesson learned and I will use dist-upgrade more wisely in the future. 
Booting into rescue mode with the 3.2.0-48 kernel produces similiar errors as regular boot and I can't get any control. I've submitted a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197698"). It's probably insufficent info, but I hope it's better than nothing.

---

### Post by tgalati4 on 2013-07-04
It would be a good idea to post this thread link in your bug report.  Also check your log files in /var/log/apt and see if you can determine what (if any) packages got removed when you performed the dist-upgrade.  It may be a missing package as opposed to a kernel bug since you performed the kernel upgrade at the same time as the dist-upgrade--confounding the issue.  It could be a kernel issue, a missing package issue, or the combination of both.

---

### Post by SeijiSensei on 2013-07-04
> **jofa said:**
> Lesson learned and I will use dist-upgrade more wisely in the future. 
Booting into rescue mode with the 3.2.0-48 kernel produces similiar errors as regular boot and I can't get any control. I've submitted a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197698"). It's probably insufficent info, but I hope it's better than nothing.

Did you try reverting to the previous kernel, either in recovery mode or normal mode?  Did the problem disappear?  That would answer  tgalati4's question about whether the problem lies in the kernel or with some other package you installed.

---

### Post by jofa on 2013-07-05
> **tgalati4 said:**
> It would be a good idea to post this thread link in your bug report.  

[Done]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197698/comments/3").

> **tgalati4 said:**
> Also check your log files in /var/log/apt and see if you can determine what (if any) packages got removed when you performed the dist-upgrade. &#8230;

Here's the log:

```
$ zcat /var/log/apt/history.log.2.gz

Start-Date: 2013-06-24  16:50:55
Commandline: apt-get dist-upgrade
Install: linux-headers-3.2.0-48:amd64 (3.2.0-48.74, automatic), linux-image-3.2.0-48-generic:amd64 (3.2.0-48.74), linux-headers-3.2.0-48-generic:amd64 (3.2.0-48.74, automatic)
Upgrade: openssh-server:amd64 (5.9p1-5ubuntu1, 5.9p1-5ubuntu1.1), libswscale2:amd64 (0.8.5-0ubuntu0.12.04.1, 0.8.6-0ubuntu0.12.04.1), nagios-plugins-basic:amd64 (1.4.15-5ubuntu3, 1.4.15-5ubuntu3.1), libxfixes3:amd64 (5.0-4ubuntu4, 5.0-4ubuntu4.1), libc-bin:amd64 (2.15-0ubuntu10.3, 2.15-0ubuntu10.4), libavutil51:amd64 (0.8.5-0ubuntu0.12.04.1, 0.8.6-0ubuntu0.12.04.1), python-minimal:amd64 (2.7.3-0ubuntu2, 2.7.3-0ubuntu2.2), libxxf86dga1:amd64 (1.1.2-1, 1.1.2-1ubuntu0.1), smbclient:amd64 (3.6.3-2ubuntu2.4, 3.6.3-2ubuntu2.6), linux-server:amd64 (3.2.0.39.47, 3.2.0.48.58), libx11-data:amd64 (1.4.99.1-0ubuntu2, 1.4.99.1-0ubuntu2.1), mysql-server:amd64 (5.5.29-0ubuntu0.12.04.2, 5.5.31-0ubuntu0.12.04.2), openjdk-7-jdk:amd64 (7u15-2.3.7-0ubuntu1~12.04.1, 7u21-2.3.9-0ubuntu0.12.04.1), libdrm-radeon1:amd64 (2.4.39-0ubuntu0.1, 2.4.43-0ubuntu0.0.1), libdbus-1-3:amd64 (1.4.18-1ubuntu1.3, 1.4.18-1ubuntu1.4), openjdk-7-jre:amd64 (7u15-2.3.7-0ubuntu1~12.04.1, 7u21-2.3.9-0ubuntu0.12.04.1), libxxf86vm1:amd64 (1.1.1-2build1, 1.1.1-2ubuntu0.1), libpython2.7:amd64 (2.7.3-0ubuntu3.1, 2.7.3-0ubuntu3.2), accountsservice:amd64 (0.6.15-2ubuntu9.5, 0.6.15-2ubuntu9.6), libgl1-mesa-dri:amd64 (8.0.4-0ubuntu0.4, 8.0.4-0ubuntu0.6), smbfs:amd64 (5.1-1ubuntu1, 5.1-1ubuntu2), libavfilter2:amd64 (0.8.5-0ubuntu0.12.04.1, 0.8.6-0ubuntu0.12.04.1), libxcb-glx0:amd64 (1.8.1-1ubuntu0.1, 1.8.1-1ubuntu0.2), libgl1-mesa-glx:amd64 (8.0.4-0ubuntu0.4, 8.0.4-0ubuntu0.6), libav-tools:amd64 (0.8.5-0ubuntu0.12.04.1, 0.8.6-0ubuntu0.12.04.1), gvfs-libs:amd64 (1.12.1-0ubuntu1.1, 1.12.1-0ubuntu1.2), libjack-jackd2-0:amd64 (1.9.8~dfsg.1-1ubuntu1, 1.9.8~dfsg.1-1ubuntu2), libwbclient0:amd64 (3.6.3-2ubuntu2.4, 3.6.3-2ubuntu2.6), aptitude:amd64 (0.6.6-1ubuntu1.1, 0.6.6-1ubuntu1.2), language-selector-common:amd64 (0.79.2, 0.79.3), python-apt:amd64 (0.8.3ubuntu7, 0.8.3ubuntu7.1), nagios-plugins:amd64 (1.4.15-5ubuntu3, 1.4.15-5ubuntu3.1), python-dev:amd64 (2.7.3-0ubuntu2, 2.7.3-0ubuntu2.2), libavdevice53:amd64 (0.8.5-0ubuntu0.12.04.1, 0.8.6-0ubuntu0.12.04.1), bash:amd64 (4.2-2ubuntu2, 4.2-2ubuntu2.1), libx11-xcb1:amd64 (1.4.99.1-0ubuntu2, 1.4.99.1-0ubuntu2.1), libmysqlclient-dev:amd64 (5.5.29-0ubuntu0.12.04.2, 5.5.31-0ubuntu0.12.04.2), libgnutls26:amd64 (2.12.14-5ubuntu3.2, 2.12.14-5ubuntu3.4), python-apt-common:amd64 (0.8.3ubuntu7, 0.8.3ubuntu7.1), libglapi-mesa:amd64 (8.0.4-0ubuntu0.4, 8.0.4-0ubuntu0.6), gvfs-common:amd64 (1.12.1-0ubuntu1.1, 1.12.1-0ubuntu1.2), apport:amd64 (2.0.1-0ubuntu17.1, 2.0.1-0ubuntu17.3), mysql-server-core-5.5:amd64 (5.5.29-0ubuntu0.12.04.2, 5.5.31-0ubuntu0.12.04.2), mtools:amd64 (4.0.12-1, 4.0.12-1ubuntu0.12.04.1), python2.7:amd64 (2.7.3-0ubuntu3.1, 2.7.3-0ubuntu3.2), libmysqlclient18:amd64 (5.5.29-0ubuntu0.12.04.2, 5.5.31-0ubuntu0.12.04.2), libavcodec53:amd64 (0.8.5-0ubuntu0.12.04.1, 0.8.6-0ubuntu0.12.04.1), libaccountsservice0:amd64 (0.6.15-2ubuntu9.5, 0.6.15-2ubuntu9.6), linux-headers-server:amd64 (3.2.0.39.47, 3.2.0.48.58), linux-firmware:amd64 (1.79.1, 1.79.4), samba-common:amd64 (3.6.3-2ubuntu2.4, 3.6.3-2ubuntu2.6), dbus:amd64 (1.4.18-1ubuntu1.3, 1.4.18-1ubuntu1.4), libxcb1:amd64 (1.8.1-1ubuntu0.1, 1.8.1-1ubuntu0.2), libdrm2:amd64 (2.4.39-0ubuntu0.1, 2.4.43-0ubuntu0.0.1), libcups2:amd64 (1.5.3-0ubuntu6, 1.5.3-0ubuntu8), libcurl3:amd64 (7.22.0-3ubuntu4, 7.22.0-3ubuntu4.1), libxinerama1:amd64 (1.1.1-3build1, 1.1.1-3ubuntu0.1), python:amd64 (2.7.3-0ubuntu2, 2.7.3-0ubuntu2.2), openssh-client:amd64 (5.9p1-5ubuntu1, 5.9p1-5ubuntu1.1), multiarch-support:amd64 (2.15-0ubuntu10.3, 2.15-0ubuntu10.4), mysql-client-core-5.5:amd64 (5.5.29-0ubuntu0.12.04.2, 5.5.31-0ubuntu0.12.04.2), libssl-dev:amd64 (1.0.1-4ubuntu5.8, 1.0.1-4ubuntu5.9), python-problem-report:amd64 (2.0.1-0ubuntu17.1, 2.0.1-0ubuntu17.3), libxt-dev:amd64 (1.1.1-2build1, 1.1.1-2ubuntu0.1), libssl-doc:amd64 (1.0.1-4ubuntu5.8, 1.0.1-4ubuntu5.9), libdrm-nouveau1a:amd64 (2.4.39-0ubuntu0.1, 2.4.43-0ubuntu0.0.1), libdrm-intel1:amd64 (2.4.39-0ubuntu0.1, 2.4.43-0ubuntu0.0.1), ffmpeg:amd64 (0.8.5-0ubuntu0.12.04.1, 0.8.6-0ubuntu0.12.04.1), libpostproc52:amd64 (0.8.5-0ubuntu0.12.04.1, 0.8.6-0ubuntu0.12.04.1), curl:amd64 (7.22.0-3ubuntu4, 7.22.0-3ubuntu4.1), libasound2:amd64 (1.0.25-1ubuntu10.1, 1.0.25-1ubuntu10.2), isc-dhcp-client:amd64 (4.1.ESV-R4-0ubuntu5.6, 4.1.ESV-R4-0ubuntu5.8), libxrender1:amd64 (0.9.6-2build1, 0.9.6-2ubuntu0.1), postgresql-client-9.1:amd64 (9.1.8-0ubuntu12.04, 9.1.9-0ubuntu12.04), libavformat53:amd64 (0.8.5-0ubuntu0.12.04.1, 0.8.6-0ubuntu0.12.04.1), libtiff4:amd64 (3.9.5-2ubuntu1.4, 3.9.5-2ubuntu1.5), dhcp3-client:amd64 (4.1.ESV-R4-0ubuntu5.6, 4.1.ESV-R4-0ubuntu5.8), icedtea-7-jre-jamvm:amd64 (7u15-2.3.7-0ubuntu1~12.04.1, 7u21-2.3.9-0ubuntu0.12.04.1), openjdk-7-jre-lib:amd64 (7u15-2.3.7-0ubuntu1~12.04.1, 7u21-2.3.9-0ubuntu0.12.04.1), libpq-dev:amd64 (9.1.8-0ubuntu12.04, 9.1.9-0ubuntu12.04), libplymouth2:amd64 (0.8.2-2ubuntu31, 0.8.2-2ubuntu31.1), bash-completion:amd64 (1.3-1ubuntu8, 1.3-1ubuntu8.1), libxtst6:amd64 (1.2.0-4, 1.2.0-4ubuntu0.1), libc6-dev:amd64 (2.15-0ubuntu10.3, 2.15-0ubuntu10.4), cifs-utils:amd64 (5.1-1ubuntu1, 5.1-1ubuntu2), plymouth-theme-ubuntu-text:amd64 (0.8.2-2ubuntu31, 0.8.2-2ubuntu31.1), python2.7-minimal:amd64 (2.7.3-0ubuntu3.1, 2.7.3-0ubuntu3.2), libx11-6:amd64 (1.4.99.1-0ubuntu2, 1.4.99.1-0ubuntu2.1), libpq5:amd64 (9.1.8-0ubuntu12.04, 9.1.9-0ubuntu12.04), python-apport:amd64 (2.0.1-0ubuntu17.1, 2.0.1-0ubuntu17.3), linux-image-server:amd64 (3.2.0.39.47, 3.2.0.48.58), openssl:amd64 (1.0.1-4ubuntu5.8, 1.0.1-4ubuntu5.9), rsyslog:amd64 (5.8.6-1ubuntu8.1, 5.8.6-1ubuntu8.4), libpulse0:amd64 (1.1-0ubuntu15.2, 1.1-0ubuntu15.3), libx11-dev:amd64 (1.4.99.1-0ubuntu2, 1.4.99.1-0ubuntu2.1), libcurl3-gnutls:amd64 (7.22.0-3ubuntu4, 7.22.0-3ubuntu4.1), gvfs:amd64 (1.12.1-0ubuntu1.1, 1.12.1-0ubuntu1.2), linux-libc-dev:amd64 (3.2.0-39.62, 3.2.0-48.74), libx11-doc:amd64 (1.4.99.1-0ubuntu2, 1.4.99.1-0ubuntu2.1), samba-common-bin:amd64 (3.6.3-2ubuntu2.4, 3.6.3-2ubuntu2.6), libxcb-render0:amd64 (1.8.1-1ubuntu0.1, 1.8.1-1ubuntu0.2), isc-dhcp-common:amd64 (4.1.ESV-R4-0ubuntu5.6, 4.1.ESV-R4-0ubuntu5.8), dbus-x11:amd64 (1.4.18-1ubuntu1.3, 1.4.18-1ubuntu1.4), libxi6:amd64 (1.6.0-0ubuntu2, 1.6.0-0ubuntu2.1), libc-dev-bin:amd64 (2.15-0ubuntu10.3, 2.15-0ubuntu10.4), libxcb1-dev:amd64 (1.8.1-1ubuntu0.1, 1.8.1-1ubuntu0.2), libxcb-shape0:amd64 (1.8.1-1ubuntu0.1, 1.8.1-1ubuntu0.2), libc6:amd64 (2.15-0ubuntu10.3, 2.15-0ubuntu10.4), python2.7-dev:amd64 (2.7.3-0ubuntu3.1, 2.7.3-0ubuntu3.2), libxcursor1:amd64 (1.1.12-1, 1.1.12-1ubuntu0.1), libxcb-shm0:amd64 (1.8.1-1ubuntu0.1, 1.8.1-1ubuntu0.2), libxt6:amd64 (1.1.1-2build1, 1.1.1-2ubuntu0.1), libxv1:amd64 (1.0.6-2build1, 1.0.6-2ubuntu0.1), libxext6:amd64 (1.3.0-3build1, 1.3.0-3ubuntu0.1), mysql-common:amd64 (5.5.29-0ubuntu0.12.04.2, 5.5.31-0ubuntu0.12.04.2), libxrandr2:amd64 (1.3.2-2ubuntu0.1, 1.3.2-2ubuntu0.2), mysql-server-5.5:amd64 (5.5.29-0ubuntu0.12.04.2, 5.5.31-0ubuntu0.12.04.2), nagios-plugins-standard:amd64 (1.4.15-5ubuntu3, 1.4.15-5ubuntu3.1), dhcp3-common:amd64 (4.1.ESV-R4-0ubuntu5.6, 4.1.ESV-R4-0ubuntu5.8), openjdk-7-jre-headless:amd64 (7u15-2.3.7-0ubuntu1~12.04.1, 7u21-2.3.9-0ubuntu0.12.04.1), plymouth:amd64 (0.8.2-2ubuntu31, 0.8.2-2ubuntu31.1), gvfs-daemons:amd64 (1.12.1-0ubuntu1.1, 1.12.1-0ubuntu1.2), mysql-client-5.5:amd64 (5.5.29-0ubuntu0.12.04.2, 5.5.31-0ubuntu0.12.04.2), libssl1.0.0:amd64 (1.0.1-4ubuntu5.8, 1.0.1-4ubuntu5.9)
End-Date: 2013-06-24  16:56:30
```

No packages were removed.

> **SeijiSensei said:**
> Did you try reverting to the previous kernel, either in recovery mode or normal mode?  Did the problem disappear?  That would answer  tgalati4's question about whether the problem lies in the kernel or with some other package you installed.

As stated in the original post the server is currently running the previously installed kernel (3.2.0-39) and the problem (can't boot) is not there. Per your suggestion (with modification) I've changed GRUB_DEFAULT in /etc/default/grub to point to this "bootable" kernel.

```
GRUB_DEFAULT='Ubuntu, with Linux 3.2.0-39-generic'
```

---

