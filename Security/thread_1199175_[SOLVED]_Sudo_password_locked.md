---
title: "[SOLVED] Sudo password locked?"
date: 2009-06-28
forum: Security
---

### Post by C++&gt;Java on 2009-06-28
I've got an Ubuntu Server running OpenSSH. After getting it set up with a key pair so I can authenticate without a password, I ran "sudo passwd -l [myusername]" as per some instructions I found [COLOR=Cyan]_[here]("http://ornellas.apanela.com/dokuwiki/pub:ssh_key_auth")_[/COLOR] to prevent remote users from logging in using anything but my private key. This worked as intended; however, I am now unable to use sudo once I'm on. I understand I could boot into the root shell and reverse this using "sudo passwd -u [myusername]", but I'd rather not - is there a way to lock an account like I did and still be able to "sudo" from it using it's password? Or is there a better way than locking to prevent random people from berading my port 22 with user/password logon requests?

Thanks.

---

### Post by rookcifer on 2009-06-28
You shouldn't need to lock the user account at all.  In sshd_config, set:

```
PasswordAuthentication no
```

That will do it.

Also, change the port from 22 to something else.  Yes, it's security through obscurity but it will help stop incessant brute force attempts.  You can also look into denyhosts or fail2ban.

---

### Post by C++&gt;Java on 2009-06-29
Brilliant! Thank you.

---

### Post by bodhi.zazen on 2009-06-29
> **rookcifer said:**
> You shouldn't need to lock the user account at all.  In sshd_config, set:

```
PasswordAuthentication no
```That will do it.

Also, change the port from 22 to something else.  Yes, it's security through obscurity but it will help stop incessant brute force attempts.  You can also look into denyhosts or fail2ban.

+1

Also, FYI, a few rules in IPTables will take the place of denyhosts or fail2ban.

---

