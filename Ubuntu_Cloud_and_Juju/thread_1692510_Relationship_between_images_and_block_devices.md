---
title: "Relationship between images and block devices"
date: 2011-02-21
forum: Ubuntu Cloud and Juju
---

### Post by NigelRen on 2011-02-21
Hi
I've been playing with UEC and also had a look at KVM which has been very interesting and useful.  The difficulty I'm having though is:
(Sorry for any incorrect terminology :-/ )
With KVM you create a disk image, In my understanding - this can only be associated with one running instance.  This means any changes to the image are maintained across subsequent instances.

With UEC you register a set of elements ( image etc ) with Eucalyptus and then this image can be used to start an instance.  Is this instance the same as a KVM image, or is this just the template for a KVM image?  What if changes are made to the kernel - does this need to be re-uploaded to Eucalyptus?

Any info - even a URL, which would help would be great :)
Thanks

---

### Post by raymdt on 2011-02-21
Hi,
Eucalyptus, uec, aws just manage KVM or XEN over SOAP/REST.  You can rebundle an image with another Kernel or ramdisk.
Just use

euca-bundle-image
to bundle the image with another kernel
then use euca-upload-bundle and euca-register to register the new image.

---

### Post by kim0 on 2011-02-23
A kernel is bundled with an image. If you need to update the kernel, you need to rebundle, just upgrading the kernel inside the image won't take effect.

Some work however is underway to change this way (using pvgrub on ec2, and kexec kernels on UEC)

---

### Post by raymdt on 2011-02-23
This link can help you
[http://cloud.ubuntu.com/2011/02/migrating-to-pv-grub-kernels-for-kernel-upgrades/](http://cloud.ubuntu.com/2011/02/migrating-to-pv-grub-kernels-for-kernel-upgrades/)

---

