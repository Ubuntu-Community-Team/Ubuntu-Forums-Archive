---
title: "Trying to understand and setup ufw for Snort reporting"
date: 2015-01-18
forum: Security
---

### Post by Curbie on 2015-01-18
I'm trying to setup network intrusion detection alert on home desktop, after some research Firewall Configuration for ufw and snort seems the best option for me. I downloaded and installed both from the Ubuntu Software Center and have spent a couple of days reading documentation, forums, search results and watching youtube videos..
    
I can't get the Status: to stay “ON” when the policy (I think that's what it is called by some) is configured as Incoming: is set to “Deny”, and the Outgoing: is set to “Allow”. Every time I exit Firewall Configuration and then reopen and unlock it, the Status: is “Off” again.

So either I'm doing something wrong or I'm thinking about this incorrectly, should I be setting the policy to Allow both Incoming and Outgoing, and then creating a rule for 0, Deny, Incoming, Log All, Both(TCP/UDP),0:65000(port range) or some such thing?

Xubuntu 12.04.1

---

