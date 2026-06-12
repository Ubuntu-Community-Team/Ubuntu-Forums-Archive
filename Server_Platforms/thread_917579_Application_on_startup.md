---
title: "Application on startup"
date: 2008-09-12
forum: Server Platforms
---

### Post by Doomsword on 2008-09-12
Hi, I need to launch an application (game "Call Of Duty 4" in server listening mode) on my ubuntu server machine at startup. I access to my box via SSH with putty from a win box. 
I need that the task will stay active if I logoff from Linux... so I wrote a bash script to launch the task with "screen" task. Everything works fine... when the COD4 (Call of duty 4) is launched it stay in "Console mode" waiting for commands (ex. : mp_rotate change the current map, mp_restart restart the current map and so on...). What can I do to:

1) Start the task at startup with "Screen" and automatically detatch the process (without manually doing CTRL+A + D)
2) Reattach the task and launching QUIT command on waiting COD4 console when the system is shutting down or restarting

Is that possible? Any workaround or any other methods are well accepted! Thank you so much in advance!

Fabio

---

### Post by windependence on 2008-09-12
OK so what you are saying is if you just launch this at startup like you would launch a normal process this won't work for you because then you cannot control that process from ssh? I guess I'm a bit confused. 

Normally if you want to launch a process or application at boot, you would just put it in the startup scripts and it would launch and run in the background at boot and shutdown when you turn off the machine. What am I missing here?

-Tim

---

### Post by azadpanchi on 2008-09-26
> **windependence said:**
> OK so what you are saying is if you just launch this at startup like you would launch a normal process this won't work for you because then you cannot control that process from ssh? I guess I'm a bit confused. 

Normally if you want to launch a process or application at boot, you would just put it in the startup scripts and it would launch and run in the background at boot and shutdown when you turn off the machine. What am I missing here?

-Tim
Yeah I agree, just add it to /etc/rc.local

---

