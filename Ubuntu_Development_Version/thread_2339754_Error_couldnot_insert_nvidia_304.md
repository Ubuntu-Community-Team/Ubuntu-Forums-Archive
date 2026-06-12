---
title: "Error: couldnot insert nvidia_304"
date: 2016-10-12
forum: Ubuntu Development Version
---

### Post by cecilpierce on 2016-10-12
Last update gave thiis error, can't login ?
lsmod!grep nvidia says no driver !

---

### Post by Bashing-om on 2016-10-12
cecilpierce; Hello;

How about we polish our crystal balls a bit with :
```

lspci -k | grep -EA2 'VGA|3D'
sudo lshw -C display
dpkg -l | grep -i nvidia
cat /var/log/Xorg.0.log

```

shows the hardware, drivers and what X thinks .

[INDENT][INDENT]see what we have
[INDENT][INDENT][INDENT]and where we go from here
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cecilpierce on 2016-10-12
> **Bashing-om said:**
> cecilpierce; Hello;

How about we polish our crystal balls a bit with :
```

lspci -k | grep -EA2 'VGA|3D'
sudo lshw -C display
dpkg -l | grep -i nvidia
cat /var/log/Xorg.0.log

```

shows the hardware, drivers and what X thinks .

[INDENT][INDENT]see what we have
[INDENT][INDENT][INDENT]and where we go from here
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

Thanks for the help, purged nvidia and using nouveau now, so far so good !

---

