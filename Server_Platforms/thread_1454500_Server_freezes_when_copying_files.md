---
title: "Server freezes when copying files"
date: 2010-04-14
forum: Server Platforms
---

### Post by paulsp on 2010-04-14
Hi there,

I recently installed a home server with Ubuntu 9.10 (regular edition, not server edition, with Apache/SSH installed). All works fine except when I save a file to, or copy a file from, the server, everything freezes. Details:

**When it happens: **
- Whenever I copy a file to or from the server using Nautilus (small files have more chance of not causing any trouble, but a 1MB+ file always causes trouble). 
- Sometimes when I save a file that I opened directly off the server in an application (ej. OpenOffice).

**What happens:**
- The process itself freezes. So the file that is being copied just sits there for a looooong time (1-15 minutes) without any progress, and then all of a sudden it keeps going again.
- The server becomes unresponsive. When I try to connect through SSH it times out, and I can not open any webpage that is installed on the server. No interaction with the server is possible whatsoever. Not from the computer that is trying to copy the file, or from another computer connected to the server. 

**What makes it weird:**
- When I look directly at the server nothing appears to be wrong. There is not a single process that takes up all CPU (as I feared), and I can use the regular interface without a problem (that is, connecting a monitor and keyboard to the server and interacting directly with it).

Any ideas what this can be? Or how can I figure out what is causing this?

Thanks,
Paul

---

### Post by kenada on 2010-04-14
Sorry it wasn't clear are you transferring locally or via network?

---

### Post by paulsp on 2010-04-14
The server is installed on a local network... the problems happen when I transfer from within that network to the server PC (generally I am using Nautilus and have the server mounted using SFTP). 

NOTE: the problems are much more likely to occur when simultaneous access takes place. So I can copy one file okay, but the moment I try to load a directory, copy another file, or have some other form of interaction with the server, it all freezes...

---

### Post by volkswagner on 2010-04-14
How much RAM do you have?

---

### Post by kenada on 2010-04-14
I remember I had this problem too but with samba, though I was running the server version.
Once I did a reinstall to 64bit from 32bit seamed to sort it out.

I remember there was a bug report
[https://bugs.launchpad.net/ubuntu/+bug/104256](https://bugs.launchpad.net/ubuntu/+bug/104256)

Though they claimed to have fixed it.

---

### Post by paulsp on 2010-04-15
Thanks for the replies. 
The machine has 1GB RAM, should be enough, right? 
The samba issue appears to be different as it involves very large files whereas I have problems even with small files (1MB) when I interact at the same time with the server. Also, I copy directly from Nautilus mounting the server using SFTP, without samba being installed.

---

### Post by paulsp on 2010-04-17
Found a possible solution here:
[http://www.fit-pc2.com/forum/viewtopic.php?f=43&t=1408&hilit=bios+gv3](http://www.fit-pc2.com/forum/viewtopic.php?f=43&t=1408&hilit=bios+gv3)

Some BIOS setting that oddly affects this. Changed the setting and so far, so good. So I hope this is fixed no!

---

