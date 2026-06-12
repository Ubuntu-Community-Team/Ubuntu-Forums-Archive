---
title: "ubuntu studio 10.04, not detecting networking devices"
date: 2011-06-04
forum: Ubuntu Studio
---

### Post by match417 on 2011-06-04
I just got a new laptop(x86), and I absolutely hate everything about microsoft, even though I have to use their products some times. I downloaded both iso's of ubuntu studio 10.04 and ubuntu 10.04 LTS. 10.04 LTS installed perfectly, it was up and running in 30 minutes. Ubuntu studio 10.04 has not been that kind, in the initial stages of install it did not recognize the ethernet/wireless drivers of my laptop, so it didn't download the latest upgrades and driver/software packages. So right now, I have the laptop triple booted running ubuntu studio, ubuntu, and win 7 until I figure out what to do with ubuntu studio. Everything else seems to work fine except that I have no networking device that ubuntu can use right now.

How do I get the wireless/ethernet drivers for this installed in ubuntu studio? Would it be better to upgrade regular ubuntu LTS to studio so that runs flawlessly instead of trying to fidn the drivers for ubuntu studio.

WIreless is Atheros AR9285 Wireless Network Adapter PCI-Express (rev 01)
Eth is JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)

---

### Post by jejeman on 2011-06-04
There should not be any differance on the driver/module/ kernel level beetween ubuntu studio 10.04 and ubuntu 10.04. That is absolutly the same systems.

So, If I understood you correctly Ubuntu 10.04 has network working, but ubuntu studio 10.04 don't? Or they both aren't working?

---

### Post by match417 on 2011-06-04
Ubuntu LTS installed perfectly, networking works amazingly.

Ubuntu studio has no networking. 5 minutes into the install I got a message that said something along the lines of "no networking adapters detected". When the install was finished, I still had no networking enable. 

The kernels are the same, but the number after them is different I believe. studio is 2.6.32-21 i think, and LTS is 2.6.32-28 I think. I'll have to reboot to verify that, but I believe that is what it is.

I might try the installation again and see if I an find a wireless usb stick, I have two pcmcia ones, but that doesn't help since my new laptop doesn't have that slot.

---

### Post by jejeman on 2011-06-04
Ubuntu 10.04 iso image is updated, Ubuntu studio's iso is not. So thats why you have diffrent kernels.
You are using new laptop, so maybe the hardware isn't supported, by 2.6.32-21 kernel.
Secondly, ubuntu studio 10.04. does not have network-manager like ubuntu 10.04 so you have to configure netwok manualy.

You can install ubuntustudio-desktop package on ubuntu 10.04, and have all the features that clean install od ubunt studio 10.04 have.

---

### Post by match417 on 2011-06-04
so I can install it as a package through synaptic or would I have to apt-get through terminal? I guess I didn't have to download the DVD iso then after all.

---

### Post by jejeman on 2011-06-04
> **match417 said:**
> so I can install it as a package through synaptic or would I have to apt-get through terminal?
It's the same. Do as you like.
> I guess I didn't have to download the DVD iso then after all.
Essentaly no. But installing from dvd frees you from some apps that ubuntu has, and studio don't. Also, there is maybe some configuration for you to do. You will see.

---

