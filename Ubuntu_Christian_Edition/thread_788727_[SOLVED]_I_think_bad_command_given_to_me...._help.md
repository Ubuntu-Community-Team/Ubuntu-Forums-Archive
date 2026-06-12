---
title: "[SOLVED] I think bad command given to me.... help?"
date: 2008-05-10
forum: Ubuntu Christian Edition
---

### Post by Pursuer on 2008-05-10
I was looking around for a way to get rid of Wine so I could start over, because trying to install ESword, something is obviously not right.

I only found out afterwards that it is probably a bad command. Any thoughts, ideas, etc. If it really bad? If so, what the heck does it mean? Can I reverse it or something if it's bad?

> rm -rf .wine

---

### Post by Whiffle on 2008-05-10
It deletes the folder ".wine" in whatever directory you run it in.  Nothing bad about it, but it is a good idea to understand what a command does before using it.

---

### Post by agim on 2008-05-10
Great avatar. Inigo Montoya.

---

### Post by tamoneya on 2008-05-10
That shouldnt do anything malicious to your computer since things in the .wine folder are not critical to the system.  Also it is not precedeed by a sudo so no system critical files could be deleted anyways since you would lack the proper permissions.  I myself would remove wine like this.```
sudo apt-get remove --purge wine
```

---

