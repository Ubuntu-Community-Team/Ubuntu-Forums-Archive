---
title: "Using not so light apps like CorelDRAW/Illustrator/Photoshop in Virtual Windows"
date: 2016-03-18
forum: Virtualisation
---

### Post by LSHINE on 2016-03-18
I'd like to ask those who used apps like these in Virtual Windows Box (In Linux) professionally - Would it perform well on larger vector files? Is the performance smooth (I have 6gb of ram, 2,2 ghz dual core Pentium)? Any other nuances?

---

### Post by MAFoElffen on 2016-03-18
The following is the System Requirements that Corel says you need to be able to run Cprel Draw Graphics Suite X8
> 
[COLOR=#494D56][FONT=Hum777n][SIZE=4]**System Requirements**[/SIZE]
[/FONT][/COLOR][COLOR=#494D56][FONT=Hum777n]

[LIST]
[*]Microsoft Windows 10, Windows 8.1 or Windows 7, in 32-bit or 64-bit, all with latest Updates and Service Pack
[*]Intel Core i3/5/7 or AMD Athlon 64
[*]2 GB RAM
[*]1 GB hard disk space
[*]Multi-touch screen, mouse or tablet
[*]1280 x 720 screen resolution at 100% (96 dpi)
[*]Microsoft Internet Explorer 11 or higher
[*]Microsoft .Net Framework 4.6
[*]DVD drive (required for box installation)
[*]Internet connection required to sign in to authenticate CorelDRAW Graphics Suite, receive performance and stability updates, access online content, and use some features, such as QR Codes or the Content Exchange. You can use CorelDRAW Graphics Suite offline provided you connect to the Internet at least once a month so that we can validate your software license.
[/LIST]
[/FONT][/COLOR]

So your "Pentium" would not even be able to run it if if it was running native Windows as the main OS without being in a Hypervisor. 

But their requirements list is comparing apples to oranges, when it mentions AMD Athlon 64. Comparably, if that were so, then a Pentium would all that would be required.For high resolution in a VM, you would add a VT-x IMMU requirement.... If it checks for an i3 or above (CPU codes) then you will need a type 1 hypervisor to be able to copy the host CPU or emulate a lesser CPU of the same make...

Those are the first 3 problem I see with yours... But you also did not say which model Pentium, so I can only answer generically.

---

### Post by LSHINE on 2016-03-20
I wasn't talking about the latest software. I run CorelDRAW X6 and AI CS6 on my lappy perfectly. My concerns are X6 and CS6.

---

### Post by MAFoElffen on 2016-03-21
LOL. Now we have a version:
> 
[SIZE=4]_**CorelDraw 6**_[/SIZE]

[LIST]
[*]Microsoft® Windows® 8 (32-bit or 64-bit Editions), Microsoft® Windows® 7 (32-bit or 64-bit Editions), Windows Vista® (32-bit or 64-bit Editions), or Windows® XP (32-bit), all with latest service packs installed
[*]Intel® Pentium® 4, AMD Athlon&#8482; 64 or AMD Opteron
[*]1GB RAM
[*]1.5GB hard disk space (for typical installation without content - additional disk space is required during installation)
[*]Mouse or tablet
[*]1024 x 768 screen resolution
[*]DVD drive
[*]Microsoft® Internet Explorer® 7 or higher
[/LIST]

AI CS6 spec's are similar...

Those versions look like they might run on a 32 bit Windows VM guest in VirtualBox with the Extension Pack installed. I just checked... I have CorelDraw, Adobe Photoshop CS and Indesign CS. Yes, the requirements look like they would go fine in most virtual machines on your hardware.

---

### Post by LSHINE on 2016-03-21
Thanks.

What Extention Pack is that? Do I need to install it manually? I have no experience with VM's, this would be my first time running it, so any tut's are very much appreciated.

---

### Post by LSHINE on 2016-03-21
Also, would there be any difference what Linux Distro I use to run a VM in?

---

### Post by MAFoElffen on 2016-03-21
IMHO-- Yes. With a 2-core Pentium 4, the least amount of overhead on the based OS on the host is going to give you better performance of the hypervisor and it's guests.

For instance Ubuntu (unity) and Ubuntu Gnome want about 1 GB as a minimum. Lubuntu can run in 256 MB. But you have 8 GB. As a rule of thumb, you can allocate about half your memory to a guest with no problems.  But being you have 8 GB, you could get away with allocating 6 GB.

What is going to be your bigger concern is that you have plenty of disk space and fast form-factor disk storage. Your are looking at about a 2 to 3 GB disk image for a full Win System and what those 2 programs recommend. That is a lot of disk IO... and that is where your performance restrictions might lie. Remember to do backups of that disk image. That is a lot of real-estate for a problem to occur on (for a disk image).

---

