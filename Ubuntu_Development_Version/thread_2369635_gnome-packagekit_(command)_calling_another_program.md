---
title: "gnome-packagekit (command) calling another program"
date: 2017-08-25
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-08-25
This program was suggested as proxy for synaptic on wayland. It works real fine but has a bug. When you invoke the command:
```

gpk-update-icon

```
in terminal it will report:

> 
ventrical@ventrical-System-Product-Name:~$ gpk-update-icon
No command 'gpk-update-icon' found, did you mean:
 Command 'pk-update-icon' from package 'pk-update-icon' (universe)
gpk-update-icon: command not found
ventrical@ventrical-System-Product-Name:~$ pk-update-icon
The program 'pk-update-icon' is currently not installed. You can install it by typing:
sudo apt install pk-update-icon


which i believe is a security risk due to a possible typo in the program.

[https://bugs.launchpad.net/ubuntu/+source/gnome-packagekit/+bug/1712914](https://bugs.launchpad.net/ubuntu/+source/gnome-packagekit/+bug/1712914)

[https://help.gnome.org/users/gnome-packagekit/stable/application.html.en](https://help.gnome.org/users/gnome-packagekit/stable/application.html.en)


Regards..

---

### Post by ventrical on 2017-08-25
non_bug
Housekeeping issues.
website not updated.

[https://bugs.launchpad.net/ubuntu/+source/gnome-packagekit/+bug/1712914/comments/4](https://bugs.launchpad.net/ubuntu/+source/gnome-packagekit/+bug/1712914/comments/4)

regards..

---

### Post by ventrical on 2017-08-26
Update:

e-mailed author of program.

---

