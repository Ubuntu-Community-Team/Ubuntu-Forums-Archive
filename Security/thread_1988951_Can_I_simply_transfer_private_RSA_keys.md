---
title: "Can I simply transfer private RSA keys?"
date: 2012-05-28
forum: Security
---

### Post by frotzed on 2012-05-28
I understand this may be a bit basic, but I do appreciate any help that is offered.

I set up RSA key authentication between my laptop (running 12.04) and my web server so I an ssh to the server without a password.  It all works flawlessly.

Lets say I wanted to reinstall 12.04 for some reason.  Or, maybe I wanted to authenticate my desktop (also running 12.04) to my web server. Can I simply copy the RSA keys in my ~/.ssh directory to the ~/.ssh directory of the other computer and have everything work flawlessly?

It's simply the _presence_ of the key in the proper directory that authenticates the computer, correct?

---

### Post by Ms. Daisy on 2012-05-28
Kind of.  There's a public and a private key.  When you generated keys on the laptop, you transferred the public key over to the server.  You never share the private key.

I would generate new keys on the desktop and transfer the public key over to the server if you want to also ssh from the desktop to the server.

---

### Post by frotzed on 2012-05-28
Gotcha, thank you for the response :)

---

