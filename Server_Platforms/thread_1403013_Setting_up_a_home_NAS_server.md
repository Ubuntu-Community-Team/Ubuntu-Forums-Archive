---
title: "Setting up a home NAS server"
date: 2010-02-09
forum: Server Platforms
---

### Post by nburns on 2010-02-09
I recently installed WHS to play around with it before doing a fresh install of ubuntu server.  The reasons why I went with ubuntu server as opposed to WHS are:
-From what I've read, the drive extender (though a cool feature) is quite slow in WHS.
-I've read too many threads about people losing all of their shares when one of their drives dies (even for shares that shouldn't be impacted)
-I'm just more familiar with ubuntu.

Though one of the best things WHS has going for it is its great admin console.  There's a fantastic disk management add-in that I'd love to see replicated in webmin, ebox, or some other remote admin software.  Does anything like this exist?

See link for an example screenshot of what I'm talking about: [http://www.tentaclesoftware.com/whsdiskmanagement/images/1.0.8.4_Main_Tab.png]("http://www.tentaclesoftware.com/whsdiskmanagement/images/1.0.8.4_Main_Tab.png").

In the screenshot, you can quickly / easily see how each drive is doing:
- Disk size
- Disk utilization
- SMART status
- Drive temp
- Current transfer activity

I know webmin offers a module close to this called "SMART Drive Status", but unfortunately the temps are buried in the full stats (and stuck on Celsius-only AFAICT) and it doesn't include disk utilization or current drive activity.  I've played around in ebox briefly, but it looks like webmin is closer.

Are there any other remote-admin type tools that can give me a good disk snapshot (something I think is pretty important in a home NAS server)?

---

### Post by pirateghost on 2010-02-09
personally i like phpsysinfo in combination with hddtemp and lm-sensors

gives a nice view of my server stats

[http://phpsysinfo.sourceforge.net/](http://phpsysinfo.sourceforge.net/)

---

### Post by tlsarles on 2010-02-09
What WHS does is essentially creates a soft RAID. If your not familiar with this concept, consult Wikipedia on RAID levels. They make a fancy RAID manager, and call it a server OS... ok, fine, but if you really want this kind of feature set, but want it to have a better feature set, reliability, and other neat stuff. either A: Get a hard RAID controller, or B: setup a soft RAID. You can do this in Linux... or check out the wiki for ZFS, which is essentially a super-awesome soft RAID that runs on open solaris, BSD, and probably others.

---

### Post by pirateghost on 2010-02-09
> **tlsarles said:**
> What WHS does is essentially creates a soft RAID. If your not familiar with this concept, consult Wikipedia on RAID levels. They make a fancy RAID manager, and call it a server OS... ok, fine, but if you really want this kind of feature set, but want it to have a better feature set, reliability, and other neat stuff. either A: Get a hard RAID controller, or B: setup a soft RAID. You can do this in Linux... or check out the wiki for ZFS, which is essentially a super-awesome soft RAID that runs on open solaris, BSD, and probably others.
+1

i hate WHS.  i prefer using LVM and Linux RAID

---

### Post by nutznboltz on 2010-02-09
[http://www.openfiler.com/](http://www.openfiler.com/)

---

### Post by pirateghost on 2010-02-09
> **nutznboltz said:**
> [http://www.openfiler.com/](http://www.openfiler.com/)

i used openfiler for a couple of years.  it is extremely picky about certain things.  they have done a lot of work on it in the last few months though, updating conary with more recent binaries.  there were some issues that i couldnt get around and decided to ditch it.  

most people are turned off by having to set up the LDAP server on it, but i have a windows active directory domain, which made things a lot easier.

---

### Post by maddog2050 on 2010-02-10
Have you looked at [www.freenas.org]("http://www.freenas.org")

---

### Post by nburns on 2010-02-10
> **maddog2050 said:**
> Have you looked at [www.freenas.org]("http://www.freenas.org")

I have, but I've also heard complaints about the samba implementation being slow.  So I decided to just go the ubuntu server route.  Though I'm anxiously waiting to see how the freenas fork/re-write turns out on debian - [http://blog.openmediavault.org/]("http://blog.openmediavault.org/")

Btw - I tried the suggestion on phpsysinfo w/ hddtemp and this seems to be a bit closer to what I was looking for (though it misses the current disk utilization/activity).

---

### Post by pirateghost on 2010-02-10
> **nburns said:**
> I have, but I've also heard complaints about the samba implementation being slow.  So I decided to just go the ubuntu server route.  Though I'm anxiously waiting to see how the freenas fork/re-write turns out on debian - [http://blog.openmediavault.org/](http://blog.openmediavault.org/)

Btw - I tried the suggestion on phpsysinfo w/ hddtemp and this seems to be a bit closer to what I was looking for (though it misses the current disk utilization/activity).


if you monitor things via ssh a lot (i do)
```
sudo apt-get install saidar
```then run saidar in ssh terminal...realtime read/write stats

also a good CLI bandwidth monitoring:
bmon
or jnettop

BTW, i am anxiously awaiting that debian fork.  it looks very promising..

---

