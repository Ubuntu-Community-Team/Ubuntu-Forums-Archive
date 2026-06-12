---
title: "SSH Private - Public Key question"
date: 2016-09-04
forum: Security
---

### Post by Pandee on 2016-09-04
Hello! This may be a silly question, but im not sure about it...

I'm starting up a 16.04 server - And my questions are:

- Do i need to create a Pub-priv key to access the server via SSH per a user? Or is it set out so it is shareable? If its not shareable how do i do it? Do i login as the other user and proceed from there (or can I do it from the user with root access?) ?

---

### Post by ajgreeny on 2016-09-04
See [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) for all the information you could need about this.

If you still have questions after reading this come back again.

---

### Post by HermanAB on 2016-09-04
Howdy,

By default on server, you can log with ssh using username and password.  You will then get a console that will work the same as a keyboard and screen plugged directly into the machine.

To use keys, the user needs to generate a key pair and upload the private key to the ~/.ssh directory of the user.  Do not reuse a key pair or passwords on multiple machines.

---

