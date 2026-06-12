---
title: "oops, chmod and chown BIG errors. no sudo?!"
date: 2008-09-22
forum: Server Platforms
---

### Post by FarmCretin on 2008-09-22
i think i made a BIG booboo, i was messing with chown and chmod and now when i try to sude i get this error "sudo: must be setuid root". all i wanted was to be able to create a guest account that couldn't change directories or see the directory tree.

---

### Post by Iowan on 2008-09-22
What did you **chown** and/or **chmod**?

---

### Post by FarmCretin on 2008-09-22
i was trying to reset my permissions from scratch. i figured first make everything only root, then my user, then a few select for my lower users. i got as far as chown -R root /  and then it all just went to crap.

---

### Post by MJN on 2008-09-23
Please try and use the search function as this is quite a common question.
 
As you're only 6 posts in I'll help by giving a direct result:
 
[http://ubuntuforums.org/showthread.php?t=219767](http://ubuntuforums.org/showthread.php?t=219767)
 
You may find you'll have other problems now that everything is root-owned. If you're not too far in I'd recommend starting a fresh install. Don't be too disheartened by this though - you learn more by your mistakes!
 
Incidentally, you don't have to edit (or post) to subscribe to a thread - you can just click Subscribe under 'Thread Tools' (or you can set this to be the default for all your posts within the Control Panel).
 
Mathew

---

### Post by pdwerryhouse on 2008-09-23
Before doing a complete reinstall, it might be worth trying booting into single user mode and then trying this:

```
apt-get --reinstall install $(dpkg --get-selections | awk '{print $1}')
```

Make sure your network is up, however.

---

