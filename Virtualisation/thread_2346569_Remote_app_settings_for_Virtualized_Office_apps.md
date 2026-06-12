---
title: "Remote app settings for Virtualized Office apps"
date: 2016-12-16
forum: Virtualisation
---

### Post by manishanand001 on 2016-12-16
I'm running a windows virtual machine on 16.04 host to use MS Word (mendeley plugin does not work with wine). I've tried to setup remote access to the app but have failed to do so. 
Does Remmina allow you to remote access the app itself? There seems to be a setting in the advanced settings tab but it doesn't seem to work for me. It just remote accesses the entire desktop. Am I doing something wrong?(please see attached file). 
I have tried Winconn but that did not work either. In fact, after I try to access an app with winconn, not only does the app not open, I can no longer remote access the desktop either.
I can't figure out the rdp settings myself, i would greatly appreciate it if someone could point me in the right direction or help me figure out how to set it up. Thanks

---

### Post by TheFu on 2016-12-17
Can't help with Windows, but for remote Linux X/Windows applications, it is really easy.

$ ssh -X remote-userid@remote-server-IP "/path/to/program -options"

So ... to run libreoffice on "hadar" and have it display back on my local machine, I use:
```
$ ssh -X hadar loffice &
```
There are assumptions in that command.
* ssh has been setup to work between the 2 systems. It creates a secure tunnel between both systems.
* my userid on both systems is the same name (just the name, not the numbers)
* loffice is in the PATH on the remote system for my userid. If it wasn't, I'd need to put the entire path to the program in.
* the '&' detaches the program from my terminal, so it can be used for other things. The remote program still runs.
* my local machine must be running an X/Server ... that usually means Linux. Windows only has X/Servers if you add one one and configure it correctly. That is non-trivial.  Out of the box, any Linux desktop has X/Windows and is running an X/Server.
So ... without all those assumptions, the command becomes:
```
$ ssh -X thefu@hadar /usr/bin/loffice  &
```

Don't think rdp supports this. Sorry.  Remmina isn't just remote desktops for Windows. It is also remote access for other systems, like Linux applications.

---

