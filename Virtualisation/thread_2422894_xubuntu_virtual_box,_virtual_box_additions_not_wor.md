---
title: "xubuntu virtual box, virtual box additions not working."
date: 2019-07-14
forum: Virtualisation
---

### Post by ocupi on 2019-07-14
I have been trying to get xubuntu installed with vbox additions but have not yet succeeded. I want to have the option where the res changes when the window is resized, seamless mouse integration (where it does not lock inside the window), clipboard bidirectional sync etc.

I have tried the following:
```
sudo apt update
sudo apt upgrade
sudo apt install build-essential dkms linux-headers-$(uname -r)
sudo apt-get install virtualbox-guest-additions-iso
```

Also tried running the autorun.sh from the mount vbox additions cd option, this caused the OS to never boot again hanging on a black screen with flashing cursor.

What am I missing?

---

### Post by &amp;KyT$0P# on 2019-07-14
What host OS?
What version of VirtualBox?

---

### Post by wildmanne39 on 2019-07-14
*Thread moved to **Virtualisation a more appropriate sub-forum**.*

---

### Post by mechanic on 2019-11-12
[https://websiteforstudents.com/installing-virtualbox-guest-additions-on-ubuntu-18-10-18-04-16-04-lts/](https://websiteforstudents.com/installing-virtualbox-guest-additions-on-ubuntu-18-10-18-04-16-04-lts/)

---

