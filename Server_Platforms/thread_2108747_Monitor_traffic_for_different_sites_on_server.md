---
title: "Monitor traffic for different sites on server"
date: 2013-01-25
forum: Server Platforms
---

### Post by bigmonmulgrew on 2013-01-25
HI guys
I have a ubuntu 12.04 LAMP web server 

I have more than one website running. Is there a way to tell how much bandwidth each is using.

---

### Post by SeijiSensei on 2013-01-25
If you have each virtual host log requests to a separate file, you could then run a website statistics generator for each site.  I use [analog]("http://www.analog.cx/") for that task, but there are others.  Analog itself is in the Ubuntu repositories.

Alternatively, you could write a script which parses each access log and sums up the size of the transfers.  The last field in a transfer log entry gives the total number of bytes transferred.  If you have a lot of sites and want to generate monthly totals, this is probably the best bet.  In bash, you can have the script extract last month's entries with grep, use awk to pull off the bytes-transferred field, and then sum them up with expr.  A Perl or PHP script might be easier if you're more comfortable with those languages.

---

