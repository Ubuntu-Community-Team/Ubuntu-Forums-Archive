---
title: "SFTP User Directory Lock"
date: 2010-08-31
forum: Server Platforms
---

### Post by cpressland on 2010-08-31
Hey guys,

I'm setting up an SFTP Server and I need help with a few things

Say like I make the user: 'smile123' and give it the home directory '/home/smile123' then create two directories inside 'Upload' and 'Download'. Now, I want the user to be able only download from the 'Download' folder and only upload to the 'Upload' folder; not see it's content.

But more importantly I don't want smile123 to be able to see '/' or '/home' or any other folder outside of '/home/smile123'

Thanks Guys

Chris

---

### Post by cpressland on 2010-09-01
Bump, anyone?

---

### Post by scorp123 on 2010-09-01
Why not run a virtual machine? That way it doesn't matter if that user can see /, /etc and other critical areas or not ... it's a VM and you can reset it back to a previously saved snapshot if you want or need to.

---

### Post by surfer on 2010-09-01
did you look at vsftp? not sure if it can meet all your requirements. but still...

---

### Post by scorp123 on 2010-09-01
> **surfer said:**
> did you look at vsftp? "vsftp" is a standard FTP daemon ... it can't do SFTP which is a sub-protocol of SSH.

---

### Post by cpressland on 2010-09-01
Because the server is ALREADY a virtual machine and well, my boss wants it setup like that. I know it can be done, i've done it before, I just cannot for the life of me remember how.

---

### Post by scorp123 on 2010-09-01
> **cpressland said:**
> Because the server is ALREADY a virtual machine  Excellent. :D

As for blocking users out of some directories ... why not use ACL's? You could put those remote users into a ACL group e.g. "guests" and then use the **setfacl** command to deny "guests" access to certain locations ... This of course requires that your filesystem supports ACL's. If you used Ext3 or Ext4 it's just a matter of mounting the file system with the right options inside **/etc/fstab**. Google will tell you the rest.

**BUT: don't overdo it.** Even "guest" accounts need access to certain files inside / and /etc or they will not even be able to authenticate, e.g. you can't block **/etc/passwd** or they won't even be able to login.

I wouldn't even put those "guest" accounts on the **/home** filesystem but rather give them their own mountpoint on their own partition, e.g. **/guests/username1**, **/guests/username2** and so on. That way you could deny them access to **/home** without affecting their ability to login.

Threads you might be interested in:
[http://ubuntuforums.org/showpost.php?p=4537745&postcount=17](http://ubuntuforums.org/showpost.php?p=4537745&postcount=17)
[http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists](http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists)

---

### Post by surfer on 2010-09-01
> **scorp123 said:**
> "vsftp" is a standard FTP daemon ... it can't do SFTP which is a sub-protocol of SSH.

you're right... sorry! i just got carried away with it because it can restrict users to their home directory, which is close to what is being looked for here.

---

### Post by sh1ny on 2010-09-01
> **surfer said:**
> you're right... sorry! i just got carried away with it because it can restrict users to their home directory, which is close to what is being looked for here.

Besides acl's , you need the user to not be able to leave his homedir, right ?

[http://olivier.sessink.nl/jailkit/howtos_sftp_scp_only.html](http://olivier.sessink.nl/jailkit/howtos_sftp_scp_only.html)

Jailkit can jail users in their home dirs for ssh/sftp sessions. The commercial ssh server supports this, but openssh does not, so jailkit is the only alternative that works ( which i have found so far ).

---

### Post by scorp123 on 2010-09-01
> **sh1ny said:**
>  Jailkit can jail users in their home dirs for ssh/sftp sessions. Nice. Thanks for the link :)

---

