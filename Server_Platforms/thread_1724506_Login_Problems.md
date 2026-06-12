---
title: "Login Problems"
date: 2011-04-08
forum: Server Platforms
---

### Post by DrHackable on 2011-04-08
Err, Is there any possible way to change the username and password on Ubuntu Server?
Without Logging in because I forgot the password :oops:

Can someone help?

---

### Post by dtfinch on 2011-04-08
You could try booting in single user mode.

I haven't done it much, but this seems to work on my 10.04 virtualbox install, based on the replies in [http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub):
Hold down shift during boot to bring up the grub menu.
Press "e" to edit the boot options.
Edit the kernel line (the line beginning with "linux /boot/vmlinuz...") so that it ends with "rw single init=/bin/bash" (rather than "ro quiet splash" or whatever the current default is)
Press ctrl-x to boot with those options.
If that gets you to a bash prompt, you can use passwd to change your password. By default it'll change the password of the current user (root) unless you give it a username.

---

### Post by DrHackable on 2011-04-09
Okay, I will try this!

---

### Post by BkkBonanza on 2011-04-09
The std Ubuntu install usually adds recovery menu items to the boot menu anyway. So if you hold shift while booting you should see the grub menu with options for recovery console. You can select that and use passwd to alter your password. This works as long as your home is not encrypted - in which case you need to take the extra step to re-wrap the passphrase too.

---

### Post by DrHackable on 2011-04-10
Lul wut? I don't have a GRUB Menu? I was holding shift and it boots normaly. I have backed up all the files on the Samba Server so I will re-install it

---

