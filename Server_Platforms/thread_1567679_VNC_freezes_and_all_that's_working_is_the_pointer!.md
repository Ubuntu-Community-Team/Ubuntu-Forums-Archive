---
title: "VNC freezes and all that's working is the pointer!"
date: 2010-09-04
forum: Server Platforms
---

### Post by Pontus Ohman on 2010-09-04
Hello folks!

I'm trying two diffrent solutions and both do the same thing, when I log in to my Ubuntu Server 10.04.1 LTS via VNC (Remote Desktop Viewer and Terminal Server Client) the both freeze when the desktop shows up and all thats working is the pointer...

Got a screen pluged in to the server just to be safe that I don't do anything bad because I can't see what's happening when it freezes!

Does anyone have any solution to this? Is it a bug that I must reg or not?

Earlier this week I had 2008 R2 server on the same machine and was using Terminal Server Client via RDPv5 and all went smooth, but I missed Ubuntu Server so I went back to it ;)

Cheers
Pontus

---

### Post by prshah on 2010-09-04
> **Pontus Ohman said:**
> I'm trying two diffrent solutions and both do the same thing, when I log in to my Ubuntu Server 10.04.1 LTS via VNC (Remote Desktop Viewer and Terminal Server Client) the both freeze when the desktop shows up and all thats working is the pointer...

Are you running Compiz? If you are, then see [[SOLVED] Remote desktop]("http://ubuntuforums.org/showthread.php?t=1475570&highlight=vnc") for a possible solution.

---

### Post by Pontus Ohman on 2010-09-05
> **prshah said:**
> Are you running Compiz? If you are, then see [[SOLVED] Remote desktop]("http://ubuntuforums.org/showthread.php?t=1475570&highlight=vnc") for a possible solution.

Got the answer last night thru IRC! And I needed to set my visual effects to None on the server...

Therefore someone can set this thread to SOLVED because I can't find it :)

---

### Post by rengifoo on 2011-01-30
Thanks a lot. It worked for me..

> **Pontus Ohman said:**
> Got the answer last night thru IRC! And I needed to set my visual effects to None on the server...

Therefore someone can set this thread to SOLVED because I can't find it :)

---

