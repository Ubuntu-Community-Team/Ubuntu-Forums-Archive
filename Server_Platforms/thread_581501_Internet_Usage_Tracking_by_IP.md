---
title: "Internet Usage Tracking by IP"
date: 2007-10-19
forum: Server Platforms
---

### Post by quietas on 2007-10-19
Howdy folks. Before I start a flame war about privacy please hear me out.

I have a few employees out of hundreds who are known to waste time browsing the net massively instead of working, others probably do as well but get work done. This includes huge downloads and streaming audio/video. I ban sites, but of course there are hundreds out there, plus it's rather easy to find proxies out there to bypass blocks.

Anyway, to reduce my internet load and reduce wasted **PAID** company time, I need a way to track Internet usage by IP. I was thinking about setting up Squid, but I need some sort of front end to produce pretty reports for my VPs also.

What's the easiest way to set up Squid so that it is transparent with tracking capabilities and might as well cache while I am at it?

~ Culley

---

### Post by quietas on 2007-10-19
Nothing?

---

### Post by johng4 on 2007-10-19
I've done this for my home network.  My ex-wife used to do some questionable activities on MySpace and Yahoo.  To prevent this while I wasn't around I used Squid and SquidGuard to monitor and block attempts made to access MySpace and Yahoo on my local network.

Since then, I've retooled my servers, as well as my network.. and gotten a new wife.  This time around I'm using Squid and Dansguardian, and found it considerably easier to manage.

Dansguardian will even allow you to isolate problem users into their own access control group and limit their browsing abilities based not only on the sites, but also the content of what they are browsing.  You can set squid up as a transparent proxy on the network as well, so no matter what proxies your users use, there's no bypassing Squid.

For reports.. Squid Cache Manager, Squid Reports, and Calamaris are all in the repos, and require little to no configuration (except apache if you go beyond the default LAMP install).

---

### Post by johng4 on 2007-10-19
Webmin also has modular support for Squid, and despite the many issues with Webmin and Ubuntu Servers - Squid modules in webmin work just fine, and include support for Calamaris Logs I believe.

---

### Post by quietas on 2007-10-23
I'll have to look into DansGuardian. I've seen more than a few mention of it, but they seem to mostly be at home, not many in a business environment.

What's up with Ubuntu and Webmin anyway? As I understand, it is poorly written, but it works. Nothing seems to have replaced it, people say Ebox, but I tried that with Gutsy and not anywhere near as many fetures.

---

