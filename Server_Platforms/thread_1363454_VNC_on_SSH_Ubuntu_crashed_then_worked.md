---
title: "VNC on SSH Ubuntu crashed then worked"
date: 2009-12-24
forum: Server Platforms
---

### Post by tapas_mishra on 2009-12-24
I was having some problem on access a remote machine via VNC so got a lot of error messages it is working fine right now I am mentioning the errors and how I solved them then the actual issue for which I am posting is at bottom

the remote machine did not had an X environment and no physical access to it so I installed the GNOME then 
I got following error 
```

[root@some machine ~]# vncviewer localhost:0


VNC Viewer Free Edition 4.1.2 for X - built Mar 24 2009 19:52:30
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com]("http://www.realvnc.com/") for information on VNC.
vncviewer: unable to open display ""


```the mistake was I was doing it as root Ubuntu does not allow to have a GUI to root
I have forgoten but some where I read that it is possible to give a GNOME login session to root also on Ubuntu some one may post the method here as I  forgot right now 
then 
I tried the following
```


tapas@tapas-laptop:~$ vncviewer IP of remote machine
IP of remote machine 5900 
java.net.ConnectException: Connection refused 
    at java.net.PlainSocketImpl.socketConnect(Native Method) 
    at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333) 
    at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195) 
    at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182) 
    at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366) 
    at java.net.Socket.connect(Socket.java:525) 
    at java.net.Socket.connect(Socket.java:475) 
    at java.net.Socket.(Socket.java:372) 
    at java.net.Socket.(Socket.java:186) 
    at rfbProto.(rfbProto.java:93) 
    at vncviewer.connectAndAuthenticate(vncviewer.java:193) 
    at vncviewer.run(vncviewer.java:122) 
    at java.lang.Thread.run(Thread.java:619) 
java.net.ConnectException: Connection refused

```did some changes on the remote machine again 


added a vncuser tapas  on remote machine
for using vnc 

in /etc/sysconfig/vncservers
```

VNCSERVERS="1:tapas" 

```note that tapas is username of vncuser who will be logging in to use vnc
then 
```

VNCSERVERARGS[1]="-geometry 640x480" 

```also did  # service vncserver start 
went to /home/tapas/.vnc and edited  
xstartup  
removed the comment from these two lines  
```

unset SESSION_MANAGER 
exec /etc/X11/xinit/xinitrc 

```also added following lines to the start of the file  
```

( while true ; do xterm ; done ) & 

```So that xterm session is available  
restarted vncserver 
```

service vncserver restart 

```vnc server was listening to the incoming vnc requests which was verified by following out put 
```

[root@localhost ~]# netstat -tualp | grep Xvnc
tcp        0      0 *:5801                      *:*                         LIST                                                                                        EN      15604/Xvnc
tcp        0      0 *:5802                      *:*                         LIST                                                                                        EN      26836/Xvnc
tcp        0      0 *:5901                      *:*                         LIST                                                                                        EN      15604/Xvnc
tcp        0      0 *:5902                      *:*                         LIST                                                                                        EN      26836/Xvnc
tcp        0      0 *:6001                      *:*                         LIST                                                                                        EN      15604/Xvnc
tcp        0      0 *:6002                      *:*                         LIST                                                                                        EN      26836/Xvnc
tcp        0      0 *:6001                      *:*                         LIST                                                                                        EN      15604/Xvnc
tcp        0      0 *:6002                      *:*                         LIST                                                                                        EN      26836/Xvnc



```then on the remote machine I checked again I had forgotten to mention following
```

exec gnome-session

```in /home/tapas/.vnc/xstartup file 
tapas being vncuser 
now over ssh it worked 
but it crashed first here is what I did 
```

ssh -X IP of remote server

```then 
```
vncviewer localhost:1
```I got a window which asked me password not the username I did enter and then pressed enter I guess that was vncpassword 
for a second I got a screen of some size which I do not know and some thing kept happening in background and then display crashed 
though there was nothing and I got following message on command line 
```

Thu Dec 24 16:43:35 2009
 CConn:       connected to host localhost port 5901
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8

Thu Dec 24 16:43:48 2009
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (MIT-SHM)
  Minor opcode of failed request:  3 (X_ShmPutImage)
  Value in failed request:  0x400
  Serial number of failed request:  523

```I repeated the above step did ssh on remote and then again vncviewer localhost:1
it worked 
if you do not use 
```

ssh -X IP of remote 
```and do ```
 ssh remote IP 
```and then execute ```
vncviewer localhost:1
```then you will get an error 
```

[tapas@remote IP ~]$ vncviewer localhost:1

VNC Viewer Free Edition 4.1.2 for X - built Mar 24 2009 19:52:30
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
vncviewer: unable to open display "
```



