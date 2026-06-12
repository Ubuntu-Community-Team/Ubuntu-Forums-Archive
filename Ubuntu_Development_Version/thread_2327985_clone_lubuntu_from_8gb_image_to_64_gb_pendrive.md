---
title: "clone lubuntu from 8gb image to 64 gb pendrive"
date: 2016-06-16
forum: Ubuntu Development Version
---

### Post by Marcin_Stankiewicz on 2016-06-16
I need copy img file (8gb) to pendrive 64 gb, I used ubuntu dd everything it's ok system boot normally, but I got only 2gb free space I need min 20gb, after I copied a image to pendrive I used gparted to extended a partition space to 20gb, but after I run system form pendrive I still got 2gb free space, but gparted show free 20gb, anybody know how to resolve the problem ?

---

### Post by sudodus on 2016-06-16
Welcome to the Ubuntu Forums :-)

Will it make a difference if you shut down the computer, wait a minute and then start the computer again?

Otherwise, to help us understand (in order to help), please post the output of the following commands (in a terminal window), when the pendrive is plugged in:

```
lsusb
df
sudo lsblk -fm
sudo parted -ls  # space minus ell ess
```

[COLOR="#606060"]Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```
[/COLOR]

---

