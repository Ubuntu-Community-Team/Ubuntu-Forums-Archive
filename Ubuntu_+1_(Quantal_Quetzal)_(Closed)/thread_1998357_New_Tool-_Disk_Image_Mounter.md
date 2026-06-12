---
title: "New Tool- Disk Image Mounter?"
date: 2012-06-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-06-06
I just noticed a new tool with qq -alpha1. Does anybody know what this tool can do? I used it to mount an .iso image .. but then, whats next.

---

### Post by williejones on 2012-06-06
> **ventrical said:**
> I just noticed a new tool with qq -alpha1. Does anybody know what this tool can do? I used it to mount an .iso image .. but then, whats next.

Not much help but the man for it can be read by:

```
man gnome-disk-image-mounter
```

I am thinking it is for other packages to use for mounting the iso.

---

### Post by VinDSL on 2012-06-06
> **ventrical said:**
> Does anybody know what this tool can do?

SOURCE: [https://plus.google.com/u/0/110773474140772402317/posts/j82tuhCReBC](https://plus.google.com/u/0/110773474140772402317/posts/j82tuhCReBC)
> Finally got around to writing a small Disk Image Mounter application for GNOME so **[COLOR="Sienna"]something sensible happens when you click an ISO file[/COLOR]** ... it's pretty cute, you can also select a bunch of ISO files and it mounts all of them. And when you click the eject icon in Nautilus, the disk image is unmounted and the loop device goes away.

SOURCE:  [http://git.gnome.org/browse/gnome-disk-utility/commit/?id=2794ee121829d656d460da58c0ecaa84271e6fe7](http://git.gnome.org/browse/gnome-disk-utility/commit/?id=2794ee121829d656d460da58c0ecaa84271e6fe7)
> **Add "Disk Image Mounter" utility and associate with application/x-cd-image**

The MINE association makes the utility show up in Nautilus for .iso
files... basically, if you open an ISO file (or even a selection of
multiple ISO files) with this tool through Nautilus the right thing
happens... that is, for each ISO file, a loop device is created and
its filesystem is mounted. This results in a set of GVolume/GMount
objects in Nautilus' sidebar and the shell will run its sniffing
machinery and ask if you want to **[COLOR="Sienna"]e.g. watch the DVD movie[/COLOR]**.

Additionally, the loop.autoclear option is used so the loop device
goes away when the loop device is unmounted.

Signed-off-by: David Zeuthen <davidz@redhat.com>


---

### Post by madverb on 2012-06-07
Nice!

---

### Post by ventrical on 2012-06-07
> **VinDSL said:**
> SOURCE: [https://plus.google.com/u/0/110773474140772402317/posts/j82tuhCReBC](https://plus.google.com/u/0/110773474140772402317/posts/j82tuhCReBC)


SOURCE:  [http://git.gnome.org/browse/gnome-disk-utility/commit/?id=2794ee121829d656d460da58c0ecaa84271e6fe7](http://git.gnome.org/browse/gnome-disk-utility/commit/?id=2794ee121829d656d460da58c0ecaa84271e6fe7)


Ahhhh .. capice! :)

Thanks.

---

