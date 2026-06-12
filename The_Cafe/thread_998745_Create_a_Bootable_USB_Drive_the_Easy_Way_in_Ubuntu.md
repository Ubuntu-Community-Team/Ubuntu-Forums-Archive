---
title: "Create a Bootable USB Drive the Easy Way in Ubuntu 8.10"
date: 2008-12-01
forum: The Cafe
---

### Post by sharks on 2008-12-01
Create a Bootable USB Drive the Easy Way in Ubuntu 8.10
[http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/](http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/)

---

### Post by kernelhaxor on 2008-12-01
Yeah, that was one of the most advertised features of 8.10

---

### Post by Corfy on 2008-12-01
Does that tool only work with *buntu ISOs, or will it work with any ISO for a bootable disc? Or does anyone know.

I don't know how that program works, so I don't know if it only works with Ubuntu ISOs, or if I can use, say, the ISO from SystemRescueCD.

It would be great if it worked for any ISO, but I certainly would understand if it only worked with ones from *buntu.

---

### Post by kevin11951 on 2008-12-01
> **Corfy said:**
> Does that tool only work with *buntu ISOs, or will it work with any ISO for a bootable disc? Or does anyone know.

I don't know how that program works, so I don't know if it only works with Ubuntu ISOs, or if I can use, say, the ISO from SystemRescueCD.

It would be great if it worked for any ISO, but I certainly would understand if it only worked with ones from *buntu.

only *buntu, not even debian will work with this.  ive tested it, and it works with gos, ubuntu, xubuntu, but not debian, open suse, or fedora, or windows xp (dont ask).

---

### Post by kernelhaxor on 2008-12-02
Kubuntu 8.10 doesn't hav this feature right?

---

### Post by Corfy on 2008-12-02
> **kernelhaxor said:**
> Kubuntu 8.10 doesn't hav this feature right?

I was about to say "Yes, it does", because I used it in Kubuntu to create a USB key.

But then I remembered that I also have ubuntu-desktop installed, so it may not come by default with Kubuntu. I don't know about that off hand, and I'm not in position to check.

Still, I'm sure it can be added through the repositories. I just don't know what the package is called off hand.

---

### Post by geoken on 2008-12-02
Does this create a separate partition on the USB drive, leaving the rest of the drive alone (i.e. as a FAT32 partition)

---

### Post by kevin11951 on 2008-12-02
> **geoken said:**
> Does this create a separate partition on the USB drive, leaving the rest of the drive alone (i.e. as a FAT32 partition)

its up to you, if you partition it that way, it will work, other wise, it will just add on top.

---

### Post by earthpigg on 2008-12-02
confirmed, it did not work with Puppy Linux :(

(although puppy live cd does let you do this, i wanted to save myself the hassle of burning a cd-rw just to make a bootable thumb drive...)

---

### Post by billgoldberg on 2008-12-02
I tried that tool in intrepid but it would not "install" to my external hdd (actually, it didn't find the drive).

Unetbootin did do the job, in a minute or so.

---

### Post by billgoldberg on 2008-12-02
I tried that tool in intrepid but it would "install" to my external hdd.

Unetbootin did do the job, in a minute or so.

--

For those that didn't know it, you need to use the first partition on your hard drive, flash drive, ... and using gparted, give it a boot flag.

When that is done, open unetbootin, point it to the iso you downloaded, and select the partition.

It won't take long for it to finish.

---

### Post by cmay on 2008-12-02
i used to create a usb stick with the ubuntu eee image and the eeebuntu image. i got a asus Eeepc just now so i am going to install from one of these usb stick anytime soon. the live cd works perfect. i also created a debian usb setup stick but as the installer on the stick wants to load a cd it cant be used as anything other than a boot devise for installing. i have tried ohter distros and minix. but that does not work. pendrive linux has instruktions for many things including how to use this usb creator. format with fat32 and it should work. at least it does here.
 (i cant find my debian live cd  but if that works.......oh joy)

---

