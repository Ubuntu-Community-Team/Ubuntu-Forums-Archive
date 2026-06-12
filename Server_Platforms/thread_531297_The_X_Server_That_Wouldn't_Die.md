---
title: "The X Server That Wouldn't Die"
date: 2007-08-21
forum: Server Platforms
---

### Post by dirtside on 2007-08-21
I've just run apt-get upgrade all, which upgraded gdm... and for some reason it decided that it would try to start a new x.org session, which I'm now stuck with. It's running on :1 and I can't get it to just GO AWAY. kill -9 just makes it restart, which I understand is the normal behavior... but I don't WANT it to restart. I don't want to reboot my computer, either, which presumably would make it go away. (I've got my original X session open on :0, which is where I'm typing this message. And I have lots of development windows open and rebooting is not a good option right now.)

How do I just *kill* an xserver session dead? I'd be satisfied with changing the running server's options to include -terminate so that it doesn't restart when the last client disconnects, but I have no idea how to do this.

Thanks in advance.

---

### Post by ddrichardson on 2007-08-22
```
/etc/init.d/gdm stop
```

---

