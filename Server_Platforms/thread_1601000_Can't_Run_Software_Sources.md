---
title: "Can't Run Software Sources"
date: 2010-10-19
forum: Server Platforms
---

### Post by faada on 2010-10-19
Hi, I've just installed server 10.10 and installed the ubuntu gui on top of it, however for some reason I'm not able to run software sources as it will not accept my password, has anyone had this issue before?

---

### Post by sikander3786 on 2010-10-19
Does any other application, for instance Software Center or Synaptic accept the same password?

Can you carry on tasks needing root previledges by using sudo from terminal. e.g,

```
sudo fdisk -l
```

Does it give any errors?

---

### Post by faada on 2010-10-19
other apps in the gui work with my user p/w and sudo does work as well, however so far software sources and synaptics don't, not sure if there are others.

---

### Post by sisco311 on 2010-10-19
Try running them from a terminal and post the error messages:
```
sudo software-properties-gtk
```
```
sudo synaptic
```

---

### Post by sikander3786 on 2010-10-19
Press Alt + F2, type gconf-editor, hit enter.

Navigate to apps > gksu and see if sudo-mode is ticked. If not, tick it and try again.

---

