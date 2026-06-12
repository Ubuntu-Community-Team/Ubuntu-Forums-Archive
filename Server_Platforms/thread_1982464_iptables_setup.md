---
title: "iptables setup"
date: 2012-05-18
forum: Server Platforms
---

### Post by Raj Singh on 2012-05-18
Hello folks, how would I specify this in iptables?

1. add specific blocks to allow
2. world should only get to SSH by default.   
[COLOR=black][/COLOR]

[COLOR=black][/COLOR]
[COLOR=black][FONT=&quot]Thanks a lot. 
[/FONT][/COLOR]

---

### Post by koenn on 2012-05-18
seen these : [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables) ?

examples near the end of the page

---

### Post by volkswagner on 2012-05-20
koenn, thanks for the link.  It was very informative to me, as I too am trying to get acquainted with IPtables.

---

### Post by Lars Noodén on 2012-05-20
One thing to add is that chains using REJECT are easier to debug than those using DROP.  

There are also other reasons to go with REJECT:

[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)

[http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)

---

