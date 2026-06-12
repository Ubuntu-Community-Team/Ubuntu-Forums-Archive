---
title: "Set the authorizations"
date: 2009-10-17
forum: Security
---

### Post by FelixS on 2009-10-17
I want to change some themes of many applications, copying them in a specific folder. I have to get in the hard drive, then in in the user folder, share folder and the application folder.
Here comes the problem, when I paste the theme folder in there, appears a window saying to me, that I don't have authorization to change something in this folder.

I am the administrator of this computer, where can I change this setup to enjoy the themes? :confused:

---

### Post by cariboo on 2009-10-17
Press Alt-F2 and type:

```
gksu nautilus
```

and enter your password. This will start the file manager in root mode, which will allow you to move the files where you want.

Even if you are the administrator, you need root privileges to manipulate files in directories other than your home directory.

---

### Post by FelixS on 2009-10-18
> **cariboo907 said:**
> Press Alt-F2 and type:

```
gksu nautilus
```and enter your password. This will start the file manager in root mode, which will allow you to move the files where you want.

Even if you are the administrator, you need root privileges to manipulate files in directories other than your home directory.

Thank you so much, now I can change the themes. :mrgreen:

---

