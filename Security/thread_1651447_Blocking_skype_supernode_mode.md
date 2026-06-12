---
title: "Blocking skype supernode mode"
date: 2010-12-23
forum: Security
---

### Post by dargaud on 2010-12-23
Hello all,
last night Skype went awry and established tens of thousands of connections on port 443 (https). My guess is that it got promoted to 'supernode' status and started routing other people's calls. It's a no-no on the network I'm sitting. So the question is, how do I block it from becoming supernode on Ubuntu ?

Searching on Google returns registry hacks, and possibly blocking port 80+443 for skype. I don't have specific firewall running on this machine so what can I do ?

Thanks.

---

### Post by HermanAB on 2010-12-23
Simple:
$ sudo killall skype

---

