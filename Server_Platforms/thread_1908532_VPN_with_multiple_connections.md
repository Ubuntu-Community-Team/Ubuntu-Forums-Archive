---
title: "VPN with multiple connections"
date: 2012-01-13
forum: Server Platforms
---

### Post by neoroses on 2012-01-13
Hey guys, im setting up a really simple little server for a local company, i got it all working using windows xp, but i have been crippled by its stupid limitation of only allowing one vpn connection at a time. the person who owns the bussiness (and i dont blame her) doesnt want to spend £££ on the server edition of windoze. iv been a ubuntu user for years but had no experiance with the server side of it. so to cut a long story short i just want to know if the ubuntu server edition will allow more than one vpn connection, and can windoz boxes connect to it fairly simply? would be great if i could get the business using ubuntu accross the board lol.

Cheers guys. Peace

---

### Post by spynappels on 2012-01-13
Yes it is very simple using OpenVPN, depends on what you are using the server to do though. Clients are available for Windows and Mac and Network Manager can connect from inside Ubuntu Desktop.

Have a search for OpenVPN.

---

### Post by neoroses on 2012-01-13
heyup mate thanks forgetting back to me. i had a look into openvpn as a way around it for windows but i was unsure as to howto get a openVPN server running. All the server has to do is be on and share its files in real time, no use sync'ing it has to be able to open the folders in a windows and use them as if it were on the client computer. the reason for this is i have access database that is split in the the FE and BE and i need people to be able to map a network drive containing the BE.

So yea do i need a openvpn server application or does a openvnp client just connect to ubuntu server edition....?

cheers man, hope im making sence lol :)

---

### Post by dirtrider1 on 2012-01-14
I don't quite understand your question but there is actually a few good solutions using Ubuntu but I also recommend Openvpn. I don't know what kind of VPN your using but Openvpn is available in the repos and is very robust, it creates either a routed (point to point link) or a virtual Ethernet bridge connection. Basically it will allow you to securely connect into your private network from that point on you may push any service you wish through the vpn, Samba will allow you to share and mount files with Windows computers.

The Openvpn server application is installed through the Ubuntu repositories and there is also a free Windows client available online as well.

Check out the Openvpn Documentation - [http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

---

### Post by neoroses on 2012-01-14
I think that thats what im looking for really. i just thought you had to pay for openvpn server side. :) would i even need to bother with ubuntu server edition as its such a simple little network? and my god im sorry to ask this but as a very last resort can you get a openvpn server for doze? thanks for your help guys. Peace out.

---

### Post by SeijiSensei on 2012-01-14
If you've been using Windows-to-Windows VPNs I'm guessing your server uses Microsoft's PPTP protocol to handle these.  If the clients are already configured to use PPTP, then you might just try installing [pptpd]("http://manpages.ubuntu.com/manpages/lucid/man8/pptpd.8.html") on Ubuntu instead.  There are no limitations to the number of concurrent sessions.

---

### Post by neoroses on 2012-01-15
nice one bro ill give that a go :) then windows can connect stright to my ubuntu box? :) brill

---

### Post by SeijiSensei on 2012-01-15
> **neoroses said:**
> nice one bro ill give that a go :) then windows can connect stright to my ubuntu box? :) brill

Just be aware that PPTP is considerably [less secure]("http://www.ivpn.net/knowledgebase/62/PPTP-vs-L2TP-vs-OpenVPN.html") than OpenVPN.

---

