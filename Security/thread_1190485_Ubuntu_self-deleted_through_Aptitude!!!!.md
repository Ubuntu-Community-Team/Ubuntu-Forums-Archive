---
title: "Ubuntu self-deleted through Aptitude!!!!"
date: 2009-06-17
forum: Security
---

### Post by whydoesitburn on 2009-06-17
Today as I was trying to install some apps into my Ubuntu partition, after I had made the selected changes that I wanted and started the update, Aptitude starting deleting everything from gnome to the kernel it self. Now whenever Grub loads up, it list the Ubuntu, yet it says file missing whenever I make that selection. Can anyone tell me what may have happened to cause this so I may avoid such an incident in the future. I know I probably won't be able to get that incarnation of my system back without a fresh install, so I'm just going to try to back up my files through my XP partition before I do said install.

---

### Post by Rubicon_82 on 2009-06-18
Hi,

I think the most likely cause of this would be a dependency conflict in the package you were trying to install.  Using aptitude with the 'full-upgrade' option (or apt-get dist-upgrade) allows aptitude to remove packages to try and resolve the dependency conflict.  Using 'apt-get upgrade' or 'aptitude safe-upgrade' would prevent the package manager from removing packages.

As to why the problem occurred, my guess is that you either:
A:  Were using an alpha release (i.e. Karmic), where a serious bug like this could reasonably be expected.  (I am not saying that such a bug currently exists - only that it *could*).

B: Had third-party repositories enabled within your /etc/apt/sources.list file.

If you do use third party repositories, it would be wise to pin them at a lower priority than the official repositories.  Done correctly, this should prevent aptitude from installing conflicting packages from third party sources.  See 'man apt_preferences' for details.

---

