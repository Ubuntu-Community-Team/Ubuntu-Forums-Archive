---
title: "Why is 755 default for the users home directory?"
date: 2010-09-12
forum: The Cafe
---

### Post by nerdopolis on 2010-09-12
I did not know where else to put this, I was just wondering:

Why does Ubuntu by default have permissions set that allow other users to read the contents of your home directory? are there some system services that run as a non root service user that needs to see some of the users files? all I can think of is the .face.icon file, but kdm/gdm runs as root...  

Right now I can enter my 'all default' test user account's home directory and see its folders, and open its .bashrc.

---

### Post by DjSesso on 2010-09-12
take read permissions from the user group. Wait arent you in your own users group?

---

### Post by nerdopolis on 2010-09-12
Sorry. I should have said that I was thinking about the 'other' group. Why is there a 5 in the other group where I would expect there to be a 0?

---

### Post by DjSesso on 2010-09-12
I honestly dont know why it is. It probably would be safer on a multiple user system. Set it to 750 and see if you can still see it.

---

### Post by cariboo on 2010-09-12
It's to make it easier for new users to share files, experienced users are expected to know how to change the directory permissions to 700, if they want more security.

---

### Post by saulgoode on 2010-09-12
On multi-user Unix systems, it was quite common for sysadmins to permit users to read each others' files by setting the umask to 022. The reasoning was that users (being the lazy dogs they are) who needed to share files might find it easier to share passwords (not a good thing) than to properly administer their file permissions.

---

### Post by nerdopolis on 2010-09-12
Ah! So its for sharing of files between user accounts!

Thanks for the explanation!

---

### Post by Dark Aspect on 2010-09-12
> **cariboo907 said:**
> It's to make it easier for new users to share files, experienced users are expected to know how to change the directory permissions to 700, if they want more security.

Just out of curiosity what is the easiest way to change the home folder permissions to 700?

---

### Post by FuturePilot on 2010-09-12
> **Dark Aspect said:**
> Just out of curiosity what is the easiest way to change the home folder permissions to 700?

```
chmod 700 $HOME
```

---

