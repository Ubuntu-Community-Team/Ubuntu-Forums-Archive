---
title: "[help pls] MRTG graphs for httpd processes Not Updating"
date: 2019-05-25
forum: Server Platforms
---

### Post by demonwick on 2019-05-25
hi guy, i'm newbie. 
i'm having problems with my MRTG Graphs Just one for httpd processes Not Updating anymore,other is OK. (see attach images) Any help configuration will be appreciated. Thank you again! 


Error Messages! 
```
[root@mydomain ~]# env LANG=C /usr/bin/mrtg /etc/mrtg/mrtg.cfg
2019-05-23 08:03:25: WARNING: Could not match host:'testsr@localhost:::::2' ref:'Descr' key:'_Interface_'
2019-05-23 08:03:25: ERROR: Target[localhost__interface_][_IN_] ' $target->{$mode} ' did not eval into defined data
2019-05-23 08:03:25: ERROR: Target[localhost__interface_][_OUT_] ' $target->{$mode} ' did not eval into defined data
```


/etc/mrtg/mrtg.cfg 
```
Target[localhost__Interface_]: \_Interface_:testsr@localhost:::::2
noHC[localhost__Interface_]: yes
SetEnv[localhost__Interface_]: MRTG_INT_IP="162.20.450.xxx" MRTG_INT_DESCR="_Interface_"
MaxBytes[localhost__Interface_]: 125000000
Title[localhost__Interface_]: _Interface_ -- mystatic
PageTop[localhost__Interface_]: <h1>eth0 -- mystatic</h1>
```

[IMG][IMG]https://d.thaihosttalk.com/uploads/default/original/2X/e/e89434ab962a85a24f2a4eea79b93fb8629237e8.jpeg[/IMG][/IMG]

---

