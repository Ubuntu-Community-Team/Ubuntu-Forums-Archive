---
title: "Delete login password"
date: 2006-05-18
forum: Server Platforms
---

### Post by maxM on 2006-05-18
Hi, I installed Dapper on my computer today, but when I was login in I got the message "Password or username was inncorect". 
Now I'v been trying every sorts of my Username and password, but I must have been typing realy wrong under the install. 

So my question is: Are there any ways to delete the password or set a new one without login in, and without typing the old one?
Or is the only selution to install once more?

---

### Post by ajgreeny on 2006-05-18
Did you by chance change your keyboard country layout after a first login or have you never got ubuntu up and running?
Sounds as if you may need to boot into recovery mode and go to the users group and reset your user name and password. Or simply reinstall and make certain you note your user name and password, and the upper or lower case you use, before a bootup into the desktop.
Good luck.

---

### Post by tkjacobsen on 2006-05-18
boot into recovery mode (an option in grub).
then```
passwd USERNAME
```
where USERNAME simply is your username

---

### Post by carterdea on 2006-05-26
I did this too. Except I can't remember what I put for username (well it was about 4 am and I was laying in bed with my eyes 1/2 closed) can I change the username?

---

### Post by tkjacobsen on 2006-05-26
you can see which user are in /home:   /home/USERNAME

or create a new user:```
adduser USERNAME
```

---

