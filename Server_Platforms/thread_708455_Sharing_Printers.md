---
title: "Sharing Printers"
date: 2008-02-26
forum: Server Platforms
---

### Post by Stephen_at on 2008-02-26
I suspect this is actually a Windows/XP HP problem but..

I've got a HP Photosmart 7960. Works fine under XP with its annoying software that insists on taking control.

Works fine under CUPS too.

I've shared the printer out from the server using SAMBA.

I can see it but when I connect to it I get the annoying "No suitable driver..." message and an option to browse for it. XP doesn't seem to know that its got this printer installed at all so has no drivers for it.

Any suggestions?

Thanks

---

### Post by sp0nge on 2008-02-26
I presume the hardware is all on your LAN. 

That being said. most printers prefer windows. Get the printer working with the windows machine then you can drop the file in a shared drive, access the windows machine (via TSClient through the linux box or directly), access the file from the windows machine and print. 

I'm sure there is some way to get the printer working directly with Ubuntu. At worst cast there is no driver created yet, depending on the age of the printer. It will come in time, I'm sure, but this will solve the problem in the immediacy. 

Hope this helps.

---

