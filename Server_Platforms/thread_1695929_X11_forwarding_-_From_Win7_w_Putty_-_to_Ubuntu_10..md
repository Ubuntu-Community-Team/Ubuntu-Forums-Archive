---
title: "X11 forwarding - From Win7 w/ Putty - to Ubuntu 10.10 server"
date: 2011-02-26
forum: Server Platforms
---

### Post by polarbar on 2011-02-26
Hi,
I have a server Ubuntu 10.10 and I installed gui xubuntu.  it is running fine.

From my client Win7 I can get a ssh session with Putty 0.60 in command line.  Now I would like to have with Putty 0.60 a gui session and I am looking for the solution  :D

I edited the file /etc/ssh/ssh_config and I activated those lines:
```
ForwardAgent yes
ForwardX11 yes
ForwardX11Trusted yes
```

then I edited the file /etc/ssh/sshd_config and I activated this line:
```
X11Forwarding yes
```

On Putty I can see there is a X11 forwarding configuration but I don't know much...

So the question is:
Can I launch a complete xubuntu desktop session using SSH via PuTTY?

If yes... How :)

---

### Post by egpetrich on 2011-02-27
The general answer to your question is, "Yes, you can launch a complete XUbuntu session using SSH via PuTTY." The details can be troublesome.

You need a remote desktop server running on your Ubuntu system, as well as a client viewer running on your Windows machine. Your first step is to decide which protocol you want to use for the connection. VNC has a long history (at least as far as this topic goes), but there are other options out there, such as NX technology:

[http://en.wikipedia.org/wiki/NX_technology](http://en.wikipedia.org/wiki/NX_technology)

We use VNC at my work, but you might find a snag. RealVNC (a commerical product) has a free VNC viewer, but only for Windows version before Vista. There may be other free viewers available, but I don't know anything about their current states.

For VNC, the general procedure is as follows:

[LIST]
[*]On your Ubuntu system, install a VNC server package (e.g. tightvncserver).
[*]From a login session (either local or via SSH) start a vncserver session running. (The command we use is "vncserver".)
[LIST]
[*]Getting the VNC server running correctly can be a challenge. On my machine, at least, the X startup file is "~/.vnc/xstartup", which is *not* the same file that runs if you start the X session locally with "startx".
[*]When the VNC server starts, it will give you the virtual desktop name that it has created (e.g. "mymachine:1"). You need to note this name in order to connect your client.
[/LIST]
[*]You can't see what the VNC server is sending unless/until you have a VNC client to connect to it. Once you have the VNC client installed, run it and give it the virtual desktop name above. (Ensure that you can do this on the local network before you try tunneling through SSH.)
[*]When you can connect to the VNC server over the local network, then you can try connecting through SSH. You need to create a forwarded port on your Windows machine to connect to the Ubuntu system. (I think that the "X11 Forwarding" option in PuTTY covers a different set of functions.)
[*]Under the "Tunnels" section, add a new forwarded port:
[LIST]
[*]Set the source port to "5901".
[*]Set the destination to the virtual desktop name above.
[*]Ensure that the "Local" radio button is selected.
[*]Click "Add".
[*]Save this profile (back in the "Session" section), so you don't have to do this every time.
[/LIST]
[*]When you log in via SSH, your local machine's port 5901 is mapped to the Ubuntu machines port controlling your virtual desktop.
[*]Now, when you open the VNC client on your Windows machine, you want to connect to "localhost:1". If all goes well, you'll be prompted for your password and then connected to the VNC desktop.
[/LIST]
Man, that explanation was complicated, wasn't it? I think that's because the topic is complicated. Maybe NX is easier to work with, but I don't know.

---

### Post by polarbar on 2011-03-06
Hi egpetrich,:D

Thanks you for this complete answer.  It is almost a manual how to do it!!!  I am sure it will help a lot of people.

---

