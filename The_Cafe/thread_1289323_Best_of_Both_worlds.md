---
title: "Best of Both worlds"
date: 2009-10-12
forum: The Cafe
---

### Post by Sashin on 2009-10-12
Tired of the choice between gnome and KDE4?
Well now you don't have to choose!

[http://i33.tinypic.com/4k8ivt.png](http://i33.tinypic.com/4k8ivt.png)

All I did to get that was run gnome-shell --replace and then press control-c and bam! A fusion of two Desktop environments.

---

### Post by NoaHall on 2009-10-12
Yes, a thread has already been made of this.

---

### Post by coldReactive on 2009-10-12
> **NoaHall said:**
> Yes, a thread has already been made of this.

Link?

---

### Post by NoaHall on 2009-10-12
[http://ubuntuforums.org/showthread.php?t=1288156](http://ubuntuforums.org/showthread.php?t=1288156)

Here.

---

### Post by Sashin on 2009-10-12
That's just gnome shell over KDE, this is gnome + KDE.

---

### Post by coldReactive on 2009-10-12
> **NoaHall said:**
> [http://ubuntuforums.org/showthread.php?t=1288156](http://ubuntuforums.org/showthread.php?t=1288156)

Here.

Oh, I thought you meant GNOME + KDE, not GNOME SHell + KDE. :|

---

### Post by NoaHall on 2009-10-12
But that's what the OP is talking about, shell + KDE.

---

### Post by hockeytux on 2009-10-12
How heavy is this memory wise?

---

### Post by coldReactive on 2009-10-12
> **NoaHall said:**
> But that's what the OP is talking about, shell + KDE.

afaik, GNOME SHell doesn't have that nice GNOME 2 panel.

---

### Post by lovinglinux on 2009-10-13
I'm doing exactly the inverse. When I'm logged into Gnome and I run this...

```
plasma-desktop &
```

...so KDE takes over gnome.

I'm pretty happy with this setup, which I call Ukubuntu :)

Performance is really good, but I'm runing Karmic. I also have compiz widget layer and screenlets enabled, so I have two separate widget layers, one from compiz+screenlets and other from plasma dashboard.

I also removed the gnome-panel [this way](http://ubuntuforums.org/showpost.php?p=6851947&postcount=2). When I log in into Gnome there is just the desktop folders and launchers. There is no gnome menu and no ALT+F2. So I have added two launchers to the desktop, one for plasma-desktop and other for gnome-panel.

Script to launch gnome-panel

```
#!/bin/bash

killall gnome-panel
killall plasma-desktop
gnome-panel &
```

Script to launch plasma-desktop

```
#!/bin/bash

killall gnome-panel
killall plasma-desktop
plasma-desktop &
```

The objective of this setup is to replace gnome-shell completely, because I don't like the concept of it, specially considering compiz will not be an option. So I will simply replace gnome-shell with plasma-desktop ;)

---

