---
title: "Xterming from windows into Ubuntu"
date: 2005-02-11
forum: Server Platforms
---

### Post by billputer on 2005-02-11
I have a Ubuntu server in my closet that I serve games and a few websites off of.  I also have a dual boot with Windows and Ubuntu as a desktop.  

Usually I either SSH into the server, or I boot Ubuntu and make it into an Xterminal into my server.  I'd like to be able to access my gnome desktop from Windows though.  What is a good way to accomplish this?

---

### Post by scoon on 2005-02-11
[QUOTE=billputer]I have a Ubuntu server in my closet that I serve games and a few websites off of.  I also have a dual boot with Windows and Ubuntu as a desktop.  

Usually I either SSH into the server, or I boot Ubuntu and make it into an Xterminal into my server.  I'd like to be able to access my gnome desktop from Windows though.  What is a good way to accomplish this?[/QUOTE]

Hey there, 

I think you may be interested in a winhell program called putty. 


scoon

---

### Post by spoetnik on 2005-02-11
Try VNC

---

### Post by mendicant on 2005-02-11
VNC is great, and you can always try cygwin, as well, for X under Windows.

---

### Post by rtz654 on 2005-02-14
There is a very nice X-Server called X-Deep/32 available as Freeware for Windows... [Homepage](http://www.pexus.com/) 

Just activate XDMCP in gdm and you are able to use your gnome desktop!!  \\:D/ 

But be aware of the security-risks you get with xdmcp, if you have to take care of security a lot use **freenx**. This is a terminal-server using ssh-tunneling, just go for the HowTo on freenx in this forum. By the way it has the best performance I ever saw on any terminal server  :wink:

---

### Post by Rottweiler on 2005-02-16
There is also NX and FreeNX.
   
   VNC is probably the easiest to set up and get running. Try: [http://www.tightvnc.com]("http://www.tightvnc.com") . vncserver is available in universe IIRC.
  
  Check back if you get stuck.

---

### Post by Zathras on 2005-05-31
I use the free Linux Terminal Server Client for Windows.  It's great.

You can get it here: [http://sourceforge.net/projects/linuxts/]("http://sourceforge.net/projects/linuxts/")

---

