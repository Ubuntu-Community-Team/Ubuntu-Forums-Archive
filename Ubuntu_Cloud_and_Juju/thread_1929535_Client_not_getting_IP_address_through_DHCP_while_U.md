---
title: "Client not getting IP address through DHCP while UEC installation"
date: 2012-02-22
forum: Ubuntu Cloud and Juju
---

### Post by Darsana on 2012-02-22
Hi all,
I am trying to set up **Ubuntu Enterprise Cloud** using **Ubuntu 10.04**. I have installed cloud controller in a PC and node controller in another PC. I am following **Eucalyptus Beginner's Guide**, but while setting up client in another PC, client is not able to get any **IP** address (though dhcp)that needed to be provided by cluster controller. I tried ***dhcping*** the server, but it returned **no answer**. I am not able to find out how to come out of this problem. Please someone help me.
Thanks all.

---

### Post by cariboo on 2012-02-24
A Bump for the move.

---

### Post by reallykrishna on 2012-04-12
Hi Darsana,
  
While installing Client machine for UEC, If your dhcp not taking ip address automatically then, try to give manual ip. Ip should be in the same series of cc & nc.

After installing Client, follow the steps given in Eucalyptus Beginer's Guide:UEC Edition.

---

### Post by Rusty au Lait on 2012-04-24
See other post and check out [http://open.eucalyptus.com/book/export/html/1174](http://open.eucalyptus.com/book/export/html/1174)

---

