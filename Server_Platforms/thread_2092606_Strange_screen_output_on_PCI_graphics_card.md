---
title: "Strange screen output on PCI graphics card"
date: 2012-12-08
forum: Server Platforms
---

### Post by t0m on 2012-12-08
Hi,

I'm using Ubuntu 10.04.4 LTS Server and rarely need screen output over VGA. Recently I did and ran into problems. The screen works fine until booting into Ubuntu, then it just shows garbled characters (see screenshot).

The graphics card is rather old and it's on PCI using VGA cable to connect to a display.

```

$ lspci|grep VGA
05:06.0 VGA compatible controller: Matrox Graphics, Inc. MGA 1064SG [Mystique] (rev 02)
```

Any ideas what I could do to make it work properly again?

Thanks.
T0m.

---

### Post by t0m on 2012-12-08
Ok, found a solution that works for me.

Just disabled all plymouth stuff and switched to pure console output by following this posting:
[http://ubuntuforums.org/showpost.php?p=9581572&postcount=10](http://ubuntuforums.org/showpost.php?p=9581572&postcount=10)

---

