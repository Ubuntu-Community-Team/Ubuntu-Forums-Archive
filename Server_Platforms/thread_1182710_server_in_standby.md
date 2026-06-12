---
title: "server in standby"
date: 2009-06-09
forum: Server Platforms
---

### Post by exile501 on 2009-06-09
I am new to ubuntu and this is my first Server project so I am not sure if this is the right place to post these questions if not I am sorry.
(1)I know that you can have ubuntu and windows on one hard drive and select what one to use at start up, however I have two hard drives and I am curious to know if I can have ubuntu on one and windows on another and select on start up.
(2)I have a MDT [www.mdtglobal.com](www.mdtglobal.com) MD02500-BQDW hard drive that can power up in standby I would like to know if this means people can access the hard drive from the network with the computer just in standby thank you.

---

### Post by tgalati4 on 2009-06-09
Server version is missing the standby/resume scripts.  Use the desktop version instead.

---

### Post by exile501 on 2009-06-09
Thank you for the information that will help a lot:D, but I must admit I need to know whether I can have ubuntu on one hard drive and windows on the other and still chose what to use on start up before I can begin installation. OH one more question can I switch between windows and ubuntu while the computer is turned on?:-k

---

### Post by v3xtra on 2009-06-09
Yes, you can have Windows on one Hard drive and Ubuntu on another, it is called Dual Booting and there are tons of tutotials on the web about it!  Just make sure to install Windows first, and then Ubuntu, so that Ubuntu will recognize Windows and be able to dual boot it.

And no, it is not possible while it is turned on, you must reset your computer and switch operating systems.

---

### Post by HermanAB on 2009-06-09
Yes, it is possible to switch OS while turned on - sort of...

The trick is to install Virtualbox on Ubuntu and configure it to run Windows off the other disk, then you can run Windows in a window, where it belongs.  

See the virtualization forum for details.

---

