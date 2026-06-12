---
title: "rsync ssh authorized_keys not working"
date: 2008-11-04
forum: Server Platforms
---

### Post by Emjx on 2008-11-04
I am having difficulty trying to get the private/public keys for password-less login for scheduled backup of a Windows machine to an Ubuntu server.

I created the key pair, copied the id_dsa.pub file to the server into the /home/<user>/.ssh directory and also /.ssh directory.

When trying to login, I am still prompted for a password. The ssh server has been restarted several times and PubkeyAuthentication is set to yes in the sshd_config file (although I note that there is another config file called ssh_config - tried putting the PubkeyAuthentication bit in there as well... didn't work either.

Can anyone suggest any solution?

---

### Post by Archmage on 2008-11-04
Try to put the public keys into .ssh/authorized_keys

---

### Post by Emjx on 2008-11-04
Thanks for the quick reply - unfortunately that didn't make any difference.

---

### Post by Emjx on 2008-11-04
I have had partial success as a result of entering the wrong username - it all works if I use the root username...

---

### Post by conjur3r on 2008-11-04
Try appending the authorized_keys file of the user you wish to login with rather than root.  Eg, if you want to login as FRED, add the public key to /home/FRED/.ssh/authorized_keys

---

### Post by standingfire on 2011-03-01
Check your file and directory permissions. The .ssh directory should be 0700.

---

### Post by garfonzo on 2011-03-01
> **Emjx said:**
> ...it all works if I use the root username...

Which is a bad idea. You shouldn't be logging in remotely (or at all, really) with the root user. If you need root power, you should use "sudo". Avoid using the root user strictly from a security/oops-I-ran-that-command perspective.

---

