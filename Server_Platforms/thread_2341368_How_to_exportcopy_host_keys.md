---
title: "How to export/copy host keys"
date: 2016-10-27
forum: Server Platforms
---

### Post by paul212 on 2016-10-27
I have a new Ubuntu 16.04 LTS server online in production mode.  The primary function of this server is SFTP.  All my clients except one were able to just manually SFTP into the new server and accept the new certs.  This one client wants me to send him the certs/pub keys but I am not sure how to get them off of the Ubuntu 16.04 LTS server.  He wants me to email them to him.   So could someone explain a step by step on how to do this?   Thank you

---

### Post by TheFu on 2016-10-27
You don't have the users make their own keys and upload the public parts?  The private ssh key needs to be private.

Don't email private keys without significant encryption.  email is like a postcard.  Any sufficiently secure encryption used to protect the keys would be 100x more complex than having them make their own and push the public keys to their account using **ssh-copy-id**.

---

