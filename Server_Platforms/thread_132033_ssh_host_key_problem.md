---
title: "ssh host key problem"
date: 2006-02-17
forum: Server Platforms
---

### Post by aceron on 2006-02-17
hey I'm very new at ssh, actually my friend set it up for me.  But yesterday it just stopped working i tried to start it in the terminal and i get this message:

> arron@------------:~$ /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server... Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Disabling protocol version 2. Could not load host key
sshd: no hostkeys available -- exiting.
 I loked through the forums for a bit and i have not seen anything similar.  Does any one know what the error is or how to fix it.  Any help would be greatly appreciated..my friend who set it up for me is in washigton interviewing for MS right now (traitor) so he is of no use at the moment. Thanks Arron

---

### Post by uopjohnson on 2006-02-17
Probably a permission problem try
```
sudo /etc/init.d/ssh start
```
the server key is only accessible by the root user.

---

### Post by aceron on 2006-02-17
Tried using sudo before cammoand and i get...
 * Starting OpenBSD Secure Shell Server....                            [[COLOR="Red"]fail[/COLOR]]

so i assume that it does not change anything.

tried to shell into my ssh and its still down....

---

### Post by uopjohnson on 2006-02-17
You may need to generate new host keys.
First look in /etc/ssh and see if there is a host key
```

ls -l /etc/ssh/ssh_host_rsa_key

```

If that returns something then this is not the problem... if it returns a file not found or similiar then do this
```

sudo /usr/bin/ssh-keygen -t rsa1 -f /etc/ssh/ssh_host_key -N
sudo /usr/bin/ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key -N 
sudo /usr/bin/ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N

```

which will generate new ssh keys.  
then try and restart ssh again and see what you get.

---

### Post by jinacio on 2006-02-17
hmm have you checked if it's already running? :P

sudo /etc/init.d/ssh restart

just a thought...

---

### Post by aceron on 2006-02-18
found out it was a problem wiht my dynamic ip address...my router did not change with it but its fixed now

---

