---
title: "SIP errors - UDP Fragmentation??"
date: 2013-03-29
forum: Server Platforms
---

### Post by kevpatts on 2013-03-29
I'm running behind router Firmware: DD-WRT v24-sp2 (10/10/09) voip on a Linksys WRT-54G Version 2.

I'm running an asterisk pbx (Ubuntu Server 12.10) behind this router and I have ports 5000-31000 forwarded to the asterisk server. The asterisk server has a software firewall that only accepts traffic from our SIP providers IP range.

Okay, so until yesterday this worked perfectly, but then suddenly we noticed that a lot of calls were going straight to the Asterisk voicemail instead of ringing the phones.

I set up wireshark on the pbx and compared the good calls to the failed ones and noticed that the failed ones just show a lot of UDP packets from the SIP provider to high port numbers on the box, some of which were not even numeric (12502, 25741, "msgclnt", etc.) whereas the successful calls start with a SIP/SDP request to us from the SIP provider on port 5060.

The strange thing is that the failed calls do go to voicemail which is hosted on the pbx inside our network. Rebooting the router/pbx seems to temporarily fix the issue.

The only change on the pbx bow was that 2 days ago I installed tftp-hpa listening on port 69 to the LAN only.

Any ideas?

---

### Post by jonobr on 2013-04-02
Any luck with this?

---

### Post by kevpatts on 2013-04-02
> **jonobr said:**
> Any luck with this?

Hey man, I've upgraded the firmware to build 14929 I think it is on the router. Going to monitor it now to see if there's progress.

---

### Post by kevpatts on 2013-04-03
> **kevpatts said:**
> Hey man, I've upgraded the firmware to build 14929 I think it is on the router. Going to monitor it now to see if there's progress.

Nothing to do with this in the end. An old virtualised asterisk server had unexpectedly restarted and it's previously disabled asterisk server had come up, causing two servers to compete for calls.

resolved now, deleted asterisk packages from the old install.

---

### Post by jonobr on 2013-04-03
Excellent, I did nothing, but I feel somehow instrumental in the fix.
Is that wrong of me:-)

---

### Post by kevpatts on 2013-04-03
> **jonobr said:**
> Excellent, I did nothing, but I feel somehow instrumental in the fix.
Is that wrong of me:-)

You did more that the folks over at the dd-wrt forums, who just gave out to me for not reading the million pages of sticks that I didn't understand before posting! **** heads!

---

### Post by matt_symes on 2013-04-03
> **jonobr said:**
> Excellent, I did nothing, but I feel somehow instrumental in the fix.
Is that wrong of me:-)

If that's the case then i was also instrumental in the fix. :D

---

### Post by kevpatts on 2013-04-03
Even more so Matt! Thanks for all your tolerance. You guys are great!

---

