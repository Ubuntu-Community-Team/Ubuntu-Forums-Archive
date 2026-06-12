---
title: "Headless box - powercut - help me"
date: 2010-12-01
forum: Server Platforms
---

### Post by mokachoka on 2010-12-01
Hi all, (please read i tried to keep it short)

I managed to setup a ubuntu 10.10 install on a SS4200 server which is headless. I installed it using a serial cable and directing the install to the serial port.

This worked ok and i administered the server using SSH no problem.

Today i had a powercut and the system obviously restarted, but i cannot ping the server on the network... 

I have connected up the serial cable and manage to see GRUB but if i choose the first option i cannot see anything, nor can i ping the server.

I have managed to pull the hard drive and put in into a windows machine and boot up using a livecd to view the drive. I have done a fsck which comes back just fine.

I figured i might need to forward all console output to the serial cable (not just grub) so i followed this guide ...

[http://koo.fi/tech/2010/11/27/serial-console-for-ubuntu-server-1004-kvm-guest](http://koo.fi/tech/2010/11/27/serial-console-for-ubuntu-server-1004-kvm-guest)
(minus the virtual stuff)

Anyway, i need to update-grub but cannot as it tries to update the live-cd grub...

Am i going in the right direction?
Can i update grub from a live cd?
Any advice?

---

### Post by SeijiSensei on 2010-12-01
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by mokachoka on 2010-12-01
Would it matter that i would be rebuilding grub from a different PC?

I have the hard drive to the server in my desktop PC...?

---

