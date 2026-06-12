---
title: "Ubuntu 11.10 Apache2 service start fails"
date: 2011-10-18
forum: Server Platforms
---

### Post by Sami Lehtinen on 2011-10-18
Hi everyone,

Apache2 wont start after system reboot. init's are ok, startup scripts are ok, everything seems to be as it should be but apache2 just isn't starting. So there has to be some kind of trick somewhere, or maybe even bug?

apachectl start - ok
service apache2 start - ok
I checked manually all start levels - ok
I used bom to remove apache2 and add it back just to confirm - ok

I asked about this issue from #ubuntu-fi and #ubuntu, no clues. Logs doens't provide (as far as I know) anything helpful information.

So how I should troubleshoot this issue, or are there known trick(s) how to fix this.

 - Thank you!

Platform is also 64 bit. I just checked there aren't any updates available and there aren't any bugs looking like this listed in Apache2 bugs. (afaik)

Best regards,
[Sami Lehtinen]("http://www.sami-lehtinen.net/")

Edit kernel & apache info:
Linux s 2.6.32-042stab036.6 #1 SMP Tue Sep 13 19:37:36 MSD 2011 x86_64 x86_64 x86_64 GNU/Linux

Server version: Apache/2.2.20 (Ubuntu)
Server built:   Sep  6 2011 18:40:05

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

---

### Post by digitalturbulence on 2011-10-20
Try to start as root the server with the following command:
apache2 -X

---

### Post by ibutho on 2011-10-20
What is the output of running
```
sudo /etc/init.d/apache2 start
```

---

### Post by Sami Lehtinen on 2011-10-21
> **ibutho said:**
> What is the output of running
```
sudo /etc/init.d/apache2 start
```

Trust me, we have checked all basic issues:
root@s:~# /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                                                                                [ OK ]
root@s:~#

Actually I think that init.d scripts aren't being used anymore at all. Because I did add
```
/bin/date > /tmp/apache-start
``` to apache2 file in init.d path. I also added similar kind row to rc.local and it wasn't called either. 

I also have removed plymothd from startup using rcconf. And guess what, it seems like nothing I do with rcconf or init files actually have anything to do with the current startup stuff. 

So is there completely new startup system being used?  Afaik I have been reading a lot of upstart and it seems to be plausible.

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

There are also many references to upstart in init.d path.

```

lrwxrwxrwx  1 root root    21 Sep 28 09:38 plymouth -> /lib/init/upstart-job
lrwxrwxrwx  1 root root    21 Sep 28 09:38 plymouth-log -> /lib/init/upstart-job
lrwxrwxrwx  1 root root    21 Sep 28 09:38 plymouth-splash -> /lib/init/upstart-

```And as said, there is nothing wrong with apache2 configuration, it works just perfectly. Only problem is that it just won't start after boot. No other problems afaik what so ever. I can start it using "service apache2 start", "apachectl start" or what ever. It works. 

 - Thanks for all help and comments. 

Now I try to uninstall and reinstall Apache2 and see what happens, if anything.

Also apachectl -X works exactly as expected.

---

### Post by Sami Lehtinen on 2011-10-22
Issues were too severe, reverted back to old version of Ubuntu. Also CPU consumption went up almost statically about 25%. New version wastes too much resources.

```

Cpu1  : 24.9%us, 49.9%sy,  0.0%ni, 25.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  SWAP COMMAND                                                                                                                            
    1 root      20   0 23612 1684 1316 R  100  0.4  18:47.48  21m init   


 20:52:44 up 21 min,  0 users,  load average: 1.00, 0.97, 0.71

```

---

