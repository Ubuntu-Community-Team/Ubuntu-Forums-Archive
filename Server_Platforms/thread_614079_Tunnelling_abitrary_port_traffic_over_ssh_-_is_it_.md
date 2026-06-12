---
title: "Tunnelling abitrary port traffic over ssh - is it possible?"
date: 2007-11-15
forum: Server Platforms
---

### Post by sammydee on 2007-11-15
Hi all.

I discovered openssh about six months ago and it still seems to me to actually be magic.

I've spent hours on my laptop over wireless making the cdrom tray on my server open and close, playing music on the server hardware through speakers connected to the server with amarok displayed on my laptop screen, streaming live movies from my 250gig hard disk on the server to my laptop using sshfs etc etc.

As far as I'm concerned, ssh is THE coolest thing that linux has that windows doesn't (or doesn't have very well, I know about cygwin etc.)

Anyway to the point - I want to remotely administer azureus over ssh. There are two ways I can do this. One is to use vnc over ssh to log on to my server's current x session and open azureus there. Unfortunately this is complicated I can't seem to get vnc to work properly no matter what I do.

The other option is azureus' web ui. It uses javascript and html and it's got everything I need. I don't trust it's security however, and as far as I'm concerned, the less ports I have to open in the firewall, the better. I want to tunnel this mini web server over ssh to my laptop, so I can connect from a firefox session on my laptop to the web ui of azureus on the server tunnelled over ssh.

So it's very similar to tunnelling, say, apache for example, over ssh. Any help?

Sam

---

### Post by HermanAB on 2007-11-15
SSH can tunnel any TCP traffic.

---

### Post by sammydee on 2007-11-15
Once again I am blown away by how magic ssh is.

All I needed to do was:

sudo ssh  -L 6886:localhost:6886 [email]myusername@xxx.xxx.xxx.xxx[/email]

And bingo! Any attempt to connect to 127.0.0.1 on port 6886 on the remote client results in a connection to the server on port 6886 even though the server is configured to only allow connections to the local host. Yay!

Sam

---

