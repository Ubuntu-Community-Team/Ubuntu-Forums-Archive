---
title: "ssh-agent loading at startup?"
date: 2009-11-28
forum: Security
---

### Post by Engromada on 2009-11-28
Is it normal for "ssh-agent" process to be loading by default when it's not in the startup apps list?

I'm just a tincy bit over paranoid, but evolution mail seemed to open by it's self, so i scrutinised my processes list (even though it means very little to me, as a recentish linux convert.


Thanks

---

### Post by Aearenda on 2009-11-28
Yes, ssh-agent is normal.

---

### Post by Engromada on 2009-11-28
*Breathes a sigh of relief*

---

### Post by OpSecShellshock on 2009-11-28
Actually, that makes me wonder about something else. Is there any reason it needs to be running if I don't want to allow remote access to my computer? To put it another way, is there anything other than remote login that depends on it?

---

### Post by Aearenda on 2009-11-28
It is there to give you easy access to **other** computers without entering your passphrase every time. It doesn't provide remote access to your computer - that would be /usr/sbin/sshd.

---

### Post by The Cog on 2009-11-29
Agreed. I think it's the little background program that remembers the password you use when you ssh into a remote computer so you don't have to enter it next time you connect to the same host in the same login session - think of the popup that asks if you want to remember the password until you log out.

---

