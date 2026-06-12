---
title: "Windows 10 write access in encrypted USB with luks+ext4 ?"
date: 2015-10-24
forum: Windows
---

### Post by NikTh on 2015-10-24
Hello, 
this problem is quite complicated for me and given that my English are not good enough, I will try to describe it as best as I can but bear with me and ask for any info I might miss writing here.

I have a USB encrypted with luks+ext4. This USB has been encrypted long time ago in Ubuntu 14.04 LTS with the Disks program(utility). Also I have a partition with Windows 8.1 that recently updated to Windows 10. Recently I mean before 10 days(almost). 

Before 2-3 days I have discovered a weird folder in this USB that indicated Windows interaction. The folder was named "**System Volume Information**" and inside was a file named **IndexerVolumeGuid** which contained a number (guid like number). 

After further searching I have also discovered some event logs in Windows for this device (USB stick). I'm quoting here the logs in pictures. 

[IMG]https://farm6.staticflickr.com/5697/21793825853_1bd979bb1b_c.jpg[/IMG]   


[IMG]https://farm1.staticflickr.com/741/21793826393_6f2a7ae965_c.jpg[/IMG]



[IMG]https://farm1.staticflickr.com/688/21793826763_5e63e25143_c.jpg[/IMG]

The Guid Class number is the number I have found inside the IndexerVolumeGuid file.

I want to highlight that I haven't installed any ext4 like program or driver in Windows, neither a decryption program like LibreCrypt or anything. Actually I'm not using Windows so much but for 1-2 programs only. I'm avoiding to attach this USB in any other operating system except the two I'm using most (Ubuntu, Arch). Sometimes maybe I'm forgetting to detach the USB from the port and I guess this is what happened when I have booted in Windows 10.   

Another weird behavior is, If I attach the USB in Windows 10 (because I have tried some things in order to reproduce this problem) a letter is assigned in this USB ( ie Drive I: ) despite that is an ext4 unsupported file-system. I'm getting the usual messages for "Formatting the driver" and/or "The operating system is unsupported".

Google Search didn't give me any clear answers , or I didn't search with the right keywords.

The only I could possibly think might happened is, in someway Windows accessed this USB through VMWare ? I have VMware Workstation installed in Windows 10 (host) and several Linux distributions there (as guests) but I have never decrypted(opened) the USB in VMware. 

Unfortunately I cannot reproduce this problem. I have tried several things like: 

Booting several times in Windows with USB attached already in port 
Booting in Windows and attaching the USB after I'm reaching the desktop.
Opening the VMware and attaching the USB (also detaching from host and attaching it to guest). 

What could possibly happened here? Any hint, but any, will be appreciated.

---

### Post by howefield on 2015-10-24
Thread moved to the "*Windows*" forum.

---

### Post by NikTh on 2015-10-24
I'm not quite sure if this is a Windows related issue
or an issue in Ubuntu ( or even a security flaw, in luks? ) because there I have encrypted the USB. 
Windows shouldn't have any kind of access in that USB stick.

---

