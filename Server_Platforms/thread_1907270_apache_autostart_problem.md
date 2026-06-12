---
title: "apache autostart problem"
date: 2012-01-11
forum: Server Platforms
---

### Post by azenz on 2012-01-11
On my new Kubuntu 11.10 64 bit apache won't start by default. /etc/init.d/apache2 exists and the rc directories list apache entries (e.g. /etc/init.d/S91apache2). But I am confused whether the apache2 script actually starts the service at boot. Therefore I set up my own script which looks like:

#!/bin/bash
/etc/init.d/apache2 start

I put it in the S95 runlevels: sudo update-rc.d apache-startup start 95 2 3 4 5 .

Now, the script sits in the runlevels, but it doesn't do its job. I still have to start apache2 manually: 

sudo service apache2 start

* Restarting web server apache2                                                                                              apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                                       [ OK ]
/var/log/error.log looks like this:

...
[Fri Jan 06 22:34:13 2012] [notice] caught SIGTERM, shutting down
[Sat Jan 07 11:41:50 2012] [notice] Digest: generating secret for digest authentication ...
[Sat Jan 07 11:41:50 2012] [notice] Digest: done
[Sat Jan 07 11:41:50 2012] [notice] Apache/2.2.20 (Ubuntu) DAV/2 PHP/5.3.6-13ubuntu3.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Jan 07 11:43:12 2012] [notice] caught SIGTERM, shutting down
[Sat Jan 07 12:12:50 2012] [notice] Digest: generating secret for digest authentication ...
[Sat Jan 07 12:12:50 2012] [notice] Digest: done
[Sat Jan 07 12:12:50 2012] [notice] Apache/2.2.20 (Ubuntu) DAV/2 PHP/5.3.6-13ubuntu3.3 with Suhosin-Patch configured -- resuming normal operations
[Mon Jan 09 08:42:21 2012] [notice] caught SIGTERM, shutting down
[Mon Jan 09 09:13:08 2012] [notice] Digest: generating secret for digest authentication ...
[Mon Jan 09 09:13:08 2012] [notice] Digest: done
[Mon Jan 09 09:13:08 2012] [notice] Apache/2.2.20 (Ubuntu) DAV/2 PHP/5.3.6-13ubuntu3.3 with Suhosin-Patch configured -- resuming normal operations
[Tue Jan 10 09:03:47 2012] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

What is wrong? How can I get this thing to autostart?

---

### Post by lisati on 2012-01-11
*Thread moved to **Server Platforms**.*

Have a look here, starting at post 7: [http://ubuntuforums.org/showthread.php?t=1748310](http://ubuntuforums.org/showthread.php?t=1748310)

---

### Post by Azdour on 2012-01-11
Hi,

I think that the error:

> apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

should not prevent apache2 from auto-starting, although the post referred to will show you how to fix that particular warning.

I would put in your script some outputs to a log file of your own in /var/log just to confirm that it is being called.

---

### Post by Lars Noodén on 2012-01-11
That warning won't actually prevent Apache from starting up.  

About logging, if you want to add logging to your script look at [logger](http://manpages.ubuntu.com/manpages/oneiric/en/man1/logger.1.html).

---

### Post by azenz on 2012-01-11
> **lisati said:**
> 
Have a look here, starting at post 7: [http://ubuntuforums.org/showthread.php?t=1748310](http://ubuntuforums.org/showthread.php?t=1748310)

It's crazy, but that fix DID IT! Now the startup script works. Cannot believe it. Thanks!

Now, the vboxdrv startup script that executes the modprobe command still doesn't work, I moved that command into the cputemp script, and for some weird reason, once it is there, it gets executed. I just DON'T UNDERSTAND why. Startup scripts remain a mystery to me...

---

### Post by Azdour on 2012-01-11
Hi,

Great to hear that lisati's url worked. At the end of the day it's what ever solution works strange or not strange. So I'm glad you did not listen to me otherwise you would still have an issue :D lol

As a side note - you may want to start a new thread about your vboxdrv startup script and close this thread.

---

