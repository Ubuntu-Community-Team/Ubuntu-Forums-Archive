---
title: "Multiple resumable remote sessions ala win2k server?"
date: 2008-07-04
forum: Server Platforms
---

### Post by Pro_D on 2008-07-04
Wondering if there is a way to do this with Ubuntu.

The Win2k server (which this Ubuntu server is replacing, quite nicely so far) was capable of having multiple remote sessions (I think it was limited to 3) all independent and if you did not log off they were persistent.  It also allowed you to have the local session (physically in front of the computer). Heck you could even log in to the same account all 3 times (well, 4), though that part is not necessary.

I came across a guide a while ago, lost the link, but that only gave a single remote session and the client had to specify the session (the console) it was connecting to among.  I did try that and couldn't get it to work, though I think that guide was for 6.06...  The system has since been scratch installed.

Mostly I am looking for some good places to look or some nice tidbits if someone has something like this setup.  My internet searches aren't helping much, I suspect I am asking the wrong question, so to speak.  I plan to use gnome so it's ubuntu-desktop on top of the server install.

---

### Post by windependence on 2008-07-04
Well I know you don't want to hear this but you can connect as many ssh sessions as you want. I know, I know, you want a GUI because you are a Windoze guy. OK you have several options. VNC can do multiple sessions, by just specifying the next session number, but the cleanest way would be to export an X session via ssh. You can just do ssh -X user@serverip and get an X session.

You really should learn the CLI though.

-Tim

---

### Post by Pro_D on 2008-07-05
I suspect a misunderstanding and a hint of condescension.  I am NOT seeking access to remote desktop session in order to /CLI but to make use of some graphical applications on the server computer as it's always on.

I will take another look at using an x session over ssh however my previous tinkerings on that have proven non-persistent (I close the client and the remote session and programs close), hence why I was looking at vnc instead.

Not that it should matter much but I am not half bad with CLI on either windows or linux though still learning the linux side of things since I have only fiddled with linux about 3 years now, only recently seriously pursuing it.

---

### Post by windependence on 2008-07-05
Sorry for the attitude, too many n00bs today I guess. :)

Yes, the problem with exporting a GUI session is that it is an interactive session. If you start applications from the CLI and append a & to the command used to start them, you can run them in the background. That's probably not what you had in mind but I'm not sure what else would work.

-Tim

---

