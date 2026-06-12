---
title: "no ethernet on vmware player"
date: 2008-09-04
forum: Virtualisation
---

### Post by wsamh on 2008-09-04
I have ubuntu as my host OS and Win Xp as my guest OS. I used easyvmx.com to create a vm. I installed win xp. but not connection with internet or to the netwrok.What am I doing wrong?

---

### Post by linux6994 on 2008-09-04
Look at the top of the vmware-player window and see if you have an Ethernet option. You should, click it to engage it if it is not.

Look in the machines directory where the .vmx file is. Open it with the text editor and look for the ethernet0 settings:

# First network interface card
ethernet0.present = "TRUE"
ethernet0.virtualDev = "e1000"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddressOffset = "0"

When the machine was created, did you check the ethernet card?

When the vmware-player was compiled was it all created cleanly?

Here is the link for the instructions that I follow. You will need to change the .tar file name for the version that you downloaded.

[http://www.smokinglinux.com/tutorials/install-vmware-player-on-ubuntu-gutsy-710](http://www.smokinglinux.com/tutorials/install-vmware-player-on-ubuntu-gutsy-710)

Good luck!

---

