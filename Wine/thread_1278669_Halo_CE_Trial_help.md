---
title: "Halo CE Trial help"
date: 2009-09-29
forum: Wine
---

### Post by InDiscord on 2009-09-29
I've installed Halo: Combat Evolved using wine, but when I try to run it with Wine i get an error message:

Cannot find 'Z:\home\myname\config.txt'

I'm on Xubuntu 9.0.4

---

### Post by InDiscord on 2009-09-30
So I get moved but no help? :\

---

### Post by ryan858 on 2009-10-01
Try running halo.exe directly from the directory, using a terminal. Like:
$cd "~/.wine/drive_c/Program Files/Microsoft Games/Halo/"
$wine halo.exe

OR

Create a launcher and use this as the command line:
env WINEPREFIX="/home/USERNAME/.wine" wine "C:\Program Files\Microsoft Games\Halo\Halo.exe" -window

Make sure to replace USERNAME with your name, and I'm not sure if \Halo\ is correct since you have trial version. make sure that's the right path. It might be \Halo Trial\.

But, running it from a terminal in the directory should make it work, and once it does, what happens to me is the graphics are all messed up and text doesn't show up correctly... it looks like Russian sorta, but not really. just messed up text. 

It worked perfect for me in Slackware, which is quite odd considering things usually *don't* work perfectly in slackware... but it won't show the graphics right in Ubuntu 9.04 64-bit. Could be the 64-bit libraries or something messing it up... i don't know really. But let me know if that happens to you, please...

---

