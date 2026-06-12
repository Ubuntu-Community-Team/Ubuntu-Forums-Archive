---
title: "No bootable medium found on Ubuntu 11.04 and VirtualBox 4.08"
date: 2011-06-05
forum: Virtualisation
---

### Post by skellyh on 2011-06-05
Hi,

I've tried a few solutions in this forum to solve my problem but have not come across anything that works. I have Ubuntu 11.04 installed on an Asus u36jc with an SSD. I installed Oracle VirtualBox 4.08 r71778 and I am trying to set up Windows 7 as a guest operating system. (I also tried XP because I have an old install disk from that, but I got the same result.)

My machine has no internal CD/DVD so I'm trying to install from an external Sony through a USB 2.0 port.

Each time I do, I get the "FATAL: No bootable medium found! System halted" error. I have attached files showing:

1. The open volume showing the contents of the CD in the host OS
2. The USB config showing the Sony CD/DVD
3. The Storage config with the Sony
4. The System config showing the Boot Order

Any assistance would be gratefully received.


Thanks,

Scott.

---

### Post by CharlesA on 2011-06-06
Did you tell the VM to mount the host drive?

---

### Post by skellyh on 2011-06-07
Hi, thanks for the response Charles.

I think I'm missing something here. The CD/DVD is mounted on the host and I am able to see files when I open it on the desktop. I then added it to the guest VM configuration and I can select the appropriate drive (I'm mounting the drive, not an ISO file). I have attached a screenshot of my Storage tab.

Is there something else that I need to do to mount the host drive?


Thanks,

Scott.

---

### Post by CharlesA on 2011-06-07
Click on the cd icon there and select "host drive"

EDIT: Nevermind. It's already set to the host drive.

Maybe try setting it to "passthrough" but I'm not sure.

If worse comes to worse, you can always create an ISO of the disk and go from there.

---

### Post by skellyh on 2011-06-11
Hi Charles, thanks for your input.

It turns out that as soon as I disabled the USB from the virtual machine, the bootable medium was found. I think there was a conflict because both VirtualBox and the virtual machine were trying to control the USB port.

So for external DVD, the USB port should not be configured on the VM.

I now have Windows running.

Regards,

Scott.

---

### Post by CharlesA on 2011-06-12
Awesome. Glad you got it working. :)

---

