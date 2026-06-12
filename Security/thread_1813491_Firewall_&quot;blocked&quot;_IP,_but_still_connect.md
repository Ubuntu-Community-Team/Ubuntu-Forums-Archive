---
title: "Firewall &quot;blocked&quot; IP, but still connecting..."
date: 2011-07-27
forum: Security
---

### Post by DawieS on 2011-07-27
I was using Transmission BitTorrent the other night, when I noticed that I was getting heavily spammed by one particular IP. I then stopped the torrents and disabled the network.

I wanted to add my own block-list, containing this IP, to $HOME/.config/transmission/blocklists, but could not get it working. Transmission is supposed to parse this text file into binary format upon startup. I tried both allowed formats, but Transmission kept on creating an empty binary file (this was version 1.93 in the official repo, I have since upgraded to 2.33 by adding a PPA, and it now works correctly).

I then blocked this IP in the firewall outbound traffic policy, allowing Transmission, on the port number that I forwarded on the router, on the inbound policy. After a restart, I watched the torrents picking up speed as more peers connected, and then saw this IP getting blocked. However, the same IP immediately also appeared as a peer in one of my torrents.

I then double checked all settings and log files, to ensure that there is no typo. The same IP that was shown as blocked in the log files, also successfully made a connection to Transmission. After a while I gave up, and shut down.

The IP was an incoming connection, but was explicitly nominated to be blocked in outgoing traffic. The firewall was supposed to silently ignore this IP, not making a connection possible.

ICMP filtering was enabled, with the following not allowed:
- Address Masking
- Redirection
- Source Quenching

Now surely this is not normal?
Is this a bug in ip-tables?
Isn't this a serious security breach?
Anyone noticed something similar?

---

### Post by bodhi.zazen on 2011-07-27
> **DawieS said:**
> I was using Transmission BitTorrent the other night, when I noticed that I was getting heavily spammed by one particular IP. I then stopped the torrents and disabled the network.

I wanted to add my own block-list, containing this IP, to $HOME/.config/transmission/blocklists, but could not get it working. Transmission is supposed to parse this text file into binary format upon startup. I tried both allowed formats, but Transmission kept on creating an empty binary file (this was version 1.93 in the official repo, I have since upgraded to 2.33 by adding a PPA, and it now works correctly).

I then blocked this IP in the firewall outbound traffic policy, allowing Transmission, on the port number that I forwarded on the router, on the inbound policy. After a restart, I watched the torrents picking up speed as more peers connected, and then saw this IP getting blocked. However, the same IP immediately also appeared as a peer in one of my torrents.

I then double checked all settings and log files, to ensure that there is no typo. The same IP that was shown as blocked in the log files, also successfully made a connection to Transmission. After a while I gave up, and shut down.

The IP was an incoming connection, but was explicitly nominated to be blocked in outgoing traffic. The firewall was supposed to silently ignore this IP, not making a connection possible.

ICMP filtering was enabled, with the following not allowed:
- Address Masking
- Redirection
- Source Quenching

Now surely this is not normal?
Is this a bug in ip-tables?
Isn't this a serious security breach?
Anyone noticed something similar?


The order of rules makes a difference in iptables, so you will need to post your rules for review.

---

### Post by DawieS on 2011-07-28
Many thanks to bodhi.zazen for pointing that out.:grin::grin:

I have now discovered that if I make use of a graphical firewall manipulation tool like GUFW or Firestarter, then the **order** in which I do things, is also important. It seems as if these tools merely add new rules to the bottom of the iptables list, in the same order that you create them.

I should have:

- First, blocked the offending IP on the outbound policy, then
- Second, allowed Transmission with the open port on inbound policy,

for the block to have been effective.

---

