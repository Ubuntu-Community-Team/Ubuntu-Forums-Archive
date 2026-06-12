---
title: "Webmin not respinding"
date: 2009-05-30
forum: Server Platforms
---

### Post by iamroddo on 2009-05-30
I've been running webmin through various installations on Ubuntu including successfully on 9.04. I just noticed that webmin is nolonger responding via the browser on [https://127.0.0.1:10000](https://127.0.0.1:10000) and neither via telnet 127.0.0.1 10000. In both cases there is a connection time out. It had been working fine before.

I think the following means that something is listening on 10000
roliver@sancho:~$ netstat -lnp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      -               

I think that the following means that webmin is running
roliver@sancho:~$ sudo ps aux |grep perl 
roliver   3594  0.0  0.9  51084 30020 ?        Sl   08:02   0:00 /usr/bin/perl -w /usr/bin/checkgmail
root      9785  0.0  0.2  12904  8668 ?        Ss   08:07   0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
roliver  21606  0.0  0.0   3336   788 pts/0    R+   08:18   0:00 grep perl
roliver@sancho:~$ 

I installed webmin via Synaptic. I've tried removing (completely) and adding it back it again. It does this without complaint but to no effect.

---

