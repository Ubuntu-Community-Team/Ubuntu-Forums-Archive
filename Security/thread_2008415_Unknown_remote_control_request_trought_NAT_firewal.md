---
title: "Unknown remote control request trought NAT firewall"
date: 2012-06-22
forum: Security
---

### Post by Xenoty on 2012-06-22
Hello,

Yesterday when i was using my computer i saw this message :


[CENTER][IMG]http://pix.toile-libre.org/upload/original/1340398446.png[/IMG][/CENTER]


And i was wondering, how does this guys manage to go trough the nat firewall of my router ( which normally don't respond to unsolicited incoming requests on any port and make my LAN invisible to Internet )? I'm on a securised home network, nat is enable and there isn't any port forwarding.

And i was also wondering is there any security threat there ?

Thank in advance for your help :)

---

### Post by cariboo on 2012-06-22
Do you have uPnP enabled on your router?

---

### Post by Ms. Daisy on 2012-06-22
You could uninstall remote desktop if you don't use it.

---

### Post by CharlesA on 2012-06-22
> **Ms. Daisy said:**
> You could uninstall remote desktop if you don't use it.
This.

Having uPnP enabled would be the reason someone was able to connect. You did set a password, right? ;)

---

### Post by HermanAB on 2012-06-23
VNC is the most (pretty much only) way in which Ubuntu machines get hacked.  You should not just turn it off - you should uninstall it. It is evil.

---

### Post by U202E on 2012-06-23
what router do you use?
maybe someone found/made an exploit for your router like one of these:
[SMCWBR14-G2 PPPoE Data Disclosure (ADSL Router)]("http://www.1337day.com/exploits/18282")[HUAWEI SmartAX MT880 CSRF Vulnerability (ADSL Router)]("http://www.1337day.com/exploits/18275")[Sagem F@st 1500WG PPPoE Data Disclosure (ADSL Router)]("http://www.1337day.com/exploits/18258")[D-Link DSL-2640U PPoE Data Disclosure (ADSL Router)]("http://www.1337day.com/exploits/18213")[TP-Link TD-W8901G CSRF Vulnerability (ADSL Router)]("http://www.1337day.com/exploits/18208")[Mikrotik Router Remote Denial Of Service]("http://www.1337day.com/exploits/18159")[D-Link DSL-2640U (ADSL Router) CSRF Change Admin Password]("http://www.1337day.com/exploits/17578")[Sagem F@ST 2604 CSRF Vulnerability (ADSL Router)]("http://www.1337day.com/exploits/17553")[D-Link DSL-2640B (ADSL Router) CSRF Vulnerability]("http://www.1337day.com/exploits/17545")if your router is on the list than you have bad luck (there are more router exploits, this is just a small list.)

---

### Post by CharlesA on 2012-06-23
> **HermanAB said:**
> VNC is the most (pretty much only) way in which Ubuntu machines get hacked.  You should not just turn it off - you should uninstall it. It is evil.
Seriously! I have no bloody idea why Ubuntu even ships with vino installed by default.

It looks like it is under "desktop sharing" but if you search for vino it pops up.

---

