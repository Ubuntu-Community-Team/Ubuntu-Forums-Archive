---
title: "Blaster Virus? Should I be concerned?"
date: 2011-05-21
forum: Security
---

### Post by usmcjgill on 2011-05-21
Now and then when I am browsing the web with Firefox I am redirected to a page from my modem/router saying that there could be a "Blaster Virus", or I just have a large amount of Internet connections or games running that suck up bandwidth. (I am using ubuntu 10.04). I have no torrents running, no games running, (not even on the network, such as xbox live) so I am concerned, mainly because I have run ubuntu for a couple of years now and never got this message. Any suggestions?

---

### Post by Mr. Shannon on 2011-05-21
I never trust anything that comes up in my browser about a virus.  If you want, you can install **clamtk** and scan your computer for viruses.

---

### Post by slooksterpsv on 2011-05-21
Do you run WINE, like running Windows apps in WINE?

Also, I would check your proxy settings on Firefox. Could you post a screenshot of when it happens?

---

### Post by Soul-Sing on 2011-05-21
> to a page from my modem/router saying that there could be a "Blaster Virus"

has this page an address/url?

---

### Post by CharlesA on 2011-05-21
> **leoquant said:**
> has this page an address/url?
This.

Post a screenshot if needed. I bet it's more then likely a pop up designed to scare you into buying something.

---

### Post by ChrisWells on 2011-05-22
Another trolling first post? If not, then you need to learn, that all these website show some fake windows box looking scan telling you you have viruses (which don't apply to Linux) and that you should remove them by downloading and installing their "virus remover" or some software to "speed up your mega slow connection" are all for luring clueless people in.  This is like decades old people should know this by now. Also, don't believe the e-mails you get saying you've won the lottery, or that some hot girl wants to meet you

---

### Post by manfromthezoo on 2011-06-01
Are you using the router that your ISP provided? You mentioned that the page seems to come from your router. If you're certain about that...

I've known certain cable providers in the past, in an attempt to stop infected / zombie machines phoning home to their respective botnets / using their backbone to propogate, to try and warn users if traffic from their network 'matches' patterns from known worms, etc. They'll do an occasional redirect to said warning page to try and alert the user. NTL in the UK used to do this.

Trouble is, I've often seen this go wrong and false positives occur - especially if you're running a *nix box and there's about as much chance of your machine being infected with Blaster as there is me ironing my socks. The other issue is that in a Windows monoculture, they don't factor in that not everybody is using MS software and so misleading reports can be presented to non-Windows users.

Are there any Windows boxes running on your home network? If not, then any warnings for MS malware are surely false positives, and you'll want to see what's generating the traffic that's getting the ISPs monitoring 'solution' into a tizzy.

A quick Google reveals that Blaster used (uses?) TCP ports 135, 3333, 4444, 666 - 765 and UDP 69. Might be worth checking with, say, a tool like Wireshark for enthusiastic activity from these ports to trace the source, and end the annoyance.

---

### Post by manfromthezoo on 2011-06-01
Ooh - you might want to also check you've got your wireless network tied down (if you're using one).

It's not beyond the realms of feasibility that if someone's using it with an infected Windows box - and let's be honest, the sort of person that would steal wi-fi is not the sort of person concerned with security - and that could be the source of your mystery port activity.

It's unlikely, for sure - but it never hurts to be certain. Perhaps check the DHCP lease info in your router. A lot of routers collect hostnames so you can ID machines on sight, but if yours doesn't just check the associated MAC addresses and make sure all belong to devices in your house.

Like I say - it's not likely (and hard to see without seeing it) but if you haven't got your wireless tied down* it's another possibility.

* If not, you should.

---

