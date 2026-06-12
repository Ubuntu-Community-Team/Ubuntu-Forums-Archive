---
title: "How do I run VMware Server on 7.10 server?"
date: 2007-12-15
forum: Virtualisation
---

### Post by tuproxy on 2007-12-15
I just bought a nice dual core system and plan on running the 64 bit 7.10 Server distro on it.  I have been able to install VMware server on previous desktop versions of Ubuntu and Server, but have not been able to get to the GUI of VMware when it was installed on my Edgy server.

So what I mean is the 7.10 server has no GUI, so is it possible to get to the graphical screen of VMware when it is running on the server OS?  Is it better to just install it on the Desktop distro and add the server features?

I'm just getting back into Linux and plan to make this my final transition.  I want to run XP as a Virtual machine.

Any suggestions on how to make this transition as smooth as possible?

Thanks :)

---

### Post by hermandy on 2008-01-04
I had the same issue i ended up doing the desktop install to get the GUI 

sudo apt-get install ubuntu-desktop

startx

the GUI is under system tools.  I found this to be my only option, I tried for a few hours to get an image to load from the command line.

---

### Post by arosenau on 2008-01-04
Vmware has the vmare web interface that can be installed. And you can can also install the vmware console on a remote machine and connect to the vmware server. This allows you to run the vmware server without the overhead of a GUI.

---

### Post by koenn on 2008-01-05
> **arosenau said:**
>  you can can also install the vmware console on a remote machine and connect to the vmware server. This allows you to run the vmware server without the overhead of a GUI.

Have you done that ? Did it work ? 

I'm running VMware Server on a server and wanted the console on my desktop, but I couldn't get the console to work correctly when installed from either the VMware tarball or the rpm package (converted to deb with alien). 

You can get the console installed  from the **server** tarball, so I installed the server package on my desktop, disabled vmware server by removing /etc/init.d/vmware, and use the console to connect to the remote server. That works very well. 

I found some notes in forums where people have similar problems, the fix has to do with copying files over from the server to the client. You'll also see that the client package fails to install menu items, while the server package does just that. Clearly there are some bugs in the vmware linux client install script - as if it"s not meant to be installed separately - kinda silly.

---

