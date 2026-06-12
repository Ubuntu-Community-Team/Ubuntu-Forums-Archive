---
title: "Should I be concerned?"
date: 2008-02-19
forum: The Cafe
---

### Post by billgoldberg on 2008-02-19
When doing the test on privacy.net/analyze

It says:

Firewall Test

The following ports were checked: 554, 1755, 443, 80
Out of the above ports, the following are open and permitting outbound traffic: 554,1755,443,80

Firewall status: NOT PRESENT (you may have a firewall, but it is not configured to block these ports from outbound traffic)

Also how do I prevent epiphany to send info about itself and the OS I use?

---

### Post by Het Irv on 2008-02-19
I know that 80 is defaul Internet port.

Here is a good site for the rest, [http://www.cirt.net/cgi-bin/ports.pl]("http://www.cirt.net/cgi-bin/ports.pl")

---

### Post by macogw on 2008-02-20
You can use Firestarter to configure the firewall (iptables) to block all outgoing traffic by default and then open outbound ports as needed to function.  This is called whitelisting.

No inbound ports are open by default.  They only open when you start up a service, like SSH, and then only that service's port opens for inbound traffic.

You can't be hacked into unless you have inbound ports open.  Outbound ports just mean that if you already have been hacked and whatever's on there is "phoning home," nothing's stopping it from phoning home.  If you've been hacked, though, it's not like they can't just go back in and re-open the ports anyway, so it doesn't really matter much.  Once they're in, you're screwed anyway.  I mean, yeah, you can change passwords and whatnot, but if they've got a keylogger, they've got the passwords anyway.  So, again, once they're in, you're screwed.

---

