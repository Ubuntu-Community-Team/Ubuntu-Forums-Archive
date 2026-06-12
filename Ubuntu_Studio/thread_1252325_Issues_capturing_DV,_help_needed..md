---
title: "Issues capturing DV, help needed."
date: 2009-08-28
forum: Ubuntu Studio
---

### Post by jaciminelli on 2009-08-28
Software Info:
ubuntu 9.04 amd64
2.6.28-15-generic
dvgrab 3.2
kino 1.3.0

Hardware Info:
04:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
Canon HV40 HDV camcorder.

Problem occurs in either dvgrab from terminal or running
kino.
Camcorder receives command over firewire cable begins playing
from beginning of tape, playback stops after about 5 seconds,
dvgrab complains.

Output is

'Found AV/C device with GUID 0x0000850001ee1b16
""     0.00 MiB 0 frames
Capture Stopped
Error: no DV'

When using kino essentially the same thing happens only kino
timeout waiting for signal from camera even after playback is
started from the tape.

Permissions and module loading issues have been taken care
of, let me know any commands you need me to run. I also have
gdb info though I have never used gdb before and may not have
done it correctly.

Failure to fix this issue will most likely lead to abandoning
of linux and a significant budget increase for my project so i
can by proprietary editing software.

-JAC

---

### Post by FreezWay on 2009-08-28
try things discussed [here]("http://ubuntuforums.org/showthread.php?p=7841763#post7841763")

---

### Post by jaciminelli on 2009-08-29
Hey, thanks for the response. Something someone in that thread mentioned got me thinking. I was shooting in HDV format this is apparently not supported by dvgrab, dvgrab only works with regular DV.

I have successfully shot and captured regfular DV content. I just now need a way to either get support for the HDV format, or to shoot my current project in DV.

If anyone knows a way to enable HDV support feel free to let me know, I will be looking into that.

Thaks again.

-JAC

---

### Post by bigtom2 on 2009-09-02
Try starting kino in terminal mode 
sudo kino

it pulls up the gui i had a lot less problems this way 
gust make sure your camera is on and running.








> **jaciminelli said:**
> Hey, thanks for the response. Something someone in that thread mentioned got me thinking. I was shooting in HDV format this is apparently not supported by dvgrab, dvgrab only works with regular DV.

I have successfully shot and captured regfular DV content. I just now need a way to either get support for the HDV format, or to shoot my current project in DV.

If anyone knows a way to enable HDV support feel free to let me know, I will be looking into that.

Thaks again.

-JAC

---

