---
title: "Ubuntu Server and LTSP Server"
date: 2013-11-21
forum: Server Platforms
---

### Post by amlwwalker2 on 2013-11-21
Hello everyone,
I have tried to not use the forums yet and find the answer through searching, but I am not stuck. I have been for about 4 days, and I cannot seem to make any headway.
I bought a small HP Proliant server and installed ubuntu server on it. I have had to learn linux for work and so thought this would be a good way to learn fast.
I have a raspberry pi, and wanted to try and setup a thin client server on my ubuntu server. Fine. I followed the two pages of instructions here:
[http://www.havetheknowhow.com/Configure-the-server/Install-LTSP.html](http://www.havetheknowhow.com/Configure-the-server/Install-LTSP.html)
 and installed the berryboot raspberry pi stuff on the SD card. All going well. When I start the rPi it finds the server and I login, however no desktop is displayed. I have the option of choosing a session which I presume is the desktop - much like on an Ubuntu desktop. Howver ubuntu, and gnome, the two Ive installed in the LTSP area of my server are not options. When I select Default, I get an error "Could not find the desktop GNOME", Logout? When I choose the other session option, Failsafe, I get a much longer error:
Xsession: unable to launch "/usr/bin/xterm" X session --- "/usr/bin/xterm" not found; falling back to default session.

This made me think that the problem might be because Ubuntu server has no software to "serve up" the desktop to the thin client. Can anyone decipher what the problem is there - and whether its to do with the actual ubuntu server install, or the LTSP install on the server. I.e if I had installed the LTSP server on an Ubuntu desktop edition would it have had the correct software to server up a desktop?

Thanks
ALex

---

### Post by ian-weisser on 2013-11-21
Your title says "Ubuntu Server".
Did you install Ubuntu or Ubuntu Server? One includes X, then other does not and is command-line-only.
Though, of course, you can easily add X to Server, and remove X from Desktop.

FYI: LTSP is included with Edubuntu.

---

