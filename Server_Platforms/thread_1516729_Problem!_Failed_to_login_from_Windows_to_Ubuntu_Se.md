---
title: "Problem! Failed to login from Windows to Ubuntu Server"
date: 2010-06-24
forum: Server Platforms
---

### Post by brucelok on 2010-06-24
Hi, I am new in Ubuntu.
I have recently installed an Ubuntu Server 10.02 as a File server in my company, and sharing files for about 20 windows vista/xp desktops.

However, I have a problem to share files with login/password protected.  I have simply created some user accounts with password in the Ubuntu File server. Every time the user logging in from windows xp/vista, it comes up with a login dialog windows, but it never login successfully. It just keep saying "incorrect login information" or "multiple login occurs" [I'm sure all user ID and password are correct]

Now all folders and files in my file server are free to list, read, write, modify and even delete. What I want is user-based login restriction.  To access the specific folder and file from the Ubuntu file server, everyone has to login with password.

Could anyone please instruct me how to do it?
Thank you!

---

### Post by volkswagner on 2010-06-24
Did you create linux users or samba users.

Most likely you need to setup individual samba users.

---

### Post by brucelok on 2010-06-24
> **volkswagner said:**
> Did you create linux users or samba users.

Most likely you need to setup individual samba users.

yes i ve already created some linux users, but not yet created in samba.

thank you!

---

### Post by brucelok on 2010-06-25
> **volkswagner said:**
> Did you create linux users or samba users.

Most likely you need to setup individual samba users.

yes i ve already created some linux users and samba users, but it doesn't work.

what can i do?

---

### Post by clrg on 2010-06-25
Let me see your /etc/samba/smb.conf

---

