---
title: "Question: Secure email with Evolution"
date: 2013-06-25
forum: Security
---

### Post by carverj on 2013-06-25
Hi All,
I am trying to get end to end encryption using email but the recipients are non-technical. So far I am using Evolution mail client on my ubuntu machine, and pulling my mail with SSL pop3 from a Lavabit account. I have a gmail account but am hoping to close that soon. I tried using the software Enlocked for Gmail which I believe uses pGp and Burn Note as well but not sure which is best. Any ideas or suggestions on how to get a secure message to non-techy?
Thanks for your time

---

### Post by TheFu on 2013-06-25
End-to-end encrypted email isn't easy yet.  There many manual steps that must be taken and if any of the users have multiple email devices, setting up all of them to work with encrypted email, safely holding the keys and being consistent across each platform will be difficult.

I use 
* thunderbird
* gpg
* enigmail plugin

I've had to manually modify the gpg init scripts to make everything right after a system reboot. A non-techie user probably wouldn't be able to do that.  My setup is highly non-standard.

I haven't setup Android with gpg yet, but **apg** and **K-9 email **are the tools I think will work.  

For the non-techie people, I haven't a clue.  Perhaps a 1-stop how-to guide that is maintained, current and eventually makes this a 1-click solution per platform would be handy. I dunno.

---

### Post by carverj on 2013-06-26
Yes, I have heard that gpg with 2048 bit key or a strong self signed SSL would work well. Not sure how the latter would work though with Evolution if at all.
For non-techs I was thinking perhaps using a combination of Tor, HTTPs and Burn note might get the job done. Any thoughts on this idea?
Thanks again

---

### Post by TheFu on 2013-06-26
HTTS is broken. If you don't trust a CA, then anyone can act like you and spoof your server.  If you do trust a CA, then governments and less-honest-CA providers can create certs that seem correct and spoof your server again. All of these can become MITM attacks, especially to an untrained/lazy end-user.

With ssh and fail2ban, that isn't possible unless the private key is not private any longer.

Doing secure email is hard. There are lots of little points in the process that can fail, while leaving an impression that everything is working perfectly.  Which is worse, a system that doesn't work at all or a believed-to-be-secure system that isn't secure at all?

TOR is not as secure as people believe. Exit nodes see everything, so guess who runs the most exit nodes around the world? Governments.  HTTPS has the government/rogue-CA flaw.  Some MiTM SSL stuff has been available to enterprises and governments for over a decade - read up on Bluecoat.  Attended an introductory session about a decade ago and was shocked at their capabilities. I think many of the features that original bluecoat systems provided are available as FLOSS for download today. Faster CPUs and GPUs make all that SSL math much quicker.

If your users cannot install GPG, setup keys, configure their email client to use them, then I suggest you run your own email server and give them all accounts. Then you can force TLS and HTTPS connections for all their clients. As soon as email leaves a known-secure "walled garden", all bets are off. Many email server systems don't even bother transmitting server-to-server email encrypted.  That makes email, which humans think of as private, more like postcards.  Actually, that is a really good analogy - a postcard.  If the message goes through a system (any hardware or pipe), then those people/machines can read it.

I think GPG is the only trusted way to have encrypted email and KNOW who can and cannot read it.  X.509 personal certs are a close second, but those were designed so that the certs can include access for others.  I've worked places where my personal X.509 cert had a corporate cert attached, so they could read anything encrypted by it.  In a corporate environment, that makes perfect sense - after all, it is their data, communications, not mine. What would happen if I quit or died. That information could be critical corporate assets. This is good for a corporate/government email system, but could be bad for end-users.  The GPG team was approached to add this to their spec, but I understand they refused, which is why adding GPG to corporate email system is not built-in like x.509 certs are. At least that's my gut feeling.

The way that most companies handle secure communications with their users is by keeping the messages internal to systems that they run. Just look at your bank. They probably have a message system. The most we get is a notification email that a reply has been posted, so we need to login to our account to read it. That same setup is available for us - though I don't know if there is a FLOSS version. I've seen commercial addons for corporate email systems.  Of course, these are all built on the broken HTTPS trust system, but I guess it is better than nothing ... if we can't make a gpg install easy enough to use for everyone.  Hummmmm.

---

### Post by carverj on 2013-06-26
> **TheFu said:**
> HTTS is broken. If you don't trust a CA, then anyone can act like you and spoof your server.  If you do trust a CA, then governments and less-honest-CA providers can create certs that seem correct and spoof your server again. All of these can become MITM attacks, especially to an untrained/lazy end-user.

