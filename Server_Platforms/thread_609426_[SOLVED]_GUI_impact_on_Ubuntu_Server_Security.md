---
title: "[SOLVED] GUI impact on Ubuntu Server Security"
date: 2007-11-10
forum: Server Platforms
---

### Post by quandary on 2007-11-10
Hi there!

I have installed Ubuntu Server 7.10 with LAMP.

Then I typed 'apt-get install ubuntu-desktop' to install xorg & co. in order to be able to do some development on my PHP webpages.

When i will be finished, i will type:
sudo update-rc.d -f gdm remove

and restart. So it won't start X on system startup.

If I then install & configure a firewall and make the server publicly accessible via DynDNS, will there be any additional security risk as compared to when i would not have typed 'apt-get install ubuntu-desktop' ? 

The question has relevance because i'm plannig to release a new aimbot (for quake3 arena), so it is very likey that there will be quite a few attemps to hack my website/server...

Additionaly, does anybody know how i can make Apache Server return a fake server name and version number, and maybe as well a fake Operating system name and version?

Thanks in advance!

---

### Post by HermanAB on 2007-11-11
X uses port 6000.  All you need to do is drop port 6000 with iptables, or disable networking in the X configuration.

The most important thing with a server, is to use long passwords of 9 or more characters for all accounts.  Most hacks occur when some bright spark uses a 4 character password.

Cheers,

Herman

---

### Post by quandary on 2007-11-14
Thanks for the tip on port 6000.

As for the password, I'm gonna use keys. Better a 4096 key than a 9+ digit pwd ;-)

---

### Post by hkgonra on 2007-11-14
> **quandary said:**
> Thanks for the tip on port 6000.

As for the password, I'm gonna use keys. Better a 4096 key than a 9+ digit pwd ;-)

4096 key ?

---

### Post by crouton on 2007-11-14
> **hkgonra said:**
> 4096 key ?

4096-bit key as in a keyfile rather than the usual keyboard-interactive password.

---

### Post by stmurray on 2007-11-14
If you are firewalled off, then your biggest risk of compromise will be your web server and application (PHP isn't known for it's security).  Make sure you secure the web server (mod_security is a start-> [http://www.howtoforge.com/apache_mod_security]("http://www.howtoforge.com/apache_mod_security"),  and google "securing apache" for guidelines).  Then test the server and the application,  for security issues.  Use a freebie  web vulnerability scanner, if nothing else, (see [http://sectools.org/web-scanners.html ]("http://sectools.org/web-scanners.html") for a list).   I would put SNORT on there as well.  

As for spoofing the Apache banner, there are many tools that can guess the web server and version by sending various requests and looking at how it responds.  So spoofing the banner is a good idea, but won't keep motivated attackers from figuring it out.

Good luck!!

---

### Post by quandary on 2007-11-16
thanks, i will do so.

Hmm, yes I had concerns about php, too; your tip seems to confirm my skepticism. Then, perhaps it's after all still better to abstain from PHP.

I also expect flood attacks. So I'm also gonna install mod_dosevasive.

---

