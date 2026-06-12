---
title: "graphics card, screen, input device not detected"
date: 2012-04-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by EmilyRose on 2012-04-09
Hi there, I upgraded to 12.04 a couple of weeks ago and installed GNOME 3.3 and later upgraded to 3.4. Its been running fine since with a handful of constant errors and crashes mostly involving epiphany and/or evolution which I've ignored. I installed a bunch of updates a couple days ago at my inlaws and went off to dinner and left my laptop in suspend. I assume its battery died at some point and shutdown - when I plugged it in and turned it back on last night, it appears to boot normally but gives an error screen which reads: 

The system is running in low-graphics mode
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.

I click ok and get this:

What would you like to do?
Run in low graphics mode for just one session.
Reconfigure graphics
Troubleshoot the error
Exit to console login

a cancel and OK button. The first one will get me to a terminal login but the other to just end in lockups, as does cancel. 

Any suggestions? I'd rather not have to reinstall, but I'm wondering if thats my best solution at this point...

---

### Post by sffvba[e0rt on 2012-04-09
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*


404

---

### Post by Bucky Ball on 2012-04-09
Get to the terminal login, login and issue:

```
startx
```

Anything?

I have asked mods to move this to the 12.04 LTS forum (beta, testing, not yet released). ;)

---

### Post by EmilyRose on 2012-04-09
I managed to get back to the terminal and did apt-get update and upgrade and am able to log back in now. However my graphics card is 'unknown'. It *should* be an intel HD 3000 (i think), so now I'm trying to figure out how to get it installed...

---

### Post by Bucky Ball on 2012-04-09
Anything in 'Additional Drivers? I remember this card being problematic for another user. Have you used it successfully in any older releases?

---

### Post by EmilyRose on 2012-04-09
Nothing in aditional drivers, I *think* it was detected correctly in 11.10, though I'm not 100% on that.

---

### Post by Bucky Ball on 2012-04-09
You can check again with this command in a terminal:

```
sudo lspci
```

... and look for a line that starts something like this:

```
01:00.0 VGA compatible controller:
```

---

### Post by EmilyRose on 2012-04-09
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

is whats listed

---

### Post by tekrei on 2012-04-10
Same problem at my Ubuntu 12.04 too. I couldn't solve the problem. I tried to change xorg, tried failsafe, but gui is not showing up. My card is Intel HD.

---

### Post by techvish81 on 2012-04-12
> **tekrei said:**
> Same problem at my Ubuntu 12.04 too. I couldn't solve the problem. I tried to change xorg, tried failsafe, but gui is not showing up. My card is Intel HD.

same here, is there any way to get gui?

---

