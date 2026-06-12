---
title: "[SOLVED] Wine from sources - trouble with configure (conf think dev-libs is missing, "
date: 2008-12-30
forum: Wine
---

### Post by fellrond on 2008-12-30
[UPDATE]
it solved!
Just did:
1. Ctrl+Alt+F1 (Enter non-graphical tty1)
2. Login to your account
3. sudo /etc/init.d/kdm stop
4. sudo ./NVIDIA-Linux-x86_64-180.xx-pkg**2**.run
5. Answer 'yes' to all questions
6. sudo /etc/init.d/kdm start
7. ?????
8. PROFIT!
[/UPDATE]

Greetings to all,

I'm trying to install wine from sources to Kubuntu 8.10 (x86_64) with NVIDIA 180.11 drivers.

But ./configure returns at the end:

```
configure: libxcursor development files not found, the Xcursor extension won't be supported.
configure: libxi development files not found, the Xinput extension won't be supported.
configure: XShm development files not found, X Shared Memory won't be supported.
configure: XShape development files not found, XShape won't be supported.
configure: libXxf86vm development files not found, XFree86 Vidmode won't be supported.
configure: libxrandr development files not found, XRandr won't be supported.
configure: libxinerama development files not found, multi-monitor setups won't be supported.
configure: libxcomposite development files not found, Xcomposite won't be supported.
configure: libGLU development files not found, GLU won't be supported.
configure: libhal development files not found, no dynamic device support.
configure: libsane development files not found, scanners won't be supported.
configure: libgphoto2 development files not found, digital cameras won't be supported.
configure: liblcms development files not found, Color Management won't be supported.
configure: libldap (OpenLDAP) development files not found, LDAP won't be supported.
configure: libcapi20 development files not found, ISDN won't be supported.
configure: libcups development files not found, CUPS won't be supported.
configure: fontconfig development files not found, fontconfig won't be supported.

configure: WARNING: libxrender development files not found, XRender won't be supported.

configure: WARNING: No OpenGL library found on this system.
OpenGL and Direct3D won't be supported.

configure: WARNING: libxml2 development files not found, XML won't be supported.

configure: WARNING: libxslt development files not found, xslt won't be supported.

configure: WARNING: OpenSSL development files not found, SSL won't be supported.

configure: WARNING: libjpeg development files not found, JPEG won't be supported.

configure: WARNING: libpng development files not found, PNG won't be supported.

configure: Finished.  Do 'make depend && make' to compile Wine.

```But all listed libs (and their dev files) are installed.

Install from binaries completes propertly, but it doesn't work.
For d3d app (Civilization 4, for example) it returns:
```
err:d3d:WineDirect3DCreate Direct3D9 is not available without opengl
```For opengl (WoW -opengl) it returns:
```
err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": libGL.so.1: cannot open shared object file: No such file or directory
err:module:import_dll Loading library OPENGL32.dll (which is needed by L"Z:\\media\\D\\Games\\World of Warcraft RU\\WoW.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\D\\Games\\World of Warcraft RU\\WoW.exe" failed, status c0000135

```Any ideas to fix this?

P.S. Sorry for my english +)

---

### Post by Zakhafr on 2008-12-30
I have the same error after having installed 180.18 Nvidia driver.

Why do you think it would run better if you recompile Wine.
Because nVidia drivers being "closed source", I would not suppose it makes any difference if you try to compile Wine after installing the new pilots... but if you have a clue it would, I'll try to recompile (as I already did for Warcraft III succesfully) and post my results.

Just guessing ?

---

### Post by Zakhafr on 2008-12-30
My findings so far (see my post on the french forum : [http://forum.ubuntu-fr.org/viewtopic.php?pid=2316060#p2316060]("http://forum.ubuntu-fr.org/viewtopic.php?pid=2316060#p2316060"))

When you install the new drivers through nVidia procedure, it removes the outdated 32bits librairies that are under /usr/lib32

Unfortunately, Wine is a 32 bit app (even on 64 bit Ubuntu) and need these libraries.

So far I know it needs :
libGL.so.1
libGLcore.so.1
libnvidia-tls.so.1

(which are symbolic links to the relevant .so from nvidia)

To check that, I created these links anew, and linked them to the old libraries. I have no more "loading error" but a segmentation error... which doesn't trouble me as it is not the right libraries but those of the previous nVidia driver.

So tomorrow (French time) I'll install a Wubi 32  bit (thank's I do still have Windows for that :D) and try to get the good 32 bit libraries.

... unless by the time you have a better idea !

(a better idea could be to build the nVidia 32 bits drivers from my Ubuntu 64... but the nVidia script for the installation is so complicated, I'll pass on that one)

---

### Post by Zakhafr on 2008-12-31
**Solved** for me !

You need to use package **2**

(I took package 1)

Package 2 installs the 64bits libraries (as do package 1) but also asks if you do want the compatibility OpenGL libraries for 32bits.

Just answer Yes to that and Wine/OpenGL works again !

---

### Post by fellrond on 2008-12-31
> **Zakhafr said:**
> **Solved** for me !

You need to use package **2**

(I took package 1)

Package 2 installs the 64bits libraries (as do package 1) but also asks if you do want the compatibility OpenGL libraries for 32bits.

Just answer Yes to that and Wine/OpenGL works again !

Yep, it solved!
Just did:
1. Ctrl+Alt+F1 (Enter non-graphical tty1)
2. Login to your account
3. sudo /etc/init.d/kdm stop
4. sudo ./NVIDIA-Linux-x86_64-180.11-pkg2.run
5. Answer 'yes' to all questions
6. sudo /etc/init.d/kdm start
7. ?????
8. PROFIT!

---

