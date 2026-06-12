---
title: "Meizu MX4 no cellular connection"
date: 2015-08-16
forum: Ubuntu Phone and Tablet
---

### Post by Kiriakos_Krastilli on 2015-08-16
Hello there,

I just got my hands on the ubuntu mx4. Unfotunately the phone cant find a cell signal anywhere. Is this a known problem? I'm on german vodafone. Is there a fix?


Thanks for any infos,
Kiriakos

---

### Post by howefield on 2015-08-16
Not that it should make any difference, but have you checked for updates.

---

### Post by Kiriakos_Krastilli on 2015-08-18
Yes, thats the first thing I did. Unfortunately I am up to date....

Is there any way I can debug this? BTW, is there any documentation on how to do cling debugging on Ubuntu Touch?

---

### Post by dumazdamaz on 2015-08-18
I once had the phone drop the phone network and it additionally seemed to indicate in the upper status bar and networking settings page that it was connected to the phone carrier network. However, when attempting to send a message or place a call it would refuse and say that there is no SIM. This survived numerous reboots, but went away after I toggle 4g on and off. I have no idea why this would happen or whether you have the same problem. However, it will to little harm to try this.

you couls also look at the logs, but I have no idea which ones would be pertinent to this issue at hand, perhaps telephony-service-indicator.log?

---

### Post by Kiriakos_Krastilli on 2015-08-19
So, I Went to /var/log but there is no telephony-XXXXX.log...

when end going to the cellular settings and selecting 2g and then going into the carrier selection I get Vodafone as the only detected network but when I try to select it it just jumps back to having automatic selected...

---

### Post by jos-vh67 on 2015-08-19
I had a similar problem when traveling from Sweden to Danmark. When I arrived in Danmark the phone did not connect to a carrier. I also tried switching back and forward between "automatic" and trying to select an carrier manually, but with the same result as above. I think a restart of the phone did the trick. (I own a BQ E3.5 by the way, so I assume it's Ubuntu related and not specifically Meizu or the MX4).

---

### Post by dumazdamaz on 2015-08-20
> **Kiriakos_Krastilli said:**
> So, I Went to /var/log but there is no telephony-XXXXX.log...

when end going to the cellular settings and selecting 2g and then going into the carrier selection I get Vodafone as the only detected network but when I try to select it it just jumps back to having automatic selected...

The logs are in /home/phablet/.cache/upstart

---

### Post by Kiriakos_Krastilli on 2015-08-24
Was user error, the microsim used had been disabled by the operator.....

Sorry for wasting your time...

---

