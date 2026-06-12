---
title: "Dell Laptop Freezes when charging battery (previous fix doesn't work in 13.04)"
date: 2013-04-04
forum: Ubuntu Development Version
---

### Post by chicken159 on 2013-04-04
The problem: Dell e5420, Intel Graphics - When plugged into power with the battery in, the system locks up completely.

Workaround: Unplugging the power OR removing the battery immediately fixes the freeze.

Previous fix: This problem was solved for previous versions as posted here: [http://ubuntuforums.org/showthread.php?t=1885546](http://ubuntuforums.org/showthread.php?t=1885546) by setting 'drm_kms_helper poll=N'

Since 13.04 however, this no longer fixes the problem, though the onset of the freeze seems to be slightly different. I haven't had time to go digging any more on this but can't see anyone else reporting an identical issue...any thoughts? 




On a forum experience note - when I edited my original post to add the detail that the fix no longer works I got a PM saying go post somewhere else (here I am doing that). I'm sure that is the correct thing to do...but being slapped down for trying to be helpful isn't going to make me keen to come back...and now the thread is closed with innacurate info I can't edit. First subjectively negative experience of ubuntuforums.

---

### Post by dino99 on 2013-04-04
without the previous setting workaround, i'll think about a powerless battery, not able to provide enough energy (or a crappy/broken one); so ask the Dell support might be the better choice to check first.

---

### Post by chicken159 on 2013-04-04
Thanks...no its not that - the battery charges OK and the laptop works ok once the battery is charged and its unplugged...

---

### Post by dino99 on 2013-04-04
> **chicken159 said:**
> Thanks...no its not that - the battery charges OK and the laptop works ok once the battery is charged and its unplugged...

yeah, but i still think about a hardware issue, here, that battery itself, or the charging process, which is also the chip(s) associated, like the condo.

---

### Post by chicken159 on 2013-04-04
Hmm...could be I guess - any suggestions how to further diagnose? [I'll start by booting it into its evil Win7 partition and see if that affects it...just as soon as I remember what the password is...]

--confirmed that all is OK when running Win7 with battery in and charging.

---

### Post by dino99 on 2013-04-04
then watch closely the logs : /var/log/dmesg mainly & also ~/.xsession-errors

---

### Post by chicken159 on 2013-04-04
Yup...ran the following test:
1. Checked and noted contents of dmesg and ~/.xsession-errors 
2. Inserted battery, noted system frozen as expected.
3. Removed battery, noted system unfrozen and operating normally.
4. Checked contents of log files - no new entries had been added.

I'm a bit short of clues...the only other thing I have is the apparent and subjective difference in behaviour depensing on whether I have applied the previous fix or not - it *appears* that without the fix, the system slows over a period of 10s of seconds to a halt; with the fix, it works normally for a period and then suddenly freezes....except that once it has frozen the first time it then instantly freezes on a repeat battery insertion in either case. All a bit mysterious....might be time for a clean install and see how that goes?

Cheers.

---

### Post by chicken159 on 2013-04-04
OK...a clue: Whilst in recovery root mode, on inserting the power I do get "Disabling IRQ #16" at about the time the freeze would otherwise occur, but the system does not freeze. Significance anyone?

---

### Post by dino99 on 2013-04-04
hm, i've never had a Dell to fight with, so i only can suggest to recheck the bios "powersave" settings (in case), possible irq setting tweaks also.
and is that issue with all the kernels, maybe test with the previous ones.

and at last, fill a linux report.

---

### Post by chicken159 on 2013-04-04
Well following the Debugging IRQ problems guide ([https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)) I seem to have fixed it by booting with acpi=off...not that that leave me much the wiser about the actual issue...

I should note that the original problem/solution is also fixed by this option.

Cheers!

UPDATE: This doesn't seem to be as simple as it seemed - having gone home and plugged into a different power supply the ACPI=OFF option doesn't seem to fix issue any more. However - going back to kernel 3.5.0-25 allows the original solution (setting 'drm_kms_helper poll=N') to work. I'll keep digging but anyone with suggestions appreciated :)

---

### Post by kevpan815 on 2013-04-05
I wonder if your issue is what was causing my system to Lockup with the Ubuntu Mainline Kernel Updates?

By the way, as of Ubuntu Final Beta, my Dell System is no longer Locking Up at least for now.

---

### Post by dino99 on 2013-04-05
> **chicken159 said:**
> Well following the Debugging IRQ problems guide ([https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)) I seem to have fixed it by booting with acpi=off...not that that leave me much the wiser about the actual issue...

I should note that the original problem/solution is also fixed by this option.

Cheers!

UPDATE: This doesn't seem to be as simple as it seemed - having gone home and plugged into a different power supply the ACPI=OFF option doesn't seem to fix issue any more. However - going back to kernel 3.5.0-25 allows the original solution (setting 'drm_kms_helper poll=N') to work. I'll keep digging but anyone with suggestions appreciated :)

Well, you have now enough details to report about the linux kernel. Cant say its a regression compared to 3.5, as it also need a boot option. Maybe install an older kernel , like 3.2, to see if the issue exist. Then you can decide if its a regression or not.

---

