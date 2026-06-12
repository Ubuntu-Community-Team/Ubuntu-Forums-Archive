---
title: "Vmware cannot acces /dev/ttyS0"
date: 2009-01-21
forum: Virtualisation
---

### Post by svennils on 2009-01-21
Hi, i've just reinstalled vmware after deleting off my last windows partition on my laptop. I got everything up and running, but when i start the guest OS, vmware complains that "
"serial0: The "/dev/ttyS0" file does not appear to be a serial port: Input/output error.
Failed to connect virtual device serial0.""
the port is there and working, my user account is in the dialout group, port has root:dialout ownership, and i'm fresh out of ideas.Except maybe logging into ubunto as root, but that's a bit against the idea of os safety.

I've googled this, and searched the forums, tried chmod 666 on the tty, no change.
Minicom has the same issue, unless i run it as root. Running vmware as root (with gksudo) gives me a black screen in the guest OS, it somehow does not get the right screen res. from the x server, so it is not an option. How do i get get ttyS0 access? I need it for a programming cable, and it has been working before (some years since i used it).
Hoping for some help,
Sven.


Oh, and i'm running Ubuntu 7.10
Linux nc-ubuntu 2.6.22-16-generic #1 SMP Mon Nov 24 18:28:27 GMT 2008 i686 GNU/Linux

With vmware 6.

---

### Post by Dedoimedo on 2009-01-21
Is any device connected to this port?
Can you try a different serial port, like ttyS1??
Dedoimedo

---

### Post by svennils on 2009-01-21
I've done som more tinkering, an come up with the following:
By looping pin 2&3 on the serial port, i should have echo in minicom (run with sudo). I don't. So i tested this on a second ubuntu laptop, same result.  Next i plugged in a xircom usb-serial adapter, ttyUSB0, and got echo if pin 2&3 were connected. So obviously something is missing. I cannot use the usb dongle because the windows software does not support it in a naitve windows installation ,let alone in vmware (dont ask me why, schneider just said it was so, and offered me a usb programming cable at the price of a docking station with serial connector. i chose the latter). Would have been an easy solution though. 
Dmesg provides the folloving on serial ports:

[   14.759186] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.759286] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   14.759710] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[   14.760229] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

Ls /dev/ttyS* -l provides the folloving:

crw-rw---- 1 root dialout 4, 64 2009-01-21 17:49 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-01-21 17:49 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-01-21 17:49 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-01-21 17:49 /dev/ttyS3

I have no idea what the dmesg listing of ttyS2 is for, and why i have ttyS1-3 at all. 

Obviously this problem changed to a "i cant communicate trough my serial ports either" type of case. Irq 4 and 3f8/3e8 is normal for the first and third serial port so what is amiss?

Any ideas?

---

### Post by svennils on 2009-01-21
Ok, more googling, and a posting on [http://www.linuxforums.org/forum/redhat-fedora-linux-help/85411-dev-ttys0-nc6000-not-working.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/85411-dev-ttys0-nc6000-not-working.html)

looks interesting. He has a hp NC6000, i have a hp NC8000 and the old compaq Evo n800v, compatible. Neither have had the serial ports active in linux for 2 years due to native windows partitions. But they have worked on the  Evo n800 in vmware. He found that pnpacpi=off in the kernel parameters in grub.conf (or menu.lst in my case) solved it. Now where in the boot parameters do i put this line? Among the common parameters at the top did no good. 
Seems i have these too:
24.776000] ttyS0: LSR safety check engaged!
24.776000] ttyS2: LSR safety check engaged!

Trying in the kernel options. Hope it works, rebooting now.

---

### Post by svennils on 2009-01-21
Ok, that did not help. I'll try more tomorrow.

Ok, problem solved. Seems that the smsc_ircc2 irda module screws up the serial ports, and as i dont need irda, i blacklisted them. ttyS0 works fine in vmware and minicom, my plc communicates nicely with the programming software.

---

