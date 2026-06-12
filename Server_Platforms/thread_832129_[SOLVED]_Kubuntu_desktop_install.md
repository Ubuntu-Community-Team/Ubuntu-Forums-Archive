---
title: "[SOLVED] Kubuntu desktop install"
date: 2008-06-17
forum: Server Platforms
---

### Post by dez1914 on 2008-06-17
Can someone help,(somewhat noob), I installed server edition (hardy) works fine, then I tried "sudo apt-get install kubuntu-desktop" and it took forever but seemed like everything installed fine. I rebooted and typed "startx" and get the no screen found error.  How can I get this resolved?

---

### Post by windependence on 2008-06-18
Try startkde

-Tim

---

### Post by gtdaqua on 2008-06-18
Minimum version of KDE for a server:

```

sudo apt-get install kdebase kdm x-window-system-core

```

If KDE is not starting, try:

```

sudo /etc/init.d/kdm stop
sudo /etc/init.d/kdm start

```

If it doesn't start, you *may* need to install your video drivers manually.

---

### Post by dez1914 on 2008-06-18
thanks to the both of you, I've already tried everything you've suggested.  I think I'll install the desktop version and play around and get more familiar then install the server version again on another computer or virtual computer.

thanks

---

