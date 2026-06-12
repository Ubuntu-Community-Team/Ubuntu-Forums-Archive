---
title: "Ubuntu home file/print server"
date: 2007-02-01
forum: Server Platforms
---

### Post by Quiet Robert on 2007-02-01
I am stating to get things together to install a Ubuntu file/print server at home.  I am trying not to make this a how-to question, so here goes...

I have a laptop running Ubuntu, a Mac G4 running OSX 10.4, a Windows XP laptop, and soon to have a low-end Edubuntu system for my three-year-old.  I want to set up a server to store our music and such on as well as a printer.  I have most everything I need and am pretty sure how to do it, but my question is, is it possible to link all three OSs on a single server?  Also, I want to use a VNC program between the systems.  Is that possible?

Links would be helpful.  Software suggestions for VNC and such with links would help also.  The free-er the better.

If this is in the wrong place, please direct me to where this should be.  If anyone knows a good how-to to make sure I do not mess it up, that wold be great, too

---

### Post by Brazen on 2007-02-01
You use samba to share files with Windows, Mac, and linux computers.  There is good documentation of setting up a Samba file server in the ubuntu online documentation.

There are also VNC clients and servers for those three platforms as well.

---

### Post by Quiet Robert on 2007-02-01
Do I need the server addition if I am just using it for file and print sharing?  I do not see the need for my situation to have a LAMP server.

---

### Post by Iowan on 2007-02-01
> **Quiet Robert said:**
> Do I need the server addition if I am just using it for file and print sharing?  I do not see the need for my situation to have a LAMP server.
In my opinion, you don't need the extra complexity of setting up a LAMP server.  You could (should?) set up a machine as a common desktop, then add the Samba-server elements.

---

### Post by Quiet Robert on 2007-02-01
that was the plan.

---

