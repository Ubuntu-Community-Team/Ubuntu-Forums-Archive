---
title: "Which router/firewall do you use ?"
date: 2018-04-23
forum: The Cafe
---

### Post by linuxyogi on 2018-04-23
Hi,I have started using pfsense and I must say its a great product.Which router/firewall do you use ?

---

### Post by wyliecoyoteuk on 2018-04-23
OPNsense, a fork of PFsense.

---

### Post by sevendogsbsd on 2018-04-23
Pfsense appliance - bought from the PFsense folks, works great. A bit pricey but does what I need it to.

---

### Post by thenailedone on 2018-04-23
I am to much of a pleb to run anything than the stock firmware on the router I purchased. Windows does have a built in firewall right? :confused:

---

### Post by CharlesA on 2018-04-23
EdgeRouter Lite here. Because reasons.

---

### Post by linuxyogi on 2018-04-23
> **thenailedone said:**
> I am to much of a pleb to run anything than the stock firmware on the router I purchased. Windows does have a built in firewall right? :confused:Search your router here >>> [https://www.cvedetails.com/ ](https://www.cvedetails.com/ )  You may get an idea how secure or insecure it is. I trust Ubuntu's firewall (ufw) but not WIndows firewall.

---

### Post by Irihapeti on 2018-04-23
Bog-standard Ubuntu server 16.04 on a small single-board machine. So that I can keep it updated.

---

### Post by 1clue on 2018-04-24
> **linuxyogi said:**
> Search your router here >>> [https://www.cvedetails.com/ ]("https://www.cvedetails.com/")  You may get an idea how secure or insecure it is. I trust Ubuntu's firewall (ufw) but not WIndows firewall.

Not sure if I like that site. It's very easy to get the wrong impression. For example, I have a router of a common brand which is not listed in that site, so does it have a cve or not, or is it just unknown to the site? As well it doesn't list CVE per version of the firmware.

Likewise the Linux router has literally thousands of CVEs but if you're up to date then likely very few actually apply to you, and you don't know their severity.

I use multiple routers, depending on the site. Commercial cisco gear, linksys and linux router, one or more of each. I've tried half-heartedly to configure pfSense but failed.

---

### Post by linuxyogi on 2018-04-25
> **1clue said:**
> Not sure if I like that site. It's very easy to get the wrong impression. For example, I have a router of a common brand which is not listed in that site, so does it have a cve or not, or is it just unknown to the site? As well it doesn't list CVE per version of the firmware.Likewise the Linux router has literally thousands of CVEs but if you're up to date then likely very few actually apply to you, and you don't know their severity.I use multiple routers, depending on the site. Commercial cisco gear, linksys and linux router, one or more of each. I've tried half-heartedly to configure pfSense but failed.This is the the details of my old router which I now use only as an access point >>>> [https://www.cvedetails.com/vulnerability-list/vendor_id-899/product_id-31624/version_id-182671/D-link-Dir-600l-Firmware-2.05.htmlIf](https://www.cvedetails.com/vulnerability-list/vendor_id-899/product_id-31624/version_id-182671/D-link-Dir-600l-Firmware-2.05.htmlIf)  If you keep your routers updated with the security patches I don't think there is a problem. Sorry to hear that you had problems configuring pfsense. If a newbie like me can do it you can do it too. May be try once more ?Instead of searching on that site go to Google and type "YOUR ROUTER NAME cve"

---

### Post by 1clue on 2018-04-25
I've been following security notices for decades. I don't like 'summary' sites like the one you posted. It's better to search for your specific hardware and firmware, and then an understanding of how the CVE database is built and maintained helps prevent unpleasant surprises.

---

### Post by wyliecoyoteuk on 2018-04-25
Pfsense is the root version of OPNsense.
The OPNsense fork is much more dynamic, for a small business network, it is superb.

---

### Post by walkeramanda00 on 2018-05-12
i don't know

---

### Post by aircon2 on 2018-05-12
BT Infinity/Norton 265

---

