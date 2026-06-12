---
title: "Can't update using Muon nor Synaptic"
date: 2012-06-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by loukingjr on 2012-06-07
just installed Kubuntu 12.10a1 and neither package will allow me to update. I get an "another application  seems to be using the package system at this time." message. this is even after a reboot.  Apt-get works.

---

### Post by Gregory Lee on 2012-06-07
I might be running Kubuntu 12.10 (not sure -- more below) and I just tried to use Muon Software Center, but got an error when I tried to download something (it said my system might be misconfigured).  However, I have been using Ubuntu Software Center, so maybe that will work for you (if you can somehow download it).

Actually, I'm running the KDE Plasma Desktop interface of Ubuntu 12.04 upgraded to 12.10, and I don't know whether that counts the same as Kubuntu 12.10.  I'm running the KDE desktop because the Gnome and Ubuntu desktops crash for me.  The nice thing about KDE is that it works (more or less).

---

### Post by PaulW2U on 2012-06-08
> **loukingjr said:**
> just installed Kubuntu 12.10a1 and neither package will allow me to update. I get an "another application  seems to be using the package system at this time." message. this is even after a reboot.  Apt-get works.
I'm seeing the same with muon but synaptic works fine now, I did have a problem with it a couple of days ago.

I've Googled for suggested fixes and none of them have worked so this must be a bug. I'll have a look on Launchpad and the KDE Bugzilla later.

---

### Post by mparillo on 2012-06-08
> **Gregory Lee said:**
> I might be running Kubuntu 12.10 (not sure -- more below) and I just tried to use Muon Software Center, but got an error when I tried to download something (it said my system might be misconfigured).  However, I have been using Ubuntu Software Center, so maybe that will work for you (if you can somehow download it).

Actually, I'm running the KDE Plasma Desktop interface of Ubuntu 12.04 upgraded to 12.10, and I don't know whether that counts the same as Kubuntu 12.10.  I'm running the KDE desktop because the Gnome and Ubuntu desktops crash for me.  The nice thing about KDE is that it works (more or less).

I posted this to Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1000939](https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1000939)

---

