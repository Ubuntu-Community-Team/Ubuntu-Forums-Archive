---
title: "SD reader does not work in new Serval performance laptop"
date: 2007-12-14
forum: System76 Support
---

### Post by bhaskar on 2007-12-14
I have a brand new Serval performance laptop on which I installed 64-bit Kubuntu Gutsy.  I am trying to get the SD reader to work so that I can import pictures from my camera.  What do I need to do to access the SD reader?  I expected that when I plugged in the SD card, I would get a pop-up, as I do when I plug in a USB drive.  Thank you very much in advance for any help.

-- Bhaskar

---

### Post by thomasaaron on 2007-12-14
We've not tested our System 76 driver support for the card reader on 64-bit Ubuntu (because we do not support 64-bit Ubuntu). So, if there is a problem arising from that, you might have to do some serious research to figure it out.

HOWEVER...

For 32-bit Ubuntu the card reader is supported by the ricoh-r5c832-fix_1_i386.deb
package located inside of the System 76 driver. You could try to run the driver. If that doesn't work, you could try to install the package. If that doesn't work...

There are several formats that card readers under Ubuntu are not compatible with. We've run into problems recognizing cards formatted by palm devices as well as some others. So, you might try re-formatting the card.

Best,
Tom

---

