---
title: "create non sparse qcow2 disk image"
date: 2012-01-10
forum: Virtualisation
---

### Post by prezbedard on 2012-01-10
I have come to figure out that qemu-img will only create sparse qcow2 images. I even tried creating a raw file then converting but as soon as I convert it also converts to a sparse file. I don't get why during the original install using virt-install doesn't do this.

I am trying to add a disk image to a windows 2008 server guest. It does not see the image at its full size but at its original which is basically nothing. 

Is there a way to create a non sparse qcow2 file?

Thanks!

---

### Post by prezbedard on 2012-01-12
I believe I may have figured this out through some more reading and experimenting.

So I created the original virtual machine using virt-install indicating a qcow2 file. However in my reading and looking over the file several times that the driver type was set to raw by virt-install. So it is a qcow2 file but in raw format?

While I was using qemu-img for testing I did the following

created 2 1 GB files. I first created test1.qcow2 format qcow2
then test1.raw format raw, The raw file showed up as 1GB when using the ls -l -h command the qcow2 did not. I converted the test1.qcow2 file to test2.raw it then showed up as 1GB. I converted the test1 raw file to test2.qcow2 and it no longer was listed as 1GB but much smaller.

I added the converted raw to qcow2 image to the xml file with driver type qcow2  defined and started it but it would not start when I changed it to raw it worked fine. I added the original qcow2 file I created using qemu-img with driver type qcow2 and it worked fine.

So when a raw file is converted to qcow2 it is not the same as just creating a qcow2 file?

Also even though I specified a qcow2 file originally when using virt-install it makes it a raw format file ?

I am a bit confused by this.

Thanks!

---

