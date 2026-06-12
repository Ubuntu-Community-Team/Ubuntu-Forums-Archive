---
title: "x11vnc XOpenDisplay failed"
date: 2012-10-06
forum: Virtualisation
---

### Post by Apathia on 2012-10-06
I know this has been posted a number of times, but I've gone through all the posts and attempted to find a solution but everything's failed so far :(

I'm running Ubuntu 12.04 Server with Gnome and my issue is this:
```
servu@ServU:~$ x11vnc
06/10/2012 11:35:21 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 5169
06/10/2012 11:35:21 XOpenDisplay("") failed.
06/10/2012 11:35:21 Trying again with XAUTHLOCALHOSTNAME=localhost ...
06/10/2012 11:35:21 
06/10/2012 11:35:21 *** XOpenDisplay failed. No -display or DISPLAY.
06/10/2012 11:35:21 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
06/10/2012 11:35:21 *** 1 2 3 4 
06/10/2012 11:35:25 XOpenDisplay(":0") failed.
06/10/2012 11:35:25 Trying again with XAUTHLOCALHOSTNAME=localhost ...
06/10/2012 11:35:25 XOpenDisplay(":0") failed.
06/10/2012 11:35:25 Trying again with unset XAUTHLOCALHOSTNAME ...
06/10/2012 11:35:25 

06/10/2012 11:35:25 ***************************************
06/10/2012 11:35:25 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:

** An X server (the one you wish to view) must be running before x11vnc is
   started: x11vnc does not start the X server.  (however, see the -create
   option if that is what you really want).

** You must use -display <disp>, -OR- set and export your $DISPLAY
   environment variable to refer to the display of the desired X server.
 - Usually the display is simply ":0" (in fact x11vnc uses this if you forget
   to specify it), but in some multi-user situations it could be ":1", ":2",
   or even ":137".  Ask your administrator or a guru if you are having
   difficulty determining what your X DISPLAY is.

** Next, you need to have sufficient permissions (Xauthority) 
   to connect to the X DISPLAY.   Here are some Tips:

 - Often, you just need to run x11vnc as the user logged into the X session.
   So make sure to be that user when you type x11vnc.
 - Being root is usually not enough because the incorrect MIT-MAGIC-COOKIE
   file may be accessed.  The cookie file contains the secret key that
   allows x11vnc to connect to the desired X DISPLAY.
 - You can explicitly indicate which MIT-MAGIC-COOKIE file should be used
   by the -auth option, e.g.:
       x11vnc -auth /home/someuser/.Xauthority -display :0
       x11vnc -auth /tmp/.gdmzndVlR -display :0
   you must have read permission for the auth file.
   See also '-auth guess' and '-findauth' discussed below.

** If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:

     gdm:     -auth /var/gdm/:0.Xauth
              -auth /var/lib/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
              -auth /var/run/xauth/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa

   Sometimes the command "ps wwwwaux | grep auth" can reveal the file location.

   Starting with x11vnc 0.9.9 you can have it try to guess by using:

              -auth guess

   (see also the x11vnc -findauth option.)

   Only root will have read permission for the file, and so x11vnc must be run
   as root (or copy it).  The random characters in the filenames will of course
   change and the directory the cookie file resides in is system dependent.

See also: http://www.karlrunge.com/x11vnc/faq.html
```

Most posts seem to point to finding which auth you'd use, so I tried:

```
servu@ServU:~$ ps wwwwaux | grep auth
servu     5162  0.0  0.0   4384   828 pts/1    S+   11:34   0:00 grep --color=auto auth
```

Not that helpful, right?

Ok, let's try guessing the auth:
```
servu@ServU:~$ x11vnc -auth guess display :0
06/10/2012 11:37:21 passing arg to libvncserver: display
06/10/2012 11:37:21 passing arg to libvncserver: :0
06/10/2012 11:37:22 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 5272
06/10/2012 11:37:22 -auth guess: failed for display='unset'
```


So now I'm at a loss as to what to do. vnc4server works, but the clipboard on it doesn't. I'm hoping switching would correct that (My client PC is using UltraVNC on Win7)

Edit* So I found that x11vnc is in the app this on the gnome desktop (vncserver desktop) so I ran it, and then I was able to connect successfully, it even shared the screen.

Progress, maybe!
I've been able to get a connection using the -create switch, but when I try and connect using UltraVNC, I get "The server running as application".

---

