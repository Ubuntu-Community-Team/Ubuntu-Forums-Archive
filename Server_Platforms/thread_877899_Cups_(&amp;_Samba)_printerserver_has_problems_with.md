---
title: "Cups (&amp; Samba) printerserver has problems with windows clients"
date: 2008-08-02
forum: Server Platforms
---

### Post by GSMX on 2008-08-02
Hey,

I have a 8.04 printerserver with cups and a good configured canon ip4300 printer connected. this printer is shared thru samba for windows clients

Now, with my ubuntudesktop-client, i can use this printer, but with the 3 windows clients (all xp), windows gives the error that it "can't use the shared driver" and that it could only use an already-installed driver on the particular windows pc, now i only have the opportunity to install this driver from the canon-cd for 1 pc and it's working alright for that pc

But now there are two windows computers who can't use the printer, because there is no driver... is there a method for the windows clients to use the driver cups is using?

---

### Post by redraiderbum on 2008-08-02
Not that I know of.  I have always had to install the driver for the printer on the windows machine even if the printer is shared on a network.

---

### Post by GSMX on 2008-08-02
but when you share a printer on a windows machine and connect to that printer from another pc, the second windowspc can use the driver of the first machine...

---

### Post by redraiderbum on 2008-08-02
Yeah that is because of the platform compatibility.  I think all you need to do is google the model of the printer with the word driver added and download and install the driver on each windows computer.

---

### Post by GSMX on 2008-08-02
I do have the correct canon driver, but the installation of that driver requires the printer to be connected to that particular computer

---

### Post by redraiderbum on 2008-08-02
That's weird.  You should just be able to install the driver by selecting it on the network or possibly just install the driver without the printer present.  That does suck; there must be some way to avoid having the printer plugged in.

---

### Post by GSMX on 2008-08-02
suggestions?

---

### Post by cariboo on 2008-08-03
Samba can do what you are looking for. Download Samba 3 by Example [here]("http://www.samba.org/samba/docs/Samba3-ByExample.pdf"),
Then go to page 215 and follow the instructions. This is a tutorial for a large network, but the instructions are the same. 

Jim

---

### Post by GSMX on 2008-08-03
It looks like it's an usefull example, i will try and error with this document.

Thanks

---

