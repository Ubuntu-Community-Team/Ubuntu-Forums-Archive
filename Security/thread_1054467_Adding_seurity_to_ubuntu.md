---
title: "Adding seurity to ubuntu"
date: 2009-01-29
forum: Security
---

### Post by Walkaa on 2009-01-29
Im running Ubuntu 8.04 with Gnome, im new to linux and learning fast and loving it plus its freedom. im the only user on my netbook and as expected the system goes straight into ubuntu on startup. Is there any way of adding a log in screen to the startup just to improve security?

Thanks Walkaa

---

### Post by shqip on 2009-01-29
> **Walkaa said:**
> Im running Ubuntu 8.04 with Gnome, im new to linux and learning fast and loving it plus its freedom. im the only user on my netbook and as expected the system goes straight into ubuntu on startup. Is there any way of adding a log in screen to the startup just to improve security?
 
Thanks Walkaa
 
 
 
It seem like you have enabled automated log in. You need to disable that so that you get a use name and password prompt when you start your OS. That can be found on user groups. Just remove the tick.

---

### Post by Walkaa on 2009-01-29
Wow that was so plainly obvious, cheers can't believe I missed that one!!!

Walkaa

---

### Post by Tubes6al4v on 2009-01-30
Just a note: if you want security from people not being able to look at your drive (i.e. if they used a live cd to mount the drive), then look into installing the OS as encrypted: [https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid](https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid)

---

### Post by Rhubarb on 2009-01-30
> **shqip said:**
> It seem like you have enabled automated log in. You need to disable that so that you get a use name and password prompt when you start your OS. That can be found on user groups. Just remove the tick.
I'm quite sure the above isn't quite right.

But anyhow, if you haven't got this working yet, you can get it working thus:

System --> Administration --> Login Window
"Security" tab, then uncheck the "Enable Automatic Login" and "Enable Timed Login" checkboxes.

---

### Post by hyper_ch on 2009-01-30
well, unticking the login box will not help you against anyone who can lay hands on your computer. The data is not encrypted and is plainly available.

---

