---
title: "Booting Ubuntu12 on HP ProLiant DL380G6 server"
date: 2012-11-09
forum: Server Platforms
---

### Post by elemings on 2012-11-09
Hello all,

We have a HP ProLiant DL380G6 server that will boot SquashFS-based CDs built on Ubuntu 10 but Ubuntu12 CDs appears to boot but NOTHING shows on the monitor.  The server hardware has a ATI ES1000 video controller.  Is a driver for this in the Ubuntu 12 kernel?  Any suggestions for troubleshoothing this greatly appreciated.

Eric.

---

### Post by elemings on 2012-11-09
Hello all,

We have a HP ProLiant DL380G6 server that will boot SquashFS-based CDs built on Ubuntu 10 but Ubuntu12 CDs appears to boot but NOTHING shows on the monitor.  The server hardware has a ATI ES1000 video controller.  Is a driver for this in the Ubuntu 12 kernel?  Any suggestions for troubleshoothing this greatly appreciated.

Eric.

---

### Post by oldfred on 2012-11-09
Merged threads. Please only one thread per topic.

I do not know ATI or AMD as I have nVidia. But found these links:

**ATI ES1000 driver for gnome-shell**
[http://ubuntuforums.org/showthread.php?t=1981168](http://ubuntuforums.org/showthread.php?t=1981168)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

---

### Post by newbie-user on 2012-11-10
I've had that same issue, though not with the same hardware. I've worked around the problem by pressing enter twice, as if going through the menu options as if I could actually see the options.

Seems as though it's just those first two menu screens, then after that, the installation process shows up just fine on the monitor. I know this isn't a fix, but if you just need to get a basic installation started, it might work.

---

