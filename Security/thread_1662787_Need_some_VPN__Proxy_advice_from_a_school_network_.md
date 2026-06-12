---
title: "Need some VPN / Proxy advice from a school network to my home server, banking etc."
date: 2011-01-08
forum: Security
---

### Post by jimmy the saint on 2011-01-08
So I am in DC for a semester, which will be fun, but I don't trust the network that I am forced to use.

I have a very basic VPN set up with OpenVPN to my home network using a 2048 bit static key, that lets me access my network pretty well.  All web traffic is still sent over the school network, though.  

Apparently, I can configure OpenVPN to forward all internet traffic through the VPN, but it requires server tweaks, and I would prefer not to mess with the setup, as I will be unable to fix it should something bad happen.  

Is there anything else I can do to ensure that my web traffic is secure?  I am thinking either a secure proxy or something similar, but I don't have much experience with such things.  

Any advice would be appreciated.  Ideally the end result would have my web traffic encrypted and passed through my home connection.  Acceptable would simply have internet traffic simply secure through the local network here.

Thanks

JTS

---

### Post by schwascore on 2011-01-09
Easiest thing to do is to use https:// whenever possible. Here's a writeup of the HTTPS Everywhere plugin from Firefox that you might be interested in.

[http://www.zdnet.com/blog/security/the-eff-releases-new-https-everywhere-firefox-extension/6738](http://www.zdnet.com/blog/security/the-eff-releases-new-https-everywhere-firefox-extension/6738)

---

### Post by Skadork on 2011-01-11
No server tweaks needed. Add the following command to your client config file:

> redirect-*gateway*This will send all data through the VPN, including broadcast traffic.  You will probably have to turn the VPN off before you authenticate on the local network, then once you can hit a public site (like [http://ubuntuforums.org](http://ubuntuforums.org) :D ) then start the VPN and then all traffic will go through your home.

*edit*: another option:

You can also you putty to punch a hole in a firewall and tunnel web traffic through an SSH connection.  I use this on public computers cause it takes about 3 minutes to set up including the time it takes to download putty :)

[http://souptonuts.sourceforge.net/sshtips.htm](http://souptonuts.sourceforge.net/sshtips.htm)

---

