---
title: "camera not being detected"
date: 2006-02-14
forum: The Cafe
---

### Post by Specialsauce on 2006-02-14
im running xubuntu so i put it in this forum because there is no xubuntu forum

my digital camera hooks up to my computer by usb cable, and usually appears as /media/usbdisk, but since i switched to xubuntu, it no longer gets detected. is my only solution to switch back?

---

### Post by mstlyevil on 2006-02-14
[QUOTE=Specialsauce]im running xubuntu so i put it in this forum because there is no xubuntu forum

my digital camera hooks up to my computer by usb cable, and usually appears as /media/usbdisk, but since i switched to xubuntu, it no longer gets detected. is my only solution to switch back?[/QUOTE]

I could be wrong on this but if you installed xubuntu on top of a Gnome install you could just execute nautilus and it would get the job done. If you have it installed on top of a server install then I bet you could just install nautilus and use that as your file manager and then it would work.

I don't know how to go about using nautilus in XFCE but I know others on this forum have done it for simular reasons.

---

### Post by Specialsauce on 2006-02-14
[QUOTE=mstlyevil]I could be wrong on this but if you installed xubuntu on top of a Gnome install you could just execute nautilus and it would get the job done. If you have it installed on top of a server install then I bet you could just install nautilus and use that as your file manager and then it would work.

I don't know how to go about using nautilus in XFCE but I know others on this forum have done it for simular reasons.[/QUOTE]
i did that and now my menu is gone, i cant right click on the desktop (which is how i got to my debian menu), and nautilus is default. and my camera still wont work.

---

### Post by Specialsauce on 2006-02-14
nevermind, a restart fixed that. but i still cant access my camera.

---

### Post by bryanl on 2006-02-14
Because I haven't figured out the automatic mounting for this, I look in the system -> administration menu for the Device Manager. It usually lists my camera and I can select the camera and go to the advanced tab to find the dev entry for it. Then I sudo mount /dev/sda1 /mnt/temp - when the camera is mounted the wizard comes up asking me what I want to do with the camera pictures. (you may need to mkdir a mount point and sda1 may not be the dev location for your camera - substitute as per the Device Manager)

For the automount stuff, there is an fstab method and there also appears to be something that will recognize USB devices and mount them by volume label. There's probably something simple to do this but finding out what it is can be challenge

---

### Post by poofyhairguy on 2006-02-14
```
sudo apt-get install digikam
```

problem fixed.

---

### Post by fuscia on 2006-02-14
just had my problem solved...

[http://www.ubuntuforums.org/showthread.php?t=128636](http://www.ubuntuforums.org/showthread.php?t=128636)

---

### Post by TechSonic on 2006-02-15
GTkam works just fine with my USB and my Serial camera.  O.o?
Only camera problem I have is with my Micro Innovations Basic Web cam locking up my entire system when I try to use it in any application, but I have an OLD IBM PC Camera that may have bad quality but it gets the job done.

---

### Post by mstlyevil on 2006-02-15
I have a GE EasyCam and even though I have installed EasyCam2,camorama and Digikam I still can not get it to work. Digicam and EasyCam2 both find that I have a cam but it still will not work. That is what I get for having a off the wall cam.

---

