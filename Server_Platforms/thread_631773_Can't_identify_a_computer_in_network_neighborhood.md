---
title: "Can't identify a computer in network neighborhood"
date: 2007-12-04
forum: Server Platforms
---

### Post by kuhsay on 2007-12-04
I am looking at smb://workgroup, and there is a computer in there identified as BRN_7DC5AC.  I don't know where it came from or what it is.  When I connect to it using a vista machine (in network neighborhood), I see a a printer called binary_p1 and if I hover over it, it says "NetBIOS port"

Can somebody please help me to identify it?  It might just be a virtual machine or something, but I'm concerned its somebody who is not supposed to be there.

---

### Post by ectospasm on 2007-12-04
You can use the smbclient tool to see what it's sharing, it may give you more information than a GUI tool:

smbclient -L <host>

If it's password protected that may not help...

---

### Post by kuhsay on 2007-12-04
I think I have identified it as a Brother HL-2070N network printer.  Why it is appearing as a windows network share is still a little confusing.

---

### Post by ectospasm on 2007-12-04
> **kuhsay said:**
> I think I have identified it as a Brother HL-2070N network printer.  Why it is appearing as a windows network share is still a little confusing.

It's fairly common nowadays for network printer manufacturers to turn on Windows print sharing by default.  I mean, you do want a network printer to show up on the network with as little hassle as possible, right?  I refer you to the Brother manual for figuring out how to turn that service off.

---

