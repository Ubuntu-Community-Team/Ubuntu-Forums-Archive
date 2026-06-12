---
title: "Ubuntu-desktop-core ? on Server 8.04 LTS 64 bit"
date: 2009-06-29
forum: Server Platforms
---

### Post by dragos2 on 2009-06-29
I want to install Gnome desktop on Ubuntu Server 8.04 LTS 64 bit for users
to work remote on some software, but I did not liked the gnome-core (debian default)
and I tryed the gnome-desktop-environment, I did not liked that either.

I would like something with the look of ubuntu-desktop package but a little lighter,
something like ubuntu-desktop-core (not many default applications like open office for
example).

Any idea of how to achive that ?

---

### Post by netztier on 2009-06-29
> **dragos2 said:**
> for users
to work remote on some software

You don't need a full desktop environment on the server for running a sever-based app and have it's graphical output elsewhere. The UNIX-style window system X11/X/Xfree86/X.org (whatever it's been named in it's various incarnations and generations) has been inherently network-capable from the start.

So install the app, along with the basic X client libraries. Have the users log in remotely using SSH with X-forwarding enabled (ssh *-X* username@server) and then start the application. The app (now acting as "X client") will run on the server, using it's RAM, CPU and disk, but the display output will be sent to the user's workstation where the "X server" runs and takes care of displaying the output on the local screen.

A simple app to try this with is **xterm**. So, first install xterm on the server (this will drag along the necessary libraries, but not the full desktop environment):

```
user@server:~$ **sudo aptitude install xterm**
```

Have the user login to the server, check the content of the DISPLAY variable (it should point to "localhost", because we're running X through the established SSH session between workstation and server) and then start xterm.

```
user@workstation:~$ **ssh -X user@server**
user@server's password: *********
..
..
user@server:~$ **echo $DISPLAY**
localhost:11.0
user@server:~$ **xterm**

```

Of course, you need an X server application that runs on the user's platform. When running Linux, this comes "with the package" in the form of X.org that's used for the desktop environment.

For Windows, there's commercial products like [Hummingbird's Exceed]("http://connectivity.hummingbird.com/products/nc/exceed/index.html"), but also free X server implementations based on X.org such as [Cygwin]("http://x.cygwin.com/") or [Xming]("http://www.straightrunning.com/XmingNotes/") .

regards

Marc

---

### Post by dragos2 on 2009-06-29
Thank you for you wonderful explanation but things are a little different. 
We already have NX Server Enterprise licenses and I must admit its 10x better than
VNC. Users are already used to use NX Client.

I did some testings locally in VirtualBox:

sudo apt-get install x-window-system-core xserver-xorg gnome-core

This is whay I want but I don't like the aspect, so I found ubuntu-artwork, 
I did not installed it yet (tomorrow when I will get back to work), maybe
it will be what I want in terms of aspect.

I still have 3 questions:

1) Is ubuntu-artwork enaught applied over apt-get install x-window-system-core xserver-xorg gnome-core to make it look like Ubuntu Desktop ?

2) If I will use xserver-xorg-core will gnome-core work ?

3) I have an error related to an appled missing or not working properly after
I install gnome-core or gnome-desktop-environment or ubuntu-dekstop,
I just delete it and it works fine after that. I will post the exact error tomorrow,
so I am wondering how stable is gnome-core under Server 8.04 64 bit?

---

