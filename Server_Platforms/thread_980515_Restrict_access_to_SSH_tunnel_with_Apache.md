---
title: "Restrict access to SSH tunnel with Apache?"
date: 2008-11-12
forum: Server Platforms
---

### Post by Pc_Madness on 2008-11-12
Hey guys, got abit of a tricky one.  We're working on a router like device with a web interface, and we want to be able to manage it remotely.  So we're setting up an SSH server to manage all of the connections and then the machines will automatically connect to the server on startup. Then I want to have a little password protected website on the server that will list all of these SSH connections and then you can view the interface on that machine using [http://sshserver:port/](http://sshserver:port/).  

The problem with this though is that the SSH is forwarding port 80 on the machine to a specific port on the ssh server, so it never goes near apache or php so I have no way of preventing users who aren't logged in from accessing the tunnels, or preventing users from trying to get into other users machines. 

Anyone have ideas on how I can add some security to this? The machines themselves have a login screen, but I'd very much prefer that those login screens weren't publicly available incase someone does manage to find an exploit.

The current solution is to have a tunnel that goes directly between the machines which basically says to turn on the web interface tunnel and a big disconnect button in the interface that will close then tunnel when its done, otherwise a timeout of say a few hours to play it safe.

We considered only sending the database over the tunnel, but then that means running multiple copies of the interface the SSH server plus I write files to the harddrive, which I won't be able to do over SSH which means I'll have to disable some sections which makes being able to remotely access it kinda pointless. :\

Hopefully that all made sense. :p

---

### Post by stelth-panther on 2008-11-13
You could just set up a VPN of sorts and just have everyone securely connect to that and then make the internal site viewable only on the network.

---

