---
title: "Should there be an ntpdate cron job?"
date: 2006-06-18
forum: Server Platforms
---

### Post by foxylad on 2006-06-18
Hi - 

As far as I can see, ntpdate is used to set the server's time when the network comes up (in network/if-up.d/ntpdate) during boot. Given that a server's clock can drift a fair amount over the normal uptime of a linux server, would it be good to include ntpdate in /etc/cron.daily so the clock is resynchronised once a day?

I have used ntpd in the past, but there doen't seem to be an ntpd package in the standard repository.

If I get positive feedback, I'll do a (very short) page for the wiki/server guide.

Cheers!
FoxyLad.

---

### Post by Randomskk on 2006-06-18
I agree; I've linked ntpdate into /etc/cron.daily so that my clock updates every day.

At least, it should do, I've just realised that I don't know if it actually is.. I should check :P

edit: ok, it seems to work, and I've done this:
```

sudo apt-get install ntp ntpdate
sudo ntpdate pool.ntp.org
sudo vi /etc/cron.hourly/ntpdate.sh

```
[quote=/etc/cron.hourly/ntpdate.sh]
!#/bin/bash
ntpdate pool.ntp.org > /dev/null
exit 0
[/quote]
```

sudo chmod +x ./ntpdate.sh
sudo ./ntpdate.sh
date

```

That seems to work nicely for me.

---

### Post by nagilum on 2006-06-18
IIRC ntpdate is intended only for occasional updates, not regular ones. To keep a system's clock in sync with a ntp server the package 'ntp-simple' should be used (it provides a simple ntp daemon).

---

### Post by Randomskk on 2006-06-18
Ah, ok, so I've installed that and configured it, should I just be able to leave it now and it will auto-update?
How often does it auto-update?

---

### Post by foxylad on 2006-06-18
Thanks to both of you. I've used ntpd before so that is my preferred solution - I just didn't find it using "apt-cache search ntpd" so I thought Ubuntu preferred the ntpdate utility for some reason.

I have done a page for the Wiki offering both of these options, and suggesting investigating pool.ntp.org for time servers [here]("http://wiki.ubuntu.com/NTPTimeSynchronisation").

---

