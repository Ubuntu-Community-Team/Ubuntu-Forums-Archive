---
title: "Working Copy of Server"
date: 2009-04-21
forum: Server Platforms
---

### Post by ubuser_7 on 2009-04-21
Hi 

We are running a few Hardy servers. All the servers are backed up using Backuppc on a nightly basis. 

I was wondering if there is a way to generate a DVD that will allow me to export a working image of a server. To clarify, lets say that if one of our server crashes, then using the CD I can immediately bootup (kinda like a live CD or perhaps a quick install) the exact same server on another machine. 

I am not sure even if I am on the right track or not, but basically we want a setup that will allow us fast recovery from crashes, especially hardware failures. We just put in this DVD in another spare machine and the server is back up.

---

### Post by Wayne_V on 2009-04-21
see [http://ubuntuforums.org/showthread.php?t=936582](http://ubuntuforums.org/showthread.php?t=936582)

you would just have to be sure everything on the DVD would be static data and any dynamic data would have to be stored/restored elsewhere.

---

### Post by ubuser_7 on 2009-04-22
Thanks! I will check it out!

---

### Post by ubuser_7 on 2009-04-23
I tried booting from the CD but got some errors. Any suggestions?

```

boot: live
Loading /casper/vmlinuz.....................
Loading /casper/initrd.gz...........................................
ready

Loading, please wait...
kernel direct mapping tables up to 100000000 @ 8000-d000
[    30.201871] hub 5-1:1.0: cannot reset port 1 (err = -71)
[    30.XXXXXX] hub 5-1:1.0: cannot reset port 1 (err = -71)
[    30.XXXXXX] hub 5-1:1.0: cannot reset port 1 (err = -71)
[    30.XXXXXX] hub 5-1:1.0: cannot reset port 1 (err = -71)
[    30.XXXXXX] hub 5-1:1.0: cannot reset port 1 (err = -71)
[    30.XXXXXX] hub 5-1:1.0: Cannot enable port 1. Maybe the USB cable is bad?
<snip>

```

The usb error is repeated 4-5 times and thats about it. it just hangs. a lot of times it just stops after kernel direct mapping message. 

I tried running the check option but that gives the same results.

Any suggestions?

---

