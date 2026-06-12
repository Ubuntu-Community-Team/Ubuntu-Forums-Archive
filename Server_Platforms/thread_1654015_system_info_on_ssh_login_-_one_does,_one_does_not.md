---
title: "system info on ssh login - one does, one does not"
date: 2010-12-27
forum: Server Platforms
---

### Post by bobwdn on 2010-12-27
I have two 10.04.1LTS command line servers running different overall jobs. One is an upgrade that started as 9.10 and was upgraded to 10.04LTS when it came out. It has since been upgraded to a 10.04.1LTS server. It's ssh login displays the following:
```
bob@b-desktp:~$ ssh admin@192.168.0.153
admin@192.168.0.153's password: 
Linux server.nnbob.net 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

No mail.
Last login: Mon Dec 27 16:33:51 2010 from bob-desktp.nnbob.net
```

My newer 10.04.1LTS server ssh login displays:
```
bob@b-desktp:~$ ssh admin@192.168.0.151
admin@192.168.0.151's password: 
Linux bckppc.nnbob.net 2.6.32-27-generic-pae #49-Ubuntu SMP Thu Dec 2 00:07:52 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

  System information as of Mon Dec 27 17:18:52 CST 2010

  System load:  0.0               Processes:           98
  Usage of /:   11.8% of 2.54GB   Users logged in:     0
  Memory usage: 8%                IP address for eth0: 192.168.0.151
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

No mail.
Last login: Mon Dec 27 17:00:10 2010 from b-desktp.nnbob.net
```

Notice the nice system information presented there. How do I get the other (upgraded) server to do that too?

---

### Post by bobwdn on 2010-12-31
Um-m-m-m, anybody? ):P

---

### Post by elico on 2011-01-07
[INDENT]check the /etc/motd file

and this
[http://www.ubuntugeek.com/how-to-change-message-of-the-day-motd-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-change-message-of-the-day-motd-in-ubuntu-server.html)
 [/INDENT]

---

### Post by bobwdn on 2011-01-07
Thanks, elico.

I installed this and it didn't quite create the same output as the 'newer' computer but, I will not have time to compare some of the configuration files between the two computers until Sunday evening. So, I'll try that then and post any needed results here.

---

### Post by CharlesA on 2011-01-07
That MOTD is called from landscape-sysinfo.

It's part of landscape-common.

You can see if it's installed by running this:
```
charles@thor:~$ dpkg -l | grep landscape
ii  landscape-common                1.5.5.1-0ubuntu0.10.04.0                        The Landscape administration system client

```

---

### Post by bobwdn on 2011-01-08
Thanks, CharlesA. That was it!!

---

### Post by CharlesA on 2011-01-08
Glad you got it sorted. :)

You can mark the thread as solved from thread tools.

---

