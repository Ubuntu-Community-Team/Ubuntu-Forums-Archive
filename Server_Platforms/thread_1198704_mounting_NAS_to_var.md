---
title: "mounting NAS to /var?"
date: 2009-06-27
forum: Server Platforms
---

### Post by wyonate on 2009-06-27
Hello,

I have a question that im sure a lot of people can answer but i cant find much about it. I am planning on running a box with ubuntu installed and using virtualbox set up a centos box to run cpanel for hosting. I have done stuff like this a lot but i have a new way i need to do it. I have a NAS running on a gigabit network that has multiple sets of 2 1tb drives running in raid1. I would like to take one of these sets of drives and mount them to the /var of the centos guest in vitrtualbox. I know some will wonder why i want to do this but it has to do with no wanting to put to many drives in the acutal server box and having my freeNas Nas running flawlessly.

Thanks for any help or ideas, you guys are always a huge help.

:)

---

### Post by HermanAB on 2009-06-27
Well, NFS of course.  It only requires two lines of configuration - one line on the NAS in /etc/exports and one line on your server in /etc/fstab.  Just read the man pages.  It is quite trivial.

---

