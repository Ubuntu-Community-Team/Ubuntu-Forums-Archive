---
title: "DNS Server with Captive Portal? Need Help!"
date: 2023-10-09
forum: Server Platforms
---

### Post by ohiodissident on 2023-10-09
I need to setup a recursive DNS server that will force a captive portal for anyone that uses it.  I'm not sure what software to use or how exactly to do this.  Any suggestions?  Will BIND do this?

When I connect a device to a network that has a captive portal, it says something about the network requiring a sign-in.  When I click on that, it brings me to the captive portal.  What causes this and how can I create my own using a DNS server?

---

### Post by MAFoElffen on 2023-10-09
At first, I thought I was having Deja Vu: [https://ubuntuforums.org/showthread.php?t=2491436](https://ubuntuforums.org/showthread.php?t=2491436)

Like this? 
[https://rachitpandya.medium.com/how-to-create-a-captive-portal-38aba6284b91](https://rachitpandya.medium.com/how-to-create-a-captive-portal-38aba6284b91)
[https://github.com/jee1mr/captive-portal](https://github.com/jee1mr/captive-portal)

---

### Post by TheFu on 2023-10-09
Some router software has the ability to invoke a captive portal.  I know pfSense can. This is used by many hotels.
[https://docs.netgate.com/pfsense/en/latest/captiveportal/index.html](https://docs.netgate.com/pfsense/en/latest/captiveportal/index.html)
[https://docs.opnsense.org/manual/captiveportal.html](https://docs.opnsense.org/manual/captiveportal.html)
[https://openwrt.org/docs/guide-user/services/captive-portal/opennds](https://openwrt.org/docs/guide-user/services/captive-portal/opennds)

Are some guides from each of those.

Looks like OpenNDS is the main tool used. It is in the Ubuntu Snap Store ... or you can get it from github if you don't like snaps.
[https://github.com/openNDS/openNDS](https://github.com/openNDS/openNDS) >  About

openNDS (open Network Demarcation Service) is a high performance, small footprint, Captive Portal. It provides a border control gateway between a public local area network and the Internet. 
Documentation is here: [https://opennds.readthedocs.io/en/stable/](https://opennds.readthedocs.io/en/stable/)

I've only played with captive portal stuff on pfSense and when trying to help a hotel setup theirs that wasn't working correctly.

---

### Post by ohiodissident on 2023-10-11
Thanks for the suggestions.  I will have to play around with them to see if I can get them to work as I need it.

My concern, though, is that those are meant to be installed on a router for use on a private network.  I need to find a way to setup a DNS server that will prompt a captive portal.  The DNS server will be on the public Internet but restricted by an ACL to prevent abuse.

---

### Post by SeijiSensei on 2023-10-11
You would need to write software that would be triggered by the arrival of a query packet on port 53. You probably would want to cache permitted IPs as well so users aren't constantly bombarded with requests. I have no idea if there are open-source options for that. It's not likely to be a simple solution.

---

### Post by ohiodissident on 2023-10-12
> **SeijiSensei said:**
> You would need to write software that would be triggered by the arrival of a query packet on port 53. You probably would want to cache permitted IPs as well so users aren't constantly bombarded with requests. I have no idea if there are open-source options for that. It's not likely to be a simple solution.
Someone suggested DNSwitch but I could not get it to work.  I tried running it in Python on Ubuntu Server and it gave me errors.

---

