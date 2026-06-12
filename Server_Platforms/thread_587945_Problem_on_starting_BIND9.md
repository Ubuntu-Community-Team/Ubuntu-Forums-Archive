---
title: "Problem on starting BIND9"
date: 2007-10-23
forum: Server Platforms
---

### Post by satimis on 2007-10-23
Hi folks,

Ubuntu 7.04 server amd64 (Host OS)
bind9
VMWare.


On running;
$ sudo /etc/init.d/bind9 start```

 * Starting domain name service... bind                                                                                           [fail] 

```

$ ps aux|grep -i named```

bind      4477  0.0  0.1  70728  3608 ?        Ssl  02:05   0:00 /usr/sbin/named -u bind
root      5488  0.0  0.0  10084   776 ?        Ss   02:48   0:00 /sbin/syslogd -a /var/lib/named/dev/log
satimis   5601  0.0  0.0   5028   888 pts/0    S+   03:09   0:00 grep -i named

```

Please advise where shall I check and how to fix the problem.  TIA


Edit:

Problem solved after reboot


B.R.
satimis

---

