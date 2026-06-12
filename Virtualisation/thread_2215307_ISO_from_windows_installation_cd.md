---
title: "ISO from windows installation cd"
date: 2014-04-06
forum: Virtualisation
---

### Post by jcroyle on 2014-04-06
Hello everyone, iam setting up a virtualbox on my ubuntu system and was wondering if anyone knows if its possible and if so how i could get an ISO image off of a windows xp pro sp3 installation CD.  I have the key just cant seem to figure this out any help would be great.  Thank you Jason

---

### Post by ajgreeny on 2014-04-06
Why do you want an iso file when you have the XP CD?  You can use the CD to install XP in VB without any difficulty, as I have already done in order to update my TomTom satnav.

PS:
XP still runs like a one legged donkey; slow, ponderous and horrible to use; I had forgotten how difficult it is to find anything in the windows filesystem!

---

### Post by sikander3786 on 2014-04-06
You can mount that ISO image and use it for installing Windows. A quick Google returned this:

[http://www.ehow.com/how_8202912_mount-iso-virtualbox.html](http://www.ehow.com/how_8202912_mount-iso-virtualbox.html)

---

### Post by ajgreeny on 2014-04-06
> **sikander3786 said:**
> You can mount that ISO image and use it for installing Windows. A quick Google returned this:

[http://www.ehow.com/how_8202912_mount-iso-virtualbox.html](http://www.ehow.com/how_8202912_mount-iso-virtualbox.html)
But the OP doesn't have an ISO image, that was the question; how to get one?

---

### Post by coffeecat on 2014-04-06
> **jcroyle said:**
> and was wondering if anyone knows if its possible and if so how i could get an ISO image off of a windows xp pro sp3 installation CD.  I have the key 

So long as you have a licensed copy and the key and that this is all legal:

You can use Brasero &#8594; Disc copy and choose write to image file.  Or k3b &#8594; tools &#8594; copy medium &#8594; tick the “only create image” box.

---

### Post by sikander3786 on 2014-04-06
> **ajgreeny said:**
> But the OP doesn't have an ISO image, that was the question; how to get one?

Oops. LOL. My bad.

Yep, it won't be a great idea to first convert the installation disk into an ISO image and then use it with VirtualBox. Still, if the OP wants to do it, for saving the ISO for future use or whatever, here are the instructions using Brasero:

[http://askubuntu.com/questions/136165/how-to-create-iso-images](http://askubuntu.com/questions/136165/how-to-create-iso-images)

---

### Post by coffeecat on 2014-04-06
> **sikander3786 said:**
> Still, if the OP wants to do it, for saving the ISO for future use or whatever, here are the instructions using Brasero:

[http://askubuntu.com/questions/136165/how-to-create-iso-images](http://askubuntu.com/questions/136165/how-to-create-iso-images)

Those instructions seem to be for making an ISO of data files using Brasero. I don't think it would work for making a bootable ISO from a bootable CD/DVD. Which is why I suggested using the Disc copy button in Brasero. That does work.

However further down there is a dd command given which should work for creating a bootable ISO.

---

### Post by heiko_s on 2014-04-14
Put your Windows CD in your CDROM/DVD drive and open a terminal, then enter:
```
dd if=/dev/cdrom of=/home/user/winxp.iso
```
where /dev/cdrom or /dev/dvd is the CDROM drive and /home/user/winxp.iso the target ISO file name in your home directory (replace "user" with your name).

if= stands for "input file" (or drive),
of= stands for "output file".

dd is a very powerful command and can do a lot of things, including backups, exact bit-by-bit copies of disks, CDs, or DVDs, or even create or wipe out files or sectors on a disk. Be careful when using it. It's worth reading more about it.

---

### Post by coldraven on 2014-04-15
This article tells you how to download an XP VM directly from Microsoft and run it in VirtualBox.
[http://www.theregister.co.uk/2014/04/10/how_to_run_xp_on_new_windows/](http://www.theregister.co.uk/2014/04/10/how_to_run_xp_on_new_windows/)

To uncompress the archive in Archive Manager you need to have cabextract installed
```
sudo apt-get install cabextract
```

---

