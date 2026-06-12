---
title: "Server login information"
date: 2011-04-09
forum: Server Platforms
---

### Post by kamaji792 on 2011-04-09
I like the server login information that gets displayed when you login to a 10.04 server.  It lists disk usage, CPU usage, Temperature etc...

Unfortunately I had problems installing 10.04 from a USB.  At the end of the process the master boot record was stored on the USB and not the hard disk.

Any way I got round that problem thanks to this thread [http://ubuntuforums.org/showthread.php?t=1517987](http://ubuntuforums.org/showthread.php?t=1517987):)

But now when I login to my server I don't get the server information.:(

Anyone know how to resolve this?

---

### Post by kamaji792 on 2011-07-04
I look like I needed to install the landscape package.

```
sudo apt-get install landscape-common
```

Now when I log into the server it get some server information.  Seems to be missing the temperature which I sure it originally displayed, but it's a step in the right direction.

K

---

