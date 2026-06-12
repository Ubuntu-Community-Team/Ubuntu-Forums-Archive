---
title: "unsuccessful first upgrade - going from 8.10 to 9.04."
date: 2010-04-28
forum: System76 Support
---

### Post by elphaba on 2010-04-28
Received an error message about lilo.conf but upgrade continued
Final message was that my upgrade was unsuccessful and that system may not be useable (or something like that).
But when I go into "Upgrade" under system and see what is indicated, it gives me the option to upgrade to 9.10. I don't want to do this until I know my 9.04 upgrade was successful.  Any tips?

I haven't rebooted because I'm afraid if I reboot, my system will be inoperable.  Have looked thru log files, at least what is in "view log files" under System menu.  Can't find where there is a log of the upgrade. Would be nice to see. Can anyone tell me where this might be?

I found on the web where someone gave a tip that you could go back to your previous upgrade by entering:
   dpkg-reconfigure -phigh -a

Can anyone confirm this for me? I don't want to make matters worse.

Or is there a way to fix "lilo"?  I'm not sure how it is broken or how it impacts my operations directly but I'm afraid to find out after I reboot that I should have fixed something in lilo.conf before rebooting.

I'm posting this here because I'm wondering if there is anything special about system76 and lilo or system76 and upgrading.

p.s. system is 64bit

---

### Post by Eldera on 2010-04-28
LILO was an old bootloader that was replaced by Grub Legacy. The 8.10 update still offered both LILO and GRUB and the thing to do was to ignore or get rid of LILO. 

Here is an old thread with more information:

[http://ubuntuforums.org/showthread.php?t=1134187](http://ubuntuforums.org/showthread.php?t=1134187)

Good luck getting things sorted out.
Eldera

PS I did a series of clean installs so can't answer your question about going back to previous upgrade. Maybe someone else will post about that.

---

### Post by elphaba on 2010-04-28
Thanks very much Eldera -- per the link you provided, I rebooted and verified that "grub" was operational and working - then I went to Synaptic and "completely uninstalled" "lilo".  Everything is great now.  
 That was rather traumatic, being my first upgrade. I wish they had a sticky somewhere with "common" upgrade problems.  I looked but didn't see one.  This seemed VERY common. oh well...

---

### Post by Eldera on 2010-04-28
[quote=elphaba]Everything is great now.[/quote]

Hooray!!! Now we both can have a great day.

---

### Post by thomasaaron on 2010-04-28
I love how you guys jump in and help the community. Thanks, Eldera (and gamerchick, and hotshotdj, and samalex... and all the rest...).

---

