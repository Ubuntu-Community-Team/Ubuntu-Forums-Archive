---
title: "Wireless has disappeared"
date: 2012-01-14
forum: System76 Support
---

### Post by smarmytime on 2012-01-14
Over the past few months, my wireless has been working flawlessly, thanks to a new wireless router in my home (using the FIOS router that verizon gave me had me having to reset every 5-10 minutes, if not more). But all of a sudden, it's died, completely. Will not connect at all - won't even see any wireless networks. While I was at school last night, I plugged in an ethernet cable, but I've done that dozens of times, and was able to go right back to using wireless afterwards. But from that point on, the wireless has not worked.

I'm using a PanP7, with ubuntu 11.10. Pressing Fn F11 does nothing. If I click the wireless icon, Enable Networking is checked.

One odd note...whenever I'd check ifconfig before, it would show eth0, lo, and wlan0. wlan0 has disappeared from that. It also doesn't show up under iwconfig - the only thing that shows up is lo and eth0, both saying no wireless extensions.

I'm finding this rather baffling...any ideas?

---

### Post by jml on 2012-01-14
Not having wlan0 listed on ifconfig suggests that it may be a hardware problem.  Has your PanP7 been dropped or in any way jarred recently?  I'm thinking may be the wireless card got unseated.  Was there any recent updates to Ubuntu between the time the card was working and now? 

One other suggestion would be to redownload and then install the System 76 drivers.  Good luck.  Hopefully, Ian will weigh in on this one.

Joe

---

### Post by smarmytime on 2012-01-15
> **jml said:**
> Not having wlan0 listed on ifconfig suggests that it may be a hardware problem.  Has your PanP7 been dropped or in any way jarred recently?  I'm thinking may be the wireless card got unseated.  Was there any recent updates to Ubuntu between the time the card was working and now? 

One other suggestion would be to redownload and then install the System 76 drivers.  Good luck.  Hopefully, Ian will weigh in on this one.

Joe

Not at all...literally, it worked, then I plugged in that ethernet cable that I mentioned before, and used the internet like that for a couple of hours, and then I unplugged it, and wireless didn't work anymore. And I believe the wireless card is integrated on the PanP7, so...yeah. Still baffled.

I will try to reinstall the drivers...thanks for the suggestion.

---

### Post by isantop on 2012-01-16
Have you tried rebooting yet? If this solves the problem, can you get it to occur again? 

Also, which wireless card do you have installed? The default option or one of the upgraded Intel options?

---

### Post by smarmytime on 2012-01-16
> **isantop said:**
> Have you tried rebooting yet? If this solves the problem, can you get it to occur again? 

Also, which wireless card do you have installed? The default option or one of the upgraded Intel options?

Hi Ian, and yes, first I tried logging out/back in, and then I tried rebooting, and neither worked. And I do have the default card...kind of kicking myself for not spending the extra $20 clams.

---

### Post by isantop on 2012-01-17
Was it a fresh installation of 11.10, or did you upgrade from 11.04?

---

### Post by smarmytime on 2012-01-18
Sigh...ok, my wireless is back, just as mysteriously as it disappeared. It came back the moment I plugged it into the ethernet at school...same as when it disappeared. It'll be interesting to see what happens when I go to school this friday.

---

