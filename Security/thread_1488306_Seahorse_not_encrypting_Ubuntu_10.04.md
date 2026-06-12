---
title: "Seahorse not encrypting? Ubuntu 10.04"
date: 2010-05-19
forum: Security
---

### Post by Luisnux on 2010-05-19
Ok, so I've created and encryption key and I'm using ext4 however after creating the key I'm not able to encrypt files as I thought I could.  I'm using seahorse, as listed above.  Please help.

---

### Post by FuturePilot on 2010-05-19
```
sudo apt-get install seahorse-plugins
```
Press Alt+F2 and type

```
nautilus -q
```

Alt+F2 again and type

```
nautilus
```

Now you should be able to encrypt files with the right click menu.

---

### Post by Luisnux on 2010-05-20
You're awesome!  However, just for my understanding what do those commands do?  BTW it did fix my issue.  Thanks

---

### Post by FuturePilot on 2010-05-20
The first one installs the seahorse-plugins package which is contains the Nautilus encryption extension. The second command just quits Nautilus since it needs to be restarted before it will show up. And the third one starts Nautilus.

---

