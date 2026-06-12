---
title: "Problem Commissioning Nodes in MAAS"
date: 2014-11-08
forum: Ubuntu Cloud and Juju
---

### Post by linuxuser600 on 2014-11-08
I am trying out Ubuntu MAAS and am having some issues. I installed it using the Ubuntu Server boot media. Everything seems to work alright. I set up DHCP and DNS in the cluster interface. Then when I pxe boot a device it adds it to the nodes section. From there I click on the node and on the right hand side I click on commission node. I then go to the device and pxe boot it again. This essentially does the same thing as the original pxe boot and shuts down the node. Am I doing something wrong? Or is there some log files somewhere that I can see what is going on? Any ideas is appreciated.

I took a video of what is happening and uploaded it to youtube. Here is the link. [http://youtu.be/ahK7XFrOUuI](http://youtu.be/ahK7XFrOUuI)

---

### Post by alittlek on 2014-11-12
As far as I see in your video there is an exclamation mark at your node. Read the content on mouse over .... I assume that there is a problem with MAAS to communicate with node. As described here, chapter "Virtual machine nodes":

[http://maas.ubuntu.com/docs1.5/nodes.html](http://maas.ubuntu.com/docs1.5/nodes.html)

you need to config your node in MAAS to give MAAS access on the hardware capabilities (start, shutdown, etc.). There for you do not need to turn your node on by hand, MAAS is doing that for you if you click on 'Comission node'.

The guide give an example for KVM, so you need to google how to config it for virtualbox ....

---

### Post by linuxuser600 on 2014-11-12
The exclamation mark is just because my power type is not defined. This same thing happens with a real server also. It comes up with the same errors even with Wake on Lan set up. So you are saying that Commissioning nodes basically just receives the information of the nodes? If this is the case how does MAAS install the OS on the server? Sorry if these are stupid questions. I am new to MAAS and even after reading many articles about it I am still confused with what it actually is. Thank you for helping.

---

### Post by alittlek on 2014-11-13
In my understanding PXE boot is only to contact MAAS to get enlisted. As far as I figured out you must configure MAAS/node accordingly to get access to power functions working. If you succeed with that you will be able to commission nodes ....

In my environment I could also not commission nodes unless power type is configured to working properly....

---

