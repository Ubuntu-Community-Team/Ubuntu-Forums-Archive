---
title: "Strange  SSH behavior"
date: 2011-01-23
forum: Ubuntu Cloud and Juju
---

### Post by Japhering on 2011-01-23
I have 6 EC2 slices,  5 Centos and 1 Ubuntu 10.10.  Yes, I'm in process of moving off of Centos to Ubuntu.

When I attempt to ssh -vvv  from my laptop to the Ubuntu slice, it shows a match to my rsa key, then it progresses onward and asks for a password which is turned off.   No matter how I try to connect via ssh (my private key, the creation key, etc) th e connection fails with ssh asking for a password.

The stranger part of the situation is that if I originate the ssh connection from within the Amazon cloud .. ssh works as expected.. accepting all the same keys that are rejected when originating from my laptop.

Any thoughts?

Thanks.

---

### Post by kim0 on 2011-01-23
Make sure you are ssh'ing using the "ubuntu" user, and that you're using the correct keys. Otherwise, anything useful in logs ? (/var/log/auth.log)? Could you post ssh -vvv output as well perhaps. It's usually the simple stuff :)

---

### Post by Japhering on 2011-01-26
Ok.. sorry about the delay .. 

I'm using the same key that works when starting in the Amazon cloud as I am from 
my laptop which doesn't work

/etc/ssh/sshd_config  has  the following:

# Logging
SyslogFacility AUTH
LogLevel DEBUG3

Attached are the ssh -vvv output  as well as the auth.log excerpt.

Thanks.

---

### Post by kim0 on 2011-01-26
It says

debug3: Not a RSA1 key file ~/.ssh/arSshKey.txt.
debug2: key_type_from_name: unknown key type '-----BEGIN'

That key is not a valid ssh rsa key. How did you generate that! The correct way is
ssh-keygen -t rsa
then copy ~/.ssh/id_rsa.pub onto the server's ~/.ssh/authorized_keys

---

### Post by Japhering on 2011-01-26
The interesting thing is the key work works when going to a Centos slice or when coming from  a Centos slice going to the ubuntu slice.

attached is a ssh -vvv  output  originating from my laptop going to my ubuntu slice using the same key.

OK.. So it sounds like my next step should be to regenerate all my keys.. and see if things
improve.

Thanks

---

### Post by Japhering on 2011-01-27
Regenerated with keys  with  ssh-keygen -t rsa   on my ubuntu 10.10  laptop .. the key has the exact same format  as the previous key and generates the same errors in the ssh -vvv output.

So where to now ?

---

### Post by kim0 on 2011-02-02
Hi,

hmm, a successful ssh of mine, outputs the same key format errors, so I guess that's not the core issue. I suppose you should post all details to the #ubuntu-server list

[https://lists.ubuntu.com/mailman/listinfo/Ubuntu-server](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-server)

---

