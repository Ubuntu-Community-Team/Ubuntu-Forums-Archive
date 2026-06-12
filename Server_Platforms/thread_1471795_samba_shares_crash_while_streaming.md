---
title: "samba shares crash while streaming"
date: 2010-05-03
forum: Server Platforms
---

### Post by jay3712 on 2010-05-03
Here's the setup:
Ubuntu Server w/ samba share 'videos'
HTPC Ubuntu 9.10, XBMC
Windows 7 Pro (regular desktop)

I can watch movies on my HTPC (xbmc) all day with no issues whatsoever. When I try to watch a movie with xbmc or vlc on my windows desktop, the shares on the server go offline periodically, typically 20-30 minutes into the movie. Shares come back up in about 2-3 minutes, and everything is fine again for another 30 minutes. This also seems to be the case when transferring large files to or from the server shares on my windows 7 machine.

Any idea why this happens on my windows 7 machine and not on my ubuntu HTPC? What log files should I be looking at to find out what is wrong?

Thanks!
Jason

Edit: SSH and other services continue to work after crashes, and if I sudo /etc/init.d/samba resart the shares come right back up, so it would appear that the issue is isolated to samba.

---

### Post by NullHead on 2010-05-03
You might consult the logs in /var/log/samba/log.<IP address/hostname>

---

### Post by jay3712 on 2010-05-03
It looks like this may point to a problem, but I don't know what any of it means. looks like wide links and unix extensions?
Thanks for your help!

From my desktop ip:
```
Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide $
[2010/05/03 21:11:45,  0] param/loadparm.c:widelinks_warning(9578)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide $
[2010/05/03 21:27:12,  0] param/loadparm.c:widelinks_warning(9578)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide $
[2010/05/03 21:42:45,  0] param/loadparm.c:widelinks_warning(9578)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide $
[2010/05/03 21:58:15,  0] param/loadparm.c:widelinks_warning(9578)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide $
[2010/05/03 22:13:45,  0] param/loadparm.c:widelinks_warning(9578)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide $
[2010/05/03 22:29:15,  0] param/loadparm.c:widelinks_warning(9578)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide $
[2010/05/03 22:42:47,  0] param/loadparm.c:widelinks_warning(9578)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide $
[2010/05/03 22:44:45,  0] param/loadparm.c:widelinks_warning(9578)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide $
[2010/05/03 23:00:15,  0] param/loadparm.c:widelinks_warning(9578)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide $

```

From my HTPC:
```
[2010/05/03 21:20:47,  0] param/loadparm.c:widelinks_warning(9578)
  Share 'videos' has wide links and unix extensions enabled. These parameters are incompatible. Wid$
[2010/05/03 21:20:47,  1] smbd/service.c:make_connection_snum(1130)
  jason-htpc (192.168.1.205) connect to service videos initially as user jason (uid=1000, gid=1000)$
[2010/05/03 21:20:48,  0] param/loadparm.c:widelinks_warning(9578)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide $
[2010/05/03 22:25:52,  1] smbd/service.c:close_cnum(1342)
  jason-htpc (192.168.1.205) closed connection to service videos

```

---

