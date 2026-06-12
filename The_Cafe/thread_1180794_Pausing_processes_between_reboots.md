---
title: "Pausing processes between reboots"
date: 2009-06-07
forum: The Cafe
---

### Post by valerij_rozouvan on 2009-06-07
Hi all,

I want to pause a process, reboot my computer, and continue running that processes. Is it possible? For example rendering a large POV-Ray render job can take weeks, if not months. So it would be beneficial to be able to turn off your computer temporarily (for whatever reason). I googled, but beyond "kill -STOP pid" and "kill -CONT pid" (see below) couldn't find anything useful.

[How-to Pause a Linux Process]("http://tombuntu.com/index.php/2007/11/23/how-to-pause-a-linux-process/")
[How to pause and resume programs on Unix and Unix-like systems]("http://www.articleworld.org/index.php/How_to_pause_and_resume_programs_on_Unix_and_Unix-like_systems/")

Thanks in advance,
[Valerij Rozouvan]("http://www.freewebs.com/rozouvan/")

---

### Post by jerrrys on 2009-06-07
reboot will kill everything, not good in your case. why not just hibernate? make a backup first, hibernate will not always work with some...

---

### Post by valerij_rozouvan on 2009-06-07
For now, this approach is faulty. Hibernate is not that stable to do 20+ hibernates (without a proper shutdown in between). Especially when there are programs running which are using nearly 100% memory (RAM + swap).

---

### Post by sim-value on 2009-06-07
Hmm ... you have a Problem with your car ?! Ill sell you a Truck ! :lol:

Ask your relatives /friends for their old PCs/laptops and put them together in a cloud rendering should be faster then ...

PS: Month to render ... sounds interessting

---

### Post by lloyd_b on 2009-06-07
> **valerij_rozouvan said:**
> Hi all,

I want to pause a process, reboot my computer, and continue running that processes. Is it possible? For example rendering a large POV-Ray render job can take weeks, if not months. So it would be beneficial to be able to turn off your computer temporarily (for whatever reason). I googled, but beyond "kill -STOP pid" and "kill -CONT pid" (see below) couldn't find anything useful.

[How-to Pause a Linux Process]("http://tombuntu.com/index.php/2007/11/23/how-to-pause-a-linux-process/")
[How to pause and resume programs on Unix and Unix-like systems]("http://www.articleworld.org/index.php/How_to_pause_and_resume_programs_on_Unix_and_Unix-like_systems/")

Thanks in advance,
[Valerij Rozouvan]("http://www.freewebs.com/rozouvan/")

One possibility I can see - run the process in a VM.  It *should* be possible to freeze the VM, image it, and save that image to disk.  Then do your reboot, load the VM image, and continue from there.

(Note: I know little to nothing about the actual use of VM's - this is just theory :))

Lloyd B.

---

### Post by MaxIBoy on 2009-06-07
> **lloyd_b said:**
> One possibility I can see - run the process in a VM.  It *should* be possible to freeze the VM, image it, and save that image to disk.  Then do your reboot, load the VM image, and continue from there.

(Note: I know little to nothing about the actual use of VM's - this is just theory :))

Lloyd B.Actually, that would work.


You could probably do some kind of fancy jiggering with copying stuff into and out of /dev/mem and /proc, but my recommendation is to not even try. 

Your best bet is to set it up on its own dedicated machine with an uninterruptable power supply (UPS.)

---

