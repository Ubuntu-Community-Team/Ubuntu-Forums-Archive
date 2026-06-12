---
title: "Can't connect to VRDP of a headless machine"
date: 2011-03-01
forum: Virtualisation
---

### Post by uberkraffs on 2011-03-01
Hi, 

I'm having difficulties connecting to my virtual machine. 

When installing, I followed the steps found at:[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-3.1-on-a-headless-ubuntu-9.10-server]("http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-3.1-on-a-headless-ubuntu-9.10-server") and [http://www.virtualbox.org/manual/ch07.html#vboxheadless]("http://www.virtualbox.org/manual/ch07.html#vboxheadless")

But when I start the machine using WBoxHeadless --startvm "WinXP" (my machine) the console displays the copyright notice and then just stops and blinks. Is the machine really running or has something gone wrong? And how do I tell.

In the beginning I thought it was supposed to be like that, but then I couldn't connect to the machine using RDP. Exactly what address am I supposed to use? The server address or the bridge? 

As you might notice, I'm rather new to VirtualBox. :)

Hope someone can help! 

Thanks,

---

### Post by uberkraffs on 2011-03-01
Never mind, installing the VirtualBox extension pack containing VRDP is a good idea before posting dumb questions. :oops:

---

### Post by jdpipe on 2011-03-08
My understanding is that before VirtualBox 4.x, the VRDP component was only available in the non-open-source version. 

Where did you get this VRDP component, in order to solve your problem? Which version of VirtualBox have you installed (and what version of Ubuntu?)

---

