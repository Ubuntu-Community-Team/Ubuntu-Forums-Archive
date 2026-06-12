---
title: "LTSP SCREEN_*=startx"
date: 2007-11-04
forum: Virtualisation
---

### Post by bazz on 2007-11-04
Anyone know how I can get past the gray screen if I place SCREEN_07=startx in the lts.conf?
Is there a forum for LTSP?

---

### Post by bazz on 2007-11-05
Found the answer....
I posted this in a different thread, but I thought this would be easer to find here.

[http://www.upfrontsystems.co.za/Memb...ly-an-x-cursor](http://www.upfrontsystems.co.za/Memb...ly-an-x-cursor)

Thin clients have grey screen showing only an X cursor
Symptom

Thin clients display grey screen with an X for a mouse pointer instead of login screen.

Possible causes:

1.

XDMCP is disabled
2.

GDM is not running
3.

Thin clients are connecting to wrong server

Solutions

1.

Check if XDMCP is enabled. To do this, go to the server (you may have to connect a display, keyboard and mouse), and click on the main menu button on the bottom of the screen. Go to the System Settings menu, and choose "Login" to modify your login settings. You will have to enter the root password. Then, click on the "XDMCP" tab, and ensure that the box that says "enabled" is selected.
2.

Check if GDM is running. You can gain access to the server by using a secure shell from one of the thin clients (refer to the section called “Using a secure shell from one of the thin clients”). To check if GDM is running (once logged in), type:

#ps -e | grep " .dm"

If GDM is running, you will see an output similar to this:

1973 ? 00:00:00 gdm
3226 ? 00:00:00 gdm

If GDM is not running, or if you'd like to restart GDM, you can type:

#gdm-safe-restart

3.

The server to be used for LTS (Linux Terminal Services) is specified in the lts.conf file using the "server" directive. This value is normally 192.168.0.254, but may be different depending on your specific setup:

#from lts.conf:
server = 192.168.0.254

If you have more than one tuXlab server, or if you have more than one computer network in your school, then this address might have to be slightly different.

So if I edit my lts.conf with
SERVER=ip of ltsp server
SCREEN_07=startx
SCREEN_08=startx
SCREEN_09=startx

I can have multiple sessions. How ever I can not get my main account to log on, only other users. Also If I leave the session for a little while it will drop the session, so the GUI no longer works.

---

