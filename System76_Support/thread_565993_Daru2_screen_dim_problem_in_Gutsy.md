---
title: "Daru2 screen dim problem in Gutsy"
date: 2007-10-02
forum: System76 Support
---

### Post by sonmez on 2007-10-02
Hello,

I just got my Daru2 laptop and decided to install Gutsy. I notice that the screen dims sporadically. It doesn't matter weather it is plugged in or not. I also noticed that as soon as the screen dims the Gnome power manager icon disappears. It sometimes returns to normal and again when in does the power manager icon comes back. 

I wonder if anyone else experiencing the same problem and whether I should feel out a bug report.

Thanks

Sonmez

---

### Post by tedrampart on 2007-10-03
the dim thing is a new feature in gutsy.. you can turn it off in the power management settings... probably buggy still which would cause the icon to disappear..

---

### Post by theologian aaron on 2007-10-03
I have the same problem with my daru2.  If that is a new feature in Gutsy, it certainly is an annoying one.

---

### Post by sonmez on 2007-10-03
Dear[COLOR=Black] [COLOR=Gray]theologian aaron[/COLOR][/COLOR] 					 I just filed a bug at 
[https://bugs.launchpad.net/system76/+bug/148533](https://bugs.launchpad.net/system76/+bug/148533)

Could you add your comments too. Hopefully it will be fixed soon. 

Thanks

---

### Post by thomasaaron on 2007-10-03
That's probably not a bug we are going to be able to fix via a System 76 bug report. It is a buggy feature with Gutsy, and the report should probably be filed against Gutsy.

Sounds like the best workaround is to turn it off using the power management settings.

---

### Post by sonmez on 2007-10-03
Thanks for the quick reply Tom
I reported it as a new bug for Ubuntu
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/148575](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/148575)

---

### Post by theologian aaron on 2007-10-03
It's not something that can be turned off.  I have the dim screen option removed, and it continues to randomly dim and brighten the screen, whether on battery or plug.

---

### Post by thomasaaron on 2007-10-03
Shoot.

OK, I'll test that when we start Gutsy testing on the Daru2. Until then, though, I'll probably not be able to get to it.

Best,
Tom

---

### Post by reh4c on 2007-10-03
Hello.  I also want to install Gutsy on my Daru2.  Hopefully, this screen dimming problem and also the associate hardware keys will be fixed for final Gutsy.  Will System76 have a 64bit version of Gutsy developed for download with the associated .deb driver file as well?  I want to make full use of that 64bit power.  Thanks.

---

### Post by thomasaaron on 2007-10-03
No, we will not have a 64 bit version. We only support 32 bit Ubuntu.

---

### Post by thomasaaron on 2007-10-03
It just dawned on me that the screen dimming problem is probably related to the erratic behavior of the battery indicator under Feisty.

Under Feisty, this problem was fixed by the System 76 driver. I'm sure it will be fixed by the driver under Feisty too. But that's not going to be released until October 18th.

---

### Post by TheBuzzSaw on 2007-10-05
Yeah, my daru2 runs into the same problem. I just disabled the power management settings.

---

### Post by thomasaaron on 2007-10-05
Did disabling the power management settings fix it?

---

### Post by theologian aaron on 2007-10-05
No.  I can't seem to do anything to fix it.  I'm fairly certain it is related to the battery issue, but it's not easy to get rid of.

---

### Post by thomasaaron on 2007-10-05
OK. Well, we start Gutsy testing Monday. I'll do the Daru2 first.

---

### Post by TheBuzzSaw on 2007-10-05
> **thomasaaron said:**
> Did disabling the power management settings fix it?
I guessed I use ambiguous terminology. What I really did was change both the AC power settings and battery settings to have 0% dim. That way, no matter how much it fluctuated between being "on AC power" and "on battery power", the dim setting would remain constant (in my case, at full brightness).

---

### Post by thomasaaron on 2007-10-05
Ah! That makes good sense. Nice workaround. 
Still, I'm pretty sure the System 76 driver already has the fix for this one.

Thanks.

---

