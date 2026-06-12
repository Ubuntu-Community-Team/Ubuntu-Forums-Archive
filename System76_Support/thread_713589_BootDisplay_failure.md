---
title: "Boot/Display failure"
date: 2008-03-02
forum: System76 Support
---

### Post by Bllz on 2008-03-02
I just got my new serval yesterday.  It's one of the new upgraded ones--WSXGA+ display and some kind of new intel thermal chip... I don't know the details


It was working fine (dual boot Ubuntu/Vista) until today.  Now when I boot, i hear the fan burst on/off (it always did this), the cd bay will spin up if a CD is in it and I see the HDD indicator light jump on a few times.  Appart from that, nothing.  The display doesn't light up, not even for the BIOS menu.

What gives?  Is this a boot issue or a display issue?

Before it happened, I was looking at some of the BIOS settings, but I didn't change anything.  I also tried to start it with an external HDD plugged in, but I tried again without it and nothing changed.

Thanks in advance

---

### Post by Bllz on 2008-03-02
Update:  I plugged another display into the VGA port, but nothing showed up.

My guess is it's just not booting?  Should I reset the CMOS?  If so, where is it?

---

### Post by thomasaaron on 2008-03-03
Email me at support(at)system76.com for instructions on resetting cmos.

---

### Post by Bllz on 2008-03-03
I've reset the CMOS and tested each individual memory card/bay, but I'm still getting a blank screen -- I don't even see the manufacturer's splash screen.

Has anybody ever experienced this before?

Thanks

---

### Post by thomasaaron on 2008-03-03
Very rarely. Chances are it is a bad hardware problem. I'm putting together an RMA and we'll turn this around quickly. Standby...

---

### Post by Kevanx on 2008-04-11
Drat. My first major issue with my month-old Serval.
I think I have this same problem. A few weeks ago I was messing around in xorg.conf, but not doing anything major (still quite a rookie). I was looking for a fix to go from metacity --replace to compiz --replace (or something similar) because going back to compiz would give me windows with no title bars and no ability to resize the windows. Eventually X would freeze. I never found a solution, but that's not the issue.

In the process, or shortly thereafter, I rebooted, and upon booting, my bios screen was replaced by thin, vertical lines on a white background, and more lines would sort of "fade in" until the screen was mostly full. Having no bios makes me kind of panicky. Then a black login screen ( the regular sounds worked, and I could log in properly) but no screen. It fixed itself, but now the problem has returned without resolution.

1) Rebooting doesn't help, nor does ctrl-alt-backspace, either before or after logging in.
2) I have not seen anything after the BIOS splash screen, which is usually just a rainbow.
3) The noises prompt me when to log in, and it seems to login fine, minus the black screen.
4) If I press F12 during the "rainbow" screen, it sits on the rainbow screen, as though it has gone to the BIOS menu.
5) Serval Performance (no idea about model, but I bought it at the end of Feb 2008 ). The sticker on the bottom says FL90. Running Ubuntu Gutsy 64-bit.

HELP!
[I]
-- update: 20 minutes off fixed it, but I would still like to resolve this problem, because it seems pretty major.[/I]

---

### Post by thomasaaron on 2008-04-11
Let's take this one to support email, OK.

First, we need to try to run memtest86. See if you can get into the grub menu (press esc when you see grub...3...2..1....). Does that show any errors?

Then, we may need to reset the cmos.

Please email me your results at support(at)system76(dot)com. Also let me know your order number (or the name under which the computer was purchased) in the email.

---

