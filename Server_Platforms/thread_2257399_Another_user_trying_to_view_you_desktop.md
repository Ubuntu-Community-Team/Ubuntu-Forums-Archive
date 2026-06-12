---
title: "Another user trying to view you desktop"
date: 2014-12-19
forum: Server Platforms
---

### Post by richard_lee on 2014-12-19
Hi all,
I am using xubuntu (for my understanding which is ubuntu desktop 14.04.1 LTS +xfce 4.01) and x11vnc for the server side. I can success to make it auto start when the computer start up.
However,when I use turbovnc to connect to the server.Then I need to enter the password.It is still fine.
After that, the server side will prompt a dialog "Another user trying to view yours desktop".I need to switch to server side computer to allow the connection.
My question is how to configure auto allow for the x11vnc. That mean no disable the dialog. 
In ubuntu, some of website instruct to go to system>preferences>remote desktop to disable it.
However I don't have that location.
On the other hand, I have tried to add -accept for the x11vnc. It does not work for me.
Do anyone have idea for this problem?
Thank you.

---

### Post by Bucky Ball on 2014-12-19
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2014-12-20
> **Bucky Ball said:**
> *Thread moved to **Server Platforms**.*

VNC is a "server" now? Seems this topic would be better helped in a desktop sub-forum.  Isn't the "server" forum mostly for apache, samba and non-GUI stuff? I could be wrong, again. ;)

Wish I could help - don't use VNC here.  We use x2go which uses ssh-keys for authentication - no password prompts, more security, better performance. I'm always amazed when folks use VNC or RDP for this stuff when NX is much quicker and x2go has made it almost trivial to setup. Install the server on the remote side and use the client from the machine you sit at. The downside of x2go is that other NX tools are incompatible, but that is also a plus (in the Apple way) - no question about which client to use. ;)

There are other ways to remotely access a Linux machine - shell, single-application and whole-desktop. These techniques can be mixed and matched as desired based on bandwidth and security requirements.
[http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)

Generally, RDP and VNC require a full VPN to be used securely.  Whereas ssh and ssh with X-forwarding and NX-based tools include the ssh-tunnel already and use ssh-keys for authentication.

---

### Post by steeldriver on 2014-12-20
AFAIK it doesn't do that by default (unless the default has changed - I'm still using 12.04)

Can you share your x11vnc command string? are you tunnelling the connection? - please give details

---

### Post by richard_lee on 2014-12-21
I just want to make a simple vnc only.
I am a beginner in linux system.I have tried to make a file in the following path /etc/init/x11vnc.conf
```

start on login-session-start
    script
    x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -shared -bg -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5901 -localhost -accept
    end script

```

---

### Post by nerdtron on 2014-12-21
HHHmmmm sorry just passing by... I'm not using any VNC server to remote the server but instead uses purely ssh and command line interface.

What are tying to achieve on the GUI that you cant do on the command line? maybe we can help more with that (if this is the case)

But if you intend to use a GUI software/program, nevermind my comment. :D

---

### Post by steeldriver on 2014-12-21
Erm.. remove the '-accept'? from the x11vnc manpage:

```

       -accept string

              Run a command (possibly to prompt the user at the X11  display)
              to  decide whether an incoming client should be allowed to con&#8208;
              nect or not. 

```

---

