---
title: "Ubuntu &amp; IBM Blade Center?"
date: 2006-09-13
forum: Server Platforms
---

### Post by tstreit on 2006-09-13
Wondering if anyone out there has had the opporuntity to install Ubuntu Server on a IBM Blade Center with an attached SAN?  I had a couple of questions.

1.  I know it worked with Red Hat Linux, but I know that you have to configure the OS to work with the SAN unit, and wanted to know if Ubuntu can be configured with the same drivers and all to work with the SAN unit.

2.  By default each server (at least with Windows Servers) has to virtual network cards that are controlled by the Blade Center chassis, is Ubuntu Server edition able to accomidate two virtual network cards in the same manner.  I don't remember if it was possible with Red Hat Linux or not, it's been a while since I had that installed.

If anyone has information on this I would appreciate it.

Thanks!

---

### Post by vmguru007 on 2007-11-07
Hi,

I know it might be an old post, But seems highly hit without people finding the answer. As I knew the answer I thought I will drop it for the rest of us. 

I have installed Ubuntu with 12 blades and booted all of them from IBM DS4700 SAN box. It work like a beat and all drivers are already included in the Ubuntu releases. Updating the driver was not bad neither a bad idea.

Teaming for network cards are as well supported. You will need to get the Broadcom teaming driver for Linux and you will run in no time.

I believe the IBM Blades are rocking roll and beating all competitors at the moment let me know if you don't agree :lolflag:.

VMguru007
[ IBM Blades VS HP Blades VS Dell Blades ]("http://www.itcomparison.com")

---

### Post by tstreit on 2007-11-07
You aren't kidding when you said IBM is taking the BladeCenter concept by storm.  I have had my BladeCenter up and running for two years with a 99.9% uptime.  It has only been taken down for maintenance.  If Ubuntu works like you said I will be very interest to see if I could get it work on mine.:guitar:

---

