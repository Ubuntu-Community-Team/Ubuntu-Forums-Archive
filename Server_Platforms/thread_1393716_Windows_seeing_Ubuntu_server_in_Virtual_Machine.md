---
title: "Windows seeing Ubuntu server in Virtual Machine"
date: 2010-01-29
forum: Server Platforms
---

### Post by M-ManLA on 2010-01-29
Ok. I'm having a slight problem. I am testing out Ubuntu Server 9.10 in VirtualBox on my Windows rig, and I am trying to figure out how to let Windows 7 64Bit "See" the server or network drive so I can map it within W7 to test out the file and backup. Is there a command line I have to learn? Please let me know and thank you in advance.

---

### Post by pirateghost on 2010-01-29
have you configured samba properly?

---

### Post by M-ManLA on 2010-01-29
> **pirateghost said:**
> have you configured samba properly?

I did install samba. If I have to configure it I would not know what to do. I am a newbie sorry. Is there a command I have to relay to samba?

---

### Post by Ryan Dwyer on 2010-01-29
I believe you need to install the winbind package in Ubuntu to make it broadcast its hostname.

---

### Post by M-ManLA on 2010-01-29
> **Ryan Dwyer said:**
> I believe you need to install the winbind package in Ubuntu to make it broadcast its hostname.

Ok I'll check it out later

---

