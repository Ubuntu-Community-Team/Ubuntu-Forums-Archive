---
title: "dpkg: unrecoverable fatal error"
date: 2010-02-01
forum: Server Platforms
---

### Post by Leszczu on 2010-02-01
Hi all,
I have a strange error trying to install smartmontools:

```

$ sudo aptitude install smartmontools
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  smartmontools
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/332kB of archives. After unpacking 823kB will be used.
Writing extended state information... Done
Selecting previously deselected package smartmontools.
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `initramfs-tools' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

```

Can anyone tell me what it is? I get same error running **dpkg -i** on that package.
My system is Ubuntu server 9.10 32-bit.

---

### Post by Barriehie on 2010-02-01
Try to download the package again:
```

sudo apt-get --download-only smartmontools
```
and then install.  Might want to --purge it first.
```

sudo apt-get --purge smartmontools
```

HTH,
Barrie

---

### Post by Leszczu on 2010-02-02
Thanks for help, Barriehie.
I did as you said, --download-only did nothing (package was already downloaded), same with --purge (it was never installed). But day after that, I did update & everything works fine. I think it might be temporary repository error. Everything's fine now. Thanks again for help.

Regards,
Leszczu

---

### Post by Barriehie on 2010-02-02
Anytime!

---

