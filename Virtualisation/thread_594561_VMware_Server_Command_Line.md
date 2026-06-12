---
title: "VMware Server Command Line"
date: 2007-10-28
forum: Virtualisation
---

### Post by tjpren on 2007-10-28
Hi guys,
I'm trying to start a virtual machine from the command line.

To find the path I use vmware-cmd -l
administrator@scada-dev:~/vmware$ vmware-cmd -l
/var/lib/vmware/Virtual Machines/Windows XP Professional/Windows XP Professional.vmx
/var/lib/vmware/Virtual Machines/Windows 98/Windows 98.vmx

When I use this path in a start, I get an error

administrator@scada-dev:~/vmware$ vmware-cmd /var/lib/vmware/Virtual Machines/Windows XP Professional/Windows XP Professional.vmx start
/usr/bin/vmware-cmd: Could not connect to VM /var/lib/vmware/Virtual
  (VMControl error -11: No such virtual machine: The config file /var/lib/vmware/Virtual is not registered.
Please register the config file on the server.  For example:
vmware-cmd -s register "/var/lib/vmware/Virtual")

I can start the VM from the VM console OK.  The path listed appears in the VM console config.

I've also tried a sudo prefix with the same error

Its probably syntax, but would appreciate some help.

---

### Post by tjpren on 2007-10-28
Thought so - Syntax problem

Apparantly where there are spaces in a name, I need to have a forward slash \ and space.

I'm now able to start the VM from the console.

---

### Post by klecu on 2008-01-31
You can also quote the path with either single or double quotes, whichever you prefer.

---

