---
title: "ssh random timeout error"
date: 2011-01-02
forum: Server Platforms
---

### Post by ssae on 2011-01-02
Happy New Year everyone.

I am having problems connecting to a server (ssh). Basically, the the connection only works part of the time, and then at other times gives me a "connection timed out" error. This seems completely random. Once I log in, I can usually only work for 5-10 mins without problems before the connection drops ("Timeout, server not responding").

The odd thing is that we have other computers in our office with Centos installed that work perfectly fine when connected to the server (I have Ubuntu, of course, while the server is Centos).

Any suggestions would be appreciated.
Thanks!

---

### Post by jgedeon on 2011-01-02
This sounds like a networking issue.  Are you sure that the Server that you are connecting to does not have the same IP as another system.  It sounds like there are two systems competing for the same IP on the network,

---

### Post by yettiman2208 on 2011-01-02
I have a similar problem that is not isolated to ssh. There is no way I can connect or even ping the server in anyway.

And there is no conflict with IP addresses. There are only 2 devices on the network atm. The server, and my Laptop

---

### Post by ssae on 2011-01-02
But in that case would't others also have the same problem? Since I am the only one having that problem in our office I think the problem is with my computer, not the server.

---

### Post by ssae on 2011-01-02
Of course I forgot to mention a detail which may be important... I have an openssh public key authentication set up between my computer and the server.

---

### Post by yettiman2208 on 2011-01-02
true, in my case the server the completely unreachable. By anybody.

---

### Post by ljpaff on 2011-01-08
Hi all,

I'm having the same issue after upgrading my Mediacenter to 2.6.31-22-generic Kernel.

When I send a big file to mediacenter (For example 14GB), after 1.7GB mediacenter network card freezes and my ftp client (SFTP over SSH) too.

At this time if you ping to my mediacenter there is no response, so you have to make a reboot and begin again.

These are upgrade packages from 2011-01-07:


2011-01-07 23:44:06 upgrade dpkg 1.15.4ubuntu2.2 1.15.4ubuntu2.3
2011-01-07 23:44:15 upgrade linux-image-2.6.31-22-generic 2.6.31-22.69 2.6.31-22.70
2011-01-07 23:44:45 upgrade dpkg-dev 1.15.4ubuntu2.2 1.15.4ubuntu2.3
2011-01-07 23:44:46 upgrade linux-headers-2.6.31-22 2.6.31-22.69 2.6.31-22.70
2011-01-07 23:44:52 upgrade linux-headers-2.6.31-22-generic 2.6.31-22.69 2.6.31-22.70
2011-01-07 23:44:55 upgrade linux-libc-dev 2.6.31-22.69 2.6.31-22.70
2011-01-07 23:44:57 upgrade xbmc 2:10.00~svn35567-karmic1 2:10.00~svn35648-karmic1
2011-01-07 23:44:57 upgrade xbmc-skin-confluence 2:10.00~svn35567-karmic1 2:10.00~svn35648-karmic1
2011-01-07 23:44:59 upgrade xbmc-data 2:10.00~svn35567-karmic1 2:10.00~svn35648-karmic1
2011-01-07 23:45:00 upgrade xbmc-bin 2:10.00~svn35567-karmic1 2:10.00~svn35648-karmic1
2011-01-07 23:45:02 upgrade apparmor 2.3.1+1403-0ubuntu27.3 2.3.1+1403-0ubuntu27.4
2011-01-07 23:45:03 upgrade libapparmor1 2.3.1+1403-0ubuntu27.3 2.3.1+1403-0ubuntu27.4
2011-01-07 23:45:03 upgrade libapparmor-perl 2.3.1+1403-0ubuntu27.3 2.3.1+1403-0ubuntu27.4
2011-01-07 23:45:03 upgrade apparmor-utils 2.3.1+1403-0ubuntu27.3 2.3.1+1403-0ubuntu27.4


Best Regards.

---

