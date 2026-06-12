---
title: "Ubuntu Server - Hardware, Partitioning, and Accessability"
date: 2009-05-22
forum: Server Platforms
---

### Post by daveb_78 on 2009-05-22
Hello All,
 
I am new to Ubuntu, and would like to ask the community for some assistance/advice on a new installation of Ubuntu Server. I am a long-time Windows guy, and a .Net developer. My passing familiarity with Linux, from university, is a rapidly fading memory.
 
I would like to install Ubuntu Server 9.04 for the sole purpose of being the host OS for VMWare Server 2. Initially, I considered using Windows Server 2008, but decided it was overkill for this single purpose. My hardware setup is:
[LIST]
[*]Intel Core 2 Quad Q6700
[*]ASUS P5B Mobo
[*]8GB DDR2 PC6400 RAM (though odly only 7.7GB detected by the System
[*]Monitor on the Ubuntu Desktop Live CD)
[*]Maxtor 250 GB STA HDD
[*]ATI Radeon X700 256MB Video Card
[*]Sound Blaster Audigy 2 ZS Sound Card
[*]NEC DVD-R/W Drive
[*]LG DVD-ROM Drive
[*]Logitech MX5500 wireless keyboard/mouse combo
[*]Samsung 275T PLUS Monitor
[/LIST]My questions are as follows:
 
**H/W Compatability**
 
[LIST=1]
[*]Are there any obvious "gotchas" to this hardware configuration, with regards to Ubuntu Server 9.04 Server AMD64? When I tried out the Desktop Live CD, I noticed that the total memory detected in the System Monitor was 7.7GB not 8.0....this would be more and oddity than a concern.
[*]Should I install the linux driver provided by AMD/ATI or stick with the Ubuntu native driver?
[*]I noticed that the numeric keypad on my keyboard cannot be used for numeric input (only direction keys) in the Desktop Live CD...can I expect this to be the same with the Server install?
[*]Initially, when the desktop Live CD boots into the GNOME desktop, my Keyboard/Mouse combo stop functioning. This is resolved by unplugging and re-inserting the USB dongle....can I expect this in the Server install (command-line) too?
[/LIST]**Partitioning**
[LIST=1]
[*]Can someone recommend a partitioning scheme for my purposes? I have read a wide-variety of schemes for other scenarios, but cannot seem to find one that I can identify as best for me. I plan to use LVM, would like to minimize the total number of partitions. Utilize the entire drive for Ubuntu Server. Have a dedicated partition for the VMs, which I believe appear to the host OS as large flat files. So I'm looking for recommendations on the total number of partitions, their respective size allocations, and file systems.
[/LIST]**Accessability**
[LIST=1]
[*]I have low-vision, and thus require accessible technology. Magnification is a must, and screen reading (speech/TTS) is a nice-to-have. I discovered Orca in the Desktop Live CD, and was impressed by the out-of-the-box feture-set. Is Orca supported in the Ubuntu Server command-line? Tips/advice is much appreciated.
[/LIST]Thanks in-advance. Apologies for the lengthy post. If it is adviseable to split this post into separate threads or another forum, just let me know and I'd be happy to do so.
 
Regards,
Dave

---

