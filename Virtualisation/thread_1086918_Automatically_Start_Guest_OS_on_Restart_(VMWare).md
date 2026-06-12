---
title: "Automatically Start Guest OS on Restart (VMWare)"
date: 2009-03-04
forum: Virtualisation
---

### Post by thornomad on 2009-03-04
Hi - is there a way I can automatically have my Guest OSes start when I restart my host server (running VMWare Server 2)?  

Or do I always have to log in via the web interface and do it manually ?

Thanks,
Damon

---

### Post by HermanAB on 2009-03-04
Look at the command 'vmrun' and put it in /etc/rc.d/rc.local.

Cheers,

Herman

---

### Post by veloce on 2009-03-04
> **thornomad said:**
> Hi - is there a way I can automatically have my Guest OSes start when I restart my host server (running VMWare Server 2)?  

Or do I always have to log in via the web interface and do it manually ?

Thanks,
Damon

In the web interface, in a pane on the right entitled "commands" is a command called "edit virtual machine startup/shutdown settings"

You can set up what vms should start up automatically, in what order, whether there should be a delay between them, how they should shutdown, ...

Much more flexible than v1.XX - one of the few areas where v2 is an improvement!

---

### Post by thornomad on 2009-03-04
Both great suggestions !  Thank you - the vmrun is the command line tool I was looking for ... and the web interface stuff is perfect.  I didn't poke around hard enough to find it under the "root" of the web interface -- kept search under the specific machine.

Terrific!  Off I go to conquer it all!

---

