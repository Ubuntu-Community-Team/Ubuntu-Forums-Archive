---
title: "VMWare Player wiki seems out of date -- Help please"
date: 2015-11-19
forum: Virtualisation
---

### Post by FerryGnu on 2015-11-19
I am trying to install VMWare Player in Ubuntu 14.04 LTS and following this
  [https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)  

I get to the line... gksudo bash ~/Downloads/VMware-Player-6.0.2-1744117.x86_64.bundle 
and it dropped back to the $ prompt with "you can install this with sudo apt-get gksudo" or something very close so I did what it said and it installed gksudo I guess.   

I retried the  gksudo bash ~/Downloads/VMware-Player-6.0.2-1744117.x86_64.bundle 
and it dropped straight back to the $ prompt.  

I checked the VMWare page and the last version for Linux was 6.0.6
 [https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/6_0|PLAYER-606|product_downloads](https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/6_0|PLAYER-606|product_downloads) 

 So I changed the gksudo-line for the latest version but nothing downloads. 

  No great surprise as I am a newbie to Ubuntu/Linux so am probably doing something stupid. :) 

Is there a later and up to date version of the installing instructions for VMWare Player for Ubuntu? 
 I have to stay with VMWarer as I already have a bunch of VMachines and the VMWare conversion to .VHD does not work so can't use VirtualBox.   

Thanks

---

### Post by sammiev on 2015-11-19
I download the bundle from [here]("https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0").

To install, use step 2 from [here]("http://www.webupd8.org/2012/06/how-to-install-vmware-player-in-ubuntu.html") but change the bundle name to match.

I never had to use any patch or anything else but step 2 only.

This was tested on Ubuntu 15.10

---

### Post by FerryGnu on 2015-11-20
@sammiev:  Excellent. Worked perfectly.  Thank you very much.

---

### Post by sammiev on 2015-11-20
> **FerryGnu said:**
> @sammiev:  Excellent. Worked perfectly.  Thank you very much.

Glad I was able to help. :P

Please mark this thread as Solved to help others.

Thanks

---

