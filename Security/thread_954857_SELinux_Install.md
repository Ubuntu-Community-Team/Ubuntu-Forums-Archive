---
title: "SELinux Install"
date: 2008-10-21
forum: Security
---

### Post by toasty_ghosty on 2008-10-21
Hello

I am trying to go for the fix it till its broke approach and have wandered on to SELinux. I have used it before without really knowing what all it was. I am thinking about installing it in Ubuntu though. Before I do I have a few questions:

1. I have read that installing SELinux and cause system instability. How true is this?

2. While I have read the installation is difficult, SELinux can now be apt-get'ed so that shouldn't be too hard...

Lastly, if it helps I am running 64-bit 8.04.

Thanks.

---

### Post by cariboo on 2008-10-21
If you are intent on installing SELinux make sure you completely remove Apparmor first or you may end up with an unusable system. Remember SELinux was designed by the CIA so take it from there.

Jim

---

### Post by toasty_ghosty on 2008-10-21
Thanks for the reply. I got the how to if there is enough there to count as one from here:

[http://ubuntu-tutorials.com/2008/03/18/how-to-install-selinux-on-ubuntu-804-hardy-heron/](http://ubuntu-tutorials.com/2008/03/18/how-to-install-selinux-on-ubuntu-804-hardy-heron/)

Also, AppArmor is a module so I would disable that and enable SELinux in the kernel correct?

I guess my question would be is it worth it? And could you clarify this:

> Remember SELinux was designed by the CIA so take it from there.

Thanks.

---

### Post by cariboo on 2008-10-22
You might want to have a look at this thread:

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6008759](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6008759)

There is a bit of flaming going here and there, but there is some good solid info too.

Jim

---

