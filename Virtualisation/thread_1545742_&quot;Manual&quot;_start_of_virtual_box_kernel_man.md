---
title: "&quot;Manual&quot; start of virtual box kernel manager"
date: 2010-08-04
forum: Virtualisation
---

### Post by Warthaug on 2010-08-04
As I've mentioned in [another thread]("http://ubuntuforums.org/showthread.php?t=1545686"), I am having an intermittent problem with some services not starting at boot.  One of these is vbox's kernel manager.  I've written a little script I can run to fix this issue when it occurs, but at the current moment it does not fix vbox.  Instead, when I try to start a guest I get an error, and the "default" fix that is offered is to recompile the kernel.  As many here can appreciate, this takes a bit of time and is overkill in regards to fixing the true issue.

I was wondering if anyone knows how to "manually" start the vbox kernel manager (i.e. from the command line).  I've not been able to figure out how to do this.  I did find a few imaginative ways to wreck vbox though,,,

I'm running vbox 3.2.6 r63112 (the closed source version) in Ubuntu 10.04, 64 bit.

Thanx

Bryan

---

### Post by Warthaug on 2010-08-04
After a whole day of searching (instead of working - he, he) I managed to track down my answer.  At the command line enter:

```
sudo /etc/init.d/vboxdrv start
```

This will start the vbox kernel driver.

Now, if only I could get it to load every time I boot...

Bryan

---

