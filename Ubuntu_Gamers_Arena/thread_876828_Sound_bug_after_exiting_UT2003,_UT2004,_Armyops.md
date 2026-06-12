---
title: "Sound bug after exiting UT2003, UT2004, Armyops"
date: 2008-08-01
forum: Ubuntu Gamers Arena
---

### Post by 3416 on 2008-08-01
Hi

My problem is, every time when I exit UT2003, UT2004 or Armyops the games are blocking the sound driver, cause they don't exit completely.

If i kill the processes by console the sound is working again, but just after armyops. After UT the sound driver is locked completely.

I have restarted alsa but there is no change.

The only way to get the sound back to work again is to restart the OS.

Is there any bugfix.

Im running ubuntu 8.04
AMD Atlon 64 3500+
nvidia gforce 6600GT
2GiB Ram
NVidia CK804 on onBoard sound

---

### Post by Brebs on 2008-08-02
> **3416 said:**
> cause they don't exit completely.
This is a bug in the libs that come with UT2004. The solution is to [symlink its libs](http://forums.gentoo.org/viewtopic-t-607847.html) to your up-to-date ones.
```
cd /opt/ut2004/System/
cp libSDL-1.2.so.0 libSDL-1.2.so.0.backup
ln -sfn /usr/lib64/libSDL-1.2.so.0 libSDL-1.2.so.0
cp openal.so openal.so.backup
ln -sfn /usr/lib64/libopenal.so openal.so
```
So that you have:
```
ll /opt/ut2004/System/openal.so
lrwxrwxrwx 1 root root 25 2008-05-15 16:41 /opt/ut2004/System/openal.so -> /usr/lib64/libopenal.so.0

ll /opt/ut2004/System/libSDL-1.2.so.0 
lrwxrwxrwx 1 root root 26 2008-05-15 16:42 /opt/ut2004/System/libSDL-1.2.so.0 -> /usr/lib64/libSDL-1.2.so.0
```
If you're running 32-bit rather than 64-bit, then obviously change lib64 to lib in all of the above.

---

