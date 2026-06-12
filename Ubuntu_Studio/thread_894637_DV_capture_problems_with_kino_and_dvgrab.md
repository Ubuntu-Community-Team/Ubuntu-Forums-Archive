---
title: "DV capture problems with kino and dvgrab"
date: 2008-08-19
forum: Ubuntu Studio
---

### Post by nerdzyboy on 2008-08-19
I have a canon optura 20 dv camera connected to my computer via firewire.  I'm trying to capture video in kino and dvgrab but neither of them is able to capture anything.  dvgrab stops with error "error: no dv" and kino says "waiting for dv 10 9 8 7 ..." until it reaches 0 and nothing happens. 
 
Both kino and dvgrab detect the camera and both of them can use dvc controls (play, pause, fast forward, etc) on the camera.  According to a couple of forums I read I have set the permissions of /dev/raw1394 and /dev/dv1394 to rw for everyone and I also tried to unload the eth1394 module (sudo rmmod eth1394).  I have also added myself to the disk group.

Still, I cannot capture any video from my camera...  

Could anyone help me figure out how to solve this problem?

just in case, here is the output of lsmod | grep 1394:

raw1394                29144  0 
dv1394                 20536  0 
ohci1394               33584  1 dv1394
ieee1394               93752  3 raw1394,dv1394,ohci1394

Please help me, I have a stack of dv tapes I'd like to convert to dvd...
nerdzyboy

---

### Post by eggdeng on 2008-08-20
Strange.
Check that the firewire cable isn't coming loose at just the wrong moment, maybe because you're moving the camera. You might try running kino as sudo to get around possible permissions problems.

---

### Post by nerdzyboy on 2008-08-20
I forgot to mention it but i'm already running kino as root.  And for the cable, the connection is correct.

---

### Post by remeeraz on 2008-10-14
Here are my instructions on how to get your firewire to work properly.

[http://ubuntuforums.org/showthread.php?t=946708](http://ubuntuforums.org/showthread.php?t=946708)

If you are using a 1394 network adaptor, get shot of it, and get another form of network adaptor. Security issues will basically give network users access to all areas on your system (IF they are clever enough) once you've configured settings correctly to get full control of your DV Cam over firewire.

Doesn't matter what make and model cam you are using so long as it's an IIDC-compliant camera (and nearly ALL of them are), if it's got firewire, it should work.

If you use any node other than the raw1394 node, you will have problems.

---

### Post by stinger30au on 2008-10-14
is your camera supported by the kernel itself???



if you go searching for firewire linux camera you should find a list of camera that are supported



your camera may not be one of the supported ones and may never work till its driver issues are fixed

---

