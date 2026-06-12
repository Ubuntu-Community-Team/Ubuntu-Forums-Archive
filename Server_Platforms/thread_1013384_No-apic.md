---
title: "No-apic"
date: 2008-12-16
forum: Server Platforms
---

### Post by crzymelly on 2008-12-16
Hello,

I am new to using ubuntu. My friend recommended that I use ubuntu as I want to set up a webserver/database server. I downloaded the latest version of ubuntu 8.10 server edition. I put it into the computer and boot it from there. I get the menu that comes up, I select my language. And then I select install ubuntu. Then I get this error, MP-BIOS bug: 8254 timer not connected to IO-APIC. How do I fix it up so I can install ubuntu?

Thanks. :cool:

---

### Post by Iowan on 2008-12-16
Does it kill the installation?  I have a server that pops up a similar message every time I fire it up (but seems to work OK, anyway).  There's supposed to be a way to change a kernel line in /boot.grub/menu.lst to eliminate the error, but I haven't tried it yet.

---

### Post by crzymelly on 2008-12-16
it just hangs and does absolutely nothing...

---

### Post by expatCM on 2008-12-17
Just trying to figure this one out myself.  I think you have to open the boot options in grub and add 

noapic

to the end of the kernel line.

However ....  it seems to me that even if that works that as soon as you run apt in the future and put a new kernel in place the setting will then be lost ...

---

### Post by expatCM on 2008-12-17
If you are installing from the CD it seems that if you press F6 as the CD loads you can then add noapic to the end of the line and that is it....

I am looking to fix this after install ...

---

### Post by crzymelly on 2008-12-18
I tried selecting the noapic option. But that didn't work. So I tried ubuntu 8.04, the error still comes up but it still installs. So all is well. Thanks for your help.

---

