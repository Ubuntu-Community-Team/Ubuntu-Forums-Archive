---
title: "Adding a second hard drive?"
date: 2010-09-11
forum: Virtualisation
---

### Post by locoHost on 2010-09-11
Using VirtualBox 3.2.8. I have an Ubuntu Lucid server with Gnome Desktop installed. Yeah, I'm -Ok- in terminal, but not awesome :-/ It's an FTP server. It works great, but my root drive is now too small. So I created a second (larger) VDI and added it as a second sata drive to the virtual machine. When I start up the machine, I can only see the root drive, not the second one. What am I doing wrong?

Thanks in advance for your help :-)

---

### Post by locoHost on 2010-09-12
No? Can't do this?

---

### Post by TJet1.8 on 2010-09-12
> **locoHost said:**
> No? Can't do this?

Well...you problem isn't with VirtualBox...but rather with Ubuntu Server.

When you add drives to Linux (virtual or physical), you need to modify your /etc/fstab file to auto-mount your new drive.

This is a Linux O/S issue...not a Virtualization issue.

---

### Post by locoHost on 2010-09-13
Yeah, I've done this many times. However, I usually do df to see the drives, then use the /dev/sda3 (or whatever) in the mount. I don't see the extra drive in the virtual Linux even though I add it as Sata 1 (Sata 0 is the boot obviously) in VBox. Follow?

Thanks for replying :-)

---

