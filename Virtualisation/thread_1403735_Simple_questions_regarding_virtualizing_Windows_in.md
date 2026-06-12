---
title: "Simple questions regarding virtualizing Windows in Ubuntu."
date: 2010-02-10
forum: Virtualisation
---

### Post by hxcobd on 2010-02-10
I'm on 32-bit 9.10, for the record.

I've never bothered virtualizing Windows before, and have always just set up dual-boot for using both Windows and linux.

I'd love to eliminate the need to dual-boot, though.

I primarily would like to run graphics applications from Windows within Ubuntu 9.10, including Fireworks and Photoshop. I'd really love it if my tablet would work in a virtual machine, also.

So, questions:

1.) If I run Windows 7 from within Ubuntu, will all my hardware work, including my Wacom tablet?

2.) Will performance be adequate for Adobe products?

3.) Is there a big difference between Virtualbox and VMWare? Which is preferrable?

I don't intend to run games or anything really graphics-intensive, so I'm not overly concerned about performance, as long as productivity programs are usable.

Thanks for the help!

*edit - Just answered a few of my own questions; looks like Virtualbox is the easiest to use free solution out-of-the-box, and only its PEUL version supports USB devices. I'll be using that, I suppose!

---

### Post by TJet1.8 on 2010-02-10
Well...I don't know if I can answer "all" your questions...but here goes...

1.) Depends on the hardware. If you have all USB devices, then yes...it will work. If you have "specific" devices in say, the pci slots in your computer...then it's iffy. You will need to test to see if your non-USB device work or not.

2. I can't comment on performance of adobe products as I don't run any. Generally speaking, if you give your vm enough resources...performance should be adequate.

3.) There's not too much difference between virtualbox and vmware. I find that USB devices and general disk performance runs better in vmware. The difference is negligible, but I notice a difference between the 2 when using skype with my usb webcam...vmware is much smoother.

VMware Player is also a free, easy to use solution that "includes" USB support under a PUEL license.
You can also download a free copy of VMware's P2V Converter...which will convert your Physical Hardware & Operating System to a Virtual Machine for you...VERY easy way to convert your O/S from physical to virtual.
I don't believe VBox has such a utility...which means you will have to use some 3rd party utility (such as Ghost) to make an image of your O/S...and then restore to your VBox virtual machine.

The P2V Converter can also be used for VBox...BUT, it will ONLY create a VMware Virtual Machine Disk file (e.i. - ????.vmdk)...but VBox has a utility that allows you to convert a VMware .vmdk disk file to a VBox disk file.

Good luck...and have fun :)

Your best bet is to try both and see which one you like best.

---

