---
title: "grub2 update"
date: 2014-04-11
forum: Ubuntu Development Version
---

### Post by QDR06VV9 on 2014-04-11
Well It is getting better with each update!
I'm running on this machine 4 SADA's with 5 OS's to boot from.
Since grub2 first made it's appearance if I did anything kernel related usually booting from one of my options from grub menu
I would then have to boot from the 1st option in grub then run the "sudo update-grub" for changes to be made to any of the others.(OS's)
But after todays updates It is working like it should (at least for me) IE changes updated for all entries.;)

---

### Post by oldfred on 2014-04-11
I have installed a variety of test installs and have not uninstalled all of them. So os-prober goes berserk. New install takes forever to find all the existing systems.

But the first thing I do after new install is turn off os-prober. I then add my own entries into 40_custom for those few that I may want to boot. 
And I install a different grub into the MBR of every drive.

To avoid having to run sudo update grub in each install that updates and then boot install in MBR and run sudo update grub so it has new kernel to boot, I boot using the links in / that most Debian based installs have. I also often add a chainload to another MBR entry in 40_custom also.

See Maintenance Free menus for example.
[URL="https://help.ubuntu.com/community/Grub2/CustomMenus#Maintenance-Free_Menuentries"]https://help.ubuntu.com/community/Grub2/CustomMenus#Maintenance-Free_Menuentries

[/URL] How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

[URL="https://help.ubuntu.com/community/Grub2/CustomMenus#Maintenance-Free_Menuentries"]
[/URL]

---

### Post by QDR06VV9 on 2014-04-11
> **oldfred said:**
> I have installed a variety of test installs and have not uninstalled all of them. So os-prober goes berserk. New install takes forever to find all the existing systems.

But the first thing I do after new install is turn off os-prober. I then add my own entries into 40_custom for those few that I may want to boot. 
And I install a different grub into the MBR of every drive.

To avoid having to run sudo update grub in each install that updates and then boot install in MBR and run sudo update grub so it has new kernel to boot, I boot using the links in / that most Debian based installs have. I also often add a chainload to another MBR entry in 40_custom also.

See Maintenance Free menus for example.
[URL="https://help.ubuntu.com/community/Grub2/CustomMenus#Maintenance-Free_Menuentries"]https://help.ubuntu.com/community/Grub2/CustomMenus#Maintenance-Free_Menuentries

[/URL] How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

[URL="https://help.ubuntu.com/community/Grub2/CustomMenus#Maintenance-Free_Menuentries"]
[/URL]

Thank You Sir.
Great Info.

---

