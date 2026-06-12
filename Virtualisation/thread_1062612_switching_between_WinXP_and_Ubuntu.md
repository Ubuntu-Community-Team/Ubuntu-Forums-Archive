---
title: "switching between WinXP and Ubuntu"
date: 2009-02-07
forum: Virtualisation
---

### Post by qui8 on 2009-02-07
i have WinXP installed through Virtual Machine, now i want to quickly switch between both OS, without turning off and on WinXP every time. what is the shortcut to minimise the WinXP while its running in Ubuntu so i can go back to Ubuntu and again to WinXP?

---

### Post by konqueror7 on 2009-02-07
you could save the state of the virtual machine instead...its like hibernate in windows...just select *Machine>Close>Save the Machine State*...

---

### Post by caver1 on 2009-02-07
> **qui8 said:**
> i have WinXP installed through Virtual Machine, now i want to quickly switch between both OS, without turning off and on WinXP every time. what is the shortcut to minimise the WinXP while its running in Ubuntu so i can go back to Ubuntu and again to WinXP?




ctrl-l

---

### Post by HermanAB on 2009-02-08
Use the Windows Remote Desktop Protocol and rdesktop on Linux.  Set the Vm so that it will keep running when you exit the Vm console.  This is the most efficient way to connect to a WinXP instance.  

Also see this:
[http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

Cheers,

Herman

---

### Post by Jose Catre-Vandis on 2009-02-08
So your host is Ubuntu and your guest is XP

When you start XP through the Sun xVM Control Panel or use a command line shortcut, it sounds like you are set to fullscreen. to get out of fullscreen and to a windowed position use the access key (the Right hand CTRL button on the keyboard) and F.
```
RCTRL+F
```

You might find it easier to go seamless. When in windowed mode (or in fullscreen for that matter) press Right CTRL and L. This gives you the XP taskbar above the bottom Ubuntu taskbar. To get back to windowed mode or fullscreen use the same key combination again.
```
RCTRL+L
```

---

