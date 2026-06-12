---
title: "Running SMTP mail server on LAN behind NAT"
date: 2008-09-30
forum: Server Platforms
---

### Post by yesmat on 2008-09-30
Hi All,

I am trying to build a simple Mail Server (sendmail or Postfix).
This mail server will sit on my home LAN behind DSL and NAT.

I want to make sure that this mail server will send emails out every time.

Issues are:

1- I have no valid FQDN
2- What do i set my Hostname as? how do i configure my /etc/hosts file
3- MY ISP may reject email coming from a server that has no FQDN, is there a workaround that?

Thanks for your support

---

### Post by yesmat on 2008-10-01
Any one??

---

### Post by orotrev on 2008-10-01
You have a few hurdles to jump to get this going. While I don't have the exact solution here are some things to research:
1. Dynamic DNS setup on your home router or server. I use dyndns.org
2. Setup an MX record on your dynamic dns provider pointing to your server
3. port forward port 25 on your router / firewall
4. setup postfix
Hope that helps get you started

---

### Post by windependence on 2008-10-02
Do you own any domain names at all?

For a workaround you can try no-ip. They have a good mail server workaround solution.

Also, you don't need your ISP's co-operation if you run your own SMTP server. I would suggest Citadel or Zimbra for a complete mail solution.

-Tim

---

