---
title: "Do I have the right Nvidia Driver ?"
date: 2011-12-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-12-02
I am just wondering if these are a match. I am having a few vid probs .. but not sure if drivers may be the cause.
Fresh Install from USB

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

---

### Post by BC59 on 2011-12-02
I have the same question. I installed both (first recommended and then updates) I didn't notice any difference.

---

### Post by mc4man on 2011-12-02
Right driver, wrong decade

---

### Post by crazy bird on 2011-12-02
To be sure of using the correct nvidia driver, check if you have this driver installed: **nvidia- current**. This is the correct driver.
 
If not and you really want the latest driver, check this post of me: [http://ubuntuforums.org/showpost.php?p=11505969&postcount=7](http://ubuntuforums.org/showpost.php?p=11505969&postcount=7).

---

### Post by ventrical on 2011-12-02
> **mc4man said:**
> Right driver, wrong decade

ehehaehaehah ha... my laugh for the day :)

---

### Post by ventrical on 2011-12-02
Here is why I asked. It may be some other reason then .. looks like some sort of scroll bug perhaps.

But the Unity 2D works well on the same machine with my other Precise transition install.

---

### Post by effenberg0x0 on 2011-12-02
> **ventrical said:**
> Here is why I asked. It may be some other reason then .. looks like some sort of scroll bug perhaps.

But the Unity 2D works well on the same machine with my other Precise transition install.

Checking Nvidia at [http://www.nvidia.com/object/linux-display-amd64-96.43.20-driver.html](http://www.nvidia.com/object/linux-display-amd64-96.43.20-driver.html) (Supported Products), 96.43.20 is the right version for this card. At the source (nvidia) FTP server, there are 3 binaries for download (for current drivers, it's only one). 

```
ftp> pwd
257 "/XFree86/Linux-x86_64/96.43.20" is current directory.
ftp> ls
200 PORT command successful.
150 Opening ASCII mode data connection for /XFree86/Linux-x86_64/96.43.20.
-rw-rw-r--   1     1994     1994 11776750 Nov 28 22:45 NVIDIA-Linux-x86_64-96.43.20-pkg0.run
-rw-rw-r--   1     1994     1994 11775529 Nov 28 22:45 NVIDIA-Linux-x86_64-96.43.20-pkg1.run
-rw-rw-r--   1     1994     1994 14572507 Nov 28 22:45 NVIDIA-Linux-x86_64-96.43.20-pkg2.run
drwxrwxr-x   1     1994     1994        0 Nov 28 23:27 README
226 Transfer Complete
ftp> 

```*.pkg1.run and *.pkg2.run must be what's inside current *96*updates*.deb Ubuntu package.

---

### Post by ventrical on 2011-12-02
Thanks for the confirm.

---

