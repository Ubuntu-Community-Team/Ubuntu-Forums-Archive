---
title: "Problem with DNS (bind9) and Hulu Plus (PS3)"
date: 2011-11-21
forum: Server Platforms
---

### Post by jlacroix on 2011-11-21
Now that DNS is actually working and resolving, I'm having a problem with Hulu on my PS3. I set up DHCP (which I got working without a hitch) and had my PS3 get a new IP address and got it connected. Now, Hulu movies skip. This only happens when using the DNS server I set up earlier. 

I had this same problem with dnsmasq, which I was playing around with a few months ago. At that time, I just assumed that dnsmasq was the problem and didn't think about it. Also, with dnsmasq I had an issue with wireless computers getting an IP address, but I hope I don't have that problem too.

Anyone know why using bind9 would cause Hulu to stutter and intermittently freeze? I did check to see if the server was under too much load, but it wasn't.

---

### Post by jlacroix on 2011-11-21
False alarm. It is acting that way without bind9 as well, so I guess it's just a coincidence. Even stranger, upon further inspection, it's specifically Terra Nova that has the problem. Sorry for the false alarm guys!

---

