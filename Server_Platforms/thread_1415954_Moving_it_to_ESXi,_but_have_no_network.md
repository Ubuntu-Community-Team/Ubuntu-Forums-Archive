---
title: "Moving it to ESXi, but have no network"
date: 2010-02-25
forum: Server Platforms
---

### Post by mickey78 on 2010-02-25
Hey guys.

I have this 7.10 Ubuntu server that I'm trying to move inside a VM on my ESXi server. I use the VMware Conversion tool and everythings goes well until I try to boot it from inside the VM, the network isn't detected. Now I understand that the drivers may not be working, I'm not an expert here. Also, since this is a 7.10 install I don't have access to the Gutsy repositories anymore. If you have any idea, I would really appreciated it. Thanks

---

### Post by mogray on 2010-02-25
I had a similar problem with 9.04.  Turned out to be a mac address config issue.  Option 1 worked for me but option two might also work from what I've read.  Not sure if this applies to your version.

Steps Option 1:

• open file /etc/udev/rules.d/70-persistent-net.rules in text editor
• change remove the line containing "eth0"
• rename teh line containing "eth1" to "eth0"
• restart udev

Steps Option 2:

• Delete or move both ".rules" files located in /etc/udev/rules.d
• restart udev

---

### Post by mickey78 on 2010-02-25
Thanks for your reply. 

You tha man! I got it working, thanks!

---

### Post by mickey78 on 2010-02-25
.

---

