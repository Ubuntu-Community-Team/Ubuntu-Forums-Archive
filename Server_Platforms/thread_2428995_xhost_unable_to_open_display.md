---
title: "xhost unable to open display"
date: 2019-10-12
forum: Server Platforms
---

### Post by jamesstan2 on 2019-10-12
I'm trying to run Remmina under 18.04lts but it throws:

```
james@james-linux:~$ remmina
Unable to init server: Could not connect: Connection refused
(org.remmina.Remmina:1421): Gtk-WARNING **: 02:09:15.975: cannot open display:
```


Similarly if I just type xhost I get:

```
xhost:  unable to open display ""
``` 

Quite a few people have tried  ```
host +si:localuser:host
```
but this does not work for me.

To try and explore the xhost issue I've tried: ```
james@james-linux:~$ pgrep -a Xorg
32577 /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch 
```

I am assuming Remmina is not getting authority by xhost becuase there is problem with authorizing (or specifying) the display? However, maybe the answer lies in the pgrep above and I'm poking with things that I'm not very sure about. (The above is a short-list of the things I've tried...)

Any help to get this running would be mightily appreciated!

---

### Post by TheFu on 2019-10-12
Which desktop?
Are you using Wayland or X11?
Is this a local request or remote?
What is the DISPLAY environment variable?

---

### Post by Skaperen on 2019-10-12
> **jamesstan2 said:**
> 
```
xhost:  unable to open display ""
``` 

that error message suggests that the DISPLAY environment variable is unset.  _xhost_ needs to have the _DISPLAY_ environment variable set so it can communicate with the local X server.

since you are using _remmina_, that suggests you are trying to connect over the network.  is that X server also listening on a network port?  within the same hosts, the default is to use Unix domain named sockets for more reliable authenticity and no need for encryption.  try this on the remote host (its console or an ssh session):
```

sudo netstat -antp|fgrep -i listen

```
and see if X is shown listening to a high port number.  you will need to have a _DISPLAY_ environment variable value that refers to that host by name or address, plus X port number.

---

### Post by jamesstan2 on 2019-10-12
While I'm unclear how this shoudl help, an attempt to run xman results in:
```
 Error: Can't open display: 
```

> **TheFu said:**
> Which desktop?
Are you using Wayland or X11?
Is this a local request or remote?
What is the DISPLAY environment variable?


In response to questions:
- which desktop - ideally none.  But to try and fix the issue I did install the Lubuntu one
-  Wayland or X11 - as far as I know X11. Isn't that what Remmina works  with?  There seems to be one variable to set in the sshd config file  which was set correctly. May be others shoudl be set too?
- remote (ssh via putty) but the results i.e., can't open display have been similar on the terminal
- display environment variable. I have tried setting to both '0' and '1' I think this needs a colon? How do I check this.

---

### Post by TheFu on 2019-10-12
If using remote X11, the easiest way is to use **ssh -X userid@remoteIP command**.  Assuming all the defaults are left alone on the remote sshd daemon, then in a few seconds, the "command", perhaps "xterm -sb" will cause an xterm to be displayed on the local machine.  No wasted overhead of remmina.  

All the X11 traffic will go through the ssh tunnel.
The DISPLAY variable will be automatically set correctly.

This doesn't work so well over the internet, unless the connections are really high-speed. Should work fine over any modern LAN and most corporate WANs.

If you want a remote desktop, there are better tools, IMHO.

---

### Post by jamesstan2 on 2019-10-12
Thanks for the response!
> **Skaperen said:**
> that error message suggests that the DISPLAY environment variable is unset.  _xhost_ needs to have the _DISPLAY_ environment variable set so it can communicate with the local X server. 
I've been trying to work out how to do this along with the correct syntax.  Some have suggested with, and other without, a colon.  Do you have an answer to this one? :)

> since you are using _remmina_, that suggests you are trying to connect over the network.
I am a noobie to this.  My goal is to remote (ssh over a non-standard port) to a Ubuntu 18.04lts box and then connect to various local machines (generally windows 10).

  > is that X server also listening on a network port?  
In my scenario I'm assuming to configure the Remmina to use RDP and the standard 33xx ports for this.  For Remmina [https://remmina.org/how-to-install-remmina/](https://remmina.org/how-to-install-remmina/)
I've tried both the repository and Flatpak approach.  The latter shows a window opening - a GUI - to configure connections.  While it all looks smooth in the video... has not worked out so smoothly on my box :evil:
  
> within the same hosts, the default is to use Unix domain named sockets for more reliable authenticity and no need for encryption.  try this on the remote host (its console or an ssh session):
```

sudo netstat -antp|fgrep -i listen

```
and see if X is shown listening to a high port number.  

Here is the result - are we interested in cupsd? (sorry for the naivete)
```
 
james@james-linux:~$ sudo netstat -antp|fgrep -i listen
[sudo] password for james:
tcp        0      0 0.0.0.0:3131            0.0.0.0:*               LISTEN      1329/sshd
tcp        0      0 0.0.0.0:3260            0.0.0.0:*               LISTEN      1227/tgtd
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      1107/systemd-resolv
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3269/cupsd

```

> you will need to have a _DISPLAY_ environment variable value that refers to that host by name or address, plus X port number.
To try and get Remmina to open its promised configuration GUI (or am I off track here - should I be setting up a config file to get this going?) is there a specific configuration (localhost and root?)

Thanks for the help so far!

---

### Post by TheFu on 2019-10-13
If you use ssh with X11-Forwarding, on the remote machine, after I use exactly these commands:

```
uxterm  -sb  -e ssh -X istar &
$ env|grep DISP
DISPLAY=istar:11.0

```
that is the style for what the REMOTE system needs to have for DISPLAY.  'istar' is the hostname to a remote system on my LAN and my client machine knows it by that name.  It could just as easily been 192.168.22.5:11.0 .  ssh fills in the 11.0 part when you use **ssh -X** for the connection.  I don't know of any way to configure that on the client-side, but I've only been doing this stuff 25+ yrs.

---

