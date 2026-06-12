---
title: "External USB Floppy Drive"
date: 2007-04-23
forum: System76 Support
---

### Post by iba10753 on 2007-04-23
On a new Ratel, I did not order an internal floppy drive.  Naturally, I didn't think I'd ever need it.

Now, I'm wanting to install Win2K Pro in a VirtualBox virtual machine.  I have the floppy boot disks and the CD.  

I can't seem to get the Ratel (with Feisty) to recognize the external USB floppy drive.  I was assuming that it was "plug, recognize, and auto-mount" in Ubuntu on this Ratel hardware.  

What do I need to do to use the external USB floppy in Feisty?  If I can get some help solving that problem, I'm sure that I can use the floppy to load the Win2K virtual machine for VirtualBox.

Thanks,
Ben Askew
Houston, TX, USA

---

### Post by thomasaaron on 2007-04-24
I use vmware and am not that familiar with Virtual Box. But if you plug in the floppy BEFORE activating your virtual machine (i.e. allow Ubuntu to recognize it first) will it then be recognized when your virtual machine is turned on?

---

### Post by iba10753 on 2007-04-24
Therein lies the actual problem.  I have not been able to get the USB floppy drive or my USB memory stick to be auto-recognized at all.   I've tried the front USB ports as well as the ones on the back panel.

I'll call the System76 support line and ask for some guidance.  If we can get these devices to auto-discover then I'll have no trouble in the VirtualBox configurations.

Thanks,
Ben

---

### Post by thomasaaron on 2007-04-24
In a terminal, type:

tail -f /var/log/messages

Then plug the drive up (see if the machine sees it)
And pull it out (see if the machine reports it)

---

### Post by iba10753 on 2007-04-24
I didn't see any indications that it was recognized - within the terminal, on the desktop, or in the file manager.

I've left my number with the support line answering service.  I've actually successfully installed an internal floppy drive for now but definitely need to figure out how to get a memory stick (for example) to get recognized on the USB ports.  

There is a beige cable inside the case that is not plugged into the circuit board at the front of the case nor onto the motherboard.  I have a feeling that it is for fireware, etc. and is not the USB cable.  Plus, I haven't been able to get the external floppy or memory stick recognized on any of the rear USB ports either.

Thanks,
Ben

---

### Post by thomasaaron on 2007-04-24
I'll look in our test Ratel tomorrow and see what the wire goes to.

Can you do:

sudo dmidecode | grep USB > ~/Desktop/dmidecode

and email it to me at support(at)system76.com as reminder

Best,
Tom

---

### Post by iba10753 on 2007-04-25
As a follow-up to this thread, the problem was solved by Tom in a support call this afternoon.  Despite watching his 37 year old Ford go up in smoke this morning, he was still fielding and making support calls from his house.

Inside the Ratel box, there was a thick beige wire that was sitting in the bottom of the case.  Neither end of this cable was plugged in anywhere.  Plugging one end of the cable into the circuit board at the front of the Ratel case and plugging the other end into the only compatible pin-out location on the system board.....fixed the problem.  

The USB memory stick is now instantly recognized when it is plugged into either of the USB ports on the Ratel.

Many thanks to Tom at System76 for the help.  It was above and beyond the call of duty.  If I had a good engine for a '70 Ford pickup, I'd send it to you, Tom!

Thanks,
Ben Askew

---

