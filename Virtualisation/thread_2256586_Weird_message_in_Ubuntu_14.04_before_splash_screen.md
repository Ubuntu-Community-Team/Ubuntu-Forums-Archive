---
title: "Weird message in Ubuntu 14.04 before splash screen and screen's locked to 640x480"
date: 2014-12-13
forum: Virtualisation
---

### Post by ethanandmax on 2014-12-13
I am running Windows 7 and VirtualBox 4.1.16 with Ubuntu 14.04 LTS 64-bit as my guest OS. Whenever I start the virtual machine, just before the splash screen comes up, I get this message on a black screen:

[   21.393103] piix4_smbus 0000:00:07.0: SMBus base address uninitialized - upgrade BIOS or use force_addr=0xaddr

I have no idea what this means. The screen is then locked to 640x480 and there is no screen resolution to choose from in System Settings > Display other than 640x480. Please help me! :confused:

I installed Ubuntu 12.04 LTS 32-bit before in VirtualBox and this did not happen.

---

### Post by ibjsb4 on 2014-12-14
> there is no screen resolution to choose from
Got dkms?  Needs to be in the ubuntu guest.
```
sudo apt-get install virtualbox-guest-dkms
```

---

### Post by oldos2er on 2014-12-14
Moved to Virtualisation.

---

### Post by ethanandmax on 2014-12-15
Thank you. The screen is fixed, but the SMBus thing still shows up when I start the virtual machine.

---

### Post by josh109 on 2014-12-22
[FONT=arial]*THIS POST ONLY APPLIES IF YOU ARE USING VIRTUAL BOX.*
Sometimes adding yourself to the "vboxusers" group can fix this. You should be but sometimes it doesn't add you for some reason. This may not fix the problem, but it's worth a shot.
In terminal, run:[/FONT]
sudo usermod -a -G vboxusers YOURuserNAME

[FONT=arial]After this, logout and then log back in and try your virtual machine again.[/FONT]

---

