---
title: "Windows XP Can't Find Samba Domain"
date: 2009-07-14
forum: Server Platforms
---

### Post by lightnb on 2009-07-14
I have a Windows XP Machine, and an Ubuntu 9.04 Server running Samba.

I can see the shares from the Windows machine by entering "\\hostname" into Windows Explorer. I can also access them with my user name and password.

When I try to join my domain, however, Windows asks for a user name and password, pauses for a minute, and then tells me "The specified domain either does not exist or could not be contacted."

Nothing shows up in /var/log/samba/log.clienthostname.

What does Windows use to find the domain controller? The hostname? A FQDN? What should I check?

---

### Post by lightnb on 2009-07-14
It magically started working... Not sure Why.

---

