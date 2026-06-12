---
title: "virsh attach-disk"
date: 2008-05-19
forum: Virtualisation
---

### Post by besson3c on 2008-05-19
Hello,

I'm stuck with this problem here:

[https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/203020](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/203020)

I'm not expecting that anybody here as a fix for this particular issue, but I'm wondering if anybody has come up with an effective workaround? 

I'm thinking that with a bit of creativity (such as copying all of the Windows CD-ROM to my disk image) that I could find a way to install Windows XP? Is there a way to mount a KVM disk image so that I can copy data to this image?

---

### Post by smithfarm on 2008-06-06
Same problem here. The workaround I came up with was this command:

sudo kvm -hda [name_of_image_file] -cdrom [name_of_iso_file] -m 512

It doesn't seem to be as fast as virsh, though, but at least it gets one through the installation. Suppose it's just a matter of time before the bug gets fixed.

---

