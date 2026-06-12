---
title: "Can't load Windows?"
date: 2007-04-16
forum: Windows
---

### Post by Harkainos on 2007-04-16
I installed Ubuntu. From the installation it wasn't supposed to mess with anything windows, but create a new partition and install onto that. When I try to load Windows (Duel Boot) it stops at a DOS screen that says 'Please wait...'

Not sure what happened. Is there any way to revert this? I read some other posts like this and it sounded like Ubuntu writes over the MBR? Is this true? Can I re-write this to make both work?

---

### Post by ibanezix on 2007-04-16
Operating systems write to the MBR in order to place their kickstart information. If it's an MBR mistake, you can fix it by booting from the windows cd and loging to recovery console, then give:

fdisk /mbr

which will restore the MBR, but you won't be able to get to Ubuntu then.

As a matter of fact, if you will be using fdisk/ mbr you might want to download the WinXP bootdisk from [www.bootdisk.com](www.bootdisk.com) which has a better version of fdisk than the one on the cd!

---

### Post by Harkainos on 2007-04-16
I have Windows XP Pro on my computer and thought it would be fun to try out Ubuntu. So I downloaded the Installer and burn a CD. I booted from the CD and installed Ubuntu to my computer. From my selection in the installer it was to make a partition on my drive (250gb Sata that also has Windows on it) Ubuntu installs without a hitch. The computer reboots and it gives me the option of Ubuntu (4 options there) and Windows XP. When I select XP it goes to a DOS page and says 'Please Wait...'. That is where it stops. Is there something I needed to do prior to the Ubuntu install? Or anything I need to dl in order for Windows to load?

---

### Post by xpod on 2007-04-16
Did you defrag a couple of times before you installed??

It`s always advised before doing any kind of resizing etc

---

### Post by Harkainos on 2007-04-16
My system was defragged. I would like to have the option of loading both windows or ubuntu. Is this possible?

---

### Post by sebbouckaert on 2007-04-16
The **Grub Super Disk** might be a great help for solving this kind of boot problems.
It can be downloaded as an iso file and burned into a bootable CD. On it you will find a lot of options and tools for repairing/booting existing Windows or Linux partitions. It certainly has helped me out several times. More info on this site: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Harkainos on 2007-04-16
Thank you seb. I clicked the link at the page there and it times out... wonder if it is under construction or something.

---

### Post by sebbouckaert on 2007-04-16
Does not work here either at this time. Couldn't Google another location to download, so you'll have to be patient I guess

---

### Post by louieb on 2007-04-16
Try it now I was just there. or the Dual Boot link in my signature is home page for this website.

---

### Post by Harkainos on 2007-04-17
I will try. Is this a common thing? When Ubuntu overrides the MBR does this normally happen. I also have the XP Pro bootable CD and could 'repair' windows. Would this cause ubuntu to stop loading?

---

### Post by sebbouckaert on 2007-04-18
Although I am not an expert in explaining such technical things as these I am quite sure that using the Windows XP recovery console (the Windows repair CD) will fix your windows MBR but it won't recognize any other operating systems on your system (certainly not Linux) and thus your Ubuntu wouln't be bootable at all. 

Hope you managed to get the Grub boot disk by now, as this seems to be the best option (apart from reinstalling first Windows, then Ubuntu, which you probably want to avoid at all cost).

---

