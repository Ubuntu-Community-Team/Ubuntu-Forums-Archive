---
title: "how do i remove apache server from startup"
date: 2012-11-17
forum: Server Platforms
---

### Post by mastablasta on 2012-11-17
how do i remove apache server form startupo (i.e. i don't want it to automaticly start on boot).

i tried this
```
sudo update-rc.d apache remove
```

and this
```
sudo update-rc.d apache2 remove
```

it doesn't seem to work as i keep getting "it works" page on localhost and also the joomla page (well if i start only mysql service).

i installed LAMP via tasksel.

---

### Post by littlegreiger on 2012-11-17
Try ```
sudo update-rc.d -f apache2 remove
```

---

### Post by sandyd on 2012-11-17
I like using chkconfig, but thats only because its easy to remember :)

```

sudo apt-get install chkconfig
sudo chkconfig apache2 off
```

---

### Post by mastablasta on 2012-11-18
adding -f  parameter worked, thanks. i saw some message about it but i didn't knwo where the parameter gues :-D

i am sure the second method also works, but needs an extra programme to be installed :-P

---

