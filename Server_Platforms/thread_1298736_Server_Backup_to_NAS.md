---
title: "Server Backup to NAS"
date: 2009-10-23
forum: Server Platforms
---

### Post by espresso_steve on 2009-10-23
I have Ubuntu 9.04 server connected to a MS domain (business network). I need to back it up...  preferably scheduled to do full backup once a week to a NAS box on the network, then daily incremental overnight through the week.  

As a total beginner to Linux... how's this done?

---

### Post by ^_Pepe_^ on 2009-10-23
Hi!

Not sure if I can help you, but I'll try. I have a NAS box at home to make daily backups.

Mainly you have to do two tasks.

1st: Automatically mount the NAS box as a unit drive. Please let me know if you know how to do it. Basically yo have to put a new line in your /etc/fstab file.

2nd: Install, from synaptic, 'simple backup' application. Simple, very simple, but can make whatever you may need.

Hope that it helps.

Regards,
^_Pepe_^

---

### Post by espresso_steve on 2009-10-26
Pepe
 
The 'simple backup' app. is perfect.  Basic but powerful tool that does everything I need.
 
Thanks
 
Steve

---

### Post by jminnick on 2009-10-26
i am going to try this as soon as I get home. I hope it works just as easy.

---

