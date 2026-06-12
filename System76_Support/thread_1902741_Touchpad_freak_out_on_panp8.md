---
title: "Touchpad freak out on panp8"
date: 2011-12-31
forum: System76 Support
---

### Post by firstclown on 2011-12-31
I have a panp8 and I've just had the touchpad completely freak out on me, jittering severely left and right. I was able to wrestle it enough to get the computer restarted, but it didn't go away after starting back up. I plugged in a mouse and got the touchpad disabled with:

```
xinput set-prop 12 "Device Enabled" 0
```

Turning it back on causes the same problems again, so I'm leaving it off for now. Any ideas on what could cause this? Haven't done any big software installs today. Any way to fix it?

---

### Post by firstclown on 2012-01-02
And now everything's working fine again.

Still, any reports of this or what causes it?

---

### Post by isantop on 2012-01-03
Which version of Ubuntu are you running? We know that the touchpad support needed to be patched in 11.04, and 11.10 has much better touchpad support out of the box.

---

### Post by firstclown on 2012-01-03
I'm running 11.10 (can't seem to change it on my profile to the right.)

I haven't had the problem since the initial post.

---

### Post by isantop on 2012-01-04
I'd keep an eye on it and see if it does it again. If it does, try cycling the touchpad with Fn+F1, then post your results here.

---

