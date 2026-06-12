---
title: "Virtual OS Instal to Real Instal..."
date: 2008-09-03
forum: Virtualisation
---

### Post by El_Belgicano on 2008-09-03
Guys, I'd like to know if it's possible (and how complicated) to move an installation created in VirtualBox (virtual disk) to a real partition on my physical drive...
Guest OS would be a minimal Hardy, Host would be my actual Gutsy.
All on the same hardware.
Thanks in advance...

---

### Post by wd5gnr on 2008-09-03
So you want to move to using the guest OS as a real OS, right?

If I were you, I'd just boot the VM, roll off my package and sources list and home directory to a shared folder and then do a fresh install. Then untar the home directory and reinstall packages. 

I assume you know how to tar off your home directory and save sources.list along with any other "important" config files under /etc that you've touched yourself.

Then:
dpkg --get-selections > packages.txt

Put that with the other files. After you reinstall and reset sources.list

dpkg --set-selections < packages.txt
apt-get update
apt-get upgrade

---

