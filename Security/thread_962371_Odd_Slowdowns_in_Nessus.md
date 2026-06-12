---
title: "Odd Slowdowns in Nessus"
date: 2008-10-29
forum: Security
---

### Post by Tk0680 on 2008-10-29
I've been using Nessus to perform regular network scans to track the effectiveness of various tactics to reduce vulnerabilities, but it's acting somewhat oddly with regard to speed.

Firstly, logging into the daemon takes a good few minutes, which seems odd for something as straight forward as a localhost login.

Secondly, the actual scanning (currently set to port scan 20 hosts at once, and perform security checks on 4 at a time) generally goes very slowly, but will occasionally zip along like a greased up Michael Phelps before slowing down again with no obvious change in environment.

I'm a long way from an expert with Nessus - can anyone suggest anything to speed things up?

---

### Post by Sarmacid on 2008-10-29
I'm not a Nessus expert, but I've been running it for a while. I usually use the default scan and have noticed that if you use the -v parameter in CLI it takes at least 5 times longer to perform the scan, and also, another thing that slows the scan is having a firewall up.

---

