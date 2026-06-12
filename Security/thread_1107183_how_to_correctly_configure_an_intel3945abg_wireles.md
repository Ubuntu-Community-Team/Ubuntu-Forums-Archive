---
title: "how to correctly configure an intel3945abg wireless card for injection??"
date: 2009-03-26
forum: Security
---

### Post by scrypt on 2009-03-26
I want to correctly patch my intel pro/wireless 3945abg with this driver:

        wget [http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2)            (downloads driver)

 What are the correct commands to apply the above driver? 

 and also what is the correct command to Blacklist the original default Wireless card driver??
Because this is where I think my problem lies, That it is not coorectly blacklistung and removing the original default driver?

   I have tried this this bellow command I was given to blacklist it, but it still reloads when I re-boot Ubuntu 8.10:

   sudo modprobe -r iwl3945          (unload driver that you do not need).

I then use this command to load the new Driver:

                sudo modprobe ipwraw                 (load the driver that you installed)

 Then I use this command to restart my wireless card along with actually turning on the power suppt too it:

               sudo ifconfig wlan0 up (enable the network adapter): This command never workd though, I get this output form the iwconfig command:

I can put my card into monitor mode using this command:   
                                                                                                   sudo iwconfig wlan0 mode monitor


This seems to work and does put my card into monitor mode. BUT does not change it fully because it should change from wlan0 to wifi0, which it doea not!

Can anyone see where i am going wrong?

also can anybody advise me how to rwctify this??

---

