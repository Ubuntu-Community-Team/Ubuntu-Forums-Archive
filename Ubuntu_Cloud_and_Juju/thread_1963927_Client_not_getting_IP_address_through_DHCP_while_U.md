---
title: "Client not getting IP address through DHCP while UEC installation"
date: 2012-04-23
forum: Ubuntu Cloud and Juju
---

### Post by reallykrishna on 2012-04-23
Hi all,
I am trying to set up **Ubuntu Enterprise Cloud** using **Ubuntu 10.04**. I have installed cloud controller in a PC and node controller in another PC. I am following **Eucalyptus Beginner's Guide**, but while setting up client in another PC, client is not able to get any **IP** address (though dhcp)that needed to be provided by cluster controller. I tried ***dhcping*** the server, but it returned **no answer**. I am not able to find out how to come out of this problem. Please someone help me.
Thanks all.

---

### Post by Rusty au Lait on 2012-04-24
By client I am assuming you mean you want to set up a host machine that's not part of UEC or an instance and you want the DHCP server on the CLC to handle all DHCP services on your network. I also assume you are using only one internal network. Check your IPtables on the CLC. Any host outside of the UEC must be able to access the CLC's DHCP server. There is documentation on using two DHCP servers without interference.
If this sound close to your problem try this doc: [http://open.eucalyptus.com/book/export/html/1174](http://open.eucalyptus.com/book/export/html/1174)

---

