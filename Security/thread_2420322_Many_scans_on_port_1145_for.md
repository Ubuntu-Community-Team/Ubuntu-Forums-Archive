---
title: "Many scans on port 1145 for??"
date: 2019-06-03
forum: Security
---

### Post by kpatz on 2019-06-03
I have my firewall logging incoming port scans mainly for my own curiosity, and to track trends.

This morning I saw a large number of incoming scans on port 1145, not a port I've seen scanned regularly before.  Even stranger, I'm seeing both TCP (SYN) and UDP scans on this port.  Sometimes the same IP will hit both TCP and UDP.

Source IPs are all over the map, so some sort of distributed botnet perhaps?  Why would they target 1145 all of a sudden?  Some new vulnerable service using that port?

According to SpeedGuide.net, this port is used by the CHCP backdoor (from 2003, very old!) and X9 ICue Show Control, whatever that is.

---

### Post by Doug S on 2019-06-03
> **kpatz said:**
> I have my firewall logging incoming port scans mainly for my own curiosity, and to track trends.I do the same, for the same reasons.

> **kpatz said:**
> This morning I saw a large number of incoming scans on port 1145, not a port I've seen scanned regularly before.  Even stranger, I'm seeing both TCP (SYN) and UDP scans on this port.  Sometimes the same IP will hit both TCP and UDP.

Source IPs are all over the map, so some sort of distributed botnet perhaps?  Why would they target 1145 all of a sudden?  Some new vulnerable service using that port?

According to SpeedGuide.net, this port is used by the CHCP backdoor (from 2003, very old!) and X9 ICue Show Control, whatever that is.I have not seen this one yet.
Between 2019.03.10 16:52:52 and 2019.06.02 23:47:50 there were 4 packets to port 1145 on my system, 3 TCP syn and one UDP.

I often observe sudden swarms of stuff from source IPs all over the map, and that these things often (mostly?) come in clumps.
I do not know what is suddenly so popular about port 1145 and have never understood the "why" or purpose of some of these things.

---

### Post by kpatz on 2019-06-03
They stopped as suddenly as they started.  Last scan on this port was at 10:02 local time.

I spot checked a couple of the IPs to see if they scanned other ports, and they didn't.  Seems that the 1145 scanners only scanned 1145.  Curiouser and curiouser.

Wonder what that was all about.

---

### Post by SeijiSensei on 2019-06-03
Sometimes these sorts of probes happen in conjunction with malware distributed in another fashion like via email.  The malware will open a specific port on infected machines that enables communication between it and other infected machines or their master.  Often these attacks will use long-abandoned TCP and UDP ports that were once assigned to a commercial entity but have since gone fallow.

By the way the service assignment for every "well-known" port is listed in the file /etc/services.  For 1145, it gives that "X9 iCue Show Control" service. Sounds like something involving theatrics.

---

### Post by TheFu on 2019-06-03
Could easily have been a DNS mess-up by some company.  To them, it appeared that their service was down. Took a little while to figure out the issue, find the DNS issue, fix it and for that change to propagate out to their clients.

Sometimes a simple mistake can explain things. Will probably never know the answer.

---

### Post by kpatz on 2019-06-03
Still no new scans on 1145 since this morning.  Marking thread as "solved".

Probably just one of those random things, and I just happened to notice it when I perused my logs.  Now back to the regular garbage... 443, 80, 23, 445, 3389, 22, etc.

(Though 1145 did hit #3 on my top 10 ports scanned for today, with 204 scans... beaten only by 445 and 23).

23... telnet... ugh.

---

