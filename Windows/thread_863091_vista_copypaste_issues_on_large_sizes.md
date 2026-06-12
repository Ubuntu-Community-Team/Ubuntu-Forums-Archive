---
title: "vista copy/paste issues on large sizes"
date: 2008-07-18
forum: Windows
---

### Post by insane_alien on 2008-07-18
short and sweet, vista won't let me copy/paste anything over ~32GB

if i try it just does nothing. particularly annoying as i am trying to copy/paste 132GB of files around 750MB a pop. 

anyone know how to fix this?

---

### Post by jnw222 on 2008-07-18
use an archiver like winrar or 7zip to archive it into managable chunks

---

### Post by insane_alien on 2008-07-18
but its already a bunch of smaller files in folders. i can transfer up to 32GB of them at a time but not more. seems a bit inconveinient.

i mean, i have terabytes of information on my fileserver, if i wanted to use vista to transfer all that to a new one(fat chance, i'd use linux for that, and i'd only be transferring it if the server was close to death) it would be very very annoying.

its not much over 100GB and its not as if vista isn't a modern OS why can't it deal with this?

---

### Post by SEMW on 2008-07-18
IIRC there were some issues with file copying in Vista pre-SP1.  If you haven't installed SP1 yet, that may be worth a try.

If that doesn't help; assuming it's a Windows Explorer bug, you could try just dropping down to the command line (Win+r, "cmd") and using xcopy (which uses a similar syntax to cp).  Certainly, when Nautilus is playing up I just open a terminal and use cp which, being simpler, is far less buggy; I don't see why the same shouldn't apply to Windows.

---

### Post by insane_alien on 2008-07-18
i do have SP1, it came installed with the laptop.

i've never been familiar with the windows command line and i must admit i haven't figured out how to get to it in windows, where is it? i'm too used to ctrl+alt+F1 or applications>accesories>terminal. bit late now though as i have everything copied.

---

### Post by fiddledd on 2008-07-18
> **insane_alien said:**
> i do have SP1, it came installed with the laptop.

i've never been familiar with the windows command line and i must admit i haven't figured out how to get to it in windows, where is it? i'm too used to ctrl+alt+F1 or applications>accesories>terminal. bit late now though as i have everything copied.

Start->Programs->Accessories->Command Prompt

And if you Right Click it you can Run as Administrator to change File Ownership etc

---

### Post by MaxIBoy on 2008-07-18
If all else fails, boot up from a Linux liveCD.

---

