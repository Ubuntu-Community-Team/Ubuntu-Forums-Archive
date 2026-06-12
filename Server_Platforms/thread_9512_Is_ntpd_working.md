---
title: "Is ntpd working?"
date: 2004-12-29
forum: Server Platforms
---

### Post by Rottweiler on 2004-12-29
How can I be certain ntpd is keeping my system clock accurate?
  
 On my RH/FC boxes I'm accustomed to seeing messages in /var/log/messages that show that ntpd is regularly updating my sys clock.
  
 I'm not seeing any activity in /v/l/daemons since I started ntpd on 12/23. There seems to be lots of action in /v/l/ntpstats but I don't know what it means.
  
  Not sure what to look for.

---

### Post by jferrando on 2007-10-07
You can check /var/log/daemon.log and search for 'ntpd'

I am also not sure if ntpd is updating my computer clock. I use ntpd as the ntp server for the local network.

jferrando@alcudia:~$ ps -ef | grep ntpd
ntp       7807     1  0 12:08 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 110:116 -g
1000     11576 11567  0 23:04 pts/5    00:00:00 grep ntpd

You can also try
$ ntpq

---

### Post by HermanAB on 2007-10-07
You can also change the clock a little bit, then see if it snaps back after a day or so.  Don't make the change too big.  If the diff is too large, then ntpd will not change the local clock - it will assume that you really want it that way, for some bloody minded reason.  A one or two minute change will work.

---

### Post by MJN on 2007-10-08
> **HermanAB said:**
> Don't make the change too big. If the diff is too large, then ntpd will not change the local clock - it will assume that you really want it that way, for some bloody minded reason.
 
It does this by design. ntpd is intended to maintain clock time with a very high degree of accuracy (+/- 128ms) - this can only be achieved by making small adjustments over time and making these subtle changes in response to the detection of how accurate the internal clock is compared with the believed-good external time sources. These tiny adjustments also keep the system running on an nice regular heartbeat which can be useful for purposes such as accurate logging - no out-of-step entries or other mismatches.
 
By default, if the clock is out by >1000s then ntpd makes the assumption that something is *very* wrong e.g hardware failure etc and so makes no attempt to correct the time (given that if things are that bad then what's the point in trying to fix it?). Furthermore, the last thing you want is time appearing to run backwards and so ntpd will try and not let this happen too much by not intervening with such a massive discrepency given something is clearly amiss (it is assumed the clock is initially set to something reasonable).
 
If you want to set the internal clock as a one-off, regardless of its current setting, then one should use **ntpdate** as this is designed for this purpose and will set the time purely on the say-so of another time source(s). It can be run as a cron job, or in a boot script, for periodic time updates (I would recommend ntpd however for any machine that spends most, if not all, of its time on).
 
This is all an aside from the issue here though[1] - but I thought it might be useful to explain why ntpd doesn't attempt a clock fix if it seems too 'wrong' (perhaps that does meet the definition of 'bloody mindedness'! ;))
 
Mathew
 
[1] Although, what *is* the issue here? The OP's question is from Dec '04 so presumably they've moved along... and jferrando doesn't actually say they're having problems (they just don't know if it's working, or not) and so there might not actually be any problem (in which case, can we all take the rest of the day off?)

---

### Post by koenn on 2007-10-08
> **MJN said:**
> I
[1] Although, what *is* the issue here? The OP's question is from Dec '04  ... 
maybe a problem with clock / ntpd ?

---

### Post by MJN on 2007-10-08
:lolflag:

---

