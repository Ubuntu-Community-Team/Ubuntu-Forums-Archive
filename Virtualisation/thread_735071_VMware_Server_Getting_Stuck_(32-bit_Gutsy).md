---
title: "VMware Server Getting Stuck (32-bit Gutsy)"
date: 2008-03-25
forum: Virtualisation
---

### Post by Nazrax on 2008-03-25
I'm running Ubuntu Server 7.10 (32-bit) with VMware server installed from the Partner repository (1.0.4-1gutsy2 & vmware-server-kernel-modules-2.6.22-14).

For the most part, things work fine. However, every couple of days, VMware stops responding. The console (and vmrun and vmware-cmd) says something about "unable to connect to vmware-serverd process" (sorry, it's not doing it right now, and I don't have the error written down). /etc/init.d/vmware-server stop doesn't work if any VMs are running - it tries to shut down the VMs forever. If I manually kill off the VMX processes, vmware-server stop will run to completion, but it'll leave behind a vmware-serverd process that has to be kill-9'd. Once it's gone, I can start VMware again, and it'll work fine - for another few days.

This happens on two different machines, both of which have a lot of VMs starting and stopping.

What can I do to make VMware more reliable?

---

### Post by Nazrax on 2008-03-25
Ok, it just started doing it again.

*vmrun list* reports (yes, it really is duplicated): 
> Error: The system returned an error. Communication with the virtual machine may have been interrupted.
Error: The system returned an error. Communication with the virtual machine may have been interrupted

The VMware server console (remote) reports:
> Unable to connect to the remote host: 511 Error connecting to /usr/sbin/vmware-serverd process..

*vmware-cmd -l* reports:
> /usr/bin/vmware-cmd: Could not connect to vmware-authd
  (VMControl error -14: Unexpected response from vmware-authd: 511 Error connecting to /usr/sbin/vmware-serverd process.)

There's nothing out of the ordinary in vmware-serverd.log.

No VMX processes are currently running.

---

### Post by HarryZ on 2008-05-06
Hi,
I've got the same problem. The reason was that in my /etc/resolv.conf I had defined a server that is virtually hosted on my VMware server. After removing that adress from resolv.conf and restarting the VMware server daemon (vmware-serverd restart) everything worked fine.
-Harry

---