With ssh and fail2ban, that isn't possible unless the private key is not private any longer.

Doing secure email is hard. There are lots of little points in the process that can fail, while leaving an impression that everything is working perfectly.  Which is worse, a system that doesn't work at all or a believed-to-be-secure system that isn't secure at all?

TOR is not as secure as people believe. Exit nodes see everything, so guess who runs the most exit nodes around the world? Governments.  HTTPS has the government/rogue-CA flaw.  Some MiTM SSL stuff has been available to enterprises and governments for over a decade - read up on Bluecoat.  Attended an introductory session about a decade ago and was shocked at their capabilities. I think many of the features that original bluecoat systems provided are available as FLOSS for download today. Faster CPUs and GPUs make all that SSL math much quicker.

If your users cannot install GPG, setup keys, configure their email client to use them, then I suggest you run your own email server and give them all accounts. Then you can force TLS and HTTPS connections for all their clients. As soon as email leaves a known-secure "walled garden", all bets are off. Many email server systems don't even bother transmitting server-to-server email encrypted.  That makes email, which humans think of as private, more like postcards.  Actually, that is a really good analogy - a postcard.  If the message goes through a system (any hardware or pipe), then those people/machines can read it.

I think GPG is the only trusted way to have encrypted email and KNOW who can and cannot read it.  X.509 personal certs are a close second, but those were designed so that the certs can include access for others.  I've worked places where my personal X.509 cert had a corporate cert attached, so they could read anything encrypted by it.  In a corporate environment, that makes perfect sense - after all, it is their data, communications, not mine. What would happen if I quit or died. That information could be critical corporate assets. This is good for a corporate/government email system, but could be bad for end-users.  The GPG team was approached to add this to their spec, but I understand they refused, which is why adding GPG to corporate email system is not built-in like x.509 certs are. At least that's my gut feeling.

The way that most companies handle secure communications with their users is by keeping the messages internal to systems that they run. Just look at your bank. They probably have a message system. The most we get is a notification email that a reply has been posted, so we need to login to our account to read it. That same setup is available for us - though I don't know if there is a FLOSS version. I've seen commercial addons for corporate email systems.  Of course, these are all built on the broken HTTPS trust system, but I guess it is better than nothing ... if we can't make a gpg install easy enough to use for everyone.  Hummmmm.

Right, OK. I hadn't heard of Bluecoat thanks for the heads up.
OKmgotcha. So if one were to build a mail server with clients that connected via a securer method other than https that would work well. The problem remains to get a public key to non-techs. Post a letter with USB with an preconfigured email client probably the best way.

---

### Post by TheFu on 2013-06-26
> **carverj said:**
> Right, OK. I hadn't heard of Bluecoat thanks for the heads up.
OKmgotcha. So if one were to build a mail server with clients that connected via a securer method other than https that would work well. The problem remains to get a public key to non-techs. Post a letter with USB with an preconfigured email client probably the best way.

Actually, anyone using any email client for IMAPS or POP3S and SMTPS access will  likely be using 3rd party certs - these are broken just like HTTPS certs for the same reason. 
If the certs are locally generated (self-signed), a MITM attack is possible still. Both are problems.  Basically, there is a small, but real, risk that a determined entity could intercept AND read the encrypted contents.  In the last few years, a number of CAs have been compromised and certificates pretending to be from huge, well-known world-wide companies have been uncovered. I have no faith in that method at all.  Is appears that the entire world is living with their heads shoved in the sand over these flaws.

IMHO, Only encryption that doesn't depend on trusting 3rd parties, should be trusted.  GPG fits. That is my opinion and perhaps this is too high a technology hill for average people to climb?  Some encryption is better than none, but a false sense of security when there are known flaws is much worse.  Perhaps others have a different perspective, but if the encryption is possible to get around, is it still worthwhile?  Without 100% trust in the method .... where are? 

When using gpg, It is very important that the private key be
* created by the individual (without someone else or any untrusted programs involved)
* never shared with anyone else
* never accidentally released anywhere
* safely backed up in 2-20 different locations ... inside extremely secure encryption.

I fear that most end-users aren't prepared for this, so their private key will "get out" and render all their encryption efforts useless.  Perhaps the difficulty of GPG use is a self-selecting technique to ensure only people serious about all this stuff **can** get it working?

