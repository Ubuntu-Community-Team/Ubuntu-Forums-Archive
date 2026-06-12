---
title: "Very Basic 32bit 64bit question"
date: 2010-05-05
forum: Server Platforms
---

### Post by jrtboat on 2010-05-05
I have an older 32bit computer that I want to setup as a web server.  Can this computer run Ubuntu Server 64bit (which seems to be the default download) or should I choose the 32bit Server edition?

---

### Post by antenna on 2010-05-05
The 32 bit one.

---

### Post by dudumomo on 2010-05-05
what is your processor ?
If your proc is a 32bit, then install the 32b one. If it is a 64b, go for the 64b.
It is quite common to see a 32b OS on a 64b proc. But as we don't really have any problem with the 64b softwares, I rather prefer using the full potiential of my proc.

---

### Post by jrtboat on 2010-05-06
Thanks for the help.  Its an older HP a420n (AMD Athlon(T) XP 3000+   2.167 GHz) so I'll go with the 32bit version I think.  The website threw me off a bit because it seemed like it was hiding the 32bit version a little.

---

### Post by howefield on 2010-05-06
> **jrtboat said:**
> so I'll go with the 32bit version I think.  

If you have Ubuntu installed, look at the output of the command

```
cat /proc/cpuinfo
```

If you can see lm in the list of flags, your processor can run either 64 bit or 32 bit. If not, it can only run 32 bit.

---

### Post by jrtboat on 2010-05-06
I don't have any OS installed right now but this computer is from 2003 and 64bit procs weren't very popular back then (I don't think they were at least).

---

### Post by Frizianz on 2010-05-07
Im Running a Athlon XP in My Server and They are not 64bit cpus

---

### Post by windependence on 2010-05-07
FYI 64 bit != speed necessarily. You only need 64 bit for heavy math operations such as high end graphics rendering, etc. In most cases such as web servers and other less intensive apps, 64 bit systems can actually slow you down as you are not using the wider data path, but you still have all the overhead. In most cases, 32 bit is still enough for normal applications. If you're running a CAD server, then go for 64 bit, but if you're setting up a mail server, 32 bit may actually run faster and more efficiently.

-Tim

---

