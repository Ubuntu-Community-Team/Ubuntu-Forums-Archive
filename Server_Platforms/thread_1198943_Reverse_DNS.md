---
title: "Reverse DNS"
date: 2009-06-28
forum: Server Platforms
---

### Post by drhiii on 2009-06-28
I need to set the PTR or reverse DNS record for an IP, somewhere.

The server in question resides under a Qwest business account.  It has a small mail server running on it.

The primary and secondary DNS resides under a Comcast Business account, elsewhere of course.

Can I set the PTR record within the DNS server on Comcast (using Webmin)?  

Or where do I need to set the PTR record, with whom?  With Qwest, or Comtas, or????

Am trying to learn DNS, but this one has me confused.  

Help?

---

### Post by Xipher on 2009-06-28
You will have to speak with the ISP providing you the IP address. Reverse DNS records are delegated by the regional registry (ARIN in this case) to the ISP the address space is allocated to. It's unlikely they will subdelegate the reverse DNS for one IP though, and you will probably have to provide then with the hostname to change it to instead.

---

### Post by drhiii on 2009-06-29
> **Xipher said:**
> You will have to speak with the ISP providing you the IP address. Reverse DNS records are delegated by the regional registry (ARIN in this case) to the ISP the address space is allocated to. It's unlikely they will subdelegate the reverse DNS for one IP though, and you will probably have to provide then with the hostname to change it to instead.

Hello, and thank you for your response.  This helps unravel the logic behind what must be done.  Not having done this before, well, I needed help.

Thank you again.  It is much appreciated, and I only need to be taught once.  And will also pass it on.

---

