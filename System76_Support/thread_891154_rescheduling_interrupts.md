---
title: "rescheduling interrupts"
date: 2008-08-15
forum: System76 Support
---

### Post by perce on 2008-08-15
powertop is reporting approximately 1000 wake ups from 
```
 <kernel IPI> : Rescheduling interrupts

```

booting with the option acpi=noirq cuts them to approximately 500 and saves approximately 3W (-20%), however it breaks sound. I didn't have so many wake ups until recently.

---

### Post by Ostien on 2009-06-20
sorry about resurrecting a dead thread but no point in making a completly new one.

I'm having the same problem (although nits more around 500-700) and I have noticed that it only occurs on a resume from hibernate if I shutdown and reboot completely  powertop shows about 10 wakeups per second from <kernel IPI> : Rescheduling interrupts.  And the power consumption is also down by about 3W (same as OP), to usually about 7.1w


```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (55.9%)         1.60 Ghz    23.7%
C0                0.0ms ( 0.0%)         1333 Mhz    22.2%
C1 mwait          0.0ms ( 0.0%)         1067 Mhz     5.1%
C2 mwait          0.3ms ( 1.4%)          800 Mhz    49.0%
C4 mwait          1.1ms (42.7%)

Wakeups-from-idle per second : 422.9    interval: 10.0s
Power usage (ACPI estimate): 10.7W (3.9 hours)

Top causes for wakeups:
  81.6% (574.5)      <kernel IPI> : Rescheduling interrupts 
   7.4% ( 52.1)       <interrupt> : extra timer interrupt 
   4.1% ( 28.8)           firefox : futex_wait (hrtimer_wakeup) 
   2.8% ( 19.6)       <interrupt> : uhci_hcd:usb3, ath 
   2.7% ( 19.3)           firefox : schedule_hrtimeout_range (hrtimer_wakeup) 
```

I'm using a Asus EeePC 1000HE with Ubuntu Netbook Remix (jaunty)

UPDATE: Seems this is also happening now after a reboot.  After a bit more digging it at first looked like firefox was the problem but then I figured it was not firefox itself but sites with embedded youtube videos caused this problem,  It't not a big problem with a site with one video but I was on a site with many (Andrew Sullivan is covering the Iran situation and is throwing up a lot of videos posted on youtube from Iran).

I'll do some further checking to see if it is firefox drawing a lot of resources for things like youtube.

---

### Post by perce on 2009-06-20
You revived the wrong thread actually, for two reasons: my original post is a couple of releases old, and this is a subforum for system76 computers. You should repost it in the general help forum.

---

