---
title: "AC97 Realtek Sound Driver"
date: 2007-11-09
forum: Windows
---

### Post by yyz on 2007-11-09
I have windows xp and there is no sound. In the control panel: sounds and audio devices properties it says "no audio device".

When I open the Volume Control application I get this message:


[IMG]http://img235.imageshack.us/img235/9983/volumecontrolsr4.png[/IMG]

**I installed the audio driver from windowsupdate.com, but I still have no sound**

Can I install the sound drivers from the Ubuntu or Xubuntu CD on to Windows XP?

The original Realtek AC97 Driver is not working..

Also another problem I have is that I can't adjust my screen resolution to 1024x768 which best fits my monitor. It says "video mode not supported".

Help is much appreciated.

Thank you

---

### Post by Steve1961 on 2007-11-09
Firstly you can't use Linux drivers (which are kernel modules) with windows.  Your best bet for the sound card problem is to go to the motherboard (if it's onboard sound) manufacturers website and download the sound drivers for your device from there.  Whilst there, assuming you also have onboard graphics, download and install the video driver.

---

### Post by yyz on 2007-11-09
Hi Steve1961 thank you for replying. The graphics is onboard SiS 650 and I have installed a driver for both the graphics and sound from the Microsoft Update website, but the sound still does not work.

How can I find out the manufacturer of the motherboard?

---

### Post by Steve1961 on 2007-11-09
Easiest way is to download a little utility called SIW, which should give you all the hardware info you need:

[http://www.gtopala.com/](http://www.gtopala.com/)

I've come across exactly the same problem you're having when fixing my customers PCs, and more often than not the manufacturers driver will work.

---

### Post by yyz on 2007-11-09
Hi Steve1961, the manufacturer is NEC computers international of the motherboard.

How am I exactly supposed to find drivers for that?:confused:

---

### Post by Steve1961 on 2007-11-09
Well if that's all that SIW is coming up with, you have a couple of other options. If your PC isn't just a generic box but made by Dell, HP or similar you could try searching their website.  Alternatively, have a look at the motherboard itself to see of there's a model number or serial number on it.  You could also try some of these utilties:

[http://www.techsupportalert.com/best_46_free_utilities.htm#43](http://www.techsupportalert.com/best_46_free_utilities.htm#43)

---

### Post by Steve1961 on 2007-11-09
You could also try this package:

[http://www.softwarepatch.com/utilities/ac97.html](http://www.softwarepatch.com/utilities/ac97.html)

---

### Post by yyz on 2007-11-10
> **Steve1961 said:**
> You could also try this package:

[http://www.softwarepatch.com/utilities/ac97.html](http://www.softwarepatch.com/utilities/ac97.html)

Hi again, this package did not work either :confused::(

---

### Post by Steve1961 on 2007-11-10
OK, my last suggestion would be to go into device manager and uninstall all sound devices.  Reboot and let windows redetect them

---

### Post by TheLions on 2007-11-10
can you tell us your pc specifications?
Use this program to see your spec: 
[COLOR="Blue"]
[http://www.astra32.com/files/astra32setup.exe](http://www.astra32.com/files/astra32setup.exe)[/COLOR]

---

