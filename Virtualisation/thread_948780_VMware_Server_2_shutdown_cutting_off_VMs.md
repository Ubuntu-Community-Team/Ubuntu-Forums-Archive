---
title: "VMware Server 2 shutdown cutting off VMs"
date: 2008-10-15
forum: Virtualisation
---

### Post by mastakebob on 2008-10-15
I'm running VMware Server 2 on Ubuntu 8.04.1 (64 bit).  I'm trying to make it so when I hit the shutdown button (in Gnome, not the hardware power button), Ubuntu waits until VMware Server 2 has completed suspending all running VMs before Ubuntu shuts down.  VMware is set to suspend any running VMs when the host OS begins shutting down.  However, Ubuntu shuts down faster than VMware Server can suspend the guest OSs, which causes the guests to be abruptly shutdown in the middle of suspending.  This causes them to act all flaky the next time they're booted.  Is there any way to force Ubuntu to wait until VMware has finished running before continuing to shutdown?

---

### Post by bodhi.zazen on 2008-10-15
You may wish to write a script. Shutdown VMWare -> sleep -> shutdown ubuntu.

---

### Post by edmondt on 2008-10-15
Check the script on this thread it has what you are looking for like waiting for the VM to shutdown before shutting down the system:

[http://ubuntuforums.org/showthread.php?t=939183](http://ubuntuforums.org/showthread.php?t=939183)

---

### Post by mastakebob on 2008-10-16
Hmmmmm, thanks, but that looks like it was developed for VirtualBox, so I'm guessing it's probably not going to work for VMware Server?

---

### Post by bodhi.zazen on 2008-10-16
> **mastakebob said:**
> Hmmmmm, thanks, but that looks like it was developed for VirtualBox, so I'm guessing it's probably not going to work for VMware Server?

You will have to look at the VMWare server commands and determine the shutdown command (I do not know it off the top of my head). Then write a simple "wrapper" script

```
#!/bin/bash
vmware_shutdown # I do not know this command

# You may not need a sleep depending on how the vmware command works
sleep 30 # you an increase or decrease the sleep

shutdown -h now
```

[http://ubuntuforums.org/showthread.php?t=594561](http://ubuntuforums.org/showthread.php?t=594561)

[http://209.85.173.104/search?q=cache:NDC7btjt6uoJ:download3.vmware.com/vmworld/2006/dvt4696.pdf+vmware+server+commands&hl=en&ct=clnk&cd=2&gl=us&client=firefox-a](http://209.85.173.104/search?q=cache:NDC7btjt6uoJ:download3.vmware.com/vmworld/2006/dvt4696.pdf+vmware+server+commands&hl=en&ct=clnk&cd=2&gl=us&client=firefox-a)

[http://articles.techrepublic.com.com/5100-10878_11-6079860.html](http://articles.techrepublic.com.com/5100-10878_11-6079860.html)

---

### Post by mastakebob on 2008-10-16
OK, assuming I get that working, this won't run unless the user specifically uses the custom shutdown script.  Is there a way to inject this capability into the default shutdown procedure?  
The issue is that this server is being installed at another installation and I need it to be as user friendly as possible (and having them shutdown with a script instead of the big friendly "shutdown" button isn't too user friendly).  
I'm not trying to sound ungrateful, you've been very helpful and I appreciate it.

---

### Post by bodhi.zazen on 2008-10-16
Easiest would be to go ahead and write the script and then make a launcher in the users menu or on the panel to replace the shutdown button. You can customize the icon to use any icon you wish, including the shutdown button :twisted:

---

