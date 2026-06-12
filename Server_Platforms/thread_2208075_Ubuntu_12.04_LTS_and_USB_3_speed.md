---
title: "Ubuntu 12.04 LTS and USB 3 speed"
date: 2014-02-26
forum: Server Platforms
---

### Post by marcelgl on 2014-02-26
I recently upgraded my mainbaords to an asus B75M to be able to use USB3.  I bought an Icybox USB3 dock as well and had to copy 3TB from a SATA HDD to an HDD in the USB3 dock.  I checked transfer speed which 
remains below 30MByte/sec. 
It seems the drive is recognized as USB3 device. 

After this I connected the same disk to a SATA port and continued with the same copy action. With SATA-SATA speed > 130MByte/sec, so it seems disks are not the bottleneck. 

I read many articles and problems report related to USB3 ... does anybody knows why it is so slow.   Is there sombody which obtained copy speeds around 100MByte/sec with Ubuntu 12.03 and USB3 ?

Any oyjer suggestions ?

Thanks,

---

### Post by sudodus on 2014-02-26
Welcome to the Ubuntu Forums :-)

USB3 works for me (in a Toshiba laptop) and gives similar speeds as eSATA. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[Link to USB 3.0 Flash Drive Speed Tests]("http://usb.userbenchmark.com/") 
[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

Did you connect at the back of the computer (USB with blue plastic) according to this picture?

[https://www.google.com/search?q=asus+B75M&client=ubuntu&hs=sCm&channel=fs&tbm=isch&imgil=bCgbHotT3N4huM%253A%253Bhttps%253A%252F%252Fencrypted-tbn3.gstatic.com%252Fimages%253Fq%253Dtbn%253AANd9GcQZiM65hYG8orno30d-CmiTw0F_FWNvTiAYRDlJZVb9uyh09Xmk%253B853%253B495%253BM4gcYtcpG5HiUM%253Bhttp%25253A%25252F%25252Fwww.techpowerup.com%25252Fforums%25252Fthreads%25252Fasus-launches-microatx-motherboards-for-superior-htpc-performance.180628%25252F&source=iu&usg=__2EJ2TG6O9IxCRuJA79dzOApTOiI%3D&sa=X&ei=LkYOU6jVK-b54QSP1IEg&ved=0CFMQ9QEwBw&biw=1317&bih=892#facrc=_&imgdii=_&imgrc=jrPuVZIEoURSpM%253A%3B_jtkd3oTSb2o4M%3Bhttp%253A%252F%252Fwww.asus.com%252Fwebsites%252Fglobal%252Fproducts%252FEH9hY1FJNh6wDFyR%252Fline-01.jpg%3Bhttp%253A%252F%252Fwww.asus.com%252FMotherboards%252FB75MPLUS%252F%3B675%3B462](https://www.google.com/search?q=asus+B75M&client=ubuntu&hs=sCm&channel=fs&tbm=isch&imgil=bCgbHotT3N4huM%253A%253Bhttps%253A%252F%252Fencrypted-tbn3.gstatic.com%252Fimages%253Fq%253Dtbn%253AANd9GcQZiM65hYG8orno30d-CmiTw0F_FWNvTiAYRDlJZVb9uyh09Xmk%253B853%253B495%253BM4gcYtcpG5HiUM%253Bhttp%25253A%25252F%25252Fwww.techpowerup.com%25252Fforums%25252Fthreads%25252Fasus-launches-microatx-motherboards-for-superior-htpc-performance.180628%25252F&source=iu&usg=__2EJ2TG6O9IxCRuJA79dzOApTOiI%3D&sa=X&ei=LkYOU6jVK-b54QSP1IEg&ved=0CFMQ9QEwBw&biw=1317&bih=892#facrc=_&imgdii=_&imgrc=jrPuVZIEoURSpM%253A%3B_jtkd3oTSb2o4M%3Bhttp%253A%252F%252Fwww.asus.com%252Fwebsites%252Fglobal%252Fproducts%252FEH9hY1FJNh6wDFyR%252Fline-01.jpg%3Bhttp%253A%252F%252Fwww.asus.com%252FMotherboards%252FB75MPLUS%252F%3B675%3B462)

Try to find out if the bottleneck is in the computer or cable or Icybox!

Can you test in another computer? Most new laptops have USB3?

Can you test with another USB device, for example a good USB 3 pendrive?

Can you try another cable?

---

### Post by marcelgl on 2014-02-27
Thanks for your reply.   The ICY box, harddisk and cable are not the bottleneck. When  used on a Windows machine I get around 150MByte/sec.  The Cable is inside the blue USB3 connector. 


Bacause I suspected something which happened due to mainboard replacement I made a fresh install of the ubunto 12.04 server. 
After this I copied a single 10GB file, which took about 5 minutes, so approx 30MB/sec. 

So it seems clearly related to Ubuntu in combination with my mainboard (or some BIOS setting)

New info:
----------------------------
Installed a Ubuntu 13.10 server to see if that helps.   Copied a single 4GB file to the same dock and compared both USB2 and USB3 connections.

USB2 - 212sec => 19MB/sec
USB3 - 76sec   => 53MB/sec 

It is faster than with 12.04, but still not what I would expect.  It is an Asus mainboard with an i3-2100 @ 3.1GHz.


Also tested 12.04 with a USB3.0 raid enclosure (that's what I actually want to use) results are very disappointing, it took 70 seconds to copy a 100MB file. After this connected 
the raid enclosure to a windows machine.. approx 135 MB/sec. 


It is hard to believe performance is that bad, what can be the reason ?

---

### Post by marcelgl on 2014-02-27
To make a long store longer.... to be sure it was not related to my new mainboard I installed W7 on it and copied a few GB to the raid via USB3. 
transfer speed far above 120MB/sec.

Conclusion:

It is not the ICY dock
It is not the Fantec raid enclosure 
It is not the cabling
It is not the mainboard

It is clearly related to the USB3 handling of Ubuntu. Whether I use 12.04 or 13.10 I am not able to get higher transfer rates than 30-50MB/sec via USB 3. 
Very hard to believe I am the only one facing this problem. It is quite a mainstream MCB Asus wit Intel chipset.

---

### Post by sudodus on 2014-02-27
You have found a weak spot of Ubuntu. It is obvious that it cannot run USB 3 well with your motherboard.

The next version of Ubuntu is Trusty Tahr, and it is right now at beta 1 testing. I suggest that you download it and test if the USB 3 driver is improved.

[http://iso.qa.ubuntu.com/qatracker/milestones/312/builds](http://iso.qa.ubuntu.com/qatracker/milestones/312/builds)

---

### Post by oldfred on 2014-02-27
Was the format you used NTFS? 

The NTFS driver is not the fastest as it has to reverse engineer the NTFS configuration and uses an extra layer of logic in Linux.

---

### Post by marcelgl on 2014-02-27
Thanks for the replies. It was not NTFS, have tried it with both ext3/ext4 with similar results.  

"It is obvious that it cannot run USB 3 well with your motherboard"  This seems so, I would expext there are many more 
mainboards which use the Intel B75 chipset.   Probably will try to find an E-sata PCI card, might be the best solution for now. 
[h=1][/h]

---

### Post by sudodus on 2014-02-28
You need no PCI card, there are very simple ***eSATA adapters***, that connect to a SATA port, for example the one displayed at this page

[http://www.akasa.com.tw/update.php?tpl=product/product.list.tpl&type=Cables&type_sub=SATA%20Cable%20Adapters](http://www.akasa.com.tw/update.php?tpl=product/product.list.tpl&type=Cables&type_sub=SATA%20Cable%20Adapters)

---

