---
title: "Broken Packages"
date: 2010-06-20
forum: Wine
---

### Post by Bungo Pony on 2010-06-20
Not sure why, but I can't install Wine on a fresh Ubuntu install. I've updated the software sources and I'm still having problems. Here's what I get when I go to install from the terminal:

```
:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages

```

I've also tried to install wine1.2 specifically, and I pretty much get more of the same:

```
~$ sudo apt-get install wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  wine1.2: Depends: libaudio2 but it is not installable
           Recommends: winbind but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not going to be installed
E: Broken packages

```

I also can't install it from synaptic or USC.

---

### Post by Bungo Pony on 2010-06-20
Nevermind, fixed it. There was a problem with the software sources.

---

