---
title: "Can I forbid an empty passphrase of SSH key?"
date: 2008-09-17
forum: Security
---

### Post by snowboard975 on 2008-09-17
I want to setup an SSH on a server where many users connect through the internet. 
I plan to use key-based SSH authentification. But I worry about the empty passphrase a user might use when he or she generate a key by "ssh-keygen -t dsa" command.
A key with empty passphrase would be a security hole because stolen key would make anybody to connect to the server anytime anywhere.

Is there any method to prevent a user from using the empty passphrase when he or she generate a key?

---

### Post by kevdog on 2008-09-17
What would be the difference if your end user generated a ssh key, and then blabbed the password to as many friends as possible?  The overall risk to your server would still be the same.  Perhaps you should think about restricting your ssh users to a jail to limit the kinds and types of programs the user can run on the server.  I personally use the jail-kit implementation, however there are others such as rssh.  

Specifically regarding your question -- I dont know a way to force the user to select a password short of editing the ssh-keygen source.

---

### Post by bodhi.zazen on 2008-09-17
Well, as the admin of the server, why don't you hand out the keys yourself then ?

---

### Post by mgjv on 2008-09-27
If you hand out the keys yourself, there wouldn't be anything to prevent the user from resetting the passphrase to empty, right? 

Once the key has been handed over, the user necessarily has full control over it. How would you prevent them from resetting passphrases?

---

