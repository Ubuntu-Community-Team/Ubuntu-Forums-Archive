---
title: "VNC Lockdown?"
date: 2006-09-29
forum: Server Platforms
---

### Post by x64Jimbo on 2006-09-29
Hi there! 
I have a server with several users plus myself. I want to prevent the users from running any sort of gui - I have VNC server installed for myself, but I would like to deny them the ability to start their own vnc sessions and even open any ports period. If I block the VNC app specifically, they can always download a standalone VNC server and run it from their home directory.
I don't want to have to do something silly like a cronjob that recursively scans for and deletes all files containing the phrase "vnc" from their home folder every 30 seconds, but after nearly an hour of searching around, I'm beginning to think that it might not be such a bad idea. 
Thanks in advance,
~Jimbo

---

### Post by Ayman on 2006-09-29
Here is what I suggest:
1) Block ALL ports (using [Iptables](https://wiki.ubuntu.com/IptablesHowTo), Firestarter, or whatever tool you are familiar with).
2) Enable ports that you need to use (for example VNC).
3) Start the daemons that use the open ports.

This way, your users won't be able to start services that listen to ports because all ports are either blocked or already in use.

Also, don't forget to password-protect VNC.

This can be hardened further, for example, you can prevent users from downloading and running programs (mount /home and /tmp noexec). It really depends on your users' needs, give them the minimal permissions they need to do their work on your server.

---

### Post by x64Jimbo on 2006-09-29
But they can get past the firewall with SSH tunneling. That's how I'm getting in.

---

### Post by Ayman on 2006-09-29
Hmm, in this case I'd search for a way to restrict access to X, I'm sorry but I'm not familiar with such a thing, but logically there should be some way to control who can login to X.

---

### Post by x64Jimbo on 2006-09-30
Thanx for the tip. I'll look around and post back if I find something.

---

