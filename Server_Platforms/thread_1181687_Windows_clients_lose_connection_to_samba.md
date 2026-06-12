---
title: "Windows clients lose connection to samba"
date: 2009-06-08
forum: Server Platforms
---

### Post by _2009 on 2009-06-08
We have a file server running the ubuntu 8.10 server platform and just recently our windows clients are losing the connection to the samba shares. When it happens the server stays online and doesn't display any errors on the login screen.

I'm new to ubuntu so don't know where to start looking in diagnosing this error, samba or NIC etc...

I'd really appreciate any form of help from anyone out there who's got any ideas or that can point me in the right direction to diagnose the problem myself...

Many Thanks,
_2009

---

### Post by zharmad on 2009-06-08
I'd start by taking a look at /var/log/samba/log.smbd f

---

### Post by _2009 on 2009-06-08
> **zharmad said:**
> I'd start by taking a look at /var/log/samba/log.smbd

Thanks. I'll take a look when I'm back at the office tomorrow morning and let you know...

Cheers,
_2009

---

### Post by _2009 on 2009-06-09
Here's the contents of /var/log/samba/log.smbd:
```
[2009/06/07 08:16:18 1] param/loadparm.c:map_parameter(6110)
  Unknown parameter encountered: "config-file"	
[2009/06/07 08:16:18 0] param/loadparm.c:lp_do_parameter(7196)
  Ignoring unknown parameter "config-file"	
[2009/06/07 08:16:18 1] param/loadparm.c:map_parameter(6110)
  Unknown parameter encountered: "config-file"	
[2009/06/07 08:16:18 0] param/loadparm.c:lp_do_parameter(7196)
  Ignoring unknown parameter "config-file"	
[2009/06/07 08:16:18 1] param/loadparm.c:map_parameter(6110)
  Unknown parameter encountered: "config-file"	
[2009/06/07 08:16:18 0] param/loadparm.c:lp_do_parameter(7196)
  Ignoring unknown parameter "config-file"	
[2009/06/07 08:16:18 1] param/loadparm.c:map_parameter(6110)
  Unknown parameter encountered: "config-file"	
[2009/06/07 08:16:18 0] param/loadparm.c:lp_do_parameter(7196)
  Ignoring unknown parameter "config-file"	

```

FYI the times & dates above don't correspond to dropped connections that we're having. 

I forgot to mention that the connection comes back after about 5 minutes.

Any ideas?

Thanks again for any help on this....

_2009

---

### Post by ghen on 2009-06-10
Do you have any network issues? How far (logically) are the workstations from the file server? Are they wireless? How often does this happen? Are the shares mapped by IP or server name? Are you able to ping the server when the shares are down? Are you able to visit the shares manually using \\servername\share in the run command? (assuming windows) What else does the file server do besides Samba?


In windows there is a "feature" that lets you turn off a network driver/card to save power. I don't know if a feature like this exists in linux but its worth a google search since this would display the same symptoms you've noticed.

---

### Post by _2009 on 2009-06-10
Hi,

Thanks for looking.

No other network issues that I've noticed, but that's a good call. I'll check connectivity to other machines when it next happens.

Not sure what you mean by logically? It's a wired Gigabit lan in a small office and all the machines are in the same room.

Usually 1-2 times a day.

Hope that helps?

Cheers,
_2009

---

### Post by trillex on 2009-06-10
Sorry to steal a bit of the thread, but I've been having the same issue. The problem comes and goes, but sticks around for a long time which sometimes forces me to reboot the server. Usually after that, it works perfectly.

This time around, it started happening because it dropped it's IP (It had an IP assigned but it refused every connection to the server, yet torrents, irssi (in screen) and other such things were still running without a problem), making me have to request a new one from the DHCP. I restarted the samba service, just to be sure that it was actually set to the new IP. It worked fine for a few hours but after a large transfer (around 16 GB), it completely shut me off. It was actually immediatley after this transfer. I've since been unable to get to it on it's NetBIOS name or it's IP. 

log.smbd is completely empty except for some CUPS errors and the SIGTERM. Same with log.nmbd. 

Everything else BUT samba is working perfectly, both in and out.

EDIT: Just as I wrote that, I'm now able to connect again. Wonder for how long.

EDIT2: Went down after 2 minutes.

---

### Post by zharmad on 2009-06-10
What's the IP address lease time set to on your DHCP server? Have you had the same issue after trying to use a static IP address?

---

### Post by trillex on 2009-06-10
> **zharmad said:**
> What's the IP address lease time set to on your DHCP server? Have you had the same issue after trying to use a static IP address?

My router unfortunately doesn't have a lease time option, so it's most likely default. I've no idea what default is, though. :) I've tried to set it up with a static IP, but it is unable to go through the router, despite DNS server and default gateway being set properly. It's like it keeps it out.

EDIT: Just tested with static again. Seems to be working better after a firmware update.

---

### Post by ghen on 2009-06-10
try using the ping -t command to test connectivity to the server at all times that the share goes down. (ctl+c to cancel)

This should rule out any network related issue.

---

### Post by _2009 on 2009-07-07
> **ghen said:**
> try using the ping -t command to test connectivity to the server at all times that the share goes down. (ctl+c to cancel)

This should rule out any network related issue.

Ok, sorry for the slow feedback, we haven't had the problem for ages. But it did just happen again.

Using the ping command reveals that the server isn't visible across the network. But it is still up and accessible via a terminal.

How can I troubleshoot the network connection?

Many thanks,
_2009

---

