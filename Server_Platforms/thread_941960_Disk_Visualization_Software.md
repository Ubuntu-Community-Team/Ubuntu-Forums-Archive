---
title: "Disk Visualization Software?"
date: 2008-10-08
forum: Server Platforms
---

### Post by davidshq on 2008-10-08
Hi All,
   I'm wondering if anyone is familiar with some command-line software that will provide visualization of hard drive utilization? Something similar to WinDirStat, but for Linux and the command-line? Thanks for any thoughts.
Dave.

---

### Post by promodus on 2008-10-09
TRY:

[http://kdirstat.sourceforge.net/](http://kdirstat.sourceforge.net/)
```
sudo apt-get install kdirstat
```

OR

[http://www.marzocca.net/linux/baobab.html](http://www.marzocca.net/linux/baobab.html)
```
sudo apt-get install gnome-utils
```

as for the command line usage,

use du
to make it like windirstat... I'm not sure how you want that data represented?

---

### Post by chitresh4u on 2009-01-17
you can try gdmap ( [http://gdmap.sourceforge.net/](http://gdmap.sourceforge.net/) ) or xdiskusage ( [http://xdiskusage.sourceforge.net/](http://xdiskusage.sourceforge.net/) ). gdmap much more similar to windirstat.

---

