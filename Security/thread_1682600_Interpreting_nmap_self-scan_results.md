---
title: "Interpreting nmap self-scan results"
date: 2011-02-06
forum: Security
---

### Post by khughitt on 2011-02-06
Hi all,

I've been experimenting with nmap lately to get a better understanding of the services running on my machine, and have a couple questions.

When I do a local scan of my own machine (e.g. "nmap <my ip addr>"), I see some ports which I expect to be open, and some others that I did not expect.

For instance, port 8080 appears to be open even though I'm not running a proxy server. Further, although I am running a local instance of Apache, it shows up as "open" even if I stop the service. Nothing shows up on the ports with either "lsof -i :8080" or "netstat -a".

Are the open ports I'm seeing actually from my router? When I run nmap locally, I would not have to go "outside" the router.

My understanding of networking concepts is pretty incomplete, so It is probably just a misunderstanding of how nmap is working.

Any insight would be greatly appreciated :)

Thanks!

---

### Post by MorleyPotter on 2011-02-06
my thoughts are that to run Nmap on your router you would need to change [your_ip] to the routers ip.
 
As for the port 8080, my understanding is that it is used as a port 80 alternative and nothing to worry about, google may be able to give you a listing of common ports perhaps?

---

### Post by CharlesA on 2011-02-06
If you run nmap on 'localhost' you'll run into "false positives" that'll show some ports as open, but won't be accessible from another machine.

For best results run it from another machine on the same network.

---

### Post by hackertarget on 2011-02-08
Or try testing your external public IP with a remote nmap scan. That's where most attackers will come from after all.

[http://hackertarget.com/nmap-scan/]("http://hackertarget.com/nmap-scan") <-- This is my site, so skip the plug and google "nmap online" if you prefer.

---

