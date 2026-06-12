---
title: "Security threat or false alarm"
date: 2009-12-10
forum: Security
---

### Post by bluntknife on 2009-12-10
Hi,
I've just been using my Ubuntu 9.10 desktop and the attached message popped up in front of me.  I'd like to point out that I'm on my home network behind a DrayTek firewall router so I wouldn't have though external connection attempts should be getting as far as my desktop machine. 

Is it anything to worry about?

---

### Post by bodhi.zazen on 2009-12-10
Sure is. First, why are you running a VNC server ? Second, why is your router not firewalling that request ?

Turn off your VNC server until you can firewall that connection.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

### Post by bluntknife on 2009-12-10
Thanks for your quick response.  I did switch that machine off shortly after the message was displayed.

I've never installed vnc server but I have installed mythtv frontend this afternoon. Could it have installed automatically with that package?

Regards.

---

### Post by bodhi.zazen on 2009-12-10
My guess is that it is vino, or desktop sharing ?

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

---

