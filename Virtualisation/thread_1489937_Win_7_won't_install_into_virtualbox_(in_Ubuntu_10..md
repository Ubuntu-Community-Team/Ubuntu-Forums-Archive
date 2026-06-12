---
title: "Win 7 won't install into virtualbox (in Ubuntu 10..4)"
date: 2010-05-21
forum: Virtualisation
---

### Post by Beowulf.1000 on 2010-05-21
I can't get Windows 7 Ultimate 64bit to install in virtualbox. I have Ubuntu 10.4 64 bit, 64 bit version of Sun PUEL virtualbox 3.2, legal copy of Win7, but when I try to install Win7 I get what you see on the attached screenshot.

Any thoughts on how to install Win7? I have WinXP 32-bit installed and working great, just thought it would be fun to get Win7 working in my virtualbox.

---

### Post by flyfishingphil on 2010-05-24
> **Beowulf.1000 said:**
> I can't get Windows 7 Ultimate 64bit to install in virtualbox. I have Ubuntu 10.4 64 bit, 64 bit version of Sun PUEL virtualbox 3.2, legal copy of Win7, but when I try to install Win7 I get what you see on the attached screenshot.

Any thoughts on how to install Win7? I have WinXP 32-bit installed and working great, just thought it would be fun to get Win7 working in my virtualbox.
You might try it again but, in case you forgot, remember that the "restart the computer" is for the VBox program, not the entire computer. Just "X" out of the windows program, tell the VBox to turn off the windows then click on it to restart it.

Also, did you remember to "add" another?

See if this does the trick.

---

### Post by andrewhg on 2011-12-24
I had the same problem but for mine instead or telling me that an un unexpected error had occured it told me that 64 bit was not supported despite running ubuntu 10.4 64 bit and VirtualBox 64bit. So I just installed 32 bit windows 7 Ultimate. Would like to know what the problem was though.

---

### Post by forrestcupp on 2012-03-12
I know this is old, but you can install Windows 7 Ultimate 64-bit in virtual box. You may need to have support for hardware virtualization, though. The way I got it to work was to go into the virtual machine's settings and enable a few things. 

In the System section, I changed the chipset to "ICH9", and I enabled "IO APIC". In the Acceleration tab, you have to have the Hardware Acceleration options enabled. I don't know if it's necessary, but in the Storage section, I changed the type to "ICH6". In the Network section, click the down arrow next to Advanced, and make sure the adapter type is an Intel adapter.

After doing those things, Windows 7 Ultimate 64-bit installed with no issues.


Edit: It will install, but it seems pretty buggy. If you can get to the point where you can boot into Win7 long enough to install the Guest Additions, it gets a lot better.

The only reason I'm posting this is for future reference because this thread came up when I was Googling for an answer.

---

