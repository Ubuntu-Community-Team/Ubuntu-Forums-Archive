---
title: "Bind Question"
date: 2012-10-27
forum: Server Platforms
---

### Post by pegruder on 2012-10-27
So - I have bind setup and running on my network.  All seems to be ok except for a few things.  I added an A record for one of the servers on my lan.  I wanted to be able to access it in windows via the \\host.  However, it seems it only works via \\host.domain.com.  I think I get why as I have the zone file created, and that A record falls within the zone.  Is there a way to setup an alias of some sort to access the server via just the hostname?

---

### Post by Doug S on 2012-10-27
Yes, you should be able to make things work on your internal LAN with abbreviated names. I use bind as my internal DNS and am able to use computer_name instead of computer_name.smythies.com on windows client computers.
See this [thread]("http://ubuntuforums.org/showthread.php?t=2067993") for some recently posted information. However, in my case I am also running the DHCP server on the same computer as bind.

---

### Post by pegruder on 2012-10-27
> **Doug S said:**
> Yes, you should be able to make things work on your internal LAN with abbreviated names. I use bind as my internal DNS and am able to use computer_name instead of computer_name.smythies.com on windows client computers.
See this [thread]("http://ubuntuforums.org/showthread.php?t=2067993") for some recently posted information. However, in my case I am also running the DHCP server on the same computer as bind.

Good Deal!  I am running DHCP on the same server as well, added the search domain and voila - worked like a charm!

---

