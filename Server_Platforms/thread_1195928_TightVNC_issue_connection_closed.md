---
title: "TightVNC issue connection closed"
date: 2009-06-24
forum: Server Platforms
---

### Post by Jay100 on 2009-06-24
Hi guys, I am not sure if I have posted this in the right forum, apogies if I haven't.
I have recently installed a Ubuntu 9.04 Jaunty server and very much enjoy this side of the computing world.

I simply wanted to be able to access this server from the internet.  I installed TightVNC on a remote windows machine and turned on the remote desktop preferences on my Ubuntu server.  All worked fine and I could access my server.  But I needed to be able to transfer files.  TightVNC has this ability but seemed to require a server version of TightVNC on the host computer, so consequently, I installed it on my Ubuntu machine.
However, now, I keep getting an error.

I log onto the address of my server from the internet and all is fine so far, it asks me for the password, which I type in. It recognises the password, but then has problems and instantly kicks me, displaying the message 'Connection Closed'

I have a log of what is going on on my Ubuntu server and if I posted it here, just wondered if anyone could shed some light as to what is going on as I can't make head nor tail of it.  Any response would be greatly appreciated:)

log:
vncSockConnect.cpp:    accepted connection from 86.137.127.198 
vncClient.cpp:    vncClient() executing... 
vncClient.cpp:    client connected : 86.137.127.198 (id 20) 
vncServer.cpp:    AddClient() done 
vncClient.cpp:    negotiated protocol version, RFB 3.8 
vncClient.cpp:    enabling TightVNC protocol extensions 
vncClient.cpp:    performing VNC authentication 
i:\tightvnc-1.3.10-setup\vnc_winsrc\winvnc\vncPasswd.h:    PASSWD : ToText called 
i:\tightvnc-1.3.10-setup\vnc_winsrc\winvnc\vncPasswd.h:    PASSWD : ToText called 
Wed Jun 24 15:31:53 2009 
vncMenu.cpp:    tray icon updated ok 
WallpaperUtils.cpp:    KillActiveDesktop 
WallpaperUtils.cpp:    unable to access Active Desktop object:80040154 
vncDesktop.cpp:    initialising desktop server 
vncDesktop.cpp:    KillScreenSaver... 
vncDesktop.cpp:    SCR-WBB: current display: w=1024 h=768 bpp=32 vRfrsh=60. 
vncService.cpp:    unable to open desktop, error=120 
vncService.cpp:    SelectHDESK() to Default (38) from 38 
vncService.cpp:    SelectHDESK failed to close old desktop 38, error=170 
vncServer.cpp:    failed to initialize desktop object 
VSocket.cpp:    closing socket 
vncDesktop.cpp:    killing desktop server 
vncServer.cpp:    Authenticated() done 
vncServer.cpp:    RemoveClient() done 
vncClient.cpp:    ~vncClient() executing... 
vncClient.cpp:    deleting socket 
vncMenu.cpp:    tray icon updated ok 
vncMenu.cpp:    tray icon updated ok 
WallpaperUtils.cpp:    unable to access Active Desktop object:80040154

---

