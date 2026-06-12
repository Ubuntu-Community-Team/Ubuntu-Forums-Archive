---
title: "driver help, please!"
date: 2011-08-31
forum: System76 Support
---

### Post by Blacktalon on 2011-08-31
Hello, I have a System 76 Gazp6 Laptop.  I have VBox installed and windows 7 32 bit installed, does anyone know where I can get some the drivers for the laptop that will work with windows 7 32 bit.  So far all I been able to find has been 64 bit drivers.


Any help would be greatly appreciated.

Thank you,
~BT

---

### Post by Dragonbite on 2011-09-01
This is a good question.  I actually have a Windows 7 DVD and if I get a System 76 machine (I am very tempted) then I would be able to put it in a VM (none of my other systems are powerful enough).

From their Wiki page [[COLOR="Blue"]_BonP4_[/COLOR]]("http://www.knowledge76.com/index.php/BonP4")
> System76 provides drivers for 64-bit editions of Windows 7 only. For 32-bit or Vista drivers, please contact a support technician. 

So it sounds like all you have to do is ask!  I'm sure a direct email or phone call will give you the best results.

Post if it works out for you!

---

### Post by Flyers2391 on 2011-09-02
If Windows is in a vm, you won't need drivers from Systems 76 as the "hardware" that Windows would need drivers for are virtual.  In your vm, go to Devices > Install Guest Additions* and follow the prompts

*I'm using VirtualBox OSE 3.1.6 so wording and placement may have changed with newer releases

---

### Post by Dragonbite on 2011-09-02
So the only time you need them is when you are dual-booting?  Or can the VM benefit from any of the drivers?

---

### Post by Flyers2391 on 2011-09-04
> **Dragonbite said:**
> So the only time you need them is when you are dual-booting?  Or can the VM benefit from any of the drivers?

Correct, the drivers are essentially a compatibility level between the OS and hardware.  In a VM, the hardware layer is emulated.  The "Guest Additions" are additional compatibilities between the software and your host OS.  They allow you, for example, to not have to hit the "host" key to release your mouse from the VM, it make the connection more seamless.  

You would have traditional wireless network connections in the VM, but you can create a LAN connection that is bridged with your actual wireless connection so it can talk over WiFi even though Windows thinks it is a hard wire connection.  The limitation there is you can't see wireless signal strength inside Windows.  

Hope some of this info is useful :)

---

### Post by Blacktalon on 2011-09-06
That all worked great, I appreciate the information.  Would you happen to know of a way for me to be able to use my graphics instead of the VM graphics.  I would love to use my Nvidia geforce gtx 560M in it.

---

### Post by Flyers2391 on 2011-09-07
I think better graphics emulation is still in the beginnings so you probably won't get the performance you are looking for through a VM.  Newer versions of VirtualBox have some 3D graphics support I think with WineD3D but I haven't tested it out.  

I don't know much more about that, I assume being able to game on a VM at almost native speed is a goal, though I don't know how achievable that is.  The folks over in the VirtualBox forums may be able to provide you some [more / better] answers [http://forums.virtualbox.org/viewforum.php?f=7](http://forums.virtualbox.org/viewforum.php?f=7)

---

