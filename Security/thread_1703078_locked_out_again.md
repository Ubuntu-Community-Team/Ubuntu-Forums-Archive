---
title: "locked out again"
date: 2011-03-08
forum: Security
---

### Post by macstl on 2011-03-08
I set up a 10.10 server and a 10.10 laptop to learn nfs. First my password stopped working on the server for admin functions. After working with nfs the next time i logged onto my laptop my keyring pasword does not work . Does this mean Im being hacked. Is there a known problem in this area with 10.10?
Do I have to have this "keyring" thigee when i reinstall laptop cause I can't get in anymore?
Thanks

---

### Post by macstl on 2011-03-08
I reloaded desktop 10.10 and it demands a keyring for my wifi setup. Thats where it did'nt take my password. I set it to boot auto no password and I set screensaver no password with the feet and clicked close cause there is no apply button or ok button. I got pw after screesaver and no feet screen. How do get ss to work?

---

### Post by cariboo on 2011-03-08
Your keyring password should be the same as the one you created when you installed Ubuntu. If you don't want to enter a keyring password every time you boot to the desktop, go to Passwords and Encryptions, and create a blank keyring password, by right clicking on login.

---

### Post by skraps on 2011-03-09
when grub boots, hit "e" over the kernel you would like to boot. 

go down to the line that says "vmlinuz etc etc foo foo"

after "ro" type "single" . Then hit ctrl-x to boot the modifed line. After that you should be confronted with a curses gui and select "drop to root shell"

after that use passwd to change your root password .

---

### Post by cariboo on 2011-03-09
> **skraps said:**
> when grub boots, hit "e" over the kernel you would like to boot. 

go down to the line that says "vmlinuz etc etc foo foo"

after "ro" type "single" . Then hit ctrl-x to boot the modifed line. After that you should be confronted with a curses gui and select "drop to root shell"

after that use passwd to change your root password .

What good is that going to do when it's a problem with gnome-keyring. Setting a user password from the command line doesn't change the keyring password. Logging is as root is a poor solution.

---

### Post by macstl on 2011-03-09
> **cariboo907 said:**
> Your keyring password should be the same as the one you created when you installed Ubuntu. If you don't want to enter a keyring password every time you boot to the desktop, go to Passwords and Encryptions, and create a blank keyring password, by right clicking on login.

I created a blank keyring Ill see how that works out.

---

