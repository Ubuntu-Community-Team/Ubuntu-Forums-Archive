---
title: "SSH connection timed out"
date: 2009-04-11
forum: Server Platforms
---

### Post by faustism on 2009-04-11
I set up openssh on my xubuntu computer and i am trying to connect to it from another computer on the same network with PuTTY.  It connects fine when i use the private IP address or the hostname, but gives me a "connection timed out" error message when i use the network's address (I have the NAT set up so that it forwards everything on port 22 to the SSH server.  I set this up for VNC(the port forwarding worked) so I'm pretty sure i didnt mess this up)

Any ideas/comments/suggestions?

---

### Post by HermanAB on 2009-04-11
Howdy,

There are a number of ways to debug connectivity issues.  One way is with telnet:
$ telnet user@server 22

You should get a SSH banner.

Or enable SSH debug messages:
$ ssh -vvv user@server

That should give you some clues.

---

### Post by faustism on 2009-04-11
i am using PuTTY (portable) on the other machine because it is running windows :( .

I tried a couple of more times to connect, and one time it did actually work.  I didnt change any settings and tried to connect again and it didnt work again. "Network Error: Session Timed Out"

Does this mean that it's Putty's problem?  I'm thinking that Putty has a timeout built in that i dont know how to change.  Or does the ssh server has a timeout to change?

I have no trouble connecting to that ip address from my xubuntu computer (the one running the ssh server)

I got nothing new when i ran ssh with the "-vvv" and telnet would not run.  In ran telnet form command line on the windows computer and it just said it couldn't make the connection.

Thanks for your help btw

---

