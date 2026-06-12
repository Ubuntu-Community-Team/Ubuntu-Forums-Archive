---
title: "FileZilla Server access and root issues"
date: 2009-05-06
forum: Security
---

### Post by n0manarmy on 2009-05-06
I've got FileZilla installed on my windows machine that I'm using to migrate files from two different networks with, both machines being Ubuntu servers. One of the problems I'm running in to and has snagged me up in the past is that the files going in to place on the new server require root permissions, such as copying files in to the /etc directory.

I could easily copy the file on the box by typing 
"sudo cp file /etc/otrs/file" but how would I do this with FileZilla

I can't seem to find where to enable root level access for transfering of files. I don't want to enable the root account on the servers as it seems that Ubuntu is really trying to move away from this.

---

### Post by cdenley on 2009-05-06
You can use key authentication to connect to ubuntu as root without setting a root password.
[https://help.ubuntu.com/community/AdvancedOpenSSH#RSA%20Key-Based%20SSH%20Logins](https://help.ubuntu.com/community/AdvancedOpenSSH#RSA%20Key-Based%20SSH%20Logins)
[http://wiki.filezilla-project.org/Howto](http://wiki.filezilla-project.org/Howto)

---

### Post by n0manarmy on 2009-05-06
> **cdenley said:**
> You can use key authentication to connect to ubuntu as root without setting a root password.
[https://help.ubuntu.com/community/AdvancedOpenSSH#RSA%20Key-Based%20SSH%20Logins](https://help.ubuntu.com/community/AdvancedOpenSSH#RSA%20Key-Based%20SSH%20Logins)
[http://wiki.filezilla-project.org/Howto](http://wiki.filezilla-project.org/Howto)

This isn't playing well with the root account. It, for some reason, is asking me for my root account's password which isn't assigned. I'm reading through the information now but not finding anything about the root account password issue. It's worked on other accounts that I have on the box.

---

### Post by cdenley on 2009-05-06
> **n0manarmy said:**
> This isn't playing well with the root account. It, for some reason, is asking me for my root account's password which isn't assigned. I'm reading through the information now but not finding anything about the root account password issue. It's worked on other accounts that I have on the box.

Is root login allowed on your ssh server?
```

grep PermitRootLogin /etc/ssh/sshd_config

```

---

### Post by n0manarmy on 2009-05-06
> **cdenley said:**
> Is root login allowed on your ssh server?
```

grep PermitRootLogin /etc/ssh/sshd_config

```

It was set to "Yes" I changed it to

PermitRootLogin without-password

when I do 

sudo ssh-copy-id -i ~/.ssh/id_rsa.pub root@(servername) it prompts me immediately with 
root@(servername)'s password:

---

### Post by cdenley on 2009-05-06
> **n0manarmy said:**
> It was set to "Yes" I changed it to

PermitRootLogin without-password

when I do 

sudo ssh-copy-id -i ~/.ssh/id_rsa.pub root@(servername) it prompts me immediately with 
root@(servername)'s password:

You can't connect to the server with a key to install a key if you haven't installed the key yet. You will have to login as an admin user and install the key manually.

```
scp ~/.ssh/id_rsa.pub (servername):./
ssh (servername)
sudo -i
cat id_rsa.pub>>/root/.ssh/authorized_keys
exit
exit
```

---

