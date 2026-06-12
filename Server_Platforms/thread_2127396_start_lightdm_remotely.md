---
title: "start lightdm remotely"
date: 2013-03-19
forum: Server Platforms
---

### Post by kid1000002000 on 2013-03-19
Hello,

I recently decided to disable the GUI to my 12.04 ubuntu server and just use ssh. To get lightdm to run (and subsequently VNC to it), I now have to have physical access to the box, login as root, and run "lightdm". I would like to do this remotely via ssh. What I have tried:

Ssh in from client1 (Ubuntu Desktop 12.10) to user1@192.168.1.2, drop to root via sudo su, and run "lightdm" (or screen -dm lightdm). A monitor on the server shows lightdm's login screen, but it is not accessible to client1 yet. Go to server and enter the password for user1. It attempts to login but returns to the login screen.

Ideas? Thank you.

---

### Post by cariboo on 2013-03-20
Why start the full desktop? use X-forwarding, and just run the app you need:

```
ssh -X user@server
```

then start the application you want to run from the command line.

---

### Post by apollothethird on 2014-03-17
> **cariboo907 said:**
> Why start the full desktop? use X-forwarding, and just run the app you need:

```
ssh -X user@server
```

then start the application you want to run from the command line.

Many things won't work unless you are actually logged into the server and not just running and X-forwarded application.

The same things mail also fail if there was a way to actually get a lightdm prompt remotely, then perform a full login.  I would imagine the OP is trying to accomplish this... it certainly appears that this is his question.

I see this same answer duplicated many times with this reoccurring question.

If it's not possible to actually have a full login to an Ubuntu's lightdm session, maybe the people responding might say it's not possible and the question might stop recurring.  But if it's possible, hopefully someone would provide the formula for doing this.

By the way and example of something that won't work over an ssh -X session (in Ubuntu version 13.10) is:

```

$ gnome-control-center

```

It works on the local machine, but doesn't work if you ssh -X into the machine from remote.  I have tried this on a number of installs and always get this error message (when running version 13.10):

```

** (gnome-control-center:24169): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-9qyJDPNLOD: Connection refused
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.

(gnome-control-center:24169): Gdk-ERROR **: The program 'gnome-control-center' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadLength (poly request too large or internal Xlib length erro'.
  (Details: serial 210 error_code 16 request_code 153 minor_code 1)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap (core dumped)
apollo@mckelveyhome:~$ gnome-control

```

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by steeldriver on 2014-03-17
You can run a full *desktop session* without starting a *display manager* (lightdm) - startx, startkde, startxfce4, startlxde etc. (although there may be some specific wrinkles with starting Unity sessions that way)

If you really want to run lightdm and log into it remotely, see [Remote VNC login to Ubuntu 11.10]("http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/") (yes it's for 11.10 which is no longer supported, but the principle is the same I think)

FWIW I was just able to run gnome-control-center over ssh -X (actually PuTTY with the 'Allow X forwarding' box checked) to xming on a Windows box from 12.04 so maybe it's something you should address specifically (bug report?) in 13.10

---

### Post by apollothethird on 2014-03-17
> **steeldriver said:**
> You can run a full *desktop session* without starting a *display manager* (lightdm) - startx, startkde, startxfce4, startlxde etc. (although there may be some specific wrinkles with starting Unity sessions that way)

If you really want to run lightdm and log into it remotely, see [Remote VNC login to Ubuntu 11.10]("http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/") (yes it's for 11.10 which is no longer supported, but the principle is the same I think)

FWIW I was just able to run gnome-control-center over ssh -X (actually PuTTY with the 'Allow X forwarding' box checked) to xming on a Windows box from 12.04 so maybe it's something you should address specifically (bug report?) in 13.10

Thanks for the information that you have provided.

I had been using the ssh -X for years.  It always worked.  I'm not sure which version it became broken in, version 13.04 or version 13.10.  But I tried to make it very clear in my post that I was referring to version 13.10 which fails.

Most of the time, with the great wisdom of the powers that be, I have learned that when something become broken in newer versions, that's because the developers are trying to enforce a new way of doing things... for instance, for years all you had to do was just edit /etc/resolv.conf and it would survive boots, not there are a number of complex configurations you have to set to have your resolv.conf survive boots.

What works with ssh -X in 12.04 doesn't work in 13.10.  Hopefully someone familiar with the way things are going will give some workable alternative.

At present I almost have to get in my car and drive miles to a client's location to do some maintenance that has for years been a simple matter from my local console.

I'm hoping there might be something for Ubuntu to Ubuntu that Canonical has provided for Ubuntu to Windows.

For windows you can run, "rdesktop ipaddress".  You'll get a login prompt and you can log in.

For Ubuntu you have: "xvncviewer ipaddress".  However, someone has to be on the other end to start the desktop session for you to connect to.

For windows, you get a login prompt and that starts the desktop session on the local machine.

The solution might be so simple that no one is noticing the problem and the question.  However, with all the discussion, I'm still trying to have someone answer how to receive a lightdm login prompt on a local machine so that you can actually have a true remote desktop environment on your locate machine as if you were there at the remote machine.

Again, I'm very certain the feature exists.  I just don't know how to make it clear enough for someone with the answer to see the question.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

