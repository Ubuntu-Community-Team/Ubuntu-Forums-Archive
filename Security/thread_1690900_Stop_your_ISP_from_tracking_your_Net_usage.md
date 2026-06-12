---
title: "Stop your ISP from tracking your Net usage"
date: 2011-02-19
forum: Security
---

### Post by Acheron3 on 2011-02-19
Hi, I've been reading an interesting _[COLOR=PaleGreen][article]("http://www.talktalkmembers.com/forums/showthread.php?t=18773")[/COLOR]_ about the fact that ISPs are able to collect net data from web users. 
What I think It's missing in the article is that in some locations it's [compulsory]("http://www.tecnoiuris.com.ar/publicaciones/proteccion-datos-personales1.php") for ISPs to collect and save all your networking data (For example, in Spain, where I live, it's compusory to store people's activity on the net for a period of 6 months (minimum) to 2 years (maximum).
In the article they state that _[Witopia]("http://alternativeto.net/software/witopia/")_ can do the job of encrypting your browsing activity and therefore mantain your privacy. Do you know any open source or, at least, free alternative to Witopia? What do you think about the article and about the ways of safeguarding your privacy?

Cheers.

Acheron3

---

### Post by An Sanct on 2011-02-19
You can use [tor network]("http://www.torproject.org/") to encrypt your browsing. I also know, that there is a plugin for Firefox, called tor button (search in that direction ;))

---

### Post by kerry_s on 2011-02-19
privacy is a myth in these times.
information is a part of modern society.
right now someone is buying or selling your info, there's nothing you can do.

go here, type your name, see how much is out there about you.
[http://www.spokeo.com/](http://www.spokeo.com/)

---

### Post by An Sanct on 2011-02-19
> **kerry_s said:**
> privacy is a myth in these times.
information is a part of modern society.
right now someone is buying or selling your info, there's nothing you can do.

go here, type your name, see how much is out there about you.
[http://www.spokeo.com/](http://www.spokeo.com/)

Tried my name ... it had zero hits :) and asked me if I type the name correctly... I did ;)

But I'm a security freak ... I even shred my old mail (the actual physical snail mail).

---

### Post by Acheron3 on 2011-02-19
> 
privacy is a myth in these times.
information is a part of modern society.
right now someone is buying or selling your info, there's nothing you can do.
Yes, I agree that our data is more and more exposed to the world every day. However I think we should be able to make moves to minimize this exposure.
I recommend you _*[Track Me If You Can]("http://www.imdb.com/title/tt1754781/")*_ documentary, if you have not already seen it.

> 
Tried my name ... it had zero hits :smile: and asked me if I type the name correctly... I did :wink:
0 hits too haha. xd

> 
You can use _[tor network]("http://www.torproject.org/")_ to encrypt your browsing. I also know, that there is a plugin for Firefox, called tor button (search in that direction :wink:)
Hey I think Tor it's a very useful resource! Thank you. In addition it's quite easy to _[install]("http://www.torproject.org/docs/debian.html.en")_ in ubuntu.
I've done some research about it and I have found that although it's a very good program to protect the transport of data it doesn't protect you from sites you visit to see your     identifying information. 
In order to solve this and to have a pretty complete privacy protection in your browser you could just try to _[connect]("http://www.privoxy.org/faq/misc.html#TOR")_ Tor with a proxy like _[Privoxy]("http://www.privoxy.org/")_.
I've done that and it seems to work althought browsing have become quite slow.

Cheers.

---

### Post by tjwoosta on 2011-02-19
> **kerry_s said:**
> privacy is a myth in these times.
information is a part of modern society.
right now someone is buying or selling your info, there's nothing you can do.

go here, type your name, see how much is out there about you.
[http://www.spokeo.com/](http://www.spokeo.com/)

Neat site, thanks for sharing :)

My username and email came up with my accounts for all the sites that I registered for using the same username and/or email, but I never fill out any personal information on those sites and when I do its a lie, so really they know nothing about me. Ive also never used data mining sites like facebook, myspace, twitter, etc.. ;)

My real name came up with hundreds of hits from people with the same name, which when narrowed down using information that most people wouldnt know about me, I did find my address, but thats about it.

Im sure our government knows everything about me (what school i attended, what was my gpa, where I work, who my friends are, my anual income, etc..) but thats another matter.

---

### Post by teejaybee on 2011-02-19
Firstly you have to see if there are laws prohibiting you from bypassing monitoring measures.

Information passed through the Tor network has to be decrypted at some point, and these "exit points" have been used in the past by people with appropriate skills to obtain information. Personally, i'd never use it.

If I wanted to avoid my ISP monitoring my web traffic i'd purchase a hosted server somewhere else and tunnel to that. Most ISP's would only monitor home/business outgoing web traffic and not co-located server web traffic.

Even this solution is vulnerable to monitoring but being further up the chain than your home connection makes it less likely.

Use HTTPS wherever possible.

---

### Post by tjwoosta on 2011-02-19
@teejaybee

Tor is ok for anonymity but not security.

Anyone can host an exit node, and anyone with an exit node can sniff the information, but they dont know where it originated (unless your sending info that gives you away) i.e anonymous but insecure.

It goes from your machine encrypted to the 1st node, which passes it to a 2nd node, then a 3rd, and so forth until it reaches the exit node where its decrypted. Only the master servers know the full route, all logs are stored on ram disks (volatile memory), and theyre deleted after 24 hours irrevocably. If however they are confronted by law enforcement officials with a warrant before that 24 hours is up they are bound by law to hand over whatever  they have.

