---
title: "Will Ubuntu GNOME Edition have 3.10 or 3.8?"
date: 2013-09-26
forum: Ubuntu Development Version
---

### Post by georgelappies on 2013-09-26
Well?

---

### Post by sgage on 2013-09-26
It will have 3.8, but by using the gnome3-next and gnome3-staging ppa's, you can get it to 3.10.

As root, the following commands will take you to 3.10:

```
add-apt-repository ppa:gnome3-team/gnome3-next
add-apt-repository ppa:gnome3-team/gnome3-staging
apt-get update
apt-get dist-upgrade
```

gnome3-next has the relatively stable bits of 3.10 that are ready.
gnome3-staging has potentially less stable bits.
Not all of gnome 3.10 is available yet, but I assume it will be coming along...

---

### Post by grahammechanical on 2013-09-26
I am sorry but I just have to chuckle. :)

Ubuntu Gnome does not, at present, have all the pieces of Gnome 3.8. To get some more bits of Gnome 3.8 we have to install a PPA. To get some (stable) bits of Gnome 3.10 we have to install a second PPA. To get some more but experimental bits of Gnome 3.10 we have to install a third PPA.

[http://ubuntugnome.org/announcement-introducing-gnome3-next-ppa/](http://ubuntugnome.org/announcement-introducing-gnome3-next-ppa/)

This is life at the edge. I recently installed Ubuntu Gnome 13:10 and it installed very well and it is very stable. It looks good. A good job of work is being done here. But I have not added any of the PPAs. 

Regards.

---

### Post by georgelappies on 2013-09-26
Thanks, so actually it would then be best to not add the ppas if one requires a stable day to day box?

---

### Post by su:bhatta on 2013-09-26
Yep, thats a good idea ! I installed and broke a Saucy Gnome by adding those ppa's. But yeah, that was my fault only. I downloaded a 'partial upgrade'.

Thanks to Grahammechanical and not doing that again. Ubuntu Gnome 13.10 is stable and very nice to have.
 In fact i installed 3.11.0-2lowlatency kernel in it along with ubuntustudio-audio package. Never gave a problem with my audio work too!

---

### Post by sgage on 2013-09-26
> **georgelappies said:**
> Thanks, so actually it would then be best to not add the ppas if one requires a stable day to day box?

I had no problems with them, really. I also had no problems in using ppa-purge to roll back to "stock" Saucy :-)  I actually prefer GS 3.8. You could try just 'next' to see if you like 3.10. If not, ppa-purge ppa:gnome3-team/gnome3-next is your friend:KS

---

### Post by slickymaster on 2013-09-26
In case someone's interested in playing around with it: [Install Gnome 3.10 in Saucy]("http://www.webupd8.org/2013/09/how-to-install-gnome-310-in-ubuntu-1310.html?utm_source=chrome&utm_medium=popup&utm_campaign=chromeext")

---

### Post by buzzingrobot on 2013-09-27
I'll probably look at the beta, perhaps stay with it.  Anyone who really requires a bona fide *stable* system, though, ought to avoid any beta release, of pretty much anything. Surprises are always lurking for someone, which is why we have betas. Even a long time after the release, we'll see posts here from someone who got around to upgrading and all of a sudden his favorite Dual Confabulator MindMeld Reddit app won't work. ;)

I make very little use of any of the apps specific to Gnome. In fact, when I add the two or three extensions I always use, I can use any release from 3.4 onward in exactly the same way. What Ubuntu Gnome gives me over, say, Debian Wheezy is the font rendering quality and access to more uptodate applications. The edge over Gnome 3.8 on Fedora 19 with Infinality added is substantially smaller.

---

### Post by kansasnoob on 2013-09-27
> **georgelappies said:**
> Thanks, so actually it would then be best to not add the ppas if one requires a stable day to day box?

That's my opinion after completing Beta 2 iso-testing ;)

I find Ubuntu GNOME to perform quite well out-of-box with only a few tweaks and added packages.

---

### Post by Hazzabin on 2013-09-27
I'm currently running Gnome 13.10 with the 3.10 update ppa's

 When computer has gone into 'lock' mode and then restarting, whatever changes one has made ie: extensions and top panel/taskbar theme (Shell Theme) are NOT retained......have to be re-set each time

Just wondering if anyone else has come up with this minor issue

regards

Hazz

---

### Post by VMC on 2013-09-27
> **grahammechanical said:**
> I am sorry but I just have to chuckle. :)

Ubuntu Gnome does not, at present, have all the pieces of Gnome 3.8. To get some more bits of Gnome 3.8 we have to install a PPA. To get some (stable) bits of Gnome 3.10 we have to install a second PPA. To get some more but experimental bits of Gnome 3.10 we have to install a third PPA.

[http://ubuntugnome.org/announcement-introducing-gnome3-next-ppa/](http://ubuntugnome.org/announcement-introducing-gnome3-next-ppa/)

This is life at the edge. I recently installed Ubuntu Gnome 13:10 and it installed very well and it is very stable. It looks good. A good job of work is being done here. But I have not added any of the PPAs. 

Regards.
I never add ppa's. Some folks want to be on the bleeding edge, I suppose. Also totally agree regarding Ubuntu Gnome. I was presently surprised.

---

### Post by mc4man on 2013-10-01
There i also a chance that 14.04 will basically be 3.8 also, if so that will certainly impact U-G & probably the gnome3 ppa's to some extend.
Obviously way too early to tell but it feels like the Ubuntu preference would be to stick with 3.8

---

### Post by sammiev on 2013-10-01
> **mc4man said:**
> There i also a chance that 14.04 will basically be 3.8 also, if so that will certainly impact U-G & probably the gnome3 ppa's to some extend.
Obviously way too early to tell but it feels like the Ubuntu preference would be to stick with 3.8

Yes it's too early to tell but I hope at least 3.10 will be the default.

---

