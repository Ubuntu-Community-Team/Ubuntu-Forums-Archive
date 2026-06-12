---
title: "Virtualbox: Install driver for Konica Minolta Magicolor 465EN in Windows 10 guest"
date: 2023-12-25
forum: Virtualisation
---

### Post by skeptikus on 2023-12-25
I am currently trying to somewhat future proof my parents' laptop. So far I installed Ubuntu 22.04.3 LTS, Virtualbox 6.1, Windows 10 pro 64bit as guest and the Corel Suite within the guest. Now I've hit a wall trying to install the driver for the Konica Minolta Magicolor 4650EN in Windows 10. The printer is plugged in via USB, both Ubuntu and Windows recognize it but Ubuntu couldn't find any compatible drivers. So I created a USB filter in Virtualbox, assigned the Magicolor to it and then tried several available Windows 10 drivers (PostScript, PCL6, PCL5 and I think PCL3 ) within the guest OS but no printing job ever reaches the printer. Sadly the error only says "Fehler beim Drucken" (error whole printing). 

Is what I am trying to do even possible?
Am I missing something? If so what?
(I am not an Ubuntu expert so please assume a lot of ignorance on my part.)

Thanks for reading! Any suggestions?

---

### Post by howefield on 2023-12-25
Thread moved to the "*Virtualisation*" forum.

---

### Post by MAFoElffen on 2023-12-25
I really thought someone else would answer this for you...

Something like this? [https://www.net-usb.com/virtual-usb/virtualbox-usb-passthrough/virtualbox-printer/](https://www.net-usb.com/virtual-usb/virtualbox-usb-passthrough/virtualbox-printer/)

---

### Post by skeptikus on 2023-12-26
Thanks for the reply! But I seem to be unable get it to work following that tutorial. Also it makes it sound like the printer is gonna work without a driver installed which seems very unlikely. 
Option 1: I upgraded to Virtualbox 7 and followed steps 1 to 4 but they do not lead to the result described in step 5. The last bit of step 4 is "Share the printer and access it in the virtual session." That sounds great but how do I do that?
Option 2: installing USB network gate doesn't seem to be possible in Ubuntu 22.04.3 LTS as it just returns "error exit status 127" 

How do I set up a guest only printer properly? Or do I need a printer that can be used within Ubuntu first before being able to share it with the Windows 10 guest? (That's my understanding of the term "sharing", if I think about it.) Is the Magicolor 4650EN just not suitable? Or am I still missing something?

---

### Post by MAFoElffen on 2023-12-26
Pass the USB port through to the VM so that the VM Guest see's the printer attached... That is the same concept with that part of it... Once seen, then install the driver to the VM Guest.

---

### Post by skeptikus on 2023-12-27
As before, the printer shows up in devices and printers as "nicht angegeben" (not specified) and when I click on "update driver" Windows claims the best driver is already installed while in reality there is no driver installed at all. The Internet connections of the guest is working and a different laptop with only Windows 10 installed is able to find and install a working driver. Are maybe my USB or Network settings wrong?

[[IMG]https://thumbs2.imgbox.com/9f/ac/yQYhm6hI_t.jpg[/IMG]](https://imgbox.com/yQYhm6hI) [[IMG]https://thumbs2.imgbox.com/34/48/hyavVpyX_t.jpg[/IMG]](https://imgbox.com/hyavVpyX)

---

### Post by MAFoElffen on 2023-12-27
This is not really an Ubuntu, nor VirtualBox (Virtualization) support question... But rather a Windows 10 support question... But, oh well, here you go:
[https://www.youtube.com/watch?v=eyOVDNPsaNc](https://www.youtube.com/watch?v=eyOVDNPsaNc)

---

### Post by skeptikus on 2023-12-27
Many thanks for your patience! Encouraged by your insistence that it had to a Windows problem, I tried everything I could think of and what finally did it was switching the port from the one named after the printer's IP address to the one called USB001. That's a relief! I was beginning to think it'd never work. Thanks again!

---

### Post by MAFoElffen on 2023-12-27
You are very welcome. Enjoy!

---

