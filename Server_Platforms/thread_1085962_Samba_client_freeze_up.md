---
title: "Samba client freeze up?"
date: 2009-03-03
forum: Server Platforms
---

### Post by kooldino on 2009-03-03
I have an odd issue.  I've verified it on multiple Windows XP machines connecting to my recently setup samba server.  

Essentially, if I load up my connection to the server (from a single machine, mind you) and open a .c file off of the server while doing it, the program I'm viewing the .c file in as well as my explorer (and Windows search windows) will lock up and stop responding.

This is on a fresh install of 8.04LTS with the latest stable build of samba.  

The odd thing is that this machine is replacing an old redhat 9 server we had with an old version of samba which doesn't cause this issue...

---

### Post by kooldino on 2009-03-04
Ok, so one new clue:

If the machine is mapped as a network drive under windows, when it finally does fail it will say that it's "reconnecting" to the drive when I run the "net use" command in Windows command prompt.

Apparently, this is timing out somehow...

---

### Post by kooldino on 2009-03-05
According to wireshark, when it does go haywire, we're getting bad checksum errors on the packets.

---

### Post by kooldino on 2009-03-06
Can anyone help me?

---

### Post by kooldino on 2009-03-10
I think the CRC error is a red herring...that happens on any machine we use during any type of file transfer (such as ftp).

---

