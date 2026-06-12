---
title: "Virtual Machine options"
date: 2011-05-12
forum: Server Platforms
---

### Post by Xeneth on 2011-05-12
I am looking for the best VM to run on my Ubuntu server.

I need somewhere to install MS products for school, and want to be able to get to it online.  Preferably a VM I can run after tunneling in to my server through ssh, but I can set it up directly if needed.

EDIT: Preferably free.

---

### Post by R.Bucky on 2011-05-12
VirtualBox is available in the repository and will meet your needs well. 

```
sudo apt-get install virtualbox
```

---

### Post by arrrghhh on 2011-05-12
I second virtualbox.  There are others out there, but none are as easy to use IMHO.

I used VBoxHeadless for a while too, and just RDP'd to the VMs I was running.  Worked great, probably need to set it back up in fact ;).

---

### Post by kevinthecomputerguy on 2011-05-12
ProxMox VE is also nice
[http://proxmox.com](http://proxmox.com)

Both are very nice

---

### Post by Groodles on 2011-05-13
+1 for Virtualbox.  Just works.

---

### Post by rg4w on 2011-05-13
Can't say enough great things about VirtualBox.  I've used Parallels and VMWare, and VirtualBox is as easy as both but seems to outperform them.  My only regret with it is that I didn't switch to it sooner. :)

---

### Post by rubylaser on 2011-05-13
+1 for Proxmox.  I have two clusters setup now, and absolutely love it's simplicity, and cost (free :) ) Virtualbox will work fine as well though.

---

### Post by Lars Noodén on 2011-05-13
In addition to virtualbox, [qemu](http://manpages.ubuntu.com/manpages/natty/en/man1/qemu.1.html) is quite good.

---

