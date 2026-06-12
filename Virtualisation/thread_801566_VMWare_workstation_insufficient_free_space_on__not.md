---
title: "VMWare workstation insufficient free space on / not checking the correct volume /data"
date: 2008-05-20
forum: Virtualisation
---

### Post by kvasimongo on 2008-05-20
After installing VMWare workstation 6.03 b 80004 on Hardy, i ran into a major problem.

When trying to create a guest machine, VMWware checks for free space when creating the disk file. Should think this was a nice thing, except for the fact that VMWare only checks the / free space, and not the free space on the /data volume where im telling VMWare to place the guest machine.
The problem with that is that my / volume only has 7gb free, but my /data volume has 130gb free, and is where i`ll store my VM`s. Therefore VMWare is limiting my guest os diskfile size to less than 7gb.... 

So has anyone else experienced this problem, or even better found a solution?

---

### Post by fjgaude on 2008-05-20
I've not run into this issue but I think you have to declare the drive in the setup... if you think you have done that then go back and look at what drives are being called and maybe get a feel for what has to be done.

In my .vmx text file there's this line:

ide0:0.fileName = "Windows XP Professional-000001.vmdk"

And from that I think you can see that is where the console looks for the created .vmdk file.

In the drive setup you have to select an ide/scsi device that works for you.

Good luck, but do let us know how you make out.

---

### Post by bradmkjr on 2008-05-20
The solution is simple.

Use Workstation to build the VM with a 1 gig drive.

Move the VMX, VMDK, Etc to your /data

Then you could use qemu to create a new vmdk or VMware workstation:

```

cd "/data/Windows XP Professional"
qemu-img create -f vmdk "Windows XP Professional-000001.vmdk" 100G

```

if you change the name of the vmdk, then don't forget to edit the line in the vmx.

Good Luck,
Bradford Knowlton
[http://x86Virtualization.com](http://x86Virtualization.com)

---

### Post by kvasimongo on 2008-05-21
Thanks Bradford, i know of a few workarounds like this one.
Im getting it running by creating a small disk file, then expanding it. But the problem still remains, there is a bug in VMWare Workstation and it needs to be fixed :)

---

