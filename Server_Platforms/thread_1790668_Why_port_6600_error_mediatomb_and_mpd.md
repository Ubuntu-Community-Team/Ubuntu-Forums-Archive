---
title: "Why port 6600 error mediatomb and mpd"
date: 2011-06-25
forum: Server Platforms
---

### Post by volkswagner on 2011-06-25
Greetings,

I have noticed this error while booting 10.04 server.  I have mpd and mediatomb both installed and working.  I noticed mediatomb a little slow while using a wireless device... not sure if it is a junk device, slow server, or if this error has anything to do with slow perf.

From boot.log
```
 * Starting AppArmor profiles                                            [ OK ] 
 * Starting Music Player Daemon mpd                                      [ OK ] 
 * Starting upnp media server mediatomb listen: bind to '0.0.0.0:6600' failed: Address already in use (continuing anyway, because binding to '[::]:6600' succeeded)

```

I can't find any documentation related to mediatomb and port 6600.


sudo lsof -i :6600
```
COMMAND PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
mpd     833  mpd    4u  IPv6   3719      0t0  TCP *:6600 (LISTEN)
```

I do realize this error may be superficial, but I'm still learning and would like help as to why this occurs.

---

### Post by papibe on 2011-06-25
I really don't have any experience with mpd or MediaTomb, but it seems odd to me that you're using ipv6 on your home network.

Maybe if you disable ipv6 support for mpd, things would run faster (I believe from their [site]("http://mpd.wikia.com/wiki/Configure") that IPV6 is enabled by default).

Just a thought.
Regards.

---

### Post by volkswagner on 2011-06-25
papibe, apparently you know more than you think!

Thanks for the reply.  I did notice the ipv6, but did not investigate that path.  

I disabled ipv6 globally using Grub2.

After reboot, I no longer get error in boot.log, and mpd is now using ipv4.  

Let me see if I get any performance gain in Mediatomb...

Color me crazy, but I think the wireless device ([EZ-Stream]("http://www.smc.com/index.cfm?event=viewProduct&cid=5&scid=36&localeCode=EN_USA&pid=1495")) is communicating better with Mediatomb.  I know the device is old, but is serves music just fine wireless to the pool!

Solved, and solved.  Thanks again.

---

