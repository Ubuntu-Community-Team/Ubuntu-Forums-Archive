---
title: "Bluetooth is disabled and won't turn on"
date: 2014-07-11
forum: System76 Support
---

### Post by Lars Noodén on 2014-07-11
I've done a fresh install of Ubuntu 14.04 LTS on a gazp9 and added the system76 drivers.  Both before and after adding the drivers bluetooth is marked as disabled and there seems no way to turn it on.  If I go to System Settings -> Bluetooth -> On, the message in the window still says that bluetooth is disabled.  I can also turn airplane mode on and off but that only seems to  affect the wireless not bluetooth.  

How do I enable bluetooth in 14.04 LTS?  

Previously, when the system was based on Lubuntu 14.04 with the package Ubuntu-desktop added, bluetooth was available with no extra action needed.

---

### Post by TheFu on 2014-07-11
What does **rfkill list** show?

---

### Post by Lars Noodén on 2014-07-11
Thanks!  It said

```

2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

So unblocking it made it show up.

```

sudo rfkill unblock bluetooth

```

I'll have to see if that survives a reboot.  Funny that was not necessary before with other installs on the same hardware.

---

### Post by TheFu on 2014-07-11
Glad it worked!

I have to enable wifi from time to time too on my C720.  I thought that was due to my mostly wired ethernet use. I've never gotten a general BT connection to work with this machine.

---

### Post by ehud on 2014-07-31
Thank you! this was showing up intermitently, usually after i had the BT headphones connected and then off. solved it for me :)

---

