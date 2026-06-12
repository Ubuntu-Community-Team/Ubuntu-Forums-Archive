---
title: "Windows XP Guest in Virtualbox missing Ethernet adapter drivers; can't access Web"
date: 2009-03-25
forum: Virtualisation
---

### Post by diablo75 on 2009-03-25
I just finished helping someone install Windows XP into a virtual machine but the virtual ethernet adapter is missing a driver, so Windows can't use it.  Anyone know where I can find a driver that I can take into XP and install so this device will work?

---

### Post by diablo75 on 2009-03-26
Bump.

---

### Post by andrew.46 on 2009-03-27
Hi,

I have not used XP with VirtualBox but the settings for Network should not be all that different, I hope. My own virtual machines are other linux distros. I attach a screenshot of my own network settings, this for the OSE version and Jaunty.

Hope this is some help? My apologies if the setup is completely different for windows :-).

Andrew

---

### Post by diablo75 on 2009-03-27
Huh, well I feel like an idiot.  I've not tried out the other "virtual" adapters listed in that drop down yet, so I'll switch those around till Windows plays friendly with one.  Thanks.

---

### Post by Eniac on 2009-03-27
any luck with that ? i have the exact same problem. transformed a winxp guest in vmware to virtual box using qemu and everything works now but the ethernet adapter just wont work. i tried uninstalling from windows, even the hidden ones, i tried changing from adapter 1 to adapter 2 in vbox, then the type of adapter...virtually all combination of things to try.

In windows, i am unable to delete the hidden ones, im getting a "unable to delete, maybe device is required to boot error"

here's a screenshot, the disabled ones are those I'm trying to delete and the yellow ones are the adapters that aren't working. there are two because i wanted to type PCNet II and PCNet III

---

### Post by diablo75 on 2009-03-28
Easy:

In the Virtualbox Control Panel thing (where you can specify your machines hardware configuration), you click on the network adapter category and then change the interface type.  There are four to select from.  Simply try a different interface type until one works.  I didn't need to give windows any drivers for the PCnet-PCI II device (the screenshot shows the PCnew-FAST III device, and that's what I use on my home computer... this other persons computer...well, it probably would have worked too, but the I picked the PCI device out of the list of four available and it work with no issues or prompts to install any drivers).

---

### Post by Eniac on 2009-03-29
Fixed it.

your solution didnt help me. i had already tried changing the adapter type and other combinations.

what i ended up doing is going in windows device manager, select update driver on broken virtual adapter. then i manually selected the driver AMD PCNet adapter. it was using the VMware driver for some reason.

now everything works.

---

### Post by skaterweb on 2009-10-22
Here there a solution that have help me :-)

[http://forums.virtualbox.org/viewtopic.php?f=11&t=16616](http://forums.virtualbox.org/viewtopic.php?f=11&t=16616)

The key is change the network hardware to Intel   p, li { white-space: pre-wrap; }PRO/1000 MT Desktop and then go to the Intel web page to download the driver:

[http://downloadcenter.intel.com/SearchResult.aspx?lang=spa&keyword=%22PRO2KXP.EXE%22](http://downloadcenter.intel.com/SearchResult.aspx?lang=spa&keyword=%22PRO2KXP.EXE%22)

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=8659&lang=spa](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=8659&lang=spa)

Luck!

---

### Post by rainyu_2002 on 2011-01-30
diablo75's answer helps me a lot. I have solve the issue.
1.I shutdown Windows XP guest OS
2.Change Network Adpater to "Intel PRO/1000 MT Desktop"
3.Startup Windows XP Guest OS
4.Download driver from [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=18717&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=18717&lang=eng)
5.Use "Shared Folders" on VirtualBox to share the driver to Guest OS
6.Install the driver. 

Done!

---

### Post by ofim on 2011-03-07
Thanks, It run :)

---

