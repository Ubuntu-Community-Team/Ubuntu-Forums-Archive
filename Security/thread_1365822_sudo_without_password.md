---
title: "sudo without password?"
date: 2009-12-27
forum: Security
---

### Post by linuxonbute on 2009-12-27
I would like to run a python script to directly access the parallel port on my desktop PC.

I have added the portio module and can run the program if I am root.

What I want to do is to be able to upload a file to my website from somewhere else and, on the desktop PC, run a python script which downloads it, examines the content ( which will contain commands for it to carry out )

From this the parallel port bits will be set or cleared which in turn will operate external kit.

The problem is that I cannot do it without sudo which requires my password.

Is it possible for me to do this?

---

### Post by viper250 on 2009-12-27
you would have to change the root password or re install without password but I would not recommend it.
 the su command gives you complete access to the system. and without a password your system is too vulnerable.
the primary reason for the root account is security and the ability to correct user account problems

remove your password at your own risk

---

### Post by linuxonbute on 2009-12-27
> **viper250 said:**
> you would have to change the root password or re install without password but I would not recommend it.
 the su command gives you complete access to the system. and without a password your system is too vulnerable.
the primary reason for the root account is security and the ability to correct user account problems

remove your password at your own risk

Sorry, what I mean is can I run the command without having to enter my password. After all I could upload the file from anywhere in the world.

---

### Post by sisco311 on 2009-12-27
> **linuxonbute said:**
> Sorry, what I mean is can I run the command without having to enter my password. After all I could upload the file from anywhere in the world.

[thread=1132821]HowTO: Sudoers Configuration[/thread]

---

### Post by BkkBonanza on 2009-12-27
As indicated above in sudoers config docs. You can tell sudo to allow execution of a particular program with no password. Just be sure it isn't a problem if some hacker gets in and runs it for you.

---

### Post by linuxonbute on 2009-12-28
> **sisco311 said:**
> [thread=1132821]HowTO: Sudoers Configuration[/thread]

Great, after reading the file, adding myself to the adm and sudo group as well as editing sudoers file it works fine.

Thanks for the pointers.

---

