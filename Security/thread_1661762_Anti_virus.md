---
title: "Anti virus"
date: 2011-01-07
forum: Security
---

### Post by smss on 2011-01-07
Is Any anti-virus for Linux?
 I have two operating systems (Windows - Linux).
 In Windows I am faced with the terribly virus that can even change my password.
 I want an Anti-virus for linux.

---

### Post by cry8wolf9 on 2011-01-07
im actually also looking for a virus scanner that runs in ubuntu from a flash drive or portable hdd and can scan windows partitions for viruses and other nasty things

---

### Post by qamelian on 2011-01-07
Clam Antivirus is in the Software Center and you can add a GUI by installing Clamtk.

---

### Post by wojox on 2011-01-07
> **cry8wolf9 said:**
> im actually also looking for a virus scanner that runs in ubuntu from a flash drive or portable hdd and can scan windows partitions for viruses and other nasty things

I use [Trinity Rescue Kit | CPR for your computer]("http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en")

It's great for Windows.

---

### Post by cry8wolf9 on 2011-01-07
> **wojox said:**
> I use [Trinity Rescue Kit | CPR for your computer]("http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en")

It's great for Windows.
thanks for the info it looks like its exactly what im looking for. i have a few questions though.
 the command
```

[FONT=Courier New]/bin/virusscan [/FONT]

```
[FONT=Arial][COLOR=black]is that a general virus scan for all operating systems? also where does it pull the virus definitions from? i saw the clam antivirus in there, now does that also work on windows viruses?[FONT=Courier New][/FONT][/COLOR][/FONT]

---

### Post by bodhi.zazen on 2011-01-07
Most antivirus scanners scan for all known viruses on all os.

Most Linux users do not need antivirus and most of the time it is a waste of time to run them.

---

### Post by smss on 2011-01-07
Thank you of everyone for the fix this problem.

---

### Post by Rob-NYC on 2011-01-07
Careful with AVG85 installations. I installed it with the Ubuntu Software Center over Ubuntu 10.10 and it crippled my PC. 

I was never able to access the AVG program -- didn't appear in the menus -- but it overwhelmed the CPU as if it were running a full system scan.

Finally had to scrub the drive and reinstall Ubuntu.

Is this typical of any 3rd party software?

---

### Post by cariboo on 2011-01-07
AVG-8 is a command line program, so you won't see a menu entry for it. Re-installing is a bit drastic, when all you had to do was stop the process. The easiest way for a new user, would be to go to System->Administration->System Monitor->Processes, highlight the problem program and click, end process.

---

