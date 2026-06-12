---
title: "How to disable encfs?"
date: 2011-06-19
forum: Security
---

### Post by djtopper on 2011-06-19
Set up a few machines yesterday to test out some parallel code.  Just for fun, I selected the "encrypt users files" option when setting up Ubuntu (10.10).  I had never used the option in years past.

Now I'm finding it a pain.  EG., ssh requires me to already have a login to the machine before it will let me log in w/o a password (eg., using id_rsa.pub and authorized_keys).

Similarly, I have no reason to encrypt files on these machines.  They're just crunching numbers.

Is there an easy way to disable this?  Or do I need to delete my original user and make another one (with all the su privelages, etc...) w/o an encrypted file system / home directory.

Thanks,

D

---

### Post by bodhi.zazen on 2011-06-19
There are steps to remove the encryption here:

[http://ubuntuforums.org/showthread.php?t=1471498](http://ubuntuforums.org/showthread.php?t=1471498)

Up to you to decide what is easier (new user or modify the old).

For ssh, edit /etc/ssh/sshd_config and put the authorized keys outside of home ;)

---

