---
title: "sony handycam - transfer movies (SOLVED)"
date: 2008-09-07
forum: Ubuntu Studio
---

### Post by graham-cracker on 2008-09-07
I just figured out how to transfer movies from a sony handycam (model dcr-sr32e , 'e' means European edition I'm assuming) to the computer.

The solution was surprisingly simple and the Windows solution can be found here:
[http://support.sony-europe.com/dime/tutorials/winvideotransfer/winvideotransfer.aspx?site=odw_en_GB&m=DCR-SR32E&sec=HDD](http://support.sony-europe.com/dime/tutorials/winvideotransfer/winvideotransfer.aspx?site=odw_en_GB&m=DCR-SR32E&sec=HDD)

1. Make sure the camera is off
2. Plug the camera into the dock and attach the usb cable from the dock to the computer
3. Make sure the dock ac-adapter is plugged in
4. Open the camera LCD
5. Turn on the camera
6. Touch the HDD option on the LCD

The camera should now show up on the desktop as a external drive. The videos for my camera were in:
videos are in a subdirectory within the MP_ROOT directory.

To disconnect:
1. unmount the drive (right click on the disk icon on the desktop and select 'Unmount Volume)
2. unplug the usb cable

I wanted to post this on the forums because I couldn't find the answer until I restarted into Windows (*shudder*).

If this works with any other handycam, please respond to this thread with the working model number.

Hopefully this helps someone. Cheers!

---

### Post by Veggiet on 2008-10-20
I would be very interested in this as well, I do not own a handycam, but am considering buying one, but I don't to buy it if it won't work in ubuntu 8.04. Tell me, Is model dcr-sr32e a fairly new one?

---

### Post by raffa on 2008-12-08
I confirm your solution works also for me. I also have a Sony DCR-SR32E. I'm on Ubuntu Intrepid.

The only difference is that I don't have any HDD option on the LCD. Instead I have a "Disc burn" button on the dock.
When I press it the camera is recognized as a 30.0 GB Media.
As you said videos are in /media/disk-1/MP_ROOT/101PNV01.
As for photos they are in /media/disk-1/DCIM/101MSDCF.

Thanks for your guide. It was very helpful.

---

### Post by Erlander on 2008-12-08
My Sony HDR-SR11E is recognised by Ubuntu 8.10 as a 60 GigB removable hard disc.  I just copy the movie clips over.

Rob

---

### Post by userbuntu987 on 2010-04-15
Thank you for that thread Graham. 

Mine is a Sony handycam dcr-sr52 and it works great too.
I am on ubuntu karmic koala 64bits.

---

### Post by IronArjen on 2010-08-29
Funny enough on my HDR-SR10 i can opt for Disc Burn and... Print. The print option works, obviously!

---

