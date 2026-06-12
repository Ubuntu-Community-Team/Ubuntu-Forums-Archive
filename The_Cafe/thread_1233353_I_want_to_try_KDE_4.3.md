---
title: "I want to try KDE 4.3"
date: 2009-08-06
forum: The Cafe
---

### Post by windows-killer on 2009-08-06
I want to try KDE 4, but I dont know if its on the repos.
When I search for KDE 4 desktop, I get version KDE- 5:48ubuntu1. what version is that? Sometimes I get version 4.2.2. If I install a previous version of KDE, will update manager update it to the current version? 

Does anyone know an easier way? a .deb would be awesome!

---

### Post by Screwdriver0815 on 2009-08-06
you have to add the following to your software sources

```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
```

after that type into the terminal: 

```
sudo apt-get update
```

and then you can install KDE 4.3 via Synaptic.

If you already use KDE you can run 

```
sudo apt-get dist-upgrade
```

after you have added the ppa to your sources

---

### Post by Ericj1186 on 2009-08-06
How would I go about switching between Gnome and KDE?  I don't want to mess anything up.

---

### Post by Skripka on 2009-08-06
> **Screwdriver0815 said:**
> you have to add the following to your software sources

```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
```

after that type into the terminal: 

```
sudo apt-get update
```

and then you can install KDE 4.3 via Synaptic.

If you already use KDE you can run 

```
sudo apt-get dist-upgrade
```

after you have added the ppa to your sources



Bingo.  Due to Ubuntu/Debian's policy regarding post-freeze software, you will not be able to get KDE4.3 from an official Ubuntu stable repo until 9.10...until then you have to get it from a backport PPA

---

### Post by Tibuda on 2009-08-06
After you add an entry to the software sources, it will ask you to update it, so you don't have to "sudo apt-get update" if you have used the GUI.

---

### Post by DeadSuperHero on 2009-08-06
Alternatively, I've found it's much faster on the latest Karmic Alpha. So, if you want to try bleeding edge and possibly deal with a bug here and there, I've found it's actually a really smooth experience.

Good stuff all around.

---

### Post by windows-killer on 2009-08-06
> **Skripka said:**
> Bingo.  Due to Ubuntu/Debian's policy regarding post-freeze software, you will not be able to get KDE4.3 from an official Ubuntu stable repo until 9.10...until then you have to get it from a backport PPA

so you mean I am downloading an RC version right now?

---

### Post by windows-killer on 2009-08-06
> **danielrmt said:**
> After you add an entry to the software sources, it will ask you to update it, so you don't have to "sudo apt-get update" if you have used the GUI.

Thanks!

---

### Post by Skripka on 2009-08-06
> **windows-killer said:**
> so you mean I am downloading an RC version right now?

No what I mean is-you're using a full KDE4.3 final--but the packages are only supported and available through unofficial backports.

---

### Post by windows-killer on 2009-08-06
> **Skripka said:**
> No what I mean is-you're using a full KDE4.3 final--but the packages are only supported and available through unofficial backports.

Makes sense now [COLOR="Yellow"][SIZE="4"]:D[/SIZE][/COLOR]

---

### Post by windows-killer on 2009-08-06
> **Screwdriver0815 said:**
> you have to add the following to your software sources

```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
```

after that type into the terminal: 

```
sudo apt-get update
```

and then you can install KDE 4.3 via Synaptic.

If you already use KDE you can run 

```
sudo apt-get dist-upgrade
```

after you have added the ppa to your sources

I followed another set of instructions from the kubuntu/KDE site the only different thing was, that I had to enter the GPG key.

---

