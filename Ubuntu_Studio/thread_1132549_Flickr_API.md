---
title: "Flickr API"
date: 2009-04-22
forum: Ubuntu Studio
---

### Post by Ralex1098 on 2009-04-22
Hey all,

After ditching F Spot and its Mono issues, I realized that I can't find another program that automatically uploads my images to Flickr. Does anyone know of a nice reliable photo management program that does this?

I currently use gThumb which works nicely.

---

### Post by lukeiamyourfather on 2009-04-22
Picasa has plugins for uploading to Flickr, not sure if they work in Linux though. Maybe Lightroom in Wine if you have Lightroom?

---

### Post by unutbu on 2009-04-22
This is what "apt-cache search flickr" turned up:

Maybe one of these packages will help:
```
flickcurl-utils - utilities to call the Flickr API from command line
flickrfs - virtual filesystem for flickr online photosharing service
dfo - Desktop Flickr Organizer for GNOME (includes "Easy Drag-n-drop photos from nautilus for uploading.")
kphotobymail - PyQt application for uploading photos to flickr
kflickr - KDE application to upload photos to Flickr
postr - upload photos to Flickr
```

---

### Post by Stochastic on 2009-04-22
And here's what I was able to stumble across:
```
apt-rdepends -r libflickrnet2.1.5-cil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libflickrnet2.1.5-cil
  Reverse Depends: dfo (0.7+svn51-2ubuntu1)
  Reverse Depends: f-spot (0.5.0.3-1ubuntu6)
  Reverse Depends: gnome-do-plugins (0.8.1.3+dfsg-0ubuntu3)
dfo
f-spot
  Reverse Depends: ubuntustudio-graphics (0.52)
ubuntustudio-graphics
gnome-do-plugins

```
This was in a Jaunty system.

I'm really enjoying Gnome Do - though I've never used the flickr upload plugin.

---

