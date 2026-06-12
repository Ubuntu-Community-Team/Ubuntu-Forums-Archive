---
title: "SSH Public Key"
date: 2010-11-17
forum: Server Platforms
---

### Post by trentscott on 2010-11-17
I'm trying to setup SSH key-based authentication between my Mac OS X laptop and an Ubuntu 10.10 Server. I've created the keys (both public and private) via Terminal on my Mac with ssh-keygen.

I opened up the generated id_rsa.pub (public key) generated on my Mac and noticed at the end it has a line in the form of <user>@<host> and the <host> attribute is currently set to my Mac's computer name.

Should I change this value to the name of my server instead (so it would read <user>@<server host>)? If I don't change it and it's supposed to stay the same, doesn't that mean each and every client has their own public key (with a custom <user>@<host> combination)?

---

### Post by ad_267 on 2010-11-18
No you can leave it as it is, it doesn't really matter what it says. I think that's just there so you can identify them easily.

---

