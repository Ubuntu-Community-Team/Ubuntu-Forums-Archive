---
title: "SSH keys"
date: 2011-04-28
forum: Server Platforms
---

### Post by I8NY on 2011-04-28
I want openssh to use key1 with user1 and key2 with user2.  I don't want key1 or key2 to access the other user.  Also how do I add key2 to authorized_files file with key1 already inside?  This is running on Ubuntu server 64bit 10.04

---

### Post by spynappels on 2011-04-28
Each user should have a .ssh directory in their home directory. For user1 you place key1 in the authorized_keys file in /home/user1/.ssh/ and for user2 you place key2 in the authorized_keys file in /home/user2/.ssh/.

Will these users be connecting from different client computers? Win or Linux? If you are using PuTTY (Win) you can specify a different key for any connection very easily.

---

### Post by HermanAB on 2011-04-28
Howdy,

Authorized_keys is a text file.  You can look at it with gedit or vi.  That way you can also selectively delete keys or copy and paste new keys into it.

---

### Post by I8NY on 2011-04-29
> **spynappels said:**
> Each user should have a .ssh directory in their home directory. For user1 you place key1 in the authorized_keys file in /home/user1/.ssh/ and for user2 you place key2 in the authorized_keys file in /home/user2/.ssh/.

Will these users be connecting from different client computers? Win or Linux? If you are using PuTTY (Win) you can specify a different key for any connection very easily.
wouldn't that not work if the sshd_config as key set as ```
AuthorizedKeysFile /home/user1/.ssh/authorized_keys
``` i get it if the client is connect but not for the host. (which is what i want) these will also be mostly windows machines from different pcs for user2 but linux only for user1 and only one pc. so can i set the key for each user to be used for logging into the host?

---

### Post by spynappels on 2011-04-29
In your sshd_conf you could say:

```
AuthorizedKeysFile %h/.ssh/Authorized_Keys
```

and this would reference each individual user's home dir.

---

### Post by I8NY on 2011-04-30
okay i did that and got the public key in /user2/.ssh/authorized_keys.  the problem now is i can't connect to user2 with user2 key.  user1 still works with key login but not user2.  is there some file permissions i need to set so openssh can access user2 authorized_keys file?

---

