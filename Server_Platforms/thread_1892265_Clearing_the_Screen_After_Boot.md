---
title: "Clearing the Screen After Boot"
date: 2011-12-07
forum: Server Platforms
---

### Post by dstnvns on 2011-12-07
Despite physical security for the server I have a problem with the start-up information showing after boot is complete. Not knowing which services a server runs makes it a tad more fun for anyone to access the system.

Short of logging on and then off, I can't figure out how to clear the screen before displaying the log-in prompt on any server version.

Any ideas?

---

### Post by jonobr on 2011-12-08
Hello

AFAIK  modifying grub (HANDLE WITH CARE!!) in /etc/default/grub has an option for 
suppressing messages
Looking at mine i think its

> GRUB_CMDLINE_LINUX_DEFAULT="quiet"

and then 

> sudo update-grub

I recall it didnt get rid of everything and removing quiet resulted in more output

Again, be extra careful!

---

