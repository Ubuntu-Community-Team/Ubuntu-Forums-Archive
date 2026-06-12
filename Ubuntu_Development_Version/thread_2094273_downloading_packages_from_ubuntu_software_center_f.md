---
title: "downloading packages from ubuntu software center for offline use (possible?)"
date: 2012-12-13
forum: Ubuntu Development Version
---

### Post by nomenkultur on 2012-12-13
Hi,


 so I'm running the alphas from ubuntu 13.04

[http://www.youtube.com/watch?v=qNxrP3BI_DE](http://www.youtube.com/watch?v=qNxrP3BI_DE)

 and I'm liking them... I will whoever not be installing alpha software so it's painful to have to go to the ubuntu software center to download a bunch of stuff everytime you want to have a live session.

 My question:

 Is it at all possible to download packages from the software center and save them in the hard drive and then install them offline

 if so how should I do it?

 I tried looking for answers online but all I could find is for instance a .deb for some stuff but it seems much smaller than the one in the s.c.


 ...

 also while I have your attention, how come I can download chromium 24 on elementary os (12.04) and when using the same console codes it downloads me chromium 22 instead in ubuntu 13.04

---

### Post by dino99 on 2012-12-13
as the package manager only own the list of the available packages, but not the packages, you need of course to be linked to the net for downloading. The other way is to get the full iso but then if you want the latest fixes/upgrades, the network is required (seems evident)

---

### Post by howefield on 2012-12-13
Thread moved to Raring forum.

---

### Post by nomenkultur on 2012-12-13
"you need of course to be linked to the net for downloading"


 yes but is there a way to, when downloading the files, to direct them to another directory or save them somewhere in order for the next time being able to install them without a network connection?

---

### Post by howefield on 2012-12-13
The .deb files you download are saved to the /var/cache/apt/archives folder.

You can copy them elsewhere for future use, but many of them will be regularly updated, 13.04 being a development release.

---

### Post by nomenkultur on 2012-12-13
thanks that's what I wanted to know

 so all I have to do is save those files to a hard drive and next time I want to run a live session I should be able to double click them and install or I have to point to them with the console?

 edit: nope doesn't work, when double clicking it open the software center but 'install' is shaded and it tells me to only download from normal software channels

---

### Post by dino99 on 2012-12-13
to install a package, from /var/cache/apt/archives :

```
sudo dpkg -i thepackage2install.deb
```

---

### Post by cariboo on 2012-12-13
Synaptic also allows you to download packages without installing them.

---

