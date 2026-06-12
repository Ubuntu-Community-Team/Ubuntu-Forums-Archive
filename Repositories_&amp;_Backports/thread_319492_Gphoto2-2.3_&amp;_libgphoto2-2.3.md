---
title: "Gphoto2-2.3 &amp; libgphoto2-2.3"
date: 2006-12-15
forum: Repositories &amp; Backports
---

### Post by rpalyvoda on 2006-12-15
Please, backport the newest version of GPhoto, I really need it to be able to use my new Canon Powershot A640 camera!!!:KS

---

### Post by limaunion on 2007-01-02
Yes, please backport this application.

---

### Post by zenzero-2001 on 2007-01-04
I would also very much like this to be back-ported. Then I could ditch openSUSE 10.2 and use my camera with Ubuntu instead.

Debian and Ubuntu forever! :D

---

### Post by mikemain on 2007-01-07
I would like to add my name to this request - just purchsed Canon's EOS 30D and can't wait to get those RAW photos into GIMP

---

### Post by angelsneverdie on 2007-01-07
I don't even know what back porting is, but if it will mean i can use my a640 camera on my ubuntu machine, i'm all for it.

---

### Post by dailer on 2007-01-08
I need it to for my Canon A710 IS. Please Backport it.

---

### Post by bedfojo on 2007-01-13
Yes please, backport to Dapper!

---

### Post by jis on 2007-02-24
> **dailer said:**
> I need it to for my Canon A710 IS. Please Backport it.

I could mount A710 IS's filesystem by Dapper's gphotofs (version 0.1-0ubuntu1 available in universe/utils repository). Do you need something else for your camera?

Unmounting works by umount, but only by root priviledges. Umounting as normal user throws complain that the mount point  "is not in the fstab (and you are not root)". I wonder how you could unmount as normal user.

---

### Post by mlind on 2007-02-26
Hi,
I only had time to backport libgphoto. I'll post links for gphoto tomorrow.

/edit backported gphoto too

gphoto2+libgphoto2 (2.3.1) for edgy
[http://www.freefilehoster.com/uploads/1172613649gphoto2+libphoto2-2.3.1_edgy.tar.gz](http://www.freefilehoster.com/uploads/1172613649gphoto2+libphoto2-2.3.1_edgy.tar.gz)

gphoto2+libgphoto2 (2.3.1) for dapper
[http://www.freefilehoster.com/uploads/1172613986gphoto2+libphoto2-2.3.1_dapper.tar.gz](http://www.freefilehoster.com/uploads/1172613986gphoto2+libphoto2-2.3.1_dapper.tar.gz)

---

### Post by MrPedagogy on 2007-03-01
Ok.

Now I have found the thread I need but how do I use the Edgy Software available. 

I have a Canon Eos30D and I want to load the Images from the Canon into my laptop and have some graphical fun with the Gimp.

Please explain or point me in the right direction on how to do this.

Cheers and thanks in advance.

---

### Post by mlind on 2007-03-01
> **MrPedagogy said:**
> Ok.

Now I have found the thread I need but how do I use the Edgy Software available. 

I have a Canon Eos30D and I want to load the Images from the Canon into my laptop and have some graphical fun with the Gimp.

Please explain or point me in the right direction on how to do this.

Cheers and thanks in advance.

do you mean installing updated packages for edgy or something else?

---

### Post by MrPedagogy on 2007-03-02
> **mlind said:**
> Hi,
I only had time to backport libgphoto. I'll post links for gphoto tomorrow.

/edit backported gphoto too

gphoto2+libgphoto2 (2.3.1) for edgy
[http://www.freefilehoster.com/uploads/1172613649gphoto2+libphoto2-2.3.1_edgy.tar.gz](http://www.freefilehoster.com/uploads/1172613649gphoto2+libphoto2-2.3.1_edgy.tar.gz)

gphoto2+libgphoto2 (2.3.1) for dapper
[http://www.freefilehoster.com/uploads/1172613986gphoto2+libphoto2-2.3.1_dapper.tar.gz](http://www.freefilehoster.com/uploads/1172613986gphoto2+libphoto2-2.3.1_dapper.tar.gz)

Well, I'm hoping either or both of these two programs are what I need to get the images from the Canon 30D onto the laptop. I have downloaded them and extracted each but thats about as far as I know how to go. Don't know how to make them executable.

Cheers.

---

### Post by mlind on 2007-03-02
Create temporary directory "gphoto_new" somewhere, on your desktop for example
Download the edgy .tar.gz archive and extract its contents in the folder you created.

open a terminal and execute
```

cd ~/Desktop/gphoto_new
sudo dpkg -i libgphoto2/libgphoto2-2_2.3.1-2_i386.deb libgphoto2/libgphoto2-port0_2.3.1-2_i386.deb
sudo dpkg -i gphoto2/gphoto2_2.3.1-1_i386.deb

```

these are for i386 arch by the way, don't install if you have other architecture.

---

### Post by larini on 2007-03-10
With my nikon coolpix 880 the error continues:

importing from gthumb:

An error occurred in the io-library ('Error updating the port settings'): Could not release interface 0 (Invalid argument).

version 2.2.1 works.

---

### Post by screening on 2007-05-04
how to backport to 2.2.1? I have too coolpix 880...

---

