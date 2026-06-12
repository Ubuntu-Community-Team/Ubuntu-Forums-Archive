---
title: "Virtual Terminals broken?"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sgage on 2012-04-14
When I press ctl-alt-Fn I get a black screen instead of a login for a virtual terminal. The monitor says "no signal" after a few seconds. A restart is necessary at this point - ctl-alt-sysrq-b usually works.

Anyone else seeing this? Is there a known fix or workaround?

---

### Post by ventrical on 2012-04-14
My Dell Opti is working just great  in Unity 2D. No delays, lickity-split switching.!

---

### Post by sgage on 2012-04-14
> **ventrical said:**
> My Dell Opti is working just great  in Unity 2D. No delays, lickity-split switching.!

That's the one thing I didn't test. I checked Gnome Shell, Gnome Classic, and Unity 3D, and they all failed.

Nvidia GeForce 8500 GT - neither the proprietary drivers or nouveau gives me VT's.

---

### Post by keithpeter on 2012-04-14
> **sgage said:**
> That's the one thing I didn't test. I checked Gnome Shell, Gnome Classic, and Unity 3D, and they all failed.

Nvidia GeForce 8500 GT - neither the proprietary drivers or nouveau gives me VT's.

Hello sgage and all

Recycled Xeon with nvidia GT520/proprietary drivers, unity 5.10.0-0ubuntu3 and compiz 0.9.7.6-0ubuntu1

Ctrl-Alt F1 gives a tty
Ctrl-Alt F7 gets me back to X desktop

Cheers

---

### Post by mc4man on 2012-04-14
I only see with a 8400m on a 32 bit install with any nvidia driver over 290.10 & only after a min of 3 restart or shutdown cycles. So not the same as you other than the possibilty of no VT's exists.
(doesn't happen on my 64 bit install

---

### Post by NHclimber on 2012-04-14
> **sgage said:**
> When I press ctl-alt-Fn I get a black screen instead of a login for a virtual terminal. The monitor says "no signal" after a few seconds. A restart is necessary at this point - ctl-alt-sysrq-b usually works.

Anyone else seeing this? Is there a known fix or workaround?

I got this with 3.2.0-22-generic and nvidia-current 295.33 but it wasn't consistent. I could switch VTs after just getting the session running but after some time when I would switch to the VT it would never come up (like you said the monitors would just DPMS off). I could switch back to VT7 though.

Isn't happening with nouveau now though.  I specifically haven't upgraded to 3.2.0-23 yet because I think this VT switching is responsible for 2 hard lockups I got earlier this week and I'd really like to catch the kernel panic if I can.

Can you switch to tty1 from the login greeter?

---

### Post by sgage on 2012-04-14
> **keithpeter said:**
> Hello sgage and all

Recycled Xeon with nvidia GT520/proprietary drivers, unity 5.10.0-0ubuntu3 and compiz 0.9.7.6-0ubuntu1

Ctrl-Alt F1 gives a tty
Ctrl-Alt F7 gets me back to X desktop

Cheers

Ctrl-Alt F1 gives me "no signal" to my monitor.

But Ctrl-Alt F7 does bring back the X desktop.

This is so with any session of Gnome or Unity. Completely updated system.

---

### Post by sgage on 2012-04-14
> **NHclimber said:**
> I got this with 3.2.0-22-generic and nvidia-current 295.33 but it wasn't consistent. I could switch VTs after just getting the session running but after some time when I would switch to the VT it would never come up (like you said the monitors would just DPMS off). I could switch back to VT7 though.

Isn't happening with nouveau now though.  I specifically haven't upgraded to 3.2.0-23 yet because I think this VT switching is responsible for 2 hard lockups I got earlier this week and I'd really like to catch the kernel panic if I can.

Can you switch to tty1 from the login greeter?

No, same thing from the login greeter, or any session, even immediately after login. But I can switch back to VT7/X at least.

Strange business.

---

### Post by NHclimber on 2012-04-14
> **sgage said:**
> No, same thing from the login greeter, or any session, even immediately after login. But I can switch back to VT7/X at least.

Strange business.

With the nouveau driver, can you run this experiment?
1. 'sudo dmesg -n 8'
1. 'tail -f /var/log/syslog' from a terminal in X.
2. try to switch to another VT.
3. wait 30 secs.
4. switch back to VT7.
5. Post any added output here

Note: dmesg -n 8 ups the console loglevel so kernel debug messages are printed to the console.

---

### Post by sgage on 2012-04-14
> **NHclimber said:**
> With the nouveau driver, can you run this experiment?
1. 'sudo dmesg -n 8'
1. 'tail -f /var/log/syslog' from a terminal in X.
2. try to switch to another VT.
3. wait 30 secs.
4. switch back to VT7.
5. Post any added output here

Note: dmesg -n 8 ups the console loglevel so kernel debug messages are printed to the console.

Step 1 (the first step 1 :KS ) gives:

dmesg: unknown level '8'

But perhaps it's moot, because VT's now seem to be working reliably when using nouveau. This is with Gnome Shell now - I don't have the time right now to test every permutation of shell and driver. VT's still not working with the proprietary drivers. 

Some people have reported that it will work for a while and then stop working, so I will run with nouveau for a while and see what I can see...

---

### Post by mc4man on 2012-04-14
If level 8 was to be debug then you'd use debug instead of 8

---

### Post by sgage on 2012-04-15
Well, it appears as though the problem I'm having with VT's is related to the proprietary nvidia drivers after all. Since I reverted back to the nouveau drivers, everything has been working fine. Hopefully they'll get the nvidia drivers fixed soon...

---

