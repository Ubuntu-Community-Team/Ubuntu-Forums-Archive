---
title: "Ubuntu server stuck at Resizing Partition.."
date: 2015-11-21
forum: Server Platforms
---

### Post by soamz on 2015-11-21
What to do ?

The screen shows the same since last 1 hour. 

Is there a problem ?
How do I skip this step or cancel it ?

Whats wrong ?

[ATTACH=CONFIG]265708[/ATTACH]

---

### Post by SeijiSensei on 2015-11-21
What have you tried since, if anything?

If this is a server, will Ubuntu be the only operating system you need to boot?  If so, why are you resizing?  Are you trying to preserve a Windows installation?  

If the machine has 4GB or more memory, and you want to keep Windows, consider installing VirtualBox for Windows then creating a virtual machine running Ubuntu Server.  If you use a "bridged" network adapter, the virtual machine will appear directly on your network.  If you don't have many clients to serve, neither you nor they will notice that the server is running as a virtual machine.

---

### Post by Vegan on 2015-11-22
Unfortunately VirtualBox is not working with Windows 10 last time I checked.

---

