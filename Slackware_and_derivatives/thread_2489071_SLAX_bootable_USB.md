---
title: "SLAX bootable USB"
date: 2023-07-17
forum: Slackware and derivatives
---

### Post by rm70 on 2023-07-17
I was attempting to follow the instructions things were going well until i opened terminal inside the flashdrive
and typed the command Sudo  ./bootinst.bat terminal came back as " command not found" can someone please tell me what went wrong? Thanks

---

### Post by Rubi1200 on 2023-07-17
Hi and welcome to the forums :-)

What instructions? Please share the link so we know what you are trying to do.

Are you trying to do this from a Linux or Windows computer?

---

### Post by deadflowr on 2023-07-18
*Thread moved to **Slackware and derivatives***

---

### Post by rm70 on 2023-07-18
I’m using Ubuntu 18.04

---

### Post by Rubi1200 on 2023-07-18
Well, if you are on Ubuntu then your command above is incorrect.

```
[COLOR=#000000]Sudo ./bootinst.bat[/COLOR]
```

Sudo should be lowercase sudo and .bat is a Windows extension so won't work on Linux.

Where did you get the instructions?

Also, which version did you download; based on Slackware or Debian?

---

### Post by rm70 on 2023-07-18
I downloaded debian version 11.06.from slax.org. The capital S was my fault. as instructed in article I opened terminal within the drive and copied the command from article on Ubuntubuzz and paste sudo ./bootinst.bat in the terminal.  Question. is there supposed to be a space between sudo and the ./ ? thanks for your help. I'm running  ubuntu 18.04. [https://www.ubuntubuzz.com/2022/02/how-to-make-slax-bootable-usb-stick.html](https://www.ubuntubuzz.com/2022/02/how-to-make-slax-bootable-usb-stick.html)

---

### Post by Rubi1200 on 2023-07-18
I'm not sure where you found those instructions but according to the Slax website, the instructions they give are here:
[https://www.slax.org/starting.php](https://www.slax.org/starting.php)

I don't see where they say to use sudo and anyway you would be looking for bootinst.sh and not bootinst.bat

---

### Post by rm70 on 2023-07-18
[https://www.ubuntubuzz.com/2022/02/how-to-make-slax-bootable-usb-stick.html](https://www.ubuntubuzz.com/2022/02/how-to-make-slax-bootable-usb-stick.html) i finally got link to the instructions i used. Thanks I will check out the link you gave.

---

