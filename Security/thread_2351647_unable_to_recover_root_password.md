---
title: "unable to recover root password"
date: 2017-02-05
forum: Security
---

### Post by fedora-refugee2 on 2017-02-05
I am trying to recover the root password on two machines. I am using Ubuntu Gnome. I found these instructions:

[http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

but when holding the left shift key, both computers boot to Ubuntu, no grub menu. Any other ideas?

---

### Post by deadflowr on 2017-02-05
Try pressing the Esc key instead.
old bios = Shift
new uefi = Esc

Or so I'm led to believe.

---

### Post by ajgreeny on 2017-02-05
It can often be difficult to get to grub in a UEFI machine, but escape should do it.  Try repeatedly tapping Esc at boot rather than holding it down.

Is this a dual boot system with Windows with secure boot and fast-startup (or whatever it is called) still enabled?
If the machine boots to Ubuntu are you able to login to your username?
Have you actually enabled a root password as your question seems to suggest?

---

### Post by fedora-refugee2 on 2017-02-05
The escape key works, thanks for the help. The initial issue was the "su" command gave me an "authorization failure" error when logging in from the console screen when installing a program. Sudo works though with the same password. Was there a change to su?

---

### Post by deadflowr on 2017-02-05
> **fedora-refugee2 said:**
>  Was there a change to su?

No
Ubuntu never uses a root password, by default.
No root password, no su.

su = needs root password
sudo = needs user's password of a user that belongs to the sudo group, or a group set as an admin group in the sudoers file.
(the sudo group in Ubuntu is sudo, but it's not cardinal, other distributions use other groups, common are admin and wheel)

---

