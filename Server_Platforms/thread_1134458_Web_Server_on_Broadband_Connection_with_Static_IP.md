---
title: "Web Server on Broadband Connection with Static IP"
date: 2009-04-23
forum: Server Platforms
---

### Post by martin1977 on 2009-04-23
I have a web server in my home/office running Ubuntu 8.04 LTS.  It is on a Static IP address (86.*.*.*) provided by NTL Telewest Business, connected to the DMZ side of a Billion BiGuard S5 (pass-through).

This morning I lost the Internet connection (and hence my website and e-mail), although the broadband connection through the router was fine (on a WAN DHCP address).

My reason for posting is to let other 'enthusiasts' having problems setting up equipment on a Static IP address know how I solved the problem, which turned out to be an incorrect Default Gateway address.

To configure the network card, eth0 in this case, three pieces of information are needed:

[LIST]
[*]IP Address
[*]Subnet Mask
[*]Default Gateway
[/LIST]

The Static IP Address is given by the broadband provider, but they offered no assistance with the other two.

I worked out that the subnet mask was 255.255.252.0, I think guessing that it was the same as for the DHCP WAN address.  The problem was determining the correct Default Gateway address.

The solution is that there are calculators available to help with this such as:

[http://online-nettools.com/subnet_calculator](http://online-nettools.com/subnet_calculator)

It seems I had one digit wrong, which does not explain adequately why the connection had worked for 3 months and suddenly died this morning!

Anyway, working again now and I hope this helps others.

Regards,

Martin

PS. For anyone considering running a light use web/email server behind a Broadband connection, consider also a 'cheap' VPS alternative.  We have both - with remote primary and secondary DNS (Gradwell) allowing sites to be switched between the home/office server and the VPS if problems occur.  The main problem with the home/office server is what do you do if it goes down when you are on holiday?  With the VPS you have a control panel which you can access from an Internet cafe or Wireless/3G connection to sort out any problems.

---

