---
title: "Unistalled SSH"
date: 2012-05-27
forum: Server Platforms
---

### Post by FracOMac on 2012-05-27
Long story short, I accidentally uninstalled some packages on my server, ssh being one of them.  Now I can't access my server while it is running to repair my damage.  I'm using Amazon EC2 so it was relatively easy to start up another instance and mount the drive on it, but I need to know what to do to manually install ssh so that I can start the server back up and ssh in to fix it.

Thanks for any help in advance.

---

### Post by CharlesA on 2012-05-27
you would have to chroom into the previous install and install ssh on it.

[http://en.gentoo-wiki.com/wiki/Chroot_from_a_livecd](http://en.gentoo-wiki.com/wiki/Chroot_from_a_livecd)

It would probably be easier to deal with from a livecd but it should work from another install.

---

### Post by FracOMac on 2012-05-27
Thanks, reinstalled the ssh server with that.  Now however, I'm having all sorts off issues after booting the server back up.  Most visible one atm is that the webserver is letting the files be downloaded instead of executing the php files.

EDIT: Nvm, all working now, many thanks!

---

