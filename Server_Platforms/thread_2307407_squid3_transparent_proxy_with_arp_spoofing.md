---
title: "squid3 transparent proxy with arp spoofing"
date: 2015-12-24
forum: Server Platforms
---

### Post by willp2 on 2015-12-24
[COLOR=#141414][FONT=verdana]hi there, Im trying to get upsidedownternet working with arpspoofing, something along the lines of this:[/FONT][/COLOR]
[https://help.ubuntu.com/community/Upside-Down-TernetHowTo](https://help.ubuntu.com/community/Upside-Down-TernetHowTo)
[COLOR=#141414][FONT=verdana](but using arp spoofing instead of changing the targets gateway manually)[/FONT][/COLOR]

[COLOR=#141414][FONT=verdana]anyway, ive got it semi-working, as some/most images that load on the target device are indeed getting flipped. However, most pages that I go to on the target device do not load, and return 404 errors. [/FONT][/COLOR]
[COLOR=#141414][FONT=verdana]It turns out that this is because of weird GET requests being made: domain.com/[targetsIP]/--GETmyip=[myexternalIP]myport=80.[/FONT][/COLOR]
[COLOR=#141414][FONT=verdana]Unsurprisingly, most domains dont like that sort of request.[/FONT][/COLOR]

[COLOR=#141414][FONT=verdana]I know you dont have much to go on, but I followed the instructions in the link exactly, and the image-flipping script seems to be running ok, as does the arp spoofing (Ive done that before with no problems), so Im left thinking its something to do with squid3.[/FONT][/COLOR]

[COLOR=#141414][FONT=verdana]Any suggestions?[/FONT][/COLOR]
[COLOR=#141414][FONT=verdana]Thanks a lot[/FONT][/COLOR]
[COLOR=#141414][FONT=verdana]Will[/FONT][/COLOR]

---

### Post by matt_symes on 2015-12-25
Thread moved to **Server Platforms**

You may get a better answer to your query in this forum.

---

