---
title: "xpenguins"
date: 2013-04-06
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2013-04-06
ever since i have upgrade to 13.04 keep getting this error message if i try to run xpenguins(note it worked in 12.10)

ray@ray-GC660AA-ABA-SR5123WM:~$ xpenguins
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  15 (X_QueryTree)
  Resource id in failed request:  0x5200003
  Serial number of failed request:  9
  Current serial number in output stream:  9

tks

---

### Post by tgalati4 on 2013-04-06
Not much to go on.  And there aren't many dependencies.

tgalati4@Mint14-Extensa ~ $ apt-cache depends xpenguins
xpenguins
  Depends: libc6
  Depends: libx11-6
  Depends: libxext6
  Depends: libxpm4
  Conflicts: xpenguins:i386

I'm running  Linux Mint Mate 14, 64-bit and it doesn't work for me.  At least no penguins to be found.  But I don't get the error message:

tgalati4@Mint14-Extensa ~ $ xpenguins
Redrawing overwritten desktop icons

I think Global Warming has wiped out the xpenguins!

---

### Post by rburkartjo on 2013-04-07
tg tks just wanted to make sure it was not just me. rofl

---

### Post by rburkartjo on 2013-04-07
latest set of updates i did this am fixed


i found this script to kill the penguins. run in the terminal. just no brain amusement.

#!/bin/bash 
 xpenguins -n 42 -s

---

