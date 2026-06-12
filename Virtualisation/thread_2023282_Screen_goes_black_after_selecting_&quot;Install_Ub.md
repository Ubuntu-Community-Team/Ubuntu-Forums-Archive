---
title: "Screen goes black after selecting &quot;Install Ubuntu Server&quot;"
date: 2012-07-12
forum: Virtualisation
---

### Post by cthart on 2012-07-12
Hi,

Host is 12.04 desktop (upgraded from 11.04 and 11.10), attempting to create a 12.04 server VM using "Virtual Machine Manager".

The VM type is KVM. Video card is cirrus, display is captured using VNC (selecting Splice gives a QEMU error on VM poweron).

The boot screen is displayed and first I can choose a language.

Then after I choose "Install Ubuntu Server", the screen goes black and after a long wait it's still black.

Yesterday I succesfully created a Windows XP VM using the same process without a hitch.

I also have a pre-existing 10.04 VM that was created when my host was still running 11.04
I considered cloning this VM and upgrading it to 12.04 but that's potentially a very long process (given that upgrades are recommended not to skip releases).

I've Googled and come across some issues relating to seabios versions and not being able to capture the VGA output but the strange thing is that the initial screen displays fine (though presumably this is plain text displayed through BIOS calls).

What can I do? Undoubtedly I'll need to supply more information so please ask.

Thanks,

Colin

---

### Post by cthart on 2012-07-12
I've submitted a bug on this as it is certainly not expected behaviour and I couldn't find an exact match for this.

[https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/1023896](https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/1023896)

---

### Post by cthart on 2012-07-16
OK, this seems to be an issue with Ubuntu Server 12.04 because 10.04 works just fine booting into the installer inside a  VM.

---

### Post by cthart on 2012-07-23
Status update:

11.10 installed fine but also exhibited the same symptoms after booting into the freshly installed OS (screen goes black during booting... I can't remember at which point).

I finally managed to create a working 12.04 VM by cloning my existing 10.04 VM and then upgrading it directly to 12.04 using "do-release-upgrade -d" (I used the -d switch because I didn't want to wait for 12.04.1).
This 12.04 works just fine.

---

