---
title: "Can you remote desktop from XP -&gt; Ubuntu in Hardy?"
date: 2008-10-11
forum: Server Platforms
---

### Post by effec on 2008-10-11
I'm having some troubles connect from my XP machine to ubuntu. 


I followed the directions outlined here:

[https://help.ubuntu.com/community/VNC?highlight=%28remote%29%7C%28desktop%29](https://help.ubuntu.com/community/VNC?highlight=%28remote%29%7C%28desktop%29)

but there's one sentence that worries me. "Unfortunately, a bug in the version that comes with Hardy makes it incompatible with most networks and VNC clients." 

Has anyone been able to get control their ubuntu machine from an XP client.

-Im on the same network, and same workgroup, so i dont need ssh
- Do i need to setup a VNC sever or start any services from the Ubuntu machine? I only used the remote desktop options in the GUI..

Any help is appreicated. Thanks.


Edit 1: I tried another method outlined at :[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Remote_Desktop](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Remote_Desktop)

But when i try to get everything going i get a blank screen with an X , like it cant connect to my ubuntu machine.

---

### Post by cariboo on 2008-10-11
Install one of the vnc clients on Windows XP and a server on Ubuntu and you shouldn't have any problems. Tightvnc server is in the repositories and and Tightvnc is available for free for Windows.

Jim

---

### Post by lykwydchykyn on 2008-10-12
Usually when that happens, it means that the server's X11 or else gdm is not allowing you to connect.  Check your firewall rules and make sure port 177  is open.  I think you might need port 6000 also.    Also, double check you did this step:

> 
On your Linux box (Gnome) go to System->Administration->Login Window->Security. Make sure the "Deny TCP connections to Xserver" is unselected.


---

