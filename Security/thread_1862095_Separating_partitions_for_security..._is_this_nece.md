---
title: "Separating partitions for security... is this necessary with apparmor?"
date: 2011-10-16
forum: Security
---

### Post by desire.linux on 2011-10-16
I've read a lot about hardening, and one way of hardening your system is to separate your partitions with different fstab options, especially to prevent an attacker from creating and executing scripts in the all writable /tmp or /dev/shm.

But is this really necessary if all your critical network applications are confined with apparmor? Like Firefox, Apache and Mysql?

And even though an attacker writes a script in /tmp, that script will get denied access if he tries to modify something that is owned by root, as an unprivileged user, right?

Any opinions?

---

### Post by 2F4U on 2011-10-16
That depends on how serious you are/have to be about security. In a highly secure environment you need to implement several layers of security measurements and separating partitions would be one of them. This is because software is prone to errors/failure and if one layer fails, it is good to have others that may prevent the worst.

---

### Post by Lars Noodén on 2011-10-16
The minimum would be to have a separate /home.  That would be a good idea for other reasons, too.  It makes it easier to do a fresh install or complete system upgrade.

The general idea in having multiple partitions is to keep the executables separate from the data.  If it's writeable, it should not be executable and vice versa.  It's more difficult to guess the right size of the partitions.  You can DOS yourself if /var/log or /tmp end up too small, but it's a waste of space if they are too big.

---

### Post by Dangertux on 2011-10-16
In my opinion because of the path based confinement of apparmor separating partitions and using apparmor would compliment eachother rather than being a duplication of effort. 

Plus as it's been said before in this thread separate partitions have added benefits besides just security in terms of an attacker. They increase the likelihood your data would survive a catastrophic system failure.

---

### Post by HermanAB on 2011-10-16
Hmm, I don't think that multiple partitions add anything in terms of security, since the file tree is still according to the LSB and therefore known.

The most important thing you can do to harden your system is to adjust PAM, to enforce long passwords, since most machines get hacked after someone set a 4 character password when you have a service such as VNC, FTP or SSH running.  

Pretty much every tale of hacking woe on these forums is due to VNC and short passwords.

---

