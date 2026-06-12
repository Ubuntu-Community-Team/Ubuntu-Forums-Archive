---
title: "panv3: iwl3945 stops responding after resume from suspend"
date: 2009-11-03
forum: System76 Support
---

### Post by drewbenn on 2009-11-03
I upgraded to 9.10 from 9.04 (64-bit) on my panv3 earlier this week.  Sometimes when resuming from suspend, my network connection isn't coming back.  I tried googling one of the phrases from the dmesg log (MAC is in deep sleep!) and found an issue from maybe a year ago, but nothing recent.  I tried 'sudo /etc/init.d/networking stop' and 'sudo /etc/init.d/networking start' but the 'start' just returns the message "networking stop/waiting."  I also tried 'sudo rmmod iwl3945 && sudo modprobe iwl3945' from a suggestion in one of those google results, but that didn't help, either.  I created a logs file with the System 76 driver immediately after this happened the second time, and I'll attach that.

Is anyone else (any Pangolin 3 owners?) seeing a problem like this, or have any ideas?  It's happened 3 times in just the 2 days since I upgraded and the only solution I've found so far is to reboot, so even a clumsy workaround would be nice at this point.

---

### Post by thomasaaron on 2009-11-04
So it's intermittent?

Does it ever happen after a *first* suspend and resume, or does it only happen after multiple suspends/resumes?

---

### Post by drewbenn on 2009-11-04
Yes, it is intermittent.
It has not happened after the first suspend/resume cycle, only after "a few."  I'd guess that I probably get somewhere in the 5-10 range of successful suspend/resumes before networking stops working.  I had to reboot again this morning to fix it, so I'll try counting my suspend/resume cycles today.
Edit: Problem occurred after my second resume from suspend today.

---

### Post by thomasaaron on 2009-11-05
Seeing as how it is intermittent and suspend/resume related, it's probably not something we can quickly fix via the forums. It's probably best to post a bug report on it.

launchpad.net/system76

---

### Post by drewbenn on 2009-11-06
Thanks, Thomas.  I filed it as [https://bugs.launchpad.net/system76/+bug/476198](https://bugs.launchpad.net/system76/+bug/476198) .
I'm curious: I'm well out of the support period, was it okay that I posted here and filed the bug?  If this turns out to be isolated to just me (like a hardware issue) I realize I'll be on my own, but is this the sort of thing that you guys will try to replicate in the shop, to see if it's just me or a wider issue?  I realize of course that with everything else going on right now this is at the bottom of your list, and if you do look into it it might be a few weeks before you have time for it! :)

---

### Post by thomasaaron on 2009-11-06
hi, drewbenn.

Suspend has come a VERY long way in Ubuntu. Most of the problems we see are related to consecutive suspend/resume cycles. Since they are hard to replicate, and there are already efforts going on to make power management ever-better in Ubuntu, I imagine it will sort of fix itself in time.

It's fine that you posted there. We don't turn people away from technical support just because their warranty period is over. The warranty period is *primarily* for hardware.

It's kind of lower priority right now, as we're still digging out from the Karmic upgrade issues. But we'll have a look at it as time permits.

In the meantime, you might want to manually configure the iwl3945 module to be removed on suspend and re-inserted on resume. I would do it like this...

sudo nano /etc/pm/sleep.d/11_iwl3945

Then enter this text...

#!/bin/sh

case "$1" in
    hibernate|suspend)
        rmmod iwl3945
        sleep 0
        ;;
    thaw|resume)
        modprobe iwl3945
        ;;
    *) exit $NA
        ;;
esac

Then click Ctrl-X, Y, and Enter.

Then reboot. Then start re-testing. Let me know if it works, and we'll try to get it into the driver.

---

### Post by drewbenn on 2009-11-09
Thanks for the reassurance on support. It's great to have this kind of support!

Suspend was so rock-solid in Jaunty that I guess I just got used to it :)

I tried that file: after 11 suspend/resume cycles I lost wireless again.  That's kind of the upper limit of suspend/resumes I was seeing in the past, so _maybe_ it helped a little.  I'll keep using it and see how things work, but I don't think it's a complete fix.  I didn't have time to do any testing after that, although I've suspended and resumed successfully 3 times since then.

I did boot into a Jaunty LiveUSB, and made 20 successful suspend/resume cycles: so I don't think it is a hardware issue, which is great for me but maybe not so great for other panv3 owners ;)

It may be a week or two before I can follow-up here again; I'll keep testing though and report back when I can.  I'll also keep an eye on the system updates that come in, with an eye to seeing if any of those fix this issue.

---

