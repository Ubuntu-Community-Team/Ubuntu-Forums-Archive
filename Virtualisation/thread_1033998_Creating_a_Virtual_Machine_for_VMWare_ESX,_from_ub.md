---
title: "Creating a Virtual Machine for VMWare ESX, from ubuntu-vm-builder"
date: 2009-01-07
forum: Virtualisation
---

### Post by shebangs on 2009-01-07
Is this supported?

This is the command I am using:

```

$VMBUILD vmserver hardy \
--mirror $MIRROR \
--components main,multiverse,restricted,universe \
--mem 1024 \

```

I can successfully run the resulting image with VMWare Player, but it doesn't work with ESX/ESXi.  We do use XEN/KVM as well, but that's for inhouse systems.  We're a developement house and I'm trying to deploy out an automated process that can build, upload/started to a ESX Test server -- then have a suit of automated tests run against it. 

Thank you

---

### Post by shebangs on 2009-01-14
Anyone able to help?

Is there *any* other way, to automatically (via a unix script) to create a Ubuntu Image that's compatible with ESX?

Thanks

---

### Post by shebangs on 2009-02-24
Anyone?

I've tried creating it using vmserv, but the .vmdk that is created isn't correct.

The vmx also uses IDE, not LSI Bus SCSI.

---

### Post by Dedoimedo on 2009-02-25
What's wrong with uploading .vmx and .vmdk files and registering them?
Regards,
Dedoimedo

---

### Post by shebangs on 2009-02-25
> **Dedoimedo said:**
> What's wrong with uploading .vmx and .vmdk files and registering them?
Regards,
Dedoimedo

Because it doesn't work.

ESXi registers the .vmx file, but labels it Invalid and it won't start.   Looking internally at the vmx, the structure is old and wrong.  No SCSI etc.

Even the vmdk is a single file, where the current standard is the .vmdk reference file and the -flat.vmdk file.

**IF** I could somehow specify a "8GB VMDK" file, I might be able to play around with it and use my own vmx and my my own .vmdk reference file.   Is there another util I could say?  For example, something that can convert KVM into a fully qualified ESX (vmx/vmdk) deployment?

Surely someone else has realized *vmserv* doesn't import into ESX/ESXi?

---

### Post by Dedoimedo on 2009-02-26
Hello,

I had no problem doing that ... :) with ESXi.

Upload the vmx and vmdk to the datastore.
Right click on vmx and select to add inventory.

When the machine starts, the ESXi might ask you about the uuid, to keep, create, always keep and always create. Your choice.

Done this many times ... Tutorial on the way, btw.

Dedoimedo

---

### Post by shebangs on 2009-02-26
Wow, I'm experienced when it comes to ESXi and Ubuntu isn't too bad.

I'm really interested to see your vmbuilder statement.   An "ls -l" on the files it creates, and a cat from the vmx.

I'm looking forward to the Tutorial.

Thanks

---

### Post by Dedoimedo on 2009-02-26
Hello,
I'm not doing this on Ubuntu, mind ... should have said it, I guess. Either way, I'll post the tutorial soon and if there are any issues afterwards, do tell.
Dedoimedo

---

