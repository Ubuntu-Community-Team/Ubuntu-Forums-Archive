---
title: "Opening 2089 for inbound vs outbound"
date: 2018-04-20
forum: Server Platforms
---

### Post by faizan90 on 2018-04-20
I have cPanel running on CentOS 7 and according to [https://documentation.cpanel.net/display/CKB/How+to+Configure+Your+Firewall+for+cPanel+Services#HowtoConfigureYourFirewallforcPanelServices-Ports](https://documentation.cpanel.net/display/CKB/How+to+Configure+Your+Firewall+for+cPanel+Services#HowtoConfigureYourFirewallforcPanelServices-Ports), I need to have 2089 open for OUTBOUND only. However, for some reason, my system admin has opened 2089 on INBOUND (not in the iptables, but in the external hardware firewall). Asking them wasn't much help.


Can anyone please confirm that 2089 (required for cPanel license) needs to be opened ONLY for OUTBOUND in iptables or also for INBOUND?


Any help will be much appreciated.


Thanks.

---

### Post by LHammonds on 2018-04-20
Typically, hardware and software firewalls allow all outbound traffic.

If the hardware guy was told to open up port 2089, he probably did so by creating an INBOUND rule since OUTBOUND is probably wide-open.

Might want to check and see if the firewalls are allowing all outbound or if they are limiting outbound too.

---

### Post by faizan90 on 2018-04-20
That's what I am wondering. Why was the hardware guy told to open 2089 for INBOUND when it is actually supposed to be open for OUTBOUND? Would you know why as like I said, they aren't very helpful. And yes I have default DROP policy on OUTBOUND traffic, hence my concern.

---

### Post by darkod on 2018-04-21
Hold on, let me understand... You have DROP on OUTPUT on yor iptables and you are worrying about the HW FW (the next hop)?

Your own iptables is blocking 2089 outbound if you have DROP rule and without any specific ACCEPT rule.

Why don't you create outbound rule for 2089 in your iptables and see if it works? If the assumption that the HW FW is letting it trough, it should work when you allow it in iptables.

If it does work, don't bother understanding what he did on the FW if they are not helpful. Whatever traffic they let through there won't enter your server if your iptables don't have corresponding rules. So if you are not letting 2089 inbound on your iptables, no ned to worry about it.

We can't speculate and answer why the FW admin did what he did because we don't even know how the request was sent to him. Like LHammonds says, if you only say "open port 2089" to FW admin the default operation is to open it inbound. So if you or anyone else giving him the request wasn't very specific, it's not his fault... But anyway all of this is sort of irrelevant, your iptables are also protecting your server. Adjust the rules you need and check if it works.

---

