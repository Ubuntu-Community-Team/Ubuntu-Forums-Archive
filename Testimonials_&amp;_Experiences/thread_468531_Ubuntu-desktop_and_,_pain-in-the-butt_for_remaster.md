---
title: "Ubuntu-desktop and , pain-in-the-butt for remastering..."
date: 2007-06-08
forum: Testimonials &amp; Experiences
---

### Post by smartboyathome on 2007-06-08
I am trying to remaster my ubuntu system (partially because FVWM-Crystal is supported here better than debian) and I found out I can't un-install any of the default packages. I tried uninstalling serpentine, but it is tied in with ubuntu-desktop. Same with Xterm. I would think that FVWM-Crystal/Ubuntu would be able to run without these, but I guess they can't. I guess they will sit there (though I would like to get rid of them both). Still, ubuntu shouldn't tie their desktop in with programs, as someone who MIGHT want to get rid of one won't. I would be happy with the debian desktop, but I can't get it on here. >.<

---

### Post by pawitp on 2007-06-09
Remove ubuntu-desktop, it's gonna be OK. The ubuntu-desktop is a meta-package that install alls the default package. So when a default package is removed, the ubuntu-desktop won't  be there anymore. But there exists a problem with auto-removing all the applications which can be cured by manually apt-get installing the files.

---

