---
title: "Setting up of Linux Server?"
date: 2010-08-12
forum: Server Platforms
---

### Post by alanmarsh on 2010-08-12
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=arial]I'm planning on changing the server in our office from Windows XP Server Ed. to Linux.
V hav 50 LAN nodes and a server node. 
My requirement is that the Linux server should support Windows XP platforms on the individual nodes
and the file and connectivity sharing be enabled between the peers.
How do i do this if to be done voluntarily by me?
In case i give it as a contract or something to some enterprise how much does it cost (INR)?[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by garfonzo on 2010-08-12
If all you are doing is using a server for file sharing between Windows computers, then Ubuntu will be fine. I have a Ubuntu server running in the garage which shares files to 4 computers in my house (3 Win XP, 1 Vista). The tricky part (and it really isn't that hard) is setting up Samba (the file sharing protocol) so that all node computers have proper access to their documents.

Note: the server edition of Ubuntu does not have a GUI like the Windows Server Edition does. You will be doing all the server work through a command line interface. Obviously, you can put a GUI on the server, but that isn't really necessary.

---

