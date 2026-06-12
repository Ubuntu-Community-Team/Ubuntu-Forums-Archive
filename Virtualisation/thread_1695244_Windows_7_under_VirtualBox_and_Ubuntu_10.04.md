---
title: "Windows 7 under VirtualBox and Ubuntu 10.04"
date: 2011-02-25
forum: Virtualisation
---

### Post by m1d4p5 on 2011-02-25
Hello,

   I have a DELL Vostro 3300 i5 520 with 4GB RAM DDR3, and with dualboot Windows 7 and Ubuntu 10.04 LTS (both 32bits).
 
   I'd like to run Windows 7 (instaled on my sda3) under VirtualBox 4.0.4, and mantain the dualboot.
 
   I tried: 
    [http://www.rajatarya.com/website/taming-windows-virtualbox-vm](http://www.rajatarya.com/website/taming-windows-virtualbox-vm)
    [http://blog.amhill.net/2010/01/27/linux-ftw-using-virtualbox-with-an-existing-windows-partition/](http://blog.amhill.net/2010/01/27/linux-ftw-using-virtualbox-with-an-existing-windows-partition/)

   But the best I'd achieved was a "Starting Windows 7" screen forever running. :confused:
  
   Some extra information fdisk and partitionlist is attached.

Can somebody help me?

Thanks,
Tony

---

### Post by m1d4p5 on 2011-02-27
Nobody?

---

### Post by Hedgehog1 on 2011-02-27
Here is the thing - it is possible (there is a massive thread about it): [http://ubuntuforums.org/showthread.php?t=984437]("http://ubuntuforums.org/showthread.php?t=984437")

But as you read through this thread, you will see that if you don't close down your vbox 'pointer' to your real windows parition properly, you will hose ***<technical term: hose>*** your windows partition.

If you want to relocate your windows partition into vbox, that makes more sense to me.

I keep my Win7 Vbox as a desktop icon in Ubuntu, works great.

However, I don't want to discourage your trying what you read in the thread; but PLEASE backup you data before you try it.

:KS

---

### Post by m1d4p5 on 2011-02-28
Thank you very much Hedgehog1,
   I'll try and post the news here.
Bye,
Tony

---

### Post by m1d4p5 on 2011-02-28
Hello again,

  I did everything that was proposed on the tread but no success yet. I even tryed that WATRemover, but the starting windows screen persists. :confused:
  I think that the problem is with WIN7 or the MBR file, because it start the base system but didn't go on.
  Any idea?

Tony

---

