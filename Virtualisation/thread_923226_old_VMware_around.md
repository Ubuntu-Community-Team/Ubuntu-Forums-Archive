---
title: "old VMware around?"
date: 2008-09-18
forum: Virtualisation
---

### Post by paeppi.p on 2008-09-18
Hi,

I have a request, which seems most unlikely to be answered positively, but I'll try anyway.

I have a CD with an old Windows image lying around. I am looking for some private data, which I suspect may be contained there, so I look for a way to read this old image. 

More precisely: the image was created in December 2000, the log file contains this information:
Dec 06 14:56:33:    ProductID = VMware for Linux
Dec 06 14:56:33:    ProductType = 2.0

I think what I need is a version of VMware, which is old enough so that this image is loadable and readable. 

Currently I use Hardy Heron. Also I have an old laptop running Windows 98, so a version of VMware running on Windows 98 would also help.

Any suggestions?

Cheers, Peter

---

### Post by jruschme on 2008-09-21
IIRC, a current version of VMware should be able to import/run an old image.

I'd suggest downloading a eval copy of Workstation 6, installing it, and trying to import the image.

John

---

### Post by paeppi.p on 2008-09-26
As suggested I have installed a eval copy of Workstation 6. But it does not seem to be so easy, at least for a VMware-non-expert like me. 

Straightforwardly importing the image did not work. I have looked for help in the "Legacy Virtual Disks" section of the "Workstation User's Manual", and also in the "Virtual Machine Mobility Planning Guide". With the multitude of VMware products and product versions covered in these documents I find it rather confusing.

I do have the log-file of the creation of my image. But I am lost already when it comes to identifying the VMware version documented in the log file within this zoo covered in the mobility guide.

> **jruschme said:**
> IIRC, a current version of VMware should be able to import/run an old image.

I'd suggest downloading a eval copy of Workstation 6, installing it, and trying to import the image.

John

---

### Post by Coombabah on 2008-09-26
The vmware forums may be a good place to look.

[http://communities.vmware.com/index.jspa](http://communities.vmware.com/index.jspa)

Another option may be using virtualbox as it can read some vmware formats.

---

### Post by paeppi.p on 2008-09-29
Thanks for your hint. Somebody in the VMware forums pointed me to vdk.exe.
Indeed I have been able to mount my old nt4.dsk image with vdk.exe.
I have copied the data I was looking for. My problem is solved. [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

> **Coombabah said:**
> The vmware forums may be a good place to look.

[http://communities.vmware.com/index.jspa](http://communities.vmware.com/index.jspa)

Another option may be using virtualbox as it can read some vmware formats.

---

