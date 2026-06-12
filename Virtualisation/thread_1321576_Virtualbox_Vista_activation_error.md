---
title: "Virtualbox: Vista activation error"
date: 2009-11-10
forum: Virtualisation
---

### Post by emwaiz on 2009-11-10
Hi everyone! I just wipe clean my laptop to Ubuntu 9.10 from Vista.
Still, need to use Vista for "things". So, there's Virtualbox OSE 3.0.8.

Installed Vista quickly, but entered the product key, it gave me activation error.

I found the Bios and System information in terminal using dmidecode. So, here they are;

```
BIOS Information
	Vendor: Acer   
	Version: v1.3401
	Release Date: 11/06/2007
```

```
System Information
	Manufacturer: Acer, inc.
	Product Name: TravelMate 6292
```

I entered the information in the terminal like these;

```
VBoxManage setextradata "Vistaem" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVendor" "Acer"
VBoxManage setextradata "Vistaem" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVersion" "v1.3401"
VBoxManage setextradata "Vistaem" "VBoxInternal/Devices/pcbios/0/Config/DmiBIOSReleaseDate" "11/06/2007"
VBoxManage setextradata "Vistaem" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemVendor" "Acer, inc."
VBoxManage setextradata "Vistaem" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemProduct" "TravelMate 6292"
```

Really biting myself now. Please someone, help me!

---

### Post by masux594 on 2009-11-10
I've heard another user that have some problem with VBox 3.0.8 + karmic.. an update of VBox [3.0.10] were released for some "karmic" compatibility.. .. try to install the last released version.. and after that.. retry..

Sysc, A

---

### Post by emwaiz on 2009-11-13
I'm really not ready to downgrade my virtualbox Karmic to Jaunty ... Is there any other way around to this problem. TQ!

---

### Post by masux594 on 2009-11-13
No, I said to Update virtualbox.. not the os =| .. Downoad and install VirtualBox 3.0.10, and then, retry..

Sysc, A

---

### Post by emwaiz on 2011-04-12
> **masux594 said:**
> No, I said to Update virtualbox.. not the os =| .. Downoad and install VirtualBox 3.0.10, and then, retry..

Sysc, A
Thank you! It solved my problem!

---

