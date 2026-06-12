---
title: "redhat cluster problems"
date: 2009-08-20
forum: Server Platforms
---

### Post by toxicdav3 on 2009-08-20
I've tried these guides to setup GFS2, redhat cluster suite and drbd with no luck.

[http://www.piemontewireless.net/Storage_on_Cluster_DRBD_and_OCFS2](http://www.piemontewireless.net/Storage_on_Cluster_DRBD_and_OCFS2)
[https://wiki.edubuntu.org/Testing/Cases/UbuntuServer-drbd](https://wiki.edubuntu.org/Testing/Cases/UbuntuServer-drbd)
[http://jun.homeunix.com/blog/?p=11](http://jun.homeunix.com/blog/?p=11)

I keep getting these errors (picture attached). If I just start it manually its always the same error on both machines and just doesn't continue:
```

@host1:~$ sudo /etc/init.d/cman start
Starting cluster:
   Loading modules... done
   Mounting configfs... done
   Setting network parameters... done
   Starting cman... done
   Starting daemons... done
   Starting fencing... /usr/sbin/cman_tool: Error getting extra info: Host is down
```

Please help.

---

