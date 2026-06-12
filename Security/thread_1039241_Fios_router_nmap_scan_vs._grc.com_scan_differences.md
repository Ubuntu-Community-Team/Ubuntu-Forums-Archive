---
title: "Fios router nmap scan vs. grc.com scan differences?"
date: 2009-01-14
forum: Security
---

### Post by lotuseclat79 on 2009-01-14
I recently ugraded to Verizon FiOS, and have made some internal changes to the ActionTec MI424WR Rev D router according to it documentation.

No Remote Administration box is checked.  Fragmented packets are disallowed - i.e. I am not using VPN at this point and I understand that there are some legitimate uses of fragmented packets with various VPN services.  uPnP is turned off.

Ok, so the grc.com tests show that all ports: 0-1055 are stealthed, and that port 4567 is open (I know how to turn it off, but have not yet done so).

When I run zenmap/nmap 4.76 version, against the router's ip address, I get the following ports open: 23, 80, 443, 992, 4567, 8080, 8443.  The latest repository version of zenmap/nmap does not show port 4567 at all - I assume that is a deficiency which needs upgrading to version 4.76.

Does this reflect a bug/problem in nmap 4.76, or some funky firewall rules in the FiOS router, or what?

Why would nmap show the non-4567 ports open when grc.com and the lack of Remote Administration says they are stealthed?  Could it possibly be a difference in the way nmap executes the test from insecure.org vs the way that grc.com executes the test from that website?

What are your thoughts on this issue?

-- Tom

---

### Post by rickyjones on 2009-01-14
> **lotuseclat79 said:**
> I recently ugraded to Verizon FiOS, and have made some internal changes to the ActionTec MI424WR Rev D router according to it documentation.

No Remote Administration box is checked.  Fragmented packets are disallowed - i.e. I am not using VPN at this point and I understand that there are some legitimate uses of fragmented packets with various VPN services.  uPnP is turned off.

Ok, so the grc.com tests show that all ports: 0-1055 are stealthed, and that port 4567 is open (I know how to turn it off, but have not yet done so).

When I run zenmap/nmap 4.76 version, against the router's ip address, I get the following ports open: 23, 80, 443, 992, 4567, 8080, 8443.  The latest repository version of zenmap/nmap does not show port 4567 at all - I assume that is a deficiency which needs upgrading to version 4.76.

Does this reflect a bug/problem in nmap 4.76, or some funky firewall rules in the FiOS router, or what?

Why would nmap show the non-4567 ports open when grc.com and the lack of Remote Administration says they are stealthed?  Could it possibly be a difference in the way nmap executes the test from insecure.org vs the way that grc.com executes the test from that website?

What are your thoughts on this issue?

-- Tom

Where is the NMAP scan coming from? If it is coming from inside the network then those would be open ports on the inside. If the scan is coming from the WAN then I'm not sure why the results would be so skewed.

Thanks,
Richard

---

### Post by lotuseclat79 on 2009-01-14
> **rickyjones said:**
> Where is the NMAP scan coming from? If it is coming from inside the network then those would be open ports on the inside. If the scan is coming from the WAN then I'm not sure why the results would be so skewed.

Thanks,
Richard
Hi Richard,

I reran a test from the WAN at nmap-online.com, and only port 4567 showed open, so the difference must have been as you said between running the scan from my computer (inside) vs. outside the WAN.

Thanks,

-- Tom

---

### Post by rickyjones on 2009-01-14
> **lotuseclat79 said:**
> Hi Richard,

I reran a test from the WAN at nmap-online.com, and only port 4567 showed open, so the difference must have been as you said between running the scan from my computer (inside) vs. outside the WAN.

Thanks,

-- Tom

No problem. I'm glad you got it figured it out!

Thanks,
Richard

---

