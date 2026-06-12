---
title: "Installing OS from a Harddrive Image?"
date: 2010-06-21
forum: Virtualisation
---

### Post by Arwen17evenstar on 2010-06-21
I know you can use an iso file in Virtualbox to install an OS instead of burning it to a dvd.  But I don't have an install disc for my current windows OS. The only thing I can do is take an image of my hard drive.   

Can I use that kind of image in Virtualbox since it doesn't have an installer or anything? Its just an image of a hard drive, not an image of a install disc.  And would it work the same way where you just select iso image when setting it up etc.? 

 I wanna make this work so I can get ubuntu and some others running virtually on my desktop computer.

**Edit:**
I'm thinking this is impossible unless I find an installation iso for vista.

---

### Post by Tylerjd on 2010-06-22
It is possible, but difficult, and the drivers *may* be screwed up. What is the image extention? Or is it a bit for bit copy of the HDD. If the second is true, mount the HDD in your virtualized of choice and reverse clone it.

Also, if it is an image file, what did you use to image it. If Clonezilla, ten mount the device with the image and mount the clonezilla iso I. Your virtualizer of choice and reverse image (restore) onto a virtual disk in the virtualizer of choice. As stated before though, the drivers will probably be messed up.

---

### Post by JustinR on 2010-06-23
If its a current OS like Vista or 7 then it will work fine - I use my Vista installation on my computer normally and in VirtualBox.

If its an older one such as XP its possible it could work but in the Control Panel Hardware section create a new hardware profile for VirtualBox.

Edit: Instead of creating a new hard drive image, if Windows is the only OS on the hard drive then you can tell VirtualBox to just use your existing Windows hard drive instead of a virtual one. If there are more os' on the computer then its a little more complicated than that but it should work. I don't know - just a thought. :)

---

