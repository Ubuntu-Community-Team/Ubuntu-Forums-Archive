---
title: "Keep SSH private key secure on Windows machine"
date: 2009-12-26
forum: Security
---

### Post by BlakeM on 2009-12-26
Hi all,


I have set up OpenSSH using public/private keys so that my netbook running Windows XP and PuTTY (the client) can remotely access an Ubuntu desktop running openssh-server (the server).  My private key is stored only on the windows netbook and is protected by a passphrase.  I understand this private key must be kept private.

My main question is how do I keep this private key private using Windows?  What security measures does Windows offer that I can use to make sure the private key doesn't end up on the Internet?  Or should I just make sure that the passphrase I use is really, really good?

Would using a really secure password for Windows administrator also help?


Thank-you :)

---

### Post by CharlesA on 2009-12-26
How would it end up on the internet, if you don't put it there yourself?

I lock down the permissions to just myself (not that it would help all that much if someone has physical access to the machine, but physical access > all)

Good passwords are a start.

---

### Post by BlakeM on 2009-12-26
Lol, good point.  So, as long as I'm running antivirus on windows and take steps to prevent physical access I should be ok with the windows machine?  It just made me a bit nervous with the private key sitting in "My Documents". Compared with Ubuntu where I had to set correct permissions, etc.

---

### Post by CharlesA on 2009-12-26
I have it in the same folder as Putty, with the permissions changed. :)

I was carrying it on a usb stick, but it was getting annoying to have to plug it in every time I wanted to access the machine.

---

