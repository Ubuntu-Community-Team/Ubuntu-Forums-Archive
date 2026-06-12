---
title: "Ubuntos 16.04.2 desktop en DEll Power Edge T130"
date: 2017-05-24
forum: Server Platforms
---

### Post by jtororeyes on 2017-05-24
Hello I am trying to install Ubuntos desktop on Power Edge T130. Tested with all images, bootable pendriver, etc. Apparently you have to make changes to the BIOS.
From my search on the internet nothing has worked for me.

---

### Post by QIII on 2017-05-24
Do you really mean UbuntOS, or Ubuntu?

---

### Post by oldfred on 2017-05-24
Moved to Server forum where those who know more about servers may be able to help.

But it is an old system.
Ubuntu Desktop with 17.04 is obsoleting the Matrox G200 video as extremely old. 16.04 should still have driver.
 This was done because they expose insecure APIs to user-space. [URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276
[/URL]

And you have a special RAID card. Desktop does not directly or easily install to RAID and does not include the RAID drivers. You many need to install server version and then add desktop of choice.
Dell PERC H330

I do not know servers but those two issues are ones you need to research.

---

### Post by Michael_McKenney on 2017-05-24
According to [http://www.dell.com/support/home/us/en/04/Drivers/SupportedOS/poweredge-t130](http://www.dell.com/support/home/us/en/04/Drivers/SupportedOS/poweredge-t130) your hardware supports

VMware ESXi 5.5                                         
                                            
Windows Server 2012 R2                                         

Red Hat Enterprise Linux 7                                         

VMware ESXi 6.5                                         

BIOS                                         

Red Hat Enterprise Linux 6                                         

Windows Server 2012                                         

VMware ESXi 6.0                                         

Windows Server 2016                                         

SUSE Linux ES 12                                         

XenServer 7.0                                         

Windows Server 2008 R2                                         

Novell SuSE Linux ES 11

---

### Post by mörgæs on 2017-05-25
The support list only displays what have been tested to work well.
If an operative system is not on the list it's not a proof that it does not work, maybe Dell simply didn't bother to test it.

---

### Post by Michael_McKenney on 2017-05-25
Dell and HP design hardware to run on certain OS properly and supported.   When I installed my Ciscco Virtual Lab on my HP DL 380e Gen8, it uses Lbuntu 14.04.  I had to remove the SAS controller and use the onboard SATA controller.   A lot of servers don't run workstation versions of OS.

---

### Post by jtororeyes on 2017-05-31
Thank you so much for the comments. After testing with several versions of UBUNTU, the machine gives pure problems for the instlaciom. I will resignare to install windows server.

---

### Post by mörgæs on 2017-05-31
Have you tried Red Hat or SuSE?

---

