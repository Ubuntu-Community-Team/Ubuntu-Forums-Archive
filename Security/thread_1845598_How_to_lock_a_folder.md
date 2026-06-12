---
title: "How to lock a folder ?"
date: 2011-09-17
forum: Security
---

### Post by sinaphysics on 2011-09-17
Hi
I use ubuntu 11.04.
I wanna lock a folder, I search lots of softwares but they don't work properly. like cryptkeeper which just work in classic mode. 
Is it possible to suggest me a way to do it ?

---

### Post by haqking on 2011-09-17
> **sinaphysics said:**
> Hi
I use ubuntu 11.04.
I wanna lock a folder, I search lots of softwares but they don't work properly. like cryptkeeper which just work in classic mode. 
Is it possible to suggest me a way to do it ?


lock ? do you mean encrypt ?

sudo apt-get install seahorse-plugins

log out and back in and right click on a folder and choose encrypt ? though you will need to create an encryption key to do this also

is this what you mean ?

---

### Post by sinaphysics on 2011-09-18
thanks. you answer my question. i test it today.:D

---

### Post by haqking on 2011-09-18
> **sinaphysics said:**
> thanks. you answer my question. i test it today.:D


No problem, glad i could help.

remember to use thread tools to mark this thread as solved, cheers.

peace

---

### Post by Linux_user101 on 2011-09-23
If you set proper restrictions on the folder, you can have the same effect as a "locked" folder. Use chmod with arguments -rw and it shouldn't be accessed by anyone but the owner of the file. For example ((sudo chmod -rw foldersname))If you want to encrypt it, I'd follow the poster's comment above.

BTW- ubuntu comes with a default option to encrypt your home directory. Just put the folder in your User directory and then encrypt. Hope this helps

---

### Post by haqking on 2011-09-23
> **Linux_user101 said:**
> If you set proper restrictions on the folder, you can have the same effect as a "locked" folder. Use chmod with arguments -rw and it shouldn't be accessed by anyone but the owner of the file. If you want to encrypt it, I'd follow the poster's comment above.

BTW- ubuntu comes with a default option to encrypt your home directory. Just put the folder in your User directory and then encrypt. Hope this helps

encryption and file/folder permissions are completely different.

It is relatively easy to change ownership/take ownership and get access to files and folders regardless of permissions set.

Encryption is a lot harder to circumvent

---

### Post by Linux_user101 on 2011-09-23
> **haqking said:**
> encryption and file/folder permissions are completely different.

It is relatively easy to change ownership/take ownership and get access to files and folders regardless of permissions set.

Encryption is a lot harder to circumvent

I agree with you. You know what's better than an encrypted folder? An encrypted folder with restrictive permissions. You can do both options for an added ring of security. But such endeavors are unwarranted for the average user. Most can get by with just strong file permissions,  passwords and limited user accounts.

---

