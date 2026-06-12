---
title: "No Preinstalled Ubuntu Laptops in the UK?"
date: 2014-11-17
forum: Ubuntu, Linux and OS Chat
---

### Post by Daveski17 on 2014-11-17
Would someone please recommend a laptop make and model that is totally Ubuntu compatible. I understand it will almost certainly have Windows 8 preinstalled. I will install 14.04 LTS on it myself as long as I can get around the UEFI secure boot. I am looking for something within £200-400 preferably x64 with around 4 GB RAM minimum. I don't need anything top of the range, just a decent, reasonably priced, serviceable laptop that I can run my favourite operating system on. 

Thanks.

---

### Post by ajgreeny on 2014-11-17
You can get a laptop with no OS very easily, and a few I think with Ubuntu pre-installed from such as Linux-Emporium, though I am not sure if that company still is trading; their website gets me nowhere.

I have used [Novatech]("http://www.novatech.co.uk/novatech/home.html") several times for accessories, and a few years ago for a netbook, which is still going fine with Xubuntu 14.04 on it, and more recently I bought a desktop for me and a laptop for my wife from [PC Specialists]("http://www.pcspecialist.co.uk/"), who allow you to customise the machine to your own spec. The laptop has the following spec:-
> UltraNote: 15.6" Matte Full HD IPS LED Backlit Widescreen (1920x1080)
Intel® Core™i3 Dual Core Mobile Processor i3-4100M (2.50GHz) 3MB
4GB KINGSTON SODIMM DDR3 1600MHz (1 x 4GB)
INTEL® HD GRAPHICS MEDIA ACCELERATOR 4600
500GB SERIAL ATA II 2.5" HARD DRIVE WITH 8MB CACHE (5,400rpm)
UltraNote Series: 8x SATA DVD±R/RW/Dual Layer (+ 24x CD-RW)
Internal 9 in 1 Card Reader (MMC/RSMMC/SD: Mini, XC & HC/MS: Pro & Duo)
STANDARD THERMAL PASTE FOR SUFFICIENT COOLING
Intel 2 Channel High Definition Audio + MIC/Headphone Jack
GIGABIT LAN & WIRELESS INTEL® N-7260 (300Mbps, 802.11BGN) + BLUETOOTH
USB Options    2 x USB 3.0 PORTS + 2 x USB 2.0 PORTS AS STANDARD
6 Cell Lithium Ion Battery (62.16WH) (Up to 7 Hours)
Power Lead & Adaptor    1 x UK Power Lead & 65W AC Adaptor
ULTRANOTE SERIES UK KEYBOARD
INTEGRATED 2 BUTTON TOUCHPAD MOUSE
INTEGRATED 2.0 MEGAPIXEL WEBCAM
for a cost of a fraction over £400, but we could have saved quite a lot by changing the spec particularly removing the HD display, but I must admit the clarity of the HD screen is superb, as indeed is the rest of the machine.

Xubuntu 14.04 is also being used on that with no problems at all.

You could get a 15.6" Genesis with no OS, a quad core pentium and 4GB ram for £269 if that fitted your bill.  They have a useful forum for linux users at [PCSpecialist Linuxforum]("https://www.pcspecialist.co.uk/forums/forumdisplay.php?32-Linux").

Got to be worth a look!

PS:
Other than being a satisfied customer I have absolutely no relationship with either of these that I am recommending.

---

### Post by Daveski17 on 2014-11-17
@ajgreeny, thanks for the information it is greatly appreciated. Can the laptops with no OS installed be installed with Linux using the cold booting method?

---

### Post by ajgreeny on 2014-11-17
What do you mean by "cold booting method"?

PCS actually install Win7 with no license in order to test the machine before it is delivered and send it to you in that state, but with no license Win7 is worthless to you, so just use a live DVD or USB, boot to that from cold and install the linux OS of your choice.

