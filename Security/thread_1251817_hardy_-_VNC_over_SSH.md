---
title: "hardy - VNC over SSH"
date: 2009-08-28
forum: Security
---

### Post by shanep-server on 2009-08-28
I have a server running ubuntu hardy desktop and a laptop with xp. The server has ssh server which I can access from the xp laptop with putty. I'm confused how I go about using VNC with a ssh tunnel. I'm new too ubuntu, VNC, an SSH I know a great combo lol. I read I need to forward ports from VNC ( standard is 5900 ) an SSH is port 22. I don't really get what these ports are for. I thought I had to manually forward ports in my router so I guess I don't get where these ports ( 5900 + 22 ) are located... ( in my router? or my machines? ) I know VNC needs a gui interface to work with an SSH is console. So I have to open a tunnel from the SSH console? Then open VNC? Do I open the tunnel from the SSH server or from the SSH client on the xp machine? If someone can explain this better too me that would help. My google searches aren't really helping me out too much. I guess I don't get how the 2 programs VNC an SSH are working together and in what order.

---

### Post by movieman on 2009-08-28
Assuming that VNC on the remote machine is configured to run only on localhost and as VNC display 1:

In a terminal, run:
ssh -L locahost:5901:localhost:5901 remote-machine

Then start the VNC viewer and set it to connect to localhost:1. It will connect to port 5901 on that machine, and SSH will forward it to the VNC server on the remote machine.

Note that the VNC viewer will probably think the server is running on that machine and set it to maximum bandwidth operation, so you'll probably need to change some settings to reduce the amount of bandwidth it requires.

---

### Post by movieman on 2009-08-28
Oh, I just noticed you're running XP: in that case you probably want to run Putty or similar and configure it to forward local port 5901 to remote port 5901 in the GUI.

---

### Post by bodhi.zazen on 2009-08-28
Like this : [http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

---

