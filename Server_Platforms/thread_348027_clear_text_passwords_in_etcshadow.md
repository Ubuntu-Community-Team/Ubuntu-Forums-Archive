---
title: "clear text passwords in /etc/shadow ??"
date: 2007-01-28
forum: Server Platforms
---

### Post by JimTDI on 2007-01-28
I've noticed -some- of the entries for users in my /etc/shadow file have the user passwords in clear text, and some have them encrypted.  The ones in clear text appear to be the users I changed passwords on, or created, by using the usermod -p and/or the adduser -p commands.

Does this make sense?  I'm still kinda new to doing all of this (working with user accounts) on the command line (Ubuntu Server) so I probably screwed something up when I ran the above commands.

---

### Post by Koybe on 2007-01-28
I don't know this way of changing passwords. The usual way is :
```
passwd username
```
What if you do it this way?

---

### Post by JimTDI on 2007-01-28
> **Koybe said:**
> I don't know this way of changing passwords. The usual way is :
```
passwd username
```
What if you do it this way?

I tried what you said - and it works (password is encrypted in /etc/shadow) and now that user can login!  Thanks for helping a command line newbie!! :D

---

### Post by Koybe on 2007-01-28
NP, happy it can help :)

---

