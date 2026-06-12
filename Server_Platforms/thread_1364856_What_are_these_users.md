---
title: "What are these users?"
date: 2009-12-26
forum: Server Platforms
---

### Post by Sejanus on 2009-12-26
Command lastlog shows me quite a few users on ubuntu server, whom I never created nor have I any idea where they came from. Are there any default users with new ubuntu install, or maybe some sofware creates them? Is it any to way to see what uses them? Is it safe to delete them? Some names are quite descriptive, e.g. mysql, but I'm sure my mySQL server runs as a different user and never ran as "mysql" one.

List is here (apart from those I created myself):

> 
daemon   **Never logged in**
bin          **Never logged in**
sys          **Never logged in**
sync        **Never logged in**
games     **Never logged in**
man        **Never logged in**
lp           **Never logged in**
mail        **Never logged in**
news       **Never logged in**
uucp                                       **Never logged in**
proxy                                      **Never logged in**
www-data                                   **Never logged in**
backup                                     **Never logged in**
list                                       **Never logged in**
irc                                        **Never logged in**
gnats                                      **Never logged in**
libuuid                                    **Never logged in**
bind                                       **Never logged in**
fetchmail                                  **Never logged in**
sshd                                       **Never logged in**
klog                                       **Never logged in**
syslog                                     **Never logged in**
smmta                                      **Never logged in**
smmsp                                      **Never logged in**
messagebus                                 **Never logged in**
polkituser                                 **Never logged in**
haldaemon                                  **Never logged in**
mysql                                      **Never logged in**


---

### Post by CharlesA on 2009-12-26
They are system accounts.

---

### Post by Jekshadow on 2009-12-27
I do not recommend deleting them, as some (haldaemon, syslog) are required by core system components and deleting others could screw up the program that uses them.

---

### Post by Sejanus on 2010-01-04
OK thanks ;)

---

### Post by HighCommander540 on 2010-01-04
> **Sejanus said:**
> OK thanks ;)

BTW, MySQL does actually run as the user MySQL.

---

### Post by Lars Noodén on 2010-01-04
Many, if not most, services run as daemons and need root privileges to attach to various ports or sockets.  After that, they no longer need root privileges and can get by with something lesser.  

So, these users are one per service so that if something does go wrong, the damage, or access, is limited to only what that low-privilege user can do.  For example, if the user **mysql** cannot write to the web server's documents, then it cannot erase them...

---

