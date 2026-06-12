---
title: "glassfish startup on boot"
date: 2008-09-20
forum: Server Platforms
---

### Post by nicolasdiogo on 2008-09-20
hi folks,


i am trying to find a way starting glassfish on boot.
by searching, i noticed that there is no /etc/init.d/glassfish

and that glassfish starts as root.

maybe someone has already done this and would be kind enough to share it here.

i suppose i am looking for a script to startup glassfish on boot and some way of running it on a non-privileged account, which would imply in creating an account for glassfish.

hope to hear from you folks,

Thanks

Nicolas

---

### Post by siju04112001 on 2008-09-20
Hi,

you can find a good tutorial with a startup script which starts glassfish with a non privileged user here :
[http://computingwithjasper.blogspot.com/2008/01/installing-glassfish-2-on-ubuntu-710.html]("http://computingwithjasper.blogspot.com/2008/01/installing-glassfish-2-on-ubuntu-710.html")

---

### Post by nicolasdiogo on 2008-09-23
thanks for your reply,

but it now have two question:

since we are creating a glassfish user with it own home directory (/opt/glassfish)

how is that starting the process with root privilegies - how is that it is less of a risk running it?

if i have to download another version of glassfish from sun - could we not achieve similar thing by using the package avaialble from ubuntu?

thanks a lot,


Nicolas

---

