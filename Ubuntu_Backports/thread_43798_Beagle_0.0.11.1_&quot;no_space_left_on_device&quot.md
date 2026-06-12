---
title: "Beagle 0.0.11.1: &quot;no space left on device&quot;"
date: 2005-06-23
forum: Ubuntu Backports
---

### Post by kamstrup on 2005-06-23
I am running the latest 0.0.11.1 beagle from Hoary backports on a 2.6.12 inotify enabled kernel.

If i run beagled in a terminal terminal and do a best search the terminal starts spitting "ioctl: No space left on device" out like crazy, and it doesn't seem to stop.

EDIT: Oh, and I have several GB free on all partitions, I might add...  ;-P

On an aside: at daemon startup I am notified of some evo address-book scanning probs, even though I have libevolution-cil installed...

```
WARN: Could not open Evolution addressbook.  Addressbook searching is disabled.
DEBUG: System.DllNotFoundException: libebook-1.2.so.0
in (wrapper managed-to-native) Evolution.Book:e_book_new_system_addressbook (intptr&)
```

I do have /usr/lib/libebook-1.2.so.3 ... so..?

Well apart from that, it seems to be working =D
Cheers!

---

### Post by jdong on 2005-06-23
link so.3 to so.0 using ln... quick hack to get it working ;)


As far as the ioctl... I don't know much about inotify... don't know.

---

### Post by kamstrup on 2005-06-23
Yes. Definitely an inotify problem. Does not happen on stock Hoary kernel... The question just is, if it's a Beagle or inotify bug, or just me being lame :-S

Does anybody else experience this? Should I file a bug somewhere?

---

### Post by jdong on 2005-06-23
It might just be an inotify bug.. .that you can't do much about....

---

### Post by ametade on 2005-06-23
I've found this at [Beagle Wiki](http://www.beaglewiki.org/Troubleshooting):

> 
"ioctl: No space left on device"

If you're getting this it's because beagle is hitting the kernel limit for the number of directories a single process can monitor. To change this limit echo a bigger number to /sys/class/misc/inotify/max_user_watches. The default is 8192. 16384 is good, 32768 is probably more than enough. Notice that this will waste more memory.

To try this do:

```
# echo 16384 > /sys/class/misc/inotify/max_user_watches
```

To make the change permanent you should put that command in one of your boot scripts.


I hope this information can solve your problem :)

---

