---
title: "Disable thttpd autostart"
date: 2005-11-19
forum: Server Platforms
---

### Post by stoffe on 2005-11-19
Hello!

I have installed thttpd via aptitude but now it autostarts when I boot the computer. Not really running the computer as a server, just think that thttpd is handy now and then, especially when started from commandline for specific tasks. I also want to use Apache on a non-regular basis, and it'd be easier if they could both use port 80 depending on which I use at the moment.

Apache, Mysql and lots of others show up in the Services menu, thttpd does not - what is the preferred way to tell Ubuntu to not start the service but otherwise keep it handy? Would it be possible to show it in the Services menu somehow?

---

### Post by yoyoned on 2005-11-19
[http://www.ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf](http://www.ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf)

---

### Post by stoffe on 2005-11-19
Thanks, looks like a good enough solution. :)

---

