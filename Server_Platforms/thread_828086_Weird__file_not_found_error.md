---
title: "Weird *** file not found error"
date: 2008-06-13
forum: Server Platforms
---

### Post by aaron465 on 2008-06-13
Hi,

I am currently trying to install a SRCDS server on my Ubuntu Server 8.04 (64-bit) machine. I have installed it on other machines many a time but its not really that which has gone wrong.

After I download the hldsupdatetool.bin from steampowered.com and chmod +x it i try to run it by doing;

```
./hldsupdatetool.bin
```

I then get the following error:

```
aaron@server:~/srcds_1$ ./hldsupdatetool.bin
-bash: ./hldsupdatetool.bin: No such file or directory

```

But it is there! there IS such a file - so why cant it run???



Thanks in advance
Aaron

---

### Post by heebus on 2008-06-13
ls -l

Is it executable to you?  Is it in the current directory? 

Try using its full path...
  /home/aaron/srcds_1/hldsupdatetool.bin

---

### Post by aaron465 on 2008-06-13
Hi,

just tried with the whole path, that fails aswell - same error.
Also, yes the file is executable for me permissions are set to 775 on it, yet still i cant execute.

Thanks

Aaron

---

### Post by heebus on 2008-06-13
Try installing this.

sudo apt-get install lib32gcc1

---

### Post by aaron465 on 2008-06-13
aha! that has done the trick nicely!


Thanks Very Much
Aaron

---

