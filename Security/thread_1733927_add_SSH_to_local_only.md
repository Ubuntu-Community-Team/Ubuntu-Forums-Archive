---
title: "add SSH to local only"
date: 2011-04-19
forum: Security
---

### Post by mynameisnotbob on 2011-04-19
On a test ubuntu computer at my work, tests run often run wrong and all privleges for all accounts are revoked. This is, to say the least, annoying. Is there any way to create a SSH password for just that console to access it locally in the event of such a lockout? We cannot connect any other computers to it for security concerns.

---

### Post by bodhi.zazen on 2011-04-19
Why not simply boot to recovery mode or a live CD and do your repairs ?

I do not understand how ssh is going to help.

You can restrict ssh to localhost if you desire, you can use iptables or /etc/hosts.deny (or both).

---

### Post by mynameisnotbob on 2011-04-19
> **bodhi.zazen said:**
> Why not simply boot to recovery mode or a live CD and do your repairs ?

I do not understand how ssh is going to help.

You can restrict ssh to localhost if you desire, you can use iptables or /etc/hosts.deny (or both).
If only it were that simple...recovery mode is disabled. This is a penetration test box, so it is very secure, that includes no root access from GRUB.

---

### Post by dfreer on 2011-04-20
I'm really confused. You say all privileges for all accounts get revoked, does that mean users can no longer log in locally? If so, SSH will not help since you need to be able to log in to use it. 

And also, don't understand why you disable recovery mode and make it harder on yourself. Anyone who has physical access to that machine can compromise it fairly easily, and if it's secured properly from unauthorized physical access, why lock physical access down?

---

### Post by mynameisnotbob on 2011-04-20
OK thank you. That's what I needed to know. I was trying to ask whether there was a way to use SSH w/o being logged on, but the answer is no. Thank you.

---

### Post by bodhi.zazen on 2011-04-20
> **mynameisnotbob said:**
> OK thank you. That's what I needed to know. I was trying to ask whether there was a way to use SSH w/o being logged on, but the answer is no. Thank you.

You can connect via ssh from a remote machine via keys or kerberos, both of which are considered secure.

---

### Post by dfreer on 2011-04-20
Yes, I didn't really explain what I meant well, I was trying to determine your intention. As stated, using a ssh key would allow you to login even if the user's password has changed, as long as the key hasn't been revoked. 

But if the user's shell has been changed to something like /sbin/nologin, or *possibly* if the user's account has been locked (haven't tested that myself) ssh will not work.

---

