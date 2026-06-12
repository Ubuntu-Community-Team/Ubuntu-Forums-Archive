---
title: "No password SSH access on multiple servers"
date: 2007-09-26
forum: Server Platforms
---

### Post by Saphira on 2007-09-26
Can one server share auth'ed keys for more than one server on the network via ssh pub key?  

I have one server that needs to have no password access to 7 different servers on the network via SSH 

Can one server have id_dsa keys shared on more than one box 
and if so, how do you do it?

---

### Post by PilotJLR on 2007-09-26
Yes! It should work if you append each public key to your authorized_keys file. I know for sure it works on Red Hat, and I *think* it's the same procedure on Ubuntu.
For example here is a consise one:
[http://www.linuxproblem.org/art_9.html](http://www.linuxproblem.org/art_9.html)

---

### Post by Saphira on 2007-09-26
do the RSA keys need to live on both servers or just the one?

---

### Post by PilotJLR on 2007-09-26
The private key would like on the one server, but the other server would have to have the corresponding public key... so each server would need 1 key from the key pair.

---

### Post by netlogic on 2007-09-26
Yes, you can use one public and private key for different server. Just use it same way you will do with one pair. If you want things to be automatic, check out seahorse. If you are going to use the same public/private for many servers, make sure your passphrase is very strong. If your goal is desktop machines with a same configuration and trying to apply manual patches, check out clusterssh to control multiple ssh or rsh sessions from a single input window.

---

