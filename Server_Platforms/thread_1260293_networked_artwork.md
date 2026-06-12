---
title: "networked artwork"
date: 2009-09-07
forum: Server Platforms
---

### Post by Clive McCarthy on 2009-09-07
I have an OpenGL application that I want to run remotely on an Ubuntu machine. The remote machine has no keyboard & no mouse -- just a screen and a power button. The application should run immediately at start-up (no login -- because you can't).

I want to be able to remotely halt the program (I currently do this with a simple 'semaphore' file that, if present, tells the application to exit) and then to be able to remotely update/overwrite the executable and then delete the semaphore halt file. A power-button restart of the machine lanches the updated application (it's an art work).

OpenGL uses x-windows and my current Ubuntu machines are configured with Gnome which sits on top of x-windows (sorry if this is tedious, I'm new to Linux).

I'm guessing I should be able to find a boot script somewhere that sets up the pre-Gnome tasks such as firing up x-windows. I should then be able to insert a call to my program?

The machine will sit on my development network but ultimately is disconnected from any network so security isn't an issue. To do what I want I guess I'll need complete access to the machine...

Suggestions and advice please?
Clive McCarthy

---

### Post by denver on 2009-09-07
Does this OpenGL app need to open a window? Is it a system process that runs in the background?

If it needs to paint a window on a screen, then you would need a X session (login to your desktop environment or window manager) or at least need to export your DISPLAY. The X server is in fact a server. The windows you see painted inside a X server are in fact clients.

If your application is a system daemon that you can connect to, then you don't need a X session.

As i see it you have a few options:

1. setup a VNC server that starts an X session remotely and fire up your OpenGL application. This can also be scripted and run at startup. Look into tightvncserver (or something similar).

2. ```
export DISPLAY=<ip here>:0
```
This will export youre display to the screen of the IP address you speciffied in the DISPLAY variable. Any command you execute that involves drawing a window will automatically open up a client on the remote machine and display it there.

3. If its a system daemon that does not require a GUI, then you are better off running a SSH session and controlling everithing that way.

The first (providing it requires a GUI) and the 3-rd options (providing it does NOT require a GUI) would be best.

The second option requires a second machine to be running and have the same app installed. Also, its more difficult to set up as you will need to modify your X acces control lists to permit accessing the server remotely.

Best of luck to you!

---

### Post by Clive McCarthy on 2009-09-07
The target machine will ultimately become detached from my network and become an isolated system. The computer is simply embedded, runs just one application, has just a power button for control.

The application, when running has no GUI (meaning literally Graphical User Interface) -- but it is Graphical --- so it's a G -- not a GUI. This might be a useless distinction? OpenGL talks straight to the x-system I think? I have so far been using XP with no remote login facility and I simply put a batch file in the start up directory which would launch my application which is stored in a shared directory -- this allows it to be updated remotely. I'm imagining a similar thing with Ubuntu.

If I disable Gnome (or maybe I don't need to?), I guess I should be able to login to the remote machine and make the necessary changes to update my application. Put a call to my application in the 'Sessions' list and it will work?

---

### Post by denver on 2009-09-07
As far as i can tell it is a system daemon that does not require gnome to be started (or X for that matter). If it is a system daemon you can just start it up when booting and update it via SSH if need be.

If you are more confortable working in a graphical user interface, just install a VNC server and you will be able to login remotely into your gnome desktop and do all your work as if you were phisically there. 

Tightvncserver has a plugin that will allow you to view your desktop remotely using any Java enabled browser.

In ubuntu you have multiple choices of remotely accessig your PC. The 2 most common i have already mentioned (VNC and SSH).

If the machine itself will have no network connection, then i am fresh out of ideeas :). If it will then i recommend tightvncserver. It has its own startup file in which you can execute whatever you want.

Search the forums for some tips on how to set up a VNC server. Seeing as you have not had much experience with the GNU/Linux CLI, this might give you the least headaches.

Best of luck!

---

### Post by koenn on 2009-09-07
do it the way you did it in XP :

- configure gnome to autologin
- there's a folder somewhere that functions as an 'autostart' for gnome, just put your app there. 

now, see if i can find that folder again ...


EDIT:
I was thinking /etc/gdm/PostLogin/ but it's maybe  not what you want (runs as root)

But this might do : [http://ubuntuforums.org/archive/index.php/t-175357.html](http://ubuntuforums.org/archive/index.php/t-175357.html)



As for maintenance of program, there's plenty of ways to replace it (scp, ...) or edit it inplace (ssh, ...)

---

