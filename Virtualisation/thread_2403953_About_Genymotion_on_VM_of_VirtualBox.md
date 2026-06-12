---
title: "About Genymotion on VM of VirtualBox"
date: 2018-10-18
forum: Virtualisation
---

### Post by satimis on 2018-10-18
Hi all,

I wonder to know whether I can run Genymotion on a VM of VirtualBox?  Since Genymotion needs VirtualBox to run.  That means I have to install VirtualBox on the VM, VirtualBox on top of VirtualBox.

Please advise.  Thanks

Regards
satimin

---

### Post by slickymaster on 2018-10-18
*Thread moved to **Virtualisation**.*

---

### Post by Claus7 on 2018-10-18
Hello,

according to this: [https://fabianlee.org/2017/09/23/ubuntu-installing-the-genymotion-android-emulator/](https://fabianlee.org/2017/09/23/ubuntu-installing-the-genymotion-android-emulator/)

I think that you install genymotion alongside virtualbox, meaning you have your ubuntu box and you install both virtualbox and genymotion in that box.

Regards!

---

### Post by satimis on 2018-10-18
> **Claus7 said:**
> Hello,

according to this: [https://fabianlee.org/2017/09/23/ubuntu-installing-the-genymotion-android-emulator/](https://fabianlee.org/2017/09/23/ubuntu-installing-the-genymotion-android-emulator/)

I think that you install genymotion alongside virtualbox, meaning you have your ubuntu box and you install both virtualbox and genymotion in that box.

Regards!
Hi,

Thanks for your advice and link.

I succeeded installing Genymotion (genymotion-2.12.2-linux_x64.bin, the personal use version download on Genymoticon website) on a Ubuntu 16.04 desktop VM of VirtualBox (Host Ubuntu 16.04 desktop).  Installation went through w/o problem including the installation of "virtualbox-5.2_5.2.20-125813~Ubuntu~xenial_amd64.deb" download on VirtualBox website.

"Custom Phone - 4.1.1 - API 16 - 768x1280(factory backup)" has been installed and running on VM VirtualBox Manager.  However it took me several house to sort out following problems:```

Unable to Start The Virtual Device
Virtual device got no IP address
The virtualbox DHCP server has not assigned an IP address to the virtual device

```
on starting its virtual version on Genymotion,

The trick is on;
-> Global Tools -> Host Network Manager

After starting "Custom Phone - 4.1.1 - API 16 - 768x1280(factory backup)" I can start the virtual device - Custom Phone of Genymotion.  But I have no idea how to use it for calling. (please see attached file- screenshot_custom_phone.png) nor to send WhatsApp.

Besides this is a Personal Use version of Genymotion.  Why it displays "Trial" on its screen?

Maybe I'll start another round cloning a new Ubuntu 16.04 VM and follow your link

Regards
satimis

---

### Post by satimis on 2018-10-18
> **slickymaster said:**
> *Thread moved to **Virtualisation**.*

Thanks

Regards
satimis

---

### Post by Claus7 on 2018-10-19
Hello,

> **satimis said:**
> Hi,
But I have no idea how to use it for calling. (please see attached file- screenshot_custom_phone.png) nor to send WhatsApp.

Besides this is a Personal Use version of Genymotion.  Why it displays "Trial" on its screen?


I have not used it before, yet looking also here: [https://docs.genymotion.com/latest/Content/03_Virtual_Devices/Emulating_sensors_and_features/Phone.htm](https://docs.genymotion.com/latest/Content/03_Virtual_Devices/Emulating_sensors_and_features/Phone.htm), I think that in order to be able to use genymotion both for calling and messages then you should need to buy a license.

I do not know if this: [https://community.kde.org/KDEConnect#What_is_KDE_Connect.3F](https://community.kde.org/KDEConnect#What_is_KDE_Connect.3F) will fit your needs.

Regards!

---

### Post by satimis on 2018-10-19
> **Claus7 said:**
> Hello,



I have not used it before, yet looking also here: [https://docs.genymotion.com/latest/Content/03_Virtual_Devices/Emulating_sensors_and_features/Phone.htm](https://docs.genymotion.com/latest/Content/03_Virtual_Devices/Emulating_sensors_and_features/Phone.htm), I think that in order to be able to use genymotion both for calling and messages then you should need to buy a license.

I do not know if this: [https://community.kde.org/KDEConnect#What_is_KDE_Connect.3F](https://community.kde.org/KDEConnect#What_is_KDE_Connect.3F) will fit your needs.

Regards!

Hi,

Thanks for your links.

What I'm trying to test is running WhatsApp on desktop computer without a SIM card nor a mobile phone.

With a mobile phone there is an easy way below;

To use WhatsApp on your computer
[https://web.whatsapp.com/](https://web.whatsapp.com/)

Pairing your phone with the WhatsApp on desktop
[https://faq.whatsapp.com/faq/web/28080003/](https://faq.whatsapp.com/faq/web/28080003/)


It is not my interest paying for a licence just for testing.  There are Open Source Android emulators such as YMMV, MEmu, Anbox etc.  Besides I can install Android on a VM for running WhatsApp.


On brief searching Internet I found follows;

How to Use WhatsApp without a SIM Card
[https://appuals.com/how-to-use-whatsapp-without-a-sim-card/](https://appuals.com/how-to-use-whatsapp-without-a-sim-card/)

How to Use WhatsApp On PC Without Mobile Phone
[https://www.techbout.com/use-whatsapp-on-pc-without-mobile-phone-21184/](https://www.techbout.com/use-whatsapp-on-pc-without-mobile-phone-21184/)

9 Best ways to use WhatsApp on PC without phone?
[https://en.softonic.com/solutions/what-are-the-best-ways-to-use-whatsapp-on-pc-without-phone](https://en.softonic.com/solutions/what-are-the-best-ways-to-use-whatsapp-on-pc-without-phone)

etc.

Regards
satimis

---

