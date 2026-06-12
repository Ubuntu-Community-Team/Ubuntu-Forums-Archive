---
title: "confusing log"
date: 2011-04-29
forum: Server Platforms
---

### Post by wlraider70 on 2011-04-29
when i log onto my server i get this report.

The thing I don't get is why I get two and why do they differ?
Its supposed to be at 10,10,10,[COLOR="Red"]2[/COLOR] I have no idea where 127 comes from?




```

$  ssh -v server@10.10.10.[COLOR="Red"]2[/COLOR]
55-Ubuntu SMP Mon Jan 10 23:57:16 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Fri Apr 29 20:06:43 PDT 2011

  System load:    0.0                Processes:           79
  Usage of /home: 0.0% of 825.04GB   Users logged in:     1
  Memory usage:   17%                IP address for eth0: 10.10.10.[COLOR="Red"]2[/COLOR]
  Swap usage:     0%

  Graph this data and manage this system at https://landscape.canonical.com/

Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Thu Apr 28 09:58:12 PDT 2011

  System load:    0.19               Processes:           71
  Usage of /home: 0.0% of 825.04GB   Users logged in:     1
  Memory usage:   8%                 IP address for eth0: 10.10.10.[COLOR="Yellow"]129[/COLOR]
  Swap usage:     0%

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Fri Apr 29 20:05:39 2011 from 10.10.10.122
server@hyrule:~$ 

```

---

