---
title: "Firefox does not start on 64bit live or VM."
date: 2014-02-27
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2014-02-27
I have tried three times to install a VM in Virtualbox 4.3.8 with a live .iso from the daily image site, downloaded 25 Feb using zsync, so I know the image file is fine.  There have been no updatsd to the image since then to attempt a newer install.

Almost everything works but Firefox (version 25) will not load giving an error in terminal. This is actually copied from a live system running in VBox, but the installed VM gave exactly the same error, except for a different process pid.  I am about to try running the live system on real hardware instead of in VBox so will report back shortly if things are any different in that situation.
```
lubuntu@lubuntu:~$ firefox

(process:3200): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size ==0' failed
Segmentation fault (core dumped)
```

The 64bit Xubuntu daily, fully updated, works fine and is running in a VM as I speak, as does the 32 bit Lubuntu daily.

Any thoughts, or is it just a glitch of that particular day's Lubuntu 64 image?

EDIT:
I have just used the same daily Lubuntu 64 iso as a live system on real hardware in stead of on VBox, as I said I was about to, and the problem is exactly the same; Firefox is simply refusing to run with exactly the same error message.

---

### Post by sudodus on 2014-02-27
You are not alone.

See this link [http://iso.qa.ubuntu.com/qatracker/milestones/312/builds/63520/testcases/1300/results](http://iso.qa.ubuntu.com/qatracker/milestones/312/builds/63520/testcases/1300/results)

and the bug report [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1278062](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1278062)

---

### Post by ajgreeny on 2014-02-27
Thanks sudodus.  I had already found a bug report a while after posting here, but it's only in Lubuntu that it has happened to me, not Xubuntu 64bit, and only the 64bit version; the i386 Lubuntu is fine.

---

### Post by sudodus on 2014-02-28
Yes, it is a strange bug.

---

