---
title: "Anonymous Web Browsing"
date: 2012-03-19
forum: Security
---

### Post by yarddogg77 on 2012-03-19
Hi all. I'm not a total newbie to linux, I've been using it for 6 years. I more or less know my way around but have a lot to learn. Right now I'm trying to learn the basics about how to mask myself and be invisible from the network. I have googled for a few hours, but like usual, most blogs are garbage and not very detailed. Too many acronyms, poorly written tutorials etc... 

Anyway, I want to learn the best way to become completely invisible when I'm surfing on line. No offense to other newbies, but I would like some class A advice from a veteran, hopefully in lay terms. Thank you.

---

### Post by zombifier25 on 2012-03-20
If you want to be anonymous, then the [Tor Browser Bundle](https://www.torproject.org/download/download-easy.html.en) is a good program to use. Just extract it and you'll be masked behind the Tor network, which is IMHO the best anonymous network out there. You can read on how Tor works at its website. Note that only the browser is routed through Tor. You can set up your entire system to use Tor, but I don't think you need to.
Another tool I recommend is [DNSCrypt](http://www.webupd8.org/2012/02/encrypt-dns-traffic-in-linux-with.html). It encrypts all DNS requests, preventing MITM attacks.
And if you are REALLY paranoid, use  [TAILS](https://tails.boum.org/). It's a live CD/USB that  directs all connection through Tor, leaves no trace on your computer,  encrypts all your files,...
However, to be truly anonymous, the first and foremost advice is: Don't do anything stupid that can give away your identity. You may have all the anonymity tools available, but if you're stupid, then no one can save you. Don't give away your login information, email address, etc.

---

### Post by Paqman on 2012-03-20
> **zombifier25 said:**
> You can set up your entire system to use Tor, but I don't think you need to.


I agree, there's a lot of stuff that it's bad netiquette to use through Tor. Bandwidth is severely limited, so don't use it for any bandwidth-hungry stuff like torrents or streaming video/audio. There are people who genuinely need Tor to stay safe online, and it's not fair to hog the network.

Even if you just use it for a bit of browsing you should be aware that it's very, very slow. You may not find it a particularly enjoyable browsing experience. But it is fairly anonymous.

---

### Post by Lars Noodén on 2012-03-20
Also your [web browser gives away information](https://panopticlick.eff.org/) that can be used to track or help track you.  Again the tor browser bundle can help with that but it is one item you'll want to check for yourself and make adjustments if necessary.

---

### Post by Grenage on 2012-03-20
> **yarddogg77 said:**
> Anyway, I want to learn the best way to become completely invisible when I'm surfing on line. No offense to other newbies, but I would like some class A advice from a veteran, hopefully in lay terms. Thank you. 

Here's some class A advice - total net anonymity is a myth.

---

### Post by tubbygweilo on 2012-03-20
yarddogg77,
May I suggest searching / browsing via [https://www.ixquick.com/]("https://www.ixquick.com/") not only do they have a good [privacy policy]("https://www.ixquick.com/uk/protect-privacy.html") but an encrypted proxy is offered as an alternative with each link returned. The usual rules apply of using it for low bandwidth browsing rather than video, music or torrents.

---

### Post by zombifier25 on 2012-03-20
> **Grenage said:**
> Here's some class A advice - total net anonymity is a myth.
I have read somewhere that everyone on the Internet has a posting pattern, which almost everyone don't even realize they have. It's possible to reveal the information of an individual if they analyze it. Very difficult work, but possible.

---

### Post by ubunbu on 2012-03-20
> **zombifier25 said:**
> I have read somewhere that everyone on the Internet has a posting pattern, which almost everyone don't even realize they have. It's possible to reveal the information of an individual if they analyze it. Very difficult work, but possible.

 Just use quotes a lot. :P

---

### Post by noobgirl on 2012-03-21
so true.
 
> **Grenage said:**
> Here's some class A advice - total net anonymity is a myth.

---

### Post by 0011235813 on 2012-03-22
> **Grenage said:**
> Here's some class A advice - total net anonymity is a myth.
Of course, but the standard configuration for browsers etc. gives away a lot of information, services like tor will increase your anonymity dramatically, if not completely (some technical babble about predicting tor nodes or whatever *yawn*) . 
> **Lars Noodén said:**
> Also your [web browser gives away information](https://panopticlick.eff.org/) that can be used to track or help track you.  Again the tor browser bundle can help with that but it is one item you'll want to check for yourself and make adjustments if necessary.
Yeah, for some reason, The Internet has decided that everyone using it should tell the world where they live, what service provider they have, what browser they use, what operating system they have...
Firefox can spoof the **U**ser **A**gent (UA) as well as Opera and a few others, ask me if you want to know how.

> **zombifier25 said:**
> If you want to be anonymous, then the [Tor Browser Bundle](https://www.torproject.org/download/download-easy.html.en) is a good program to use. Just extract it and you'll be masked behind the Tor network, which is IMHO the best anonymous network out there. You can read on how Tor works at its website. Note that only the browser is routed through Tor. You can set up your entire system to use Tor, but I don't think you need to.
Another tool I recommend is [DNSCrypt](http://www.webupd8.org/2012/02/encrypt-dns-traffic-in-linux-with.html). It encrypts all DNS requests, preventing MITM attacks.
And if you are REALLY paranoid, use  [TAILS](https://tails.boum.org/). It's a live CD/USB that  directs all connection through Tor, leaves no trace on your computer,  encrypts all your files,...
However, to be truly anonymous, the first and foremost advice is: Don't do anything stupid that can give away your identity. You may have all the anonymity tools available, but if you're stupid, then no one can save you. Don't give away your login information, email address, etc.
Not sure why anyone would need to go through the pain of installing tor browser when they can just install tor-network-tools from the repos (itories) and configure their browser to run like tor browser, i.e block JS (JavaScript) cookies etc.

Do be aware that the service for encrypting DNS lookups requires OpenDNS which I don't recommend is it is more of a content filter than a security service, I would suggest Google Public DNS or some of the DNS services some anti-virus makers have come up with.

+1 to the last bit.

Note: Tor is probably the fastest free anonymity proxy available, but it is still pretty slow.

---

### Post by MasterGamerJK on 2012-03-22
> **Grenage said:**
> Here's some class A advice - total net anonymity is a myth.


Not exactly....take it from a security professional. It is all about WHAT and where you do online that determines who you are.

---

### Post by VinDSL on 2012-03-22
> **yarddogg77 said:**
> I would like some class A advice from a veteran, hopefully in lay terms. Thank you.
For browsing, best way is WarDriving, so called.

Second best is kiosks at public libraries.

For email, encrypt your message(s) inside .jpg attachments.

---

### Post by sammiev on 2012-03-22
> **yarddogg77 said:**
> Hi all. I'm not a total newbie to linux, I've been using it for 6 years. I more or less know my way around but have a lot to learn. Right now I'm trying to learn the basics about how to mask myself and be invisible from the network. I have googled for a few hours, but like usual, most blogs are garbage and not very detailed. Too many acronyms, poorly written tutorials etc... 

Anyway, I want to learn the best way to become completely invisible when I'm surfing on line. No offense to other newbies, but I would like some class A advice from a veteran, hopefully in lay terms. Thank you.

The best way to protect your self is to stay off the net. I use [this]("https://www.witopia.net/") VPN which has been great to me so far.

---

### Post by spynappels on 2012-03-23
> **MasterGamerJK said:**
> Not exactly....take it from a security professional. It is all about WHAT and where you do online that determines who you are.

That does not change that total net anonymity is a myth, as Grenage said.

---

### Post by spynappels on 2012-03-23
> **VinDSL said:**
> For browsing, best way is WarDriving, so called.


Except that this is viewed as theft or even breaking and entering in some jurisdictions and thus illegal.

Dishonestly obtaining electronic communication services is an offense under Section 125 of the U.K. 2003 Communications Act, while unauthorized access to computer material is a summary offense under Section 1 of the 1990 Computer Misuse Act.

---

### Post by tubbygweilo on 2012-03-23
Just a thought as Queensland Police to Look For Unsecured WiFi Spots.

via [slashdot.org]("http://mobile.slashdot.org/story/12/03/23/039239/queensland-police-to-look-for-unsecured-wifi-spots")

---

### Post by VinDSL on 2012-03-23
> **spynappels said:**
> Except that this is viewed as theft or even breaking and entering in some jurisdictions and thus illegal.
Set your Wifi SSID to INTERPOL_SURVEILLANCE_VAN and the cops will leave you alone.

---

### Post by 0011235813 on 2012-03-23
> **sammiev said:**
> The best way to protect your self is to stay off the net. I use [this]("https://www.witopia.net/") VPN which has been great to me so far.

+1 thanks for that.

---

### Post by haqking on 2012-03-23
> **spynappels said:**
> Except that this is viewed as theft or even breaking and entering in some jurisdictions and thus illegal.

Dishonestly obtaining electronic communication services is an offense under Section 125 of the U.K. 2003 Communications Act, while unauthorized access to computer material is a summary offense under Section 1 of the 1990 Computer Misuse Act.

you are confused with piggybacking.

wardriving is not illegal

[http://www.sans.org/reading_room/whitepapers/wireless/avoid-ethical-legal-issues-wireless-network-discovery_176](http://www.sans.org/reading_room/whitepapers/wireless/avoid-ethical-legal-issues-wireless-network-discovery_176) section 5.1

---

### Post by spynappels on 2012-03-24
> **haqking said:**
> you are confused with piggybacking.

wardriving is not illegal

True, but the poster I was replying to was using it in the piggyback sense, and that was what I was referring to as illegal in the UK.

---

### Post by haqking on 2012-03-24
> **spynappels said:**
> True, but the poster I was replying to was using it in the piggyback sense, and that was what I was referring to as illegal in the UK.

no worries.

i was just clarifying the terms for others reading, it is often misunderstood that wardriving is a active attack vector and classed as illegal when it isnt.

Cheers

---

### Post by VinDSL on 2012-03-24
3 words you need to remember:

[LIST=1]
[*]Who
[*]What
[*]Huh
[/LIST]

Pronounced: Who? Wha? Huh?

You can intermix them, like:

[LIST]
[*]Who wha huh?
[*]Huh? Who wha?
[*]Wha? Huh? Who?
[/LIST]

When asked any questions, the answer is always the same:

[LIST]
[*]I don't know what you're talking about!
[*]Or...
[*]I still don't know what you're talking about!
[/LIST]

Of course, you can combine all of these... 
[LIST]
[*]Who? Wha? Huh?  I don't know what you're talking about.
[/LIST]

It's called plausible deniability.

After all, we don't know nothing about computers, right? ;)

---

### Post by dvp786 on 2012-08-30
sometimes ago i tried this website: [www.anonymously.in]("http://www.anonymously.in")

I think it works, it can hide your IP, and allows u to handle cookies and referral info.

thnx ;)

---

### Post by dodo3773 on 2012-08-30
> **Grenage said:**
> Here's some class A advice - total net anonymity is a myth.

This ^^. Closest thing would probably be to chain proxies, spoof your mac address & user agent, and use someone else's network. Aside from that do not do anything to break your anonymity (checking email, updating your system, logging into websites, etc, etc.. (common sense goes a long way sometimes...)).

---

### Post by Hungry Man on 2012-08-30
Chaining proxies won't do you much good without encryption between each network. You can achieve perfect forward secrecy through TOR - that's not a myth.

You can also use something like netcat.

Typical SSL

A -> C - > D

A and C create private/public key and C and D create private and public key, A and D don't connect.

NetCat goes

A -> C  -> D

A and D share their public keys as private keys leaving C only acting as a forwarder.

---

### Post by rookcifer on 2012-08-30
> **Grenage said:**
> Here's some class A advice - total net anonymity is a myth.

If that were true, then all hackers would be caught.  They obviously aren't.  There are ways to hide, but it takes some work and some expertise.

---

### Post by BrianBlaze on 2012-08-30
Such a weird and almost illegal question so here is my smart *** illegal answer... use a neighbors WIFI haha

---

### Post by sammiev on 2012-08-30
> **BrianBlaze said:**
> Such a weird and almost illegal question so here is my smart *** illegal answer... use a neighbors WIFI haha

If your band with was a little better, I would be using yours! :lolflag:

---

### Post by Stonecold1995 on 2012-09-03
> **Hungry Man said:**
> Chaining proxies won't do you much good without encryption between each network. You can achieve perfect forward secrecy through TOR - that's not a myth.

You can also use something like netcat.

Typical SSL

A -> C - > D

A and C create private/public key and C and D create private and public key, A and D don't connect.

NetCat goes

A -> C  -> D

A and D share their public keys as private keys leaving C only acting as a forwarder.

That's not true.  While Tor is virtually unbreakable with today's technology, there ARE attacks against Tor, like timing attacks, social engineering and phishing attacks, and attacks that use things like Flash and Java to "phone home" and reveal your IP.  Plus, Tor uses 128-bit AES (I think) which is technically breakable, although not with today's computational power.  But it IS technically possible to decrypt Tor encryption, and it is very possible to use other attacks on the network (DDoSing a popular Tor node to see how the relay re-forms, etc).  The only way for Tor to be unbreakable would be to have the relay node(s) 100% trustworthy (including trusting that it can't be hacked), and for the encryption to use a one-time pad.

There *are* plenty of ways to break through Tor, but most of those rely on the target's foolishness (e.g. successful attack using Flash because the target has scripts enabled, or the target logging in to his e-mail within 10 minutes of logging in to an illegal site).

There is no way to achieve perfect security while still being able to browse the web, etc (disabling your wireless card would make you invincible to attacks through the network, but that doesn't seem like a very practical solution).

---

### Post by rookcifer on 2012-09-04
> **Stonecold1995 said:**
> Plus, Tor uses 128-bit AES (I think) which is technically breakable, although not with today's computational power. 

Tor uses public-keys and AES.  It uses RSA 1024 I believe (they may have upgraded to 2048 bit).  The AES key is encrypted with the public key. This is known as a hybrid cryptosystem.

And AES-128 isn't breakable even with all the computing power on the earth.  Of course it's possible NSA has some super secret method of cryptanalyzing it, but they aren't going to break it with brute force.

>  But it IS technically possible to decrypt Tor encryption, and it is very possible to use other attacks on the network (DDoSing a popular Tor node to see how the relay re-forms, etc).  The only way for Tor to be unbreakable would be to have the relay node(s) 100% trustworthy (including trusting that it can't be hacked), and for the encryption to use a one-time pad.

While it's true Tor isn't perfect, one-time-pads are useless in practice.  How do you propose for them to distribute keys with a OTP?  It's impossible.  That's why we have public-key crypto like RSA.  If OTP's solved everything, cryptography would have stopped back in the 1920's.  Sure OTP's are unbreakable but who cares when you can't distribute keys?  Not only that but they key has to be the length of the message (thus if you download a 2 GB file, you need 2 GB's of key).  And you can never ever reuse a key, thus each bit of data must be encrypted uniquely each time.  And not only that but you need a perfect RNG (dice rolls or card shuffling, etc.)  This is why OTP's are fine for spies behind enemy lines using a pencil and paper to decode short messages over short-wave radio (look up "numbers stations" on YouTube), but it's not very practical in the computer age.

> There is no way to achieve perfect security while still being able to browse the web, etc (disabling your wireless card would make you invincible to attacks through the network, but that doesn't seem like a very practical solution).

That's probably true unless you resort to illegal methods. It always a cat and mouse game.

---

### Post by Stonecold1995 on 2012-09-04
> **rookcifer said:**
> While it's true Tor isn't perfect, one-time-pads are useless in practice.  How do you propose for them to distribute keys with a OTP?  It's impossible.  That's why we have public-key crypto like RSA.  If OTP's solved everything, cryptography would have stopped back in the 1920's.  Sure OTP's are unbreakable but who cares when you can't distribute keys?  Not only that but they key has to be the length of the message (thus if you download a 2 GB file, you need 2 GB's of key).  And you can never ever reuse a key, thus each bit of data must be encrypted uniquely each time.  And not only that but you need a perfect RNG (dice rolls or card shuffling, etc.)  This is why OTP's are fine for spies behind enemy lines using a pencil and paper to decode short messages over short-wave radio (look up "numbers stations" on YouTube), but it's not very practical in the computer age.

My whole point was that it was practically impossible.  There is no way to make a node 100% trustworthy and a one-time pad is completely impractical, if possible at all. :roll:

---

