---
title: "Loading Kubuntu side by side with Ubuntu using Gnome"
date: 2007-01-14
forum: The Cafe
---

### Post by CubicleDweller on 2007-01-14
I want to run Ubuntu with KDE and Gnome side by side to get a good comparison of how it works. Plus I don't want to have to work out why Knoppix 5.1 doesn't support the video card in my server and what I would have to do to get around it.
Does anyone have any benchmarks or information/personal preference/ experience one way or the other as the best to run with Ubuntu?

---

### Post by nandasunu on 2007-01-14
assuming you have ubuntu (gnome) installed, just run:

```
sudo apt-get install kubuntu-desktop
```

---

### Post by floke on 2007-01-14
To get KDE on ubuntu, open a terminal and enter

apt-get install kubuntu-desktop

(if this doesn't work then use 'sudo apt-get install kubuntu-desktop)

then logout. from the login window select the option for 'sessions' and you can now select either kde or gnome

---

### Post by dbbolton on 2007-01-14
don't be surprised when your boot splash changes to a blue kubuntu one.

---

### Post by v8YKxgHe on 2007-01-14
> don't be surprised when your boot splash changes to a blue kubuntu one.

Yeah, how do you change it back? Or better still, how do you change it completely?

---

### Post by GarethMB on 2007-01-14
Don't use apt-get. Use aptitude instead.

---

### Post by aysiu on 2007-01-14
> **Steve.K said:**
> To get KDE on ubuntu, open a terminal and enter

apt-get install kubuntu-desktop

(if this doesn't work then use 'sudo apt-get install kubuntu-desktop)

then logout. from the login window select the option for 'sessions' and you can now select either kde or gnome
Since the OP isn't using Edgy, I would strongly recommend *against* using *apt-get* in this situation.

Full instructions here (with screenshots):
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by MkfIbK7a on 2007-01-14
yes i would agree with aysiu use 
sudo aptitude install kubuntu-desktop

---

### Post by GarethMB on 2007-01-14
> **aysiu said:**
> Since the OP isn't using Edgy, I would strongly recommend *against* using *apt-get* in this situation.

Full instructions here (with screenshots):
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)Can someone explain why edgy is different with regards to atp-get meta package handling?

---

### Post by aysiu on 2007-01-14
> **GarethMB said:**
> Can someone explain why edgy is different with regards to atp-get meta package handling?
Edgy has a new option called *autoremove* that allows you to remove unused dependencies along with a package: ```
sudo apt-get autoremove *packagename*
``` Dapper doesn't have this feature.

---

### Post by GarethMB on 2007-01-14
> **aysiu said:**
> Edgy has a new option called *autoremove* that allows you to remove unused dependencies along with a package: ```
sudo apt-get autoremove *packagename*
``` Dapper doesn't have this feature.

Thanks, didn't know about that. I've been using aptitude anyway (good habit).

---

### Post by nandasunu on 2007-01-15
To change your usplash back to the normal ubuntu one (and more), check out Start Up Manager - [http://www.ubuntuforums.org/showthread.php?t=295524](http://www.ubuntuforums.org/showthread.php?t=295524) . It gives an easy graphical way to do it.

---

### Post by Peti29 on 2007-01-15
I wouldn't recommand you to install kubuntu-desktop on your Ubuntu. I've tried that and ended up clearing my partition and installing Ubunto anew.
I wanted to try out KDE but I now think I should've done it by a separate install of Kubuntu. I didn't like all those gnome / KDE applications mixed together in my menus. 'aptitude --purge kubuntu-desktop' freezed and though I managed to make it continue after reboot, some of my icons as well as my splash screen remained KDE-like. My Beryl broke too.
So I chose to reinstall Ubuntu and I don't regret it for it's so much easier than it was the first time and I learn it better by repeating all those configuration steps.

---

