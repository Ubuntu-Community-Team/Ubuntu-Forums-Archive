---
title: "Here Is My Goal"
date: 2007-03-16
forum: Server Platforms
---

### Post by Noah0504 on 2007-03-16
Okay, I just recieved an older computer from my brother.  It's an old Compaq Presario with a 400MHz processor and 64MB or RAM.  It's not good for much, but I'd like to turn it into a server.

Once the computer is up and running it won't have a monitor, so I'll need to make sure I can use SSH to control the computer when I need to do something.  Also, I think I'd like to run a simple webserver so I can test websites and maybe host a few things for friends.  And, if it's possible, I'd like to be able to use it for storage.  My dad and I like to backup files (school work, finances, etc.).  He uses Windows and I use Ubuntu and Windows sometimes.  Will I be able to connect from Windows and move files to and from?  I think I know the answer (and I think it's yes), but I wanted to double check.

Can someone throw a little guidance towards me in accomplishing this?

---

### Post by spin2cool on 2007-03-16
You'll want to borrow a monitor for setting up the system intially.  Once it's up, install SSH (sudo apt-get install ssh).  That will give you command line access over a network.  If you'd like graphical remote access, look for one of the many VNC tutorials on this site.  VNC may be a bit sluggish on that system though.

The easiest way to share files depends on where you're accessing them from.  If you're on the same network, using a windows samba share is pretty simple, and accessible from both OSes.  You just mount it as a network drive.  There are tons of tutorials and questions related to this topic on the forums - browse around, try some different combinations of keywords, and after you do, ask if you need more specific help.

---

