---
title: "Protecting my privacy"
date: 2010-06-12
forum: Security
---

### Post by SonOfOdin on 2010-06-12
Heya

Intrepid Ibex (U8.10) is what I am using presently and I would like to know if there are measures that I can take to prevent my ISP from keeping data that flows between my PC and it.

I am living in Australia, I am wanting to keep the bastards (read: Australian Government) ignorant about what I use my PC for.

Its them storing any of my personal information that I am worried about, but if I can keep my history from them completely, even better...

Cheers for all and any help,

---

### Post by CharlesA on 2010-06-12
There is no real way to keep them from "keeping" data, but you could tunnel your traffic over an SSH tunnel so that it would be encrypted.

---

### Post by Rubi1200 on 2010-06-12
This might be of interest to you:

[http://en.wikipedia.org/wiki/Telecommunications_data_retention#Protection_against_data_retention](http://en.wikipedia.org/wiki/Telecommunications_data_retention#Protection_against_data_retention)

To be perfectly honest, I have to wonder what you are doing that you are so concerned about revealing.

> I am living in Australia, I am wanting to keep the bastards (read: Australian Government) ignorant about what I use my PC for.

Privacy is a concern for most, if not all, computer users. However, your language usage suggests something more than that.

---

### Post by HermanAB on 2010-06-12
You need to rent a server in another country - USA, Singapore, wherever.  Then you set up a SSH encrypted tunnel to that server.

Of course, then you are at the mercy of the government and ISP in that country.

---

### Post by OpSecShellshock on 2010-06-12
I believe the reason that Australia is of particular relevance here is due to recent news that the government wishes to require ISPs to retain information beyond what's relevant for properly billing users and allocating network resources. I've seen some rumors that it would go so far as to require that ISPs store anything available in plain text, including all header data and browser history. I don't know, for the children or something?

---

### Post by Rubi1200 on 2010-06-12
A quick look around Google suggests there may be little, if anything, that could be done to prevent this type of information retention.

---

### Post by SonOfOdin on 2010-06-12
Believe me, my actions are not nefarious.  

It has just been announced in the local media that the Australian Government is planning to force ISP's to keep all transmitted data, amidst a massive backlash aimed at Google for snooping wireless internet accounts recently.  Its a counter terrorism manoeuvre / big brother thing... 

I dont want to be implicated in copyright infringment any more than the next person, but honestly, Im worried about credit card / bank transactions being intercepted and misused more than anything.  I do torrent, books mainly and I have a small but growing mp3 collection.  Im not a terrorist nor do I run a kiddy porn ring, although that is what you'd expect me to say I spose.  :)

---

### Post by rookcifer on 2010-06-12
As others have said, the only way is a private VPN or an ssh tunnel.

You ---- ISP ---- VPN/SSH server ---- Internet

The ISP is always going to see the first hop from their server.  The trick is making that first hop a black hole of sorts for them (an encrypted tunnel to a VPN).

This is the only way to stop them from viewing what you're doing.  Tor can be used for HTTP/S, various chat protocols and a few other things, but not torrents.  If you want to tunnel *everything* you will probably need a private VPN service.

---

### Post by Penguin Guy on 2010-06-12
You should look into [TOR (The Onion Router)]("apt:tor") - use it through [privoxy]("apt:privoxy") and you have a very secure, but slow, means of accessing the internet privately.

> **SonOfOdin said:**
> Im worried about credit card / bank transactions being intercepted and misused more than anything.  I do torrent, books mainly and I have a small but growing mp3 collection.
Serious stuff like credit card details are encrypted so they cannot be intercepted, even by the government. As for torrents, google it - I'm sure I saw an advertisement for some torrent anonymity software somewhere on the 'net.

---

### Post by aysiu on 2010-06-12
This isn't really relevant to your question, but in case you didn't know Ubuntu 8.10 is no longer supported with security updates. Support for most Ubuntu releases ends after 18 months.

---

### Post by SonOfOdin on 2010-06-13
> **aysiu said:**
> This isn't really relevant to your question, but in case you didn't know Ubuntu 8.10 is no longer supported with security updates. Support for most Ubuntu releases ends after 18 months.

Yes I realise this.  I have used Ubuntu on and off over the last couple of years, and have stuck with this version as I have it on a mass produced CD and when I have tried to upgrade through Synaptic, the process has left my machine less than useless and I've had to reinstall regardless.  Sometimes falling back to Windows, other times U8.10.

I will upgrade when I feel the next version runs better on my system or when I can upgrade my lappy.

---

### Post by bodhi.zazen on 2010-06-13
I think it is better to consider any activity you do on the internet to be public and trackable.

It is a sad reality.

IMO TOR and a VPN are still traceable, if you can send and receive information over the internet you can be tracked.

It is simply a matter of how difficult you want to make it for someone to track you.

I also think you are over reacting, Why would the government want to search through the billions of packets to track you personally ?

That does not mean the government is right or that you are not entitled to privacy, but think about it, why would the government care that you post on the Ubuntu forums ?

---

### Post by ddrichardson on 2010-06-13
[http://en.wikipedia.org/wiki/Internet_censorship_in_Australia](http://en.wikipedia.org/wiki/Internet_censorship_in_Australia)

I fear that the only course of action you have is to pressure government, unfortunately it may well be unsuccessful. People are surprisingly quick to assume that if you have nothing to hide then you have nothing to worry about, when perhaps we should say I have nothing to hide, so why are you worrying?

---

### Post by bodhi.zazen on 2010-06-13
> **ddrichardson said:**
> []("http://en.wikipedia.org/wiki/Internet_censorship_in_Australia")People are surprisingly quick to assume that if you have nothing to hide then you have nothing to worry about, when perhaps we should say I have nothing to hide, so why are you worrying?

I agree with this , I think people have a right to privacy and find the sentiment disturbing.

Just because I want privacy does not mean I have something to hide.

However, we are talking about the internet. The internet is, IMO, a public realm and as such one has limited expectations of privacy.

Privacy in your own home is one thing, but privacy policies do not extend to public places.

Thus I think the crux of this discussion is the expectation of privacy on the internet. IMO the internet is Public domain. My LAN or VPN is private and in this case the Australian government is no extending to a LAN or VPN.

If you want privacy do not conduct your business in public.

---

### Post by ddrichardson on 2010-06-13
> **bodhi.zazen said:**
> However, we are talking about the internet. The internet is, IMO, a public realm and as such one has limited expectations of privacy.

Privacy in your own home is one thing, but privacy policies do not extend to public places.
There is truth in that but it is limited by your expectation and definition of public. Indeed, I wouldn't consider Internet a forum at all. While it might be reasonable to assume that publishing to a web page is considered public, it is probably reasonable to assume that an authenticated connection between two people is not public.

---

### Post by PDA1 on 2010-06-15
I have a right to privacy and have a right NOT to be spied on by the govt.  So the argument of "I have nothing to hide" is wrong.  If you're being spied on by your govt. (as we are here in the US through the NSA) then the govt. is already beyond the limits it is allowed by the Constitution Amendment 4 and 5.  It's not the citizen that has to obtain privacy- it's the govt. the must prove what allows it to spy on us.  Also, the spying they do merely increases the size of the bureaucracy and creates more govt. jobs for a bunch of "tax-feeders" that provide no product and no useful service.  Welcome to the "military-industrial-security state" where there's a Bogey Man and "threat" around every corner and everyone's a potential criminal.  What a bunch of TRASH!!!!

---

### Post by HermanAB on 2010-06-15
I presently live in a restrictive place and I do all internet access through a SSH Socks 5 proxy to a GoDaddy server in the USA.  This is easy to set up and it makes services like Skype work better.

People who complain about USA Patriot Act restrictions don't appreciate what they got.

---

### Post by rookcifer on 2010-06-15
> **ddrichardson said:**
> There is truth in that but it is limited by your expectation and definition of public. Indeed, I wouldn't consider Internet a forum at all. While it might be reasonable to assume that publishing to a web page is considered public, it is probably reasonable to assume that an authenticated connection between two people is not public.

I agree.  One can think of the Internet as an abstraction of "real life."  There are activities on the 'net that should have no expectation of privacy (such as publishing a website or blog or posting to this forum), but is it unreasonable to believe a sensitive instant message conversation should be considered private?  How about online banking?  Should we accept that anyone can snoop in (of course SSL stops that, but you get the point)?

---