See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for the info you will need on using UEFI.  There is no need to fear it if not using dual boot, but make sure you have made the small efi partition or you will not get the machine to boot.  Both my machines use UEFI with no problem.

---

### Post by Daveski17 on 2014-11-17
> **ajgreeny said:**
> What do you mean by "cold booting method"?

Placing a DVD/CD with an image (usually from a downloaded ISO file) of Ubuntu into a computer's optical drive and then booting. This is how I normally test distros or install.

> **ajgreeny said:**
> PCS actually install Win7 with no license in order to test the machine before it is delivered and send it to you in that state, but with no license Win7 is worthless to you, so just use a live DVD or USB, boot to that from cold and install the linux OS of your choice.

Oh right, thanks. That kind of makes it easier in a way.

> **ajgreeny said:**
> See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for the info you will need on using UEFI.  There is no need to fear it if not using dual boot, but make sure you have made the small efi partition or you will not get the machine to boot.  Both my machines use UEFI with no problem.

So if I don't plan on dual-booting, and just wipe the original OS and replace it with Ubuntu, I don't need to worry about UEFI? 

Thanks again for the help.

---

### Post by ajgreeny on 2014-11-17
> **Daveski17 said:**
> Placing a DVD/CD with an image (usually from a downloaded ISO file) of Ubuntu into a computer's optical drive and then booting. This is how I normally test distros or install.



Oh right, thanks. That kind of makes it easier in a way.



So if I don't plan on dual-booting, and just wipe the original OS and replace it with Ubuntu, I don't need to worry about UEFI? 

Thanks again for the help.
You don't need to *worry* about UEFI, but you do need to make sure that you have a GPT partition table, not msdos, and that you make sure you have the EFI fat32 partition at the start of the disk.  I suggest you make a new partition table in gparted to be sure about this, then add the partitions you want. See that UEFI link I gave earlier.

My set up has an EFI fat32 partition of 200MB, root partition of 25GB, swap of 8GB (I hibernate occasionally so need as much swap as memory), and all the rest of my 1TB disk is /home.

---

### Post by Daveski17 on 2014-11-17
> **ajgreeny said:**
> You don't need to *worry* about UEFI, but you do need to make sure that you have a GPT partition table, not msdos, and that you make sure you have the EFI fat32 partition at the start of the disk.  I suggest you make a new partition table in gparted to be sure about this, then add the partitions you want. See that UEFI link I gave earlier.

My set up has an EFI fat32 partition of 200MB, root partition of 25GB, swap of 8GB (I hibernate occasionally so need as much swap as memory), and all the rest of my 1TB disk is /home.

I just follow the Ubuntu installation wizard and it does it for me. I wipe what was on before and replace it. It's always worked before.

---

### Post by ajgreeny on 2014-11-18
Good luck.

I only used the default installation the first time I installed Ubuntu; since then I have made my own partitions with the "Something Else" option and had a separate /home, but as far as I'm aware the default installation should do all that is needed on a UEFI system.

---

### Post by Daveski17 on 2014-11-18
> **ajgreeny said:**
> Good luck.

I only used the default installation the first time I installed Ubuntu; since then I have made my own partitions with the "Something Else" option and had a separate /home, but as far as I'm aware the default installation should do all that is needed on a UEFI system.

OK, thanks again for all the information. :D

Eventually I found a Lenovo preinstalled with Ubuntu. It is x64 with 4Gb RAM and runs at 2.6 GHz. Seems fine. :guitar:

---

