---
title: "Fresh lucid Install: SNMP Scan?"
date: 2010-04-30
forum: Security
---

### Post by Anapologetos on 2010-04-30
I just installed amd64 LL Desktop on my Hyper-V server.  Within 5 minutes of connecting it to my local network, I got an alert from my APC UPS that it had detected an unauthorized IP attempting to access the SNMP interface. Come to find out, the IP was my new Ubuntu install.

All I had done in those 5 minutes was to do an apt-get update & upgrade.

Any ideas on this weird behavior?

Thanks!

-Anapologetos

---

### Post by bodhi.zazen on 2010-04-30
Hard to tell from what little information you provided.

Can you tell us anything more ?

run tcpdump or wireshark and tell us more about what type of traffic you are seeing.

---

### Post by Anapologetos on 2010-04-30
Will do a little bit more digging and post it when I get the time.

-Josh

---

### Post by The Cog on 2010-04-30
Is it Karmic that you were running? I had a run-in with our security fellas about that - they got authentication failures from every switch and router in the building when I ran up the Karmic live CD. They tracked the source back to the floor port I was plugged into, and they weren't happy.

The cause is that it broadcasts an SNMP GET request to every device on the local LAN asking for the device type, using a password of "public". I gather it's the print spooler looking for printers. Muppets!

I think that particular stupidity has been removed from Lucid. I checked one of the betas anyway - haven't checked the release version though.

---

