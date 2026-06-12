---
title: "USB HDD (win7) to 2 PC's in dual boot"
date: 2016-07-04
forum: Ubuntu Studio
---

### Post by uBoldie on 2016-07-04
Hi All
I have 2 PC's with Ubuntu Studio 16.04 (64 bit) on them.
One PC is a tower, the other is a laptop with UEFI.
The laptop HDD has now been changed to SSD running Ubuntu Studio.
The old laptop HDD has only Win 7 on it in working order.
I plan to purchase a USB/Sata interface to this older HDD so that I can use Win7 via USB to either PC in dual boot mode.
I am not sure what I need to do, software-wise for my plan to work.
I would appreciate any advice to achieve my goal. Can anyone assist me please as I am not sure about Grub2.
I have not found any similar requests by others when searching the web.  TIA.

---

### Post by sudodus on 2016-07-04
It is straight-forward to run linux from a USB drive. But ***Windows does not boot from USB***. I think it is because Microsoft limits the usage of each system to one computer.

A workaround could be to install an Ubuntu flavour (in a USB HDD), install a virtual machine (for example VirtualBox), and install Windows in the virtual machine.

There are many USB/Sata interfaces/boxes that work well. There are also interfaces that can also connect via eSATA, which is much faster than USB 2.

I have a box from StarTech 'USB3.0/eSATA Trayless 3.5" HDD Enclosure with UASP', but there are many other alternatives. If you need only USB (not eSATA), you can find many less expensive alternatives.

---

### Post by oldfred on 2016-07-04
When USB3 was new and when multi-TB drives were new we also saw many USB enclosures that did not work with either USB3 or gpt partitioned large drives.

So best to check to make sure you have newer USB enclosure.

---

### Post by uBoldie on 2016-07-05
Thanks for your replies.
I mainly use Ubuntu Studio and not really interested in Windows, except I have to use it for CAD & CAM software mainly.
Accordingly UbS is preferred on my internal HDD and sharing Win7 between PC's would be an ideal preference.
I have tried WinXP with VirtualBox and that worked out quite well, so the tower machine can work that way again.
Since my laptop has SSD now I'm not sure that using VirtualBox would be a good idea due to wear levelling. 
When I think about it a hard disk must suffer wear levelling (especially when Windows is the OS) too.
Hmm...   I play with PIC chips using Windows down in the shed and the laptop is the most convenient way to test my programs.
The idea of putting the Windows disk back on my laptop and having UbS getting the external USB drive space is an unpleasant thought.
There has to be another way of doing things.
@Oldfred - I'm over 70, so I guess I'm in that 'old' bracket also.

---

### Post by oldfred on 2016-07-05
I have pretty much stopped worrying about SSD life.
I still change some settings to reduce writes, but use SSD primarily as system partition and have most data on HDD.

       SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)
SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)
[http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb](http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb)

---

### Post by uBoldie on 2016-07-10
Thanks Oldfred for the above info on SSD lives.  I read quite a lot of it to realise (not that understood all the tests) that I don't have to worry about it.
I think I'll make the laptop SSD work in dual boot mode and keep the data space in NTFS as Ubuntu Studio can read & write in that format.
Not sure if I can claim that my problem is solved though. My old USB HDD can be more data space.
Thanks again.

---

