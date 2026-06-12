---
title: "Startup and system programs free for shutting down??"
date: 2008-08-24
forum: System76 Support
---

### Post by hardy_gnome on 2008-08-24
Hello
i've searched some term for startup programs, and similar therms but i haven't found anythins...
so i ask here...
can u tell me which programs (i mean startup programs and system) i have to keep runnin and which i can turn off.. because i want more memory to be free and faster working computer..

everday i use this:
amarok, emesene, firefox, vlc player, compiz....

i will send i a few minutes programs which r now running...

processes
> bonobo-activation server, dbus-daemon, fast-user-switch-applet, firefox, gconfd-2, gnome-keyring-daemon, gnome-panel, gnome-power-management, gnome screensaver, gnome settings daemon, gnome system monitor, gnome vfs daemon, gvfsd, gvfsd burn, gvfsd trash, gvfs fuse daemon, metacity, mixer applet 2, nautilus, nm applet, pulseaudio, python, seahorse agent, tracker applet, trackerd, trashapplet, update notifie, xsession manageer

startup programs available
> network manager, power management, pusle audio session management, tracker, tracker applet, update notifier 

and now the compiz won't work... i turn effects on but nothing... 
i click fusion-icon.. and all gets ****** up... --- solved with compiz --replace& command.. but some effects are slooooow.. not like at the begginig when i discovered them...

---

### Post by thomasaaron on 2008-08-25
It's generally best not to tinker too much with running processes. If they are running, there is most likely a good reason for it. It is better to disable start-up programs that you don't want. The ones I see that you might want to disable are: tracker and tracker applet.

You probably want to leave update manager on. If you turn it off, you will need to remember to manually check for updates.


As for compiz being slow, you didn't specify what you changed that made it slow.

---

