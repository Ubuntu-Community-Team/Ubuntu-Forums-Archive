---
title: "Thinking aloud - Extending VBox images w/LVM"
date: 2008-09-28
forum: Virtualisation
---

### Post by Greyed on 2008-09-28
This is just me thinking aloud here.  VBox currently is incapable of extending the size of the image.  However having recently installed 8.04 onto an image it dawned on me that we might be able to address that.

The 8.04 install (of KUbuntu at least) asks of we want guided partitioning.  One of the options in guided partitioning is to partition with LVM.  Normally I'd say no since, really, it's just a VM.  However LVM allows combining of volumes across different hard drives into a single partition.  I know ReiserFS can be extended (on the fly no less!) and I believe ext3 can as well.

So a simple solution to the problem would be to ensure to install with LVM.  If the original image gets tight, create a new VDI, extend the LVM volume onto that new VDI, then extend the file system into the expanded LVM.

Does this sound plausible or am I missing something painfully obvious which whould make it non-viable from the start?

---

### Post by lazyart on 2008-09-30
That makes perfect sense.  Pretty clever idea.

What I tend to do when I need more space is the same thing I do with a physical machine-- buy a new hard drive, clone the old to the new and resize.

Create a new disk.  Boot to a Clonezilla iso and copy.  Boot to GParted to fill out the space.  Finally, delete the old disk (once you've seen that it works).  I haven't had to do that with a Linux VM yet, but did do it with a Windows VM recently.

---

### Post by Delvien on 2008-09-30
> **Greyed said:**
> This is just me thinking aloud here.  VBox currently is incapable of extending the size of the image.  However having recently installed 8.04 onto an image it dawned on me that we might be able to address that.

The 8.04 install (of KUbuntu at least) asks of we want guided partitioning.  One of the options in guided partitioning is to partition with LVM.  Normally I'd say no since, really, it's just a VM.  However LVM allows combining of volumes across different hard drives into a single partition.  I know ReiserFS can be extended (on the fly no less!) and I believe ext3 can as well.

So a simple solution to the problem would be to ensure to install with LVM.  If the original image gets tight, create a new VDI, extend the LVM volume onto that new VDI, then extend the file system into the expanded LVM.

Does this sound plausible or am I missing something painfully obvious which whould make it non-viable from the start?

Good idea, but not sure if it would work, it seems too simple though, theres probably some restriction somewhere. Lemme know if it works.

---

### Post by Greyed on 2008-10-02
For the record, it works perfectly.

I have an Ibex alpha 6 image I've been tinkering with.  I archived it to prevent the re-install blues if I mucked something up.  It took a little bit of noodling around but I got it to work.

In VBox's disc manager I created a new 2Gb image and assigned it to the VM.  Booted into it and found it was there as /dev/sdb.

Then the sequence was something like this:

```

pvcreate igtest /dev/sdb
vgextend igibex /dev/sdb
lvextend /dev/igibex/root /dev/sdb
resize2fs /dev/mapper/igibex-root

```Obviously the names of the volumes will differ from person to person.  The end result, however, was that my 7.75Gb partition was extended to 9.75Gb.  Usage went from 35% down to 29%.

---

### Post by HermanAB on 2008-10-02
Interesting trick - however I use NFS.  I create a NFS share on the host and mount it in the VM, then put my data there.  The upshot is that the VM guest remains small and manageable and all the data is in one place and can be easily backed up by the host.

---

