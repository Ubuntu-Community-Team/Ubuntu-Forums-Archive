---
title: "How do I create a new user on Kali?"
date: 2016-09-19
forum: Ubuntu/Debian BASED
---

### Post by dcpifhq on 2016-09-19
Hi,
I have been using the root account ever since I got a Raspberry Pi, and figured that root account should not be used like a regular user.
So, how do I make another user account?

---

### Post by howefield on 2016-09-19
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Roger_Williams on 2016-09-28
> **dcpifhq said:**
> Hi,
I have been using the root account ever since I got a Raspberry Pi, and figured that root account should not be used like a regular user.
So, how do I make another user account?

In terminal use the command adduser then type a name for your user then a password twice. You will not see the password as you type it so type and hit enter and after that you're all done. Log off as root and login as the new user. Just remember that once you login as the new user you will have to use either su or sudo when you do commands that require root privilege. You become accustomed to not doing that when you're operating as root so it's a bit getting used to or it was for me.

---

### Post by yancek on 2016-09-28
Kali Linux is designed to be used for computer forensics and penetration testing and by default runs as root.  It is not a good distribution to run as a Desktop system as explained at the Kali site.  If you want to learn computer forensics using Kali, you would probably be better off using a flash drive with a persistent system which is explained in detail at the Kali site.

---

### Post by dcpifhq on 2016-09-30
Thanks! All clear now!

And btw I am using Kali just for learning. I am not doing anything illegal or anything with no permissions.

---

