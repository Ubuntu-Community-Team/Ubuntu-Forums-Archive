---
title: "How can I be sure that a CA is the CA he pretends to be"
date: 2010-09-07
forum: Security
---

### Post by jaaf64 on 2010-09-07
I became interrested in security just a little while ago so I am not yet at ease with some basic principle.

From my recent readings I understood that to ensure that a site is the site you expect to be in https connection with, you must check that its certificate is authentic. To do so you would just click on the small padlock near the https mark and read the certificate. At this point you should trust what you are reading because it's decrypted by the public key of the Certificate Authority responsible for the delivery of this certificate.

Well. But at this point my question is:

" how did  my browser manage to get the public key of the CA and how it can ensure that it really comes from this CA?"

Is the Ubuntu installion procedure automatically managing this?

---

### Post by slowth5 on 2010-09-07
These sites should help explain how the browser gets the key and why CAs aren't absolutely trustworthy.

SSL protocol:  [http://www.grc.com/sn/sn-195.htm](http://www.grc.com/sn/sn-195.htm)

CAs:     [http://www.grc.com/sn/sn-179.htm](http://www.grc.com/sn/sn-179.htm)


Why it's not perfect:

[http://www.grc.com/sn/sn-223.htm](http://www.grc.com/sn/sn-223.htm)

[http://www.grc.com/sn/sn-243.htm](http://www.grc.com/sn/sn-243.htm)

[http://www.grc.com/sn/sn-262.htm](http://www.grc.com/sn/sn-262.htm)

[https://www.eff.org/observatory](https://www.eff.org/observatory)

---

### Post by jaaf64 on 2010-09-07
Probably a lot of very interesting things to read.
I am on my way on.
Thank you very much.

---

### Post by slowth5 on 2010-09-07
I apologize for just posting a bunch of links, but I think they will explain it better than I ever could.

Steve Gibson and Leo Laporte banter quite a bit at the beginning, but the content is pure gold.

---

### Post by BkkBonanza on 2010-09-07
Short version...

Your browser comes with a built-in set of certificates. You can view them in the Preferences, Advanced, Encryption dialog. View Certificates.

You can disable ones you may not want to automatcially trust. 
Such as foreign govts.

There are problems with the CA methodology that those links above can more fully explain. 

Probably your best defense currently is to use the Firefox add-on "**Certificate Patrol**" to keep a tighter watch on your SSL activities.

While you still accept a certificate initially it will watch them for any changes that are suspicious, such as when the expiry date isn't near. And it pops up warnings that really Firefox should check for but doesn't because everyone would complain it's too noisy. But mostly it adds a reasonable degree of automation to watching for funky MITM behaviours.

---

### Post by rookcifer on 2010-09-07
Basically, the whole SSL model is broken because the Certificate Authorities (CA's) just simply can't be trusted to do the job they're supposed to do.  For one thing there are over 100 of them accepted by most browsers and everyone of them are given ultimate trust, so all it takes is one bad CA to spoil the whole bunch.  And even the honest CA's can be fooled by criminals since most of the time they don't even do much identity checking.  All they care about is collecting their money and moving on to the next guy.

In addition to the links already posted, here's some more links I recommend:

Professor Matt Blaze's (a foremost expert in cryptography) take: [http://www.crypto.com/blog/spycerts/](http://www.crypto.com/blog/spycerts/)

Some good info from the EFF: [http://www.eff.org/deeplinks/2010/03/researchers-reveal-likelihood-governments-fake-ssl](http://www.eff.org/deeplinks/2010/03/researchers-reveal-likelihood-governments-fake-ssl)

There's already a MITM appliance (which allows a person in the middle to circumvent your security) being sold to governments and it's just a matter of time before criminals get them too: [http://www.wired.com/threatlevel/2010/03/packet-forensics/](http://www.wired.com/threatlevel/2010/03/packet-forensics/)  Keep in mind, a government only needs a single faked cert from a single CA and the whole system is broken.  It's extremely likely the NSA already has such certs (whether through court order or NSL's or just simply paying for them under the table).

Actually an attacker doesn't even need a hardware appliance to do this -- there are already software packages created for this purpose: 
[http://www.thoughtcrime.org/software/sslsniff/](http://www.thoughtcrime.org/software/sslsniff/)

The only way around this is to not trust so many CA's and/or to verify the authenticity of the certs some other way (good luck with that).  As another guy already said, "Certificate Watch" will help some, but it's not a magic bullet either.  

All in all, I don't know if there is really any good solution because it is impractical to tell the user to verify his own certs (which would require calling the website owner, verifying he is who he says he is and then getting him to read off the cert fingerprint, etc.).  This works fine with PGP and key-signing parties, but it is impractical to do for every encrypted website.

---

### Post by jaaf64 on 2010-09-07
Hi everybody,

I am presently reading the conversation between Steve and Leo.
It's just a little bit hard for the non native English reader and non computer scientist I am but, but nevertheless it's a delectation.

I can see from the numerous replies my question triggered that the subject is a hotly debated issue.

I probably will need some time to deepen my understanding but I feel hopeful of managing to do so by following your very relevant links and considering your opinions

Thanks again.

---

### Post by BkkBonanza on 2010-09-07
It isn't perfect by any stretch but Certificate Patrol (**CP**) allows us to say "ok today I'll believe this is a good cert", now watch it as I go forward, move around and if the cert changes then at least I'll know. Because right now FF doesn't even let you know when certs change and why.

The Verisign Root certs are pretty long term so they shouldn't be changing often at all. **CP** pops up a msg bar when a new cert comes in so you can check quickly if it's some derivative (intermediate) CA that's claiming authenticity. It helps take it out of the background and into view. 

Of course, with only about 38,000 odd **CP** downloads practically no one is paying any attention to what certs they're getting. They've been told for so many years that it's all safe, safe, safe.

You can at least raise the bar so that an eavesdropper has to have significant  resources and not just be hacking on your LAN/Wifi. Does that totally secure it, nullify the threat entirely? No way. I've been looking into various tools and threat methods and they're real and not too hard to set up.

Maybe DNSSEC will help eventually but I don't expect much there either. Why would Verisign and such create a new system that wrecks havoc with their current cash cow? Makes no sense.

---

### Post by BkkBonanza on 2010-09-07
> **jaaf64 said:**
> 
I can see from the numerous replies my question triggered that the subject is a hotly debated issue.

It's pretty well understood now. More of an "exposing" than a debate.

In the general public few know about this because it would be terrible for business. But in the net security world it's well understood as a real problem.

---

### Post by movieman on 2010-09-07
> **rookcifer said:**
> Keep in mind, a government only needs a single faked cert from a single CA and the whole system is broken.

A single faked cert for every web server they plan to spoof. I don't believe any sane web browser will trust a random certificate to sign others?

> It's extremely likely the NSA already has such certs (whether through court order or NSL's or just simply paying for them under the table).

In that case, why has no-one ever managed to produce such a certificate?

I agree that the whole CA concept is fundamentally flawed, but I don't believe there's any evidence that it's as broken as you claim. A single deliberately faked certificate from a CA would be catastrophic for their business as they'd rapidly be pulled from every web browser on the planet (well, maybe not IE).

---

### Post by BkkBonanza on 2010-09-08
Actually they only need one **CA cert**. Not a server cert or client cert.

But with a cert that has the "Certificate Basic Constraints" field set to "Certificate Authority". Then they can create server certificates for **ANY** CN "Common Name" they desire. The only defense is knowing thru a alternate channel which CA the real server cert is signed by because the browser will accept ANY in it's store.

It goes one step even worse because one CA cert can sign and create other CAs. So Verisign can, and does, create subCA certs for other organizations (called an Intermediate CA). If they ever created one for the NSA then that cert can be used to create an infinite number of ANY name.

Try out the TinyCA package in the Ubuntu repos. It's a front end to openssl that can be used to do all this. I have done it and can do all these things myself. But my certs are only signed by me, so the browser will always warn. But if I compile my cert into the built-in cert store in FF then mine won't warn, just like other built-ins.

It's more than flawed. It's completely broken. It's just that few people know and the authorities keep telling everyone to use SSL for end-to-end security.

This isn't new news either. See [http://www.schneier.com/](http://www.schneier.com/) recent post. And there are dozens of other places documenting it if you go look. As mentioned above see [Moxie Marlinspike's]("http://www.thoughtcrime.org/software/sslsniff/") site for a working ssl sniffing proxy that carries out a MITM attack using arp spoofing to intercept your gateway, and then auto generates server certs on the fly according to what site you visit.

I suggest you try out TinyCA - a certificate auhtority management tool. Create a CA, then in the CA create a server cert. Install that in a local test web site. Then export the CA cert and put a link to the file on the site. Now click the link in FF. It will prompt to add the CA to your FF cert store and once you do it will accept any certs you create with that CA. Now create a dummy *.paypal.com cert and install that in your site, set the local domain to match paypal.com and load the site.

The only difference between yours and the ones the NSA (or Mafia) has is that they can buy a CA cert from ANY of over 260 existing CAs accpeted by browsers now. If they do then theirs gets accepted without warning.

Unless you go now and disable the weird ones you likely don't really trust.

The fact this is well known is part for the reason some security/privacy organizations are pushing for DNSSEC to mature, They'd like certs to be stored in DNS data, only signed by the real domain, and pushed to your machine by encrypted DNS lookups. You still depend on the root DNS authority for signing but not half the wanna-be CAs worldwide.

-----
> In that case, why has no-one ever managed to produce such a certificate?
See [http://www.schneier.com/](http://www.schneier.com/) [link to article]("http://www.slate.com/id/2265204") about UAE govt mobile phone co that was sold such a CA cert long ago.

-----
In a corporate controlled network environment they can install their own CA cert into every browser under their control either manually (visible warning) or by compiling the browser with a new cert added (no visible warning). Mozilla also provides a tool for managing add/deleting such built-in certs called [certutil]("http://www.mozilla.org/projects/security/pki/nss/tools/certutil.html").

---

### Post by movieman on 2010-09-08
> **BkkBonaza said:**
> Actually they only need one **CA cert**. Not a server cert or client cert.

But with a cert that has the "Certificate Basic Constraints" field set to "Certificate Authority". Then they can create server certificates for **ANY** CN "Common Name" they desire. The only defense is knowing thru a alternate channel which CA the real server cert is signed by because the browser will accept ANY in it's store.

Are you seriously claiming that Firefox will just download a random CA certificate and start using it to verify site certificates because it's signed by some CA it trusts by default? Because that would be so braindead it's hard for me to believe it could possibly be true.

Google doesn't find any definitive answer and Schneier's blog basically just seems to be circular links to articles making claims that don't provide any technical details.

---

### Post by BkkBonanza on 2010-09-08
Well, you're past the first stage (ignorance) and onto denial...

Keep researching and if you really want to know, try it yourself. But unless you can get a trusted CA cert it **will** warn you. My guess is that you'd need a good amount of money (or undeniable govt authority) to get a trusted CA cert, but you can add one manually in FF and test what would occur if you could.

BTW your wording is off a bit. FF doesn't need to download the CA cert if it's signed by a trusted CA. It automatically follows the chain up to the trusted CA. So any site's server cert it is checking is followed up to it's root CA and if that chain results in trust then the server cert is accepted.

Since you only believe sites that sounds "authoritative" I suggest reading about [CAs]("http://en.wikipedia.org/wiki/Certificate_authority"), [Intermediate CA]("http://en.wikipedia.org/wiki/Intermediate_certificate_authorities") and Certs on Wikipedia. It has a decent explanation how the chain of trust works.

This page is interesting too, list of Mozilla [trusted CAs]("http://www.mozilla.org/projects/security/certs/included/").

---

### Post by movieman on 2010-09-08
> **BkkBonaza said:**
> Well, you're past the first stage (ignorance) and onto denial...

No, I'm just waiting for someone to provide some evidence; vague claims that some random site has a CA certificate signed by a trusted CA doesn't tell me anything about what Firefox will do if it makes a connection to a site which sends it that CA certificate.

If it says 'this certificate is signed by Supertrust, Inc, who's listed as able to sign certificates so I'll trust it to sign certificates', then Firefox clearly is completely broken. But since I don't have any such certificate and I haven't seen any indication on the web of what Firefox will do if it receives one, I can't tell.

BTW, I've been involved in cryptography on and off since the early 90s, so being called 'ignorant' is quite amusing.

---

### Post by BkkBonanza on 2010-09-08
> **movieman said:**
> 
If it says 'this certificate is signed by Supertrust, Inc, who's listed as able to sign certificates so I'll trust it to sign certificates', then Firefox clearly is completely broken. But since I don't have any such certificate and I haven't seen any indication on the web of what Firefox will do if it receives one, I can't tell.
Who is SuperTrust? What makes them different as far as you're concerned from eg. 
CNNIC ROOT - Chinese Govt, or
Staat der Nederlanden - Netherlands Govt, or
Kamu SM - Turkish Govt, or
Hongkong Post - well, you can guess.
IdenTrust - a private corp serving the private, commercial and government sectors...

These are just some amongst many that are trusted by Firefox.
They can sign a certificate for any name they choose, that will be accepted by Firefox.

> **movieman said:**
> 
BTW, I've been involved in cryptography on and off since the early 90s, so being called 'ignorant' is quite amusing.
I said you're past ignorance now since now you know about it. You just don't believe it. Obviously you haven't looked into this too deeply.

---

### Post by rookcifer on 2010-09-08
I haven't given the details a whole lot of thought, but I wonder if the PGP web of trust model could somehow be incorporated into the web browser in order to gain extra assurance that a cert is legit?  The nice thing about PGP/GPG is it puts the verification into the hands of the end user (key signing parties, etc.) which means no shady third party has to be trusted. This way a user doesn't have to trust a key he/she (or a trusted friend) did not personally verify and sign.  I would much rather trust a group of individuals who participate in their own browser web of trust than some CA in some not so friendly country (or one ran covertly by FBI or NSA). It could be sort of like the "WOT" browser plugin which alerts the user when a website might be serving malware.  This plugin gets its info from average people around the world.  

The Certificate Patrol plugin will help matters, to be sure, but it's not a magic bullet.  It can only alert you when a cert has changed, but cannot tell you if the original cert (the one in the browser when you first installed the plugin) was itself legit.

The one saving grace is that these attacks require quite a bit of focus by the attacker; that is, a person would have to be targeted individually since the attacker would have to be in between the victim and the destination (most likely at the ISP in the case of the government).  A fairly easy way to "check" if you are being targeted is just to merely ask someone you trust to view the site's certificate and see if it matches yours (again, this is where PGP's web of trust model could come in).  The MITM attack is kind of risky since it isn't that difficult to be found out.  This is why it's probably not likely to be used by law enforcement (they would just subpoena the website for the info), but would be much more up the alley of intelligence agencies, or even more likely, criminal organizations (who don't really care if they're found out since they just want to grab the CC#'s and run).

So, is the sky falling?  Probably not, but unless you are absolutely sure the certificate really is owned by the website operator, you cannot be sure your communications are not being eavesdropped on just because you see the little lock in the browser's toolbar.

EDIT:  It seems at least one project out there is already implementing my aforementioned idea of a PGP web of trust into TLS/SSL:  [http://web.monkeysphere.info/](http://web.monkeysphere.info/)

---

### Post by OpSecShellshock on 2010-09-08
There was a bit of a thing a few months back because someone discovered that Firefox had some weird legacy CA listed that nobody on the development team recognized right away. I believe they identified its origins after some digging, and there wasn't any harm that resulted from it, but it did sort of call attention to the drawbacks of the CA-said-so model.

Oh, for what it's worth (not much) the root name servers have made the DNSSEC transition. That whole thing is still a bit messed up in the first place, though. I mean, how does one company get to maintain one of the root name servers, act as one of the main CA's, and have control over allocation of the two most widely used TLD's?

---

### Post by BkkBonanza on 2010-09-08
I think some sort of network to help gain trusted info about certs is likely a good idea. I don't know quite how it should be organized.

One thing I thought of but haven't put energy into yet towards gaining a stronger trust for the original site fingerprint in Certificate Patrol is to use my handy ssh proxy tunnel to check it from various locations and be sure it matches consistently.

I have a server in UK, and access via one in Germany. Also there are 4 Amazon EC2 regions that I can access on demand for pennies. Including local access that means being able to check 7 paths to the site. God forbid if the link is compromised at their just before their end. 

Maybe a user network where certs can be checked from random locations in an automated fashion would work. Really we just need a consensus amongst some large number of users that a fingerprint is correct and through a WOT approach being able to trust the fingerprint. Certificate Patrol could be designed to automate that in the background (but would then perhaps take on some undesirable liability). 

Just ideas. I'm happy enough for now if CP tells me when it changes. If it does then I have to decide if it was right before or after the change - heart sinks desperately. :(

MonkeySphere looks interesting. Thanks for that.

From that site found link to [article at EFF]("https://www.eff.org/deeplinks/2010/03/researchers-reveal-likelihood-governments-fake-ssl") and [Wired Magazine]("http://www.wired.com/threatlevel/2010/03/packet-forensics/").

---

