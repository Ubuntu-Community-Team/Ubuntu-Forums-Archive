---
title: "No password prompt when installing Skype"
date: 2006-07-19
forum: Server Platforms
---

### Post by nirudha on 2006-07-19
Hi,

I am not sure if this is a real big isssue or not. I am a new user of Linux (few days) and am quite happy with the Sudo scheme, so much so I am using winsudo on my XP machine. But when I downloaded and ran the Skype Deb package the installer didn't ask me for a password but just gave me a prompt which stated that this operation needs admin rights and had two buttons. One was grant rights which allowed the installation with no password entered.

Isn't this a potential risk? If someone finds an unlocked desktop they can install some software without knowing a password.

---

### Post by aysiu on 2006-07-19
When you run *sudo*, you're not asked for another password again until the timeout is over (I think it's something like 10 minutes).

You can change the timeout, though:
[http://ubuntuforums.org/showpost.php?p=116697&postcount=6](http://ubuntuforums.org/showpost.php?p=116697&postcount=6)

---

### Post by nirudha on 2006-07-19
Thanks for the link. I can't recall giving the password within such a short period of time but I guess I could be mistaken.

---

### Post by MrHorus on 2006-07-19
> **nirudha said:**
> Thanks for the link. I can't recall giving the password within such a short period of time but I guess I could be mistaken.

That is one possibility, yes.

The other is that it is installed under the local username in which case it wouldn't need to modify anything owned by root and thus, wouldn't require sudo although if it actually states it requires admin rights...

*plumps for the first possibility*

---

