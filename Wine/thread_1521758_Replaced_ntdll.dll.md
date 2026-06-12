---
title: "Replaced ntdll.dll"
date: 2010-07-01
forum: Wine
---

### Post by sarthorks on 2010-07-01
how do i find out if i have the wrong ntdll.dll in my system32 folder? I think i may have replaced the original one with some other downloaded from the net.

I'm on Ubuntu 10.04 and using wine-1.2-rc4.

---

### Post by cogadh on 2010-07-01
It doesn't matter if you replaced it, as long as the override for it is not set in winecfg. The "DLL" files in Wine's system32 directory are little more than pointers to Wine's actual "DLL" files (which are not found in the .wine directory) and as long as winecfg still has ntdll set for "built-in" or has no override set at all, it is still using the normal Wine ntdll.

BTW - ntdll is on the very short list of DLL files in Wine you should never try to replace (along with kernel32.dll, gdi32.dll and user32.dll) as they can and will break Wine's core functionality. As far as I know, even if you did replace the ntdll in Wine's system32, it won't let you override it in winecfg.

---

