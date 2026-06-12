---
title: "Issue connecting to VPN - VPN service failed to start"
date: 2017-02-12
forum: Server Platforms
---

### Post by andrewgt6 on 2017-02-12
Brand new install of Ubuntu 16.04 LTS - I added a VPN connection but I keep getting this error when trying to connect to it:

"The VPN Connection 'VPN Connection 1' failed because the VPN service failed to start"

Any advice? 

Thank you.

---

### Post by bearlake on 2017-02-12
Hi and welcome,

How did you install it?

Can you post the service you are using?

---

### Post by wildmanne39 on 2017-02-12
*Thread moved to **Server Platforms**.*

---

### Post by andrewgt6 on 2017-02-12
How did I install Ubuntu? I installed it via an .iso on a USB. I followed the steps by my VPN provider here: [https://support.ivacy.com/kb/how-to-setup-ivacy-pptp-protocol-manually-on-ubuntu/](https://support.ivacy.com/kb/how-to-setup-ivacy-pptp-protocol-manually-on-ubuntu/)

---

### Post by bearlake on 2017-02-12
Which Gateway did you select? Is it on the list [here]("https://support.ivacy.com/kb/vpn-servers/")?

If it isn't, select one from the list and try it again.

I haven't used PPTP in years. It can be hacked very easily.

---

### Post by andrewgt6 on 2017-02-12
I used a gateway on their list, usla1.dns2use.com. PPTP is the only option I have with Ubuntu. I would try OpenVPN but I can't find instructions for Ubuntu.

---

### Post by darkod on 2017-02-12
Did you contact the provider to ask them? Because after all, the instructions are created by them and it might be something on their end.

Also look at the logs for example /var/log/syslog to see if there are any error messages when trying to connect.

Using OpenVPN is very easy but in this case you will have to ask the provider if they are set up to use openvpn and in such case they can probably help you sending you the .conf file you need to use for their service. Using openvpn on the client side is as easy as installing the package and putting the correct .conf file in /etc/openvpn. So it all comes down to having the file/instructions from them.

---

### Post by 2105harryjones on 2017-07-28
[COLOR=#000000][FONT=Arial]I faced this problem before and tried to solve it long time. I read a lot about it but I found help on [/FONT][/COLOR][https://www.bestvpnrating.com/how-set-vpn](https://www.bestvpnrating.com/how-set-vpn)[COLOR=#000000][FONT=Arial] and it started working. It may be that you missed or did something wrong when you followed steps and didn't notice it. It can be really simple[/FONT][/COLOR]

---

