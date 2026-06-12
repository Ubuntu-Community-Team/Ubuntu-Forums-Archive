---
title: "server version + xdm"
date: 2009-10-02
forum: Server Platforms
---

### Post by pdc124 on 2009-10-02
ive installed the server version and want to add a GUI . I ve apt-getted xdm

what now ?

---

### Post by Bachstelze on 2009-10-02
Do you want to access the GUI remotely, or just run it with a monitor and keyboard plugged to the server?

---

### Post by pdc124 on 2009-10-02
remotely principally, but i'll have something local 'just in case'

---

### Post by Bachstelze on 2009-10-02
First, you probably have to install a windows manager (Fluxbox, wmii, fvwm, whatever). Then you will have access to it when you start xdm (sudo /etc/init.d/xdm start). For remote access, install a [VNC](https://help.ubuntu.com/community/VNC) server.

---

