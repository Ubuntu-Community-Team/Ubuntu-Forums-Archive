---
title: "Ultra 2 and Sun TGX+ framebuffer - text ok. Black screen with graphics"
date: 2007-04-09
forum: Sun Sparc Users
---

### Post by sandpiper on 2007-04-09
Hello 

Have sucessfully installed Ubuntu dapper on Ulltra 2 in text mode thanks to previous help on this forum. 

The Ultra 2 is running a Sun TGX+ framebuffer card installed in SBUS slot 0.  

My problem is with running X-windows on such a card.  
I appear to have a probelm with the card switching to graphics mode. I get a  black screen. 

Have viewed the dmesg file and I see:

Console: Switching to colour framebuffer device 144x56
cg6: CGSix [TGX+ sparc] at 1ff: 000000000

Searching all the forums for "example" dmesg file  I see the entry should be:

Console: switching to colour framebuffer device 144x56
fb0: cgsix at 1ff 30000000 TEC Rev 4 CPU sparc Rev b [TGX+]

I have subsequently used a utility called Fbset with option --info to interrogate the card. This programme  appears to use the device node fb0 to gain info on the card. The "address" line in the print out  is shown  00000. I presume this is wrong.....
My questions are: 
1) Given the card is recognised by the Kernel for the text mode install why is there a problem with graphics. 
2) Are there different drivers being used. 
3) Should I be looking for another driver other than cg6. If so how do I install this driver. 
4) Can I do this at install time using Modprobe? 
5) Or do i have a Udev problem. I note the graphics driver class is there but not a listing in Udev. 
6) Do i need to run Udev to install a driver. I note the udev deamon is running.. 

Any help really appreciated particularly if I have gone down the wrong diagnosis route!  Chris

---

