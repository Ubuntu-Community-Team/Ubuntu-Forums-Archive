---
title: "Hyper-V Automatic Stop Action"
date: 2021-11-16
forum: Virtualisation
---

### Post by Marc-NJ on 2021-11-16
In Hyper-V, under Settings -> Automatic Stop Action, it states the following under "Shut down the guest operating system" : The integration service that controls shutting down the guest operating system must be installed and enabled on the virtual machine.  


I have Ubuntu Server 20.04 LTS installed, and am wondering if Windows and Hyper-V will gracefully shut down the Ubuntu Server VM whenever I shut down / reboot Windows, or if this functionality doesn't exist for an Ubuntu VM running under Hyper-V.  


And any way to check that the shutdown was graceful on Ubuntu Server?


Thanks!

---

### Post by MAFoElffen on 2021-11-16
It means a few things and there are pre-req's for it to happen.

The VM (whether WIN based or Linux Based) needs to be "Generation 2", and have integration services enabled...

Once enabled, if you select Automatic Stop, you have to select one of three options... 

> 

[LIST]
[*]**Save The Virtual Machine State****:**  This saves the VM Machine state. 
[*]**Turn Off The Virtual Machine****:**  This is equivalent to a forced stop, an/or pulling the plug on the virtual machine. No state  information is saved. 
[*]**Shutdown The Guest Operating System****:** The guest OS of the virtual machine will be gracefully shut down when before the host will be shut down. No state is saved. 
[/LIST]

For #1 to happen, it has to have disk space to save the machines states to...

For #3 to happen, it will take the time to shut down any VM with this status... Just as if you had shut down the OS and quit each VM sessions set this way.

---

### Post by Marc-NJ on 2021-11-16
How do I tell if Ubuntu Server 20.04 is Type 1 or Type 2?  I thought hypervisors were classified as Type 1 or 2, but didn't realize guest OS's were also classified in this manner.

And I'm aiming for "Shutdown The Guest Operating System" - but want to make sure this is a graceful shutdown, and since it states an integration service is required, I'm not sure how to determine if Hyper-V is gracefully shutting down the Ubuntu Server guest OS on a shutdown of the physical Windows system.

Thanks.

---

### Post by MAFoElffen on 2021-11-16
I should reword and edit my first post... as a Hyper-V VM, as an installation type, "Generation 1" or "Generation 2" have diffrent capabilities as a Hyper-V VM. It needs to be installed as Generation 2...

---

### Post by Marc-NJ on 2021-11-16
Yup - it is installed as Generation 2.  But is there any way to confirm that Hyper-V is sending a graceful shut down command to the Ubuntu Server guest OS when the physical Windows box reboots?  Thanks!

---

### Post by MAFoElffen on 2021-11-17
When you shutdown and reboot, there will be a message in the blue shutdown screen notifying that it is closing down the Hyper-V service, and it will take a while to do so. It will not start the VM on startup unless you also pick/select Auto Start for those VM's.

On the start/restart, then check the system logs, and you will see the system had received the message to shut down, then see the Hyper-V VM's shut down. (The VM's that are selected/configured to Auto Stop). Note that each VM is selected and configured individually. You can configure them manually, or via PowerShell. 

I had PowerShell Scripts that I wrote, where I could configure multiple VM's at the same time, that made things easier, and faster to manage. All my scripts were digitally signed by our local CA. All my remote nodes were Win10 VM's with connections from the outside via VPN. All those I had set as Auto Stop: Shutdown, "and" Auto Start. I also had system shutdown scripts on those VM's using the System account, that notified all users of those VM's, that those VM's were going to be shutdown... I was very wary of making sure that I was giving ample time when it meant that those affected were dealing with financials. I also had shutdown scripts written for my Linux VM guests, that did the same on shutdown. I felt it was just an extra bit of a safety net for the just in cases...

On shutdown scripts... If mission critical, I recommend to customers and try to do the same for VM guests in KVM. It just makes sense to me. Sometimes things happen.

I learned the hard way... Just because the "system" shut's down gracefully, doesn't mean that there wasn't users on that system that had a chance to save and close down their files before that VM system shutdown. That is why I went a step further to write system shutdown scripts.

---

