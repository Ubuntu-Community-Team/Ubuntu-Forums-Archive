---
title: "Many Apache Processes"
date: 2012-04-18
forum: Server Platforms
---

### Post by jonedney on 2012-04-18
Hello!

Just wanted to drop a line about what I noticed when I ran 'top', that there seems to be a lot of apache processes on my VPS; is this normal?

```
top - 01:38:30 up  1:47,  1 user,  load average: 1.00, 1.00, 0.99
Tasks:  24 total,   2 running,  22 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.5%us, 17.6%sy,  0.0%ni, 74.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1048576k total,   320936k used,   727640k free,        0k buffers
Swap:        0k total,        0k used,        0k free,        0k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                   
    1 root      25   0 23592 1660 1332 R  100  0.2 107:06.22 init                                                      
 1148 root      15   0 93724 4872 3848 S    0  0.5   0:00.03 smbd                                                      
 1154 root      18   0 63764 2052 1268 S    0  0.2   0:00.12 nmbd                                                      
 1209 root      15   0 49644 2812 2236 S    0  0.3   0:00.00 sshd                                                      
 1256 root      18   0 14796 1132  940 S    0  0.1   0:00.00 xinetd                                                    
 1260 root      15   0 18936 1048  816 S    0  0.1   0:00.01 cron                                                      
 1283 syslog    15   0 12580  856  660 S    0  0.1   0:00.01 syslogd                                                   
 1317 root      18   0 93724 1512  488 S    0  0.1   0:00.00 smbd                                                      
 1419 root      18   0 72244 2524  808 S    0  0.2   0:00.11 sendmail-mta                                              
 1548 root      15   0 73044 3572 2788 S    0  0.3   0:00.14 sshd                                                      
 1560 root      15   0 20092 2096 1584 S    0  0.2   0:00.01 bash                                                      
 4014 root      18   0  130m 8584 3900 S    0  0.8   0:00.02 apache2                                                   
 4018 www-data  15   0  131m 7528 2444 S    0  0.7   0:00.00 apache2                                                   
 4019 www-data  18   0  130m 6424 1672 S    0  0.6   0:00.00 apache2                                                   
 4021 www-data  18   0  130m 6424 1672 S    0  0.6   0:00.00 apache2                                                   
 4022 www-data  18   0  130m 6424 1672 S    0  0.6   0:00.00 apache2                                                   
 4025 www-data  15   0  130m 5260  564 S    0  0.5   0:00.00 apache2                                                   
 4026 www-data  17   0  130m 5260  564 S    0  0.5   0:00.00 apache2                                                   
 4027 www-data  15   0  130m 5260  564 S    0  0.5   0:00.00 apache2                                                   
 4028 www-data  15   0  130m 5260  564 S    0  0.5   0:00.00 apache2                                                   
 4029 www-data  15   0  130m 5260  564 S    0  0.5   0:00.00 apache2                                                   
 4030 www-data  19   0  130m 5260  564 S    0  0.5   0:00.00 apache2                                                   
 7317 mysql     17   0  183m  23m 6816 S    0  2.3   0:00.09 mysqld                                                    
 7386 root      15   0 21288 1364 1088 R    0  0.1   0:00.04 top
```

Thank You,
Jon Edney

---

### Post by SeijiSensei on 2012-04-19
Apache spawns "children" when it starts up.  This enables it to handle many simultaneous requests efficiently.  Most of the memory the children use is shared across all of them.  In the top results you show, you'll see that the RES usage for each child is pretty small, while the shared portion is 130M.  The apache process running with root privileges is the master; the children all run with the restricted privileges of the "www-data" user.

The number of children is controlled by the StartServers directive in apache2.conf.  You can reduce it, but I wouldn't bother given how little they "cost" in terms of memory and performance.  You also have about 700M in free memory, so I wouldn't be too concerned.

---

### Post by jonedney on 2012-04-19
Thank you for that explanation.  Trying to learn as much as I can, and was curious when I checked out the processes on my server if that was normal.

Thank you,
Jon Edney

---

