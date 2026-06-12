---
title: "Best Rootkit detector"
date: 2009-10-19
forum: Security
---

### Post by haz13 on 2009-10-19
I looked in the Synaptic Package Manager and found three
rkhunter
chkrootkit
unhide
Which one is the safest and best

---

### Post by witeshark17 on 2009-10-19
It may be a bit old, but a spot of reading that can't hurt: [ rootkit info]("http://sectools.org/rootkit-detectors.html")

---

### Post by unspawn on 2009-10-20
> **haz13 said:**
> I looked in the Synaptic Package Manager and found three
rkhunter
chkrootkit
unhide
Which one is the safest and best

I agree with witeshark17 that reading wouldn't hurt (even if that article is seriously outdated as it's from 2006). 

Unhide is a standalone application that tries to find hidden processes and network ports. If found (during --propupd) Rootkit Hunter will use it. Chkrootkit, like the same features in OSSEC HIDS, is a standalone application like Rootkit Hunter that tries to find evidence of rootkits and malware by looking for known device, process, file and directory names and other signs.

By reading further you would understand that all applications mentioned are *passive* because they respond to finding evidence *after* the breach of security has occurred as opposed to applications that daemonize themselves, remain active and conduct continuous checks in the background.

The best way to start your quest for "better" detection however hinges on hardening your machine, enabling auditing features, reporting and using an *active* approach to detection and deterrent.

For instance the article witeshark17 points to mentions tripwire, which AFAIK due to lack of development and licensing issues remains dormant, giving way to better (maintained, supported) alternatives like Aide or Samhain. I classify Aide as *passive* because it only runs manually or scheduled (cronjob). Samhain OTOH daemonizes itself, runs scans at intervals, can protect itself, can operate in a client-server way and comes with a Linux Kernel Module to watch for Interrupt Descriptor Table and system call problems.

It also is my opinion that no single application, or its reports, should be taken as gospel. This is well illustrated by comparing the current versions of OSSEC HIDS, Chkrootkit and Rootkit Hunter: you'll see that there's a lot of overlap in signatures but also that some applications will be more detailed in their searching or look for stuff others don't.

Next to that you should realize that "true" rootkit attacks have been dropping dramatically in favour of "light" and easy compromises that the current wave of badly configured machines and badly coded PHP-based applications allow. After all PHP is short for *Pretty Horrific Programming* ;-p


This post is in no way complete but I hope it sparks off your interest in "doing things the right way" instead of just installing one application in the hope that "fire and forget" tactics will result in a truly secure working environment. 

HTH

---

