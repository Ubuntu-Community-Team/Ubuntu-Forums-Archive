---
title: "apt-get is so slow"
date: 2008-11-09
forum: Server Platforms
---

### Post by Vegan on 2008-11-09
Since I upgraded to intrepid (Ubuntu Server 8.10) installing some packages has slowed to a trickle.

:guitar:

---

### Post by Philio on 2008-11-09
Which part is slow? Download, install?
Not noticed any difference personally.

---

### Post by frankleeee on 2008-11-09
> **Vegan said:**
> Since I upgraded to intrepid (Ubuntu Server 8.10) installing some packages has slowed to a trickle.

:guitar:

If it is the download it's probably the server, I have had no problems either.

---

### Post by Vegan on 2008-11-09
Guess the bandwidth of the server is saturated too bad with peep installing the new 8.10, once downloaded its fast, considering my server is a museum piece.

IBM 300 GL, go check it out on IBM.com where manuals are still available. Pentium 3, 667 and its fine with Ubuntu.

---

### Post by TrendRat on 2008-11-10
Agree, download is absolutely glacial.  Install is fine.

---

### Post by Philio on 2008-11-10
Maybe it depends on your location, our servers are in Bluesquare, Maidenhead (UK) and they downloaded the required packages for upgrade from 8.04 in about 10 seconds (it's about 135Mb), I've upgraded 4 servers so far still got a few to go but none have been slow at all.

---

### Post by ciscosurfer on 2008-11-10
Try a faster mirror: [http://www.ubuntugeek.com/how-to-select-fastest-mirror-in-ubuntu.html](http://www.ubuntugeek.com/how-to-select-fastest-mirror-in-ubuntu.html)

---

### Post by Vegan on 2008-11-12
Might be a project for the repositories to use load balancing.

:guitar:

---

### Post by TrendRat on 2008-12-03
Finally fixed this problem - went to System-Administration-Software Sources-Ubuntu Software tab, and switched from Canadian server to Main Server.  The Canadian server was absolutely glacial (it us cold up here after all).  Now my Ubuntu updates happen fast.

---

### Post by cariboo on 2008-12-04
This one might be just a little bit closer to you:

[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/)

Jim

---

### Post by Thirtysixway on 2008-12-04
How can I do this in server edition?

---

### Post by Vegan on 2008-12-13
One wrinkle, tabs? tabs? what tabs? I don't need no stinkin' tabs. Servers do not have a GUI.

What the repository needs to do it fix the repositories and find some better bandwidth. Maybe a torrent is whats needed.

:guitar:

---

