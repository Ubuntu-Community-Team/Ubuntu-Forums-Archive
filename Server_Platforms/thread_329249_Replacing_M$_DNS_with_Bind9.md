---
title: "Replacing M$ DNS with Bind9"
date: 2007-01-01
forum: Server Platforms
---

### Post by jonathan.lees on 2007-01-01
Does anyone have any suggestions for replacing M$ DNS 2003 with Bind9. I have an AD domain, it works fine, but I'd like the DC to do just 2 things: Authentication and Group Policies. I setup an Ubuntu server to perform DHCP, all is ok except that the M$ DNS server doesn't pick up on any of the workstations that got their DHCP IP address from the Ubuntu server, so at a guess I need to run Bind on the Ubuntu DHCP server and Bind needs to be able to communicate with the DC.

Is this possible, or am I barking up the wrong tree and I need to move DHCP back onto the M$ 2003 DC?

thanks

---

### Post by Brazen on 2007-01-01
> **jonathan.lees said:**
> Does anyone have any suggestions for replacing M$ DNS 2003 with Bind9. I have an AD domain, it works fine, but I'd like the DC to do just 2 things: Authentication and Group Policies. I setup an Ubuntu server to perform DHCP, all is ok except that the M$ DNS server doesn't pick up on any of the workstations that got their DHCP IP address from the Ubuntu server, so at a guess I need to run Bind on the Ubuntu DHCP server and Bind needs to be able to communicate with the DC.

Is this possible, or am I barking up the wrong tree and I need to move DHCP back onto the M$ 2003 DC?

thanks

It's possible.  I think about the only special thing you have to do is enable dynamic dns.  Documentation on this is sketchy though.  It's one of the things I've looked into and would like to do myself some day.

---

### Post by StickyStyle on 2007-01-01
A DHCP server need to be 'authorized' in an AD domain before the DC's will accept updates from them, you may have to do some very manual configuration to allow ubuntu DHCP servers to update an AD DNS server.  AD DNS is tightly integrated (thats why its called 'AD integrated mode') with the AD whole system, I would make sure you fully understand how it all works before changing it.  

There is really no problem running DNS and DHCP on your DC's, so unless you have some really compelling reasons to do this project I would say your barking up the wrong tree.  If you want to start bringing ubuntu into your network, start small with samba or a jabber server.  then if your not married to exchange, drop in postfix and  and IMAP server of choice.  If you do have exchange drop a frontend postfix server to lessen the load on your exchange box.

---

### Post by jonathan.lees on 2007-01-02
thanks for the advice, back to the drawing board then.

---

