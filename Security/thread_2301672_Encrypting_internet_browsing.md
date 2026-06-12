---
title: "Encrypting internet browsing"
date: 2015-11-04
forum: Security
---

### Post by UncleMonty on 2015-11-04
What options are there for encrypting internet activity?

---

### Post by Lars Noodén on 2015-11-04
Using the [HTTPS Everywhere](https://www.eff.org/https-everywhere) add-on helps, if you are using one of the browsers that it supports.  But it only helps with sites that are HTTPS-enabled and even then the way the web has implemented certificates is kind of broken and vulnerable.

---

### Post by brian-mccumber on 2015-11-04
You could use a proxy service like Tor or Hide My Ass but if you are wanting to do bad things and cover them up it doesn't matter what you use, if big brother wants to hack your machine they will find a way.

---

### Post by nknwn on 2015-11-04
There's Vidalia in the Ubuntu Software Centre - it's a TOR front end.
After it is set up your internet connection is encrypted and goes through the TOR network (onion router)

When you use this even your ISP doesn't get a list of your web pages. It only sees a list of TOR routers I understand.
However I don't use Vidalia as it gave me a problem when I tried to set it up recently.

Instead I've dabbled with the Tor Browser from here: [https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)
It's interesting and it might become essential if the so called snoopers charter comes in to force in the UK.

---

### Post by HermanAB on 2015-11-04
Download the 'Tor Browser Bundle'.  It works.  It costs nothing.  Nuf sed.

---

### Post by bashiergui on 2015-11-05
There are VPN services like OpenVPN. This will encrypt all your traffic between you and the VPN. It won't encrypt all your traffic as it exits the VPN. Someone sniffing your traffic on the same wifi network would only intercept encrypted traffic. However the VPN service would have records of your traffic as it leaves the VPN and goes to unencrypted websites.

Tor encrypts your traffic until it reaches a non SSL website. Encryption is done in a way that prevents others from tracing your traffic back to you. So even if the destination website isn't encrypted, the traffic won't be traced to you.

HTTPS Everywhere encrypts all traffic to websites that support SSL. If the website you visit doesn't support it then the session will not be encrypted.

A combination of Tor, VPN, and HTTPS Everywhere would maximize realistic encryption possibilities.

---

### Post by dave205 on 2015-11-16
not internet browsing but internet sharing would be to use Demonsaw. ultra secure, all encrypted. google it or just go to demonsaw.com

---

