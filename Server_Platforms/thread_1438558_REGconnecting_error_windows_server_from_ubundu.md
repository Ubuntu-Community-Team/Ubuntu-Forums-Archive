---
title: "REG:connecting error windows server from ubundu"
date: 2010-03-25
forum: Server Platforms
---

### Post by vaskbtech on 2010-03-25
Hi,
When i connect windows server 2003 from ubuntu these error displayed .

[FONT=Verdana]When i installing the tsclient, by executing these following command from a Terminal window:[/FONT]
 [FONT=Verdana]*sudo apt-get install tsclient*[/FONT]


[FONT=Verdana][I]When i run these command the following error displayed.
[/I][/FONT]

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?:popcorn:

---

### Post by cdenley on 2010-03-25
> **vaskbtech said:**
> Hi,
When i connect windows server 2003 from ubuntu these error displayed .

[FONT=Verdana]When i installing the tsclient, by executing these following command from a Terminal window:[/FONT]
 [FONT=Verdana]*sudo apt-get install tsclient*[/FONT]


[FONT=Verdana][I]When i run these command the following error displayed.
[/I][/FONT]

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), **is another process using it?**:popcorn:

This usually means you have another package manager running. You can only run one at a time, to prevent inconsistency and corruption.
```

sudo lsof /var/lib/dpkg/lock

```

---

