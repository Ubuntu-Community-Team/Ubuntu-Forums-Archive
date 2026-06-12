---
title: "Starting a window manager on a remote display"
date: 2006-10-20
forum: Server Platforms
---

### Post by Ruskie on 2006-10-20
Uhm, not sure if this is the right forum to post, I hope so.
I have read all over the forum looking for help on how to do this thing, but I didn't find it anywere...

Basically, at home on Kubuntu and at work on Solaris/AIX/Tru-64/HP-UX I am able to launch all sort of graphical applications, ranging from xclock, to OUI, to Sapinst etc, using the old usual method:

1. Launch an XServer on corporate Windows laptop (I use X-Win32)
2. Logon to Unix/Linux server through telnet or ssh
3. Export DISPLAY=<ip of laptop>>:0
4. Launch the application

This works perfectly if I launch a program, like those I said above, or Konqueror, or whatever.
But I would like to launch directly KDE, or in general a Window Manager, only running on a remote display. How can I obtain that??

I tried using startx -- :1 and some variants, but it never worked... At best cases, when the command did not fail, I could notice a new logon screen popping out on Linux screen, but nothing on the laptop.

How can I do if I want that startx output appeared in a window on my laptop? I would like to have something similar to what you get when you run VNC, but with the system console "free" for use on local site. Is this result achievable?

Thanks
Marco

---

### Post by Woei on 2006-10-21
> **Ruskie said:**
> Uhm, not sure if this is the right forum to post, I hope so.
I have read all over the forum looking for help on how to do this thing, but I didn't find it anywere...

Basically, at home on Kubuntu and at work on Solaris/AIX/Tru-64/HP-UX I am able to launch all sort of graphical applications, ranging from xclock, to OUI, to Sapinst etc, using the old usual method:

1. Launch an XServer on corporate Windows laptop (I use X-Win32)
2. Logon to Unix/Linux server through telnet or ssh
3. Export DISPLAY=<ip of laptop>>:0
4. Launch the application

This works perfectly if I launch a program, like those I said above, or Konqueror, or whatever.
But I would like to launch directly KDE, or in general a Window Manager, only running on a remote display. How can I obtain that??

I tried using startx -- :1 and some variants, but it never worked... At best cases, when the command did not fail, I could notice a new logon screen popping out on Linux screen, but nothing on the laptop.

How can I do if I want that startx output appeared in a window on my laptop? I would like to have something similar to what you get when you run VNC, but with the system console "free" for use on local site. Is this result achievable?

Thanks
Marco


The problem is that login managers like GDM, XDM and KDM use the ***XDMCP*** protocol. XDMCP uses UDP, and SSH does not support forwarding UDP traffic. Your login manager launches quite a bit of scripts at login to start all services a modern desktop environment like Gnome or KDE needs, so the trick is to "transcribe" these login scripts into a single script and launch it after logging in remotely with SSH. (BTW, if you login with ssh -Y, you needn't explicitly export your DISPLAY environment variable.) These scripts are located at */etc/X11/Xsession.d/*, and a lot of variables used in these scripts are set by GDM. Just like with the sysv init system, scripts with a higher number are sourced later on in the startup process than scripts with a lower number.

I was in exactly the same situation as you were, and this is my ~/.start-gnome script, which I launch with ```
source ~/.start-gnome
``` after logging in through SSH:```

# This file is sourced by Xsession(5), not executed.

DBUSLAUNCH=/usr/bin/dbus-launch

STARTSSH=
SSHAGENT=/usr/bin/ssh-agent
SSHAGENTARGS=

if [ -x "$SSHAGENT" ] && [ -z "$SSH_AUTH_SOCK" ] \
     && [ -z "$SSH2_AUTH_SOCK" ]; then

     STARTSSH=yes

  if [ -f /usr/bin/ssh-add1 ] && cmp -s $SSHAGENT /usr/bin/ssh-agent2; then

    # use ssh-agent2's ssh-agent1 compatibility mode
    SSHAGENTARGS=-1

  fi
fi

if [ -n "$STARTSSH" ]; then
  STARTUP="$SSHAGENT $SSHAGENTARGS $DBUSLAUNCH --exit-with-session $STARTUP"
fi

echo "$STARTUP"
exec $STARTUP gnome-session

```

Replace gnome-session with the KDE's session manager (kdeinit ?).

---

### Post by Ruskie on 2006-10-22
Thank you very much Woei, will try this...

---

