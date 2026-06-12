---
title: "LD_LIBRARY_PATH and 10.04 (Lucid Lynx)"
date: 2010-06-13
forum: Ubuntu Dev Link Forum
---

### Post by Emanuele_Z on 2010-06-13
Hi guys,

I am testing some shared objects (.so - to be precise these are the libav*.so which contain VP8 codec).
I managed to compile them with patches etc etc.
Now, I know mplayer uses the above libraries in shared mode (i.e. the code of libav*.so is not embedded in mplayer (while usually ffmpeg used them *copying-and-pasting* the code inside of the executable itself).

Problem is that now I'd like to test my libraries with mplayer, and what I was doing in all past version of Ubuntu (and even at work to be honest) was:
```

export LD_LIBRARY_PATH=<path to compiled libav*.so>

```
This works in virtually any Linux system, and allows to overwrite the default .so search location.
In this way when a program is dynamically linked, you can replace the .so without actually recompiling it (provided that the API stays the same naturally).

Now, apparently, with Lucid Lynx, this doesn't work anymore.
If I do this from a terminal session, it's like if the dynamic loader will refuse to use this search path.
I am not the only one noticing it:
[http://lists.freedesktop.org/archives/mesa-users/2010-May/000013.html](http://lists.freedesktop.org/archives/mesa-users/2010-May/000013.html)
[http://ubuntuforums.org/showthread.php?p=9393190](http://ubuntuforums.org/showthread.php?p=9393190)
[http://forums.amd.com/forum/messageview.cfm?catid=390&threadid=133077](http://forums.amd.com/forum/messageview.cfm?catid=390&threadid=133077)
[http://www.pythian.com/news/10857/installing-tora-with-oracle-support-on-ubuntu-10-04-lucid-lynx/](http://www.pythian.com/news/10857/installing-tora-with-oracle-support-on-ubuntu-10-04-lucid-lynx/)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9450929](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9450929)
and so on...

Why such a change?
How are developer supposed to quick test dev shared objects without changing the system-wide libraries?

Can anyone please confirm this?

Cheers,

---

