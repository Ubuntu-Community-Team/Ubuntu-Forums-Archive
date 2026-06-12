---
title: "Getting back to Ubuntu"
date: 2010-09-24
forum: System76 Support
---

### Post by michaelpagz on 2010-09-24
Hello. I have a Star3 that I got recently. Dummy that I am, I decided to try Meego on it. I installed it and then decided almost immediately I didn't like it. 
I have installed and reinstalled Ubuntu a thousand times using unetbootin. 
I am not sure why but this time the usb installer is completely ignored and Meego boots. 
I have tried f12 and I have also tried going into setup and changing the boot order. 
 Thinking it might be the iso or something I tried it on a different computer and it responds normally. I am not sure what is going wrong. 
Any suggestions? 
I know this isn't technically a system76 problem but I figured I'd give it a shot. 
Thanks

---

### Post by gamerchick02 on 2010-09-24
Did you tell the installer to overwrite your partitions?

When you get to the partitioning scheme, either tell it to take over the entire drive, or tell it to pick the partitions.

Overwrite your / partition, and if you don't have anything in your /home, you might as well overwrite that too.

Amy

---

### Post by michaelpagz on 2010-09-24
Unfortunately, I can't even get to the Ubuntu installer itself. Sorry if my description wasn't clear I can see the confusion. What I meant was that the bootable USB is not even recognized. The netbook boots to meego as if no USB were inserted at all. It doesn't allow the installation of Ubuntu to begin at all. Sorry for the confusion.

---

### Post by michaelpagz on 2010-09-24
Okay so I got it recognized by formatting the USB as a FAT partition. Now I am getting the initramfs busybox error. I am not sure how to fix this. Is there a netbook edition alternate install?

---

### Post by michaelpagz on 2010-09-27
Got it working with 10.04.

---

