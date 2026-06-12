---
title: "I don't like the hassle of dual-booting/ have basic question about virtualization"
date: 2008-01-14
forum: Virtualisation
---

### Post by boriquajake on 2008-01-14
I am a refugee from the "Absolute Beginners" forum so please forgive me the silly questions.

I have two fairly mission critical apps that I need to be able to run on my laptop. I need to be able to use either Microsoft Streets and Trips or Delorme Street Atlas, and I need to be able to use my EVDO PCMCIA card. I have messed around with WINE for the mapping and GPS program and I have spent many hours searching forums and trying to follow how-tos with no success on the EVDO front and I have come to the conclusion that Virtualization is the way for me to go. My laptop has no windows partition right now so I am starting from scratch.

I would like to know what is the minimum I need to accomplish my goal. Right now my understanding is that I need to purchase a license for VMware Workstation and a copy of a Windows OS like XP, is that correct?

---

### Post by Vadi on 2008-01-14
Hang on with a license for VMware, because there's also Virtualbox, another virtualisation program, which is open-source even.

You can also get a trial version of vmware products. The reason you want to hold off purchasing is that it *might* not work.

But as for Windows, see if you can get just an install CD for that too. You can use Windows for 30 days before needing to register it - so if it won't work, you won't be wasting money.

In short, get either the trial versions of vmware or the full version of virtualbox, and a windows install disk, test those. If they work, then go ahead with your purchase.

---

### Post by Mit kebes on 2008-01-14
I was able to download a free version from the VMWare site that's worked perfectly for running other operating systems. it doesn't have all the features installed, but it has plenty for what I want to do. I would get the free version (be sure to register before downloading!) and see if that will work for you.

---

### Post by yottabit on 2008-01-14
AFAIK VirtualBox will not allow booting a raw partition on the physical disk.

VMware-Server does allow this, and this is how I run my XP VM.

I boot Ubuntu native on sda2, while I have a native XP installation on sda1.

I created a separate hardware profile in XP, and I can choose "native" or "virtual" when loading XP, depending whether I'm booting it native or in the VM.

I also changed the virtual XP profile from "ACPI Multiprocessor" to "Standard PC" kernel which improved the VM speed tremendously.

I typically run XP in the VM and connect to my work VPN which locks down the network stack of the VM, but leaves me to do whatever I like in my native Ubuntu. Occasionally I need to run XP with direct hardware access for my EVDO Cardbus card, GPS connection, or Cardbus flash drive loading, so I can choose to boot XP natively whenever needed.

