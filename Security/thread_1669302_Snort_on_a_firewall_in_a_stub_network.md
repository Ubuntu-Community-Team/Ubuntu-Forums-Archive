---
title: "Snort on a firewall in a stub network"
date: 2011-01-17
forum: Security
---

### Post by crashed111 on 2011-01-17
Hi all

I was wondering what everyones views were on running SNORT on a Firewall  on a stub network (basically a network with only one exit point such as  a home network connecting to the Internet). 

From what I gather there is the possibility of performance issues but  for now that does not bother me I am more interested in the security  implications. 

From what I gather there is no implications running SNORT on a firewall  in daemon mode listening on the external interface on a stub network  except if the firewall gets compromised the interface is in promiscuous  mode so it gives the attacker that tool. I was wondering if anyone else  had any views?

I want to put one on a small office network where running a separate box for snort really does not make sense. 

Thanks for your help

---

### Post by bodhi.zazen on 2011-01-17
A better question is what do you want to use snort for ?

Is there a reason you want to capture all traffic ? 

Usually I put as little as possible on the firewall, and snort on the inside as I am not concerned with all the traffic the firewall sees, only what it passes.

---

### Post by crashed111 on 2011-01-19
Hi 

Thanks four your reply. In the same situation as you I only want to capture traffic that passes through the Firewall. I know it is best to keep it separate but this is for a small network.

All I want to do with SNORT is check for is any possible intrusions on the LAN.

---

### Post by bodhi.zazen on 2011-01-19
IMO you want as little as possible running on your firewall.

The more applications you install the more vulnerabilities you introduce.

There are several ways you can run snort behind your firewall, or you can run several snort sensors with a central database.

Alternately you can get switches with a monitoring post ;)

---

### Post by Erixcode on 2011-10-18
HI
would u please tell me what is thoes several ways? or give me any docs! thanks in advance :):)

---

### Post by bodhi.zazen on 2011-10-18
> **Erixcode said:**
> HI
would u please tell me what is thoes several ways? or give me any docs! thanks in advance :):)

Seeme your google is broken

[http://www.snort.org/start/documentation](http://www.snort.org/start/documentation)

---

