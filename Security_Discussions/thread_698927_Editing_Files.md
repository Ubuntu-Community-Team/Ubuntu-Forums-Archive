---
title: "Editing Files"
date: 2008-02-16
forum: Security Discussions
---

### Post by bzachd on 2008-02-16
Hi,

Brand New to Ubuntu, I like the OS so far, fairly new to Linux as well, just working through the learning curve. My question is, I am trying to install Oracle 11G, and am required to edit a file owned by root. Signed in under my normal user account, is there any way to switch to root while in the GUI, in order to open the file and edit it? I can switch to sudo in the terminal, but I would like to edit it in the GUI. Any ideas?

Thanks,
Zach

---

### Post by Dr Small on 2008-02-16
Try:
```
gksudo gedit
```

Also, some good documetation is on the wiki:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Good luck!
Dr Small

---

### Post by bzachd on 2008-02-16
Dr. Small...

Hey man thanks, that did the trick !

Z.

---

