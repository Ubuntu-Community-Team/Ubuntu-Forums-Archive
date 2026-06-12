---
title: "Please help - trying to get a program to work in Wine"
date: 2009-04-02
forum: Wine
---

### Post by thebbxx on 2009-04-02
Hi, I am running a program that logs into a remote server.
When the program opens it asks for login information and a server to connect to. I enter my login, and the IP of the server the same way I do when running windows. Then I press connect and the error I just mentioned keeps repeating itself until the program tells me the server is not responding. I know the server is fine because I can connect in Windows with the same info.

I am getting the following error:

fixme:secur32:schan_InitializeSecurityContextW Using hardcoded "NORMAL" priority
fixme:secur32:schan_QueryContextAttributesW Unhandled attribute 0x5a
fixme:secur32:schan_QueryContextAttributesW Unhandled attribute 0x53
err:ole:CoWaitForMultipleHandles Unexpected wait termination: 192, 0
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:ras:RasEnumConnectionsW (0x82b0028,0x32e430,0x32e42c),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl 0x00000001, 0x32e404
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl 0x00000002, 0x32e404

Can someone tell me how I can get around this?

Thanks!

---

### Post by lswest on 2009-04-02
Firstly, what program are you running?  Have you tried the remote desktop client (Vinagre) that comes pre-installed with Ubuntu?  (In the Applications menu under "Internet" I think).

Any information such as program name, version, wine version, etc. would be useful.

---

### Post by thebbxx on 2009-04-02
Hi lswest, the program is called Encompass.  It's a loan origination software.  I would like to get this to run through wine and not remote desktop.  My wine is version 1.1.17 and I have installed .net with winetricks.  Need any other info just let me know.  Thanks

---

### Post by lswest on 2009-04-02
I've never heard of the program, nor do I have any experience trying to get it to run in Wine, so I really don't think I can be of much assistance.  Hopefully someone else in the community will be able to help you further.

Sorry,
Lswest

---

### Post by NightMKoder on 2009-04-04
From the error log, seems like the program is trying to use the RAS api, which is not implemented in wine yet ([http://source.winehq.org/source/dlls/rasapi32/rasapi.c#L115](http://source.winehq.org/source/dlls/rasapi32/rasapi.c#L115)).

Try settings rasapi32 to native (maybe the app comes with it), or try getting it from a windows box and then settings it to native.

---

### Post by thebbxx on 2009-04-06
Thanks NightMKoder!  I've set rasapi32 to native, but now it says:
Unknown login error: Error creating the Web Proxy specified in the 'system.net/defaultProxy' configuration section.

Any idea?  Thanks


> **NightMKoder said:**
> From the error log, seems like the program is trying to use the RAS api, which is not implemented in wine yet ([http://source.winehq.org/source/dlls/rasapi32/rasapi.c#L115](http://source.winehq.org/source/dlls/rasapi32/rasapi.c#L115)).

Try settings rasapi32 to native (maybe the app comes with it), or try getting it from a windows box and then settings it to native.

---

### Post by thebbxx on 2009-04-07
Also, the connection I am trying to make is over https

Could this be related to the problem?

---

