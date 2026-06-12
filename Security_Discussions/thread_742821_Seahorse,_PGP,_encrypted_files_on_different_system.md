---
title: "Seahorse, PGP, encrypted files on different systems...."
date: 2008-04-02
forum: Security Discussions
---

### Post by giorgosc61 on 2008-04-02
&#919;&#953;,

I have installed seahorse on my ubuntu laptop and through

Applications -> Accessories -> Passwords and Encryption keys

I did created a new key Myname Mylastname [email]myname@mymail.com[/email].

I used pgp though console to enrypt a tar file using [email]myname@mymail.com[/email].

I installed ubuntu on my desktop and seahorse and i searched with find remote keys for [email]myname@mymail.com[/email] and imported the key.

I tried to decrypt the file in the desktop machine and it show an error and does not prompt for a password like it does on my laptop.

What am i doing wrong?

---

### Post by hyper_ch on 2008-04-02
I think you only imported the public key and not private one.

---

### Post by giorgosc61 on 2008-04-02
How can I import the private key?

---

### Post by hyper_ch on 2008-04-02
you need to export it first...

or simplest way would be to copy the ~/.gnupg folder

---

### Post by giorgosc61 on 2008-04-02
Thank you,

I will try copying of the folder to the other computer in the evening.

---

