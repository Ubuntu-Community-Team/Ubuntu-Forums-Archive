---
title: "Brightness keys don't work Daru2"
date: 2008-09-05
forum: System76 Support
---

### Post by elusivespoon on 2008-09-05
Using Fn-F4 or Fn-F5 doesn't change my brightness. I've tried a couple of fixes from the forums, none of which have worked on my Daru2. (One was adding "blacklist video" to  /etc/modprobe.d/blacklist, and the other changing the scripts in  /etc/modprobe.d/blacklist). Any suggestions?

---

### Post by greg_g on 2008-09-05
Do you remember any changes that happened to the sytem relatively soon before it stopped working?  I'm assuming it was working at some point as mine works and hasn't ever had problems.

---

### Post by elusivespoon on 2008-09-05
Yes. I upgraded to Hardy.

---

### Post by greg_g on 2008-09-05
Have you installed and run the System76 Driver?
[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

---

### Post by elusivespoon on 2008-09-07
Well, when I run the System76 driver it says version 2.2.1 in 'about', but in Synaptic it says it's version 2.2.2. So I might not have the latest version.

---

### Post by AusIV4 on 2008-09-07
On my Gazelle, I had a similar issue where any ACPI controlled keys would stop working after resuming from suspend. Does this happen after fresh boots, or just after suspending?

---

### Post by elusivespoon on 2008-09-07
Fresh boots. (At the moment you can't suspend a Daru2 with out problems).

---

### Post by thomasaaron on 2008-09-08
elusivespoon,

If you are using the kernel option that fixes the power management on the daru2, it hoses the brightness keys.

Right now, the workaround is to put a brightness applet on one of your panels. Let me know if you need help with this.

---

