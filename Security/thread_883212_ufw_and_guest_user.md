---
title: "ufw and guest user"
date: 2008-08-07
forum: Security
---

### Post by animalprimate on 2008-08-07
I installed firestarter first, then learned ufw's better, now i have both installed could that be a problem?, to run them both at once? i want the best.

so i've:

> 
sudo ufw default deny

sudo ufw enable


another question, will my ufw setup that i did with master user account still be active when i log in as guest user who isn't entitled to sudo access?  I hope I'm not asking too much all in one thread, thank you for being here for us absolute begginers, its awesome. ty.

---

### Post by bodhi.zazen on 2008-08-07
IMO you should remove firestarter.

sudo apt-get purge firestarter

Then reboot and use ufw

ufw configures your firewall, iptables. In general you configure it and forget about it, ufw does not need to be run by users or set multiple times.

You can list your iptables rules with :

```
sudo iptables -L
```

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

### Post by animalprimate on 2008-08-07
okay, alright.

did you know jumbo was the name of an elephant in the 1800's?

tremendous!

---

