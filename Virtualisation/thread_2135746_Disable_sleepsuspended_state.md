---
title: "Disable sleep/suspended state"
date: 2013-04-15
forum: Virtualisation
---

### Post by peadwen on 2013-04-15
I would like to disable sleep/suspended state on a VirtualBox 4.2.10 > Ubuntu 12.04 LTS with no GUI but I cannot find the right settings to do so.

When the VM goes into a suspended state it crashes and has to be restarted.
This VM is used to run Joomla only and it constantly shutting down is a bit inconvienient since it will be our internal website.

Here is an excerpt from the Virtualbox Log:

00:00:12.441530 Changing the VM state from 'RUNNING' to 'SUSPENDING'.00:00:12.444727 AIOMgr: Preparing flush failed with VERR_NOT_SUPPORTED, disabling async flushes00:00:12.456472 AIOMgr: Endpoint for file 'C:\Users\gselector.CCR-GS-SERVER\VirtualBox VMs\Joomla\Joomla.vdi' (flags 000c0781) created successfully
00:00:12.471835 PDMR3Suspend: 30 193 310 ns run time
00:00:12.471850 Changing the VM state from 'SUSPENDING' to 'SUSPENDED'.
00:00:17.665665 Console::powerDown(): A request to power off the VM has been issued (mMachineState=Stopping, InUninit=0)
00:00:17.667136 Changing the VM state from 'SUSPENDED' to 'POWERING_OFF'.

---

