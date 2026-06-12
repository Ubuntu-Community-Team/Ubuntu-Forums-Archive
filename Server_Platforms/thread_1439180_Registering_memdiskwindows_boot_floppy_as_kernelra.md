---
title: "Registering memdisk/windows boot floppy as kernel/ramdisk images"
date: 2010-03-25
forum: Server Platforms
---

### Post by bianster on 2010-03-25
I'm trying to get a Win2k3 instance running on UEC/Eucalyptus following the guides on [http://megam.info/2009/12/24/windows-on-eucalyptus/](http://megam.info/2009/12/24/windows-on-eucalyptus/) and [http://ajmf.wordpress.com/2009/10/14/running-windows-on-eucalyptus-impro](http://ajmf.wordpress.com/2009/10/14/running-windows-on-eucalyptus-impro)... using KVM

However, I've not been successful in getting the instance to actually run on Eucalyptus. I've narrowed down the issue to the fact that Eucalyptus is not recognising memdisk and the Windows boot floppy image as kernel/ramdisk images respectively. After registering the images, the image IDs I receive are emi-XXXXXX instead of eki/eri.

Attempting to run euca-run-instance with the --kernel/--ramdisk options doesn't work also as the command fails with an error indicating the Eucalyptus doesn't recognise either image as valid kernel/ramdisk images, "ImageVerify: Image specified is not a kernel".

---

