---
title: "Need dpkg help - file shows up as corrupt"
date: 2006-10-23
forum: The Cafe
---

### Post by alecjw on 2006-10-23
I've just made my first .deb today, of folding at home. But it doesn't work. When i try to open it with GDebi, it gives me an error that it is corrupt or i don't have access to it, but the access level is 777 or wahtever full RW access to everyone is. I've attached the files which I made the package out of (dir.tar.bz2) and the DEB file (foldingathome_5.02_all.deb.gz (**This is not a GZ file, it's a .deb, but I can't upload .deb files**)) in case anyone wants to see them to check out what's wrong with it. I made it using the command:
```
dpkg -b /path/to/directory/ foldingathome_5.02_all.deb
```

Can anyone help me fix this problem? I've tried running the commmand again a few times in case the file actaully was corrupt but it didn't seem to help.

Thanks.

---

### Post by alecjw on 2006-10-23
Bump...

---

### Post by .t. on 2006-10-23
Errr... I've just been teaching myself about packaging. I'll give this problem a shot.

What method are you using to make the package? checkinstall? Or vanilla dpkg-buildpackage, with your own control/rules/changelog files?

---

### Post by alecjw on 2006-10-23
> **.t. said:**
> Errr... I've just been teaching myself about packaging. I'll give this problem a shot.

What method are you using to make the package? checkinstall? Or vanilla dpkg-buildpackage, with your own control/rules/changelog files?

I used dpkg --build (whihc i think is the same as dpkg-buildpackage, but I'm not sure)

Btw, I've been a Windoze user 1996/7-2006 too (since i was 4/5... how sad) I agree. 10 years is too long.

---

### Post by .t. on 2006-10-23
Try using dpkg-buildpackage... I dunno...

And I'm sad too.

---

### Post by John.Michael.Kane on 2006-10-23
This may offer some help

[**Howto make debian standard debs from scratch**]("http://ubuntuforums.org/showthread.php?t=51003&highlight=howto+build+deb")

---

