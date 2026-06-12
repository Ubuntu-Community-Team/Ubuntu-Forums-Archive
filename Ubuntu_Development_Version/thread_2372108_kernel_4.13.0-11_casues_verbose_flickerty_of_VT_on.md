---
title: "kernel 4.13.0-11 casues verbose flickerty of VT on reboot."
date: 2017-09-21
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-09-21
Filed bug report here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1718713](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1718713)

---

### Post by ventrical on 2017-09-21
Confirmed by bot.

---

### Post by ventrical on 2017-09-22
This seems to be a gdm problem.

I did this:

```


   [FONT=Cantarell][SIZE=1]sudo update-alternatives --config gdm3.css[/SIZE][/FONT]

I then pressed 1 and <enter>.

```

and now I have only one verbose flickerty before gdm loads up

---

