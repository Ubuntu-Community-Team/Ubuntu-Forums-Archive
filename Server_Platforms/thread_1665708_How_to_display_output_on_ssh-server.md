---
title: "How to display output on ssh-server"
date: 2011-01-12
forum: Server Platforms
---

### Post by ulriksvensson on 2011-01-12
Hi all,

this is probably a strange question.

I have two computers both running Ubuntu 10.04. I use my laptop to ssh to the other computer. If I start for instance firefox via ssh from my laptop to have the browser showing up on the screen attached to the computer I ssh to? The computer i ssh to is better in handling graphics so I want to connect it to the TV and use my laptop as remote-control.

//Ulrik

---

### Post by wongo888 on 2011-01-12
Have you considered VNC?

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by vortmax on 2011-01-12
When you use x-forwarding, the server forwards openGL commands to the client to be rendered, so it really isn't gaining you much.

I have used both virtualgl+turboVNC and freenx for running matlab remotely and they both run visualizations very smoothy, although I haven't pushed the limits.  The nice think about freenx is you can run single applications through it, giving you something similar to x-forwarding, but much, much faster.  I have heard talk about running virtualGL on freenx, which would honestly be pretty cool, but I haven't seen it work or attempted it myself.

If you are talking about leaving the other computer connected to the TV and just controlling it with your laptop, you will want to use X11vnc.  X11vnc allows you to attach a vnc server to screen :0, so when you connect with your laptop, you get a mirror copy the desktop running on the server, allowing you to control it remotely.  Video on the client will be choppy, but you will be able to manage applications and such.  There are also some media apps out there that let you setup a backend on the server and connect to it remotely to control it.  That would be more of a true remote control, but also more involved to setup

---

### Post by sj1410 on 2011-01-12
```
ssh -X user@server
```

---

### Post by ulriksvensson on 2011-01-13
To clarify: I want to use my laptop to start a program on the server (the other computer) and have the display on the server. If the display shows up on the laptop as well it's fine but not nessecary. I think vortmax is closest in his last sentence.

---

### Post by arrrghhh on 2011-01-13
> **ulriksvensson said:**
> To clarify: I want to use my laptop to start a program on the server (the other computer) and have the display on the server. If the display shows up on the laptop as well it's fine but not nessecary. I think vortmax is closest in his last sentence.

Indeed.  NoMachine FreeNX, X11VNC, any of these things will get the job done for ya.

Why do you have a GUI on a server tho?  Seems kinda silly.  Should've just installed the desktop edition :p

---

### Post by ulriksvensson on 2011-01-13
> **arrrghhh said:**
> Indeed.  NoMachine FreeNX, X11VNC, any of these things will get the job done for ya.

Why do you have a GUI on a server tho?  Seems kinda silly.  Should've just installed the desktop edition :p

No, I used the term server because this computer is the one which I would ssh to. It's got the desktop edition running. So I guess I'll have look on X11VNC then. Thanks for all your help!

---

### Post by CharlesA on 2011-01-13
You can just use FreeNX instead of VNC, as VNC shouldn't be exposed to the internet.

---

### Post by CharlesA on 2011-01-13
You can just use FreeNX instead of VNC, as VNC shouldn't be exposed to the internet.

---

### Post by ulriksvensson on 2011-01-20
FreeNX seems pretty much impossible to get to work on Maverick.

---

### Post by ulriksvensson on 2011-01-20
FreeNX seems pretty much impossible to get to work on Maverick.

---

### Post by vortmax on 2011-01-20
I'm running freenx on maverick without any problems.

I followed this guide: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

What problems are you having?

---

### Post by vortmax on 2011-01-20
Dp

---

### Post by CharlesA on 2011-01-20
I was able to get FreeNX installed and working on Maverick. The window decordations weren't visable tho.

---

### Post by CharlesA on 2011-01-20
I was able to get FreeNX installed and working on Maverick. The window decordations weren't visable tho.

---

### Post by vortmax on 2011-01-20
It's a known bug.  I connect to my freenx server with clients on windows, Kubuntu Lucid and Ubuntu Lucid.  On the windows and Kubuntu machines, window decorations are drawn fine.  When I connect from my laptop running Ubuntu (gnome) Lucid, I get the no boarders bug.

FWIW, if you run KDE (kubuntu desktop) on the server, you don't have the problem.

---

### Post by arrrghhh on 2011-01-20
> **vortmax said:**
> It's a known bug.  I connect to my freenx server with clients on windows, Kubuntu Lucid and Ubuntu Lucid.  On the windows and Kubuntu machines, window decorations are drawn fine.  When I connect from my laptop running Ubuntu (gnome) Lucid, I get the no boarders bug.

