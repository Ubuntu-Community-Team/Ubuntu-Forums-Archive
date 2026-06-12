---
title: "TESTING Backport: Bzflag 2.0.0"
date: 2005-01-19
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-19
**Summary**
Awesome game!


**Backporting Process**
Grabbed + Compiled from Debian Sid.

**Upload Log**
```

building file list ...
269 files to consider
dists/warty-backports-staging/main/binary-i386/Packages.gz
        1262 100%    0.00kB/s    0:00:00  (1, 2.6% of 269)
dists/warty-backports-staging/universe/binary-i386/
dists/warty-backports-staging/universe/binary-i386/Packages.gz
        6367 100%   19.99kB/s    0:00:00  (2, 5.6% of 269)
dists/warty-backports-staging/universe/binary-i386/bzflag-server_2.0.0.20050118-4.10ubp1_i386.deb
      504912 100%   24.06kB/s    0:00:20  (3, 8.2% of 269)
dists/warty-backports-staging/universe/binary-i386/bzflag_2.0.0.20050118-4.10ubp1_i386.deb
     7834092 100%   24.35kB/s    0:05:14  (4, 8.6% of 269)
dists/warty-backports/main/binary-i386/Packages.gz
       10904 100%  186.81kB/s    0:00:00  (5, 19.7% of 269)
dists/warty-backports/universe/binary-i386/Packages.gz
       25759 100%  262.03kB/s    0:00:00  (6, 38.7% of 269)
dists/warty-extras-staging/contrib/binary-i386/Packages.gz
          20 100%    0.19kB/s    0:00:00  (7, 91.1% of 269)
dists/warty-extras-staging/universe/binary-i386/Packages.gz
         317 100%    2.50kB/s    0:00:00  (8, 92.2% of 269)
dists/warty-extras/contrib/binary-i386/Packages.gz
          20 100%    0.15kB/s    0:00:00  (9, 93.7% of 269)
dists/warty-extras/universe/binary-i386/Packages.gz
        2388 100%   12.61kB/s    0:00:00  (10, 94.8% of 269)

wrote 8357758 bytes  read 640 bytes  23121.43 bytes/sec
total size is 242031488  speedup is 28.96


```

**Known Issues**
None

**Testing Status**
Untested.

---

### Post by sparkiegeek on 2005-01-20
Works great on my system and a colleague's- thank you, now I just need to get familiar with those new flags....

---

### Post by Arktis on 2005-01-23
Thankyou kindly.  :D

---

### Post by techn9ne on 2005-01-25
Every time I run this program it crashes my gnome.

---

### Post by Baltor on 2005-01-27
Yup, mine crashes gnome too.

---

### Post by jdong on 2005-01-28
Hmm, any telltale errors? What video card?

---

### Post by Baltor on 2005-01-28
No errors, but I am using the nvidia driver package if that's any help.

---

### Post by jdong on 2005-01-28
hmm... It might be an Nvidia thing. Are you using the default kernel? Can you run Glxgears without crashing? How about other OpenGL games (i.e. Supertux in OpenGL mode)

---

### Post by Baltor on 2005-01-29
I can run glxgears and supertux fine in OpenGL mode, so I'm not sure what the problem is.

---

### Post by john280z on 2005-02-03
run "glxinfo", check for a line (near top) that says:

direct rendering: Yes

(you can run glxgears and _not_ have 3D rendering)

if you do not have rendering them go here and check each and everything presented here:

[http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)

---

### Post by ming0 on 2005-02-09
I'm having the same problem (I have a radeon 95pro). I do have direct rendering enabled, and can play games like quake III and doom 3 (tho doom 3 crashes :().

Do you have any other ideas or suggestions?

Thx

---

### Post by jdong on 2005-02-09
Very weird -- I've failed to reproduce these problems. Perhaps I'll do a rebuild.

---

### Post by rufius on 2005-02-10
[QUOTE=techn9ne]Every time I run this program it crashes my gnome.[/QUOTE]
 It doesn't crash my gnome but the game isn't fully responding to my input. When press <tab> it won't jump the tank, so I tried to remap the key and still get nothing. Anyone had that problem?

---

### Post by sparkiegeek on 2005-02-10
Sounds silly but has the server you're connecting to turned off jumping?

---

