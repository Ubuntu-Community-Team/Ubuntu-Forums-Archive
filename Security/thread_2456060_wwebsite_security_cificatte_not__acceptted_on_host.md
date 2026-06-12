---
title: "wwebsite security cificatte not  acceptted on hosting compuutter"
date: 2021-01-03
forum: Security
---

### Post by astarmathsandphysics on 2021-01-03
I have an ubuntu server hosting some websitess. All of the websites use cloudflare. I have no problem viewwing the websites from another compuuter, but on the hosting compputer, I get anerrror mesage telling me the security certficate is invlid. Further inveesttigation tells me the ceertificate passef to the browers iss "ubuntu,pemm", whiich I havee nevr generrted nand ccannot find.. I have examined all my apaache2 filess and all seem coorrectt annd the coct certifiicatees are there andd are accesseed by external xccomputers.

Can someeone giive mme a hint?

jusstto be clear: asstarmathsandphssics.com iss visible froom outside, but no visibile on the server hossting it.., becuase, I am toldd, the scurity certificcatt "ubuntu" i sself signedd, so invalid.

---

### Post by CharlesA on 2021-01-05
Hi,

Cloudflare can do SSL for you rather than present the certificate you have configured on your site. See here: [https://www.cloudflare.com/ssl/](https://www.cloudflare.com/ssl/)

You can verify this by viewing the certificate in the browser when accessing the domain externally and see who signed it.

If you want to use a non-self signed certificate on the server itself, you can look into using Lets Encrypt with [certbot]("https://certbot.eff.org/") to generate a certificate for you.

---

### Post by astarmathsandphysics on 2021-01-08
Am using cloudflare certificate, which was working for years.I had a broken leg and spent months away from my server. When I got down to work again I had this problem, which only shows up on the hosting server. Upfating does not cure it.

---

### Post by TheFu on 2021-01-08
> **astarmathsandphysics said:**
> Am using cloudflare certificate, which was working for years.I had a broken leg and spent months away from my server. When I got down to work again I had this problem, which only shows up on the hosting server. Upfating does not cure it.

So ... does the FQDN resolve to the cloudflare service or the local machine?  My guess is that one has the current cert. The other does not.

---

### Post by astarmathsandphysics on 2021-01-09
updating ubuntu now.  Will check fqdn as soon as I am done.

---

