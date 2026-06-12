---
title: "Accessing Windows application through VB?"
date: 2010-01-19
forum: Virtualisation
---

### Post by aquascrotum on 2010-01-19
I have a Ubuntu host running a VirtualBox (not OSE version) with Win XP as guest.

I need the WinXP guest to run an Outlook PST sharing application that is shared with other Windows computers over the network (Code2 Public Folders for information). The guest OS is intended to run the server part of the application, sharing the pst with client applications run on the other machines.

I have configured the guest OS with the Host network interface so has its own IP address on the network, and the virtual computer shows up fine on the windows machines in Workgroup Computers.

However, the application shares over port 5002 - when I start the client part of the application and ask it to connect to the computer name on the network or point it to the IP address, I get an error saying that the "The requested address is not valid in its context. (0x2741).  TCP socket failed to connect to "VBMCL003" using port 5002.

I can only assume this is an issue with sharing the network via VB.  Can anyone shed any light?

---

