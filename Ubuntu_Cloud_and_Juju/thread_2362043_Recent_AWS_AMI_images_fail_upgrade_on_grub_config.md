---
title: "Recent AWS AMI images fail upgrade on grub config"
date: 2017-05-23
forum: Ubuntu Cloud and Juju
---

### Post by bedge on 2017-05-23
When installing ami-efd0428f (xenial hvn-ssd us-west-2) from [https://cloud-images.ubuntu.com/locator/](https://cloud-images.ubuntu.com/locator/) as well as a few others I tried around the latest releases, all for us-west-2, all fail on `apt-get upgrade` with:
```

Searching for default file ... found: /boot/grub/default^M
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst^M
Searching for splash image ... none found, skipping ...^M
Found kernel: /boot/vmlinuz-4.4.0-78-generic^M
A new version of /boot/grub/menu.lst is available, but the version installed ^M
currently has been locally modified.^M
^M
  1. install the package maintainer's version^M
  2. keep the local version currently installed^M
  3. show the differences between the versions^M
  4. show a side-by-side difference between the versions^M
  5. show a 3-way difference between available versions^M
  6. do a 3-way merge between available versions (experimental)^M
  7. start a new shell to examine the situation^M
^M
```

There's a post on the packer forum about this: [URL="https://groups.google.com/forum/?utm_medium=email&utm_source=footer#!msg/packer-tool/e1CVNAbDxQI/RGtYW_FDAwAJ"]https://groups.google.com/forum/?utm_medium=email&utm_source=footer#!msg/packer-tool/e1CVNAbDxQI/RGtYW_FDAwAJ
[/URL] 
which indicates that some changes are needed in the packaging of the Ubuntu AMI.

---

