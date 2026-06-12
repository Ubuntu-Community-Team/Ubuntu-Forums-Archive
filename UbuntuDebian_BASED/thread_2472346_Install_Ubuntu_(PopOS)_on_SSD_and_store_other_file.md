---
title: "Install Ubuntu (PopOS) on SSD and store other files and games on HDD"
date: 2022-02-24
forum: Ubuntu/Debian BASED
---

### Post by jagerhino on 2022-02-24
Hello, I am running Ubuntu (PopOS) and I have installed the operating system on my SSD. However, the two hard drives I have in my PC are not used. Everything I download is put on my SSD.


I would like to have my operating system and software that needs to be launched quickly on my SSD like Steam and such. And everything else (like Steam games for example) on one of my hard drives.


I'm a beginner on Linux and I always knew how to do everything myself until now, but now I'm stuck. Could someone explain me how to do it step by step to configure it correctly?

---

### Post by deadflowr on 2022-02-24
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by oldfred on 2022-02-24
You can create a Linux partition like ext4 on HDD. Then mount it, give yourself ownership & permission and use it for data.
You can link folders into /home, so they look like they are part of system, but really on HDD not SSD.

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by jagerhino on 2022-02-28
Ok thank you

---