### Post by vasa1 on 2014-11-26
[http://discourse.ubuntu.com/t/preinstalled-ubuntu-computers-in-the-uk/1968](http://discourse.ubuntu.com/t/preinstalled-ubuntu-computers-in-the-uk/1968)

---

### Post by Daveski17 on 2014-11-27
Thanks. I guess I should have searched harder lol. Anyway, I needed a new laptop and I really did not want Win 8. The last computer I purchased ran Android. I still like my Win 7 desktop box but I doubt I'll be buying anything preinstalled with Microsoft in the future. I'm very impressed with Ubuntu on this laptop.

---

### Post by BlinkinCat on 2014-11-27
Hi,

I could not work out if you have seen this link yet - [http://linuxpreloaded.com/](http://linuxpreloaded.com/)

Cheers - :)

---

### Post by Daveski17 on 2014-11-27
> **BlinkinCat said:**
> Hi,

I could not work out if you have seen this link yet - [http://linuxpreloaded.com/](http://linuxpreloaded.com/)

Cheers - :)

Thanks, that looks interesting. I have just purchased a Lenovo laptop preinstalled with Ubuntu from Amazon. I was considering a Galaxy laptop made to custom specifications, but the distributor couldn't guarantee the hardware would be compatible. The only other real alternative was to buy a Windows preinstalled computer and wipe it to install Trusty Tahr, with the attendant incompatibility problems. It's odd that shops/stores I phoned told me that they just couldn't find me a laptop installed with Ubuntu. I found one and I'm not in the laptop selling business. lol

---

### Post by vasa1 on 2014-11-27
> **Daveski17 said:**
> ... It's odd that shops/stores I phoned told me that they just couldn't find me a laptop installed with Ubuntu. I found one and I'm not in the laptop selling business. lol
I came across a post or article or blog quite some time back about why it isn't profitable for stores to stock Linux laptops or desktops. I think the author went by the nick of Mad Dog. I'm not sure if it was John Hall. I'll see if I can hunt down that link.

---

### Post by Daveski17 on 2014-11-27
> **vasa1 said:**
> I came across a post or article or blog quite some time back about why it isn't profitable for stores to stock Linux laptops or desktops. I think the author went by the nick of Mad Dog. I'm not sure if it was John Hall. I'll see if I can hunt down that link.

OK cheers. I can understand why it isn't particularly profitable for small shops, and even for some of the bigger chains, as most people are only familiar with Windows. But when someone in the business tells me that they can order or get me anything I wanted, then after a few days tell me they can't find it, I start to wonder. Luckily, the fates were with me.

I'll need to do some research on hardware compatibility issues. Eventually I will want to change my custom-built desktop PC (Win 7 x64) to Ubuntu. I plan on changing a few things on it soon anyway. At least there is that option with a box. Laptops are a different matter entirely.

---

### Post by vasa1 on 2014-11-27
Could you please mention the specific model of the Lenovo laptop you bought?

---

### Post by coldraven on 2014-11-27
I think this company will sell you a laptop with no OS installed. The one that I looked at was £41 cheaper without Windows. You would need to ask them about compatibility.
[http://www.chillblast.com/Laptops/](http://www.chillblast.com/Laptops/)

---

### Post by vasa1 on 2014-11-27
Oh, and what version of Ubuntu was present? Was it 12.04 or 14.04? Dell sells laptops with Ubuntu 12.04 in India.

---

### Post by Daveski17 on 2014-11-27
> **vasa1 said:**
> could you please mention the specific model of the lenovo laptop you bought?

p12-04

> **vasa1 said:**
> Oh, and what version of Ubuntu was present? Was it 12.04 or 14.04? Dell sells laptops with Ubuntu 12.04 in India.

14.04 LTS, but there was an option to order 12.04 if you wanted. I'm familiar with Ubuntu Trusty Tahr though so it seemed logical to stick with that.

> **coldraven said:**
> I think this company will sell you a laptop with no OS installed. The one that I looked at was £41 cheaper without Windows. You would need to ask them about compatibility.
[http://www.chillblast.com/Laptops/](http://www.chillblast.com/Laptops/)

There are a handful of companies who will sell you a laptop with no OS. PCSpecialist would have made me up a Galaxy laptop with a wide choice of hardware options, but they couldn't guarantee compatibility with Ubuntu. I communicated with them via email, and once they realised what I wanted they were helpful, but claimed to know nothing about any compatibility with Linux operating systems.

---

