---
title: "Migration"
date: 2017-01-26
forum: Server Platforms
---

### Post by andrea-c on 2017-01-26
Hello
I'm planning to update Ubuntu from 14.04 to 16.04 server and I want to migrate some configurations.

I'm currently use samba with the GUI interface
Is there a way / which files should I consider if I want to keep the same shared list of devices/NAS folder from my actual OS setup to the new one?
GUI option is not available with Ubuntu server or am I wrong?

---

### Post by ajgreeny on 2017-01-26
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit.

---

### Post by andrea-c on 2017-01-26
thanks ajgreeny

---

### Post by mastablasta on 2017-01-27
> **andrea-c said:**
> 
GUI option is not available with Ubuntu server or am I wrong?

server is usually ran via CLI, but you can use various webgui's (for better efficienty) or a desktop on it if you want to. it is your machine.

there are a couple of web gui available. i use Ajenti, but there is also for example Zentyal. there are others out there to explore.

server uses configuration files which for samba are in /etc/samba
more on samba:
[SIZE=2]https://help.ubuntu.com/community/Samba
[/SIZE]
samba also has some option on it's own: [SIZE=2]https://www.samba.org/samba/GUI/
[/SIZE]

---

### Post by andrea-c on 2017-01-31
Thanks a lot

I know, I want to avoid GUI but boss is not comfortable to use terminal so better provide him with a GUI as well.

---

### Post by TheFu on 2017-02-01
I always give the clients full admin access to their systems. After they break it, I'm paid time + materials and 2x time during non-business hours!  Nice, unexpected bonus for their own screw up. ;)

The way to avoid surprises is to practice the migration a few times. Use virtual machines for this. It is also a good chance to validate the backups and restore methods/techniques used are working correctly.

If you do add a GUI, be certain to lock down the access so that only people authorized even have a chance to see it.  For example, running a webGUI that only allows connections from localhost, never through a NIC.  That way, only people with ssh (and knowledge to setup an SSH PROXY) can use it. That isn't much of a barrier, but it will keep the script kiddies on the subnet away when they only find ssh open.

---

