---
title: "Not able to install Intell 865 graphics driver in Virtual-machine.."
date: 2010-11-09
forum: Virtualisation
---

### Post by tajiknomi on 2010-11-09
[SIZE=2]I have installed **Xp** Via my **Virtual-Box**,
it gets all driver Except my graphics-driver.

i downloaded the driver from different sources but when i am going to install it ,it shows me the Error message **"No inf Information was found for your Hardware"**

More-over i had Accelerate my Video memory to MAX 4 Virtual-machine.

How can i install my Graphic driver now...?
[/SIZE]

---

### Post by fjgaude on 2010-11-09
ASAIK you can't install a graphics driver as it is emulated in software by VBox or in VMware.

---

### Post by tajiknomi on 2010-11-10
[SIZE=2]thanks for the reply...

but how can i play my games in VB then..?as it is not getting my graphics driver....!!

All other driver's are **automatically installed by default** but problem in installing graphics driver only....well its not like that ,that i am unable to watch vedio's clearly or something else..but i am sure that my games will not play as i haven't installed **suitable graphics driver**....
[/SIZE]

---

### Post by SeijiSensei on 2010-11-10
Short answer is you probably can't.  VM's aren't really well-suited for games that demand direct access to the video hardware or expect to see high-powered graphics adapters.  The VM software presents a generic video interface to the virtual machine.

For games that need these resources, your only real recourse is dual-booting.

---

### Post by C0derBear on 2010-11-10
VirtualBox tools includes a MS Windows display driver that suports hardware-accelerated DirectDraw and Direct3D ( up to DirectX 9c ).

You must have the VM configured to enable the ddraw and d3d acceleration, and it seems like you need to install the virtualbox tools while in Safe Mode in XP, but then it can work.

---

### Post by tajiknomi on 2010-11-10
> **C0derBear said:**
> 
You must have the VM configured to enable the ddraw and d3d acceleration, and it seems like you need to install the virtualbox tools while in Safe Mode in XP, but then it can work.

[SIZE=2]I had enabled the **3d acceleration** of Virtual-box...
which **tools** u are talking about(to install it in **safe-mode**) for VB..?
sorry i haven't used any virtual-machine b4 ,
[/SIZE]

---

### Post by C0derBear on 2010-11-10
> **tajiknomi said:**
> [SIZE=2]I had enabled the **3d acceleration** of Virtual-box...
which **tools** u are talking about(to install it in **safe-mode**) for VB..?
sorry i haven't used any virtual-machine b4 ,
[/SIZE]

Once you have your VM booted into windows safe mode ( hit F8 and select Safe Mode GUI while Windows is booting ) go to the menu for your VM and pick Devices -> CD/DVD Devices -> VBoxGuestAdditions.iso.

Once that ISO has been mounted if Autoplay doesn't do it for you, you should be able to run the installer by going to the "DVD" within Windows, browsing it, and running either the VBoxWindowsAdditions-x86.exe or VBoxWindowsAddtions-AMD64.exe and install the drivers.

---

### Post by tajiknomi on 2010-11-11
[SIZE=2]Thanks for your Kind replies...now the **driver is installed** by VBoxWindowsAddtions....:guitar:


[/SIZE] [SIZE=2]
[/SIZE]

---

### Post by fjgaude on 2010-11-11
With driver installed do you get what you wanted with respect to games?

---

### Post by tajiknomi on 2010-11-21
> **fjgaude said:**
> With driver installed do you get what you wanted with respect to games?

[SIZE=2]No i still didn't able to play game's **within Virtual-Machine** and now i realize that it will **not work**,because all the driver's are **virtual** and it will not play **3d Game's**,however it can play simple **2D games**.....
But 2D game's ..... Su**K's....;) Therefore am not playing games anymore, 
well i have decided to **Dual-Boot Ubuntu with Win-7** so that i can play my Desire Game's on windows :p...............[/SIZE]

---

