---
title: "Unable to get two X sessions working in desired manner"
date: 2012-07-15
forum: Ubuntu Studio
---

### Post by leo_m on 2012-07-15
Log of activities till date and problems encountered:

Installed fglrx drivers for 3D acceleration.  Could not start two X servers successfully using lightdm.conf seats clauses.

Thought this might be a limitation of fglrx drivers.  So instead of starting two X servers, attempted to start two X sessions in the same X server.  startx resulted in the xfce session,  but I wanted ubuntustudio session.  startx also resulted in starting X as root; if I ran startx as a different user, I got 'protocol' errors upon starting X and could not get the desktop on the virtual terminal.

Back to using two servers, but using radeon driver.  I was able to run the dummy driver for one of the X servers and thus get two X servers up (one with radeon driver, the other with dummy driver), but this means I do not get a nice desktop on the physical monitor attached to the machine using virtual terminal switching (ctrl-alt-Function key (f7/f8 in my case)).  This is expected as dummy driver is not expected to render anything on physical display (vt8) I suppose.  But this does not meet my needs as I need both  VNC access and physical rendering.

Back to using startx and same problems except the machine does not hang while doing virtual terminal switching after some time (it hanged when fglrx was being used).

What I want to do:
On system startup,
Autologin user a into X session 1 running on default active virtual terminal.  This is used for XBMC.  I want to run some scripts to mount network shares when this user is auto-logged in, for use by XBMC.
Autologin user b into X session 2 running on next virtual terminal (or a fixed no. virtual terminal, such as vt8).  I want to run some scripts to run some VMs when this user is auto-logged in.  For this user, I also want this active session to be accessible via vnc remotely.  I would have been happy to get vnc running for all my X sessions, but XBMC needs 3D acceleration and for some reason, is not viewable over vnc.

The lilghtdm.conf for multi-X servers, all available via VNC is as below (server :1 is not started, VNC too is started for :0 and :2 only).  For startx mode using one server only, I just comment out all Seat sections:

```
SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=ubuntustudio
greeter-hide-users = true
greeter-allow-guest = false
greeter-show-manual-login = true
allow-guest=false


#The last seat mentioned below will become the active seat if using fglrx; if using radeon/radeonhd,
#the first seat mentioned will become the active seat

#dummy driver, in memory layout, intended for use only in remote sessions, either via xdmcp or vnc
#main desktop
[Seat:0]
#amdcccle Layout in case one wants to use fglrx proprietary driver by ATI instead of radeon/radeonhd open
#source drivers.  fglrx supports 3-D acceleration but lacks multi-X servers running on same card [201207]
#xserver-layout="amdcccle Layout"
xserver-command=/usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -sharevts
#greeter-setup-script=/usr/bin/x11vnc -display :0 -xkb -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -localhost -ncache 0 -ncache_cr -o /var/log/x11vnc-0.log

#mediacenter
[Seat:1]
xserver-command=/usr/bin/X :1 -auth /var/run/lightdm/root/:1 -nolisten tcp vt8 -novtswitch -sharevts
#greeter-setup-script=/usr/bin/x11vnc -display :1 -xkb -auth /var/run/lightdm/root/:1 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5901 -localhost -ncache 0 -ncache_cr -o /var/log/x11vnc-1.log

[Seat:2]
xserver-layout="DefaultLayout"
xserver-config=/home/leo/scripts/x/xorg.dummy.conf
xserver-command=/usr/bin/X :2 -auth /var/run/lightdm/root/:2 -nolisten tcp vt9 -novtswitch -sharevts
greeter-setup-script=/usr/bin/x11vnc -display :2 -xkb -auth /var/run/lightdm/root/:2 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5902 -localhost -ncache 0 -ncache_cr -o /var/log/x11vnc-2.log

[XDMCPServer]
#enabled=false
#port=177
#key=
enabled=true
 
#
# VNC Server configuration
#
# enabled = True if VNC connections should be allowed
# port = TCP/IP port to listen for connections on
#
# Not enabled because asks for password if enabled but it is not clear where the password is to be configured
[VNCServer]
enabled=false
#port=5900
#width=1024
#height=768
#depth=8

```As soon as I define any seat, I lose virtual terminal switchinig capability (ctrl-alt-Function keys) and the text consoles are lost too.

As I wish to continue to use lightdm if possible (want to make as few changes to the default installation as possible), I guess a solution which enables me to...:

a) use startx as non root user (setting allowed-users=anybody is no use) and get ubuntustudio session instead of xfce session when using startx without involving lightdm
or
b) use startx such that I get lightdm greeter on another vt
without losing text consoles on vts2-6

...would be acceptable.

Also, while tinkering with the config, certain presumptions I had do not seem to hold well...
I had thought every graphics card gets a display number (:0, :1 etc.); screens on that card are then referred to using . notation, as in :0.0 for 1st graphics terminal (whether 1st head or virtual terminal based) on 1st card, :0.1 for 2nd graphics terminal (2nd head for a multi-head card or 2nd graphics virtual terminal) on 1st card etc.  But different xsessions, even if running on the same card (hardware), get different display numbers (:0, :1 etc., contrast with expected :0.0, :0.1 etc.).  So, for a card with 3 heads (vga, hdmi, dvi), I expected numbering as follows (assuming physical heads take precedence over virtual ones):
VGA: 0.0, HDMI: 0.1, DVI: 0.2, VT7: 0.3, VT8: 0.4, VT9: 0.5...of course, the numbers after the . should be customizable, as in if you wanted to name VT8 as 0.10 you could do that, but to name an xsession as :1 instead of :0.n is something I do not quite understand ('cos the two different sessions are still on the same card).

This way, virtual terminals are attached to a machine, not to a head (vga, hdmi, dvi etc.)

But apparently, I have not grasped the scheme fully, otherwise xsessions would be numbered as above, not as :0, :1 etc.

---