here is my problem 
1) Why did it crashed 
2)If I try to access it in mozilla  I am getting message
```

RFB 003.008

```Any guesses as to what should I do to access it using mozilla.
I would also like to mention that I am able to transfer display in opera via vnc

---

### Post by MontelEdwards on 2009-12-24
Did you know that Ubuntu already has a built in GUI for VNC? Go to applications, internet, remote desktop viewer.

---

### Post by tapas_mishra on 2009-12-24
Well it did not worked.

---

### Post by HermanAB on 2009-12-25
Howdy,

VNC is mainly a Windows thing and on Linux, VNC is almost always the wrong solution.  There are also VNC attack scripts on the loose, so putting a VNC machine on the public internet will get you hacked in no time.  You can search these forums for many tales of woe.

Since you already have SSH working, you don't need VNC at all.  Simply do this:
$ ssh -X -C -c blowfish user@server gnome-panel

and then drag this remote panel to the side or somewhere and go click happy.

---

### Post by HighCommander540 on 2009-12-25
> **HermanAB said:**
> Howdy,

VNC is mainly a Windows thing and on Linux, VNC is almost always the wrong solution.  There are also VNC attack scripts on the loose, so putting a VNC machine on the public internet will get you hacked in no time.  You can search these forums for many tales of woe.

Since you already have SSH working, you don't need VNC at all.  Simply do this:
$ ssh -X -C -c blowfish user@server gnome-panel

and then drag this remote panel to the side or somewhere and go click happy.

So what exactly does this do? Ok, but what if you want to run programs like a game? Wouldn't you need to to VNC over SSH? And how can they hack it if the VNC is only on localhost and you are using SSH to view the VNC?

---

### Post by tapas_mishra on 2009-12-25
> **HermanAB said:**
> Howdy,

VNC is mainly a Windows thing and on Linux, VNC is almost always the wrong solution.  There are also VNC attack scripts on the loose, so putting a VNC machine on the public internet will get you hacked in no time.  You can search these forums for many tales of woe.

You are right here.

> **HermanAB said:**
> 
Since you already have SSH working, you don't need VNC at all.  Simply do this:
$ ssh -X -C -c blowfish user@server gnome-panel

and then drag this remote panel to the side or somewhere and go click happy.
Well I got a crash report ```

The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet
```What could have caused this error and what should I look in for 
thanks for giving hint about ssh
there are a lot  more error messages 
like ```

** (gnome-panel:4952): WARNING **: panel-applet-frame.c:1287: failed to load applet OAFIID:GNOME_Panel_TrashApplet:
Failed to resolve, or extend '!prefs_key=/apps/panel/applets/trash_applet/prefs;background=none:;orient=up;size=x-small;locked_down=false
** Message: Could not connect to power manager: Could not get owner of name 'org.gnome.PowerManager': no such name
Unable to open desktop file /usr/share/applications/redhat-email.desktop for panel launcher: No such file or directory
Unable to open desktop file /usr/share/applications/openoffice.org-1.9-writer.desktop for panel launcher: No such file or directory
Unable to open desktop file /usr/share/applications/openoffice.org-1.9-impress.desktop for panel launcher: No such file or directory
Unable to open desktop file /usr/share/applications/openoffice.org-1.9-calc.desktop for panel launcher: No such file or directory
Unable to open desktop file /usr/share/applications/redhat-email.desktop for panel launcher: No such file or directory
Unable to open desktop file /usr/share/applications/openoffice.org-1.9-writer.desktop for panel launcher: No such file or directory
Unable to open desktop file /usr/share/applications/openoffice.org-1.9-impress.desktop for panel launcher: No such file or directory
Unable to open desktop file /usr/share/applications/openoffice.org-1.9-calc.desktop for panel launcher: No such file or directory

```
Dunno which ones should I look for

---

### Post by HermanAB on 2009-12-26
Hmm, the trash applet crashes???

If you make a brand new user account, then Gnome should set all the defaults up properly.  So try creating a new account on the server, ensure that Gnome actually works, then try it again over SSH.

Note that once you got it to work remotely, you can shut X down on the server - you won't need it anymore, since SSH forwards all X functions to your local machine X server, so this is less taxing on the server than VNC.

---

