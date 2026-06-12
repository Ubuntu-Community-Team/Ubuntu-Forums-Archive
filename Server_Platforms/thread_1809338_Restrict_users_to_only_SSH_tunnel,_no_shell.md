---
title: "Restrict users to only SSH tunnel, no shell"
date: 2011-07-21
forum: Server Platforms
---

### Post by lemming2011 on 2011-07-21
I have an Ubuntu 11.04 instance running on Amazon EC2. I am currently using it as an SSH tunnel/SOCKS proxy. Most of my Net activity is on a Windows 7 machine running PuTTY. 

This setup is working very well. So well that a few of my friends have expressed interest in accessing it.

Question is, how do I share this proxy, without giving away my private key and root access? I would like to limit users to only being able to set up an SSH tunnel/SOCKS proxy, with no shell access. What other security measures would you recommend for such a setup? I googled a bit and saw references to rbash and chroot.

I have already changed the SSH port, and set the EC2 firewall to allow inbound SSH only from my ISP's address range. My friends use the same ISP. They would probably be running Windows 7/Vista, and PuTTY too. 

Would appreciate your suggestions.

---

### Post by stlsaint on 2011-07-21
A quick google search of "ssh user into chroot" will provide you with a very good amount of help on setting up users in a chroot! From there you can continue to configure the restrictions you want set.

This example is done using arch linux: [http://allanfeid.com/content/creating-chroot-jail-ssh-access](http://allanfeid.com/content/creating-chroot-jail-ssh-access)

---

### Post by lemming2011 on 2011-07-25
Thanks for the pointer. I'll look it up.

---

### Post by CharlesA on 2011-07-25
could always change the shell to something like this:

```
#!/bin/bash
read -p "Hit any key to disconnect"
```

Might not be the absolute best way, but it would work.

---

### Post by pAsM on 2011-07-26
You could change their shell to /bin/noshell

(you may need to install it with "sudo apt-get install noshell")

---

