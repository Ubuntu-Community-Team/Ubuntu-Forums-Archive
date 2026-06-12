---
title: "Virtualbox 3.1 won't run"
date: 2010-01-30
forum: Virtualisation
---

### Post by Pressondude on 2010-01-30
I'm trying to install the x86_64 version from the .deb provided on the website, and keep getting an error that an existing package is conflicting. This is a fresh Kubuntu install. I was also unable to run when I installed through Kpackage (and have uninstalled) because I was apparently missing my generic linux headers (I'm not, and they're up to date). Why won't this install?

This is the output from the GDebi when I try to install.
```
dpkg: regarding .../virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_amd64.deb containing virtualbox-3.1:
 virtualbox-ose-source conflicts with virtualbox
  virtualbox-3.1 provides virtualbox and is to be installed.
dpkg: error processing /home/wraith/Desktop/virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_amd64.deb (--install):
 conflicting packages - not installing virtualbox-3.1
Errors were encountered while processing:
 /home/wraith/Desktop/virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_amd64.deb

```

---

### Post by rogue_0111 on 2010-01-30
This happened to me a few months back. Check to see if another version of Virtualbox is already installed.

---

### Post by Pressondude on 2010-01-31
huh...apparently it had installed the source package and wasn't removing it...thanks!

---

