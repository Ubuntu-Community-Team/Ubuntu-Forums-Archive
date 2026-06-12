---
title: "security reason to isolate server daemons?"
date: 2009-01-06
forum: Security
---

### Post by Kain000 on 2009-01-06
I was wondering weather or not there is a security reason to isolate the SFTP daemons on a seperate box from my desktop.

I use my server to host my media over SFTP and my lan, and to torrent, but I dont see why I cant do all that from my desktop.

I believe SFTP is pretty secure, and I'm not that worried about being hacked.

Any advice?

---

### Post by bodhi.zazen on 2009-01-07
It is not really *that* big an issue and it is likely just fine to run a server on your desktop.

From a security viewpoint If you are running a server (or desktop) the less applications the less potential points of attack. Another advantage in keeping a server isolated would be your personal data.

For casual home use I am not sure it makes a huge difference to you.

Other options would be:

Run virtualization

Run your server on an old box. In the case of an isolated server why waste resources running an X server or what not.

---

### Post by Kain000 on 2009-01-09
I would like to be able to access my server from anywhere not just a pre specified network, like school or home.  How secure is SFTP to allow all requests on port 21, but require a user name and password?

---

### Post by hyper_ch on 2009-01-09
it all boils down to the username/password combination used IMHO

---

### Post by Kain000 on 2009-01-09
> **hyper_ch said:**
> it all boils down to the username/password combination used IMHO

alright then thanks to you both for the info

---

