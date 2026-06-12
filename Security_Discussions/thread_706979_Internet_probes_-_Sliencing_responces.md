---
title: "Internet probes - Sliencing responces"
date: 2008-02-24
forum: Security Discussions
---

### Post by metzen_w on 2008-02-24
I was wondering if there is a way to configure my system to not respond to port scans with an Internet probe. I have found that my systems does this to determine information about potential hackers/script kitties. I currently have shorewall firewall installed with the following rules:

SECTION NEW
ACCEPT  net     fw      tcp     3333
DROP    net     fw      tcp     1:3332
DROP    net     fw      tcp     3334:65535
DROP    net     fw      tcp     113
DROP    net     fw      icmp
DROP    loc     fw      icmp
DROP    loc     fw      tcp     1:52
DROP    loc     fw      tcp     54:79
DROP    loc     fw      tcp     81:138
DROP    loc     fw      tcp     140:444
DROP    loc     fw      tcp     446:3332
DROP    loc     fw      tcp     3334:8079
DROP    loc     fw      tcp     8081:9999
DROP    loc     fw      tcp     10001:65535

I understand that I do not need to drop the net ports because they are already un-trusted however in light of the internet prob responses I tried this method. Any explanation on why the system responds this way and how to change the response would be greatly appreciated.

---

### Post by metzen_w on 2008-02-25
I found the answer to my own question.  Its an iptables config.
--no-rdns      - Disable name resolution against scanning IP addresses.

Source for this option
[http://trac.cipherdyne.org/trac/psad/changeset/2061](http://trac.cipherdyne.org/trac/psad/changeset/2061)

---

