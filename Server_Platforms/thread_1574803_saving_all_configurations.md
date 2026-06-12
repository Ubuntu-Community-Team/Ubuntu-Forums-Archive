---
title: "saving all configurations"
date: 2010-09-14
forum: Server Platforms
---

### Post by rbalaa on 2010-09-14
Hi All,

I bought a new server and I want to install Ubuntu on it but also want to transfer all my configurations on my current server to the new one.

Is there any tool out there that I can use to build and image of my current Ubuntu server so that I can deploy it elsewhere ? Or just copying everything under "/etc" and then pasting it into the new server ?

Any advice.

Thanks in advance.

---

### Post by Darent on 2010-11-22
Hello there.

I've never used the server edition so i cannot be sure, but in desktop-edition  /etc only contains the default configurations of the system, not the config than you set or change. When you install a new program and run it for the first time, its config file is copied to your home so you can modify it without changing the default. But if you want to transfer your personal config, you need to copy the hidden files of /home/youruser

In case you are using it only as root, the config files must be the same files but stored as hidden on /root

Instead of copying it, you can use some backup program like simplebackup (don't remember the exact name, google it). I use ubuntu-tweak, it has a section to backup/restore your setings. You'll need to do a backup with it, copy the backup files and restore them with the new system using the same program.

I wish it helps, good luck :)

---

### Post by koenn on 2010-11-22
copying /etc should be sufficient, unless you've installed software that uses it's on hierarchy and has config files : /opt/program-name/etc or some other non-standaard directory (/usr/lib/...  and /usr/share/... are also likely candidates).
Software from Ubuntu repos should be standard, though, and have its config under /etc.

you will, of course, have to install the relevant programs on your new machine, and you'd also have to transfer any data the server holds.

Since a server isn't meant for personal use, you can ignore what Darent says about configuration in home dirs, server config should be system-wide, not user-specific. The only 'config' you'd have in root would be things like root's vim preferences and such; you may want to keep that, but it's not your server configuration. If your server serves home dirs to  users, that falls under "data", it's also not config. 

you might want to be careful about copying files such as /etc/passwd, /etc/groups, and /etc/shadow 


"cloning" or imaging only works reliably  if your new machine is identical or sufficiently similar to the old one.


you may get some inspiration here:
[http://users.telenet.be/mydotcom/howto/linux/automatic.htm](http://users.telenet.be/mydotcom/howto/linux/automatic.htm)

---

