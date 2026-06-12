---
title: "Mouse gesture program doesn't work on Xubuntu virtual machine"
date: 2017-01-23
forum: Virtualisation
---

### Post by peter1897 on 2017-01-23
I have Xubuntu installed on virtualbox machine and i installed Easystroke which is mouse gesture program. I am unable to record a gesture, every other option in the program works but i am unable to record a gesture. And the problem is that because Xubuntu is installed on virtual machine. I installed the program on Ubuntu from live usb and i was able to record a gesture.
Any idea why the program doesn't work on virtual machine?

---

### Post by KillerKelvUK on 2017-01-23
Hey, this worked fine for me...just created a test vm and live booted 16.10, enabled community sources and installed easystroke...worked first time.

I'm using KVM/Qemu for virtualisation, what are you using?

[IMG]https://s24.postimg.org/wkpzwgnw5/Easystroke.png[/IMG]

---

### Post by peter1897 on 2017-01-23
I am using Xubuntu 14.04 x32 virtualbox guest machine and host Windows 7 x64. Still doesn't work for me.

---

### Post by KillerKelvUK on 2017-01-23
Not really up to speed on VB to be of much help sorry but have you installed the VB extensions and all the guest drivers needed?  Any options to change the virtual mouse driver/hardware, I know with qemu there are a couple of different options for virtual mouse hardware.

---

### Post by &amp;KyT$0P# on 2017-01-23
peter1897, are Guest Additions installed in the VirtualBox guest?  If not, please do so (Devices > Insert Guest Additions CD image) and try disabling mouse integration.  Does it work now?

---

### Post by peter1897 on 2017-01-23
It looks like the mouse integration was the problem. I go to Input>Mouse Integration and click on the entry and after that i was able to record a gesture. I am not sure how this mouse integration works in virtualbox because i was able to use the mouse so far without clicking on enable mouse integration. Guest additions are also installed.

---

