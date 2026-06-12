---
title: "Howto: XP guest in VMware Workstation to use Paravirtualized SCSI"
date: 2009-10-27
forum: Virtualisation
---

### Post by bakegoodz on 2009-10-27
I've search and search I couldn't find how to do this, but I figured it out myself and now sharing.
In theory using Paravirtualized drivers in your guest is faster and use less CPU. This is because the PV guest OS drivers knows how to talk to the Virtual Machine directly rather than running on emulated hardware. I'm too lazy to do any bench marks, but I'm seeing lower CPU numbers from vmware-vmx in TOP when doing some heavy IO tasks that I do. Disclaimer: VMware is not recommending to use pvscsi driver for a main OS drive yet. Though I haven't had any problems and others on VMware forums ignore this warning too.


I did this with the New VMware Workstation 7 and Ubuntu 9.10 rc

Use an existing Guest or setup a new one. The Virtual hard drive needs to be SCSI though. Creating a SCSI drive with the Bus Logic interface would be most painless, because you wouldn't need to use a F6 driver. If your curious, I had the Virtual LSI SAS interface setup to a physical drive.  Do a custom install of VMware tools, choose to install the pvscsi driver. I also installed the vmxnet3 driver too, because the word on the street is that this is the best Virtual Network adapter and is Paravirtualized.
Shutdown and close VMware and Edit the vmx file (ex. ~/vmware/XP/XP.vmx)
after the line: (Yours may be a little different)
scsi0.present = "TRUE"
scsi0.virtualDev = "lsisas1068"
add these lines:
scsi1.present = "TRUE"
scsi1.virtualDev = "pvscsi"
Boot up your guest, Windows will detect a new adapter, and it should automatically install with the default dialogs. Then shutdown the guest and close VMware
Go back to your vmx file and edit the scsi0 and scsi1 lines to just be:
scsi0.present = "TRUE"
scsi0.virtualDev = "pvscsi"
I also added
ethernet0.virtualDev=vmxnet3
after the line:
ethernet0.present = "TRUE"
Now your Guests hard drive and network adapter are Paravirtualized and not emulated.

---

### Post by bakegoodz on 2009-11-01
I am really liking this setup. Everything runs quicker, and I have had zero problems. When I build a UBCD4Win image in Virtual XP it only uses 30 to 50% CPU utilization (run "top" on the host), when before it would use 80% to 100%.

---

### Post by bakegoodz on 2010-08-06
Bus logic needs the VMscsi F6 Driver. Glad I posted guide because I forgot how to do this

---

