---
title: "[Ubuntu 16.04 Server] Cant switch vty using hwe-edge kernel + xorg-hwe"
date: 2017-04-26
forum: Server Platforms
---

### Post by ju2wheels on 2017-04-26
I have a 16.04 server that I boot into multi-user target by default then after I login, I manually isolate the graphical target, exit the vty 1 and login to Gnome on vty 7 via GDM.

This process works fine for me using hwe kernel and xorg-hwe. However, I recently decided to give the hwe-edge kernel a go and I hit problems. Basically everything works fine until I try to switch from vty 7 after isolating graphical to bring up GDM back to vty 1 so I can exit the CLI. When I try to switch from vty 7 to vty 1, the mouse cursor/kb disappears but the graphics dont switch from vty 7 back to vty1 console.. it just stays displaying vty 7 GDM login. Then when I switch back from vty 1 to vty 7, its goes back to GDM login and the mouse cursor/kb return as normal (it doesnt logout out the session if I had one open though, but it will lock any open session's screen forcing you to put in the password).

Has anyone had any similar issue?

Im not sure if this is a systemd issue, kernel issue, xorg issue, or GDM.

Any thoughts?

---

### Post by cariboo on 2017-04-27
Moved to Server Platforms.

---