Trust is a key part of this, so if I can't trust that the recipient will properly manage their private key.  
A friend of mine is likely to be sued for divorce, we routinely use encrypted email for communications.  I've asked her to delete all old messages, so a subpoena doesn't force those email to be released. While she hasn't refused, she has not clearly agreed to delete them.  I'm positive that she will follow whatever a judge requires, so if a demand for access to the email happens AND she still has the emails around, then the content will become part of the court case.  I take this trust seriously and have deleted all emails to/from her on my side.  If she doesn't delete them on her side, I will probably stop emailing her anything remotely private. 

It is about trust.

---

### Post by carverj on 2013-06-27
I had a test run to a Windows 7 client and might have to come back to it in future when gPg a bit more widespread.
Meantime, I will have to rely on as much TLS/HTTPS as possible with some anonymity (Tor) and then whichever is strongest of:-

[http://www.crypo.com/](http://www.crypo.com/) 
[http://www.encrypt-easy.com/encrypt-text](http://www.encrypt-easy.com/encrypt-text) (Blowfish)
Enlocked plugin ([http://www.enlocked.com/Works.html](http://www.enlocked.com/Works.html))
[https://burnnote.com/](https://burnnote.com/) (Only a link is provided in the message and this link will point to nothing once message has been read)

Ideas, preference or suggestions welcome

---

### Post by TheFu on 2013-06-27
Well, for sharing "sensitive data" with others, the only solution that I've been able to get them to use is encrypted ZIP files with a non-trivial, 30+ character passphrase.  Everything else was simply too hard.

I don't think all ZIP tools and formats are created equal and they definitely ARE NOT 100% compatible, so use the most standard possible.  Plus know that ZIP passwords can be brute forced - tools have existed for decades to efficiently attack a ZIP file with a few billion attempts per second.  Create a password accordingly with that knowledge in mind.  I think all 8 character passwords can be attempted in under 1 hour on a slow PC, but it has been a few years since I even bothered trying to crack a ZIP file using a professional tool.

OTOH, you should have seen the smile on my face when our corporate accountants emailed some information and used an encrypted ZIP file with our pre-agreed key.  I was so proud. ;)

---

### Post by carverj on 2013-06-28
That is great thank you, a good interim solution until gPg for non-techs is very smooth. 7z and winzip seem pretty compatible and both capable of AES-256 encryption. Will just need to share passphrase safely first. Thanks again

---

### Post by Blitzkriegz on 2013-06-29
Are your contacts using Windows or Ubuntu? Nontech = Windows to me. A simple way to encrypt information for unsophisticated contacts is with the Microsoft Office suite (2007 and newer). It uses AES-256 and is decent as long as you use a strong password that you don't email along with the encrypted document. You can use gmail for that. The contents of the email will be secured but who you're emailing will be discoverable.

---

### Post by TheFu on 2013-06-30
> **Blitzkriegz said:**
> Are your contacts using Windows or Ubuntu? Nontech = Windows to me. A simple way to encrypt information for unsophisticated contacts is with the Microsoft Office suite (2007 and newer). It uses AES-256 and is decent as long as you use a strong password that you don't email along with the encrypted document. You can use gmail for that. The contents of the email will be secured but who you're emailing will be discoverable.

Very few of my current contacts have Microsoft Office, so this isn't really an option.  Most end-users don't get MS-Office on their home PCs.

Then there is the question as to whether anyone should propagate the use of $300-$500 proprietary software just to read email?

Yesterday, I discovered a new TWiT show ... "Know How ..."  [http://twit.tv/kh](http://twit.tv/kh) They did an episode about setting up GPG with Thunderbird and Enigmail. Also showed a browser-only option using some plugin for Firefox and Chrome (don't know if Chromium works).  I'm not a fan of browser plugins for gpg - seems like a deck of cards from a security standpoint.  The demonstrators seemed a little less knowledgeable about security than I would have liked too.  To the point that I'm not certain about the security of their installs. Anyway, it was an interesting show even if they left out gpg key signing and uploading our public keys to key servers completely.

Again, sorry this isn't about Evolution.

LATE UPDATE:
[http://lifehacker.com/how-to-encrypt-your-email-and-keep-your-conversations-p-1133495744](http://lifehacker.com/how-to-encrypt-your-email-and-keep-your-conversations-p-1133495744) explains installation for GPG, enigmail, thunderbird and keys.

---

