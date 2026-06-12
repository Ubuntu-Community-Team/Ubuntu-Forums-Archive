---
title: "PPTP security"
date: 2012-06-08
forum: Security
---

### Post by wlraider70 on 2012-06-08
Hello,

I have read that pptp has some security flaws? Is this true?
I have a small church with a lot of old PCs and new tablets, PPTP seems like the easiest and most versatile. 

Is it possible to secure PPTP?

---

### Post by wacky_sung on 2012-06-09
[http://www.ivpn.net/knowledgebase/62/PPTP-vs-L2TP-vs-OpenVPN.html](http://www.ivpn.net/knowledgebase/62/PPTP-vs-L2TP-vs-OpenVPN.html)

[http://vpnblog.info/pptp-vs-l2tp.html](http://vpnblog.info/pptp-vs-l2tp.html)

---

### Post by Ms. Daisy on 2012-06-09
Is this a windows network?

Here's a website that answers your question very thoroughly (but is probably WAY more than you care about)
[http://www.sans.org/security-resources/malwarefaq/pptp-vpn.php](http://www.sans.org/security-resources/malwarefaq/pptp-vpn.php)

---

### Post by wlraider70 on 2012-06-11
The network has windows clients, but the server structure is all linux.

Can anyone recommend a L2TP guide? There was an iOS bug once upon a time there.

---

### Post by Ms. Daisy on 2012-06-11
Not a guide but a comparison of PPTP, L2TP and VPN:
 
[http://www.ivpn.net/knowledgebase/62/PPTP-vs-L2TP-vs-OpenVPN.html](http://www.ivpn.net/knowledgebase/62/PPTP-vs-L2TP-vs-OpenVPN.html)
 
Is there a reason you're avoiding VPN?

---

### Post by wlraider70 on 2012-06-11
The lack of IOS Compatibility.

---

### Post by wacky_sung on 2012-06-12
> **Ms. Daisy said:**
> Not a guide but a comparison of PPTP, L2TP and VPN:
 
[http://www.ivpn.net/knowledgebase/62/PPTP-vs-L2TP-vs-OpenVPN.html](http://www.ivpn.net/knowledgebase/62/PPTP-vs-L2TP-vs-OpenVPN.html)
 
Is there a reason you're avoiding VPN?

The user is asking for security but not guide.

---

### Post by Lars Noodén on 2012-06-12
The short answer is "not really" for PPTP

[http://www.vpnc.org/vpn-standards.html](http://www.vpnc.org/vpn-standards.html)

For secure VPN connections you choices are IPsec with encryption, L2TP inside of IPsec, or SSL with encryption.

---

### Post by wacky_sung on 2012-06-14
Lately Openvpn site get defaced. 

[http://zerosecurity.org/security/openvpn-hacked-and-defaced/]("http://zerosecurity.org/security/openvpn-hacked-and-defaced/")

---

