---
title: "Webmin Login Failed. Please Try Again."
date: 2009-10-20
forum: Server Platforms
---

### Post by ericwj08 on 2009-10-20
I get Webmin Login Failed. Please Try Again. when i try to login. Webmin worked perfectly fine for me up until I first changed the memory limit for php, then I changed the file permisions to 777 for the /etc directory, all files, and subdirectories. I think the last part was probably my mistake. Does anyone know what damage I did, and how I may be able to fix it?

---

### Post by ericwj08 on 2009-10-20
Anyone? I have no idea how to fix this. Anyone any ideas please???

---

### Post by cariboo on 2009-10-20
Most files and directories in /etc have a permissioin of 644, sudoers has a permission of 440. You can try fixing the permissions, I don't garauntee this will work, but give it a try.

```
sudo chmod -R 644 /etcv
```

and

```
sudo chmod 440 sudoers
```

---

