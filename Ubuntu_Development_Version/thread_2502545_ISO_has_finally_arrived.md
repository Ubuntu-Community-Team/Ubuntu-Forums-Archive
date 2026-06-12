---
title: "ISO has finally arrived"
date: 2024-11-19
forum: Ubuntu Development Version
---

### Post by corradoventu on 2024-11-19
[https://cdimages.ubuntu.com/daily-live/pending/](https://cdimages.ubuntu.com/daily-live/pending/)

---

### Post by Rubi1200 on 2024-11-19
thanks for the update

---

### Post by corradoventu on 2024-11-19
ISO arrived but i'm unable to install from it.

---

### Post by 1fallen on 2024-11-19
Same Here.

---

### Post by ajgreeny on 2024-11-19
Just out of interest is it possible to  manually edit the sources file to point to 25.04 and move on from that point to run plucky?

I'm not suggesting it's a good way to get to the new version but just wondering ; is it an installer fault or is there more to it than that?

---

### Post by 1fallen on 2024-11-19
ajgreeny, that is how I did it.

It appears to be a installer bug so far but don't quote on that yet.

Just to save time these need the edit, This one needs the change "/etc/apt/sources.list.d/ubuntu.sources"
also this "/etc/os-release" and lastly "/etc/lsb-release"

---

### Post by Rubi1200 on 2024-11-20
Installation failed for me too.

Oh well...hopefully the apport report will help them fix things.

---

### Post by 1fallen on 2024-11-20
Bug filed here: [https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2089164](https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2089164)

Sheesh they make it hard to gather logs.....LOL

---

### Post by Rubi1200 on 2024-11-20
Added my name to this bug affects me too aargh!

From a very quick look it seems I had pretty much exactly the same types of errors (more or less).

---

### Post by VMC on 2024-11-20
Added my name just to see what the fuss is all about (harhar)
Actually I plan to download just to experience the hubbub.

---

### Post by corradoventu on 2024-11-21
With Ubuntu 25.04 "Plucky Puffin" - Daily amd64 (20241121.1)
[https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2089275](https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2089275)

Edit: using today ISO Ubuntu 25.04 "Plucky Puffin" - Daily amd64 (20241122)
I successfully installed on both my desktop and laptop
[https://iso.qa.ubuntu.com/qatracker/milestones/464/builds/317357/testcases/1761/results](https://iso.qa.ubuntu.com/qatracker/milestones/464/builds/317357/testcases/1761/results)

---

### Post by 1fallen on 2024-11-25
Xubuntu Daily with minimal install succeeded today's date 11-25-2024

With a big delight to me..."Zero" snaps was installed, quickly pinned snapd to hold....Perfect!
I hope this remains on final release.
```
PRETTY_NAME="Ubuntu Plucky Puffin (development branch)"
NAME="Ubuntu"
VERSION_ID="25.04"
VERSION="25.04 (Plucky Puffin)"
VERSION_CODENAME=plucky
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=plucky
LOGO=ubuntu-logo
```

---

