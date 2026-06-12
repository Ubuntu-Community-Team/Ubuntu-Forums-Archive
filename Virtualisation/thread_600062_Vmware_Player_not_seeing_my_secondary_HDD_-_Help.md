---
title: "Vmware Player not seeing my secondary HDD - Help"
date: 2007-11-01
forum: Virtualisation
---

### Post by OneLinux on 2007-11-01
I just followed the guide found here (including his vxm vmdk files): [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

I used parted as stated and have a fully working Windows XP virtual machine running from my existing WindowsXP installation which resides on primary on first IDE channel (HDA) along with my Ubuntu installation. 

My problem is that I have a 250GB Hard drive running as primary on the second IDE channel (HDB) This drive is where all of my media resides and needed so I can sync my iPod via iTunes running in the VM. I mistakenly thought it would automatically find the secondary hard drive. 

I'm guessing I need to edit either the vxm or vmdk file to add this drive. I don't know how to add a drive. I can use parted again to get the drive info (units s, units cyl, etc.) but I don't know where or how to add it.

Any and all help is greatly appreciated.

---

### Post by Jbs63 on 2007-11-05
you will need to use samba and network the two computers together and make the files shared on ubuntu.
there is a nice video tutorial on youtube you can use: 
[http://www.youtube.com/watch?v=Ad17kma8rNM]("http://www.youtube.com/watch?v=Ad17kma8rNM")
it explains everything quite nicely.

---

