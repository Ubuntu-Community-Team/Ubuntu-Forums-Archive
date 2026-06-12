---
title: "Problem with 12.04 install on Dell PE1600SC"
date: 2013-03-07
forum: Server Platforms
---

### Post by orientdude on 2013-03-07
[COLOR=#000000]Hello All,[/COLOR]

[COLOR=#000000]I am a complete noob here, so apologies first and foremost to resurrect a previous tread.[/COLOR]

[COLOR=#000000]I have Dell 1600SC with dual Xeon CPUs and 4 SCSI drives. I have tried installing the server 12.04 edition but with no joy. The SCSI drives are setup and partitioned correctly, as it was a 'next-select-next-continue-etc.' process without problems. Only at the end with the reboot it triggers the error message as follows:[/COLOR]

[COLOR=#000000]"1:Auto Detect/AnalogInput Cannot Display This Video Mode: Optimum resolution 1680x1024 60Hz"[/COLOR]

[COLOR=#000000]I think the Dell has the Rage ATI 8MB graphics card. I have tried all 'vga=xxx" modes, but nothing.[/COLOR]

[COLOR=#000000]Please can anyone show me the correct path to complete the installation? Otherwise, I ave a dead server![/COLOR]

[COLOR=#000000]Thanks in advance to all.

[/COLOR]

---

### Post by cheshire mouse on 2013-03-07
If you were asked to reboot the server, then installation is completed. 
 Start ubuntu and connect via SSH (did you select OpenSSH package during the installation?)

Add **GRUB_GFXMODE=640x480** to the [B]/etc/default/grub

[/B]run **update-grub** and restart the server

more about grub [https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)

---

### Post by orientdude on 2013-03-08
Thanks for your reply Cheshire Mouse.

I did install the Open SSH package, but how do I connect via SSH upon bootup? Also, how do edit (or text editor) the grub.cfg when I have no OS running yet?

Thanks again.

---

### Post by cheshire mouse on 2013-03-08
If i got it right, your monitor shows you an error message AFTER you start ubuntu from grub menu. If so, don't worry about this message, just wait about 5min till the system finishes boot process and try to connect  from another PC via SSH

---

