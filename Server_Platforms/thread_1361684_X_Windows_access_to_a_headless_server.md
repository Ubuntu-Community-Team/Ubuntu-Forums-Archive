---
title: "X Windows access to a headless server"
date: 2009-12-22
forum: Server Platforms
---

### Post by brewster8493 on 2009-12-22
Good Day - I have a Karmic server setup in console mode. Everything works fine and all LAMP services are available. The server runs as a headless appliance. I would like to be able to remotely access it via Xming in GUI mode as well. Is it possible to run X or Gnome as a service on a headless box for remote access? What Services would be required to do this? Thanks for your help!

Brewster

---

### Post by kpholmes on 2009-12-22
You can install a GUI if you want, and VNC in and view the desktop that way, but that is considered a security risk by some people.  If you only need to use a couple apps then you can forward the apps to the remote desktop through ssh known as x11 forwarding.  You mentioned lamp so I'm guessing it's a web server, what other processes do you plan to run?

---

### Post by BkkBonanza on 2009-12-22
I believe for running X remotely you need to install some components but not the full desktop. I have tried it with just ssh -X and you can run some X apps but I found to do much more you needed Gnome or equivalent. I know there are some good tutorials around so maybe google for that. It sounds like it's more light weight than doing VNC and since X is handled natively through ssh it is not a security problem. I think for a server it is more appropriate than VNC but so far I have only made a few tests and still do my admin by ssh. 

Probably the only thing I'd like to achieve by using a remote desktop is easier GUI based file editing. I achieved this by using sshfs - a ssh based file system that allows mounting remote directories into your local filesystem. Then any local tools will work with them.

Incidentally if you ssh in and "apt-get install gedit" (for example) it will show you what collection of dependencies it needs. I suspect that is pretty much what is needed for remote X as well.

PS. I know there are a few board members here who are keen users of X for remote server admin so hopefully one of them will drop notes here.

---

### Post by Tulth on 2009-12-22
I regularly use
```
ssh -X <ip> desktop.sh
```
where /home/<me>/desktop.sh (on the server) is something like
```
#!/bin/bash
sh /etc/X11/xinit/xinitrc
```

I did install full desktop though.  I'm not sure exactly what packages are required.

---

### Post by brewster8493 on 2009-12-22
Thanks for the replies. This is just my home test server. I typically test anything of interest and then reload it when I get it unstable enough...
I would just like to be able to access it via GUI and command line. I want to make sure it doesnt hang without a monitor.

Brewster

---

