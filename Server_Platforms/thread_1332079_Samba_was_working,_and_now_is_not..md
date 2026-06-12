---
title: "Samba was working, and now is not."
date: 2009-11-19
forum: Server Platforms
---

### Post by Roclemir on 2009-11-19
Don't know what happened. I had a complete fresh install earlier this week of 9.10 Ubuntu for amd64. All was working perfectly. Got Samba working beautifully. Even my temporamental vista box could see it. 

Then one day it stopped.

I've run sudo testparm
no errors

Checked the smb.conf files, I can't see anything wrong here.
I had at one point restarted the box.
I didn't notice it till after the restart and after the installation of an sftp server.
Can anyone help?

---

### Post by SOME1 on 2009-11-20
I have the same problem since the last upgrade of samba (via upgrade manager) on my laptop. I tried to remove samba (with purge) and reinstall it but it still not working. please help. thanks.

EDIT: I think I found the solution [here]("http://ubuntuforums.org/showthread.php?t=1169149").

---

### Post by Roclemir on 2009-11-28
Tried that setup. Crashed on winbind install. I had to reboot. After reboot, crash icon was up to, so I hit report, that was yesterday, lemme put it this way, the window that pops up saying "Collecting problem information" is still up 24 hours later, so I'm guessing it's crashed too.

What's going on.

---

