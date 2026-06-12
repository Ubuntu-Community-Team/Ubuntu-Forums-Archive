---
title: "Fresh XP install, no networking"
date: 2008-04-14
forum: Windows
---

### Post by Pethegreat on 2008-04-14
I have just reformatted a windows XP machine to get it back to how it was when it was new. I cannot get the internet to work on the thing. I have the internet on my Ubuntu laptop, my Ubuntu desktop, and on an xbox 360. I have tried all the tools that come with XP to try and get it to connect. 

I have an Intel 865 series motherboard which I am running the Ethernet cable into. I think I need network drivers, but Intel's site does not appear to have them.

---

### Post by Dr. C on 2008-04-15
It sounds like you need the XP drivers. Have you tried the site for the motherboard manufacturer?

---

### Post by Chiko2008 on 2008-04-15
You'll have to know what network card you have. Try to use any hardware identification program if you don't wish to open your PC, like Everest or Aida (try to download one of them here: [http://www.hardwaresecrets.com/page/download_id](http://www.hardwaresecrets.com/page/download_id)).

Once you know what network card is yours, do some google and you'll easily find the drivers.

[Ubuntu]("http://www.linux-archive.org/ubuntu/")

---

### Post by Midwest-Linux on 2008-04-15
> **Pethegreat said:**
> I have just reformatted a windows XP machine to get it back to how it was when it was new. I cannot get the internet to work on the thing. I have the internet on my Ubuntu laptop, my Ubuntu desktop, and on an xbox 360. I have tried all the tools that come with XP to try and get it to connect. 

I have an Intel 865 series motherboard which I am running the Ethernet cable into. I think I need network drivers, but Intel's site does not appear to have them.

 I had a similar problem , I reinstalled XP and did a dual boot with Linux Mint 4.0. Linux Mint found all the drivers and XP couldn't find the embedded (built onto the motherboard) sound  and the embedded network .

 So I had a spare PCI sound card and a spare PCI network card, XP found those...so until I have time to find the drivers for the embedded sound and network, the PCI substitutes will have to do.

 Linux was able to find the embedded sound and network and XP could not...another win for Linux!

---

### Post by heartburnkid on 2008-04-15
You should go to your motherboard manufacturer's website and see if you can locate drivers from there.  The generic chipset drivers are usually fine, but some mobo manufacturers will source networking components, audio components, etc. from other companies as a cost-cutting measure, so it's definitely better to use the manufacturer's drivers whenever possible.

Do you know the make and model of your motherboard?

---

### Post by Battie on 2008-04-15
I posted this elsewhere. It should work for you too:
> 
-Open your device manager, and go to the properties of the unknown device.

-Go the details tab and look at the long string that describes the device.

-In this string, there should be a vendor ID (VEN) and a device ID (DEV). Look them up here: [http://www.pcidatabase.com/](http://www.pcidatabase.com/)

-Now you know which drivers to download!

For example, my network card shows this string: PCI\VEN_14E4&DEV_1677&SUBSYS_01AD1028&REV_01\4&117 729E2&0&00E0

So, I look up 14e4 in the vendor search. This correctly takes me to a Broadcom listing. Now I look for 1677 in the list. It says my card is a NetXtreme Gigabit Ethernet PCI Express, which is exactly right!


You can also just get the drivers from here, since you know your chipset: [http://support.intel.com/support/network/sb/cs-012904.htm](http://support.intel.com/support/network/sb/cs-012904.htm)

---

### Post by Pethegreat on 2008-04-15
Ok. Looks like this should all work. I will post back with results tomorrow. 

Linux gives us great support on things like networking and program installation.

---

