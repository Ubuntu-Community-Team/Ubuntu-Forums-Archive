---
title: "How To Install GUI on Server 9.04"
date: 2010-01-20
forum: Server Platforms
---

### Post by cataztrophe on 2010-01-20
Hello there,
i just installed ubuntu server 9.04.
now i wanna install GUI on that such as Xinit, and others, theni stuck because i wannna install it without connection (from source / offline) can anyone help me plz :popcorn:
thanx before guys;)

---

### Post by gg234 on 2010-02-04
Try this [http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html)

> **cataztrophe said:**
> Hello there,
i just installed ubuntu server 9.04.
now i wanna install GUI on that such as Xinit, and others, theni stuck because i wannna install it without connection (from source / offline) can anyone help me plz :popcorn:
thanx before guys;)

---

### Post by quietas on 2010-02-04
```
sudo apt-get install ubuntu-desktop
```

This is a topic sure to draw out the CLI zealots. Please don't beat the guy to hard people.

I actually use a Gnome on my server so I can run FreeNX as though it were a terminal server.

---

### Post by dragos2 on 2010-02-04
```

apt-get install gnome-core

```
or 
```

apt-get install xorg-core gnome-core

```

We have the commercial NX server which is working great with Ubuntu server 8.04 and
gnome-core.

---

### Post by quietas on 2010-02-04
Good idea with Gnome core only.

---

