---
title: "Headless Server - Launch Console KDE from SSH Session?"
date: 2008-03-11
forum: Server Platforms
---

### Post by sanitycheck on 2008-03-11
I have a Gutsy i386 server with kubuntu-desktop installed.  I disabled KDM from running automatically at boot time, so I have to log in and "startx" to get it running manually.  I prefer this so I can run X only when I really need it, and shut it off when I don't.  I have the KDE Remote Desktop (VNC) server configured to run when KDE is running.

I'd like to move the server to a location with no keyboard, mouse, or monitor (headless server).  Is it possible to launch KDE (startx) in the console session from an SSH session?  Simply running startx from the SSH session does not work, not to my surprise. 

If I could launch X (KDE) from SSH, I could then shut X+VNC down from a VNC session by simply logging out of the session.  This would allow me to turn X+VNC on or off at will, just as I do at the console now.

I am aware that it's possible to configure a different VNC server package to allow me to connect to the X login screen (KDE's Remote Desktop VNC server I prefer does not run unless user is logged in and KDE is running).  Those alternative VNC server methods require KDE and VNC run all the time, which I'm trying to avoid.

Thanks in advance for any help.

---

### Post by netlogic on 2008-03-11
**[COLOR="Red"]try conspy[/COLOR]**

man conspy (1) - virtual console spy tool
NAME

conspy - virtual console spy tool
SYNOPSIS

conspy [ options ] [ console ]
DESCRIPTION

Conspy allows the user to take control of a Linux virtual console. The user can see what is displayed on the console and their keystrokes are sent to it.

To exit from conspy press the escape key three times in quick succession.

COMMAND LINE

-V, --version
    Print the program's version and exit. 
-v, --viewonly
    Don't send keystrokes to the virtual console. 
console
    If supplied, console must be a number in the range 1 .. 63, corresponding to the virtual console device /dev/tty1 .. /dev/tty63. If not supplied the currently active virtual console is opened and tracked. 

LIMITATIONS

Conspy will not pass keystrokes to a virtual console whose keyboard is configured to send scan codes. X configures its keyboard like this. If the terminal does not have at least 64 colours no colour will be displayed. Conspy ignores the mouse. Conspy may display some non-ASCII characters incorrectly. Conspy does not handle displays larger than 16000 characters (eg 200 rows x 80 columns).

Conspy depends on terminfo and curses working correctly for your terminal, and sometimes they don't. Konsole is/was one example of where they don't. Typing control-L will redraw the screen, which usually fixes the mess created. It also sends a control-L to the virtual console, of course.
FILES

/dev/ttyX, /dev/vc/X
    The characters typed are sent to this device. The latter is for devfs. It is only used if the former does not exist. 
/dev/vcsaX, /dev/vcc/aX
    The display of the virtual console is read from here. The latter is for devfs. It is only used if the former does not exist. 

AUTHOR

Russell Stuart, <russell-conspy@stuart.id.au>.

---

### Post by sanitycheck on 2008-03-11
Perfect, thanks!  I'm sure I'll think of some other uses for Conspy in addition to this one.

Because I want to Conspy the console of my server, I installed it there.  I SSH into the server from my workstation as usual and type:

```
sudo conspy 1
```

In my same SSH window I get switched to the display of the console (the text looks a little different).  I log in and run startx, and quickly press ESC three times to escape from the Conspy session.

Now X/KDE is running, and I can disconnect from my SSH session and connect using VNC.

---

### Post by HermanAB on 2008-03-11
VNC is insecure so it is best avoided and running VNC over SSH is redundant, while running the whole huge desktop is a waste of time, since you already have one on your local machine.  

Soooo, if you are addicted to pointy-clicky-thingies, just run the taskbar remotely over SSH like this:
$ ssh user@server kicker

or
$ ssh user@server gnome-panel

Cheers,

Herman

---

### Post by sanitycheck on 2008-03-12
HermanAB: Not sure what you mean.  I get this error:

ERROR: KUniqueApplication: Can't determine DISPLAY. Aborting.

---

### Post by netlogic on 2008-03-12
He is doing this over home network. I think he is safe. Yea, don't ever use VNC over internet. Rehashing the key authentication takes few seconds with the right app. I have seen apps that put all the picture frames to a movie file. Forwarding the x application to the desktop is only ideal if he plans to NOT resume the session again. Still no graphical **screen **application. It would be nice. Vnc can be ideal if he is using a graphical downloader or p2p on the server.  It is very similar to how Windows users are using their RDP.

---

### Post by netlogic on 2008-03-12
> **sanitycheck said:**
> HermanAB: Not sure what you mean.  I get this error:

ERROR: KUniqueApplication: Can't determine DISPLAY. Aborting.

You have to type **ssh -X machine.domain.com nameoftheapp**

also, on your /etc/ssh/sshd_config
make sure you have 
X11Forwarding yes

---

### Post by sanitycheck on 2008-03-13
Thanks for the X forwarding tip.  

It is true that in many cases I would need to resume a session, which is a big reason I wanted to use VNC.  I knew about X forwarding but I'd never bothered to try it up to now.  

For some reason my VNC performance is poor on this now-headless server, so the X forwarding of specific apps will allow me to get around that issue until I can properly troubleshoot it.  X forwarding also eliminates a couple of steps compared to having to ssh + conspy + startx when I don't have an X+VNC session already running to resume.

Forwarding kicker did some strange things on my screen, but running Dolphin as a test app worked as expected.

---

### Post by netlogic on 2008-03-13
I don't run graphical apps on the server. I think VINO (VNC package by Gnome) doesn't have a jpg compression. You should research about an app called, Tightvnc. It has more image compression and caching support. 

From what I know, you can't run apps that you are already running on your local xserver, because drawing doesn't take place on the server. It is happening local.  Only the application process happens on the server.

---

### Post by yangeryanger on 2008-07-15
I remember a x11 server part that emulated the desktop and you could access it via vnc or ssh - i don't remember what it was called or if it was even worked on.. but .. yeah, when you booted the server up, the x11-desktop-emulation like thing would log in and from there you could remotely access it and work in that "emulated" desktop...

---

