---
title: "Recent update results in a kernel panic on boot"
date: 2024-06-10
forum: Server Platforms
---

### Post by jisey55167 on 2024-06-10
Ubuntu 22.04.4 LTS running on a Lenovo Tiny (type 10RR)

no changes in the BIOS prior to this panic

I can boot into previous version "Ubuntu, with Linux 5.15.0-107-generic" 
but the default boot option of "Ubuntu, with Linux 5.15.0-112-generic" 
panics with the following screen attached.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293851&stc=1[/IMG]

Ideas please?

grep -iR ubuntu /etc
/etc/os-release:PRETTY_NAME="Ubuntu 22.04.4 LTS"
/etc/os-release:NAME="Ubuntu"
/etc/os-release:ID=ubuntu
/etc/os-release:HOME_URL="https://www.ubuntu.com/"
/etc/os-release:SUPPORT_URL="https://help.ubuntu.com/"
/etc/os-release:BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
/etc/os-release:PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
/etc/os-release:UBUNTU_CODENAME=jammy
/etc/lsb-release:DISTRIB_ID=Ubuntu
/etc/lsb-release:DISTRIB_DESCRIPTION="Ubuntu 22.04.4 LTS"

---

### Post by jisey55167 on 2024-06-10
attaching output of sudo lshw -short

[ATTACH]293852[/ATTACH]

---

