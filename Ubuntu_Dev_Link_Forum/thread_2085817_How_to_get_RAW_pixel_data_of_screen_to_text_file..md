---
title: "How to get RAW pixel data of screen to text file."
date: 2012-11-19
forum: Ubuntu Dev Link Forum
---

### Post by Darvenkry on 2012-11-19
Hi, I'm trying to find a simple way to get the raw pixel data, or image of the screen. For example, I can run cat /dev/input0 (to get the mouse coordinates) or cat /dev/video0 (to get the webcam video). I've tried to run cat /dev/nvidia0 but it wont work. Any other ways that this can be done?

It can either be programatic, and as generic as possible (a.k.a it should something standard that exists in the linux shell commands). So if i were to run this on a very dumbed down linux system (not a distro like Ubuntu) it would still work. 

P.S. This will later be used similar to a print screen function.

Cheers.

---

### Post by Abhinav Kumar on 2012-11-19
> **Darvenkry said:**
> Hi, I'm trying to find a simple way to get the raw pixel data, or image of the screen. For example, I can run cat /dev/input0 (to get the mouse coordinates) or cat /dev/video0 (to get the webcam video). I've tried to run cat /dev/nvidia0 but it wont work. Any other ways that this can be done?

It can either be programatic, and as generic as possible (a.k.a it should something standard that exists in the linux shell commands). So if i were to run this on a very dumbed down linux system (not a distro like Ubuntu) it would still work. 

P.S. This will later be used similar to a print screen function.

Cheers.
Hi,
 I think you are talking about > operator.
eg: if you want to put the output of ls command in a file say new.txt
```

ls > new.txt

```
This will also delete if something was already present in the file.
If you want to append to the contents of the file
use
```

ls >> new.txt

```

Regards,
Abhinav

---

### Post by Darvenkry on 2012-11-19
Thanks Abhinav, I'm aware of the > operator. I'm more interested in the source of the raw pixel data. Where can I find the data. I have managed to get something working using the framebuffer /dev/fb0 or /dev/graphics/fb0. But apparently there is no reliable way to know if that is a full frame or mid way between two frames and their will be corruption. Any thoughts?

---

### Post by japadamaray on 2012-12-09
You can do this with the **import** command provided by ImageMagick:

```
import -silent -window root RGB:-
```

This seems to work, but I haven't checked the output.

---

