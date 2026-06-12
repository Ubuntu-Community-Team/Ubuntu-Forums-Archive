---
title: "Kubuntu bootsplash"
date: 2010-04-23
forum: The Cafe
---

### Post by iRiUX on 2010-04-23
Not sure about the Ubuntu bootsplash, but the Kubuntu one didn't work until yesterday... I haven't updated today to see if it does work now.

Are they purposely waiting or its something they're having difficulty with? Its really close to final release date.

---

### Post by NightwishFan on 2010-04-23
It works here, perhaps your problem is with plymouth itself. Do you just not get a boot splash?

---

### Post by iRiUX on 2010-04-23
I see no boot splash... I first see a blinking underscore "**_**", then I see some warningings, followed by a blue bar at bottom left corner, and it jumps to KDE splash screen... thats it...

---

### Post by NightwishFan on 2010-04-24
Then I think thats just a plymouth problem. When shutting down I see the new Kubuntu logo with all blue.

---

### Post by James78 on 2010-05-01
I have the official Ubuntu(KDE) 10.04 64-bit release, and all I see is a blinking underscore too, then it flashes the splash screen for a second and is at the login.. I want to see the Kubuntu splash! :(

---

### Post by kio_http on 2010-05-01
Save problem here. I see the Splash on the last second of the booting process. Before that its the blinking underscore. Could you others having this problem state your screen resolution? I get the splash on live cd but not on installed version!:confused:

---

### Post by praveesh on 2010-05-02
> **kio_http said:**
> Save problem here. I see the Splash on the last second of the booting process. Before that its the blinking underscore. Could you others having this problem state your screen resolution? I get the splash on live cd but not on installed version!:confused:

Update after a week . The issue with plymouth is a known one , I think .

---

### Post by MirzaD on 2010-05-02
I allso have this problem, and this is after the final version has been released...
Anyone have more information, solution, or bugreprot ?

---

### Post by James78 on 2010-05-06
For people who want to see the splash screen, here is a fix for you guys.

Type into terminal...
> sudo echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash && sudo update-initramfs -u

If permission is denied, then simply just create the file, then paste the contents into it.

The problem is that the graphics driver doesn't have enough time to initalize before plymouth can take care of displaying the splash screen, then the system decides to go ahead and startx since it's taking too long. What this does, is introduce a ~0,5 second boot delay, which allows the graphics driver to take hold, and lets plymouth show the splash screen. The boot delay really isn't that bad, I don't even really notice it at all.

Enjoy the fix!

---

### Post by kio_http on 2010-05-06
> **James78 said:**
> For people who want to see the splash screen, here is a fix for you guys.

Type into terminal...


If permission is denied, then simply just create the file, then paste the contents into it.

The problem is that the graphics driver doesn't have enough time to initalize before plymouth can take care of displaying the splash screen, then the system decides to go ahead and startx since it's taking too long. What this does, is introduce a ~0,5 second boot delay, which allows the graphics driver to take hold, and lets plymouth show the splash screen. The boot delay really isn't that bad, I don't even really notice it at all.

Enjoy the fix!

I believe it is ```
sudo update-initramfs -u
``` and **NOT** initramfs -u

---

### Post by NightwishFan on 2010-05-06
If permission is denied run:
```
sudo su
```

Then:
```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash && sudo update-initramfs -u
```

Then:
```
exit
```

---

### Post by James78 on 2010-05-06
> **kio_http said:**
> I believe it is ```
sudo update-initramfs -u
``` and **NOT** initramfs -u
Oops, typo, excuse me. ;)

---

