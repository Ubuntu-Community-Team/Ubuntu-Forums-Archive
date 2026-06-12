---
title: "How do I  set up a VM that runs entirely off of a SSD"
date: 2021-08-07
forum: Virtualisation
---

### Post by snype9lives on 2021-08-07
on windows it used to be easy but I for some reason cant do it on ubuntu, does anyone know how they do it?

---

### Post by QIII on 2021-08-07
Not sure what you mean.  An SSD is just another storage device.

On this machine I have VMs on both 2.5" SSDs and NVMe devices.

What is happening?

---

### Post by snype9lives on 2021-08-08
nvm, sorry

---

### Post by volkswagner on 2021-08-08
Are you trying to [pass through the physical hardware/ssd]("https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_administration_guide/sect-virtualization-adding_storage_devices_to_guests-adding_hard_drives_and_other_block_devices_to_a_guest")?

---

### Post by monkeybrain20122 on 2021-08-08
What do you mean? Do you try to set up your VM in an external storage or something like that? Sorry man it is really hard for people to help you if you don't describe your problem clearly. We don't know what you try to do and you said "it is not working" and we don't know what is not working and what are the error messages or warnings if there was any. It is like going to the doctor and say I am not feeling well can you help me.

---

### Post by recepserit on 2021-08-08
Could you explain exactly what do you mean? I'm using VirtualBox. If you want to use SSD with VM, just create a new disc and check "Solid-state Drive" option.
Like this:


[IMG]https://i.ibb.co/dtyrLmF/2021-08-08-225912.jpg[/IMG]

---

### Post by MAFoElffen on 2021-08-10
If you were using KVM, and NVMe SSD, then it would be easy using Virt Manager... You just create the VM and ensure you check the box to modify before the installation...

Use lspci to located the bus:slot of the NVMe drive.

Then in the Details Panel, select Add New Hardware" > Add Physical PCI Device, find the Bus:Slot: Address of the drive... select and add.

Will be passed through to the VM for use. It will then show up in the Boot section, so you can set the passed through Physical Device in the boot order.

This is similar to how I connect some specific VM's directly to physical USB Storage Drives... Especially if I am creating a VM from a downed physical machine, to help with migration.  This really speeds up recovery time. This is also how I test USB thumb drives and how they boot.

EDIT/Afterthought: Notice I said migration... If it has a preinstalled OS that is not dynamically aware of device changes at boot, then the static device drivers will be a problem and the machine will need to be migrated/transformed into a VM. 

If that is the condition... Then the better end goal is to both benefit your host and the created VM. If you temporarily pass-through the NVMe to do a migration to a QCOW2 image... then the advantage of QCow2 is that it is provisioned as a size, but is the size of what is used in the image file. if migrated to QCow2... Then the NVMe could be added back to the Host and then the QCow2 stored back on it as an image file, and add benefits to the Host as a storage resource also...

---

