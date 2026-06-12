---
title: "vmware parallel port for sentinel dongle in win xp guest"
date: 2008-12-12
forum: Virtualisation
---

### Post by ghostwriter78 on 2008-12-12
Hello Everybody,

we use Sentinel parallel port dongles for our windows software and would like to access them in the VM on ubuntu host.

The VM itself was created on windows host, and the parallel dongle works fine there.

Unfortunately i can not manage to get the software in the VM Guest to access the parallel port on the host.

System:
host: ubuntu 8.10
guest: windows XP sp3
dongle: sentinel, parallel port

I tried following:
sudo modprobe ppdev
chmod 666 /dev/parport0
rmmod lp

I added also this to the /etc/init.d/vmware :
	 rmmod lp
         chgrp lpadmin /dev/parport0
         chmod g+rw /dev/parport0
at end of
vmwareService() {
   case "$1" in
      start)


On startup of the VM i do NOT get the parallel port assignment error anymore.

But still the dongle cannot be accessed.

can somebody guide me through as i tried already a few things and havent been able to make it work.

Kind regards
Tibor

---

### Post by Dedoimedo on 2008-12-12
Hello,

If you get a parallel port error, this probably means something is using it. I'm getting that error on a machine where indeed, a printer is connected to that port.

Is any hardware using the parallel port 0? Did you try other ports?

Dedoimedo

---

### Post by ghostwriter78 on 2008-12-14
Hello, :)

im getting no report from the vmware workstation.

The host has ubuntu 8.10 standard installation, and one parallel port dongle attached. there should be no software using it.

then i start the vmware workstation and a VM which needs the parallel port dongle.

the vm starts fine, but the dongle can not be accessed from within the vm, even there is NO startup error for parallel port.

I have only one physical parallel port so i cant move the dongle to other port.

what could i try else?

Tibor

---

### Post by ghostwriter78 on 2008-12-17
Hello,

is there anybody who has experience with parallel port setup and could help me a bit to find the issue?

regards
Tibor

---

### Post by dubfazer on 2008-12-23
Just checking the obvious. Have you edited the vm settings (when vm is powered down) and added the parallel device to the machine. Without creating a parallel port device you will never see it in the vm.

---

### Post by ghostwriter78 on 2009-01-05
the VM was created on a windows machine and copied later to ubuntu..

on windows i used the vm with the parallel dongle, and it was working.

could you help me to figure out what is wrong with my ubuntu and parallel port config?

i tried to use instructions from ubuntu website but it didnt work, and i assume there was something not matching the real way of configuration for ubuntu 8.10.

---

### Post by dubfazer on 2009-01-05
Not sure, but it may be that the physical parallel port device is different under linux as the host verses windows as a host, thus the virtual device that you added to the VM under windows may not map to anything on the ubuntu physical host. So I think it would be worth editing the VM and removing and re-adding the parallel port. (you can always take a snapshot before hand to allow you to go back if it doesn't help).

---

### Post by ghostwriter78 on 2009-01-05
I changed already the config of the vmx file..

now it contains following: (edited a bit)

.encoding = "UTF-8"
config.version = "8"
virtualHW.version = "6"
scsi0.present = "TRUE"
memsize = "1024"
ide0:0.present = "TRUE"
ide0:0.fileName = "hd01-000006-cl1-000001.vmdk"
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "cdrom-raw"
floppy0.autodetect = "TRUE"
ethernet0.present = "TRUE"
ethernet0.connectionType = "nat"
ethernet0.wakeOnPcktRcv = "FALSE"
usb.present = "TRUE"
ehci.present = "TRUE"
sound.present = "TRUE"
sound.fileName = "-1"
sound.autodetect = "TRUE"
svga.autodetect = "TRUE"
pciBridge0.present = "TRUE"
mks.keyboardFilter = "allow"
deploymentPlatform = "windows"
virtualHW.productCompatibility = "hosted"
tools.upgrade.policy = "useGlobal"

ide1:0.autodetect = "TRUE"
floppy0.present = "FALSE"
serial0.present = "TRUE"
serial0.autodetect = "TRUE"
parallel0.present = "TRUE"
parallel0.autodetect = "FALSE"
parallel0.fileName = "/dev/parport0"
parallel0.bidirectional = "FALSE"
snapshot.action = "prompt"

ide0:1.present = "TRUE"
ide0:1.fileName = "hd02-000006-cl1-000001.vmdk"
ide1:1.present = "TRUE"
ide1:1.fileName = "hd03-000006-cl1-000001.vmdk"

ide1:0.startConnected = "TRUE"

isolation.tools.hgfs.disable = "TRUE"

ethernet0.addressType = "generated"
ide0:0.redo = ""
ide0:1.redo = ""
ide1:1.redo = ""
pciBridge0.pciSlotNumber = "17"
scsi0.pciSlotNumber = "16"
ethernet0.pciSlotNumber = "32"
sound.pciSlotNumber = "33"
ehci.pciSlotNumber = "34"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
inVMTeam = "FALSE"

vmotion.checkpointFBSize = "16777216"

parallel0.startConnected = "TRUE"

does it look right?

---

### Post by ghostwriter78 on 2009-01-12
Hello,

is there anybody who has experience with parallel port on ubuntu in combination with wmware?

would appreciate your help.

kind regards
Tibor

---

