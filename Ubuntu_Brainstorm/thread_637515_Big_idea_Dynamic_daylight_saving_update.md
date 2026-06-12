---
title: "Big idea: Dynamic daylight saving update"
date: 2007-12-11
forum: Ubuntu Brainstorm
---

### Post by nick4mony on 2007-12-11
We need a better way of handling daylight saving changes.  There have been three recent changes in rapid-fire in two countries (Australia and New Zealand), and the Linux community has trouble keeping up.

My idea is to have a dedicated protocol that transfers updated daylight saving information.

This protocol would be cross-platform (as NTP & DNS is), and there would be a heirarchy of computers that hold daylight saving information, and client computers can check on a monthly or weekly basis.

I realise this idea is a lot bigger than Ubuntu, but if we start up something that's robust, other distros will climb on board, and yes, Mr Gates is welcome provided he plays by the rules.

The current "protocol" of hand crafting TZ files and handing them out (manually or by apt-get) is fairly clumsy, so it needs to be something much more dynamic (like NTP or DNS), and it should work across all OSs.

Ideas for a protocol: 
[list=1]
[*] http download of timezone files
[*] XML file to a particular schema (with HTTP download)
[*] Extensions to the NTP protocol
[*] Another protocol, another port.
[/list]

This has parallels with DNS: in the very early days, name resolution was actually done by distributing hand-craft /etc/hosts files, but after a short while it became clumsy; they invented the DNS protocol, complete with a heirarchy of DNS servers.

**The aim is** a single point of update, which every computer in the world will eventually find out about.

---

### Post by smartboyathome on 2007-12-11
What type of update do you suggest? You state everything but HOW it would be updated.

---

### Post by ccw on 2007-12-11
Edgy tzdata was updated 6 times in the year+  after its release. I would rather take those 6 timely updates than constantly poll some root server for changes that may or may not affect my environment.

Ubuntu's upgrade policy is rather friendly to tz updates.

Is this in reference to this:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=433869](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=433869)

---

### Post by nick4mony on 2007-12-12
Hi guyz,

ccw and smartboy - thanks for your comments.

**smartboy** - I have several examples in my mind of the type of update, but I think we need to flesh out the merits of the idea before the mechanics.

**ccw** - I agree that Ubuntu is reasonably up-to-date with timezones, but they did miss the Commonwealth Games change in Australia in 2006 (and Breezy never got the update).  However, my central point is that each distribution must independently source a TZ update, package it into Yum, apt, Windows Update, or whatever, and this is duplicated work.

Also remember that many Ubuntu users run a mixed environment (eg a RHEL server, or Windows, or pfSense or Untangled), and they'd prefer to see auto updates, rather than having to figure out when this or that platform is going to be updated, or whether/how to go into a system and fiddle with the files.

I hadn't seen the Debian bug report, but it does illustrate the pain quite well - I'd hate to think if I was running pfSense or untangled - if they'd ever get updated.

Even if every distribution keeps up-to-date, there are home-made (LFS) systems, or systems running old versions (they shouldn't but they do).

As I said in the beginning **I realise this idea is a lot bigger than Ubuntu**.  If Ubuntu can run with this, and convince Fedora Core to go along with it, then we've probably got a critical mass which everyone else will probably follow.

---

### Post by Neon Lights on 2007-12-14
Yeah, we'd definitely have to get at least one other distro involved in this. But I think it's a good idea, if we can get it going. =]

---

