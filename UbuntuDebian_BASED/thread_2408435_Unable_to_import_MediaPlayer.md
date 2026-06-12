---
title: "Unable to import MediaPlayer"
date: 2018-12-18
forum: Ubuntu/Debian BASED
---

### Post by sumi12 on 2018-12-18
I have installed ffmpeg and ffpyplayer on raspberry pi 3 - raspbain stretch. When I try to import MediaPlayer as: ```
from ffpyplayer.player import MediaPlayer
```
I get this error: ```
Traceback (most recent call last):  File "<stdin>", line 1, in <module>
  File "/home/pi/.virtualenvs/cv/local/lib/python3.5/site-packages/ffpyplayer/player/__init__.py", line 10, in <module>
    from ffpyplayer.player.player import MediaPlayer
ImportError: /home/pi/.virtualenvs/cv/local/lib/python3.5/site-packages/ffpyplayer/player/player.cpython-35m-arm-linux-gnueabihf.so: undefined symbol: x264_levels
```

Can you please help me resolve this issue: ```
 undefined symbol: x264_levels
```
Thank you ^_^

---

### Post by coffeecat on 2018-12-18
*Thread moved to **Ubuntu/Debian BASED**.*

---

