---
title: "Is this stronger than AES-256?"
date: 2010-06-19
forum: Security
---

### Post by Ulysses_ on 2010-06-19
These people offer a free VPN that claims ''2048-bit military strength''.    [http://webcache.googleusercontent.com/search?q=cache:PGWCfrL5hacJ:https://proxpn.com/faq.php+site:proxpn.com+bit&cd=3&hl=el&ct=clnk&gl=gr&client=firefox-a](http://webcache.googleusercontent.com/search?q=cache:PGWCfrL5hacJ:https://proxpn.com/faq.php+site:proxpn.com+bit&cd=3&hl=el&ct=clnk&gl=gr&client=firefox-a)  But last time I looked AES-256 was the strongest available to us non-military users.  So what is it they're offering, illegal encryption?  Or is it just misleading marketing and it's weaker than AES-256?

---

### Post by Bachstelze on 2010-06-19
It is probbly misleading marketing. 2048-bit keys indicate almost certainly that an asymmetric key algrithm is being used (using a symmetric key algorithm with a key that large would be unpractical), but I don't think it's even possible to use a VPN with an asymmetric key algorithm, since both the server and the client should be able to encrypt and decrypt data. It's probably bulls*it, especially with the very little information they give about how the thing really works.

---

### Post by Ulysses_ on 2010-06-20
> **Bachstelze said:**
> It's probably bulls*it, especially with the very little information they give about how the thing really works.

So if we can't trust them for offering what they say, then we can't trust them for keeping our communications private or anonymoys.  However, I have an idea:

What if you connect to the vpn, share the connection to another computer B in your lan (internet connection sharing), and then on computer B you set up a connection to another vpn from another provider, that you then share using internet connection sharing to another computer C, and repeat?  In other words:  

a vpn inside a vpn inside a vpn ...  

which is NOT vpn chaining.  

Then an adversary would have to force ALL vpn providers involved to reveal decrypted data in order to break your privacy.  And if just one vpn is in a hostile jurisdiction, the adversary gets stuck there.

---

### Post by Bachstelze on 2010-06-20
> **Ulysses_ said:**
> So if we can't trust them for offering what they say, then we can't trust them for keeping our communications private or anonymoys.

More like they don't tell us exactly what they are offering, but the conclusion is the same: I wouldn't trust them with my data.

> **Ulysses_ said:**
> However, I have an idea:

What if you connect to the vpn, share the connection to another computer B in your lan (internet connection sharing), and then on computer B you set up a connection to another vpn from another provider, that you then share using internet connection sharing to another computer C, and repeat?  In other words:  

a vpn inside a vpn inside a vpn ...  

which is NOT vpn chaining.  

Then an adversary would have to force ALL vpn providers involved to reveal decrypted data in order to break your privacy.  And if just one vpn is in a hostile jurisdiction, the adversary gets stuck there.

In theory, yes. In practice, that would be unnecessary complexity imo. Just use the one VPN that is in a "hostile jurisdiction". ;)

---

### Post by Ulysses_ on 2010-06-20
But I don't know which vpn is in a hostile (to the adversary) jurisdiction.

---

### Post by Bachstelze on 2010-06-20
You need to know whom you want to protect against. "Everyone" is not a valid answer, as no measure is effective against all adversaries.

---

### Post by Ulysses_ on 2010-06-20
What about "as many as possible" is it valid answer? ;) 

