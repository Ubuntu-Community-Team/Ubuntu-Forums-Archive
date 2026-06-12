---
title: "What is the password for official images?"
date: 2011-09-30
forum: Ubuntu Cloud and Juju
---

### Post by Günter on 2011-09-30
UEC running image centos.5-3.. from official site
GUI in this moment not possible for me, OK
But try to connect to this image a login appears and i Don`t know the
password for root or another user on this image

What is the password for official images?

---

### Post by lisati on 2011-09-30
With Ubuntu, the usual procedure is to create a user with a password when you install it. When you use SSH to login remotely, you'd use the user/password that you created on the remote machine.

The root password is disabled by default in Ubuntu. For more information, see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Günter on 2011-09-30
the procedure I'm tested:
take [euca-centos-5.3-x86_64.tar.gz]("http://eucalyptussoftware.com/downloads/eucalyptus-images/euca-centos-5.3-x86_64.tar.gz") create a image with this running it in Private UEC and test the connect.
At this time only ssh-login to terminal-Session is possible with
    ssh -X -i /home/test/.ssh/id_qwe qwe@192.168.2.119 xeyes
terminal show:

qwe@192.168.2.119's password:

and now?

---

### Post by lisati on 2011-09-30
You do realize that this is an **Ubuntu** forum, not a **centos** forum?

---

