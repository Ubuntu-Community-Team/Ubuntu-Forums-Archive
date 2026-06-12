---
title: "Need Help with USB Port Setup on VirtualBox 4.1.4"
date: 2011-10-19
forum: Virtualisation
---

### Post by FoxtrotAnon on 2011-10-19
I've been having issues setting my virtual machine so it is able to recognize whenever something is plugged into the USB port on the host machine. I've followed all the basic rules, which were to install the VirtualBox that is on the official website and not the software center and then added myself to the users for VirtualBox and yet it still doesn't recognize anything that is plugged into the port (I'm using Windows XP (SP 3) on the virtual machine for anyone who was wondering). I'm mainly doing this so I can sync my iPod to iTunes, but all of the other instructions on how to do this are fairly outdated and obviously everything has since then changed drastically. Any help on this subject would be greatly appreciated! Feel free to simply post links if you need to.

---

### Post by haqking on 2011-10-19
> **FoxtrotAnon said:**
> I've been having issues setting my virtual machine so it is able to recognize whenever something is plugged into the USB port on the host machine. I've followed all the basic rules, which were to install the VirtualBox that is on the official website and not the software center and then added myself to the users for VirtualBox and yet it still doesn't recognize anything that is plugged into the port (I'm using Windows XP (SP 3) on the virtual machine for anyone who was wondering). I'm mainly doing this so I can sync my iPod to iTunes, but all of the other instructions on how to do this are fairly outdated and obviously everything has since then changed drastically. Any help on this subject would be greatly appreciated! Feel free to simply post links if you need to.

Do you have the extensions pack installed ?

also make sure your account is in the vboxusers group

if it isnt then

```
sudo usermod -a -G vboxusers username
```

and then also on devices menu in VBox you need to select the USB device to unmount from the host and mount in the VM

---

### Post by FoxtrotAnon on 2011-10-19
No, that wasn't the issue. I just had to simply log out and then log back in. Sorry!

---

### Post by haqking on 2011-10-19
> **FoxtrotAnon said:**
> No, that wasn't the issue. I just had to simply log out and then log back in. Sorry!

cool no worries.

enjoy ;-)

---

