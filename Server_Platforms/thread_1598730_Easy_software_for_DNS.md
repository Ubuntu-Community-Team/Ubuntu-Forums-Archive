---
title: "Easy software for DNS"
date: 2010-10-16
forum: Server Platforms
---

### Post by joeaura7 on 2010-10-16
Does anyone know of any software that will set up a DNS server automatically? The only software I know of is bind9 and I do not want to manually create the  zones and set it up. I will be using it as a nameserver and the public ip address is for the most part static (it is actually dynamic, but does not change for years and so I treat it as a real static ip address).

---

### Post by lykwydchykyn on 2010-10-16
I'm not sure what you mean by setting up DNS "automatically"; ultimately you have to give the server some information about what it's serving up.

If you want something less complex than Bind, DNSmasque is fairly straightforward, but I don't know if it's suitable for a public-facing DNS, I've always thought of it more as a small LAN nameserver.

---

### Post by CharlesA on 2010-10-16
+1 for dnsmasq. It's great for small networks (and it's what my dd-wrt router uses)

---

### Post by joeaura7 on 2010-10-16
If DNSmasque can be used as nameserver for my website then that would be perfect. I did not know it could that. As long as I do not have to deal with records (mx, a, soa and so on), I will be happy. I curious if there is more should i check into? If not, I try this software.

---

### Post by CharlesA on 2010-10-16
Normally DNS records are dealt with by the hosting company control panel, aren't they?

---

### Post by Vegan on 2010-10-16
I use the defacto standard BIND9 for DNS services. I use it to create subdomains etc.

---

### Post by joeaura7 on 2010-10-16
Typically yes, the domain provider will allow to use their dns servers. That is how currently how it is set up, however there is an option for externel servers. Due their dns servers been flaky, I want to have the dns server inhouse so I have better control of it.

---

### Post by lykwydchykyn on 2010-10-16
> **joeaura7 said:**
> If DNSmasque can be used as nameserver for my website then that would be perfect. I did not know it could that. As long as I do not have to deal with records (mx, a, soa and so on), I will be happy. I curious if there is more should i check into? If not, I try this software.

I'm pretty sure you're always going to have to deal with records, since that's the whole point of DNS.  Maybe I don't understand what you're after, but somehow those values (which it sounds like in your case is just one IP address anyway) have to get in there.

---

### Post by Vegan on 2010-10-16
You can add lots of extra DNS servers to the BIND config so that if one craps out then all the rest are available.

Read the manual, its a bit rough but with patience it can be mastered.

---

### Post by joeaura7 on 2010-10-16
i have tried to work with bind9. i been trying to learn it. it is hard through. i got lucky with email. after trying to learn postfix, i found citadel which made it super easy. i was hoping to get lucky with dns. if i deal with records and zones no matter what, I guess I will have to study it :(

---

### Post by CharlesA on 2010-10-16
Bind is a pain in the butt, but once you get the hang of it, it isn't that bad.

---

### Post by HermanAB on 2010-10-17
Well, there is Webmin, which has a BIND wizard.  Otherwise, you have to switch to Suse or Mandriva, which have wizards for everything.

---

