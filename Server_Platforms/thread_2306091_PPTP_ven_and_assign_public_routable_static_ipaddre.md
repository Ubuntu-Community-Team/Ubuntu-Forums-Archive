---
title: "PPTP ven and assign public routable static ipaddress"
date: 2015-12-12
forum: Server Platforms
---

### Post by ShapeShiftme on 2015-12-12
Hi All

I have a server with a ISP. that server has 8 public ipaddresses.
i would like to do a PPTP vpn and have one of thoose ip addresses assigned to the client connection.

So i can forward al traffic to them directly.

A similar public service would be [www.unblockvpn.com](www.unblockvpn.com)

There are alow of tutorials on how to setup a pptp server but not on how to give it a public ipaddress.

And help would be awesome.

---

### Post by TheFu on 2015-12-12
Cannot help iwth this specific issue without lots more information about your network.

PPTP has been hacked lots of times (search "pptp hacked" to see). If you care about security, don't use it. Use IPSec or L2TP or openVPN.  Even Microsoft says you shouldn't use pptp.  [https://www.schneier.com/cryptography/pptp/faq.html](https://www.schneier.com/cryptography/pptp/faq.html)

---

### Post by ShapeShiftme on 2015-12-12
For what i need scurity is not a big issue. the stuff im doing over the vpn is encypted anyway https and ssh. but ok i wont use it.
does any one know howto do it over openvpn or l2tp.

If you nee more info on the network let me know what type of info you need.
But what i have so far it rhat i have a xxx.xxx.xxx.xxx/28 range of ip allocated to me.

Any help would be awesome

---

