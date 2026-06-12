---
title: "dynamic DNS with multiple virtual domains"
date: 2006-03-06
forum: Server Platforms
---

### Post by VinceDee on 2006-03-06
I'm on cable internet and, although my DNS is technically considered dynamic, my current IP address has remained unchanged for the last 8 months (which has allowed me to set up a web server without having to deal with a constantly changing IP address). Problem is, I recently got a email warning from Comcast that they are going to start changing IP addresses more frequently, and soon, so I want to go ahead and configure my server to deal with the situation. 

So far, I think I understand how to use a service like zoneedit or dyndns to point a single domain name (like mydomain1.com) to my server using ddclient (or some similar program) to automatically update it. What I don't understand is how to get *multiple* domains pointing to that same server (since I'm virtual hosting).  Would I have to set up a new domain "pointer" for each domain name, or is there some way that I just set up one pointer for the entire server and it takes care of all the domains?

---

### Post by Horndog on 2006-03-06
Each domain name has to be represented in your dynamic DNS script for all the domains to be updated when your dynamic IP changes. That' how mine is done with five.

---

### Post by jinacio on 2006-03-07
just add more domains to your dyndns account, reconfigure ddclient (wich detects all of them), and select you want to update all.

---

