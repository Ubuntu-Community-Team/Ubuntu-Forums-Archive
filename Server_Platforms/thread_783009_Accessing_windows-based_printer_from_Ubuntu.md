---
title: "Accessing windows-based printer from Ubuntu"
date: 2008-05-05
forum: Server Platforms
---

### Post by explainer on 2008-05-05
I have Ubuntu in 32-bit and 64-bit versions in use in my local network.  I also have a Windows desktop with an HP OfficeJet G85 attached to it.  The OJ does printing, faxing, copying and scanning.  What I wish to add is to make it the default printer for all of the Linux images.  I have Samba installed across the network for file sharing, but I would like some recommendations as to the best way to leverage the Win32 printer.  What approach should I take, Samba or CUPS? Or some other approach?

---

### Post by azadpanchi on 2008-07-25
I have used samba without issue, I recommend it.

---

### Post by cariboo on 2008-07-25
You don't need samba to connect to a printer on a computer running XP. Go to System-->Administration-->Printing. Click Add New Printer, In the Select Connection Pane select Windows printer via smb (I running the alpha 3 version of Intrepid Ibex on my desktop, so things aren't exacty the same) click the Browse button, if you windows printer is shared properly, it should show up in the browse window select the printer and click forward. Next select your printer manufacturer from the list, click forward, select the printer model, leave the default dirver selection as is and click forward. Enter a Name, description and location and your ready to go. You have to make sure you have your windows printer shared for this to work.

Jim

---

