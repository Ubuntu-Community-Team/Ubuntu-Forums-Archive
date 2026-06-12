---
title: "Amazon EC2 - Free NX (auth problem)"
date: 2010-03-22
forum: Server Platforms
---

### Post by p3dro.sola on 2010-03-22
Hi. I've set up a EC2 using a standard Ubuntu 9.10 AMI.

I followed _[this]("https://help.ubuntu.com/community/FreeNX#Installing%20the%20FreeNX%20server%20on%20Ubuntu%20Karmic%20%289.10%29")_ tutorial, and got FreeNX set up correctly. The default config for FreeNX is to use keys and not passwords for authentication. After setting up FreeNX it prints a message saying that it's now configured so that the user's can user their normal login information to access the server through NX. 
The problem is that the AMI is configured so that the _[ubuntu user desn't have a password]("http://alestic.com/2009/04/ubuntu-ec2-sudo-ssh-rsync")_. But the FreeNX client requires one, as well as a key.

Also, am i supposed to login as ubuntu? make a new user?

Comments are appreciated. Cheers!

---

### Post by p3dro.sola on 2010-03-22
Never mind. I figured it out.

The problem is that you gotta enable Password based ssh authentication in /etc/ssh/sshd_config

(after creating a new user.)

---

### Post by Ezrie on 2010-12-12
> **p3dro.sola said:**
> Never mind. I figured it out.

. . . you gotta enable Password based ssh authentication in /etc/ssh/sshd_config.

(after creating a new user.)

How do you do this?

---

