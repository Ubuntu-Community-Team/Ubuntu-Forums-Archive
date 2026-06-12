---
title: "&quot;Starting NFS kernel Daemon&quot; Hanging"
date: 2009-10-09
forum: Server Platforms
---

### Post by GriFF3n on 2009-10-09
I have 9.04 Ubuntu server running. I just did an update/upgrade on the system and performed a reboot. Now when i start the system it loads to the "Starting NFS kernel Daemon" and just hangs there. I'm unable to get the system up and I can not ssh into it. Any suggestions?

---

### Post by karlson on 2009-10-09
> **GriFF3n said:**
> I have 9.04 Ubuntu server running. I just did an update/upgrade on the system and performed a reboot. Now when i start the system it loads to the "Starting NFS kernel Daemon" and just hangs there. I'm unable to get the system up and I can not ssh into it. Any suggestions?

Boot into single user mode.
disable nfsd from running.

Then once booted.  Try Starting it manually to see what happens.

---

### Post by GriFF3n on 2009-10-09
> **karlson said:**
> Boot into single user mode.
disable nfsd from running.

Then once booted.  Try Starting it manually to see what happens.

How do I boot into "single user mode"?

---

### Post by karlson on 2009-10-09
> **GriFF3n said:**
> How do I boot into "single user mode"?

When you get the grub tickdown you can press ESC then a on the selected line and type in single at the end of the boot string.

Then press Enter.

---

### Post by GriFF3n on 2009-10-11
> **karlson said:**
> When you get the grub tickdown you can press ESC then a on the selected line and type in single at the end of the boot string.

Then press Enter.

Disabled nfs-kernel-server, but now it hangs at "Starting Samba daemons". Going to disable that and see what happens.

---

### Post by GriFF3n on 2009-10-11
Ok, she boots up, but for some reason it can not obtain an ip address. ifconfig shows no ip address. Samba and NFS were disabled from startup. When I boot the recover kernel, I can startup as "netroot" and will receive a default IP of 192.168.1.101. Any time I try to reload into my normal kernel, it is unalbe to obtain the static ip I have assigned it. Any other suggestions?

---

### Post by GriFF3n on 2009-10-11
Ok, so trying to restart my network through:



```
sudo /etc/init.d/networking restart
```

causes this error:



```
ifdown: failed to open statefile /var/run/network/ifstate: no such file or directory

ifup: failed to open statefile /var/run/network/ifstate: no such file or directory
```

still there, but i get an error of:


```
ifdown: failed to open statefile /var/run/network/ifstate: Is a directory

ifup: failed to open statefile /var/run/network/ifstate: Is a directory
```

Any ideas?

---

### Post by karlson on 2009-10-12
> **GriFF3n said:**
> Ok, so trying to restart my network through:


Any ideas?

Does /var/run/network exist?

---

### Post by GriFF3n on 2009-10-12
> **karlson said:**
> Does /var/run/network exist?

I have to create it everytime i restart the server. Once I make the directory and restart the network, everything works. It's listed as a bug on launchpad, but the solution is to delete the file "/etc/udev/rules.d/85-ifupdown.rules", which I do not have. Here's the launchpad [LINK]("https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/377432/").

---

### Post by GriFF3n on 2009-10-13
Bump, still having the same problem. Any suggestions?

---

### Post by karlson on 2009-10-13
> **GriFF3n said:**
> Bump, still having the same problem. Any suggestions?

You can try a few things:

1.  Try manually stopping and Starting NetworkManager to see if that removes the directory.
2.  Check the rc Scripts if any of them refer to /var/run/network
3.  based on what I see in /etc/network/if-up.d/mountfs it creates that directory, so you may have to debug the script to see why it doesn't in your case.

---

