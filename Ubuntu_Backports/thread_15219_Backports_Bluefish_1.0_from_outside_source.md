---
title: "Backports: Bluefish 1.0 from outside source"
date: 2005-02-12
forum: Ubuntu Backports
---

### Post by jdong on 2005-02-12
**Synopsis**
Bluefish 1.0 is a major step forward in GNOME web development. We gotta have it.

**Backporting process**
This source package is from a non-Debian source:  [http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish-1.0.tar.bz2](http://pkedu.fbt.eitn.wau.nl/~olivier/downloads/bluefish-1.0.tar.bz2)

Fortunately, it's already debianized by the author.

**Packaging Status**
i386: staging rev 18.
ppc: No maintainer
amd64: No maintainer

**Beta testing notes**
The debianization wasn't done so wonderfully.... There were a few cases of "sandbox violation", but I forced the build to continue as root. Make sure no files are missing from the archive as a result.

---

### Post by jdong on 2005-02-16
Any word on whether or not this works?

---

### Post by ember on 2005-02-16
It works for me and german localisation is far better than in 0.12 - haven't noticed any problems with that version.

---

### Post by kassetra on 2005-02-20
Oh please tell me you're moving it from staging soon.  I need this version to run my happy 1.x bluefish projects, and since it's the app I use to make my income, I can't risk the staging version.  :(
 
 would money help it move faster...?  ;)

---

### Post by crun on 2005-02-20
Works great here. It seems very stable and handles larger php files (+2000 lines) much smoother than previous versions.

---

### Post by jdong on 2005-02-20
I've instructed rufius to promote it. Thanks everyone for your testing.

(I'm recovering from Reiser4+RAID5+LVM-mania..... **REMIND ME NOT TO DO THAT AGAIN**)

---

### Post by kassetra on 2005-02-20
[QUOTE=jdong]I've instructed rufius to promote it. Thanks everyone for your testing.
 
 (I'm recovering from Reiser4+RAID5+LVM-mania..... **REMIND ME NOT TO DO THAT AGAIN**)[/QUOTE]
 
 oh yeah, hey jdong...?
 
 [color=Red]**DON'T DO THAT AGAIN!**[/color]
 
 heh ;)
 
 thank you soooooo much for the backports sir!!

---

### Post by jdong on 2005-02-20
Yay, ext3 + RAID5 Hoary. Nice stable configuration.

Isn't this debootstrapping fun? I can start one while sleeping...

Snore. Snore. Snore. Sudo debootstrap hoary /var/chroot/hoary/2 [http://archive.ubuntu.c.....err......Snore](http://archive.ubuntu.c.....err......Snore). Snore.

---

### Post by jdong on 2005-02-20
P.S. [http://backports.ubuntuforums.org/log.php](http://backports.ubuntuforums.org/log.php)
R57: Bumped to stable.

---

### Post by kassetra on 2005-02-20
snore... LOL
 
 [QUOTE=jdong]P.S. [http://backports.ubuntuforums.org/log.php]("http://backports.ubuntuforums.org/log.php")
 R57: Bumped to stable.[/QUOTE]
 
 awesome possum.  I'll keep that little gem in my favorites...
 I think I upgraded within a few seconds of the bump... :)
 
 THANK YOU!  My projects work again!  WOO!
 my clients will be so happy.  heh.  :)
 
 oh wait, that means I have more work to do... can we bump it back down?  LOL

---

### Post by jnoreiko on 2005-04-05
I've enabled warty backports but synaptic doesn't see any more recent version of bluefish.

Looking through the backports repository, I'm guessing it's because the file is in the wrong place -- see [http://backports.ubuntuforums.org/backports/dists/warty-backports/](http://backports.ubuntuforums.org/backports/dists/warty-backports/) -- shouldn't the deb file be inside one of the sections?

---

### Post by jdong on 2005-04-05
[QUOTE=jnoreiko]I've enabled warty backports but synaptic doesn't see any more recent version of bluefish.

Looking through the backports repository, I'm guessing it's because the file is in the wrong place -- see [http://backports.ubuntuforums.org/backports/dists/warty-backports/](http://backports.ubuntuforums.org/backports/dists/warty-backports/) -- shouldn't the deb file be inside one of the sections?[/QUOTE]
[http://backports.ubuntuforums.org/backports/dists/warty-backports/main/binary-i386/](http://backports.ubuntuforums.org/backports/dists/warty-backports/main/binary-i386/)

Bluefish packages exist in that directory...

---

### Post by jnoreiko on 2005-04-06
I still can't see it I'm afraid.
Both apt-get and synaptic are telling me 0.12 is the most recent version.

I have the line
deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe  
 
in my sources.list and I've run update.

---

### Post by jdong on 2005-04-06
[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

You need to switch the ubuntu-bp.sf.net address overto [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports)

---

### Post by jnoreiko on 2005-04-06
Not that it's going to matter in a few days, but the Unofficial Ubuntu 4.10 Starter Guide has the wrong URL.

EDIT... I was looking at my saved copy. it doesn't seem to have it at all now...

---

### Post by jdong on 2005-04-06
Hmm, I'll have to talk to the guy about including the new Backports....

---

### Post by jdong on 2005-04-19
[QUOTE=jnoreiko]EDIT... I was looking at my saved copy. it doesn't seem to have it at all now...[/QUOTE]

There was the only backports bug ever -- Firefox 1.0 & Java applets crashing... That scared him away from recommending backports. It's too bad. Oh well, at least we've moved on.

---

