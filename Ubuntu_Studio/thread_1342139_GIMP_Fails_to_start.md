---
title: "GIMP Fails to start"
date: 2009-11-30
forum: Ubuntu Studio
---

### Post by ElSlunko on 2009-11-30
Looks like GIMP heard me supporting it's removal from Lucid and it borked itself! Well maybe I borked it.

Anyways, I can't think of why it would have just stopped working. It used to work and the only thing I can think of that was installed between it working and not working has been Picasa and PicasaPhotoViewer. I've tried purging all files related to Picasa and GIMP. I've also removed 2.7 and installed 2.6 and still get the same error... which is :

```
gimp: symbol lookup error: /usr/lib/libgegl-0.1.so.0: undefined symbol: babl_total_usecs
```

Info:
Karmic Koala 9.10
Gimp 2.7 Testing Version

---

### Post by ov1d1u on 2009-11-30
Yep, same problem here.

Distro: Ubuntu Karmic Koala
Gimp version: 2.7.3-2009112001~kk

---

### Post by ElSlunko on 2009-11-30
Did you install or have any updates that may have caused it to stop working?

---

### Post by jamjamjam on 2009-11-30
The problem certainly comes from the updates I made today : Gimp was working yesterday night. I started my computer this evening, updated via system administration and then GIMP produced the related error.

---

### Post by theirishkiwi on 2009-11-30
Hi 

I believe it was caused by the upgrade of libgegl, that or when I installed Cinepaint?

I forced version for libgegl back to ppm version after upgrade installed ubuntu version, but still same error message when opening gimp in terminal.

I think I might purge everything again.

Distro: Ubuntu Karmic Koala
Gimp version: 2.7.3-2009112001~kk

---

### Post by ElSlunko on 2009-11-30
Let us know how that works out. I won't have access to my Ubuntu machine for a while so I won't be able to report back 'till later tonight.

---

### Post by Prominence on 2009-11-30
I'm having the same issue

---

### Post by theirishkiwi on 2009-11-30
So, I uninstalled gimp, purged all related files and downloaded gimp from scratch. But still the same error message!

---

### Post by theirishkiwi on 2009-11-30
matthaeus123 has just updated his PPA version of libgegl to libgegl - 0.1.1-2009113001~kk.

[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+packages](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn/+packages)

This solved the problem with Gimp not starting, for me.

So, reload APT or your package manager and upgrade packages to latest versions, making sure you have forced version of libgegl to gegl - 0.1.1-2009113001~kk, or what ever version you have installed (ppa version) before upgrading. You should be up and running again, hopefully. 

To force version select package (libgegl) in Synaptic Package Manager, right-click and click on properties, under versions tab you'll see there are two versions installed. Follow instructions at bottom if this window to force version.

Between forcing version and upgrading to gegl - 0.1.1-2009113001~kk, I did end up uninstalling gimp and purging all files etc. So if upgrade fails to solve problem, maybe try doing a completely clean install after purging all related files.

Cheers

---

### Post by ElSlunko on 2009-12-01
Update tonight fixed it! :)

---

### Post by boombox1387 on 2009-12-01
Same thing here.  I started up my computer this morning and Gimp refused to start.  I just got updates to gegl and libgegl, and now everything is awesome again.

---

### Post by jamjamjam on 2009-12-01
Yes, with today updates, GIMP works again.
Best regards

---

