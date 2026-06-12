---
title: "no-ip"
date: 2012-09-21
forum: Server Platforms
---

### Post by noxxallison on 2012-09-21
hi all 

i am having problems with my no-ip its active but the ip address is as 0.0.0.0
and i have tried to update it but it does not update this is what i am getting


1 noip2 process active.

Process 1052, started as noip2, (version 2.1.9)
Using configuration from /usr/local/etc/no-ip2.conf
Last IP Address set 0.0.0.0
Account [EMAIL="noxx.allison@gmail.com"]xxxxxxxx@gmail.com[/EMAIL]
configured for:
    host  xxxxxx.zapto.org
Updating every 30 minutes via /dev/eth0 with NAT enabled.

Any body having the same problem help please

---

### Post by Groodles on 2012-09-22
I guess you built noip2 from source as it's not in the repos for 12.04?

Were there any dependency issues?  I'm pretty sure it needs CURL and a couple of other things to work.

Other than that I'd suggest re-creating your config (as root:  noip2 -C)

---

