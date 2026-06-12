---
title: "Huge iso size increase."
date: 2024-04-20
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2024-04-20
Just installed the April 20 iso of Xubuntu and noticed a huge increase in the size of the iso from 3.0G to 3.8G since I last used one, just 2 days ago.

Anyone have a quick answer as to what has been added to increase the size so much.
I know I could get the manifest with all details but that would certainly take a lot of searching and I have never looked at one in the past and I don't have it for the April 18 iso anyway and not sure how I can now get it.

This new version is working very well so far and doesn't appear to use more disk space than previous daily iso versions so I'm simply wondering if somebody has an answer for me.

---

### Post by Irihapeti on 2024-04-20
This version is working with offline install, which has been a problem for quite some time (with that horribly vague error message: "Something went wrong").

---

### Post by ajgreeny on 2024-04-21
I've never seen that message when installing that I can remember, though there were many days just after the bootstrap installer was addad to Xubuntu when the installer always crashed.
I can't remember in detail what error message was seen when that happened but is that what you mean by the "offline installer"? Surely not?
And 800M or thereabouts is a huge install system if that's the main or only big difference.

---

### Post by Irihapeti on 2024-04-21
I might be getting mixed up with messages from Calamares. Perhaps I'm doing too much testing and need a break. :)

---

### Post by ajgreeny on 2024-04-21
I've not used calamares as I personally don't like either Lubuntu or Kubuntu which use it (nothing else does, correct?) so I've not tested them.

Interesting to note that the new Noble wallpaper for Xubuntu has gone green; nearly 20 years of blues/greys and out of the blue to green - quite a change!

---

### Post by guiverc on 2024-04-21
Ubuntu Unity also uses calamares.

[https://cdimage.ubuntu.com/ubuntu-unity/daily-live/current/noble-desktop-amd64.manifest](https://cdimage.ubuntu.com/ubuntu-unity/daily-live/current/noble-desktop-amd64.manifest)

```

calamares	3.3.5-0ubuntu3
calamares-settings-ubuntu-common	1:24.04.37
calamares-settings-ubuntu-unity	1:24.04.37

```

I've not tested Xubuntu in awhile; it was 3.2GB last time I grabbed it

```

guiverc@d7050-next:/de2900/xubuntu_64$   ls -ltrh nob* 
-rw------- 1 guiverc guiverc 3.1G Apr  9 04:12 noble-desktop-amd64.iso.zs-old
-rw------- 1 guiverc guiverc 3.1G Apr  9 04:12 noble-desktop-amd64.iso.old
-rw-rw-r-- 1 guiverc guiverc  58K Apr  9 14:08 noble-desktop-amd64.manifest.old
-rw-rw-r-- 1 guiverc guiverc 6.1M Apr  9 14:12 noble-desktop-amd64.zsync.old
-rw------- 1 guiverc guiverc 3.2G Apr 10 12:54 noble-desktop-amd64.iso
-rw-rw-r-- 1 guiverc guiverc  58K Apr 10 22:49 noble-desktop-amd64.manifest
-rw-rw-r-- 1 guiverc guiverc 6.3M Apr 10 22:54 noble-desktop-amd64.iso.zsync

```

---

### Post by Irihapeti on 2024-04-21
Since we are talking about installers, I might ask the question here:

I've noticed that Subiquity uses a *lot* more CPU in my VMs than Calamares does. Is that something others have noticed (not just in VMs), or is something simply wrong with my QEMU/KVM setup?

---

### Post by Claus7 on 2024-04-21
Hello,

> **Irihapeti said:**
> Since we are talking about installers, I might ask the question here:

I've noticed that Subiquity uses a *lot* more CPU in my VMs than .... Is that something others have noticed ..., or ...

the answer is affirmative. Always when testing ubuntu 24.04 I try to use the maximum available cpus and memory for the installation to take place under virtualbox. Especially at the early steps of the new installer. I cannot tell between subiquity and calamares, because I haven't compared them. In general the installation is taking more resources than it used to.

Regards!

---

### Post by Doug S on 2024-04-21
Interesting, I also see a huge increase in the size of the Ubuntu Desktop amd64 ISO. 510,533,632 bytes. However, my last reference is April 7th:

```
doug@s15:~/iso$ ls -l noble-desktop*
-rw-r--r-- 1 doug doug 5336997888 Mar 17 01:15 noble-desktop-amd64-2024-03-17.iso
-rw-r--r-- 1 doug doug 5341532160 Mar 22 00:44 noble-desktop-amd64-2024-03-22.iso
-rw-r--r-- 1 doug doug 5341255680 Mar 22 23:41 noble-desktop-amd64-2024-03-23.iso
-rw-r--r-- 1 doug doug 5343690752 Apr  7 02:19 noble-desktop-amd64-2024-04-07.iso
-rw-r--r-- 1 doug doug 5854224384 Apr 20 23:12 noble-desktop-amd64-2024-04-21.iso
```

If I just look at the daily web site I see:

```

2024.04.17 5.3G
2024.04.18 5.3G
2024.04.20 5.6G
2024.04.21 5.5G

```

---

### Post by #&amp;thj^% on 2024-04-21
Along with the size increase, and load it imposes, My zfs-root would not install over my current zfs system until I blanked the drive/disk.

I keep good back-ups so all is good.

---

