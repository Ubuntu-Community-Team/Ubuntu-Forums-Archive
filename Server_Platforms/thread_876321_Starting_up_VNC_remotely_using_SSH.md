---
title: "Starting up VNC remotely using SSH"
date: 2008-07-31
forum: Server Platforms
---

### Post by jmmL on 2008-07-31
To being with: I know there are a lot of other questions in the forums about starting up VNC remotely, however I either can't understand most of them, or they use messy work-arounds like autologin on the remote machine.

I've just set up a server using the ubuntu-server CD, and I also installed afterwards a very basic graphical environment. I can successfully log into the remote machine via SSH, but when i try to start X with "sudo startx" doesn't work.

Basically, the question is: "What is the easiest way to start up a VNC server using SSH?"

I'm sure there must be something I'm missing. Any help would be very much appreciated! (Ideally, the solution would be with vino and vinagre, as they seem to be the easiest-to-use VNC server and client I've come across.)

---

### Post by grandsatrap on 2008-07-31
I am using TightVNC on Ubuntu.
I ssh & login. Then I type "vncserver". This starts the VNC server and tells me if it is on port 1,2,3, ... (ie. 5901, 5902, ...). I could change the settings to fix it.
Then I can just VNC to the Ubuntu computer from the local end of the SSH connection (via tunnelling of course).

I remember having some problems that I needed to fix with the display.

---

