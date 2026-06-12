---
title: "Is it true that session hijacking works just as easily when Linux users are targetted"
date: 2011-03-22
forum: Security
---

### Post by brawnypandora0 on 2011-03-22
...as opposed to Windows? Whenever I'm out with my laptop in an unfamiliar area, I'm really concerned about this. I feel safe at school since my school's network requires a login, but I'd never visit an online banking website or Amazon or go on Facebook when I'm in an area with free wifi like the airport or a public library. Am I being overly worried?

Also, since Facebook and Twitter can easily be targetted, are online banking and webmail sites just as vulnerable?

---

### Post by HermanAB on 2011-03-22
Howdy,

A properly designed bank site uses HTTPS.

---

### Post by brian_p on 2011-03-22
> **brawnypandora0 said:**
> ...as opposed to Windows? Whenever I'm out with my laptop in an unfamiliar area, I'm really concerned about this. I feel safe at school since my school's network requires a login, but I'd never visit an online banking website or Amazon or go on Facebook when I'm in an area with free wifi like the airport or a public library. Am I being overly worried?

Also, since Facebook and Twitter can easily be targetted, are online banking and webmail sites just as vulnerable?

Coincidentally, in the past few days I've been looking at the questions you raise but haven't yet come to any firm conclusion as to the attitude I should take to what could be a potential problem in using networks outside my control.

Hijacking appears to work through ARP spoofing and the type of OS or being required to login are immaterial, although your school's network could have some techniques to detect when it is happening. You could always ask them, which is something you won't be able to do at the airport. 

Caution on unknown networks is sensible. Whether there is a satisfactory technical solution to any concerns you may have is worth investigating.

---

### Post by brian_p on 2011-03-22
> **HermanAB said:**
> Howdy,

A properly designed bank site uses HTTPS.

I must admit this is the answer I'd have given up to a few days ago. Actually, I'd probably still say relying on an https link is good advice. However, coming across sslstrip has given me something to think about.

---

### Post by rookcifer on 2011-03-22
Do not visit banking sites over an open Wifi connection or another public shared network.  The OS has nothing to do with it -- everyone is vulnerable to Wifi snooping.

If you must do sensitive stuff over a shared connection, then be sure to check the bank's certificate against the certificate in the browser to make sure they match. FF should do this automatically, but there are ways an attacker can easily fool you if you don't pay attention.  If you must do banking over a connection like this, then I recommend [Certificate Patrol.]("https://addons.mozilla.org/en-US/firefox/addon/certificate-patrol/")

---

### Post by bodhi.zazen on 2011-03-22
> **brawnypandora0 said:**
> ...as opposed to Windows? Whenever I'm out with my laptop in an unfamiliar area, I'm really concerned about this. I feel safe at school since my school's network requires a login, but I'd never visit an online banking website or Amazon or go on Facebook when I'm in an area with free wifi like the airport or a public library. Am I being overly worried?

Also, since Facebook and Twitter can easily be targetted, are online banking and webmail sites just as vulnerable?

Depends on the vulnerability. Some "cracks" are OS independent (phishing, man in the middle, etc),some vulnerabilities are also likely OS independent (buffer overflows). But then, assuming you have shell access, windows is not bsd is not linux and then you would be confronted by apparmor or selinux (or not).

So the answer is not so simple, you need to research a specific vulnerability in your browser (some vulnerabilities affect all os, others do not) or the attack vector.

---

### Post by njdove on 2011-03-22
The type of session hijacking that you refer to tends to work through stealing HTTP authentication cookies through: sniffing an insecure network; actively intercepting a cookie with a man-in-the-middle (MITM) attack; or using cross-site scripting (XSS) to convince your browser to implicitly use its cookie on the attacker's behalf. GNU/Linux is just as susceptible as any other OS to these attack vectors.

I concur with this thread's consensus to use HTTPS. This secures traffic against prying eyes, even over an insecure physical network, and adds a 3rd party trust infrastructure that mitigates MITM attacks. Modern browsers tend to give much more visible SSL/certificate warnings, which you should heed. I will also add that you should explicitly type "https://" before the address because tools like @brian_p mentions can intercept an initial, insecure request.

---

### Post by Dire_Devourer on 2011-03-22
HTTPS Everwhere available @ [https://www.eff.org/https-everywhere](https://www.eff.org/https-everywhere) ;)

---

### Post by HermanAB on 2011-03-23
Howdy,

Yes, SSL man-in-the-middle attacks are certainly possible, but fortunately still very unlikely since it is hard to pull off.

---

### Post by rookcifer on 2011-03-23
> **HermanAB said:**
> Howdy,

Yes, SSL man-in-the-middle attacks are certainly possible, but fortunately still very unlikely since it is hard to pull off.

Not hard to do at all.  There is software out there that does it for you.  There are numerous tools: ettercap, dsniff, SSLstrip, and Mallory to name a few.

Here's a video that shows how even unsophisticated people can sniff your wireless connection (even SSL connections): [http://www.youtube.com/watch?v=Ku2sN3H8gKo](http://www.youtube.com/watch?v=Ku2sN3H8gKo)

The key is to pay attention and make sure that:

1) You use HTTP**S**

2) That the certificate the banking site is using is legit.  If you get a warning about a bad cert, *do not* proceed.

SSLstrip simply strips the "S" from HTTPS and routes it through an unencrypted stream.  Other tools actually create fake certs.  Either way, you can defeat it if you just pay attention.  This is why I think "Certificate Patrol" for Firefox has some value.

---

### Post by brian_p on 2011-03-23
> **rookcifer said:**
> 

Here's a video that shows how even unsophisticated people can sniff your wireless connection (even SSL connections): [http://www.youtube.com/watch?v=Ku2sN3H8gKo](http://www.youtube.com/watch?v=Ku2sN3H8gKo)

