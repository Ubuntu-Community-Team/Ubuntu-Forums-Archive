---
title: "Daru2 shutdown on ACPI: Critical trip point"
date: 2008-11-11
forum: System76 Support
---

### Post by williumbillium on 2008-11-11
Twice over the past few days my Daru2 running gutsy 64bit has shutdown with no warning.  I am using the ec_intr=0 kernel parameter.

I wasn't doing anything particularly resource heavy at the times it shutdown.  The first time I wasn't even at the computer.

/var/log/messages looks like this when the shutdown happened:

```
Nov 10 20:22:14 koe kernel: [ 4513.425436] ACPI: Critical trip point
Nov 10 20:22:28 koe kernel: [ 4525.340195] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Nov 10 20:22:28 koe exiting on signal 15
```

I also had a look at /var/log/kern.log which has these lines:

```
Nov 10 20:22:14 koe kernel: [ 4513.425436] ACPI: Critical trip point
Nov 10 20:22:14 koe kernel: [ 4513.425441] Critical temperature reached (110 C), shutting down.
```

Normally I would be concerned seeing a temperature so high but given this computer's track record with ACPI, I am wondering if the temperature readings are false.  However, the top of the laptop where my right wrist rests was quite hot.  Should I be concerned?  How can I tell if the reading is reflecting reality?

Please let me know if there is anything else I can provide to assist in remedying this problem.  Thanks.

---

### Post by jdb on 2008-11-11
> **williumbillium said:**
> Twice over the past few days my Daru2 running gutsy 64bit has shutdown with no warning.  I am using the ec_intr=0 kernel parameter.

I wasn't doing anything particularly resource heavy at the times it shutdown.  The first time I wasn't even at the computer.

/var/log/messages looks like this when the shutdown happened:

```
Nov 10 20:22:14 koe kernel: [ 4513.425436] ACPI: Critical trip point
Nov 10 20:22:28 koe kernel: [ 4525.340195] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Nov 10 20:22:28 koe exiting on signal 15
```

I also had a look at /var/log/kern.log which has these lines:

```
Nov 10 20:22:14 koe kernel: [ 4513.425436] ACPI: Critical trip point
Nov 10 20:22:14 koe kernel: [ 4513.425441] Critical temperature reached (110 C), shutting down.
```

Normally I would be concerned seeing a temperature so high but given this computer's track record with ACPI, I am wondering if the temperature readings are false.  However, the top of the laptop where my right wrist rests was quite hot.  Should I be concerned?  How can I tell if the reading is reflecting reality?

Please let me know if there is anything else I can provide to assist in remedying this problem.  Thanks.

ec_intr is not supported anymore, if you pass it as a kernel parameter it is just ignored so that's probably not your problem.

I did some googling & a common fix was to take the cover off & clean out the fan.

Don't know if that's the problem, but it's worth a try.

jdb

---

### Post by thomasaaron on 2008-11-11
Are you using Gutsy? If so the intr=0 option is correct.

If you are using Hardy or Intrepid, you should have the acpi=noirq kernel option.

I've never heard of the *lack* of either option giving false temp readings, though.

JDB's idea is a great one.

If you are using it on a bed or pillow that is restricting airflow, that could be a problem too.

After cleaning it out (use canned air), you should contact me at support(at)system76(dot)com for support if the problem happens again.

---

### Post by williumbillium on 2008-11-11
I am using gutsy still so thanks for clarifying the kernel option.

Both times this happened it was on a desk with adequate airflow.  Also, it is only around 6 months old but I'll try opening it up and cleaning it out.

Thanks.

---

### Post by williumbillium on 2008-11-12
I just wanted to clarify, are you suggesting I take off the case or just blow out the dust through the vent?  If the former, are the any instructions for doing so with the Daru2?

---

### Post by thomasaaron on 2008-11-12
Remove the bottom cover:

1. Remove the screws on the bottom (there are five of them)
2. Slide the bottom cover to the rear of the machine.
3. Pull up on it to remove it.

---

### Post by jdb on 2008-11-12
> **williumbillium said:**
> I just wanted to clarify, are you suggesting I take off the case or just blow out the dust through the vent?  If the former, are the any instructions for doing so with the Daru2?

I marked the screw holes with white x's.

[IMG]http://h1.ripway.com/jdbowman/pictures/daru2.jpg[/IMG]

jdb

---

### Post by williumbillium on 2008-11-17
Well I removed the case, and removed the dust from the fan with compressed air.  There wasn't a lot of dust but there was some.  It's gone now though so we'll see what happens.

One thing I did think was slightly odd was that some of the air vents in the case were covered by a plastic film.  Seemed strange to me as they would reduce air intake/circulation.  Specifically the vent over the main fan is half open and half covered.  It looks from jdb's photo that his is possibly the same.  Is this normal?

---

### Post by thomasaaron on 2008-11-17
That definitely could be the problem. The vents should not be obstructed.

---

### Post by jdb on 2008-11-17
> **thomasaaron said:**
> That definitely could be the problem. The vents should not be obstructed.

I took the back cover off again to look at it.
On the inside of the cover there are three pieces of plastic tape covering some of the vents.

It looks like it was deliberately put there.
Should it be removed ???

Thanks,

jdb

---

### Post by williumbillium on 2008-11-17
> **jdb said:**
> I took the back cover off again to look at it.
On the inside of the cover there are three pieces of plastic tape covering some of the vents.

It looks like it was deliberately put there.
Should it be removed ???

Sounds the same as mine.  I can post a photo tonight if that's useful.

---

### Post by thomasaaron on 2008-11-17
Oh, those black pieces? Those should stay there. Kind of odd, though. Not sure why they did that.

---

### Post by williumbillium on 2008-11-18
> **thomasaaron said:**
> Oh, those black pieces? Those should stay there. Kind of odd, though. Not sure why they did that.

Sounds like that's what it is.  Here's a photo of the inside of the case to confirm:

[IMG]http://www.willlaw.org/files/daru2_case.jpg[/IMG]

---

### Post by thomasaaron on 2008-11-18
yes. that's normal.

---

