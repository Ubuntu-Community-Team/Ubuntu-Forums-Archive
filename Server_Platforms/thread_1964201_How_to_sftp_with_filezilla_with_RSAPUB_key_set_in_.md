---
title: "How to sftp with filezilla with RSA/PUB key set in sshd"
date: 2012-04-23
forum: Server Platforms
---

### Post by Mobidoy on 2012-04-23
I have set my server, ssh connection can only be done via pub/rsa key. 

I am trying to set an sftp connection on the server and users will be using filezilla to connect to it. Sadly, I cannot seem to find a way to set it.

I have tried to add the key in filezilla edit -> settings -> sftp but it say the format of the key is not recognized by filezilla and ask to convert it, if I do so, it wont then connect to the server.

Anyone knows of a good tuto to set Ubuntu -> Filezilla -> SFTP -> Ubuntu server with key logging only

---

### Post by Mobidoy on 2012-04-23
Using the right server adress helps

---

### Post by papibe on 2012-04-23
:D

Is it necessary to convert the key then?
Regards.

---

### Post by Mobidoy on 2012-04-23
not at all, in fact, dont even need to go to edit -> settings -> sftp

Thing I did tho was to set : 

SSH_AUTH_SOCK=/home/username/.ssh/id_rsa on my computer.

Will reboot and see if it revert back to what is was and let you know

---

### Post by Mobidoy on 2012-04-23
> **Mobidoy said:**
> not at all, in fact, dont even need to go to edit -> settings -> sftp

Thing I did tho was to set : 

SSH_AUTH_SOCK=/home/username/.ssh/id_rsa on my computer.

Will reboot and see if it revert back to what is was and let you know

dont even need to do this, a printenv SSH_AUTH_SOCK= showed a different path upon reboot and still, Filezilla connected !

---

### Post by papibe on 2012-04-23
Good to know! Thanks for sharing that Mobidoy ):P

Kind Regards.

---

