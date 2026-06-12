---
title: "ssh rsa setup gone wrong"
date: 2011-07-31
forum: Security
---

### Post by Encaitar on 2011-07-31
New to Ubuntu,
If this is in the wrong place please move or let me know. 

Using Ubuntu 10.4, local machine, followed ubuntu ssh setup ([https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)).

ran:
mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa

Changed /etc/ssh/sshd_config:
PasswordAuthentication no
AuthorizedKeysFile ~/.ssh/authorized_keys

Try to run ssh username@localhost on the same Ubuntu box and get "Permission denied (publickey)"

Not sure how I have managed to mess up the process.
I have tried the troubleshooting solution of:
chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

 but still the same error.

What is the best way of resetting the ssh and public/private key settings so that I know I am starting from a fresh system again? I have a backup copy of the sshd_config file and so can put that back but I dont know if I would have to reset anything else before starting at the beginning and trying again.

---

### Post by CharlesA on 2011-07-31
Did you add the public key to authorized_keys ?

cat ~/.ssh/id_rsa >> ~/.ssh/authoried_keys

---

### Post by Encaitar on 2011-07-31
Thanks for the quick replay. There was not a file called authorized keys (only known_hosts) so I created the file and pasted in the single line public key.

---

### Post by CharlesA on 2011-07-31
Should work now.

---

### Post by Encaitar on 2011-07-31
So I don't know what is worng with it. I've tried a number of things I have found on some websites now so I'm no sure if I've messed anything up. 

I was thinking it might be a god idea to flush the ssh and rsa things and try to start again. Does anyone know about, or where to find out about, the contents of the /etc/ssh/ folder, I have a ssh_host_rsa_key and ssh_host_rsa_key.pub which are pointed to by the HostKey param in /etc/ssh/sshd_config but I don't know what that is doing.

---

### Post by CharlesA on 2011-07-31
purge it and retry.

```
sudo apt-get purge ssh
```

---

### Post by cariboo on 2011-08-01
CharlesA, Ubuntu uses openssh-client and openssh-server by default, instead of ssh, so the op would have to purge those packages and then re-install them in order to start all over again.

---

### Post by CharlesA on 2011-08-01
> **cariboo907 said:**
> CharlesA, Ubuntu uses openssh-client and openssh-server by default, instead of ssh, so the op would have to purge those packages and then re-install them in order to start all over again.

Ah thanks. Guess they changed that on me. :)

---

