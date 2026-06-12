---
title: "How to VNC to Ubuntu Server when not logged in"
date: 2010-07-28
forum: Server Platforms
---

### Post by pittmantechno on 2010-07-28
hello Smart People ! 

This may sound like a silly question, but I have a few Ubuntu server's that are Headless, and rather than walking to the server room with a display i thought, id rather push for a good challenge..

So I would like to know how to remotely login to these Server's Desktop environments. not necessarily with more than one user at a time. just need to login to the machine's via VNC or RDC preferably VNC I do my admin work with Apple Remote Desktop. but I have RDC as well..

I set these systems up for my IT Department... and I need them to be super easy to access for the rest of my team. ( I am the only one aside from or Director privy to using the command line ) 

so in order to make it possible for normal humans - I'm installing the desktop enjoyment on each of them now. but....

From what I have found in my previous Linux adventures - it is not possible to VNC to system that is not already logged in, in other words if the machine is booted, but at the login window.. I have never been able to connect via VNC, I am only able to do this once the machine is physically logged in to it's desktop environment once that has happened I am able to connect with VNC, but,, something tells me this is possible - this is something I do on a regular basis with my OSX server's - and with RDC to manage my active directory server.

If panic instates and I am forced to reboot a machine from across the globe - Id like my team to able to connect to these systems without traipsing through the server rooms with displays =)

---

### Post by CharlesA on 2010-07-28
You cannot use the default vnc server that cames with Ubuntu Desktop, since it won't start until you login.

Use something like tightvncserver, SSH in then start the server and connect that way.

---

### Post by YesWeCan on 2010-07-28
tightvncserver is what you want. I use this to remotely administer a server.

The idea is that the Ubuntu machine can spawn any number of desktop instances. VNC exports them at port 590n where n is the desktop number. The one that actually appears on the local display is number 0. The "remote desktop" application (aka Vino) only exports desktop 0 at port 5900. Tightvncserver will create and export as many other desktops as you like, starting at 5901. In either case you can use the desktop on a client running a vnc viewer like Vinagre.

To use Vino you have to be logged in at the local console or a desktop 0 will not exist. To use tightvncserver desktops you need to be logged in remotely or at the local console.

---

