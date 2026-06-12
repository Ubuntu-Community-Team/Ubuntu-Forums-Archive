---
title: "Securing Ubuntu on WLAN"
date: 2011-04-25
forum: Security
---

### Post by Stisfa on 2011-04-25
After reading [[COLOR="DarkOrange"]this blog post[/COLOR]]("http://blogs.pcmag.com/securitywatch/2007/10/ssid_hiding_is_futile_so_is_ma.php") and it's [[COLOR="DarkOrange"]source[/COLOR]]("http://blogs.technet.com/b/steriley/archive/2007/10/16/myth-vs-reality-wireless-ssids.aspx"), I'm feeling thoroughly unsecure, even though I have WPA2 properly implemented (using a passphrase, not a password).  Is there anything I can do within Ubuntu to increase my security while connected to my WLAN?  I realize there's probably nothing it can do *for* the router, as it's a device that's not maintained by Ubuntu, but is there anything I can do within my Ubuntu machine to secure the wireless connection between the router and my Ubuntu box?

Also, as a non-critical question, I was wondering if anybody knew why and how the methods of MAC Address Filtering and SSID Hiding became pseudo-security practices, ones that have been advocated in certification material such as CompTIA's?

---

### Post by Ryan Dwyer on 2011-04-25
The article is saying that SSID hiding and MAC address filtering can both be bypassed and that WPA/WPA2 (preferrably WPA2) is the only real way to secure a wireless network. You said you've got WPA2 properly implemented so you're all good.

SSID hiding and MAC address filtering are suggested by some sources because they'll stop the typical user. You just can't rely on those methods though.

---

### Post by Stisfa on 2011-04-26
> **Ryan Dwyer said:**
> SSID hiding and MAC address filtering are suggested by some sources because they'll stop the typical user. You just can't rely on those methods though.

I was so proud of myself when first I implemented those "security" techniques, and a little more research revealed how [[COLOR="DarkOrange"]these 2 things are at the top of the dumbest things one can do to secure one's WLAN...[/COLOR]]("http://www.zdnet.com/blog/ou/the-six-dumbest-ways-to-secure-a-wireless-lan/43")

It's disappointing that these things only exist to inconvenience an informed user, much like how gates and fences only serve as nuisances for an intelligent thief.

---

### Post by Redblade20XX on 2011-04-26
> **Stisfa said:**
> I was so proud of myself when first I implemented those "security" techniques, and a little more research revealed how [[COLOR=DarkOrange]these 2 things are at the top of the dumbest things one can do to secure one's WLAN...[/COLOR]]("http://www.zdnet.com/blog/ou/the-six-dumbest-ways-to-secure-a-wireless-lan/43")

It's disappointing that these things only exist to inconvenience an informed user, much like how gates and fences only serve as nuisances for an intelligent thief.

LMAO, those were pretty good!

---

### Post by movieman on 2011-04-27
Ultimately you need to know what the threat is; SSID hiding and MAC filtering are barely even a speed-bump for someone who's determined to hack your network, but they will stop Joe Average who knows nothing about PCs if you have an open access point or WEP with a weak password.

Of course you're much better off using WPA2 with a strong password rather than trying to hide behind tissue paper walls.

---

### Post by bodhi.zazen on 2011-04-27
As with all things white/black hat it will come down to your skill vs your intruder.

IMO WPA is sufficient for most home users.

---

