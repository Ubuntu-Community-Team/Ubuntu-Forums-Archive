---
title: "sshfs"
date: 2009-10-27
forum: Security
---

### Post by u_kapaley256 on 2009-10-27
Hi all,
I am trying to mount my roomie's home through sshfs
But i can do it only through root 
I dont have previliges as a user 
pls help
Thanks 

PS :
I followed these steps :-
1)Install sshfs
2)make directory /media/user
3)chown on the directory
4)adduser udayan fuse
5)sshfs user@192.168.1.67:/home/user /media/user

and then :-

*chmod 777 /media/user
*chgrp fuse /media/user

---

### Post by u_kapaley256 on 2009-10-27
Hi ,
Actually it was the error in ssh
i cleared the ~/.ssh/known_hosts file and i was done
Sorry for being so impatient 
And thanks anyways

---

