---
title: "Can't Find Samba Server"
date: 2011-01-17
forum: Server Platforms
---

### Post by bryanfblareunion on 2011-01-17
I have Ubuntu 10.04 Server running on an old pc in my basement. I installed samba and samba4 on it. I added users, etc. However, i cannot find it in my network locations on my Ubuntu 10.10 laptop. Any help would be greatly appreciated. Any ideas as to what is wrong?

---

### Post by cap10Ibraim on 2011-01-17
this is how i have it running 
if you installed samba server from synaptic package manager 
right click on folder -> sharing options -> share   , this share will be through smb

---

### Post by Morbius1 on 2011-01-17
> I installed samba and samba4 on it.
Uninstall everything labeled > samba4. It's at an alpha state and not meant to be used by anyone other than testers.

Once you've done that:

Restart samba:
```
sudo service smbd restart
sudo service nmbd restart

```
Then run the following command to see if your server can at least see itself:
```
smbtree
```

---

### Post by bryanfblareunion on 2011-01-17
I did all of that and it still doesn't show up. I don't know what else could be wrong.

---

