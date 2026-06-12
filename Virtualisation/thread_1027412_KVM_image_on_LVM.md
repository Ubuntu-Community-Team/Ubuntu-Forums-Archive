---
title: "KVM image on LVM"
date: 2009-01-01
forum: Virtualisation
---

### Post by kasper22 on 2009-01-01
Hi guys,

I've got everything setup almost the way I want it with KVM.  The last step I would like to do is move the guest images from file to running off LVM.  This seems like it should be really simple and I have two sources: [http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-8.10-p4](http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-8.10-p4) and [https://help.ubuntu.com/community/KVM/CreateGuests](https://help.ubuntu.com/community/KVM/CreateGuests) (this is general for block devices) both say all I should need to do is run:

qemu-img convert disk0.qcow2 -O raw /dev/vg/lv

I've tried this with a ubuntu image and a windows xp image.  Neither one seems to work.  When I load the ubuntu image and then vnc in I see a messages that says crc error.  On the windows it just says disk boot error.

Is there something else that I'm missing?  The only other step I see is that the config file path needs to be updated (which I've done).  I'd be grateful for any advice.

Thanks,
Bryan

---

### Post by EightBitHustler on 2009-01-01
I managed to get this working, but I had separate issues (forgot to enable the CPU virtualization extensions in the CPU)

I posted the XML dumps from libvirt along with a few benchmarks.

[http://ubuntuforums.org/showthread.php?t=1026006]("http://ubuntuforums.org/showthread.php?t=1026006")

Maybe something there will help you. I followed the same tutorials you used.

---

### Post by frippz on 2009-01-14
Just experienced this mishap myself on two recently created machines, and of course I didn't backup my orginal images due to a small system partition. I hate myself...

I followed the guide at Howtoforge as well. Oddly enough, I couldn't find any comments in their forums about this. There's bound to be more people around that have experienced these problems.

---

### Post by frippz on 2009-01-15
Just wanted to post a follow-up. I've posted in Howtoforge's forum and Falko (the author of the guide) is helping me solve this issue (no luck as of yet though).

[http://www.howtoforge.com/forums/showthread.php?p=164751](http://www.howtoforge.com/forums/showthread.php?p=164751)

---

