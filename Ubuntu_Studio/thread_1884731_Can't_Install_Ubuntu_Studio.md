---
title: "Can't Install Ubuntu Studio"
date: 2011-11-21
forum: Ubuntu Studio
---

### Post by hbnmgr on 2011-11-21
Tried v11.10 and v11.04. I get the Menu, click Install Ubuntu Studio and the screen goes black. Waited ... Waited ...  20 minutes and still nothing on the screen. Switched monitors. Same thing. Disabled SATA, to dual boot next to WinXP - but black screen.
 
Can Not Install Ubuntu Studio using DVD from ISO download (MD5 checked OK).
 
Have the following Setup on Desktop.
 
MOBO:  PC Chips 3000 Goal+
RAM:  1 GB
CPU: AMD Sempron 3000+
HD: 80 GB PATA MSDOS partition and EXT4 partition; 
      250 GB SATA EXT4 partition
 
 
Please Help ! ! !
Thanks
SRR

---

### Post by IWantFroyo on 2011-11-21
Hit 'e' and add pci=noacpi into the file.

I tried Ubuntu Studio, and the screenshots of 11.10 are inaccurate. It's just a really basic and drab XFCE interface. I would recommend sticking with 10.04 or 11.04.

I'm starting to wonder if the project is dying...

---

### Post by hbnmgr on 2011-11-22
If you will note in my post - Had the same problem with 11.04.
 
And do you mean hit the 'E' key?  When?
 
SRR/arr

---

### Post by sgx on 2011-11-22
As a live cd/dvd begins booting, you can interrupt the process to type
in modified commands. There usually are brief messages stating F-keys to press that will interrupt the boot, list the various options, and resume booting.

You can also tap an f-key during a
regular boot process to access an early boot menu, at which time the alternate drives, usbsticks or burned media can be chosen to boot from.
Cheers

---

### Post by hbnmgr on 2011-11-22
I got into a Help Menu, but still don't know how to input any of the commands. For example, it states - "You can use the following boot parameters by pressing F6, in combination with the boot method (see F3) 
 
Disable buggy APIC interrupt routing  .....  noapic
 
-------------
 
In a post above it was suggested to use something else which doesn't look right if it is supposed to reference 'pci'.  So still confused, as to what and how to input some parameter at or during boot-up, or why it is even necessary. 
 
It should not take days and more programming knowledge and effort to install Ubuntu or Ubuntu Studio. 
 
Can anyone help?
Thanks
SRR/arr

---

### Post by hbnmgr on 2011-11-22
Looks like I'm making progress. Using 'F6' and 'ESC', I then commented out all but the install and initialize command, then it proceeded to boot and install. Chose the 250 GB SATA drive for the install. 
 
Will see If I can take it from here.
 
Thanks!
SRR/arr

---

