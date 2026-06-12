---
title: "Grey screen with VNC"
date: 2020-05-09
forum: Server Platforms
---

### Post by burkina76 on 2020-05-09
Hi all,

I had my VNC connection working well between my office's Ubuntu and my  home Ubuntu (both 18.04). The connection basically works with vnc4server  and vncviewer (or Remmina, but the result is the same).
Some time ago, there was a blackout in my office, and my system was down until today, when one colleague of mine restarted it.

However, the VNC connection is now not properly working. I get a gray  screen with a mouse pointer (which I can move), but no other options,  instead of the standard X session.

My xstartup is very basic:

```
#!/bin/bash
startxfce4 &
```

but it worked well before! Nevertheless, I tried to change it according  to various solutions found on the web, but still I get the grey screen.
In principle, nothing changed in the server (no updates, since it was  down), the client has been regularly updated, but still in Ubuntu 18.04.
The log of the connection seems similar to what I obtained in the past, when it worked (not sure...):

```
Fri May 8 14:27:45 2020
vncext: VNC extension running!
vncext: Listening for VNC connections on port 5902
vncext: created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
AUDIT: Fri May 8 14:27:45 2020: 6583 Xvnc4: client 1 rejected from local host
AUDIT: Fri May 8 14:27:46 2020: 6583 Xvnc4: client 1 rejected from local host
AUDIT: Fri May 8 14:27:47 2020: 6583 Xvnc4: client 1 rejected from local host
/usr/bin/startxfce4: X server already running on display :2
xfce4-session: Another session manager is already running
AUDIT: Fri May 8 14:27:48 2020: 6583 Xvnc4: client 1 rejected from local host
AUDIT: Fri May 8 14:27:49 2020: 6583 Xvnc4: client 1 rejected from local host

```
Don't know what to try... unless the problem is due to the fact that I'm  not physically logged in the server. I usually left it logged in in the  past, but I have no access to it in this period. I assume the server is  simply up (I can access it via SSH and VNC indeed connects), at the  login page.

It may also be that the X-server did not properly start on the server.  There are some issues with the graphic card I never solved, and  sometimes I have to reboot 2-3 times before getting a working X-server.  It is likely that the pc is now up and connectable via ssh, but the  X-server has not properly started. Would this explain the VNC behaviour?  How can I check it? Of course I could reboot various time remotely, but  it's risky since I don't know when someone else can re-start the server  in case of failure...

Thanks,

Stefano

---

### Post by wildmanne39 on 2020-05-09
*Thread moved to **Server Platforms for a more appropriate fit**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by burkina76 on 2020-05-10
Hi all,

I found the solution!
I suspected the problem was with:

```
/usr/bin/startxfce4: X server already running on display :2
xfce4-session: Another session manager is already running
```

so I did a search for that on the web.
It turns out that this could be solved by changing my xstartup file to:

```
#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
startxfce4 &
```

and it worked!
I don't know why this issue appeared after the blackout and the reboot of the server, but I'm happy as long as this solution works...

Thanks,
Stefano

---

