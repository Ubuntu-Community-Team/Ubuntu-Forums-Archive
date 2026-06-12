---
title: "Webmin &amp; Wine Command"
date: 2013-04-12
forum: Server Platforms
---

### Post by RaJiska on 2013-04-12
Hello,

I have to post here because I have a problem with Webmin and the wine command.
When I launch the command "**sudo wineconsole --backend=curses file.exe -r file.txt -m file**", then it throws me back this error:

```

Error opening terminal: unknown. 
Application tried to create a window, but no driver could be loaded. 
Make sure that your X server is running and that $DISPLAY is set correctly. 
err:systray:initialize_systray Could not create tray window

```

This is perfectly working when I do from Putty.
I even launched the thing from Webmin with the same user than Putty, but still not working.

Thanks for your help :).

---

### Post by RaJiska on 2013-04-14
Up Please.

---

### Post by cariboo on 2013-04-14
Do you have a gui installed on your server?

---

### Post by RaJiska on 2013-04-15
> **cariboo907 said:**
> Do you have a gui installed on your server?

Yes, I It's perfectly working when I connect with the VNC X2GO.

---

### Post by CharlesA on 2013-04-15
It's probably because webmin doesn't run things the same way as you would run something via SSH.

I don't use webmin anymore, but that is likely the problem.

Run this from both webmin and SSH and see if there is any difference:

```
sudo echo $DISPLAY
```

---

### Post by RaJiska on 2013-04-15
> **CharlesA said:**
> It's probably because webmin doesn't run things the same way as you would run something via SSH.

I don't use webmin anymore, but that is likely the problem.

Run this from both webmin and SSH and see if there is any difference:

```
sudo echo $DISPLAY
```

I had the same problem from a PHP code, that's why I decided to move to Webmin, cause I thought I was a ****** dev.
But then, I've the same error on Linux.

I don't think it comes from Display since the xclock perfectly works from X2GO, but when I change the DISPLAY, it doesn't work.
My DISPLAY = :50.0

Thanks for your replys.

EDIT: More Informations:

First time I launched a server with Wine as desktop, here is what I got:
> 
wine: created the configuration directory '/root/.wine' Application tried to create a window, but no driver could be loaded. Make sure that your X server is running and that $DISPLAY is set correctly. err:systray:initialize_systray Could not create tray window Application tried to create a window, but no driver could be loaded. Make sure that your X server is running and that $DISPLAY is set correctly. Application tried to create a window, but no driver could be loaded. Make sure that your X server is running and that $DISPLAY is set correctly. Application tried to create a window, but no driver could be loaded. Make sure that your X server is running and that $DISPLAY is set correctly. fixme:storage:create_storagefile Storage share mode not implemented. err:mscoree:LoadLibraryShim error reading registry key for installroot err:mscoree:LoadLibraryShim error reading registry key for installroot err:mscoree:LoadLibraryShim error reading registry key for installroot err:mscoree:LoadLibraryShim error reading registry key for installroot err:mscoree:LoadLibraryShim error reading registry key for installroot err:mscoree:LoadLibraryShim error reading registry key for installroot fixme:seh:RtlAddFunctionTable 0x61e45620 1 61e40000: stub fixme:seh:RtlAddFunctionTable 0x61776ba0 1 61700000: stub fixme:seh:RtlAddFunctionTable 0x64f69540 1 64f40000: stub fixme:seh:RtlAddFunctionTable 0x622c6620 1 622c0000: stub fixme:seh:RtlAddFunctionTable 0x6ce47620 1 6ce40000: stub fixme:seh:RtlAddFunctionTable 0x682d4b20 1 682c0000: stub fixme:seh:RtlAddFunctionTable 0x638d1dc0 1 63800000: stub fixme:seh:RtlAddFunctionTable 0x3b6ea0 1 390000: stub fixme:seh:RtlAddFunctionTable 0x68f5b6a0 1 68f40000: stub fixme:seh:RtlAddFunctionTable 0x6b431bc0 1 69c40000: stub fixme:iphlpapi:NotifyAddrChange (Handle 0xd9e2f8, overlapped 0xd9e2c0): stub Application tried to create a window, but no driver could be loaded. Make sure that your X server is running and that $DISPLAY is set correctly. p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory fixme:storage:create_storagefile Storage share mode not implemented. err:mscoree:LoadLibraryShim error reading registry key for installroot err:mscoree:LoadLibraryShim error reading registry key for installroot err:mscoree:LoadLibraryShim error reading registry key for installroot err:mscoree:LoadLibraryShim error reading registry key for installroot err:mscoree:LoadLibraryShim error reading registry key for installroot err:mscoree:LoadLibraryShim error reading registry key for installroot fixme:iphlpapi:NotifyAddrChange (Handle 0xe6e8cc, overlapped 0xe6e8b0): stub p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory wine: configuration in '/root/.wine' has been updated. Error opening terminal: unknown.

Then, I do a CTRL + C and relaunch it and I've this error that appears messed up on my Terminal, BUT the server launch itself anyway:

```

Error opening terminal: unknown. Application tried to create a window, but no driver could be loaded. Make sure that your X server is running and that $DISPLAY is set correctly. err:systray:initialize_systray Could not create tray window

```

Screenshot: [http://img15.hostingpics.net/pics/642268Sanstitre.png](http://img15.hostingpics.net/pics/642268Sanstitre.png)

It ONLY hapens when I launch it with screen.

EDIT Of The EDIT:

More Informations on X Server.

I launched with VNC startx, and it said:

> Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log

I deleted the .X0-lock, and when I do a new sudo startx, I've it:

> desktop@ks353658:~$ sudo startx
xauth:  error in locking authority file /home/desktop/.Xauthority
xauth:  error in locking authority file /home/desktop/.Xauthority
xauth:  error in locking authority file /home/desktop/.Xauthority
xauth:  error in locking authority file /home/desktop/.Xauthority

_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
Server terminated with error (1). Closing log file.

That looks like to be a port problem, isn't it ?

---

### Post by CharlesA on 2013-04-15
Is there a reason you need to run that command with sudo? That might be part of the problem.

---

### Post by RaJiska on 2013-04-15
> **CharlesA said:**
> Is there a reason you need to run that command with sudo? That might be part of the problem.

You mean the startx ? yes, because I'm connected as desktop, if I don't do sudo, it throws me back:

```
xauth:  /home/desktop/.Xauthority not writable, changes will be ignored
xauth:  error in locking authority file /home/desktop/.Xauthority
xauth:  error in locking authority file /home/desktop/.Xauthority
xauth:  error in locking authority file /home/desktop/.Xauthority

X: user not authorized to run the X server, aborting.
```

I also tried with user root without sudo, but same problem as desktop + sudo.

I also would like to add that the command:

> gnome-terminal -x sh -c "ls"

Perfectly works with X2Go, is that a problem with ports ?
It works in local but not from website.

It looks like it try to do it with GUI things on SSH thingy.

Thanks.

---

