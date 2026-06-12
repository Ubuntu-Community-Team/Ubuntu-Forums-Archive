---
title: "PC goes comatose when trying to boot"
date: 2012-06-04
forum: Ubuntu Studio
---

### Post by Smokey DeVille on 2012-06-04
Greetings! I am completely new to Linux and Ubuntu, and I am having some trouble getting Ubuntu to install on my machine. I am using an HP Pavilion AMD 64 with 8G RAM and 1Tb hard drive space. For over a month I have attempted to install Ubuntu 11.10 from an ISO burned onto a DVD, and that wouldn't work (I have a new set of coasters now, though), Then I tried to install it from a prepared USB drive, and was unsuccessful. Now I am trying to install Ubuntu Studio 11.10 from a USB stick prepared using Linux Live USB creator, and this is the farthest I have been able to get: Ubuntu Studio allegedly installed, and upon completing the install it needed to reboot. I rebooted and my screen stays black. Every time I turn on my terminal and select  Ubuntu, with Linux 3.0.0-12 generic, my screen goes black and stays that way. I have re-downloaded, reburned, reformatted, recreated ad nauseum. Am I seriously stuck using Windows? 

Thanks in advance for any help you can offer.

---

### Post by jejeman on 2012-06-04
I would suggest that you install 12.04 version of ubuntu studio. 11.10 is not that lucky version.
12.04 has live dvd, download it and try it out.

Which graphic card do you have?

---

### Post by wilee-nilee on 2012-06-04
Try the failsafe boot from the grub recovery choice in the grub menu. If yuou only have one instll use the shift key held down after power on to show the menu.

Second choice nomodeset as well.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Smokey DeVille on 2012-06-05
My graphic card is an AMD Radeon HD6530 D. 

I downloaded US 12.04, and I created a bootable stick. When I boot, it would give me the options to install Ubuntu or try Ubuntu without installing. Selecting either option send my machine into it's coma. I am starting over with this stick and seeing if a do over is an orer. 

I tried going in through recovery, and I'll be perfectly honest, I am not too keen on line commands at this point. I'll do some reading on the interwebs and find what I need to know. 

Thank you to both of you!

---

### Post by wilee-nilee on 2012-06-05
> **Smokey DeVille said:**
> My graphic card is an AMD Radeon HD6530 D. 

I downloaded US 12.04, and I created a bootable stick. When I boot, it would give me the options to install Ubuntu or try Ubuntu without installing. Selecting either option send my machine into it's coma. I am starting over with this stick and seeing if a do over is an orer. 

I tried going in through recovery, and I'll be perfectly honest, I am not too keen on line commands at this point. I'll do some reading on the interwebs and find what I need to know. 

Thank you to both of you!

Look at the link In put in my last post on nomodeset, it is pretty basic stuff, with the stick it is just hitting f6 at the gui you would see as well if you hold down the shift as soon as you power on, hit f6 and click nomodeset and boot to the live desktop.

THe shift key has dual uses, it will show the grub menu on a single install, and with a cd/usb boot it will bring up an early gui that has the options you mention as well as a memory check.

Ubuntu is probably the best by and large Linux distro where you can avoid the command line as well. If you need it though and use the forum it is a copy and paste generally.

---

### Post by sgx on 2012-06-06
> **Smokey DeVille said:**
> My graphic card is an AMD Radeon HD6530 D. 

I downloaded US 12.04, and I created a bootable stick. When I boot, it would give me the options to install Ubuntu or try Ubuntu without installing. Selecting either option send my machine into it's coma. I am starting over with this stick and seeing if a do over is an order. 

I tried going in through recovery, and I'll be perfectly honest, I am not too keen on line commands at this point. I'll do some reading on the interwebs and find what I need to know. 

Thank you to both of you!
Hi Smokey, try getting an older nvidia graphics card,
one without any built-in audio, or hdmi.

In the meantime, try a puppy linux, and an rpm based linux,
as they don't use the same hardware ID code, or kernel

a Lucid based Puppy linux:

[www.puppylinuxstuff.meownplanet.net/10wt3ch/PuppyStudio3.3-rt.iso](www.puppylinuxstuff.meownplanet.net/10wt3ch/PuppyStudio3.3-rt.iso)

[http://www.pclinuxos.com/?page_id=180](http://www.pclinuxos.com/?page_id=180) get the kde minime iso

The main thing about linux, is starting with compatible
video hardware, then compatible audio hardware. The freedom is
worth a little patience horse-trading. Gamers are a good source
for a well maintained older nVidia card.The newest gear often takes
too much time to get supported in the linux kernel, so its good
to make the needed compromise.

Cheers

---

