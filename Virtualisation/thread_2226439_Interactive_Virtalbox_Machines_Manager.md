---
title: "Interactive Virtalbox Machines Manager"
date: 2014-05-27
forum: Virtualisation
---

### Post by A77ILA on 2014-05-27
Hi at all.
I'm sorry if i am posting in the wrong place and eventually for the bad english :oops:

I'm working on my first "semi" complex program written in bash, and i am wondering if someone else could be interested to use it.

The goal of the program is to manage Virtualbox Machines on a server host in headless mode, like an a ubuntu server installation.
At the moment is still poor as i am working on that for a small amount of time.

The feature that actually works:
[LIST]
[*]* Registration of the VM giving as parameters:
[LIST]
[*]Name
[*]Ram and V/Ram
[*]Cpu core n°
[*]Virtual Disk dimension
[*]Mount of the ISO for the installation if given
[/LIST]
[/LIST]


[LIST]
[*]Modify/Manage
[LIST]
[*]Start/Stop of the VM
[*]Backup of the VM: The machine will be suspended if running and when completed restarted. In this way you will not loose your work or uptime of the VM.
[*]Delete of VM: The machine will be unregistered and the main virtual hardisk deleted like the config ".vbox" file.
[*]VM Showstate: Will show the state for each machine: poweroff|saved|running|stopped|aborted.
[*]VM Showinfo: Will show the setting in the config file for the given VM.
[*]Verify Config: Will verify the directory in the config file for the correct manage of the backups and machines.
[/LIST]
[/LIST]

The feature i want to add now:
[LIST=|INDENT=1]
[*]Modify/Manage
[LIST]
[*]Changing and setting the vnc port used to launch each machine.
[*]Changing settings of the machine like; chipset, usb|ps2 keyboard/mouse
[*]Mount of the VBoxGuestAdditions.iso to the machine.
[/LIST]
[/LIST]

At the moment is localised in italian but as i said if someone is interested on this i can translate it :D

NOTE: all the machines is for now launched with "VBoxHeadless -s <VMName> -n -m <VNCPort>". In this way you will only need a vnc client to manage and monitor the machine from a computer that is not the server, obviusly. Also if you are running multiple machine you will only need to run htop or top to read the correct port of each machine if you forgive it.

---

### Post by TheFu on 2014-05-27
You might want to look at libvirt, virsh, virt-manager and vagrant to add your ideas to those long-running projects.

---

### Post by A77ILA on 2014-05-27
Damn, never seen that projects before, thank you :)
But in fact i was looking for something else: i just want a standalone simple as much as possible script (in fact, only bash and virtualbox installed here) and a simple interface with only numbered options :)

---

### Post by TheFu on 2014-05-27
> **A77ILA said:**
> Damn, never seen that projects before, thank you :)
But in fact i was looking for something else: i just want a standalone simple as much as possible script (in fact, only bash and virtualbox installed here) and a simple interface with only numbered options :)

About 6 months ago, someone else posted something similar on these forums ... I think in the scripting/programming section.

The OP seems to say you are creating a script, not looking for one.  

If you are trying to build a VM management platform, that has been done and is being continuously updated by teams of developers.

I would also caution against using VirtualBox for server deployments. Too many reasons to list. Sure, some people have used it and it is working ... .er ... until it doesn't.  The "smart money" is on KVM - IMHO.

Regardless, I wish you well and much success. Options are always good.

---

