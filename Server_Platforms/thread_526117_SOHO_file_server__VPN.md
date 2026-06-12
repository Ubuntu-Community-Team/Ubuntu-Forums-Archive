---
title: "SOHO file server / VPN"
date: 2007-08-15
forum: Server Platforms
---

### Post by jdbg on 2007-08-15
Hi,

I've looked around the forums, but couldn't find the info I need.

I'm looking on building a SOHO server for friends of mine. They have two offices (two different physical locations). I managed to setup Ubuntu, put the Samba share of folders in one of the office and this works almost fine. However, I need to set it in such a fashion, so that the server is accessible to users from the other office in a way as if they are in one office.

I know this is VPN, but I have no idea how to set it up. Please help.

---

### Post by koenn on 2007-08-15
you're correct that VPN is e very good sollution for what you have in mind. You can use OpenVPN, which is in the ubuntu repo's (universe, i think). 
This should get you started : 

[http://openvpn.net/howto.html](http://openvpn.net/howto.html)
[http://www.techimo.com/forum/t176687.html](http://www.techimo.com/forum/t176687.html)
[http://www.thebakershome.net/?q=node/56](http://www.thebakershome.net/?q=node/56)

You're gonna want to do this right, because if you mess up, it won't work, or only work sometimes,  or worse : it will work but be insecure. So I suggest you bowse the openvpn howto to get your bearings and an overall understanding of what you're getting yourself in for, then refer to the 2 other howtos for inspiration on how to actually getting a working sollution (keeping in mind that those people's sollution is not necessarily the best sollution to *your* problem.

Have fun.

---

### Post by jdbg on 2007-08-15
Thanks koenn!

I've never dealt with VPN before and this is the challenge.
I'll look throught the links and most probably I'll be asking stuff again soon ;)

---

### Post by jdbg on 2007-08-15
Ah, just one thing - my server is behind an router. Does this makes any difference?

---

### Post by koenn on 2007-08-15
If your router is a linux pc you've set up as a router, the logical sollution would be to set it up as the vpn gaterway at  your end. 

But probably you mean a dsl router of some sort - if it does NAT and/or firewalling, it should at least be  configurable to allow /forward incoming traffic on the udp port openvpn uses (check the manual, i forgot the port number). 
here's a quick intro to NAT; you may have to set up "port forwarding"
[http://users.telenet.be/mydotcom/library/network/nat.htm](http://users.telenet.be/mydotcom/library/network/nat.htm)

---

### Post by jdbg on 2007-08-15
Yes, it's an ASUS router. 

10x for the help!

---

### Post by koenn on 2007-08-15
y're welcome. 
Enjoy.

---

