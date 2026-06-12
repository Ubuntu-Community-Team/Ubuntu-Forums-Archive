---
title: "Installing BIND9 and ???"
date: 2010-02-09
forum: Server Platforms
---

### Post by wgregori on 2010-02-09
I've got bind9 up and running using the ubuntu [howto ]("https://help.ubuntu.com/community/BIND9ServerHowto").  But there is a reference to "syslod" that I don't understand.  The file /etc/init.d/sysklogd does not exist... is there a package that I haven't installed?

I'm running ubuntu server 9.10.

Thanks,
Wayne

---

### Post by adam814 on 2010-02-09
Ubuntu doesn't use sysklogd by default.  It uses rsyslog.  I suppose you could run "sudo /etc/init.d/rsyslog restart", but I don't think it's really necessary.

---

### Post by kiranmurari on 2010-02-09
Hi,
   You need to install the sysklogd package.
```
$ sudo apt-get install sysklogd
```      For more info on this package, see: [http://packages.ubuntu.com/karmic/sysklogd](http://packages.ubuntu.com/karmic/sysklogd)
   
Hope this helps.

---