FWIW, if you run KDE (kubuntu desktop) on the server, you don't have the problem.

I experienced this when compiz was enabled.  Is compiz enabled on your Lucid box?

---

### Post by ulriksvensson on 2011-01-22
> **vortmax said:**
> I'm running freenx on maverick without any problems.

I followed this guide: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

What problems are you having?
I can't log in. I get connected to ulrik@[ip-address of server] but then it says that NX service is not available on this computer. I guess I'm not sure if the setup of the server was done correctly. When I issue
sudo /etc/init.d/freenx-server start
I get "start: Unknown job: freenx-server".

---

### Post by vortmax on 2011-01-22
Did you run /usr/lib/nx/nx-setup?  Did you get any errors?  

I seem to remember having this error too, but don't remember what fixed it.  I believe it was trivial though.  If you can't figure it out, I can post the upstart script.

Disabling compiz doesn't seem to matter.  Its an issue with metacity itself.

---

### Post by ulriksvensson on 2011-01-22
> **vortmax said:**
> Did you run /usr/lib/nx/nx-setup?  Did you get any errors?  

I seem to remember having this error too, but don't remember what fixed it.  I believe it was trivial though.  If you can't figure it out, I can post the upstart script.

Disabling compiz doesn't seem to matter.  Its an issue with metacity itself.
Yes I've ran it without errors.

---

### Post by vortmax on 2011-01-22
here is my working freenx-server.conf file (in /etc/init/)

```


# apport - automatic crash report generation
#
# While this job is active, core dumps will captured by apport and
# used to generate automatic crash reports.

description     "automatic crash report generation"

start on runlevel [2345]
stop on runlevel [!2345]

env enabled=1

PATH_BIN=/usr/lib/nx

pre-start script
    if [ ! -e "/var/run/freenx-server" ]; then
        [ ! -d "/tmp/.X11-unix" ] && mkdir -m1755 /tmp/.X11-unix/
        $PATH_BIN/nxserver --cleanup
        $PATH_BIN/nxserver --start
        touch "/var/run/freenx-server";
    else
        echo "Not starting freenx-server, it's already started."
    fi
end script

post-stop script
    $PATH_BIN/nxserver --stop
    $PATH_BIN/nxserver --cleanup
    rm -f /var/run/freenx-server
end script

```

If you have this file installed already, double check your $PATH_BIN.  I seem to recall this is what I had to change. 

I would also try and run the server directly (/var/lib/nx/nxserver -start) and see if that works.  You may have to touch some log and tmp files and grant the nx user rw access to them.

---

### Post by ulriksvensson on 2011-01-22
> **vortmax said:**
> here is my working freenx-server.conf file (in /etc/init/)

```


# apport - automatic crash report generation
#
# While this job is active, core dumps will captured by apport and
# used to generate automatic crash reports.

description     "automatic crash report generation"

start on runlevel [2345]
stop on runlevel [!2345]

env enabled=1

PATH_BIN=/usr/lib/nx

pre-start script
    if [ ! -e "/var/run/freenx-server" ]; then
        [ ! -d "/tmp/.X11-unix" ] && mkdir -m1755 /tmp/.X11-unix/
        $PATH_BIN/nxserver --cleanup
        $PATH_BIN/nxserver --start
        touch "/var/run/freenx-server";
    else
        echo "Not starting freenx-server, it's already started."
    fi
end script

post-stop script
    $PATH_BIN/nxserver --stop
    $PATH_BIN/nxserver --cleanup
    rm -f /var/run/freenx-server
end script

```

If you have this file installed already, double check your $PATH_BIN.  I seem to recall this is what I had to change. 

I would also try and run the server directly (/var/lib/nx/nxserver -start) and see if that works.  You may have to touch some log and tmp files and grant the nx user rw access to them.
/var/lib/nx/nxserver doesn't exist. And my PATH_BIN is correct.

---

### Post by vortmax on 2011-01-22
What does "which nxserver" return?  What happens if you just run "nxserver -start" ?

---

### Post by ulriksvensson on 2011-01-22
```
ulrik@ulrik-desktop:~$ which nxserver
/usr/bin/nxserver
ulrik@ulrik-desktop:~$ nxserver -start
NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
Usage: nxserver <option>
--passwd: Change password
ulrik@ulrik-desktop:~$
```

---

### Post by vortmax on 2011-01-22
sorry, try:

sudo nxserver --start

---

### Post by ulriksvensson on 2011-01-23
Ok, it seems the server is working. I guess there's something on the client side then. I think I don't know how to use it really. Do I have to have a user on the client called "nx"?

---

