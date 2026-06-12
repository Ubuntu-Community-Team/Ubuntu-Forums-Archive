---
title: "Had to rollback 'gnome-terminal' &amp; 'gnome-terminal-data'"
date: 2014-10-17
forum: Ubuntu Development Version
---

### Post by VinDSL on 2014-10-17
I don't know if anyone else is running GS Staging.  I've been getting pesky error dialogs after each login.

Downgrading 'gnome-terminal' & 'gnome-terminal-data' took care of the error messages.

Synaptic history:

```
Commit Log for Fri Oct 17 15:07:22 2014

Downgraded the following packages:
gnome-terminal
gnome-terminal-data
```

The workaround was to downgrade from:

```
gnome-terminal (3.12.3-0ubuntu1~utopic2)
gnome-terminal-data (3.12.3-0ubuntu1~utopic2)
``` 

to...

```
gnome-terminal (3.6.2-0ubuntu1)
gnome-terminal-data (3.6.2-0ubuntu1)
```

Anyone else experiencing this problem?!?!?

---

### Post by tista on 2014-10-17
Hi VinDSL ;)

If I remembered well, version 3.12.3-0ubuntu1~utopic1 had some "override" installation errors between gnome-terminal and gnome-terminal-data unfortunately. And now I've got newer:
```
Commit Log for Fri Oct 17 12:10:16 2014

Upgraded the following packages:
gnome-terminal (3.12.3-0ubuntu1~utopic1) to 3.14.1-0ubuntu1~utopic2
gnome-terminal-data (3.12.3-0ubuntu1~utopic1) to 3.14.1-0ubuntu1~utopic2
```
Yeah it seems to work pretty well. ;)

Best Regards,
Tista

---

### Post by VinDSL on 2014-10-18
Hi Tista,

Good one!  That solved the login problem(s).  No more errors.

Strangely, it also stopped Guayadeque from crashing/hanging while opening & closing it.  This problem cropped up after I downgraded 'gnome-terminal' & 'gnome-terminal-data'.  Guayadeque seems to work fine now, too.

Thx! ;)


Synaptic history:

```
Commit Log for Sat Oct 18 15:40:21 2014

Upgraded the following packages:
gnome-terminal (3.6.2-0ubuntu1) to 3.14.1-0ubuntu1~utopic3
gnome-terminal-data (3.6.2-0ubuntu1) to 3.14.1-0ubuntu1~utopic3

Installed the following packages:
libvte-2.91-0 (0.38.0-2~~utopic1)
libvte-2.91-common (0.38.0-2~~utopic1)
```

---

