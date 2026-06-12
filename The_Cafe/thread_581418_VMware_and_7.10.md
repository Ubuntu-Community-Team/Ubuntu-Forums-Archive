---
title: "VMware and 7.10"
date: 2007-10-19
forum: The Cafe
---

### Post by Black Mage on 2007-10-19
Has anyone experienced a problem with running VMware in 7.10? When I try to power on a machine, it exits with an error.

```

Unable to change virtual machine power state: The process exited with an error:
End of error message.

```

---

### Post by tpearson@alltel.net on 2007-10-19
Since the last update of Gusty last week I have been having similar problem.

I click on player and it begins to load and disappears.  I have been having to rerun vmware-configure.pl  everytime i reboot my machine.  I have not tried to stop machine and start back up in same session.

---

### Post by tilapia on 2007-10-19
I have the same problem. I think I read somewhere here yesterday that the vmware kernel module isn't yet available for certain kernels. I'm running 2.6.22-14-generic #1 SMP and when I do an apt-cache search for vmware I only get the 2.6.20 kernel modules listed as available. 

Can anyone confirm or deny if I am barking up the wrong tree?

---

### Post by Black Mage on 2007-10-19
But do you atleast get yours to work though?

And what command is vmware-configure.pl?

---

### Post by tilapia on 2007-10-19
I had Vmware Server already installed. The console starts up fine, but when I try to fire up a vm I get the message "Unable to change virtual machine power state: The process exited with an error. End of message."

If you go to Advanced  and then Enable debugging information you get a more detailed message which says this is because it could not open /dev/vmmon. Make sure the kernel module vmmon is loaded. 

That's what makes me believe that this is kernel related. Is it possible to reinstall then? Anyone got Vmware Server working at yet?

---

### Post by tilapia on 2007-10-19
> VMWare server is not available right now.

See here: [http://ubuntuforums.org/showthread.php?t=579347&highlight=vmware+gutsy](http://ubuntuforums.org/showthread.php?t=579347&highlight=vmware+gutsy)

---

### Post by Black Mage on 2007-10-22
> **tilapia said:**
> I had Vmware Server already installed. The console starts up fine, but when I try to fire up a vm I get the message "Unable to change virtual machine power state: The process exited with an error. End of message."

If you go to Advanced  and then Enable debugging information you get a more detailed message which says this is because it could not open /dev/vmmon. Make sure the kernel module vmmon is loaded. 

That's what makes me believe that this is kernel related. Is it possible to reinstall then? Anyone got Vmware Server working at yet?

Yea, that is what it said. So how do Ioad the vmmon module?

---

