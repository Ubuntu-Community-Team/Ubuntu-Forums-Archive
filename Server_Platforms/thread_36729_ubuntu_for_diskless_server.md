---
title: "ubuntu for diskless server"
date: 2005-05-24
forum: Server Platforms
---

### Post by BatsotO on 2005-05-24
hi,

i'm running 2 linux server, one is redhat for internet gateway and ltsp client, and the other is diskless client using ubuntu for applicaton server.
the ubuntu server is using 1 gig RAM and serving 12 diskless client (prior to ubuntu, im using windows 2k advance server, and it was running "fine").
does anyone have any experience in this, coz i having some problems, one of these problem is whenever the client crash ( and it's seems to be happening to often ), it's take ages for them to login again.

i'm new to linux and ofcourse to ubuntu ( it's not me who set those ltsp things ), but i suspect that not all the aplication running on the client have not ben shut down properly ( whenever it crash the only thing can be done is press the power button ), as in windows i can kill the process using task manager, without administrator privilage ( using power user privilage that i cant find it in linux ).
 
is it posible, in ubuntu, to set one of the user ( name it operator ) to kill process running by other user withoutsetting it as root/administrator as in power user privilage in windows?

n.b : sometime, after the crash, it says that panel is already running, and it's need  need to exit or something like that, then the client running without any panel at all, or sometime there's nothing on the desktop.

---

### Post by dannysauer on 2005-05-25
Gnome does that to my xterminal machines all the time - applications will keep running, and lockfiles aren't cleaned up.  I generally have to go through and kill all of the processes that are owned by the unfortunate user, and then remove all of their files from /tmp.  That's been the most reliable way to clean it up, in my experience of seeing things like the panel running, nautilus not starting, etc.

To kill a process, you have to either be the user or root.  Remember that, from a root account, you can su to any other user.  Basically, you'd have to kill the processes from an environment running as root.  I've had particularly good luck with webmin in this regard - it has a process viewer that will allow you to kill all of the processes belonging to a specific user (among other things), and you can get to it from any web browser.

---

### Post by BatsotO on 2005-05-26
does kubuntu have the same problem?

---

