---
title: "Kernel upgrade not sticking on Starling"
date: 2009-07-06
forum: System76 Support
---

### Post by biologic on 2009-07-06
After receiving my netbook, I immediately ran sudo aptitude update && sudo aptitude safe-upgrade. This prompted me to install the 2.6.28.13 kernel. However, after rebooting and running uname -r, it's still running on the 2.6.28.11 kernel, and /boot/grub/menu.lst still only has entries for the old kernel in it, and none for the new.

What's up?

---

### Post by thomasaaron on 2009-07-07
Run...

sudo apt-get update
sudo apt-get --assume-yes dist-upgrade

---

### Post by biologic on 2009-07-07
Running the specified commands resulted in no change.

"Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

sudo aptitude safe-upgrade has appropriately updated the kernel in my Ubuntu desktop. Still not sure why it's not working on the netbook.

---

### Post by thomasaaron on 2009-07-08
I'm not sure why it's doing that. I've not heard of many people upgrading that way. Safe-upgrade has been known to do weird things based on dependencies.

I'd recommend using Administration > Update Manager for your updates/upgrades, or using the apt-get commands mentioned above.

---

### Post by biologic on 2009-07-09
So how do I fix it so that I'm running on the current installed kernel?

---

### Post by Vrekk on 2009-07-10
I had this problem on mine, but it wasnt that the Kernel not getting installed, it is that the menu.lst file wasnt edited to reflect it.  I fixed it by running 

```
sudo gedit /boot/grub/menu.lst
```

Then i made a copy of the first entry on the list (just in case) and changed every 2.6.28-11 in the first entry to a 2.6.28-13 

That worked fine for me.  Hope this works for you as well

---

### Post by biologic on 2009-07-10
That probably would have worked but I was looking for a more permanent solution. After doing additional searches on the Ubuntu forum, I found the following instructions, which worked perfectly:

sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.old
sudo update-grub
answer 'yes' to the prompt to create a new menu.lst

I guess something with the old menu.lst was corrupt.

---

