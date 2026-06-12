---
title: "Protection for my Windows Network"
date: 2008-04-04
forum: Security Discussions
---

### Post by gratefulfrog on 2008-04-04
Hi!

I'm concerned with the security of my Windows machines with regard to an attack that could come via my Linux box.

Suppose that a malicious piece of software were to get installed on my Linux box with normal user permissions.

Suppose that I have shared folders on my Windows machines mounted via samba with r/w permission.

I am wondering if the malicious software could write to a Windows shared folder and do damage (erase, corrupt, infect) there?

Can anyone adivise on this?

If protection is indeed necessary, would firestarter or other software protect against this, or are there other options to protect against it?

Cheers,
GF.
[http://gratefulfrog.net]("http://gratefulfrog.net")

---

### Post by bhavi on 2008-04-04
Yep you can do it with an IDS (Intrusion Detection System) I believe which is used to prevent intrusion and snort is widely used as an IDS.. (IDS basically is just a trap sort of thing)

More on snort in windows here:

[http://articles.techrepublic.com.com/5100-6345_11-5287011.html](http://articles.techrepublic.com.com/5100-6345_11-5287011.html)

Snort on ubuntu here:

[http://www.howtoforge.com/intrusion_detection_base_snort](http://www.howtoforge.com/intrusion_detection_base_snort)

---

### Post by mattress on 2008-04-04
I used Prelude-IDS a while back and was very impressed with it.

[http://www.prelude-ids.org/](http://www.prelude-ids.org/)

-m

---

### Post by bhavi on 2008-04-04
> **mattress said:**
> I used Prelude-IDS a while back and was very impressed with it.

[http://www.prelude-ids.org/](http://www.prelude-ids.org/)

-m
Yes you can use Prelude IDS too.. Prelude is now an industry standard in IDS...

---

### Post by The Cog on 2008-04-04
That said, an attack is far more likely to come in the other direction - from your compromised windows boxes towards Linux. Either way, using an IDS will help.

---

### Post by kevross_33 on 2008-04-04
you can provide protection for the whole network using ipcop ([www.ipcop.net](www.ipcop.net)) though it is installed on its own on a machine but works great on an older machine. Like sonicwall and equivalent it had IDS, VPNs, stateful firewall etc and addons for intrusion prevention and rules selection (guardian from mhaddons), network antivirus, webproxy, caching windows updates so they are only downloaded once, content filtering etc. A great solution. Type in "the perfect linux firewall" into google to get a good guide to getting started with it.

---

