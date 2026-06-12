---
title: "Move vm from vmware fusion to vmware server"
date: 2008-02-24
forum: Virtualisation
---

### Post by poonaka on 2008-02-24
I'm trying to move a vm from fusion (on OS X) to vmware server on gutsy server.  I copied over the .vmdk and .vmx files from inside the .vmwarevm package.  When I run vmware-cmd -s register nameOfMyVM.vmx I get the following error:

VMControl error -11: No such virtual machine

Anyone have any luck with this?  Is there a way that I can recreate my .vmx file?

Thanks

---

### Post by fjgaude on 2008-02-24
Maybe you might get a reply from the vmware.com forums... not many here use Fusion. Most of us no longer buy software. <grin>

---

### Post by huwge on 2008-04-23
Hi,

vmware-server doesn't understand the disk format used by Fusion. You need either vmware player 2 or vmware workstation 6.

It looks like vmware-player has been removed from Gutsy but someone is maintaining a repo that contains it, info here:

[https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/135358](https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/135358)

hth
Huwge

---

### Post by huwge on 2008-04-24
I have also found that the beta of vmware server 2 for linux handles fusion VMs correctly.

H

---

