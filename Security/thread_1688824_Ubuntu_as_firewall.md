---
title: "Ubuntu as firewall"
date: 2011-02-15
forum: Security
---

### Post by seastick on 2011-02-15
Is it possible (sensible) to use Ubuntu as a firewall.  And if so is it possible to use it to limit the time a certain machine spends connected to a specific website?  Or are there tools that would be more appropriate.  Any suggestions gratefully received.

---

### Post by PapaNerd on 2011-02-15
In general, no system (unix, Mac, windows, etc.) should ever be a firewall for itself.  Any server that is configured as a firewall guarding an Internet connection should be limited to only that function, and with other services removed.  Hardware firewalls (as in dedicated gear) are more effective at preventing intrusions because they are quite dumb by comparison to everything a computer can do.

---

### Post by handy on 2011-02-16
I use a cheap as chips PIII as a 24/7 firewall/router. It runs IPCop which is very mature & specialised for its job. It costs me a little over $50-/year in electricity last time I checked.

An ADSL modem/router is really all that anyone needs for protection these days except in certain server situations or if they are just interested in playing around with the software technology.

You may pick up an increase in internet speed using a Linux based router as opposed to all of the Windows centric firmware out there that runs the standard home modem/routers. You also may not.

For standard home usage a Ubuntu install using a standard ADSL modem/router is more than enough to keep you safe.

This is a good read:

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by seastick on 2011-02-16
Thanks for the replies.  I figured the router would provide protection.  I'm looking to have some control over what sites the children go to for how long - eg to limit time spent on facebook so that homework gets done.  If I can set up a Ubuntu machine as a firewall that would be its only purpose in life.  It would be good to get some good monitoring of web use going too - I'm used to WebMarshal in my previous job.
Any thoughts?

---

### Post by bodhi.zazen on 2011-02-16
> **seastick said:**
> Is it possible (sensible) to use Ubuntu as a firewall.

It is possible, but ill advised.

On a firewall you really want a minimal set of applications / binaries (to reduce vulnerabilities) and IMO even a minimal Ubuntu installation is too bloated for this purpose.

Use a firewall specific distro (IPCop or similar). Google search or look at distrowatch for suggestions.

If you want content control you need a proxy, such as squid or dansguardian.

---

### Post by tjwoosta on 2011-02-18
If its just restricting certain pages to certain times of the day that you want then squid should work fine for that. Its a caching proxy, but it also allows for restricting sites by various means including by time of day. 

see here
[http://www.deckle.co.za/squid-users-guide/Access_Control_and_Access_Control_Operators#Current_day.2Ftime](http://www.deckle.co.za/squid-users-guide/Access_Control_and_Access_Control_Operators#Current_day.2Ftime)

---

### Post by handy on 2011-02-19
The following may interest anyone who does or is willing to run an IPCop box:

[http://www.dageek.co.uk/ipcop/squid/index.htm](http://www.dageek.co.uk/ipcop/squid/index.htm)

---

### Post by seastick on 2011-02-28
THanks for all your help - it sounds like I can acheive all that I want to.
Now all I need to do is work out how to fit it in with my ADSL wireless router

---

