---
title: "turning a router into a network bridge?"
date: 2008-05-25
forum: The Cafe
---

### Post by il-luzhin on 2008-05-25
I've got linksys WRTSL54GS taking up closet space.  If I could use it to pick up my 2-WIRE's signal and drop it into my DVR and X-box I'd get rid of a really annoying 60 foot cable on my kitchen floor.

Google hasn't given me any sites that seem particularly trustworthy.

Thanks folks

---

### Post by diablo75 on 2008-05-25
Your router will need to support bridge mode if you want to use it for this purpose.  If it doesn't support bridging, then you're only other option may be hacking the firmware...

---

### Post by mips on 2008-05-26
Under the Advanced Routing tab you can try and set the mode to Router but I suspect that this will only apply to the actual WAN port and not the WLAN port.


The best option I could recommend is to look into something like DD-WRT, [http://www.dd-wrt.com/dd-wrtv3/index.php](http://www.dd-wrt.com/dd-wrtv3/index.php) , as I know they support "client mode" for the wireless interface which will allow you to do what you want.

Other 3rd party firmware versions are [http://en.wikipedia.org/wiki/Linksys_WRT54G_series#Third-party_firmware_projects](http://en.wikipedia.org/wiki/Linksys_WRT54G_series#Third-party_firmware_projects)
Just follow the links and read up a bit on them as they could potentially offer you the same.
[http://www.linksysinfo.co.uk/thibor/](http://www.linksysinfo.co.uk/thibor/)

[http://www.linksysinfo.org/forums/showthread.php?t=47282](http://www.linksysinfo.org/forums/showthread.php?t=47282) The table on this page tells you which ones support Client mode WPA and Client Bridged Mode

[http://www.linksysinfo.org/forums/showthread.php?t=47124](http://www.linksysinfo.org/forums/showthread.php?t=47124) Shows the different hardware versions. If you have a Version5 and above you will NOT be able to use 3rd party firmware on it.

[http://www.linksysinfo.org/index.php](http://www.linksysinfo.org/index.php) is a good overall resource.

---

