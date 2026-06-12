---
title: "How to put samba in your environment Path"
date: 2013-09-01
forum: Tutorials
---

### Post by Toxic64 on 2013-09-01
If you installed samba from git, by default it goes in /usr/local/samba/.../...

Here is a way to configure is so you can use samba commands from anywhere..

Just edit your **/etc/environment** file :

```
sudo nano /etc/environement
```

now add **:/usr/local/samba/bin:/usr/local/samba/sbin** before the ending quote

Save and close.

Now you can use your samba commands from anywhere at the prompt without having to type /usr/local/samba/.../.../

---

### Post by TheFu on 2013-09-01
Or ... change just YOUR settings and not those for the entire installation by modifying your ~/.bashrc file. Add a line like this:
```
export PATH=$PATH:$HOME/bin:/usr/local/bin:/usr/local/sbin
```

Notice how I added a personal "$HOME/bin" to my path?  That is handy for any power-user to have their scripts available.

The enterprising scripter might want to check if /usr/local was already inside the path before adding. That line above doesn't prevent multiple additions.  PATHs can get overly long with duplicates if we aren't careful.

---

### Post by JnPson on 2013-09-01
What are the benefit and downsides between these two?

---

### Post by TheFu on 2013-09-01
Post #2 has the benefits and downsides ... or did I miss something?

---

### Post by Toxic64 on 2013-09-02
Yep that's true. 

BUT...

If Samba 4 is installed as an AD server, having only the administrator loging, it doesn't change much.
 You don't create multiple profiles with the ability to login and play with your LDAP server on an enterprise infrastructure.
anyway, I wouldn't.

---

