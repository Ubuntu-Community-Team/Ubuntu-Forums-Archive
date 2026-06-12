---
title: "8 hrs power management on my travelmate"
date: 2010-05-16
forum: Ubuntu Studio
---

### Post by debianlinux on 2010-05-16
hi, i recently installed ubuntustudio 10.04 on my notebook travelmate 8371 series where if  i'm using vista on that, i can save power and the battery can stand long up to 8 hrs of continues usage... since i dumped vista and use ubuntu as my primary os.. i found out that i can only use my notebook just for around 2-3 hours.. is there anyway to make my notebook battery can hold up as 6-8 hours continues? how to adjust or tweak..

thanks in advance...

---

### Post by mikewhatever on 2010-05-16
Doesn't Ubuntu Studio have a low latency kernel of some kind that is useful in multimedia production, but should draw more power? Check what kernel is in use with *uname -r*, and run *sudo powertop* as well.

---

### Post by debianlinux on 2010-05-16
result for sudo powertop:  

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 4.0%)         1300 Mhz     1.9%
polling           0.0ms ( 0.0%)         1200 Mhz    98.1%
C1 mwait          0.0ms ( 0.0%)
C2 mwait          0.5ms ( 2.0%)
C6 mwait          2.3ms (94.0%)

Wakeups-from-idle per second : 448.0    interval: 15.0s
Power usage (ACPI estimate): 12.4W (3.1 hours)

Top causes for wakeups:
  45.5% (238.9)   PS/2 keyboard/mouse/touchpad interrupt
  22.7% (119.1)   [kernel scheduler] Load balancing tick
  11.6% ( 61.1)   [i915] <interrupt>
   4.3% ( 22.3)   [iwlagn] <interrupt>
   4.2% ( 22.1)   firefox-bin
   3.3% ( 17.3)   [extra timer interrupt]

Suggestion: Enable SATA ALPM link power management via:
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.


result for uname -r :

2.6.32-22-preempt

i hope this could help you to configure how..

---

### Post by mikewhatever on 2010-05-16
Well, the question here is, 'Is it imperative for you to run the preempt kernel?'.

---

### Post by debianlinux on 2010-05-16
i dont know what preempt kernel was.. and i dont know anything about power usage etc in kernel and whatsoever... i only use ubuntu for internet surfing, word processing, internet messaging and gimp graphic editing... so i think we can power down the 'power usage' as low as possible so i can use up my 8hrs feature respectively... if there's i can do to make it possible.. please help.. :)

---

### Post by mikewhatever on 2010-05-17
In this case, may I ask why use Ubuntu studio? There is nothing wrong with using it, it's just that a multimedia production OS might be an overkill for internet browsing. I am no expert in power management, so you might want to ask for a second opinion, but I think you should switch to the desktop edition.

---

