---
title: "SSH multiple clients w/RSA keys"
date: 2008-01-24
forum: Server Platforms
---

### Post by ecrissman on 2008-01-24
I am a little confused about this and need some help, although I am sure it is an easy answer. I have SSH working with RSA Authentication for my server and one remote client. How would I setup another computer to access the server with the right keys? Do I have to generate another pair of keys on the new client and add the public key to my authorized_keys on the server? Or do I have to copy the key that is on the first client to the new client so that they all match?

Thanks.

---

### Post by smileypaul on 2008-01-24
on the client computer, as the user you will be logging into your server with, you have to generate the key ..  then take the id_rsa.pub , copy it to the users home directory on the server.. make a directory in their home directory named .ssh .. and add it to a file called "authorized_keys" .. then they will be able to log in with that key..  

just make sure to remove unnecessary permissions on the keys..

---

### Post by ecrissman on 2008-01-25
Okay so I was reading in another forum that I can create a second pair of keys on the second client and copy to the server. My only other question is when I add the second key to my authorized_keys files on the server, how should that look? Does the second key go directly after the first or should there be a space?

**EDIT:**
It looks like it should be:
```
cat id_rsa.pub >> authorized_keys
```
which will add the second key.

Here are some links in case anyone else is confused:
[http://www.linuxquestions.org/questions/linux-server-73/openssh-with-multiple-secret-keys-491457/](http://www.linuxquestions.org/questions/linux-server-73/openssh-with-multiple-secret-keys-491457/)
[http://www.wsrcc.com/wolfgang/sshd-config.html](http://www.wsrcc.com/wolfgang/sshd-config.html)

---

