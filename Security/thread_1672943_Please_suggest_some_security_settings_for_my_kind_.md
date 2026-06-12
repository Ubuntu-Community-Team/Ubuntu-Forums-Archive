---
title: "Please suggest some security settings for my kind of user"
date: 2011-01-21
forum: Security
---

### Post by 3602 on 2011-01-21
First, of course, allow me to describe what I do, intend to do and probably will do with this computer. It is running Ubuntu Maverick 64-bit.
1. Browse at home. Most common sites: CNN, UF (here), Head-Fi;
2. General school work at home. Pushing papers (lab reports) and drawing molecules;
3. Bring it to school to perform 1 & 2;
4. Occasional torrenting from Pirate Bay (not here to discuss legality issues).
Now I don't know what systems people use at school, I'd say mostly Windows, some Mac. However there is a *huge* Ubuntu logo painted on the walls of the computer department, so that may or may not be a threat.
I have *rkhunter* and *chkrootkit* installed. Ran them and read the logs. Couple of false positives.
_bodhi.zazen_ mentioned SSH tunnelling. Well, I have no standing machine at home that allows me to do this, although I do have a wireless router (bringing it up, may or may not be of help). Are there ways of host-based communication encryption?
I can take care of the *physical* security part (BIOS passwords, encrypted Home, wrap a chain around, etc etc.) however I'd like some advice on the "soft" part of security.
Oh, and if you'd like to know why I am asking for this, as of right now you may consider me as paranoid.:)
Thank you very much.

EDIT: I tried NoScript but found it to be a very big hassle as it breaks the interface of NewsPulse (CNN), along many other web functions.

---

### Post by matt_symes on 2011-01-21
Hi

I don't condone piracy but i do understand the need for security. This is a good place to start.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Kind regards

---

### Post by Rubi1200 on 2011-01-21
Did you try configuring the various options in NoScript?

It can be set to allow the features you want to work on a per-site basis.
[http://noscript.net/features#basics](http://noscript.net/features#basics)

---

### Post by 3602 on 2011-01-21
> **matt_symes said:**
> Hi

I don't condone piracy but i do understand the need for security. This is a good place to start.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Kind regards
Thank you, I have indeed read that several times. Reading that inherently brings up the question: Does it apply to advanced uses (servers, etc) or does it apply to absolutely everyone? AppArmor read sure seems pretty complicated and the Dissecting a Profile part is quite advanced for me already...
(And when you want to watch a mini-series that haven't published a DVD set yet, well...)
To the member who gave me that NoScript page, thank you. Although there are many things in that page that I do not understand (seem to be stuck in the 20th century, don't I).

---

### Post by cariboo on 2011-01-21
I've been using a Linux variant for several years, and most of what I do is the same as you. At home and work, I'm behind a router with no ports forwarded, and upnp disabled, I don't run noscript, but do have ad-block for both chromium and Firefox. The only extra thing I do is enable ufw when I'm out and about with my netbook. Common sense, also helps a lot.

---

### Post by dFlyer on 2011-01-21
Common sense, should top your list. I've been using some distro of linux since the mid 90 and have never had a virus or been hacked.

---

### Post by 3602 on 2011-01-21
> **cariboo907 said:**
> I've been using a Linux variant for several years, and most of what I do is the same as you. At home and work, I'm behind a router with no ports forwarded, and upnp disabled, I don't run noscript, but do have ad-block for both chromium and Firefox. The only extra thing I do is enable ufw when I'm out and about with my netbook. Common sense, also helps a lot.
What does UPnP and/or NAT-PMP do? I set Vuze to auto port-forward using UPnP or NAT-PMP so I don't have to configure a static IP and port-forward from my router (as I did back in Windows).
Also I have ABP for Firefox. Don't really go to much other sites (sometimes Cracked, BBC).

---

### Post by cariboo on 2011-01-21
With Upnp enabled on the router, you could open it up for access from outside accidentally. For instance if you were to start the remote desktop server, and set the same options as in the screen shot, you would leave yourself open to being cracked in no time if Upnp is enabled.

---

### Post by 3602 on 2011-01-22
I see... I'll disable UPnP and see how it goes. I don't have Remote Desktop enabled. Thank you.

---

### Post by cariboo on 2011-01-22
Remote desktop was just an example, with Upnp enabled, other applications can open ports that you aren't aware of too.

---

