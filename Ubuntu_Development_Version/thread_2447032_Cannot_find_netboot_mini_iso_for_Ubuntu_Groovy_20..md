---
title: "Cannot find netboot mini iso for Ubuntu Groovy 20.10"
date: 2020-07-11
forum: Ubuntu Development Version
---

### Post by jagsdesai on 2020-07-11
hi guys,
there used to be mini iso (around 75-80 MB) available for development version of Ubuntu (which used to be updated once a month or so) from a link similar to this:
```
http://archive.ubuntu.com/ubuntu/dists/eoan/main/installer-amd64/current/images/netboot/
```

Now all I could find is this page:
```
http://cdimage.ubuntu.com/netboot/focal/
```

that asks to try "new Ubuntu Server installer":

```
https://ubuntu.com/download/server
```

but there's link for Focal 20.04 only, and I cannot find any link for Groovy 20.10. By the way, I'm trying to install development version of Ubuntu MATE 20.10 using netboot / mini iso. Any help is greatly appreciated.

---

### Post by sudodus on 2020-07-11
There will be no mini.iso of Groovy, to be released as Ubuntu 20.10, and future versions.

---

### Post by jagsdesai on 2020-07-11
> **sudodus said:**
> There will be no mini.iso of Groovy, to be released as Ubuntu 20.10, and future versions.

Many thanks for the reply. 

What about the "[COLOR=#E8E6E3][/COLOR]new Ubuntu Server installer" at ```
[FONT=&amp]https://ubuntu.com/download/server[/FONT]
```
Any ETA for Ubuntu Groovy 20.10 Server ISO there?
[COLOR=#E8E6E3]

[/COLOR]

---

### Post by ajgreeny on 2020-07-11
Focal seems to be the final mini.iso that will be available [http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso)

Perhaps you could install that and move to groovy by editing the /etc/sources.list file manually.

I've never done that in Ubuntu, but it certainly works fine in a basic Debian install where I've moved from buster, Debian 10 Stable, to bullseye, Debian 10 Testing.

Maybe worth a try, perhaps in a virtual install, just to see if it's a feasible move.

---

### Post by jagsdesai on 2020-07-11
> **ajgreeny said:**
> Focal seems to be the final mini.iso that will be available [http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso)

Perhaps you could install that and move to groovy by editing the /etc/sources.list file manually.

I've never done that in Ubuntu, but it certainly works fine in a basic Debian install where I've moved from buster, Debian 10 Stable, to bullseye, Debian 10 Testing.

Maybe worth a try, perhaps in a virtual install, just to see if it's a feasible move.

Many thanks for the reply. 

If Ubuntu decided to make the mini.iso not available going forward, I guess that is it.

But what about the "new Ubuntu Server installer" at

```
https://ubuntu.com/download/server
```
Any ETA for Ubuntu Groovy 20.10 Server ISO there?

---

### Post by sudodus on 2020-07-12
There is a link to the Ubuntu Server Groovy iso file at the iso testing tracker: [Download links for Ubuntu Server Subiquity amd64](http://iso.qa.ubuntu.com/qatracker/milestones/413/builds/216719/downloads) and we can expect it will be released as 20.10 in October.

---

### Post by jagsdesai on 2020-07-12
> **sudodus said:**
> There is a link to the Ubuntu Server Groovy iso file at the iso testing tracker: [Download links for Ubuntu Server Subiquity amd64]("http://iso.qa.ubuntu.com/qatracker/milestones/413/builds/216719/downloads") and we can expect it will be released as 20.10 in October.

Thanks alot :)

This is what I was looking for: ```
http://iso.qa.ubuntu.com/qatracker/milestones/413/builds/216719/downloads
```

---

