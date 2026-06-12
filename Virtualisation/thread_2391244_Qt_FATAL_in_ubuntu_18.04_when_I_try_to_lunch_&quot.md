---
title: "Qt FATAL in ubuntu 18.04 when I try to lunch &quot;virtualbox&quot;"
date: 2018-05-07
forum: Virtualisation
---

### Post by rubenlb on 2018-05-07
I have installed Virtualbox 5.2.10 from deb package with gdebi and everything was good, but when I try tu run the application, shows:

- - - - - - - 
Qt FATAL: This application failed to start because it could not find or load the Qt platform plugin "xcb"
in "".

Available platform plugins are: dxcb, eglfs, linuxfb, minimal, minimalegl, offscreen, vnc, xcb.

Reinstalling the application may fix this problem.

- - - - - - - -  
I tried to reinstall but I have the same problem.

Something weird is when i install with deb package, in software center appears virtualbox to install :(. It seems there are  some conflict between software center and deb packages installation

---

### Post by deadflowr on 2018-05-07
*Thread moved to **Virtualization** *

---

### Post by cruzer001 on 2018-05-07
Several people getting hit with this one.  Check this out

[https://www.google.com/search?client=ubuntu&hs=s4G&channel=fs&ei=sx3xWte0BJKgjwP85YeIAw&q=virtualbox+could+not+find+or+load+the+Qt+platform+plugin+%22xcb%22&oq=virtualbox+could+not+find+or+load+the+Qt+platform+plugin+%22xcb%22&gs_l=psy-ab.12...7910.11702.0.16158.2.2.0.0.0.0.154.286.0j2.2.0....0...1..64.psy-ab..0.1.154...0j0i67k1j0i10i67k1.0.slgJYCmJXag](https://www.google.com/search?client=ubuntu&hs=s4G&channel=fs&ei=sx3xWte0BJKgjwP85YeIAw&q=virtualbox+could+not+find+or+load+the+Qt+platform+plugin+%22xcb%22&oq=virtualbox+could+not+find+or+load+the+Qt+platform+plugin+%22xcb%22&gs_l=psy-ab.12...7910.11702.0.16158.2.2.0.0.0.0.154.286.0j2.2.0....0...1..64.psy-ab..0.1.154...0j0i67k1j0i10i67k1.0.slgJYCmJXag)

I didn't get hit though.  I loaded vBox (same version) from our Ubuntu software sources.

---

### Post by rubenlb on 2018-05-09
Thank you  cruzer001!
I could solve the problem..... I did:

1) open terminal (ctrl+alt+t)
2) write: locate libqxcb to look where to find the libqxcb.so file
3) run ldd on it (ldd /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so). ldd will display all dependencies and you will have to install packages corresponding to the NOT FOUND entries (sudo apt install --reinstall libxcb-xinerama* for me).
 After that the application should work.

---

### Post by surajit697 on 2018-07-31
Thank you.
Encountered the same problem, and exactly same solution worked. Mine also missing that libxcb-xinerama.so file.
Thanks.

---

