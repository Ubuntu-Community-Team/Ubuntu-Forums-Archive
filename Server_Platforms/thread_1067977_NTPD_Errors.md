---
title: "NTPD Errors"
date: 2009-02-12
forum: Server Platforms
---

### Post by ManuNarayan on 2009-02-12
I had previously been using the brute force and mostly maligned ntpdate in a cron to update the system clock on a few Ubuntu servers that I have.  I began looking into ntpd as a form of the preferred/more elegant solution to clock updates. 

I, for the life of me cannot get ntpd to work properly.  I did an apt-get install ntp and then configured /etc/ntp.conf with my local time server.  

If I do an ntpq I get the following:

> ntpq> peers
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 10.96.1.11      .LOCL.           1 u    2   64  377    0.182  8228.46  31.240
ntpq> association

ind assID status  conf reach auth condition  last_event cnt
===========================================================
  1 14607  9014   yes   yes  none    reject   reachable  1

It clearly can read the time from the ntp server and realizes what the offset is.  If I look in my ntpstats/peerstats I have entries every so often that indicate it is checking the time server but my ntp.drift does not have anything in it.

I've tried this on 2 servers with the same results.  I imagine I have something simple I am missing, but can't figure it out.  I assume the "Condition Reject" on the ntpq association has something to do with my errors.

Any help would be appreciated!

---

### Post by tubezninja on 2009-02-12
I have a feeling that the refid of ".LOCL." may have something to do with it, but I'm not sure of this.  For whatever reason, the ntp daemon on your boxes have deemed the server unhealthy enough to work out, and are rejecting it as a reference.

the assID of this server appears to be 14607.  in ntpq, issue this command:

```
ntpq> rv 14607
```

And post the result.

---

### Post by tubezninja on 2009-02-12
Actually, I think I can already see the problem.  I just didn't notice it because the proportional fonts kinda mangled the output.

Your 'peers' output:

[quote=ManuNarayan]```
ntpq> peers
remote refid st t when poll reach delay offset jitter
================================================== 
10.96.1.11 .LOCL. 1 u 2 64 377 0.182 8228.46 31.240
```[/quote]


Suggests that your server has a really high frequency offset, on the order of 8228+ ppm, suggesting an inaccuracy of more than 10 minutes per day.  Generally ntpd won't consider an ntp server "healthy" unless the offset is less than 500ppm, and most servers have offset way lower than this (mine is 2.075 ppm, and it syncs to a stratum 1 server that has an offset of -0.7ppm).

Considering the reference for your server is ".LOCL." I'm guessing the server you're trying to sync to is just using its own internal clock, unsynchronized to any other time reference.  Is that correct?

---

### Post by ManuNarayan on 2009-02-12
Thanks for the response.  That offset of 8228 came over the course of about 18 hours.  That is in MS right?  So that translates to 8 seconds?  

The local NTP server is just currently using its local clock it is the DC in an AD domain.  

An offset of 8MS over the course of 24 hours shouldn't be too much, should it?

---

### Post by tubezninja on 2009-02-12
No, it's not in milliseconds, it's clock frequency drift in parts per million.  And 8228 is **a lot**, certainly out of the bounds that ntpd was designed to accept as a sync reference.

Part of the problem here is that your server doesn't have a time reference to do its own corrections.  you should probably have it connect to pool.ntp.org so it can gain some accuracy of its own.  Once it's doing it's own corrections, the other hosts syncing off it will be more willing to use it as their reference.

---

### Post by ManuNarayan on 2009-02-12
Appreciate it.

I'm going to first try to just use pool.ntp.org on this Ubuntu box if that fixes its time issue, I'll look at getting my DC to sync time to an external box and then point my Ubuntu server at the DC.

Appreciate it, will let you know how that works.

---

### Post by tubezninja on 2009-02-13
Sounds like a plan!

Generally, I have one box in my cluster that syncs to one of four stratum 1 servers, and then all my other machines, regardless of platform, then sync to that in house ntp server.  That way several dozen servers and 50+ workstations aren't unnecessarily adding to the load of the ntp pool.

---

### Post by ManuNarayan on 2009-02-13
Yeah, that is what the arcitecture is supposed to be here, but I've not started syncing my DC to a stratum 1 source outside of the network, just using its internal HW clock.

I already see a different in my ntpq peers and association.  I am going to let it run over night, but assuming things look good, I'm going to look to get my DC looking at a stratum1 and go from there.

---

