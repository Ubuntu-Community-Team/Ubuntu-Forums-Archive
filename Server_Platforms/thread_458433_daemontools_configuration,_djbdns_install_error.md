---
title: "daemontools configuration, djbdns install error"
date: 2007-05-29
forum: Server Platforms
---

### Post by uncleducati on 2007-05-29
I ran apt-get install djbdns-installer on 7.04 server and then ran build-daemontools succesfully, then I entered:
--------------------------------------------
# svscan - daemontools -- [http://www.froyn.net/blosxom/blosxom.cgi/2007/1/12](http://www.froyn.net/blosxom/blosxom.cgi/2007/1/12)

#

# This service maintains an svscan process from the point the system is
# started until it is shut down again.

start on runlevel-1
start on runlevel-2
start on runlevel-3
start on runlevel-4
start on runlevel-5
start on runlevel-6

respawn /command/svscanboot
-----------------------------------------

I ran

start svscan

which returned 

svscan (start) running, process 3509 active

but when I run build-djbdns and then attempt to install the .deb in /tmp I get this error:

dpkg: dependency problems prevent configuration of djbdns:
 djbdns depends on daemontools; however:
  Package daemontools is not configured yet.
dpkg: error processing djbdns (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 djbdns

why doesn't it see daemontools? Is this related somehow to ucsci-tcp, which I don't believe the installer installed? I rebooted just for kicks.

Alternately I was going to just install from source, though I don't know how to do the following step from djb's website:

As root, install the ucspi-tcp programs under /usr/local:

what switches would I need to use with make to do this if I'm installing from /usr/src/uscpi-tcp.xxx/ ?

Thanks, and hopefully this will help the next guy attempting to install djbdns from multiverse.

Thanks,
Cameron
San Diego

---

### Post by jongt1 on 2008-01-17
The above svscanboot job doesn't work with gutsy. You need to replace the "runlevel-n" with "runlevel n" (ie change the minus to a space). After that, supervise gets started properly during boot and qmail will be running by the time boot completes.

---

### Post by Railsbuntu on 2008-01-25
Hi guys,

I don't understand how daemontools works. Can womeone write a quick howto?

Basically what I want to do, is start a fastcgi server for nginx, and that when this server dies it shall be automatically restarted by daemontools.

Currently I start the server by hand issuing:
> [$ /usr/bin/spawn-fcgi -a 127.0.0.1 -p 10005 -u www-data -g www-data -f /usre/bin/php-cgi
So how to make this automatically start and resurrect using daemontools?

From the little documentation available I understood that I need to create some directory under /service, but what to put in it? What permissions to set? Should I write a script in in too?


I also created the file /etc/event.d/svscan, then when I do:
> sudo start svscan
I get the following error message:
> start: Unknown job: svscan

What did I do wrong?

---

### Post by anthony.rasat on 2008-03-27
> **Railsbuntu said:**
> 

I also created the file /etc/event.d/svscan, then when I do:

I get the following error message:

What did I do wrong?

I think you should recheck your /etc/event.d/svscan again. There is typo mistake. It supposed to be like this:

```
    start on runlevel 2
    start on runlevel 3
    start on runlevel 4
    start on runlevel 5

    respawn
    exec /command/svscanboot
```

---

