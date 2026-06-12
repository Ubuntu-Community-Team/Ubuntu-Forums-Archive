---
title: "How do you check GPU temp in Linux/Windows?"
date: 2010-09-12
forum: The Cafe
---

### Post by user1397 on 2010-09-12
title says it all!

---

### Post by Bachstelze on 2010-09-12
Depends on the brand. For nvidias, nvidia-settings will tell you.

---

### Post by MadCookie on 2010-09-12
On Windows you can use "Speccy"
[http://www.piriform.com/speccy](http://www.piriform.com/speccy)

---

### Post by Frogs Hair on 2010-09-12
For  Ubuntu I use Nvidia Xserver settings for Windows I use CPUID Hardware monitor , which gives CPU, GPU , Hdd temps. , fan speed , and voltage.

---

### Post by cariboo on 2010-09-12
Add the sensors-applet to your panel, it will display cpu temp, fan speed, gpu and hdd temps.

I normally just use nvidia-settings, as gnome-shell doesn't use panel applets yet.

---

### Post by ST3ALTHPSYCH0 on 2010-09-12
x2 for CPUID in Windows. I used it to monitor everything while I was stability testing my overclock.

---

### Post by handy on 2010-09-12
I use lm-sensors on the command line in Arch (actually via a configured button in Worker :)):

>$ sensors

Here is an old link for Ubuntu, I'm sure it is easier to set up now:

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

---

### Post by user1397 on 2010-09-12
thanks for all the replies everyone.  marking this thread as solved.

---

