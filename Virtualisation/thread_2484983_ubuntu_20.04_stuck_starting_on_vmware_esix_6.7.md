---
title: "ubuntu 20.04 stuck starting on vmware esix 6.7"
date: 2023-03-16
forum: Virtualisation
---

### Post by rzghari on 2023-03-16
Good morning, 
I have a virtual machine on VMware ESXi 6.7 installed on Ubuntu 20.04 that is stuck with this message:
[B]ordering cycle found skipping system initialization 
[/B]How can I fix it without losing my application that is installed on the server?
Thank you for helping me.

---

### Post by slickymaster on 2023-03-16
Thread moved to **Virtualisation** for a better fit

---

### Post by naufrsb on 2023-03-16
The "ordering cycle found skipping system initialization" error message means that a circular dependency between two or more of your system services. This prevents the virtual machine from booting up properly. First, try to boot into recovery mode, then try the following: 

[LIST=1]
[*]Use the command "journalctl -xb" to view the system log files and look for any error messages related to the circular dependency issue. This can help you identify which services are causing the problem.

[*]Disable the problematic service: Once you've identified the service(s) causing the circular dependency, try disabling them temporarily using the command "systemctl disable <service>". This will prevent the service from starting during boot, allowing the virtual machine to boot up properly.

[*]Fix the service dependency: If you're able to identify the root cause of the circular dependency, you may be able to fix the issue by modifying the service dependencies using the "systemctl edit <service>" command.

[*]Backup and restore the application: If none of the above steps work, you may need to backup the application installed on the virtual machine and restore it on a new virtual machine with a fresh installation of the operating system.
[/LIST]

---

### Post by MAFoElffen on 2023-03-17
First... Is this VM Server Edition or Desktop Edition? That matters in where that message appeared...

Second which release of Ubuntu?

At that point, the cloud-init process has already started, so is late in the bootup process. You may be able to toggle to another VTTY session if they have been initialized by that stage... Try <Cntrl><Alt<F4> If so, then log in and check your logs for errors and warnings. That is usually a systemd service error.

---

