---
title: "Linking Several OS via Ubuntu Server"
date: 2010-09-12
forum: Server Platforms
---

### Post by ibrrfarr on 2010-09-12
I am currently finalizing a SSH Tunnel (gSTM) via Ubuntu Server (see:  [this%20thread"]]("http://ubuntuforums.org/showthread.php?t=1567503)[http://ubuntuforums.org/showthread.php?t=1567503](http://ubuntuforums.org/showthread.php?t=1567503)).  The gentleman who helped me there went *above and beyond* the call of duty as we used to say in the military.  Accordingly, I wanted to start a new thread to explore options to the pending completion.

So, several systems in play here.  I will list two of the three with the presumption that the SSH situation is in play (testing it today from outside of my network). 

Systems Currently in Play:  Ubuntu 10.04 Desktop Edition with all updates as of today's  post:  Server:  Acer Aspire AST180-400A. It is currently being accessed from  Ubuntu 10.04 Desktop Edition with all updates as of today's post from a  laptop:  Toshiba Satellite A200.  Router:  Netgear N300 WNR 2000v2.  Modem is Motorola Netopia 2210-02-1006.

Proposed System To Add:  eMachine ET1331G-05w running Windows 7.  Why?  Well, my girlfriend is *terrified *to ditch the Bill Hates way of things.  :)  It is running through the router currently as well.

What I would like to be able to do is access the Windows 7 desktop via my laptop on the road as well.  Specifically, I need to be able to access and view documents and photos.  Now, the docs are at least in OpenOffice; she switched to it finally.  :)  I would like to also be able to view my desktop to access docs and pictures on the server, but that may be a new thread as the Win7 situation is the _priority_ right now.

I thank all of you for helping me along; it is *really *refreshing to be a part of a forum where you *actually* get help instead of the run around! ):P

---

### Post by Bachstelze on 2010-09-12
If it is XP Pro, you can activate the built-in remote desktop thing and access if from Ubuntu with rdesktop.

---

### Post by ibrrfarr on 2010-09-12
> **Bachstelze said:**
> If it is XP Pro, you can activate the built-in remote desktop thing and access if from Ubuntu with rdesktop.

It's Windows 7.  All accessing will be from the Ubuntu laptop.

---

### Post by BobVila on 2010-09-14
Depending on the version of Win7, you can still RDP into the machine. You'll need to do the following on the windows box:

Right-click Computer, click Properties
Click Remote Settings in the left pane
Under the Remote Desktop heading, select the middle option

That'll allow you to use Terminal Server Client on your Ubuntu box to connect to the Win7 desktop internally. 

To make this work remotely, you'll need to forward port 3389 on your router to the IP address of the Windows box. Note that doing so does expose the RDP service to the internet. You'll be able to remotely log in, but anyone on the internet will be able to try as well. Make sure you've got a strong password on the box.

If you don't need to remotely control the Windows box from the internet, don't do the above - instead, I'd forward port 22 to one of your linux boxes so you can SSH into your home network. You can then access the windows machine via samba to get to docs, etc. Adds a little bit of complexity, but I'd rather ssh in than go over rdp.

---

