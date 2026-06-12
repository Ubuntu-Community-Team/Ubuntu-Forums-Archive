---
title: "Windows Driver Problem"
date: 2007-12-09
forum: Windows
---

### Post by Black Mage on 2007-12-09
Ok, this isn't the most user friendly forum but I don't no where else to turn, and  this is my first windows server install.

So I installed Windows Server 2003 on a Dimension Dell 3000 and  the ethernet controller driver wasn't there. I went to Dell's Website and downloaded the drivers and they installed but it still can't my ethernet controller to work. I downloaded all the drivers and installed all of them and under device manager, its still a question mark.

Does anyone know where I can get Windows Server 2003 ethernet driver for a Dell Dimension 3000?

---

### Post by Erdaron on 2007-12-09
You can try this website: [http://driversguide.com/](http://driversguide.com/)

It has all kinds of bizarre drivers, and it also has feedback from users who have successfully (or otherwise) have tried these drivers under specific systems and OSs.

You should look up the ethernet card (whether on Dell's website, or by opening up the case). You can try getting drivers from the card's manufacturer.

Make sure previous attempts at driver installations are completely removed before trying the next thing.

Are you sure the ethernet card actually works? Have you tried it in a different box?

---

### Post by salamba on 2007-12-09
As stated above, you need to find out what the network controller in that machine is.   Boot off an ubuntu live cd, start a terminal and type 'lspci'  - This will give you a list of hardware.  From that you should be able to figure out the network controller - be it realtek, intel, marvell or whatever.   Then go to the network controller makers website and get the driver.

---

### Post by Black Mage on 2007-12-09
> **Erdaron said:**
> You can try this website: [http://driversguide.com/](http://driversguide.com/)

It has all kinds of bizarre drivers, and it also has feedback from users who have successfully (or otherwise) have tried these drivers under specific systems and OSs.

You should look up the ethernet card (whether on Dell's website, or by opening up the case). You can try getting drivers from the card's manufacturer.

Make sure previous attempts at driver installations are completely removed before trying the next thing.

Are you sure the ethernet card actually works? Have you tried it in a different box?

Ahh yes, driversguide.com had what I needed. thnx.

---

