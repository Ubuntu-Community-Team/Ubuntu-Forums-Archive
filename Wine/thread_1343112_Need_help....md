---
title: "Need help..."
date: 2009-12-01
forum: Wine
---

### Post by Draygera on 2009-12-01
I just tried to get epsxe to work Ubuntu 9.10 64-bit edition and had to use getlibs to get some of of the 32-bit dependencies. What happened after that was my WINE no longer worked. This is what my terminal keeps on saying:

draygera@ubuntu:~$ winecfg
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": libasound.so.2: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
[http://www.freetype.org](http://www.freetype.org)
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
err:systray:initialize_systray Could not create tray window
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
draygera@ubuntu:~$ libgcc_s.so.1 must be installed for pthread_cancel to work
wine client error:10: write: Bad file descriptor

Can anyone help me please? And thank you!!! I want to get back to WOW as soon as possible!!!

---

### Post by saadlulu on 2009-12-01
try doing what the terminal is telling u to do mate :)
go to : [http://freetype.sourceforge.net/download.html#stable](http://freetype.sourceforge.net/download.html#stable)
download and install 
and give us a feed back :)

am still a noob in ubuntu, but i think this should work.

---

### Post by Draygera on 2009-12-02
The thing is, I already had them installed. It was working before I updated my graphics driver.

---

