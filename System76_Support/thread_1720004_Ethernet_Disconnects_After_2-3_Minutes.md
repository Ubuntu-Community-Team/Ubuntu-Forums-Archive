---
title: "Ethernet Disconnects After 2-3 Minutes"
date: 2011-04-02
forum: System76 Support
---

### Post by M.R.D. on 2011-04-02
Hey, just got my Gazelle Pro today and am very happy with it.

However, I used it for about 3-4 hours, then all of a sudden it disconnected from the ethernet connection.

After rebooting, it reconnects for about 2-3 minutes and then loses connection again.

When this happens, and I try to reboot, the computer locks up on shut down and has to be restarted manually by holding the power button.

Not entirely sure what could be going wrong as I've only installed a handful of programs since getting the computer (Pidgin, AWN, emacs and Guake). I did email this to support but figured I would ask here in case anyone else had encountered and solved anything similar.

Thanks!

---

### Post by M.R.D. on 2011-04-02
Well, the problem has not yet replicated itself on my home connection. Maybe just a shoddy install at work or an IP conflict.

Not sure why that'd cause the shut down issue, though.

---

### Post by isantop on 2011-04-04
I'd keep an eye on it. Let us know if it happens again.

I think you may have sent in an email too. We can handle your case either there or here, your choice.

---

### Post by M.R.D. on 2011-04-04
> **isantop said:**
> I'd keep an eye on it. Let us know if it happens again.
Howdy, hasn't happened again, yet... I'm guessing it was just some weird IP conflict that I won't be able to test again until I head to work on Wednesday.

Great laptop, though! I never realized how dated my home desktop computer was! :D

---

### Post by isantop on 2011-04-04
Yeah, we're pretty proud of our new professional machines. I'm glad you like it!

---

### Post by thomasaaron on 2011-04-15
If it occurs again, please try this fix...

Turn you computer off. Hook up Ethernet and AC power. Boot Up. You should have Ethernet now.

1. Click the link below and save. The package should go to your Downloads folder...

[http://mirror.pnl.gov/ubuntu//pool/main/p/pm-utils/pm-utils_1.3.0-1ubuntu1_all.deb](http://mirror.pnl.gov/ubuntu//pool/main/p/pm-utils/pm-utils_1.3.0-1ubuntu1_all.deb)

2. Now open a terminal and run these commands, pressing Enter after each one...

cd Downloads

sudo dpkg -i pm-utils_1.3.0-1ubuntu1_all.deb 
# NOTE: after typing the "pm" you can just hit tab and auto-complete the rest of the filename

You'll be prompted for your password. You won't see it typing, but the terminal is accepting it. Hit enter after typing it.

Once the terminal returns you to a command prompt, you're finished. Reboot your computer.

At this point, the Ethernet should be working fine, and the freezing should be solved.

---

