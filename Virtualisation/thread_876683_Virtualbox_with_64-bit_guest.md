---
title: "Virtualbox with 64-bit guest?"
date: 2008-08-01
forum: Virtualisation
---

### Post by scradock on 2008-08-01
Is it possible to get a 64-bit guest OS to run in Virtualbox on a 64-bit host (Ubuntu 8.04)? I find a deafening silence in the user manual and all the info pages about VB on the topic, and as it refuses to accept 64-bit guests on my amd64 machine, running on a 64-bit Ubuntu Hardy host, I am wondering if it is a limitation of the VB itself.

If so, I have to choose btw sticking to 64-bit purity and having 32-bit versions of OSs running in VB. Otherwise WinXP is the only 32-bit OS I have...

Any information available?

---

### Post by sonofusion82 on 2008-08-01
a quick googling gave me this:

[http://www.virtualbox.org/wiki/VBox_vs_Others](http://www.virtualbox.org/wiki/VBox_vs_Others)

in summary, nope, currently seems like only VMWare supports 64-bit guest

---

### Post by scradock on 2008-08-01
> **sonofusion82 said:**
> a quick googling gave me this:

[http://www.virtualbox.org/wiki/VBox_vs_Others](http://www.virtualbox.org/wiki/VBox_vs_Others)

in summary, nope, currently seems like only VMWare supports 64-bit guest

Thanks for the link - my googling didn't bring that one up!

---

### Post by blurpo on 2010-08-15
Just to update this information, current versions of VirtualBox (I believe starting v2.0 or v2.2 -- we are now at v3) do support 64-bit guests even on 32-bit hosts.

All you have to do when creating a new virtual machine is select a 64-bit version of the OS you want to use. 

My problem is I don't see any 64-bit versions of any OS - I just see Windows, Ubuntu, and so on. 

The VirtualBox manual says that to support  64-bit guests, you must enable hardware virtualization, which your CPU must support, of course. I have a lousy Intel Core 2 Duo T5800 (type "cat /proc/cpuinfo | grep name" to find out your model name). [According to Intel]("http://ark.intel.com/Product.aspx?id=35581&code=T5800") this CPU does support "Intel Virtualization Technology". Guess I'm screwed then, but the best of luck to the rest of you.

---