I think that video is positively misleading about the capabilities of SSLstrip. The exploit has to be conducted when the user requests an http URI. Any https links in the returned page are replaced by http links which it is hoped the target will not notice. SSLstrip does not work by removing the 's' from https in the address bar, which is what is shown in the video.

> We have yet to find a site this doesn't work on.


They haven't looked hard enough. It doesn't work if the initial requested URI is https.

> The key is to pay attention and make sure that:

1) You use HTTP**S**

2) That the certificate the banking site is using is legit.  If you get a warning about a bad cert, *do not* proceed.

I agree. Also, it would be good to look for a green favicon in the address bar. Blue? I'm unsure how to react to that.

---

### Post by njdove on 2011-03-23
> **brian_p said:**
> 
I agree. Also, it would be good to look for a green favicon in the address bar. Blue? I'm unsure how to react to that.

I agree with @brian_p re: sslstrip being overrepresented. Again, be sure you manually type the "S" in "https://".

Firefox' [Site Identity Buttons]("https://support.mozilla.com/en-US/kb/Site%20Identity%20Button") [1] use the following color code:

[LIST]
[*]gray - Site does not provide a certificate and is not encrypted or is partially encrypted.
[*]blue - Site uses valid 3rd party certificate and information is encrypted.
[*]green - Site uses an "EV certificate", which indicates that the Certification Authority (CA) engaged greater due diligence when ensuring the identity of the certified party and control of their domain.
[/LIST]
Blue is generally trustworthy and green is as good as it gets currently.

[1] [https://support.mozilla.com/en-US/kb/Site%20Identity%20Button](https://support.mozilla.com/en-US/kb/Site%20Identity%20Button)

---

### Post by rookcifer on 2011-03-24
> **njdove said:**
> [*]green - Site uses an "EV certificate", which indicates that the Certification Authority (CA) engaged greater **due diligence** when ensuring the identity of the certified party and control of their domain.


Which may not be [very much]("https://blog.torproject.org/blog/detecting-certificate-authority-compromises-and-web-browser-collusion") diligence indeed.  :(

---

### Post by Duncan Williams on 2011-03-28
A few basic steps.
OpenDNS DNS Server information:
[http://www.opendns.com/start/](http://www.opendns.com/start/)
Add new dns settings in ubuntu:
[http://www.liberiangeek.net/2010/12/change-dns-server-address-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/12/change-dns-server-address-ubuntu-10-0410-10-maverick-meerkat/)
Use Last Pass (browser extension) for secure password management.

---

### Post by goopen on 2011-04-11
I have a site that sslstrip wont work on: sms7.schoolsoft.se/nti Seems like they use something else. Feel free to test tho.

---

### Post by EJeanmaire on 2011-04-12
sslstrip also can put a cool "lock" favicon on the browser to trick users into thinking that the site is secure.  Always check the cert (never accept a cert warning message).  Always look for https. Never log into your bank account from a login page that isn't https from the start (I know a few bank's that only POST login info to https, which is a coding no-no as its too late to tell you got stripped).  For example : [http://www.tdameritrade.com/welcome3.html](http://www.tdameritrade.com/welcome3.html)  If you logged in from this page and you were being MiTM'd at the airport, you'd get no warning.

---

### Post by hyperAura on 2011-04-13
Hi guys, is it possible to be hijacked if you SSH over a public wifi network?

---

### Post by bodhi.zazen on 2011-04-13
> **hyperAura said:**
> Hi guys, is it possible to be hijacked if you SSH over a public wifi network?

As long as you are connected to an untrusted network all things are possible.

It would be highly unlikely mind you.

---

### Post by brian_p on 2011-04-14
> **hyperAura said:**
> Hi guys, is it possible to be hijacked if you SSH over a public wifi network?

It depends what you mean by "hijacked". A bit of ARP spoofing could result in your traffic going through another machine before it gets to the gateway to the internet, so in that sense you have been hijacked. However, all communication using ssh is encrypted, so the intercepted data will be useless to the hijacker.

Which is not to say they could not make life interesting for you in other ways.

---

### Post by hyperAura on 2011-04-14
Thanks for your answers guys. I just wanted to be sure that even though information can be stolen, it is not possible to read them in anyway.

Lately I've been using ssh through my blackberry so I was worried a little.

---

### Post by hyperAura on 2011-04-14
Thanks for your answers guys. I just wanted to be sure that even though information can be stolen, it is not possible to read them in anyway.

Lately I've been using ssh through my blackberry so I was worried a little.

---

### Post by BkkBonanza on 2011-04-14
Actually **sslstrip** + **sslsniff** does not ONLY work with http connections. If you give it a CA certificate or intermediate CA certificate acceptable to your browser then it will generate on-demand certificates for any web site and fake those sites. In this case the user sees what appears to be a valid certificate. This was initially demonstrated with the null-prefix certificates but will work with any certificate or rogue intermediate CA.

The hard part, of course, is getting either a usable intermediate certificate or tricking the user into installing a "special" certificate authority in their browser. This isn't so hard for non-tech users as you can setup a link to a certificate that will install it with only a confirmation by the user. Some people don't know what they're doing. Also, if someone can get a few seconds access to your machine they can install a certificate authority that will then accept fake certificates for any web site.

I've actually done this on my system as I manage a small CA of my own and use it for my own sites. Once installed you can literally fake any popular site you please.

This is all a pretty serious risk - though not anywhere near "wide open".

If you are worried about this type of thing you should use the Firefox add-on "Certificate Patrol" to watch certificates and warn you when a different one gets provided by sites you visit. 

When you are travelling and using unknown systems you would be very wise to use an SSH proxy to a known system or simply not do anything sensitive, whether https or not.

---

