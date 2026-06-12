---
title: "Geek squad -- battery replacement"
date: 2011-04-11
forum: The Cafe
---

### Post by Tadcrazio on 2011-04-11
So my Ubuntu is telling me that my laptop battery may be old or broken it is only accepting a charge of up to 45.7%. Well I'd agree with Ubuntu on this one, but my question is does anyone think that geek squad will replace the battery seeing as I am still under warranty?

---

### Post by leclerc65 on 2011-04-11
Don't take the Battery Indicator seriously.Hardware makers never write drivers for Linux.

---

### Post by Tadcrazio on 2011-04-11
> **leclerc65 said:**
> Don't take the Battery Indicator seriously.Hardware makers never write drivers for Linux.

not for nothing, the battery doesn't hold a charge.

---

### Post by fuduntu on 2011-04-11
> **Tadcrazio said:**
> So my Ubuntu is telling me that my laptop battery may be old or broken it is only accepting a charge of up to 45.7%. Well I'd agree with Ubuntu on this one, but my question is does anyone think that geek squad will replace the battery seeing as I am still under warranty?

Try cycling it three times, and see if it goes back to normal.

Each time, boot the system and kill the gnome-power-manager process.  Disconnect the power cable and let the computer idle, or play video in a loop or whatever until it dies completely and shuts off.  Recharge the battery for 14 hours without using the computer (keep it powered off).  Repeat two more times.

---

### Post by disabledaccount on 2011-04-11
> **leclerc65 said:**
> Don't take the Battery Indicator seriously.Hardware makers never write drivers for Linux.This is not true. Almost every battery is using one of standard chips for battery load control - and linux have drivers for most of them. But this is true that charge indicator can show incorrect value - because charge isn't measured directly.
First of all Ubuntu is learnig of battery characteristics and needs at least 2-3 full charge/discharge cycles to compute correction factors with desirable accuracy.
This is superior method comparing to bullshits that are often shown in some proprietary solutions.
If Your battery will never reach nominal charged state voltage (readed from battery control chip) then computed charge will never reach 100% This can be due to both battery or chip malfunction. In both cases Battery should be replaced, as even if it's only damaged measuring circuit then it can lead to serious problems in future (such as damage of laptop's internal battery charger).
If the battery doesn't hold the charge, then check if it's getting warm when running on AC - if yes, then it is most probably damaged and indeed constantly charging.

---

### Post by t0p on 2011-04-11
> **tomazzi said:**
> This is not true.

When I was running Karmic on my netbook it warned me about the battery being "broken" every time I used it without using the AC adaptor.  Now I'm using Maverick the netbook's battery is fine.

Do you think the battery healed itself?  Or elves exchanged the broken battery for a good one?  Or maybe Karmic is a damn liar!

---

### Post by kostageas on 2011-04-11
Did you buy the *extended* warranty that lasts 2 whole years?  If so, they will replace your battery *once* for free.  If you have any other warranty instead, they will not.

---

### Post by disabledaccount on 2011-04-11
t0p: Nope - explanation is very simple - it couldn't read battery info, only the ACPI state.
But this can/could be fixed very easily by reading data directly from chip, overriding often buggy ACPI tables.
I would say that Your ACPI info was buggy and patch/workaround was released - but is also possible that there was some regression in ACPI driver.

edit: But it's not the case, because here battery info is available.

---

### Post by fuduntu on 2011-04-11
> **t0p said:**
> When I was running Karmic on my netbook it warned me about the battery being "broken" every time I used it without using the AC adaptor.  Now I'm using Maverick the netbook's battery is fine.

Do you think the battery healed itself?  Or elves exchanged the broken battery for a good one?  Or maybe Karmic is a damn liar!

What a wonderful bug that was.

[https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/403303](https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/403303)

---

### Post by disabledaccount on 2011-04-11
...so I was right :)
> The Eee pc's battery does not adhere to ACPI standards in reporting its  capacity, returning a percentage in a field which is specified as having  the unit mAh.
BIOS again - nothing new...

---

### Post by Tadcrazio on 2011-04-11
Thanks I will try the cycling.

And I got the warranty for 3 years, I didn't know how much of a fuss they would make if I wanted a new battery.

---

### Post by wolfen69 on 2011-04-12
But if they see that it has linux on it, they will probably try and weasel out of it saying that the warranty is only good if windows is on it. The Geek Squad can be very devious.

---

### Post by Tadcrazio on 2011-04-16
Ah true that wolfen, 

I cycled the battery and now its saying 29.5% battery life. yeesh

---

