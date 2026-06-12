---
title: "Wput----help"
date: 2007-05-25
forum: Server Platforms
---

### Post by relegate on 2007-05-25
iam a newbie to the open world.iam using wput to upload files [in MB format] to the FTP server.
the thing is the the upload rate is denoted in K/s.May anyone help as to what
does K/s stand for.Is it KB/s or it Kb/s.
I also need help as to how can i format the upload rate so that it shows in form of MB/s and not K/s.
Thanks

---

### Post by MJN on 2007-05-25
You should be able to work it out - upload a file whose size you know (in kB) and see how long it takes (in seconds). First divided by the second gives you the rate in kB/s then compare it with that shown.

Note however that given the capital K it's likely (if they're not being sloppy with their notation!) to be referring to *kibi*bytes (KiB) or *kibi*bits (Kib) i.e. 1,024 bytes or 1,024 bits respectively, as opposed to units of 1,000.

Post some figures of a few runs if you're not comfortable doing the above and we can go through them. As for changing the output format I'm afraid I don't know as I haven't used wput.

Mathew

---

