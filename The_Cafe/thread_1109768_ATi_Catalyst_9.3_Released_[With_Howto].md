---
title: "ATi Catalyst 9.3 Released [With Howto]"
date: 2009-03-29
forum: The Cafe
---

### Post by Vince4Amy on 2009-03-29
Even though I've left the forums I did however say I'd still post updates and help guides for those who do care. 

The ATi Catalyst 9.3 driver has been released and can be installed OOTB on Ubuntu 7.10+. **This driver will NOT work on 9.04 as it uses a newer version of X**

If you have used the restricted manager or envy make sure to disable them and uninstall the driver before doing the below. 

*Download The Driver*
```
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run
```

*Run The Driver Installer*
```
sudo sh ati-driver-installer-9-3-x86.x86_64.run
```

Choose ALL automatic steps.

*Configure The ATi Driver With X*
```
sudo aticonfig --initial -f
```

Then reboot your system. Alternatively you can press ctrl-alt-backspace to restart X but this may not work as reliably as simply rebooting. 

**Do not turn this into a bashing thread. If you do then I will ask for the entire post to be deleted and I will not longer post help or howtos.**

---

### Post by Eisenwinter on 2009-03-29
I've had trouble with Catalyst, both on Ubuntu, and on Arch.

I use the opensource driver for Radeon 9200, works nice and smooth :P

---

### Post by Vince4Amy on 2009-03-29
> I use the opensource driver for Radeon 9200, works nice and smooth

Yeah the OSS Driver works on my 9550 but on my X1550, X1950 and HD4850 the OSS Driver is simply not an option.

Have you tried 9.3? It was always buggy on Arch for me but when I try it on Ubuntu it usually works.

---

### Post by BramWillemsen on 2009-04-03
Thanks for the guide. It showed up high on google. Guides like this are really helpful for new people like me. Btw, i first disabled the proprietary drivers before installing this. That is the right way to go right? To avoid conflicts? I did not manage to find the new ** catalyst control center **. With the proprietary drivers there was a shortcut in the applications tab. 

Thanks for your help!

Bram

---

