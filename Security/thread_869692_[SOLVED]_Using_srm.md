---
title: "[SOLVED] Using srm"
date: 2008-07-25
forum: Security
---

### Post by Helios1276 on 2008-07-25
Whats wrong with this = helios@helios-laptop:/home$ srm -r-z /helios/example.jpg

(I'm new to the terminal, only teaching myself at this point and wish to learn the correct application of srm, any example for say, deleting a file in a particular folder might help or even/also wiping free space on the HD)

---

### Post by hyper_ch on 2008-07-25
there's no space between  -r and -z

---

### Post by Vivaldi Gloria on 2008-07-25
> **Helios1276 said:**
> Whats wrong with this = helios@helios-laptop:/home$ srm -r-z /helios/example.jpg

You can also join options as follows:

```
srm -rz folder
```

There is no point in using the r option if you are not deleting a folder with subdirectories.

Also it is bad etiquette to mess with the / folder. Don't create folders under it. I suggest you keep your testing to ~/test.

---

