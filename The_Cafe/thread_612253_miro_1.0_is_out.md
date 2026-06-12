---
title: "miro 1.0 is out"
date: 2007-11-13
forum: The Cafe
---

### Post by ssam on 2007-11-13
miro 1.0 is out [http://www.getmiro.com/](http://www.getmiro.com/) ubuntu repos at [http://www.getmiro.com/download/ubuntu.php](http://www.getmiro.com/download/ubuntu.php)

> Miro (previously known as Democracy Player and DTV[1]) is an Internet television application developed by the Participatory Culture Foundation (PCF).

Miro can automatically download videos from RSS-based "channels", manage them and play them. Miro is designed to mesh with other PCF products such as Video Bomb, a social tagging video website, and the Channel Channel, a TV guide for internet television.

also digg it at
[http://digg.com/software/Miro_1_0_is_here](http://digg.com/software/Miro_1_0_is_here)
or
[http://digg.com/software/Finally_Miro_1_0_is_released_2600_video_channels_2](http://digg.com/software/Finally_Miro_1_0_is_released_2600_video_channels_2)

---

### Post by FG123 on 2007-11-13
Interesting. I hope it's not as buggy as its predecessor was.

---

### Post by Frak on 2007-11-13
> **FG123 said:**
> Interesting. I hope it's not as buggy as its predecessor was.
Buggy, slow, and nearly unusable. Plus, it made random calls to firefox sometimes. I'll try it out and see if it changed any.

---

### Post by clouserw on 2007-11-14
I just upgraded with apt-get and it didn't pull the new 'miro-data' package with it.  I emailed them, but until they fix the dependency, make sure you're upgrading miro and miro-data.

---

### Post by sprice on 2007-11-15
couldn't grab it with apt-get so i downloaded the tar.gz

I've got everything needed but i'm running into problems

>:~/Miro-1.0/platform/gtk-x11$ ./run.sh
Traceback (most recent call last):
  File "setup.py", line 75, in ?
    from Pyrex.Distutils import build_ext
ImportError: No module named Pyrex.Distutils
>:~/Miro-1.0/platform/gtk-x11$

---