---

### Post by uRock on 2011-02-19
I see nothing wrong with the ISP monitoring what you are doing via their equipment. It is their equipment and I am sure that their license agreement tells you that they have the right to do so.

If you have LoJack in your car, then how do you know when it is being monitored? You don't.

---

### Post by tjwoosta on 2011-02-19
> **uRock said:**
> I see nothing wrong with the ISP monitoring what you are doing via their equipment. It is their equipment and I am sure that their license agreement tells you that they have the right to do so.

If you have LoJack in your car, then how do you know when it is being monitored? You don't.

I wouldnt mind, if they only kept it to themselves. My issue is when they start sharing it with anybody willing to pay.

---

### Post by lisati on 2011-02-19
I tried out the spokeo site and it returned information from the "wrong" country. A simple geolocation lookup would have at least pointed them a bit closer to home. Even if I'd been using a proxy, it's sometimes possible to detect that I'm doing so.

---

### Post by handy on 2011-02-19
Yes, spokeo only worked on the USA when I tried it.

---

### Post by bhaverkamp on 2011-02-19
So you're fine with the phone company listening in on your phone calls too! You are using their equipment as well...

---

### Post by PaulReaver on 2011-02-19
tor and privoxy should have you sorted....

onion routing... layers.... like shrek

---

### Post by uRock on 2011-02-20
> **bhaverkamp said:**
> So you're fine with the phone company listening in on your phone calls too! You are using their equipment as well...
Phones are protected by law from being monitored, the Internet is not. ISPs can record as much info as they want, but they can not read encrypted material, which is all that matters to me. Do you really think ISPs have the capability to record all traffic?

I have not seen an email carrier that bars encrypted email and my Thunderbird has multiple keys in use.

---

### Post by Diametric on 2011-02-21
Yes, however the same argument could be made about renting an apartment or house.  While you pay rent, that property is "yours" and the owner usually has to give written notice before entering the premises.  I feel the same laws should apply to an ISP.  I pay a monthly bill to use their equipment - and thusly all data I generate should be considered mine.  A realistic implemetation of this could be to charge some folks a higher rate to not have their data stored, or offer a lower rate to those who agree to have their data tracked and marketed to.

---

### Post by uRock on 2011-02-21
> **Diametric said:**
> Yes, however the same argument could be made about renting an apartment or house.  While you pay rent, that property is "yours" and the owner usually has to give written notice before entering the premises.  I feel the same laws should apply to an ISP.  I pay a monthly bill to use their equipment - and thusly all data I generate should be considered mine.  A realistic implemetation of this could be to charge some folks a higher rate to not have their data stored, or offer a lower rate to those who agree to have their data tracked and marketed to.
I have seen no proof that ISPs keep information. The fact that piracy and torrenting are unchecked tells me that they do not care to store any user data.

Anyway, this isn't the cafe and the question of this thread is to find a way to protect information, not argue over the legalities of the problem.

---

### Post by dave2001 on 2011-02-22
As a reminder, privacy/security when using a proxy service is only as good as the server your using. If those who maintain the service have questionable practices (as many free proxy services often do) then you might be worse off than without a proxy.

There are many proxy services which have good reputations, excellent bankwidth, and even offer encryption, but they will demand payment.

---

### Post by BigCityCat on 2011-02-22
> **kerry_s said:**
> privacy is a myth in these times.
information is a part of modern society.
right now someone is buying or selling your info, there's nothing you can do.

go here, type your name, see how much is out there about you.
[http://www.spokeo.com/](http://www.spokeo.com/)

My name is Paul Smith. Do you think they have anything on me?

---

### Post by tubbygweilo on 2011-02-24
ISPs can track most if not all the sites you visit and although they can show visits to proxy sites I still expect they can peek into proxy and vpn sites but are you really worth the effort? Another way of tracking is to look for common usernames across forums or derivations of a username and explore via google or other search engine.

---

### Post by perspectoff on 2011-02-24
> **uRock said:**
> I have seen no proof that ISPs keep information. The fact that piracy and torrenting are unchecked tells me that they do not care to store any user data.



I went into a smaller ISP's corporate office a few times. 

They had multiple monitors that scanned the traffic that passed through the ISP. I was appalled. 

Remember the type of geek that goes into computers -- often without a real life, spending all day on tech forums, a little bit of "know-it-all" to them.

Such people are happy to scan clients' traffic "for security reasons" simply because they have nothing better to do.

Now comes WikiLeaks, where a compendium of such traffic is put online for all to see.

Encrypt all email (using PGP-enabled encrypters available for all email programs, including Thunderbird, Evolution, and KMail). Tor is a good idea, but it was set up with assistance from the US military and there are some nodes in it that the military uses, as well as organised crime.

Tor is not enough. Encryption is more important.

Man-in-the-middle attacks are insidious and commonplace these days, making keyed encryption critical.

There's a reason Shuttleworth made a fortune with security certificates, but even these can be spoofed.

SSL is important.

OpenSSH (key connections, not password connections) or OpenVPN for remote connections is important.

Avoiding the "cloud" (where your data is under anyone and everyone's control) is important.

Firewalls and knockd are important to minimise attacks, DoS, etc.

Good fences make good neighbors.

---

### Post by FrankenCub on 2011-03-03
> Tried my name ... it had zero hits  and asked me if I type the name correctly... I did 

But I'm a security freak ... I even shred my old mail (the actual physical snail mail).


LMAO...I just tried my name and it looks like I finally got a pay raise :D
$100,000 increase !

---

