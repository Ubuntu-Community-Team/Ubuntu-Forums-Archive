---
title: "virt-manager no ;onger shutting down Windows 10"
date: 2021-06-13
forum: Virtualisation
---

### Post by cjsmall on 2021-06-13
Xubuntu:  20.04
virt-manager:  1.2.2.1-3ubuntu2.1 package
Windows 10 Pro:  21H1 build 19043.1055

Both Windows and virt-manager were updated sometime during the past month on my system.  I cannot pin-point the exact moment that the problem started, but recently the virt-manager light-switch icon no longer shuts down Windows.  None of the actions from the associated pull-down menu (reboot, shut down, etc.) work either.  Windows still reboots and shuts down fine using its internal Start Menu controls.

Does anyone else see this new behavior?  If so, what version of virt-manager and Windows are you running?  I'm trying to figure out if this is a problem that a Windows Update created or whether some change was made to virt-manager which broke something.

---

### Post by ajgreeny on 2021-06-13
Is your VM of Windows the only one you run or do you have others, eg. other Linux distros?
If so, do they shutdown properly, or is this just a Windows problem?

If you run in a non full-screen mode can you shutdown by using the **Virtual Machine -> Shutdown -> Force Off** menu item?

I recently deleted my Windows 10 VM as I had no need for it any more so I can't tell you if I have the same problem as you, but in my time of using it I never saw anything similar except when the whole OS crashed to a dreaded blue screen and I used that method to power-off and then restart.

I am also using Xubuntu 20.04 and the same virt-manager as you with many test Linux distros and all of those shutdown exactly as if a bare-metal installation.

On my system there were upgrades of the several **libvirt** packages on 6th May 2021 but no upgrade recently of virt-manager itself.

---

### Post by cjsmall on 2021-07-06
Sorry for the long delay in responding.  I lost track of this thread.

I'm currently only running a single VM with Windows 10.  As previously stated, the shutdown button (light switch icon) doesn't work selecting either reboot or shutdown.  But Force Off does an immediate and inglorious termination of the running session.  I speculate that that is because virt-manager is talking to itself and simply terminating the running process while the shutdown and reboot signals are being sent to Windows 10 and are being ignored.  As I said, this behavior is recent and I suspect it may be due to a change in Windows 10, so it would still be good if anyone else running a fully updated Windows 10 could confirm whether virt-manager was or was not working in this respect.  I'm wondering if Windows changed the signaling process for shutdows and virt-manager needs to catch up?

I realized I had an older backup VM version of Windows 10 that hasn't been recently patched.  I started it up and virt-manager was able to shut it down just fine.  So it looks like the problem resides in a recent patch to Windows.  I'm going to submit a bug report on this.

---

### Post by MAFoElffen on 2021-07-06
Is the Windows VM guest setup with the Spice Guest Agent or the Qemu Guest Agent?  --Which would help if with Guest types of Agents for it running within KVM, as well as how it relates to KVM itself, such as the software shutdown and reboot signaling.

What I'm thinking is.. That if you did install those previously, maybe a recent Windows update did something with that. Maybe try to reinstall those agents and see what happens.

---

### Post by tea for one on 2021-07-06
Ubuntu 20.04 host (with gnome 3.36.8)
Windows 10 guest (Home version 21H1 build 19043.1052) fully updated
Windows Spice guest tools included
Virtual machine manager 2.2.1 with kvm-qemu

Using the graphical console of  Virtual Machine Manager

Virtual Machine > Shutdown > Reboot [COLOR="#0000FF"]Functions OK[/COLOR]
Virtual Machine > Shutdown > Shut Down [COLOR="#0000FF"]Functions OK[/COLOR]

However, you have Windows 10 Pro, although I doubt if it is significant.

---

