---
title: "Migrate fedora core 5 to Ubuntu Server LTS"
date: 2009-10-13
forum: Server Platforms
---

### Post by dnr101 on 2009-10-13
Hi all, I am a High School Comp Sci teacher and I have inherited the care and feeding of our school's web server - an old beast running Fedora core 5. I would like very much to migrate this machine to Ubuntu Server LTS. Will it be possible (aka easy...) to do this and keep the same network configurations and user accounts? Where can I go to get further, possibly step by step instructions on how the process might work for me? I am not exactly a newbie (I've been running Ubuntu desktop off and on since 6.04) but I don't have a whole lot of experience with the ins and outs of server setup, etc. I just know that my out of date Fedora sys has got to go, and I'm much more comfortable with apt than yum (plus I just like Ubuntu better - it's what I run on the desktop machines in my lab...) Any help that anyone can offer would be greatly appreciated (even just a book or website recommendation!)
Thanks,
-Dave

---

### Post by windependence on 2009-10-13
I would recommend going to CentOS instead. The problem you have is that you are going from a Red Hat based distro to a Debian based distro and unfortunately, they are very different. It's not impossible, but you are not going to be able to just do an import like you may be able to with a Red Hat based distro like CentOS. CentOS is an exact copy of RedHat without the RedHat brand.

-Tim

---

### Post by dnr101 on 2009-10-13
Thanks - I'll look into CentOS. Would that leave me with yum still? I've read that it's possible to install and use apt on Red Hat based systems, is that worthwhile or difficult to manage?

---

### Post by bab1 on 2009-10-13
> **dnr101 said:**
> Thanks - I'll look into CentOS. Would that leave me with yum still? I've read that it's possible to install and use apt on Red Hat based systems, is that worthwhile or difficult to manage?

I'm sure the reason Tim suggested CentOS is because of the directory structure and underlying OS libs.  Although yum based Linux is similar to apt based (in that they are Linux) the packaging systems are very different.  You have to first decide which flavor of Linux you want to use.

AFAIK yum only works with RH based systems (SUSE too) and Deb works with Debian/Ubuntu.  There are conversion routines but I would stay away from them.

To my way of thinking, unless you have 100's of users, I would install what I wanted to use and configure from scratch.  The Web content is easily moved.  The network configuration is only about 5 minutes worth of work.  Not really a consideration.

---

