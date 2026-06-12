---
title: "ircd-hybrid help"
date: 2008-10-28
forum: Server Platforms
---

### Post by Gannon8 on 2008-10-28
How do I configure ircd-hybrid, and what port does it use, so I can forward it? I tried looking at the man page, telling me to go to a file in the /etc directory, but it does not exist. The configuration file in /etc/ircd-hybrid only has a line that tells it to start the server.

---

### Post by forger on 2008-10-28
1) Ubuntu release? Ubuntu hardy heron? 8.04 or 8.04.1?
Post the output of:
```
lsb_release -a
```
2) the package from the "hardy" release has several files in /etc/:

> 
/etc/default/ircd-hybrid
/etc/init.d/ircd-hybrid
/etc/ircd-hybrid/cresv.conf
/etc/ircd-hybrid/dline.conf
/etc/ircd-hybrid/ircd.conf
/etc/ircd-hybrid/ircd.motd
/etc/ircd-hybrid/kline.conf
/etc/ircd-hybrid/nresv.conf
/etc/ircd-hybrid/rkline.conf
/etc/ircd-hybrid/rxline.conf
/etc/ircd-hybrid/xline.conf
/etc/logrotate.d/ircd-hybrid


the manpage: [http://manpages.ubuntu.com/manpages/hardy/en/man8/ircd-hybrid.html](http://manpages.ubuntu.com/manpages/hardy/en/man8/ircd-hybrid.html)
the filelist: [http://packages.ubuntu.com/hardy/i386/ircd-hybrid/filelist](http://packages.ubuntu.com/hardy/i386/ircd-hybrid/filelist)

note that you have some example files:
> 
/usr/share/doc/ircd-hybrid/examples/example.conf.gz
/usr/share/doc/ircd-hybrid/examples/example.efnet.conf.gz
/usr/share/doc/ircd-hybrid/examples/example_module.c.gz
/usr/share/doc/ircd-hybrid/examples/simple.conf


You can "unpack" them just to see them, e.g.
```
cat /usr/share/doc/ircd-hybrid/examples/example.conf.gz | gunzip
```

---

### Post by forger on 2008-10-28
Hint for the future, lists the files contained in an _installed_ package:
```
dpkg -L ircd-hybrid
```

---

### Post by Gannon8 on 2008-10-28
Thanks for the example. I think I have fixed it.

---

### Post by Gannon8 on 2008-10-29
I see some "connect" options in the config. If this is a standalone server, can I comment them out? I don't really understand what they do...

---

### Post by kennedy7 on 2008-11-17
Ircd-hybrid usually uses 6667 as its connect port. You can set it different in ircd-hybrid line "listen".

---

