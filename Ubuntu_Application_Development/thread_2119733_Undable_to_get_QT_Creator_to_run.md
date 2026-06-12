---
title: "Undable to get QT Creator to run"
date: 2013-02-24
forum: Ubuntu Application Development
---

### Post by Paul126 on 2013-02-24
Hi,

I'm trying to follow the tutorial for Ubuntu phone. I am on 12.10 have installed everything I need but when I rund QT Creator I get

```
qtcreator: error while loading shared libraries: libQt5Widgets.so.5: cannot open shared object file: No such file or directory
```

There's nothing on google, I can't find it as a bug. It's probably something obvious but I'm stuck and not too proud to ask for help!

Help!

---

### Post by brucegu on 2013-02-25
pay attention to the command line execution result, it should have some errors or warnings.

---

### Post by Paul126 on 2013-02-25
Thanks but that is the command line output. When I hit the icon in unity it just flashes and does nothing. So I used the command line as user and with sudo just in case and my first post was the output. Any other ideas?

---

### Post by morchuboo on 2013-02-25
check if you have libqt5widgets5 installed

---

### Post by Paul126 on 2013-02-25
yeah, I do. I ran a strace, there are lots of things that it is looking for that it seems to not be finding in the right place. That command line output was just the last thing it couldn't find. It's not just a case of relocating a couple of files to the right place. 

I'll post the details in the morning. But I'm surprised that QTCreator has a problem like this. Will continue to investigate, might boot up 12.04 in a VM to see what happens. I will solve this, oh yes, I will!

---

