---
title: "Can I install Ubuntu on an external SSD ?"
date: 2018-07-18
forum: Ubuntu, Linux and OS Chat
---

### Post by automate-stuff on 2018-07-18
My laptop has a USB 3.1 gen2 port which supports 10gbps transfer rate...

I want to know whether I can install Linux on a USB 3.1 gen2 external SSD...Can I do that ? should I buy an external SSD ?



Many Thanks

---

### Post by oldfred on 2018-07-18
Moved to chat since not specific technical issue on Ubuntu.

I have an old SSD that I originally used with my old BIOS system. To see how well it worked I bought a USB to SATA adapter & pluged it in.

Its an oem Microcenter SSD from 2011, shown as ADP 60GB.
      ```
 /0/100/14/1/3/0.0.0    /dev/sdc    disk           60GB ADP-07U3
sdc                                                             
&#9500;&#9472;sdc1  vfat   EFI_SSD64   7B30-5ACA                            
&#9500;&#9472;sdc2                                                          
&#9500;&#9472;sdc3  ext4   bionicSSD64 2c25bc79-df54-400f-8df3-e6bc15ff7bc2 /media/fred/bionic
&#9492;&#9472;sdc4  ext4   cosmicSSD   f4a5523a-b8b2-4c96-9fb2-bd9109ed09c2 /media/fred/cosmic 

```    

I have done multiple full installs in BIOS & UEFI to flash drives and it takes about 40 mins with my USB3 ports & USB3 flash drives.
My installs to internal SSD take less than 10 Min. 
So I was quite surprised when my installs to the external SSD was about 10 min. I thought USB3 would be limit, but it really is write speed.

UEFI is more complicated.
But whether UEFI or BIOS you have to partition in advance. I only use gpt, now whether BIOS or UEFI.

And USB does not support trim. So I will have to plug old SSD in regularly to SATA port if I was using it more frequently. 
I believe many newer SSD have internal trim capability, but that is something you need to check, first.

---

