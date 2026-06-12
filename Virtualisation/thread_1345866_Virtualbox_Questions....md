---
title: "Virtualbox Questions..."
date: 2009-12-04
forum: Virtualisation
---

### Post by ngrieb on 2009-12-04
Hi,
I had a few questions about Virtualbox that I am sure people can answer. I am not too familiar with virtual machines, although I think I understand the concept. As far as I can tell VB simply boots another OS through your currently running OS (please correct me if I am wrong). 

I have a 2 HD machine, one which is smaller and has Windows 7 on it, and the other, which has Ubuntu 9.10. Can I run my Windows hd using VB under Linux without rebooting and chosing the grub boot option etc.? I really would like some more info, as people all seem to love VB and it sounds very promising.

Thanks.

---

### Post by Druke on 2009-12-04
you will first need to run something like [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/) to convert the windows disc into a virtual drive. The vm cannot exist os both a vm and a real install at the same time, however it can be emulated ,to an extent, via shared folders.

---

### Post by Druke on 2009-12-04
I tihnk norton ghost will do it as well... vmwre converter may not be what I thought.

---

### Post by ngrieb on 2009-12-04
So will the programs I have installed be intact after I convert? What are the limitations? 

Is it possible to convert my convert my Windows drive onto a chunk of my Linux drive so I can also have a real Windows boot?

---

### Post by Druke on 2009-12-04
yes, it will basically clone your windows hard drive, and make it a large file on your linux hard drive.

You will need to set up shared folders between your cloned drive and your windows hd if you want any sort of syncing.

---

### Post by ngrieb on 2009-12-04
So then do I need to set up a VB file as large as my Windows hd? I have 80GB Windows, 160 Linux...

---

### Post by Druke on 2009-12-04
if you are doing that sort of conversion, I think you will have to have an 80gb file on linux

---

### Post by ngrieb on 2009-12-05
Ok, I think I have enough space on my hd. Is there some kind of tutorial I could use to get through converting a drive to a virtual drive, and how to create a shared partition?

---

### Post by bingoUV on 2009-12-06
> **ngrieb said:**
> So will the programs I have installed be intact after I convert? What are the limitations? 

Is it possible to convert my convert my Windows drive onto a chunk of my Linux drive so I can also have a real Windows boot?

Maybe you already know this, but :

Since the hardware in real windows and virtual windows is different, you cannot keep switching between booting the real windows and virtual windows. This is because drivers will be stored in hard disk, (disk image in case of virtual); settings of drivers will be stored in registry etc.

---

### Post by blues_1pt on 2009-12-06
Hi people, i'm new at the forum.....I have a W5F from  ASUS, with 1 Gb of RAM and a disc of 100Gb, nothing special. At this time, i am thinking of installing Ubuntu at my labtop, but I want to install a virtual machine in it with windows. 
Can anyone tell me, which virtual machine is lighter for my pc (i will put windows XP)?
And is it difficult to put internet working at the VM?
Thanks for your help.

---

### Post by ngrieb on 2009-12-06
What do you mean by keep switching? Even if the virtual windows is on a different hard drive? (I am currently dual booting with 2 HDs. )

---

### Post by bingoUV on 2009-12-07
> **ngrieb said:**
> What do you mean by keep switching? Even if the virtual windows is on a different hard drive? (I am currently dual booting with 2 HDs. )

Keep switching means - Boot the same windows installation alternately from:

1. VM within linux.
2. Directly booting windows as you did prior to the VM creation.

It does not matter if the virtual windows is a different hard drive or not. Once you boot this virtual windows from VM within linux, you will have problems booting it directly. Then if you do succeed in booting it directly by re-installing drivers etc., you will now have problems in booting it from a VM.

---

### Post by ngrieb on 2009-12-11
Hmmm ... I'm very confused now. Will cloning the windows drive corrupt the boot record and drivers even if I clone the windows drive to a totally different partition? I realize that the virtual copy would no longer be able to keep up with updates etc. on the newer half but don't really care about this. :confused:

---

### Post by joes7 on 2009-12-11
Get VMWare.

---

