---
title: "I cant login!!!"
date: 2009-01-24
forum: Server Platforms
---

### Post by abbec on 2009-01-24
After rebooting Ubuntu server 8.10 after som e cups tweaking, i cant login! It says nothing about incorrect or invalid password, it just gives me the login again. Any ideas?

---

### Post by sisco311 on 2009-01-24
Did you try to boot in recovery mode?

---

### Post by abbec on 2009-01-24
I can do everything usual in recovery mode as root.

It just loops the login but never logs me in!

---

### Post by abbec on 2009-01-24
Please help me with this i really need it.

---

### Post by sisco311 on 2009-01-24
You posted your question in the Server Platforms forum.
Are you using a GUI (login manager, DE)?
Any error message when you try to log in?
Did you try to change your password?

---

### Post by albinootje on 2009-01-24
> **abbec said:**
> After rebooting Ubuntu server 8.10 after som e cups tweaking, i cant login! It says nothing about incorrect or invalid password, it just gives me the login again. Any ideas?


Do you have enough free disk space ?

To reset your password :
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by abbec on 2009-01-24
> **sisco311 said:**
> You posted your question in the Server Platforms forum.
Are you using a GUI (login manager, DE)?
Any error message when you try to log in?
Did you try to change your password?

No I'm not using GUI, no error message it just gives me a new login.

Yes I've tried to create a new account but that doesn't help either...

---

### Post by abbec on 2009-01-24
> **albinootje said:**
> Do you have enough free disk space ?

To reset your password :
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I've already reset it and yes I have enough free space.

---

### Post by albinootje on 2009-01-24
> **abbec said:**
> I've already reset it and yes I have enough free space.

Can you then boot from the recovery mode, and post here *any* error messages from the files /var/log/syslog and /var/log/syslog.0

---

### Post by abbec on 2009-01-24
> **albinootje said:**
> Can you then boot from the recovery mode, and post here *any* error messages from the files /var/log/syslog and /var/log/syslog.0

This is the only related message i can see:

Jan 25.... kernel: [  99.662439] login[5146: segfault at 0 ip b7ccbb0b sp bfacbbc0 error 4 in pam_smbpass.so[b7c6f000+12a000]

---

### Post by abbec on 2009-01-24
or what more specifically might I be looking for? :)

---

### Post by albinootje on 2009-01-24
> **abbec said:**
> This is the only related message i can see:

Jan 25.... kernel: [  99.662439] login[5146: segfault at 0 ip b7ccbb0b sp bfacbbc0 error 4 in pam_smbpass.so[b7c6f000+12a000]

Very good!
Please check the comments here :
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/260687](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/260687)
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/303458](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/303458)

---

### Post by abbec on 2009-01-24
It is Working!!!! :D Thank you very much. You can now mark this tread solved.

---

