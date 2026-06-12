---
title: "TWiki 4 on Ubuntu 6.06"
date: 2006-06-14
forum: Server Platforms
---

### Post by AllBuntu on 2006-06-14
I want to run twiki 4.0.2 on Ubuntu 6.06LTS with Apache2. I have twiki-Cairo running already with Apache2, SSL, digest.

Upgraded to 6.06LTS to see if there was a newer TWiki: NO?!
Still the one from 2004...

1. Is there a way to find a package to twiki >= 4.0 ([http://twiki.org](http://twiki.org)) that I can load onto my Ubuntu?
2. if there is not case 1, I might be able to make one night-owling. If I do, can I contribute my fancy package somewhere?
3. If there is not case 2, I was thinking of uninstalling the ancient-twiki, retaining the depending packages, then just copying files out of the downloadable twiki 4.0.2 to the same locations, hope it works and never install Ubuntu-twiki again. Is this likely to be feasible?

My level is a skilled now-nothing.

-Harry

---

### Post by begkev5 on 2006-07-19
Hi Harry,

Easiest way to get Twiki 4 running is to do the following:

1. Install VmWare Player or Server ([free]("http://www.vmware.com/products/free_virtualization.html") - from Vmware.com)
2. Download the Twiki VmWare appliance and run it in the virtual machine 
([free]("http://www.vmware.com/vmtn/appliances/directory/53") - from VwWare.com)
3. Configuration / more info [here]("http://twiki.org/cgi-bin/view/Codev/TWikiVMDebianStable")

Good luck.

---

### Post by az on 2006-07-19
It seems pretty simple to install it from upstream.  I figure that is more advasable since you can better keep up with security updates.

A server core with a long release cycle is desirable, but that does not mean that you should stick with the same verison of your web application throughout the cycle.  Probably it's best to use and update your web application yourself.

---

### Post by tjb4u on 2006-07-31
If anyone is interested I have posted some instructions on how to get TWiki up and running on Ubuntu Server. Being a Linux newbie I struggled for a while to get it up and thought others might be interested in a more detailed instructions on how to do the same:
[LIST]
[*][ HOWTO: Install TWiki 4.0.4 on Ubuntu Server 6.06 LTS]("http://ubuntuforums.org/showthread.php?t=219213")
[/LIST]

---

