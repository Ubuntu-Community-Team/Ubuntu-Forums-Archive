---
title: "dvgrab ERROR! &quot;NO DV&quot;"
date: 2010-02-27
forum: Ubuntu Studio
---

### Post by squareff255 on 2010-02-27
Well, I just got a brand new Canon Vixia HV40 which cost me $700 and I'm so excited about it, but I can't get dvgrab to capture it onto the computer! It came with a windows cd and I was pretty bummed, but I installed it on a windows-box and bought a firewire cable, but it wouldn't work... so I did some research and ppl were saying you could do it on Ubuntu with dvgrab/Kino and a firewire connection. So, I've been trying for days and can't get it to work. I have run the following commands:
```

sudo apt-get dvgrab

```
```

sudo apt-get kino

```
```

sudo modprobe raw1934

```
```

sudo modprobe dv1934

```
```

sudo chmod 777 /dev/raw1934

```
```

sudo chmod 777 /dev/dv1934

```
and I have run Kino as root and added myself to the disk group. I have gotten the AC controls to work. I can rewind and stop and play and whatever from Kino or command-line (using dvgrab), but if I try to capture in Kino, it says "waiting for dv..." and counts down from 10 and when it gets to 0, it stops and says "No DV". When I run the 
```

sudo dvgrab

```
command in the terminal, it gives the following output:
```

Found AV/C device with GUID 0x0000850001ec335d
""     0.00 MiB 0 frames
Capture Stopped
Error: no DV

```
Also, when I run dvgrab, I can see the video playing on my camera's lcd screen, but still, nothing captures.
I know this error has been posted quite a few times on many forums, but I'm just hoping with more posts, it will get more attention and focus.
THANKS in advance for any help you may offer. I'M DYING HERE!!!

Squareff255

---

### Post by squareff255 on 2010-03-10
Well, in case anyone has this problem and stumbles across this, I figured it out. I just needed to issue the following commands:
[code]
sudo modprobe raw1394
[\code]
[code]
sudo modprobe dv1394
[\code]
[code]
sudo chmod 777 /dev/raw1394
[\code]
[code]
sudo chmod 777 /dev/dv1394/
[\code]
Then make sure the camera is on HDV and not DV and then issue this command:
[code]
sudo dvgrab -f hdv
[\code]
Yeah... pretty simple. I felt a bit silly when I figured it out. :)

---

