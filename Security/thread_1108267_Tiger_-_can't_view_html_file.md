---
title: "Tiger - can't view html file"
date: 2009-03-27
forum: Security
---

### Post by Kevbert on 2009-03-27
Hi, I've just installed tiger from the repos and run it once in terminal with 
```
tiger -H
```
If I try to view the output file I do not have the privileges to view it in /var/log/tiger/ and Firefox displays a blank screen. How do I get the privileges ?
Thanks in advance.

---

### Post by snova on 2009-03-27
I think Tiger runs as root, so it will generate files owned by root as well. For security purposes, that file is probably set to be readable only by its owner.

You could copy it to your desktop and change its permissions there:

```
sudo cp /var/log/tiger/**file.html** ~/Desktop
sudo chown $USER:$USER ~/Desktop/**file.html**
```

Or you could run Firefox as root:

```
gksudo firefox /var/log/tiger/**file.html**
```

The argument against the first one would probably be that, since Tiger generates files with sensitive security information in them, you shouldn't copy them, or allow normal users to view them.

---

### Post by Kevbert on 2009-03-28
Thanks for that. Tried the second one with wireless deactivated. Nothing much to worry about.

---