Even better, "adversaries of the widest range of skill/capability".  So it is not count that matters (we don't care too much about crowds) but range of capability.  EDIT: range meaning NOT the range of capabilities of each individual but I mean the range of grades of the entire "school".  Like listing all pupils in a school in order of the grade they got and being interested in a range of grades that is as wide as possible, ideally all grades.

---

### Post by Bachstelze on 2010-06-20
Well, if you want to protect against a government, you're pretty much screwed anyway. They can use the $5-wrench method, or put a logger in your keyboard, or something like that*. For a big corporation, it's pretty much the same. That leaves us with small companies or random people who hate you and/or want your money. A single VPN with a reliable provider will probably be enough againts those.

* That is, if they really want you. If they don't and you just want your traffic encrypted so that they don't stumble on it, once again, a single VPN from a reliable provider will do. They can't just force everyone who encrypts their traffic to decrypt it for them, there's just too much of them.

---

### Post by Ulysses_ on 2010-06-20
> **Bachstelze said:**
> Well, if you want to protect against a government, you're pretty much screwed anyway. They can use the $5-wrench method, or put a logger in your keyboard, or something like that*. 

Could you expand upon this?  How can they put a logger in my keyboard if they do not suspect me of anything?  

And what is a wrench method?  

You mean a software keylogger?  Hardened linux and NoScript always set to "refuse all scripts" are not enough to prevent infection with keylogging malware?

---

### Post by Bachstelze on 2010-06-20
> **Ulysses_ said:**
> Could you expand upon this?  How can they put a logger in my keyboard if they do not suspect me of anything?  

That's what I was saying: if they don't really want you, they won't go in a lot of trouble to get your keys. They probably won't even pay any attention to you, so a single VPN will do.

> **Ulysses_ said:**
> And what is a wrench method?

[img]http://imgs.xkcd.com/comics/security.png[/img]  

> **Ulysses_ said:**
> You mean a software keylogger?  Hardened linux and NoScript always set to "refuse all scripts" are not enough to prevent infection with keylogging malware?

No, I mean they can get inside your house and put an electronic device inside your keyboard that records the keys you pressed. Once again, they will only go to such lengths if they really want you.

---

### Post by anomie on 2010-06-20
[QUOTE=Ulysses_]These people offer a free VPN that claims ''2048-bit military strength''.[/QUOTE]

I do find it interesting that they have no wikipedia page (as of this writing). Presence there is by no means the be-all end-all of project legitimacy, but absence there is curious.

-------

Also, you might want to give this a read: [http://myvpnreviews.com/proxpn/](http://myvpnreviews.com/proxpn/)

---

### Post by Ulysses_ on 2010-06-20
> How can they put a logger in my keyboard if they do not suspect me of anything?

> **Bachstelze said:**
> That's what I was saying: if they don't really want you, they won't go in a lot of trouble to get your keys. They probably won't even pay any attention to you, so a single VPN will do.If I'm visiting the site of an ex soldier that publishes on youtube etc videos of attrocities of the US in Iraq (such the wikileaks site, there's one of a helicopter shooting at civilians and killing lots, including two Reuters reporters), what then?  I think it is likely that anyone visiting there without a normal IP but a VPN IP, is guaranteed to be paid attention to, and investigated further by the same types harassing the owner of the site who's currently hiding:

[http://www.presstv.ir/detail.aspx?id=130017&sectionid=3510203](http://www.presstv.ir/detail.aspx?id=130017&sectionid=3510203)

A typical vpn owner in western countries will be forced to give your true ip to such types if you visit sites like wikileaks.  But which is that one vpn that will not give your ip to US-obedient powers that be?  You can't possibly know.  Hence, vpn nesting.

---

### Post by Ulysses_ on 2010-06-20
> **anomie said:**
> Also, you might want to give this a read: [http://myvpnreviews.com/proxpn/](http://myvpnreviews.com/proxpn/)

It says in the linked site: 

"Scammers! ProXPN records your information and steals sensitive data off your computer!"

Guess what happened when I set up proxpn on a windows 2000 VM a while ago?  It got unusually slow at times. ;) I think they may well be including malware in their executable.

---

### Post by Bachstelze on 2010-06-20
> **Ulysses_ said:**
> 
 But which is that one vpn that will not give your ip to US-obedient powers that be?

[http://www.prq.se/?p=tunnel&intl=1](http://www.prq.se/?p=tunnel&intl=1)

---

### Post by Ulysses_ on 2010-06-20
> **Bachstelze said:**
> [http://www.prq.se/?p=tunnel&intl=1](http://www.prq.se/?p=tunnel&intl=1)

What, Sweden is not under the US sphere of influence?  It's in NATO.  Or this vpn has something special I haven't noticed?

---

### Post by Bachstelze on 2010-06-20
> **Ulysses_ said:**
> What, Sweden is not under the US sphere of influence?  It's in NATO.  Or this vpn has something special I haven't noticed?

Sweden is a democracy, the judicial system is independent from the executive power (i.e. the government). And only a court can force a VPN provider to surrender your key. If what you want to do is legal under the Swedish law, PRQ will not give out yor identity.

---

### Post by Ulysses_ on 2010-06-20
You're Swedish by any chance? Now I've noticed you've put France as your location.  Isn't France just as democratic as Sweden in these matters?  From what I know, all countries are supposed to be democratic and in most countries there is a similar law, but there are also exceptions, and there are also secretive forces that make a joke of such laws.

---

### Post by Bachstelze on 2010-06-20
> **Ulysses_ said:**
> Isn't France just as democratic as Sweden in these matters?

It is not only the country that matters, but also having a VPN provider that stands with its promise of only surrendering your information when ordered by a court, and not by external pressure. PRQ has a long record of doing just that. For example, they refused, despite a lot of pressure, to close a forum hosted by them that was a "meeting point" for pedophiles, because Swedish law does not allow closing a website in such cases.

> **Ulysses_ said:**
> From what I know, all countries are supposed to be democratic and in most countries there is a similar law, but there are also exceptions, and there are also secretive forces that make a joke of such laws.

If you want to protect aginst "secretive forces", as I said, you're screwed. Once you got their attention, they *will* use the wrench method or something similar if they think they have to. You can't do anything, the power imbalance is just too big.

But you'd have to be onto something very big to warrant the "secretive forces" to come into play. I don't know what you want to do, but remember that if they didn't use that for pedophile websites, you probably have a lot of free room until they come after you.

---

### Post by Ulysses_ on 2010-06-20
> **Bachstelze said:**
> Once you got their attention, they *will* use the wrench method or ...

So you conclude that once the attention of secretive forces has been got to your public IP, there is no way to stop them from finding your true IP?  No vpn in the world can do that, not even PRQ?  Not even one in North Korea?  Not even one in Iran that is about to get nuked?  

My understanding is secretive forces are always competing against each other.

---

### Post by Bachstelze on 2010-06-20
> **Ulysses_ said:**
> So you conclude that once the attention of secretive forces has been got to your public IP, there is no way to stop them from finding your true IP?  No vpn in the world can do that, not even PRQ?  Not even one in North Korea?  Not even one in Iran that is about to get nuked?  

My understanding is secretive forces are always competing against each other.

At that level, I don't think anyone can really guess what would happen, but let's try, just for the discussion's interest. I don't know of any North Korean or Iranian VPN providers, but assuming some exist, a North Korean one would probably be relatively safe, but not an Iranian one. Iran is not a bunker-country like North Korea, I believe it would be fairly easy for US secret agents to infiltrate an Iranian VPN provider. Iran only really care about their nuclear facilities. :p

---

### Post by rookcifer on 2010-06-20
> **Ulysses_ said:**
> If I'm visiting the site of an ex soldier that publishes on youtube etc videos of attrocities of the US in Iraq (such the wikileaks site, there's one of a helicopter shooting at civilians and killing lots, including two Reuters reporters), what then?  

Just to correct you.  That video shows no atrocities whatsoever.  It shows a gunship firing at insurgents who were holding AK-47's in the middle of a battle zone.  It just so happens that a couple of Reuters **freelance** "reporters" happened to be embedded with these insurgents.  According to the rules of war, having journalists embedded with a military unit does NOT make that unit immune from being shot at.  Moreover, these "journalists" were well known as being terrorist supporters.

However, it is true that a couple of kids were shot (because they were with the man who came to "rescue" the insurgents).  It is not the fault of the helicopter pilots that this man brought kids onto the battlefield (a typical terrorist tactic -- hide behind civilians).  It is perfectly within the rules of engagement to fire upon those coming to the aid of a wounded enemy combatant!  These pilots broke no rules.  They even got clearance with their ground commanders before firing.

---

### Post by cariboo on 2010-06-20
this thread seems to have drifted off topic. Please keep on topic, or you know hat will happen.

---

### Post by OpSecShellshock on 2010-06-20
If you plan on attracting any heavy-hitters' attention, they aren't going to be as interested in an IP address as they are other information that can identify a real person. Within a LAN an IP address is a decent way to identify a specific user/device/DHCP lease. Out on the internet it's not a very good identifier at all. It can be useful if you want to harass somebody you know is innocent (since a lot of non-techy people in the courts and the press believe it can identify a person--or at least they all agree to pretend that it can).

You don't really need to sniff for the interesting stuff, though, because people willingly give it away to any number of third parties who don't care as much about your privacy as they care about their own operational continuity. What's hilarious is that often people pass the data to these third parties because they believe it increases their privacy.

It's not a lot to worry about, though. Con artists are still far more of a risk to most users than intelligence people. Also, data dragnets are a lot less useful than the widespread belief that they're being employed.

---

### Post by Ulysses_ on 2010-06-21
Thanks for the input rookcifer. I'd have to agree with cariboo907 that this is not a suitable place to discuss what really happened in such incidents.  Do you participate in any other forums?  I would honestly enjoy a discussion at an appropriate place of your choice.

OpSecShellshock I'm surprised by what you said about IPs not being enough to identify a real person.  How many people visiting sites like wikileaks, or any site that exposes embarassing videos (whether true or not), how many such visitors are likely to not be using a standard ISP's ADSL or dial-up line like most of us?

---

### Post by OpSecShellshock on 2010-06-21
It's not a question of usage, but of non-repudiation. Sure, everyone (for the most part) uses an IPv4 address to move data. However, between DHCP, NAT, onion routing, and the fact that spoofing alone is quite trivial, an IP address is simply unacceptably flimsy when it comes to using it as a way of uniquely identifying who did what, and when with any certainty. All things considered, an IP address is pretty useless information in and of itself. It might supplement other existing information about a person or device, but it can't be used alone to prove anything.

---

### Post by Ulysses_ on 2010-06-21
> **OpSecShellshock said:**
> between DHCP, NAT, onion routing, and the fact that spoofing alone is quite trivial, an IP address is simply unacceptably flimsy when it comes to using it as a way of uniquely identifying who did what, and when with any certainty.

You're connecting to the internet from a spaceship, is it an aircraft carrier? :)  Last time I looked, most people were connecting through an adsl line or cable registered to a person and an address.  Or a dial-up line in rural areas.  Either way, they had to register with an isp.  Customer name and address not unique enough?  Or an isp's customer that is a company, can't the company identify who's working at their premises?

And how on earth can ip spoofing work, how can you lie about your ip and still get data transfered, how would packets know where to go?  Or is it really some sort of nat through a someone else's hacked computer using their internet connection?

---

### Post by LiQuidAiR on 2010-06-21
It seems Ulysses is trying to stir emotions to gain insight into a bigger picture of things.. What that is, only he/she knows..

---

### Post by OpSecShellshock on 2010-06-21
> **Ulysses_ said:**
> You're connecting to the internet from a spaceship, is it an aircraft carrier? :)  Last time I looked, most people were connecting through an adsl line or cable registered to a person and an address.  Or a dial-up line in rural areas.  Either way, they had to register with an isp.  Customer name and address not unique enough?  Or an isp's customer that is a company, can't the company identify who's working at their premises?

And how on earth can ip spoofing work, how can you lie about your ip and still get data transfered, how would packets know where to go?  Or is it really some sort of nat through a someone else's hacked computer using their internet connection?

Sure, you can (with a court order) obtain customer records for a given IP address in use at a given time. But before you've gotten that far, how can you be assured that the IP address is genuine? Even if it is, how do you know which machine of that customer's was actually involved? If you know that, then how do you know it was actually under that person's control and not compromised by someone else? Which brings us to my main point--if you know enough to be certain of who the person is and what unique device they were using, you don't really need the IP address--this is assuming you have already gotten the authorization to investigate a specific person, which still cannot simply materialize from nowhere.

Remember that any given individual need not disguise their IP address, because enough people can (and do) that it's not a reliable way to identify anyone (or more accurately identify the device that was using it)--which means nobody really cares. There are more important pieces of information to look for that users don't think about because they're worried about their IP addresses.

---

### Post by Bachstelze on 2010-06-21
> **OpSecShellshock said:**
> 
Remember that any given individual need not disguise their IP address, because enough people can (and do) that it's not a reliable way to identify anyone (or more accurately identify the device that was using it)--**which means nobody really cares**. There are more important pieces of information to look for that users don't think about because they're worried about their IP addresses.

Slightly off-topic, but you are crediting the random court with far more knowledge than they actually have (or, at least, demonstrate). There have been countless occurrences when someone was fined/imprisoned because their IP address was found downloading some movie or song, and I would bet a lot of money no one cared to check whether or not they actually donloaded the content in question.

So technically you are right, an IP address is obviously not sufficient to identify a computer, let alone a person. In practice, though, a lot of powerful groups have decided it was the case, and a lot of courts have decided to believe them. So yes, you should care very much about making sure your IP address will not be used by unauthorized people.

---

### Post by rookcifer on 2010-06-21
> **Ulysses_ said:**
> And how on earth can ip spoofing work, how can you lie about your ip and still get data transfered, how would packets know where to go?  Or is it really some sort of nat through a someone else's hacked computer using their internet connection?

It works because the original IP is being tunneled through a network of proxies and the IP address seen at the "destination" will be that of a proxy and not of the original requester.  Under normal circumstances the IP can merely be backtracked through the chain of proxies.  But in the case of Tor, this is prevented because no hop along the chain knows what the previous or subsequent hop will be.  Moreover, everything is encrypted within the circuit which makes sniffing IP headers impossible.  The only known way to trace a Tor connection is if all three hops were in collusion with each other, a very unlikely scenario.

---

### Post by OpSecShellshock on 2010-06-22
> **Bachstelze said:**
> Slightly off-topic, but you are crediting the random court with far more knowledge than they actually have (or, at least, demonstrate). There have been countless occurrences when someone was fined/imprisoned because their IP address was found downloading some movie or song, and I would bet a lot of money no one cared to check whether or not they actually donloaded the content in question.

So technically you are right, an IP address is obviously not sufficient to identify a computer, let alone a person. In practice, though, a lot of powerful groups have decided it was the case, and a lot of courts have decided to believe them. So yes, you should care very much about making sure your IP address will not be used by unauthorized people.

Not precisely--at least in the US, infringement is a civil matter, not criminal. However, your main point as I understand it is correct--many of the rightsholders' representatives do use nothing more than an IP address to find a user. Consequently, many, many of their identifications have been incorrect. However, it's more expensive and a higher risk to challenge the validity of their so-called evidence than it is to simply pay the settlement, so most people settle. I do believe that eventually someone who is identified in this way will mount a challenge, and will succeed. It only takes one case. Of course, since these parties are willing to shake innocent people down on the basis of incorrect identifications, then an IP address that matches mine could show up on one of their lists even though I haven't done it--so the value of hiding my IP address is still negligible since the process on the rightsholders' end is already arbitrary. To put it another way, there are any number of scenarios that could get me targeted: I could actually participate and be recorded, someone else could coincidentally pick my IP address as the random one they present, the representative of the rightsholder could just make the whole thing up. There's no validation process outside of a court case, which most people can't afford. Obviously, that isn't right or just. So it's simply a matter of time before they mess with the wrong person.

---

### Post by johngreth on 2010-07-01
Bringing it back to computer land...

AES works by running several rounds of the same operations and for each round it uses a different key. The keys are generated by the rijndael key schedule, which uses one original key (128, 192, or 256 bits) and generates a set of 128 bit keys from the first. 2048 bits could just mean that instead of having one small original key, it uses a set of random keys (2048 bits total) to add security by making the key longer and eliminating the possibility of a related key attack.

The only problem is that AES uses 11, 13, or 15 128 bit keys in the rounds (depending on the original key size), and none of these adds up to 2048 bits. 2048 bits would mean 16 keys.

Moral: It could possibly be a method that is similar to AES but clearly different, OR, it is some other encryption (the later is more likely).

Moral (part 2): The military uses normal AES-256 bit, so that must be a lie, but I didn't see any mention of military strength on the web page.

---

### Post by rookcifer on 2010-07-02
> **johngreth said:**
> 
The only problem is that AES uses 11, 13, or 15 128 bit keys in the rounds (depending on the original key size), and none of these adds up to 2048 bits. 2048 bits would mean 16 keys.

Moral: It could possibly be a method that is similar to AES but clearly different, OR, it is some other encryption (the later is more likely).


I think the VPN provider is meaning to say it uses 2048 *asymmetric* encryption.  One should not confuse asymmetric (public key crypto) with symmetric (AES and other such block ciphers).  Asymmetric ciphers have much larger key lengths due to the large modulus that must be generated (typically large primes).  

It is estimated that a 2048 public key will provide about 112 bits of symmetric security (i.e, 2048 bit RSA is about as strong as a hypothetical AES-112).  It takes RSA-3072 to be about equal to AES-128 and RSA-15360 to be equal to AES-256.  This means asymmetric ciphers are much slower and thus are never used for anything but encrypting a symmetric session key.

All that said, I think the VPN provider that OP was asking about is selling snake oil.  Run far away.

---

### Post by johngreth on 2010-07-02
Two things.

1. It would take even the most powerful super computer 2 weeks to break even a 32 bit symmetric encryption, so is 256 bits really that much more secure than 128 or even 64?

2. What is the point of using a vpn for normal access to the Internet anyway?

---

### Post by movieman on 2010-07-02
> **johngreth said:**
> It would take even the most powerful super computer 2 weeks to break even a 32 bit symmetric encryption

If I remember correctly, about $100k worth of hardware was enough to crack 56-bit DES in a few hours a few years ago.

> so is 256 bits really that much more secure than 128 or even 64?

A 64-bit key is easy for any dedicated adversary to break, making 128 the minimum you should use. The addition of 256-bit keys was primarily driven by quantum cryptography, for which a 256-bit key would be about as hard to break as a 128-bit key using conventional hardware.

---

### Post by rookcifer on 2010-07-02
> **johngreth said:**
> Two things.

1. It would take even the most powerful super computer 2 weeks to break even a 32 bit symmetric encryption,

32 bit keys were easy for a single PC to break even 10 years ago.  Today they would take a top-end desktop GPU literally about 10 seconds and a very marginal CPU just a few minutes.

>  so is 256 bits really that much more secure than 128 or even 64?

256 bit keys are too large to even discuss.  As the other guy said, they were a requirement in the AES specification because the NIST wanted protection against quantum computing if it ever became feasible, and just because 256 keys would future proof the algorithm in general (AES is supposed to be a very long term algorithm).  There are roughly as many atoms in the universe as there are possible keys in a 256 bit key space.

> 2. What is the point of using a vpn for normal access to the Internet anyway?

Privacy from ISP snooping.  Only you and your VPN know which sites you're is visiting.

---

### Post by Bachstelze on 2010-07-02
> **movieman said:**
> If I remember correctly, about $100k worth of hardware was enough to crack 56-bit DES in a few hours a few years ago.

That's why DES is not used anymore, and we now have AES, Serpent or *fish.  The key-length alone is meaningless, you also need to now which cipher is used.

---

### Post by movieman on 2010-07-02
> **Bachstelze said:**
> That's why DES is not used anymore, and we now have AES, Serpent or *fish.  The key-length alone is meaningless, you also need to now which cipher is used.

The difference in time required to brute-force a symettric key between algorithms of the same key length is typically in the noise when compared to the difference between a 56-bit key and even a 64-bit key. If algorithm A takes ten times longer to perform an encryption/decryption operation than algorithm B, that's about equivalent to having three extra bits of key when you're trying to crack it.

And for obvious reasons, we generally prefer fast algorithms to slow ones; I believe AES is significantly faster than DES when implemented in software, and much faster when using the new AES instructions in Intel CPUs.

---

### Post by rookcifer on 2010-07-02
> **movieman said:**
> And for obvious reasons, we generally prefer fast algorithms to slow ones; I believe AES is significantly faster than DES when implemented in software, and much faster when using the new AES instructions in Intel CPUs.

Yes, AES is much faster than DES, which is the main reason Rijndael was chosen in the AES competition over Serpent.

---

### Post by Bachstelze on 2010-07-03
> **rookcifer said:**
> Yes, AES is much faster than DES, which is the main reason Rijndael was chosen in the AES competition over Serpent.

And not everyone is happy with that choice. Rijndael a much more complex design than Serpent, which increases the chance of a "hidden flaw". I know a lot of people that always use Serpent when possible (and even rewrote some programs to make them use Serpent instead of AES).

---

### Post by johngreth on 2010-07-07
> It would take even the most powerful super computer 2 weeks to break even a 32 bit symmetric encryption.

I based this on the calculations per second of a super computer and the number of possible keys in 32 bit encryption and I have no real source to back it up, so it is probably wrong. If anyone has a source that can prove it wrong, I'd be very interested in seeing it. 

> Privacy from ISP snooping. Only you and your VPN know which sites you're is visiting.
privacy from who? Websites? Someone monitoring your traffic? Anyway, don't most ISPs have dynamic IP addresses that you can change by resetting the modem?

> The difference in time required to brute-force a symmetric key between algorithms of the same key length is typically in the noise when compared to the difference between a 56-bit key and even a 64-bit key.

DES is breakable, meaning that the attacker can be smarter and figure out the key in 2^41 tries, and not have to try all 2^56 possibilities. So, DES is theoretically as easy to break as 41 bit AES.

> A 64-bit key is easy for any dedicated adversary to break.

> 32 bit keys were easy for a single PC to break even 10 years ago. Today they would take a top-end desktop GPU literally about 10 seconds and a very marginal CPU just a few minutes.

if this is accurate, and 64 bit is 2^32 times more secure, then it would take over 1000 years to break 64 bits.

---

### Post by rookcifer on 2010-07-07
> **johngreth said:**
> I based this on the calculations per second of a super computer and the number of possible keys in 32 bit encryption and I have no real source to back it up, so it is probably wrong. If anyone has a source that can prove it wrong, I'd be very interested in seeing it. 

A 32 bit key has 2^32 possible keys.  This is nothing for modern desktop computers to brute-force and hasn't been in forever.  If a CPU can check 1,000,000 keys a second, it can brute-force it in about an hour.  Most modern CPU's can go much faster than 1,000,000 checks a second.  And this says nothing about GPU's which are much, much faster than that.

A 64 bit key was brute-forced by distributed.net in less than 5 years.  And that was using clusters of mostly 1990's computers.  Today 64 bit keys could be broken in days or months using a cluster of modern computers.  NSA could probably do it in days (or possibly even in hours).

So, no, 64 bit keys are not safe today and haven't been for years.

> privacy from who? Websites? Someone monitoring your traffic? Anyway, don't most ISPs have dynamic IP addresses that you can change by resetting the modem?

An ISP knows which IP was assigned to whom at what time.  Therefore, it can snoop on whomever it wants at any time as long as the data is coming across unencrypted.  A VPN encrypts all data and hides it from the ISP.  The ISP only sees the user connecting the the VPN -- it cannot see what the user does from there.

> DES is breakable, meaning that the attacker can be smarter and figure out the key in 2^41 tries, and not have to try all 2^56 possibilities. So, DES is theoretically as easy to break as 41 bit AES.

Single DES is really old -- it was the standard starting in the mid 70's.  The original designers wanted it to have 128 bit keys but the NSA took it and cut the key length down to 56 bits.  

At any rate, there was a scheme designed in the 90's that allowed 3 separate DES keys to be use on the same message.  This is known as 3DES or Triple-DES and has a key-size of 56 * 3 or 168 bits.  However, cryptanalysis has broken it to the point where it is only effectively as safe as 112 bits (which is still extremely secure even with today's computing power).  

So, DES is not dead; Triple-DES is still secure and NIST says it *should* be secure until at least 2030.  The only problem is it's slower than the more modern ciphers and has a smaller block size.

---

### Post by movieman on 2010-07-07
> **johngreth said:**
> DES is breakable, meaning that the attacker can be smarter and figure out the key in 2^41 tries, and not have to try all 2^56 possibilities. So, DES is theoretically as easy to break as 41 bit AES.

I seem to remember that the better than brute force attacks on DES require an improbable amount of memory to store precomputed results?

In any case, a 2^56 brute force attack took 56 hours in 1998 with $250k of hardware:

[http://en.wikipedia.org/wiki/EFF_DES_cracker](http://en.wikipedia.org/wiki/EFF_DES_cracker)

That was one of the reasons for replacing DES with AES.

Equivalent hardware would probably cost a few thousand dollars today, and any serious adversary could have millions of them. A few billion dollars worth of similar boards could break 64-bit keys in seconds.

---

### Post by johngreth on 2010-07-07
If the ISP wants to know what you are doing so bad, why don't they use a man in the middle attack?

Also

> 64 bit key was brute-forced by distributed.net in less than 5 years. And that was using clusters of mostly 1990's computers. Today 64 bit keys could be broken in days or months using a cluster of modern computers. NSA could probably do it in days (or possibly even in hours).

I reworked my calculation and that sounds about right.

2^64 / 10^15 (operations per second) is about 18000 seconds or 5 hours, so thats 5 hours times the number of operations in the algorithm.

---

