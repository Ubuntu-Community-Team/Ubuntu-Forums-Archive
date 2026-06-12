---
title: "Limited connection on ubuntu server"
date: 2011-07-05
forum: Server Platforms
---

### Post by mmmp on 2011-07-05
Hello,
I've installed ubuntu server with PPTP VPN. Everything works fine and I can connect to the VPN server but when i connect to my VPN server i get limited connection, and i am not able to access the website on my server.
Is anyone know this problem?

---

### Post by mmmp on 2011-07-05
.

---

### Post by arrrghhh on 2011-07-05
Please wait *at least* 24 hours before bumping a post.  You waited... all of 17 minutes it seems.

Anyhoo, are you trying to access your website thru the domain name or the WAN IP, or are you trying to hit your website via the LAN IP?

If you're using a VPN, you should be trying to hit the site via LAN IP.

---

### Post by mmmp on 2011-07-05
> **arrrghhh said:**
> Please wait *at least* 24 hours before bumping a post.  You waited... all of 17 minutes it seems.

Anyhoo, are you trying to access your website thru the domain name or the WAN IP, or are you trying to hit your website via the LAN IP?

If you're using a VPN, you should be trying to hit the site via LAN IP.

What do you mean?
My PPTPD config is:

localip 192.168.1.103
remoteip 192.168.1.140-150

I can connect succesfuly to VPN server (with Windows Vista) but have limited connction to network and not connection to internet.

---

### Post by arrrghhh on 2011-07-05
> **mmmp said:**
> What do you mean?
My PPTPD config is:

localip 192.168.1.103
remoteip 192.168.1.140-150

I can connect succesfuly to VPN server (with Windows Vista) but have limited connction to network and not connection to internet.

This is the problem with VPN connections.  Do you want to use the VPN to access the internet, or just use the VPN to access the LAN?  If you're using the VPN to access the internet, you'll need to make sure that's allowed thru the server.

I'm not an expert on VPN's, but describing how you've set it up and maybe providing some configuration files would help others help you.  I just know that with a VPN, quite often there is additional config to access internet & LAN.  LAN-only, you should have already - yes?

---

