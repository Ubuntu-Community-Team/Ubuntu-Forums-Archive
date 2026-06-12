---
title: "can't get on internet with virtualbox"
date: 2010-05-16
forum: Virtualisation
---

### Post by ghetelek on 2010-05-16
I have ubuntu 10.04 as my main operating system and I have windows xp loaded in virtual box and I can't get on the Internet.  I'm a newbie

---

### Post by Revolutionary101 on 2010-05-16
I think you will have to install the Ethernet and wireless drivers for your computer from within your virtual Windows XP install.

---

### Post by Old_Grey_Wolf on 2010-05-17
From the VirtualBox window where you select the Guest OS, select the XP OS. Then select settings, then select "Network", you should see a check next to "Enable Network Adapter". Below that "Attach to" should show NAT. Next click the arrow next to "Advanced". There is an "Adapter Type" menu. I don't remember which Adapter you need for XP; however, there are only 6 of them to choose from. I think it is one of the Intel PRO/1000 that you want.

You don't have to install an XP driver within the Guest OS. The Guest OS doesn't interface to the actual hardware NIC. The Guest OS interfaces with a virtual LAN that is setup within the Host.

---

### Post by opacatica on 2010-05-21
Hard to answer why you can't browse internet without knowing your setup.  But try changing the config of your virtual network adapter from NAT (default) to Bridged.
 
This works fine for me with my computer connected to a router.  This way both your host and guest will appear to be "asside" on the network point of view.
 
If this does not solve your problem, please describe your setup:
- Do you have a router
- Is the router separate from the modem or all-in-one appliance
- What host OS runs what guest OS
  (example Ubuntu 10.04 64 bit with a virtual WindowsXP)
- What version of VBox
  (do you have the latest 3.2.0 version or a legacy version)
- What's the config of your virtual network card?

---

