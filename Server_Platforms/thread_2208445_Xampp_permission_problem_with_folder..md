---
title: "Xampp permission problem with folder."
date: 2014-02-28
forum: Server Platforms
---

### Post by TheUninvited on 2014-02-28
So in my xampp i tried to put an image on a **htdocs/images** and i wasn't able to do.

When i go to properties it shows me that i am not the owner and i can't change the permission and the owner is **root.**

My account i am using is on administrator group then why i can't change the permissions on it?

---

### Post by cariboo on 2014-02-28
Seeing as there is no indication that this is a Trusty issue, moved to Server Platforms.

---

### Post by nerdtron on 2014-03-01
Post the output of
```
id
```
and 
```
ls -l /path/xampp/htdocs/images
```

---

### Post by TheUninvited on 2014-03-02
is this enough?

[http://imgur.com/xgCLsMb](http://imgur.com/xgCLsMb)

---

### Post by nerdtron on 2014-03-02
I have noticed that the folders have no write permissions for the group, even if you are member or the root group, you won't be able to add or delete files in the images directory and its subdirectories.
You need to add write permissions for the groups, also include the parent folder (the images folder itself).
I guess even the upper folders are like this so you need
```
sudo chmod -R g+w /opt/lampp/htdocs/forum
```
After you have issued that command, you use "ls -l" again and you'll see the folders to have drwxrwxr-x attribute.

---

### Post by TheUninvited on 2014-03-03
> Operation not permitted 

This is what it says. and when i go to user accounts my account is an administrator.

---

### Post by nerdtron on 2014-03-03
I edited my post, try it again with sudo and see if it will accept.
It will ask for your password. Type your password (no characters will be shown when you type your password.

---

### Post by TheUninvited on 2014-03-04
> **nerdtron said:**
> I edited my post, try it again with sudo and see if it will accept.
It will ask for your password. Type your password (no characters will be shown when you type your password.
Thanks m8te, it really worked.I really appreciate it , you know is kind of hard for a web designer to do not be able to move/put pictures on that directory and again thank you so much!!!

You are the best:D and you better know it haha!

---

