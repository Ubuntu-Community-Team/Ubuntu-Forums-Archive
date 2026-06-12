---
title: "ssh-copy-id: why am I asked to enter my password after?"
date: 2009-12-07
forum: Security
---

### Post by sa125 on 2009-12-07
Hi - I've copied my public key to a remote server using ssh-copy-id and it worked fine. When I try to connect to that machine with ssh, I am prompted to enter my OWN password before connection is made:

```

sa125@~$ ssh root@192.168.12.12
Enter passphrase for key '/home/sa125/.ssh/id_rsa':

root@/$

```

On a different machine I wasn't required to do that. What's the catch? thanks.

---

### Post by teward on 2009-12-07
did you restart your ssh server?  Any changes usually require a restart to take effect.

---

### Post by okplayer02 on 2009-12-07
well has nothing to do with the server and restarting the service

make sure you copied the key to the correct directory 


for myself i did 

ssh-copy-id -i /home/ubuntu/.ssh/id_rsa.pub okplayer02@host

first u make sure you have generated a key before you attempt to copy the key to the server

---

### Post by Lars Noodén on 2009-12-07
> **sa125 said:**
> Hi - I've copied my public key to a remote server using ssh-copy-id and it worked fine. When I try to connect to that machine with ssh, I am prompted to enter my OWN password before connection is made:

```

sa125@~$ ssh root@192.168.12.12
Enter passphrase for key '/home/sa125/.ssh/id_rsa':

root@/$

```

On a different machine I wasn't required to do that. What's the catch? thanks.

@ TrekCaptainUSA  : no need to restart the ssh unless your changing the ssh *server*'s keys or configuration.  Even then you can do a HUP to have it reload the configuration.  

```

# change configuration
$ vi /etc/ssh/sshd_config

# find process id for sshd
$ pgrep -l sshd
4572 sshd

# reload / respawn, 
# note if there is a mistake in the configuration it will just plain die
$ kill -HUP 4572

```

@ sa125 : did you remember to copy your private key to the other machine that you are trying to log in from?

---

### Post by bodhi.zazen on 2009-12-07
> **sa125 said:**
> Hi - I've copied my public key to a remote server using ssh-copy-id and it worked fine. When I try to connect to that machine with ssh, I am prompted to enter my OWN password before connection is made:

```

sa125@~$ ssh root@192.168.12.12
Enter passphrase for key '/home/sa125/.ssh/id_rsa':

root@/$

```On a different machine I wasn't required to do that. What's the catch? thanks.

That is not your own pasword, that is the password for the id_rsa key.

I am not sure what you are asking exactly so I do not know if it is a problem with the keys in that you did not transfer your id_rsa to the other machine or a problem with your server, ie, did you disable your password logins to the ssh server ?

Please be more specific.

---

### Post by ayenack on 2009-12-09
Sounds to me like you've left password login on in the server.

Check it.

```
 sudo nano /etc/ssh/sshd_config
```

Check that password login is set to no and uncommented.

---

### Post by Jive Turkey on 2009-12-10
It sounds to me like you have two different authorized keys, one for each machine.

The machine where you are prompted for a password has a key with a passphrase.  This is not a bad thing neccessarily but if it bothers you you can delete the key from ~/.ssh and from the server in your authorized_keys file and generate a new key with no passphrase and repeat the steps to add it to the server.

---

### Post by Muttley99 on 2009-12-13
..or you could set up ssh-askpass so you only have to put the passphrase in once at startup!

---

### Post by BkkBonanza on 2009-12-13
As the message indicates it's asking for the password for your key. This is set when you generate the key pair. Often people will generate a key pair with "blank" password so that the key can be used in scripts and automated logins. It may be that on the other machine you mention this was how the key was generated. It is possible to remove the password on the key but of course anyone with access to your account then has access to ther server as well.

Another way would be to use ssh-agent to automate the password after an initial time.

---

