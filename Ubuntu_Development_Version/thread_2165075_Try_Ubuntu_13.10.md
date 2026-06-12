---
title: "Try Ubuntu 13.10"
date: 2013-08-03
forum: Ubuntu Development Version
---

### Post by volkerbradley on 2013-08-03
My system is 160 GB Intel X25-M Solid State Drive, Core i7-920XM Processor Extreme Edition ( 45nm, 8M), 8 GB DDR3 1066 MHZ 2 DIMMs, Nvidia GeForce GTX 285M Graphics with 1GB GDDR3 Vi.  Presently have Ubuntu 13.04 - 64 Bit Linux installed.
I have downloaded Ubuntu 13.10 (Saucy Salamander) Daily Build 64-bit PC (AMD64) desktop image and installed it on a bootable USB drive.
When I boot from this image, I get to the initial screen as shown in the included file, but I can't find a way to click on the "Try Ubuntu" button.
Could you give me a suggestion on how to try the alpha 2 version of 13.10?

---

### Post by Frogs Hair on 2013-08-03
Moved to Ubuntu +1

---

### Post by terry-gardener on 2013-08-03
have you tried clicking the cd icon above the try ubuntu button if the try ubuntu isn't clickable. not tried the new ubuntu this time round

---

### Post by grahammechanical on 2013-08-03
The outer edge of the button should be orange when the button is active. You may have to wait a few seconds. You can try pressing tab as that moves the focus from button to button.

There is another way to run the live session. Boot to the DVD/USB and at the first purple screen press Enter. Then press enter again to select English as the session language (it is default) and at the underlying screen you will see options. One of those options is Try Ubuntu. Another option is Install Ubuntu. We use the arrow keys and the Enter key to make a selection. See, if that works.

I might suggest that it is better to use the daily image as there have been a number of updates since the Alpha milestone was reached.

Regards.

---

### Post by volkerbradley on 2013-08-04
Thanks for your responses.  I found that if I clicked on the <- arrow, I was brought to the language selection screen.  When I then clicked on Enter, a new screen appeared with the choice to Try Ubuntu without installing.  I seem to have X Window problems when I try to use 13.10.  Newver saw the cursor and could not control anything.

---

### Post by grahammechanical on 2013-08-05
One assumes that if 13.04 is installed then there should not be issues running a 13.10 live session. But for many weeks during the development cycle of 13.04 I could not run a live session without using one or two of the F6 options even though I never needed to do that with any other version of Ubuntu. The issue was solved later on in the development cycle. It may be a similar situation that you are in.

We assume that by now the live session and the installer should all be sorted out but that is not the case. I have had the installation fail at the copying files stage because the partition did not have enough space when in fact it had 10GB - more than enough. I tried one of the other methods of installing and this time the installation completed.

This is how things are.

Regards.

---

### Post by ventrical on 2013-08-05
> **grahammechanical said:**
> 

I might suggest that it is better to use the daily image as there have been a number of updates since the Alpha milestone was reached.

Regards.

Considering the daily ...

correction.. seems only the btrfs filesystem option is affected..

---