P.S. My notebook BIOS sees my physical disk differently than the VMware BIOS does (evidenced by XP saying "NTLDR compressed" while booting, so I had to create a virtual boot floppy that VMware boots when loading my XP in the VM environment. This just involved formatting the virtual floppy as FAT16, copying ntldr, ntdetect.com, and boot.ini to the floppy. You can use a real floppy if you like, but I don't even have a floppy drive any more, so I just created a floppy in a loopback device, did what was needed, and then told VMware to boot the floppy for the XP VM. If you need a copy of this virtual floppy image just PM me and we'll arrange it.

J

---

### Post by boriquajake on 2008-01-15
> I typically run XP in the VM and connect to my work VPN which locks down the network stack of the VM, but leaves me to do whatever I like in my native Ubuntu. Occasionally I need to run XP with direct hardware access for my EVDO Cardbus card, GPS connection, or Cardbus flash drive loading, so I can choose to boot XP natively whenever needed.


So, does that mean that I will not be able to connect my Kyocera EVDO card using VMware? My hope was to be able to open up vmware and connect to the internet using my EVDO card from XP and then share the connection to Ubuntu. Is that hope dashed against the cold, hard rocks of reality?

---

### Post by yottabit on 2008-01-15
I have a Novatel V620 EVDO card that works by including a USB hub and two USB devices (data port & monitor port). Since this is USB-based, I suspect the USB pass-through function of the VM may allow the card to work, but I have not tested it. If your card works in a similar way, there may be hope!!

J

---

### Post by yottabit on 2008-01-15
P.S. I just re-read your post and it struck me as odd. Why would you want your VM to control your Internet connection and share it with your native host? It should be done the other way around...

I have no problems using my V620 with Ubuntu and the PPP dialer, after I set some keepalive options different than default (Google search for "V620 evdo linux disconnect" or something like that).

Also, if you're using bridged networking, you may need your LAN to be plugged into a switch, or else use a loopback plug to keep your Ethernet interface "alive." You can create a loopback plug very easily simply by taking a new 8P8C (usually erroneously called an RJ-45) plug, and a short length of Ethernet cable. Strip the outer sheath of the Ethernet cable, pick your two favorite colored wires, cut to a small length, and then in the 8P8C plug, run pin 1 to 3, and pin 2 to 6. Crimp, and you're ready to go. Now all packets sent out your Ethernet interface will immediately come right back in, so this way we're sure your bridge will work correctly. I had to do this with VMware back in year 2000; perhaps it's different now, but if it doesn't work you'll know you need this loopback plug.

J

---

### Post by ex_treeclimber on 2008-01-16
I have spent the last two evenings trying to get the Delorme Street Atlas program to work in a virtual Windows XP SP environment under a Ubuntu Studio 7.10 host system on an HP nc6400 laptop.  The end result is that I have never spent a worse 10 hours doing system management work.

The Delorme Street Atlas program installed correctly.  My problem was that I was not able to get Bluetooth to work under virtual XP SP2.    I tried to connect to the notebook's internal Bluetooth transmitter.  I tried to connect to a Kensington USB Bluetooth 2.0 dongle.  I loaded the Windows XP SP2 Bluetooth drivers.  I tried the HP-supplied WinComm 4.0 Bluetooth drivers.  I tried the Kensington-supplied WinComm 5.0 Bluetooh drivers.  Nothing worked.

You believe that you can avoid the Bluetooth problem by using an external  USB GPS.   Please not that I found connecting an external USB device to a virtual XP SP2 environment to not be reliable.  It seemed the only way I was able to connect an external USB flash drive to my virtual XP environment was to shut down my computer completely, attach the USB flash drive, boot the host Linux system, and finally virtually boot the XP SP2 enviroment.  Under that scenario, I could locate the USB flash drive most of the time.

So be careful what you wish for.  You may find running the Delorme mappiing software in a a dual boot system to be frustrating.  But, from my experience, trying to run Delorme in a virtual XP SP2 environment on a notebook is an invitation to spend time in system manager hell.

Good luck.  Please let me know if you succeed.  As for me, tonight I am going to wipe the drive on my notebook and begin the installation of a dual-boot Windows/Linux environment.

---

### Post by yottabit on 2008-01-16
Good notes, thanks for the attempts.

I have the original DeLorme Earthmate USB (the one that actually works). I haven't tried bridging that device into my VM yet, but I will when I next get the opportunity.

FWIW, you must unload the drive associated with your USB device before you can map/bridge it into the VM. For instance, if you plug in a USB HDD, the Linux kernel will detect the new device, then hotplug will load the appropriate driver/module, and then autofs will auto-mount the volume. You must unmount the volume and unload the module/driver before you can map the device through to the VM. This goes for both VMware Server and Workstation.

---

### Post by boriquajake on 2008-01-16
So it sounds to me like the only way to reliably use a map program is going to be to dual boot. Is that the consensus? 

By the way, thank you to everyone that has chimed in. I really appreciate it.

---

### Post by boriquajake on 2008-01-16
> **yottabit said:**
> P.S. I just re-read your post and it struck me as odd. Why would you want your VM to control your Internet connection and share it with your native host? It should be done the other way around...

I have no problems using my V620 with Ubuntu and the PPP dialer, after I set some keepalive options different than default (Google search for "V620 evdo linux disconnect" or something like that).

Also, if you're using bridged networking, you may need your LAN to be plugged into a switch, or else use a loopback plug to keep your Ethernet interface "alive." You can create a loopback plug very easily simply by taking a new 8P8C (usually erroneously called an RJ-45) plug, and a short length of Ethernet cable. Strip the outer sheath of the Ethernet cable, pick your two favorite colored wires, cut to a small length, and then in the 8P8C plug, run pin 1 to 3, and pin 2 to 6. Crimp, and you're ready to go. Now all packets sent out your Ethernet interface will immediately come right back in, so this way we're sure your bridge will work correctly. I had to do this with VMware back in year 2000; perhaps it's different now, but if it doesn't work you'll know you need this loopback plug.

J

My Brother,

I would freaking love to be able to get my EVDO card to run in Linux but I am way too stupid to follow all but the most specific instructions. Essentially if it doesn't say ```
paste this into terminal, Idiot
``` I can't figure it out.
;-)

---

