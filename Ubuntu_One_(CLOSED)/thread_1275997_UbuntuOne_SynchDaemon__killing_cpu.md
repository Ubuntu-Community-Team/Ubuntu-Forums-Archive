---
title: "UbuntuOne SynchDaemon  killing cpu"
date: 2009-09-26
forum: Ubuntu One (CLOSED)
---

### Post by bdubsemail on 2009-09-26
whenever i open my system monitor the ubuntuone-synchdaemon is running and taking 90-100% cpu and its doing this all day non stop i dunno what to do about this

---

### Post by joshuahoover on 2009-09-29
> **bdubsemail said:**
> whenever i open my system monitor the ubuntuone-synchdaemon is running and taking 90-100% cpu and its doing this all day non stop i dunno what to do about this

I'm sorry to hear Ubuntu One appears to be taking all your CPU cycles. If you don't mind, can you right-click on the Ubuntu One applet and select "Report a Bug" so that we can get some more debug info and track this bug there.

Thank you,

Joshua

---

### Post by b5baxter on 2009-11-17
I am also having this issue with 9.10 and the latest version of UbuntuOne.

---

### Post by b5baxter on 2009-11-24
The problem turned out to be related to file permissions.

I deleted a *.LNK file created by GnuCash and the SynchDaemon cpu time immediately went down.

---

### Post by joshuahoover on 2009-11-25
> **b5baxter said:**
> The problem turned out to be related to file permissions.

I deleted a *.LNK file created by GnuCash and the SynchDaemon cpu time immediately went down.

Thanks for sharing this! I found this out more recently as well. If you have a file that is owned by root then it caused the Syncdaemon to try to hash the file over and over and over, which causes the high CPU usage.

Joshua

---

