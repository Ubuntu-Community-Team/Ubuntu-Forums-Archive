---
title: "ath64bit server login"
date: 2008-11-23
forum: Server Platforms
---

### Post by ke7icz on 2008-11-23
i installed ubunto ath64 server on a athlon 64bit dual processer
server for some reason i cant log on at at all can anyone tell me what i am doing wrong when i formatted i used the guided use all of drive option 
thanks in advance

---

### Post by Philio on 2008-11-23
Are you trying to login directly on the box or via SSH?

If you cannot access the box, you will need to login using the username and password you specified during the installation process. If you can't remember the login then there are a few ways you could recover it:

Boot into single user mode and use the passwd command to reset the password.
Boot a rescue/boot/live disk and mount/chroot into your installed system and use passwd to reset the password.

You should ideally reset the password for your created user, not root as your default user account will be able to perform admin tasks using sudo.

If you can access the box directly but cannot access SSH you'll probably need to install the SSH server package via the following:

sudo apt-get install openssh-server

---

