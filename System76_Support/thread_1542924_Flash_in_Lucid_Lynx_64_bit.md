---
title: "Flash in Lucid Lynx 64 bit"
date: 2010-07-31
forum: System76 Support
---

### Post by silvertuna on 2010-07-31
Flash in Lucid 64-bit was very rocky (some mouse clicks disabled) until i came across this solution. It worked for me.

```
gksudo gedit /usr/lib64/nspluginwrapper/i386/linux/npviewer
add the following line BEFORE the last line of text
export GDK_NATIVE_WINDOWS=1
Save
```

Thanks to: [http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

---

