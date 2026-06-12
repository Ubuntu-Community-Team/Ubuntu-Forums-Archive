---
title: "dedicated server locks up"
date: 2008-05-18
forum: Server Platforms
---

### Post by tmilam on 2008-05-18
I just leased a dedicated server from serverpronto.com

It was running Dapper, and I really wanted it to have 8.04 - Hardy Heron, on it. I followed these instructions [https://help.ubuntu.com/community/HardyUpgrades#head-e059d5452a24b50d09c64df48058ef2d834eb197-2]("https://help.ubuntu.com/community/HardyUpgrades#head-e059d5452a24b50d09c64df48058ef2d834eb197-2") to upgrade it. But when I did so in the middle of an upgrade (apt was decompressing an archive so that it could install it...think it was lsof...it froze up on me!

I tried logging back in and couldn't. So I put in a reboot ticket and they rebooted it for me. As far as I know I only get one reboot ticket per month, but it's locked up on me again while I was attempting to finish the upgrade.

What could be going on here? I'm going to have to pay $29 to get it rebooted again and this really stresses me out :(

---

### Post by hyper_ch on 2008-05-18
is there any reason why you wanted to have it upgraded to hardy?

only one reboot per month? how much do you pay for the server and what are the server specs?

---

### Post by tmilam on 2008-05-18
It is $30/month, 40gb hard drive, 512mb ram, 1.6ghz athlon xp and 1TB data transfer per month...

Tech support rebooted it for me and said that this was the last message detected:

```
BUG: soft lookup detected on CPU#0
```

---

### Post by hyper_ch on 2008-05-18
you might want to have a look here:

[http://www.ovh.co.uk/products/kimsufi08.xml](http://www.ovh.co.uk/products/kimsufi08.xml)

I had such a server for a while before I needed more power / diskspace...

it would equal about to $ 32.-/M

---

### Post by tmilam on 2008-05-18
That's a great deal. I wish I'd shopped around more. Leasing a server without a remote reboot feature turned out to be a huge mistake. The server I leased is non-refundable. Maybe I'll make the switch in 3 months when my server time is up with this company....

Thanks for the suggestion.

---

