---
title: "Gazelle Professional : Fan stuck on high"
date: 2012-04-28
forum: System76 Support
---

### Post by rajeevsingh on 2012-04-28
Hello all,

Just this morning all of a sudden the fan on my System76 Gazelle Professional sped up to high and it's been stuck at high for the past hour. 

+ I have powered off the laptop and restarted several times however that does not seem to help.  

+ The laptop is placed on my study table and is in a cool environment. Nothing is blocking the air vents on the rear.

Details
=======
Hardware: System76 Gazelle Professional, approx. one year old, Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz, 8 GB RAM 


OS: 
Ubuntu Natty 11.04 x86_64 
Linux rsingh-system76 2.6.38-14-generic #58-Ubuntu SMP Tue Mar 27 20:04:55 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Any help will be appreciated. 

Regards.

---

### Post by rajeevsingh on 2012-04-28
This issue seems to have been resolved after I did the following:

i) Powered off the System76
ii) Unplugged AC adapter and took out the battery
iii) Waited for a minute
iv) Re-installed battery 
v) Restarted the laptop. 

Weird!

---

### Post by Dusty Wilson on 2012-04-29
This is exactly what fixed it for me on my Bonobo Pro.  I had to shutdown, unplug AC, and remove battery.  I have had the incredibly loud fan running for about a week or so before I had both time and patience to debug the issue.  I even installed several different Linux distros, shutdown, and rebooted tons of times during that time period.  To fix it, I had to also remove the battery.  Thanks for this, Raj.

---

### Post by isantop on 2012-04-30
If you press Fn+1 (Not Fn+F1) on the system, the fans will toggle up to full blast too. It may have been that you inadvertently hit that, and then removing power from the system reset it.

---

### Post by rajeevsingh on 2012-05-01
Thanks for the information. This is quite likely what happened. Until I researched fan issues on System76 I was not aware of the Fn+1 fan-control key combination.

---

### Post by mgolden on 2012-05-01
Is it possible to get a list of these keystrokes that the BIOS reads?  There isn't much doc about the S76 bios.

---

### Post by isantop on 2012-05-02
> **mgolden said:**
> Is it possible to get a list of these keystrokes that the BIOS reads?  There isn't much doc about the S76 bios.

Apart from the labeled hotkeys, that's the only one. The BIOS developers actually call it the "secret key".

---

### Post by cprofitt on 2012-08-24
> **isantop said:**
> Apart from the labeled hotkeys, that's the only one. The BIOS developers actually call it the "secret key".


Does this key combo work on the new Gazelle?

---

### Post by Carborundum on 2012-08-24
> **cprofitt said:**
> Does this key combo work on the new Gazelle?
It does not. I just tried.

---

