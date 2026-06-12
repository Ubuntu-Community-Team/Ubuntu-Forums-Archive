---
title: "How to recover data from a .vmdk disk image that won't boot"
date: 2008-09-08
forum: Virtualisation
---

### Post by beaver29 on 2008-09-08
i run gutsy as a VM under VMWare player 2.0.1 on a windows XP host.  two weeks ago i installed a new package that trashed something on my virtual disk image (the .vmdk file) and i couldn't boot the VM.  i had data on that machine that i desperately needed.  after a long ordeal, i recovered the data.  i thought it would be good to share the process.  (perhaps this should be a "howto" post but i couldn't figure out how to do a "howto".)

the first step was to make a copy of the corrupted virtual disk and mount it to another linux VM.  thanks to Bradford Knowlton for suggesting this idea in this post:

[http://www.ubuntu-forums.net/showthread.php?t=803411&highlight=bradmkjr+ruialexbarbosa]("http://www.ubuntu-forums.net/showthread.php?t=803411&highlight=bradmkjr+ruialexbarbosa")

in order to do this, i downloaded the free VMWare server and made a new linux VM.  i used the same appliance i had used to make the original VM but any linux VM should work.  i opened it in VMServer and did the edits described in Bradford's post.  this added my corrupted .vmdk virtual disk image to the new virtual machine as a second SCSI disk, SCSI(0:1).  after i did that, the new VM refused to boot.  eventually i was able to make the new VM boot by adding the corrupted .vmdk as SCSI (0:0) and the new .vmdk as SCSI(0:1).  don't ask me why that worked.

next i tried to mount my corrupted virtual disk.  "fdisk -l" showed the corrupted disk as "sdb" with these partitions:  

  /dev/sdb1 * 1 31 248976 83 Linux
  /dev/sdb2 32 1044 8136922+ 5 Extended
  /dev/sdb5 32 1044 8136891 8e Linux LVM

cool!  but when i tried to mount them like this:

  $ sudo mkdir /Junk
  $ sudo mount -t ext2 /dev/sdb2 /Junk

i got this error message:

  mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
  missing codepage or helper program, or other error
  (aren't you trying to mount an extended partition,
  instead of some logical partition inside?)

eventutally, i noticed that sdb5 was of type "Linux LVM" (Logical Volume Manager).  i'd never heard of LVM before but after an inordinate amount of googling, i found this web page which explains how to mount a logical volume:

[http://www.linux-sxs.org/storage/fedora2ubuntu.html]("http://www.linux-sxs.org/storage/fedora2ubuntu.html")

i followed these steps and successfully mounted my corrupted disk.  fortunately i generated a log file when i was installing the package that broke my machine.  i could see that the package only installed one new library file.   i mounted the drive read/write ("mount .... -o rw,user" instead of "mount ... -o ro,user"), removed the suspect library file and BOOM! i was able to boot the original VM.  all my data is fine and i don't have to rebuild my machine!  i love happy endings!

i realized later that i didn't have to get VMServer to add the corrupted disk to my new VM.  i coulda just done that part by editing the *.vmx file or maybe using Easy VMX. [http://easyvmx.com/]("http://easyvmx.com/")

[http://www.howtoforge.com/linux_lvm]("http://www.howtoforge.com/linux_lvm") is a good place for newbies to learn how to deal with LVM partitions in Linux.  it even has a small prebuilt debian VMWare appliance you can download.  that could be handy if you have any trouble getting the LVM commands working in your distro.  just be aware that the default keyboard for that VM is not english.

---

### Post by Thelasko on 2008-09-08
The same way you recover data from a hard drive that won't boot.  A Live CD.

---

