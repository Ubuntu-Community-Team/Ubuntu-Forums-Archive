---
title: "Samba share permission issues with Windows."
date: 2010-08-04
forum: Server Platforms
---

### Post by jesuscamp on 2010-08-04
I created a share with Samba and can access is with my Linux users from windows easily, but I want to be able to drag and drop files into from Windows but I always get access denied, anyone know how I can drop files into my shares from windows and not having to be on the server?

---

### Post by Morbius1 on 2010-08-04
All we need to know now is what method of samba you are using ( there are two ). This will tell us that information:
```
net usershare info
``````
testparm -s
```And we also need to know the linux permissions of the folder you're sharing:
```
ls -dl /folder-name
```

---

