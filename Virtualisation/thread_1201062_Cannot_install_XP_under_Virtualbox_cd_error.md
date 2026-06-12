---
title: "Cannot install XP under Virtualbox cd error"
date: 2009-06-30
forum: Virtualisation
---

### Post by osl_d on 2009-06-30
Hello guys,

I'm trying to install Windows XP in VirtualBox since i don't get Wine to work properly.
The VirtualBox install went smooth, no problems at all, but when i tried to install XP everything went fine untill right after the "reboot".

It starts asking for an SP2 cd, which i have in the drive, it's the typical windows "please put a cd in the drive and press ok" window.
However when i press "ok" it comes back ](*,). Now it even got to the stage where i have about 15 secs to look at this message and then my comp gets real slow the virtualbox window closes and everything is back to normal except that the window is closed.

I have googled it and in all tutorials/howto's the install seems to be a piece of cake according to them a baby could do it. But somehow for me it doesn't work.
Does anyone recognize my situation? Cause I havn't found anything in the forum. Maybe I'm missing some real easy set up thing or so.(i hope so)



I have:
Almost no knowledge of Ubuntu (sorry, i'm learning though)
Ubuntu 9.04 jaunty with latest updates
VirtualBox 3.0.0 downloaded and installed today 30.06.09
Genuine XP and SP2 cd's
a screenshot of the window before it closed

---

### Post by Perryg on 2009-07-02
Why not unmount the CD in the VBox settings for the guest.  Boot up and then put the cd in the drive and mount it from the devices tab of the VBox window then hit OK.  Assuming this is a CD and not an image file.

---

### Post by osl_d on 2009-07-03
Well thanx for the reply. But in the mean time i install the windows 7 RC on the virtual harddisk (the one of XP) and that runs as normal as it can be.
Since i wanted to try out your advice i made a new virtual machine with 20GB, RAM and rest stay same. I don't get further as the loading after that it gives me an error saying all windows nonsens.
Second try with 60 GB same, RAM and rest. It installs with no problems!
Windows once again confuses me

---

