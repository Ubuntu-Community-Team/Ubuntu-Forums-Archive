---
title: "bin exicution"
date: 2008-12-14
forum: Server Platforms
---

### Post by Frugoo Scape on 2008-12-14
I'm getting this random issue: (ubuntu 8.4 server)
```

root@frugooscape:/home/##USERNAME##/srcds_l# chmod 777 *
root@frugooscape:/home/##USERNAME##/srcds_l# ls
hldsupdatetool.bin
root@frugooscape:/home/##USERNAME##/srcds_l# ./*
bash: ./hldsupdatetool.bin: No such file or directory
root@frugooscape:/home/##USERNAME##/srcds_l#

```

Is there a reason why it's not locating it? It has all the permissions.

Works fine on my virtual machine though that I'm running off my home pc.

I want to avoid restarting it.

---

### Post by spiderbatdad on 2008-12-14
you might try specifying the full path. Why are you root? Ubuntu uses an administrator/user with sudo privileges.
In which case you could set a path in your .bashrc like:
```
export PATH=$PATH:$HOME/##USERNAME##/srcds_l
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$Home/##USERNAME##/srcds_l 
```

---

### Post by Frugoo Scape on 2008-12-14
> **spiderbatdad said:**
> you might try specifying the full path. Why are you root? Ubuntu uses an administrator/user with sudo privileges.
In which case you could set a path in your .bashrc like:
```
export PATH=$PATH:$HOME/##USERNAME##/srcds_l
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$Home/##USERNAME##/srcds_l 
```
I did sudo. =\

---

### Post by Frugoo Scape on 2008-12-14
Still having the same problem and i did what you told me. It has the correct permissions and i have tried it on multiple account's including root.
It works on the other computer, that's what driving me crazy.

code i was trying to do:

```
mkdir srcds_l
cd srcds_l
wget http://www.steampowered.com/download/hldsupdatetool.bin
chmod +x hldsupdatetool.bin
./hldsupdatetool.bin
```
Downloads fine, changes it to executable, but i get this:
```
bash: ./hldsupdatetool.bin: No such file or directory
```

Any other thoughts, other then what was already offered?


Edit:
I was running x64 all i had to do was install the 32bit lib.
apt-get install lib32gcc1

---

