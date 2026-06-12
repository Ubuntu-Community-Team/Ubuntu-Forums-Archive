---
title: "Boot Kernel messages to another TTY (problem)"
date: 2008-05-13
forum: Server Platforms
---

### Post by promodus on 2008-05-13
*
I want to set kernel messages to be on another tty on boot. 
I have set in /boot/grub/menu.1st at the end of my kernel options I have set 
 [FONT="Courier New"]kernel  /boot/vmlinuz-2.6.24-16-generic root=UUID=fe5d20c8-8f1d-48a3-a15d-ab8a86ce2902 ro console=tty7 quiet[/FONT]
Which is great, I get all kernel messages there except for 3.

I get:
[FONT="Courier New"]Starting up ...
[80379.250223] sd 2:0:0:0: [sda] Assuming drive cache: write through
[80379.250418] sd 2:0:0:0: [sda] Assuming drive cache: write through
[80381.317500] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled![/FONT]

Then finally I get my tty1 from /boot/event.d/tty1

Anyone have any idea how to get rid of those last 3 boot messages?
Thank you kindly in advance.

---

### Post by promodus on 2008-05-13
I assume stdout has gone to tty7
it's stderr that is still showing up on tty1.

Any ideas?

---

### Post by promodus on 2008-05-13
It appears as I had thought. These are stderr messages.

I have found this option for grub:
[FONT="Courier New"]loglevel=[/FONT]
And the options are from 0 to 7 being:

0 (KERN_EMERG)		system is unusable
1 (KERN_ALERT)		action must be taken immediately
2 (KERN_CRIT)		critical conditions
3 (KERN_ERR)		error conditions
4 (KERN_WARNING)	warning conditions
5 (KERN_NOTICE)		normal but significant condition
6 (KERN_INFO)		informational
7 (KERN_DEBUG)		debug-level messages

(taken from kernel documentation kernel-parameters.txt)
However, I'd rather not suppress these errors, I'd rather have them on another TTY. This I have not found an option for in kernel-parameters.txt

I hope someone has an idea...

---

