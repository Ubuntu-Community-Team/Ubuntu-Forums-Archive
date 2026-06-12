---
title: "howto sftp with permitted public key only?"
date: 2011-11-21
forum: Security
---

### Post by adhg on 2011-11-21
Hi there,

   I've just established an sftp account (with sudo apt-get install openssh-server). 

I'm able to sftp (via WinSCP and the correct credentials) - problem is that I don't want anyone to access his account without sending me first their PUBLIC KEY (so I can store it and only than allow them access). 

Is there a way to do so? If so, what is the process?) once they send me a public key - where should I store it and ensure that with its absence the login will fail?

Thank you!!!

---

### Post by Dangertux on 2011-11-21
> **adhg said:**
> Hi there,

   I've just established an sftp account (with sudo apt-get install openssh-server). 

I'm able to sftp (via WinSCP and the correct credentials) - problem is that I don't want anyone to access his account without sending me first their PUBLIC KEY (so I can store it and only than allow them access). 

Is there a way to do so? If so, what is the process?) once they send me a public key - where should I store it and ensure that with its absence the login will fail?

Thank you!!!


Have them generate the public key and place it in /home/user/.ssh/authorized_keys

Then once you have everyone's key change this line in your /etc/ssh/sshd_config

```

PasswordAuthentication yes

```to 
```

PasswordAuthentication no

```Restart the server, if their key is not in authorized_keys they will receive the following error when connecting.

(publickey failed)

and the connection will terminate.

---

### Post by adhg on 2011-11-21
Thank you, what if I don't have /home/user/.ssh/authorized_keys file?
(of course I change the user to the real name).

---

### Post by Lars Noodén on 2011-11-21
> **adhg said:**
> Thank you, what if I don't have /home/user/.ssh/authorized_keys file?
(of course I change the user to the real name).

Then you can add one and fill it with the public key.

---

### Post by gsgleason on 2011-11-22
You will want to disable keyboard interactive logins as well as password.

You can use the Match configuration directive, available in openssh server OpenSSH 4.4p1+, in the openSSH server to do this.

[http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config](http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config) - see the Match section

I haven't tried this, but maybe this would work:

#deny all users
Match User *
  KbdInteractiveAuthentication no
  PasswordAuthentication no
  PubkeyAuthentication no

#users we want to have public key auth:
Match User bob,karen,billy,dudeman,ralph
  PubkeyAuthentication yes

That stuff will have to be at the end of the file.

Also, you could change the authorized key files to one global file that only you can manage.

---

