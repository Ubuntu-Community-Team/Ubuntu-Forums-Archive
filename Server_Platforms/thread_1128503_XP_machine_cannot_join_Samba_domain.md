---
title: "XP machine cannot join Samba domain"
date: 2009-04-17
forum: Server Platforms
---

### Post by Celauran on 2009-04-17
I'm trying to set up a Hardy server as a Samba PDC. I have followed tutorials on both [samba.org](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html) and [help.ubuntu.com](https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html) and am pretty sure my smb.conf is fine as I am able to map a drive. I run into problems, however, when I try to join the XP Pro box to the domain. I get the following error:

"The following error occurred attempting to join the domain UBUNTU: Access is denied"

All the tutorials I have read suggest using the root username/password when prompted but, for obvious reasons, this won't work on an Ubuntu install. I'm using my own account (which has sudo priveleges) instead. I have tried using the add machine script outlined in the 8.10 server guide as well as setting up the machine user manually, all to no avail. I'm sure it's something obvious that I've overlooked but I have fairly run out of ideas.

Anyone encountered anything like this?

---

### Post by DJonsson2008 on 2009-04-17
I'd have to dig through my notes, but in the end I may of not ended up
using the domain method, somehow it seems my samba is working as a workgroup and in samba like with windows there seems to be a difference.

another entry point was having matching username/passwrd accounts on both windows and ubuntu sides of the equation.

---

### Post by Celauran on 2009-04-17
Setting it up as a workgroup member works fine, it's strictly when I try to set up the PDC that I encounter problems. Windows user has a valid Linux account and an active Samba account, all three sharing the same password.

---

### Post by freebeer on 2009-04-18
Would this be an XP Home version?  MS deliberatly disabled the ability for Home to connect to a domain.  (Although I've read that there is a work-around for it.)

---

### Post by Celauran on 2009-04-18
My bad, I thought I had specified that. It is an XP Pro machine, so the ability to join a domain exists. Original post updated.

---

### Post by brianhenson on 2009-04-19
Celauran,

I can't remember but i think you have to create a computer account as well when you add it to a domain.  I think I had to do that manually once before with an error close to that.  Hope this helps


Brian

---

### Post by Celauran on 2009-04-20
Managed to get it connected but had to unlock the root account to do so.

---

