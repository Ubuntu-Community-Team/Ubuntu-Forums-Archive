---
title: "suspend-to-ram appears to succeed but fails to recover"
date: 2010-03-27
forum: System76 Support
---

### Post by arch_o_median on 2010-03-27
Model Number:     gazp3
Ubuntu Version:   9.10 karmic
Symptoms:       
      After running sudo /etc/acpi/sleep.sh sleep the laptop shuts down without apparent error.  The only sign of life is the blinking green power led.   Once I press the power button the fan begins running at high rpms, and the hard-drive access light blinks occasionally.  This state persists until I get tired of waiting and cycle the power (approx. 2 minutes, at longest).   There is no other sign of life, e.g. the screen is blank.

   Some idiosyncracies about my system:

   I dislike gnome and have uninstalled it.   Apparently the system76-driver expects gnome and will not run without it.    This complicates things in that I cannot attach system76-driver generated diagnostics.... 

   I attached logs (/var/log/syslog) and dump of dmesg.

---

### Post by thomasaaron on 2010-03-29
We only support standard Ubuntu (gnome). What are you running? KDE?

Also, are you running 32-bit or 64-bit (U/Ku/Xu)buntu? 64-bit seems to have better support for suspend than 32-bit.

---

### Post by arch_o_median on 2010-03-29
I'm using dwm ([http://dwm.suckless.org/](http://dwm.suckless.org/)) as my window manager, on top of X.  I'm running 64-bit Ubuntu.

---

### Post by thomasaaron on 2010-03-30
OK. One two more questions before we start working on this one...

1. Does the machine suspend if you run it with the gnome window manager?
2. If you run it in gnome and turn off desktop effects, does it suspend?

---

### Post by arch_o_median on 2010-03-30
Well I'm embarrassed to admit, I haven't managed to reinstall gnome yet.  I'm currently using gparted to make a new partition to install a fresh ubuntu on.  
  I have noticed that the caps-lock light is unresponsive after a failed recover-from-suspend so I suspect the bug is not in the display software...

---

### Post by arch_o_median on 2010-04-01
After "apt-get install(ing) ubuntu-desktop", I suspended using the gnome widget under System->Shut Down->Suspend.

  The machine suspends but fails to recover with no apparent change in symptoms:

  - flickering hard-drive light
  - high rpm fan
  - blank screen
  - no response in the caps-lock LED when I press caps lock.

  I don't know how to turn off desktop effects.  Are they on by default?

---

### Post by thomasaaron on 2010-04-02
To turn desktop effects off, go to System > Preferences > Appearance > Visual Effect and select None.

If that doesn't help, go ahead and post logs after the next failed attempt to recover. Please go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

I'll have a look at it and see what I can figure out.

---

### Post by arch_o_median on 2010-04-02
OK.  I checked the desktop effects, they were set to off. 
  I attempted suspend from gnome-gui again with the same result. 
  I attached the system76 log.   
  By the way, suspend-to-disk works, and now that I think about it, it may be that suspend-to-RAM has never worked for this machine.
   Thanks for the attention!

---

### Post by thomasaaron on 2010-04-02
We may have had suspend to ram working on that machine at one time. If memory serves, it took some tinkering with a config file. I'll dig through the old documentation on Monday and see what I can drum up.

---

### Post by Alver on 2010-04-03
> **arch_o_median said:**
> After "apt-get install(ing) ubuntu-desktop", I suspended using the gnome widget under System->Shut Down->Suspend.

  The machine suspends but fails to recover with no apparent change in symptoms:

  - flickering hard-drive light
  - high rpm fan
  - blank screen
  - no response in the caps-lock LED when I press caps lock.

  I don't know how to turn off desktop effects.  Are they on by default?

Hi there, I've been suffering from the same phenomena as you described above (I'm running Xubuntu 9.10 on a Toshiba Satellite 2410-303) after using the "suspend" button at the end of a working session and I have not been able to make my laptop recover. From what I read I gather that you managed to get your machine working again. How did you go about??

Thx for a possible reply

Alver

---

### Post by MichaelNW on 2010-04-04
> **arch_o_median said:**
> Model Number:     gazp3
Ubuntu Version:   9.10 karmic
Symptoms:       
      After running sudo /etc/acpi/sleep.sh sleep the laptop shuts down without apparent error. 

And then the screen never comes back.

I have a very similar problem. Once the system suspends only a reboot will bring it back to life.  

Please share the solution here.

---

### Post by arch_o_median on 2010-04-05
Hi there!   I have now set up my system to run on a gnome session.  This means I can run the system76-driver.  I ran "Install Drivers", and "Restore System", to make my machine as close to default as the driver is capable of.  I attached the logs generated immediately after running the above.

  Please let me know if there're trouble-shooting, debugging, etc. tasks I can undertake to help with this problem.

---

### Post by MichaelNW on 2010-04-06
FWIW - I upgrade to Kubuntu 10.4 and power management is now working wonderfully.

---

