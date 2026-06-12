---
title: "insmod: ERROR: could not insert module ./drivers/hid/hid-redragon.ko: Invalid paramet"
date: 2023-08-23
forum: Ubuntu/Debian BASED
---

### Post by ricciolino on 2023-08-23
[FONT=arial black]**[SOLVED]**[/FONT]

[IMG]https://i.stack.imgur.com/HZ4ka.png[/IMG]

I am trying to insert **hid-redragon.ko** module in my current kernel.

 ```
# uname -r
5.19.0-41-generic
```
```

# apt source linux-image-unsigned-$(uname -r)

``` This download linux-hwe-5.19-5.19.0 (that is not the same exact version of my running kernel, I don't know why this happen...).

 ```
# cd linux-hwe-5.19-5.19.0

# chmod a+x debian/scripts/*

# chmod a+x -R ./scripts

# cp /boot/config-$(uname -r) ./.config

# make oldconfig

# make -j 24

# sudo find . | grep -i "redragon\.ko"

# insmod ./drivers/hid/hid-redragon.ko 
insmod: ERROR: could not insert module ./drivers/hid/hid-redragon.ko: Invalid parameters

``` How can I solve this ?

---

### Post by ricciolino on 2023-08-27
Without needed to recompile the whole kernel, I actually solved by running these two commands:

```
sudo apt install --reinstall linux-modules-extra-6.2.0-26-generic
sudo apt install --reinstall linux-modules-extra-5.19.0-41-generic
```

Now *.ko modules came back to original locations:

```

/usr/lib/modules/6.2.0-26-generic/kernel/drivers/hid/hid-redragon.ko
/usr/lib/modules/5.19.0-41-generic/kernel/drivers/hid/hid-redragon.ko
```

---

