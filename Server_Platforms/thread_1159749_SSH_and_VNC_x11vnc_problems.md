---
title: "SSH and VNC x11vnc problems"
date: 2009-05-15
forum: Server Platforms
---

### Post by davidmigl on 2009-05-15
Hi,

I am trying to set up VNC over ssh. I am using x11vnc and I am following the tutorial on [this page](https://help.ubuntu.com/community/VNC#x11vnc-before-login).

Satellos is the name of the remote computer.

However, when I launch the command, I see x11vnc giving all its initialization and documentation, but nothing happens after that. Attached are screenshots of the command I typed in and how far the program gets.

Forwarding individual x11 windows over ssh is no problem. However, I do have a problem with Nautilus. Say I want to copy files via a GUI from my computer to the server. So I open up a nautilus window on the server via ssh and open up a local nautilus window. I select the files and drag 'n drop. I get the error "there was an error getting information about [filename]" More details: Error stating file [filename]: No such file or directory"

I believe whats going on here is that the server is looking for these files on itself, while they are actually on my computer that I'm sshing from. So how do I get this to work?

I remotely remember setting up a VNC password sometime. It's the same one as the username password.

Thanks for your help!!
David

---

### Post by davidmigl on 2009-05-15
So for the Nautilus problem, I found that I had to connect to the server by going to Places -> Connect to Server, selecting ssh as connection type and entering my credentials. So that problem is solved.

However I still can't connect via VNC from the command line (I would like NOT to use remote desktop viewer bc I will be remotely administering this headless machine and nobody will be logged on).

I tried using vncviewer instead but it tells me "unable to connect to host: Connection refused"

---

### Post by davidmigl on 2009-05-15
Well the solution to the vncviewer problem was a rather simple one. I had overlooked that I had not enabled remote desktop sharing on the remote machine. I had to go to System -> Preferences -> Remote desktop and check "allow other users to view/control your desktop.

However, this won't allow me to view the remote desktop when no one is logged in. I suppose I will have to keep searching for a solution....

EDIT: Well I got around to setting up a vnc server but whenever I log on it gives me the dreaded grey checkerboard with x! I've tried at least three different xstartup scripts. This is my current one (it doesn't work). Can anybody tell me what's going wrong?

```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 800x600+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &

```

---

### Post by krunge on 2009-05-15
> **davidmigl said:**
> 
However, when I launch the command, I see x11vnc giving all its initialization and documentation, but nothing happens after that. Attached are screenshots of the command I typed in and how far the program gets.


Looking at your screenshots, everything looks fine. x11vnc (a server) is waiting for a vnc viewer client to connect.  Did you try connecting with a VNC viewer at this point?

---

### Post by krunge on 2009-05-15
> **davidmigl said:**
> Well the solution to the vncviewer problem was a rather simple one. I had overlooked that I had not enabled remote desktop sharing on the remote machine. I had to go to System -> Preferences -> Remote desktop and check "allow other users to view/control your desktop.


Note that this enables the "vino" vnc server, not x11vnc.  There is no need to run x11vnc when you do the above gui setting.

---

### Post by 3L33T on 2009-05-16
> **davidmigl said:**
> 
EDIT: Well I got around to setting up a vnc server but whenever I log on it gives me the dreaded grey checkerboard with x! I've tried at least three different xstartup scripts. This is my current one (it doesn't work). Can anybody tell me what's going wrong?


Do you have a shell prompt in the checkerboard X screen?  If so, try this command:

```


cd /etc/X11/xinit/
. xinitrc &


```

That should start the GNOME GUI desktop you're using (or KDE if you're using KDE).

---

### Post by windependence on 2009-05-16
FreeNX is probably a better solution.

If the server is headless, why use anything but SSH? That's what I do with all my servers.

-Tim

---

### Post by davidmigl on 2009-05-18
The solution for the VNC problem I was having was to put this line into my x11 startup file:
```
unset SESSION_MANAGER
```
Apparently that cleared out whatever previous session manager that was defined and allowed gnome to take control.

I will look into FreeNX.

---

