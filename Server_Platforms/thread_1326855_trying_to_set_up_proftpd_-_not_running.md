---
title: "trying to set up proftpd - not running"
date: 2009-11-14
forum: Server Platforms
---

### Post by hendrixj on 2009-11-14
I've installed proftpd. Tried to /etc/init.d/proftpd and it says
   ProFTPd is started from inetd/xinetd

Looked this up, and see that xinetd is supposed to start it when someone does an ftp request on port 21. (Though the config file says servertype inetd)

But i still get "Can't connect to ... Connection refused."

The log files in /var/log/proftpd are empty

I saw some suggest typing: sudo dpkg-reconfigure proftpd
I assume this should allow me to change configuration settings, but nothing happens when I type it.

I thought of reconfiguring to standalone, but not even completely removing and reinstalling is giving me a chance to choose standalone again.

xinetd seems like the best choice because I don't expect to need it often.

Any help will be appreciated.

---

### Post by Vegan on 2009-11-14
I use VSFTPD and it works. VS is the popular choice for Ubuntu.

---

