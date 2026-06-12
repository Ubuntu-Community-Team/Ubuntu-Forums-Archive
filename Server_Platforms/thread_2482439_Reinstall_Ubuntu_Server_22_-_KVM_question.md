---
title: "Reinstall Ubuntu Server 22 - KVM question"
date: 2022-12-30
forum: Server Platforms
---

### Post by Heeter on 2022-12-30
Hi all,

Quick question: Just want to confirm.

If I copy the kvm guests onto a external HD, reinstall UbuntuServer22+KVM, Can I put the VM guests back into the server after fresh install and the guests will work again?

I currently have a fully functioning UbuntuServer22LTS with only KVM server installed. Everything is functioning properly, but I am having issues with Ubuntu since I did a 20LTS to 22LTS a few months ago.

What will I need to do to KVM Host to get the existing reinstalled guests to get them spinning?

Regards

---

### Post by MAFoElffen on 2022-12-31
Just make sure that the guest files end up in the same path directory that they were in...

For mine, I have my storage for VM's and ISO's separated on another drive... Just to make migrations easier.

---

### Post by MAFoElffen on 2022-12-31
And remember the XML files at /etc/libvirt/qemu...

---

### Post by Heeter on 2022-12-31
Ok Great Thank you!! Did not realize that I had to save anything else other than the guest folders

Thank you so much!!

Regards

---

