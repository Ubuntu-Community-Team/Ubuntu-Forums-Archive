---
title: "ubuntu server will not boot up"
date: 2011-02-20
forum: Server Platforms
---

### Post by 1gryan on 2011-02-20
hi all, I am new to networks and server so do call me stupid if I have missed something obvious. right I was installing ubuntu 10.04 server to a old computer(it did comply with all minimal specs)and we had a power cut, and now the computer will not boot up ... it powers up, the fans go on and the hard drives spin, but there is no visual display, so I cannot get onto the bios or boot to disk. and there is no bleeps or error codes:( I think I may have corrupt the MBR *I think it is GRUB in ubuntu. Can you please help me I am really stuck on what to do. I have also checked internal components and replace the bios battery.

---

### Post by nashibuntu on 2011-02-20
While I am waiting for someone to answer one of my questions, I might as well try to help out here. I recently upgraded a server to 10.04 (then 10.10) and had a similar problem. The monitor (an old CRT one) was blank. It think they removed some support for older monitors. Quite annoying that they did that for server versions without any warning. Anyway, I was still able to get access via ssh. I then modified by /etc/default/grub.cfg to contain this line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=3847 nomodeset"

and did

update-grub

I think it's the nomodeset command in particular that sorted the problem out. Hope that helps.

---

### Post by trundlenut on 2011-02-21
I would say it is a hardware fault if you have no display at all and can't access the bios.

I would try a different monitor, graphics card and also prehaps try booting the machine with the hard drives disconnected and the memory removed.  It could well be that the motherboard is bust.

---

