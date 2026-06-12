---
title: "driver issues on reinstall"
date: 2006-10-30
forum: System76 Support
---

### Post by polkadotchickens on 2006-10-30
I have a Pangolin value laptop, and due to some unhappy accident while I was upgrading from Dapper to Edgy this weekend was forced to do a complete reformatting/reinstall.  I now have Edgy up and running in a basic sort of way, but I can't get the system76 drivers back on here.

What I've done so far:
- added [http://planet76.com/repositories/](http://planet76.com/repositories/) ./ to my software sources (as per somebody's software sources list I found on the internet)
- installed the system76-drivers package with synaptic
- tried to run the 'system76 driver installer' from the applications-->system menu, but I always get the following error message: These drivers a designed for System76 computers.  If you purchased your computer from System76 and are receiving this message please contact customer support at [email]support@system76.com[/email]

So, I did fire off an email, but I have yet to hear back from anyone, and I'm getting kind of sick of staring at nasty resolution and weird scaling as I crank out all the papers I have to write this week, not to mention being unable to use wireless internet (read: I am tethered to the wall in my busy and noisy living room)

Anyone have any ideas about how I can work around this and get my computer back up and running nicely?

---

### Post by crichell on 2006-10-31
Hi polka - we moved our email server this weekend so your mail may have been lost in the transition.  Please shoot me another one - support (at) system76.com  I'll make sure to get you taken care of.

BTW: For wireless the Edgy install does not install restricted modules by default.  The following will fix the issue:

```
sudo apt-get install linux-restricted-modules-generic
```

The only necessity for the driver on your machine is the microphone.  It doesn't do anything else.

Cheers, Carl

---

