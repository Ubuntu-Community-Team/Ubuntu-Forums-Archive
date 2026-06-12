---
title: "Logging Internet use"
date: 2010-12-24
forum: Security
---

### Post by Toolah on 2010-12-24
G'Day all,

Am new to Ubuntu, though I have been futzing with linux for a while now.

My twin Godsons have just started high school and for Christmas (tomorrow =/) I wish to give them a pair of old Thinkpad T43 laptops (rescued out of a bin believe it or not) on which I have installed Xubuntu 10.10.

These are going to be two stand along laptops connecting to a wireless modem/router at my mates place, so I am unable (and friend unwilling) to configure another computer to act as a conventional proxy / web filtering box between the users computer and firewall to monitor their Internet use.

What I would like to do is configure a way to log their web use and have that emailed to their parents once a week.  How would I do this in a way that is not easily thwarted please?

Mick

---

### Post by iponeverything on 2010-12-24
I think you can get usage reports if you sign up for OpenDNS.

Put the OpenDNS servers in /etc/resolv.conf and set the immutable flag on it.

---

