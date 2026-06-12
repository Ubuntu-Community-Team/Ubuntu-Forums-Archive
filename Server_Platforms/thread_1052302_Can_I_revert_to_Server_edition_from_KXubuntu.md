---
title: "Can I revert to Server edition from K/Xubuntu"
date: 2009-01-27
forum: Server Platforms
---

### Post by orionMX on 2009-01-27
Initially installed Xubuntu, then wished to  experience the KDE 4.2 desktop for the heck of it.  The main goal though was to use this as a development server box.  My mistake was to load all my server, app server, mysql, and development IDE, before realizing that I wanted to remove most gui stuff.  What should i remove and how, to go from kubuntu to server version.

thanks

---

### Post by Coreigh on 2009-01-27
```
sudo apt-get -s remove kubuntu-desktop
```

This will show you what is going to be done (its the -s that tells apt to do a practice run.) You can then read through and see if removing kubuntu will affect anything you want to keep. Mave a note of these (if any) and re-install them after kubuntu is gone.

I always run the "apt-get -s" option before adding or removing packages. I have burned myself too many times losing stuff I wanted to keep or overloading my system with stuff I don't want.

---

### Post by benblout on 2009-02-27
> **Coreigh said:**
> ```
sudo apt-get -s remove kubuntu-desktop
```
I don't think this is the correct answer.  Imagine, after the initial install (server edition) a package was added that is not part of kubuntu-desktop.  Removing kubuntu-desktop would not remove the additional package.

---

### Post by Iowan on 2009-02-27
For the sake of clarity, how was the server set up - in what order (using what package manager) were (what) things added?

---

