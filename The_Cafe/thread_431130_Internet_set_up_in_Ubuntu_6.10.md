---
title: "Internet set up in Ubuntu 6.10"
date: 2007-05-02
forum: The Cafe
---

### Post by wwtza on 2007-05-02
Hi, all!

Is there any one capable of helping me set up my ADSL internet connection in Ubuntu 6.10, please! As I do not need a modem/router I am only using an onboard ethernet connected Thompson model SmartAX MT882 ADSL modem.
This might be pretty simple to do, but I can't simply do it. Please see if you can be of help in this regard. Thank you in advance for your kind co-operation.
Amilcar Reis

---

### Post by misconfiguration on 2007-05-04
I'm not sure exactly what you mean..

You can configure your ethernet card many different ways, if you're connecting DIRECTLY to your PC from the modem, you need to make sure the modem has been rebooted since the last time it was plugged into a interface.

Also, most of the time you need to 'dial-in' with ADSL services, the easiest way to do this without a router would be. Directly connect the modem to the PC, set your static IP options to match the subnet of the IP of the modem.

Modem IP 192.168.0.1
IP of YOUR ethernet card = 192.168.0.2
subnet 255.255.255.0
gateway 192.168.0.1

You can manually enter the above or just click System > Administration > Networking to configure you eth0 device. Now open your browser type in 192.168.0.1 and you can manually put in your username//password for the ISP, now the MODEM will handle this information in the firmware instead of having a router do so, or software managing the info.

Put your eth0 IP address back to DHCP remove your gateway and reboot the modem and PC, see how well this works?

---

