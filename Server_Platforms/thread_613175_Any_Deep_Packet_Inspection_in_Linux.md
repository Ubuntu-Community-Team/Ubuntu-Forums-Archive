---
title: "Any Deep Packet Inspection in Linux?"
date: 2007-11-14
forum: Server Platforms
---

### Post by netlogic on 2007-11-14
Any free solution for DI (Deep Inspection) firewall or routers available for Linux?  Are there any plans for DI focus functions appear to the future IPTABLES? I know there are tools for most prevalent static internet protocol such as  HTTP, SMTP, IMAP, POP, FTP, and DNS, but we live in time, we need to go beyond them. I know there are products like Procera and Ellacoya, but there must be a free and open source solution to this problem, so things can be deployed faster based on the tech knowledge, not deep pockets.

---

### Post by HermanAB on 2007-11-14
If you compile the kernel, netfilter and iptables from source, then you can have many more features.

Cheers,

H.

---

### Post by netlogic on 2007-11-14
Hello again, but I wasn't taking about Statesful Inspection. I was talking about Deep Packet Inspection. When the did the current kernel added this feature? I wasn't aware.   DPI looks at Layer 2 through Layer 7. Routing and shaping  based on the port numbers are obsolete now.

---

### Post by HermanAB on 2007-11-15
There are lots of fancy features in netfilter and iptables that are not enabled in standard distros.  Visit the iptables web site and have a look around.

Cheers,

H.

---

### Post by MJN on 2007-11-15
As HermanAB says, iptables by virtue of its extensible nature may at least enable part way, if not all, of what you want to achieve. Iptables can inspect the full stack through the string match extension.

Check out the [Snort IDS](http://www.snort.org/) if you're not already familiar with it as you can convert Snort rules (loads of free ones available via a Google search) using [fwsnort](http://www.cipherdyne.com/fwsnort/) into suitable rules for iptables to use.

DPI is an area where, by virtue of its scale and power, requires a considerable amount of work to do properly which is why it is largely the preserve of commercial solutions and more general dedicated hardware devices.

Hope this helps, if only as food for thought and something to experiment with to achieve your goal.

Mathew

---

### Post by netlogic on 2007-11-15
I always thought Snort was a pattern based. I didn't knew it actually looks at the headers of the packets. Are you saying, it is possible to look into the headers to slow down certain traffics? That's interesting. I didn't know it was possible with the iptables with snort. Thanks for the information.

---

### Post by MJN on 2007-11-15
To clarify, you wouldn't actually be using Snort but rather the rules (converted) *from* Snort. Given the string match method the difficulty is in defining the right rules to correctly identify the traffic you're looking for but that's where utilising the work that's already underway for feeding Snort is going to be one less wheel for you to invent.

You could indeed use this technique to slow traffic down based on its type (*true* type as you've discussed rather than assuming web traffic, for example, would always be on a particular port).

I'm no expert in this area, indeed I have next to no practical experience in it, so it would be interesting to hear what you manage to achieve should you decide to take it further as I'm sure it'd be of general interest (it might be a solution looking for a problem for a lot of people although perhaps, like you touched on, traffic shaping of shared Internet connections is one obvious use that may be applicable).

Mathew

---

### Post by sciurus on 2007-11-22
[http://l7-filter.sourceforge.net/](http://l7-filter.sourceforge.net/)

---

