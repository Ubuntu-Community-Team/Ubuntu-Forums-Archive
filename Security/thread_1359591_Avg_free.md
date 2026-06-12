---
title: "Avg free"
date: 2009-12-19
forum: Security
---

### Post by ubun2_dude on 2009-12-19
I installed avg free and executed the sudo commands to start, update, and run the scan. Avg returned the following results:


Files scanned     :  806(806)
Infections found  :  0(0)
PUPs found        :  0
Files healed      :  0
Warnings reported :  0
Errors reported   :  1

How do I view the error or log file?

thanks in advance

---

### Post by aklo on 2009-12-19
I never install avg on ubuntu...but did you try using the GUI? Much better than typing commands


Btw I think there is no need for anti virus on linux computers. 


Go easy on me ,  i've only use linux for about 2 weeks.

---

### Post by ubun2_dude on 2009-12-19
Thanks for the response! Sadly i cant find the GUI. As far as i know the only need for ativirus with Unbuntu is if you dual boot windows. I will not have it running continuously, it will only be for the occasional scan :) However, it is possible that i still dont need it...

---

### Post by cariboo on 2009-12-20
From the looks of the deb, the log files should be located in /opt/avg/avg8/log

---

### Post by ubun2_dude on 2009-12-20
awesome thanks

---

### Post by odranoelson on 2009-12-20
Hi,

"As far as i know the only need for ativirus with Unbuntu is if you dual boot windows."

This is not true. Look, viruses made for windows ONLY run on windows, as far as if you write a virus for linux it will only run on linux (but writting viruses for linux is a little bit complicated...)

So the viruses you get on windows will not "pass" through the dual boot to your linux, don't worry about this.

The only way antiviruses are usefull on linux is when you want to SCAN YOUR WINDOWS partition.

Hope that helps

---

### Post by teward on 2009-12-20
actually, you can get a windows virus if you have wine installed.  seen this on a system I serviced before.  took me a while to clear it.  just make sure WINE doesn't run as root, and there shouldn't be any problems with Windows viruses.

Now for the real threat, there are a few websites that are starting attacks against Debian-based Linux systems.  It was reported at least once, so you don't really need super antivirus for Linux.  clamtk is a good one, it detects Linux viruses, as well as possible Windows infections on your WINE folder.

---

### Post by teward on 2009-12-20
> **odranoelson said:**
> Hi,

"As far as i know the only need for ativirus with Unbuntu is if you dual boot windows."

This is not true. Look, viruses made for windows ONLY run on windows, as far as if you write a virus for linux it will only run on linux (but writting viruses for linux is a little bit complicated...)

So the viruses you get on windows will not "pass" through the dual boot to your linux, don't worry about this.

The only way antiviruses are usefull on linux is when you want to SCAN YOUR WINDOWS partition.

Hope that helps

that's not entirely true, odranoelson.  Although this is true with dual boot configs, if you use WINE, you can still get those nasty Windows viruses.  Assuming that you don't run WINE as root, you'll be fine, but thats why antivirus exists.  also refer to the post I wrote before this one.

---

### Post by cariboo on 2009-12-21
Removing viruses in wine is pretty easy, just delete the wine directory in your home directory and your done. This is said as someone who refuses to use wine for anything. :)

---

### Post by __p1n__ on 2009-12-21
> **TrekCaptainUSA said:**
> that's not entirely true, odranoelson.  Although this is true with dual boot configs, if you use WINE, you can still get those nasty Windows viruses.  Assuming that you don't run WINE as root, you'll be fine, but thats why antivirus exists.  also refer to the post I wrote before this one.

There's some truism to this.  One thing that I've noticed in the posts in this thread however is the presumption of an o/s being the target.  If you look at the entire technology stack with specific regards to modern Intel-based platforms then you'll find a whole other "layer" to attack.  SMM exploits have existed for at least 3 years and a new Vt-d attack was published just last week.  In these cases the underlying microcode on the chipset is the target of the malware payload and anything running at or above the o/s level is simply the exploit target.

In any event toy applications (such as windows antivirus solutions based upon pre-defined pattern scans against hooked o/s calls such as file i/o, process load/execute, etc.) just don't cut it against modern malware that (mostly) operates outside of these areas so a preventative approach (hardened kernel, policy-driven) using a fundamentally secure platform such as linux is far more worthwhile imho.

---

