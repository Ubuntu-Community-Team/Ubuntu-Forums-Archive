---
title: "Can you place a protocol under the GPL?"
date: 2011-07-24
forum: The Cafe
---

### Post by ki4jgt on 2011-07-24
Can you place a protocol that you've written under the GPL?

Here's the protocol you guys have been helping me with:

[http://sourceforge.net/projects/smashindex/files/E3%20Protocol/E3%20Protocol.txt/download](http://sourceforge.net/projects/smashindex/files/E3%20Protocol/E3%20Protocol.txt/download)

I have placed it under the FDL. I don't want it totally locked down, but this should prove it to be my idea.

---

### Post by NovaAesa on 2011-07-24
You don't really write protocols, you specify them. You write software that implements protocols. My understanding is that protocols aren't released under any licence at all (although some people that make protocols try to keep them secret). I'm not a lawyer though, so I could be wrong (I'm pretty sure I'm right though).

---

### Post by ki4jgt on 2011-07-24
This was my understanding. The only problem was that I have actually written documentation on a protocol, I may place it under the free documentation license, but need it to remain consistent where ever it's used.

---

### Post by doas777 on 2011-07-24
depends on whether you are talking about a specification or a implementation.

for implementations, yes, for standards, mabey. see here:
[http://en.wikipedia.org/wiki/Open_standard](http://en.wikipedia.org/wiki/Open_standard)

---

### Post by disabledaccount on 2011-07-25
Of course You/I can.
Standards are open from definition - otherwise it's not standard. There are many organizations responsible for keeping consitency of thousants of standards, like IANA, IEEC, PCI-SIG etc.
Protocols however are different thing, and I would say that you can consider it the same thing as in case of closed/open source. Closed protocols can be safer at the beginning of usage, but it's much harder to keep them safe over time. Of course it depends what informations are carried trough and on what scale.

---

### Post by Dave_L on 2011-07-25
You might be able to patent it. :neutral:

---

### Post by ki4jgt on 2011-07-25
> **Dave_L said:**
> You might be able to patent it. :neutral:

Don't want to patent it, just create a standard.

---

### Post by sanderd17 on 2011-07-25
You could place your documentation under a CC-BY-ND license. That way, someone can not just make a little adaptation to your documentation and make it a new protocol, but your documentation can be spread without legal limitations.

Another way to assure that the protocol is implemented the same everywhere is to provide an open-source implementation. You can put that implementation under GPL, this does allow changes, but if you protect the name of the protocol, than a derivated version of your implementation can not claim to implement your protocol.

Once you choose a name for your protocol, it is protected automatically. But you do have to watch out for it. If the name you chose becomes a common word, than the protection drops. This are also the problems with the app store from Apple. People use it for a general app store and the protection drops (unless you have enough money to sue everybody).

This is the same as you can't call a derivated version of Firefox the same name (unless you have the approval from Mozilla). But if Firefox would happen to become a synonym for "browser", than Mozilla would have a hard time defending the name Firefox.

---

### Post by forrestcupp on 2011-07-25
To me, it seems like the GPL is the opposite of what you would want for a standard. A standard needs to be unchangeable. The whole point of the GPL is that you are allowed to change what is licensed, but you're not allowed to change the license attached to it. It seems like that's the opposite of what you would want.

---

### Post by ki4jgt on 2011-07-25
> **forrestcupp said:**
> To me, it seems like the GPL is the opposite of what you would want for a standard. A standard needs to be unchangeable. The whole point of the GPL is that you are allowed to change what is licensed, but you're not allowed to change the license attached to it. It seems like that's the opposite of what you would want.

That's very true, perhaps I should just write a program for it and place it under GPL like everyone else has stated.

---

### Post by ninjaaron on 2011-07-25
> **ki4jgt said:**
> Don't want to patent it, just create a standard.

You could/should patent it and give the licence away for free.  This might be wise, if you want to keep patent trolls from patenting it and charging people (including you!) to use it.

GPL is more a matter of copyright.  It' applies to physical data (music, pictures, words... and also circuit-board layout, interestingly enough).  Patents apply to ideas, which is what you have.  If you are serious about ensuring the freedom of this idea, you should get a patent, or find a FOSS organisation to work on it.  Even if you application is denied, it will still insure that nobody else can patent it in the future.

If you have a really good idea, and you don't want to make money off of selling it, please pursue a patent, for all our sakes.

---

### Post by ki4jgt on 2011-07-25
> **ninjaaron said:**
> You could/should patent it and give the licence away for free.  This might be wise, if you want to keep patent trolls from patenting it and charging people (including you!) to use it.

GPL is more a matter of copyright.  It' applies to physical data (music, pictures, words... and also circuit-board layout, interestingly enough).  Patents apply to ideas, which is what you have.  If you are serious about ensuring the freedom of this idea, you should get a patent, or find a FOSS organisation to work on it.  Even if you application is denied, it will still insure that nobody else can patent it in the future.

If you have a really good idea, and you don't want to make money off of selling it, please pursue a patent, for all our sakes.

Can't afford a patent. Which is why I was looking into my options in the FREE department. The FOSS idea sounds cool, but the protocol is not fully developed yet. I thought the whole idea of copyright was to prove that the idea was yours to begin with. If so, then how is posting the idea on the internet (on a site which can verify the date submitted) not a copyright? (Just asking)

---

### Post by ninjaaron on 2011-07-25
> **ki4jgt said:**
> Can't afford a patent. Which is why I was looking into my options in the FREE department. The FOSS idea sounds cool, but the protocol is not fully developed yet. I thought the whole idea of copyright was to prove that the idea was yours to begin with. If so, then how is posting the idea on the internet (on a site which can verify the date submitted) not a copyright? (Just asking)

You can't copyright an idea.  You could post the documentation online, and that would be copyrighted.  If someone tried to steal the idea later, however, you may be able to point to that documentation as proof that you had invented it.  Worth a shot.

However, the only thing that you are legally protecting simply by posting the documentation on the Internet is the documentation itself.  It could be used as a legal argument for the protection of the idea, but it is not a guarantee.  On the other hand, if you get the documentation is out and the protocol becomes widely used, and then some patent troll tries to buy it up, there is a greater chance that a FOSS organisation would take up the cause.

If you won't or can't pursue a patent, I would suggest leaving as much evidence as possible around the Internet that proves it was your idea.  Both documentation and code would probably be good.

---

### Post by forrestcupp on 2011-07-25
> **ninjaaron said:**
> You can't copyright an idea.  You could post the documentation online, and that would be copyrighted.  If someone tried to steal the idea later, however, you may be able to point to that documentation as proof that you had invented it.  Worth a shot.

However, the only thing that you are legally protecting simply by posting the documentation on the Internet is the documentation itself.  It could be used as a legal argument for the protection of the idea, but it is not a guarantee.  On the other hand, if you get the documentation is out and the protocol becomes widely used, and then some patent troll tries to buy it up, there is a greater chance that a FOSS organisation would take up the cause.

If you won't or can't pursue a patent, I would suggest leaving as much evidence as possible around the Internet that proves it was your idea.  Both documentation and code would probably be good.

I think a copyrighted document of a protocol would hold up in court more than an IP. Intellectual Property is pretty shaky and not something that has been strongly tested in court, while copyright infringement is obvious.

I think having a copyrighted document of the protocol is the way to go.

---

### Post by zekopeko on 2011-07-25
> **ki4jgt said:**
> Can you place a protocol that you've written under the GPL?

I suggest you contact a lawyer. I have no experience here but if I was in your shoes I would contact the [Software Freedom Law Center]("http://www.softwarefreedom.org/") or the [Electronic Frontier Foundation]("https://www.eff.org/") or your **local bar association** (my first choice) so that you can get a recommendation for a lawyer.

The important part is for you to get a lawyer who would take your case pro bono or for a small fee. You want that because than s/he will be legally obligated to work in your best interest.

Do not trust organizations because what you want and what they want could be very different. **Trust a lawyer who works for you and will make your wishes happen how you want them to happen**.

---

### Post by walt.smith1960 on 2011-07-25
> **ninjaaron said:**
> You can't copyright an idea.  You could post the documentation online, and that would be copyrighted.  If someone tried to steal the idea later, however, you may be able to point to that documentation as proof that you had invented it.  Worth a shot.

However, the only thing that you are legally protecting simply by posting the documentation on the Internet is the documentation itself.  It could be used as a legal argument for the protection of the idea, but it is not a guarantee.  On the other hand, if you get the documentation is out and the protocol becomes widely used, and then some patent troll tries to buy it up, there is a greater chance that a FOSS organisation would take up the cause.

**If you won't or can't pursue a patent, I would suggest leaving as much evidence as possible around the Internet that proves it was your idea.  Both documentation and code would probably be good**.

Disclaimer: Not a lawyer and with no experience in the field 
By putting as much code and documentation in the public domain you'd at least make a patent troll work to patent your idea.  There'd be 'prior art' which precludes a patent, I believe.  Key would be to be as broad as possible to as to preclude "yeah but *my* implementation of his idea is unique because ______ so i can patent this".

---

### Post by ki4jgt on 2011-07-25
I have added the GPL to the protocol anyway. I am trying to word it to where the protocol will be treated as software code in the original "this software is free message" I haven't got it worded completely correct, but am working on rewording it the best I can. Even though it can't be copyrighted, it won't be able to be patented by someone else because it is placed as a software code. Since computer languages are merely a communication technique between computer and user, another language which is communication between user and user which speaks of protocols may just be able to be seen as program code.

---

### Post by forrestcupp on 2011-07-25
> **ki4jgt said:**
> Even though it can't be copyrighted, it won't be able to be patented by someone else because it is placed as a software code.

Tell me once again why a protocol in written form can't be copyrighted? Placing it as documentation in code just to be able to use the GPL for something that you don't want changed is a pretty ridiculous way to get at what your trying to do.

Just write a document that words your protocol in written form, and copyright it. That is what you want. You don't even have to pay and register something for it to be copyrighted. As soon as you write it, it is copyrighted, and you can put your copyright on it. You can register it for added legal backing if you wish. It doesn't cost much to do that, but it's not required. If you write it up in LibreOffice, or something like that, your file will be time stamped, which is proof of when you created it.

---

### Post by zekopeko on 2011-07-25
> **ki4jgt said:**
> I have added the GPL to the protocol anyway. I am trying to word it to where the protocol will be treated as software code in the original "this software is free message" I haven't got it worded completely correct, but am working on rewording it the best I can. Even though it can't be copyrighted, it won't be able to be patented by someone else because it is placed as a software code. Since computer languages are merely a communication technique between computer and user, another language which is communication between user and user which speaks of protocols may just be able to be seen as program code.

Oh god. Listen. You are not a lawyer. Get a lawyer to draft your wishes otherwise you risk making loopholes. You aren't even sure if the protocol can be copyrighted or patented. I'm pretty sure that pretty much anything that person creates can be copyrighted.

Now go and get a lawyer if this is so important to you.

I presume that you wanting to use GPL means you want any extensions to your protocol be released back. I gave you a link to the Software Freedom Law Center. Go and contact them.

---

### Post by ki4jgt on 2011-07-25
> **forrestcupp said:**
> Tell me once again why a protocol in written form can't be copyrighted? Placing it as documentation in code just to be able to use the GPL for something that you don't want changed is a pretty ridiculous way to get at what your trying to do.

Just write a document that words your protocol in written form, and copyright it. That is what you want. You don't even have to pay and register something for it to be copyrighted. As soon as you write it, it is copyrighted, and you can put your copyright on it. You can register it for added legal backing if you wish. It doesn't cost much to do that, but it's not required. If you write it up in LibreOffice, or something like that, your file will be time stamped, which is proof of when you created it.

> **zekopeko said:**
> Oh god. Listen. You are not a lawyer. Get a lawyer to draft your wishes otherwise you risk making loopholes. You aren't even sure if the protocol can be copyrighted or patented. I'm pretty sure that pretty much anything that person creates can be copyrighted.

Now go and get a lawyer if this is so important to you.

I presume that you wanting to use GPL means you want any extensions to your protocol be released back. I gave you a link to the Software Freedom Law Center. Go and contact them.

Thanks guys for your concern. I'm merely doing this until I can figure out what I'm going to do. @forrestcupp I read up on a copyright method once which involved mailing your idea to yourself. Because the envelope is sealed, you can prove you had the idea, and the post office stamps the date on the envelope, making it government verifiable as happening at that time. I was just adding this as an extra layer of protection, but thanks for the reminder of this approach. It does assist a lot. I had totally forgotten about self copyright methods :-)

---

### Post by forrestcupp on 2011-07-26
> **ki4jgt said:**
> Thanks guys for your concern. I'm merely doing this until I can figure out what I'm going to do.My only concern is that you aren't thinking that the GPL will allow anyone in the world to take what you put out there and "fork" it. The only restriction is that it still has to be GPL. What the GPL does is the opposite of what you need. It gives permission to everyone to do what they want with it. But if it's really not that important to you, then there's nothing wrong with GPLing it until you figure it out. I just think putting it under GPL is worse than doing nothing until you figure it out. 

Also, I'm pretty sure that the creator is allowed to change the license, but I'm not totally sure about that. You'd better make sure that once you release it as GPL that you aren't bound to that forever. I'm sure you can revise it and change the license, but you may be stuck with your original protocol out there bound to GPL where anyone can do anything they want with it.

But I guess it's not my business.

> **ki4jgt said:**
> @forrestcupp I read up on a copyright method once which involved mailing your idea to yourself. Because the envelope is sealed, you can prove you had the idea, and the post office stamps the date on the envelope, making it government verifiable as happening at that time. I was just adding this as an extra layer of protection, but thanks for the reminder of this approach. It does assist a lot. I had totally forgotten about self copyright methods :-)
That's actually a great idea.

---

### Post by ki4jgt on 2011-07-26
> **forrestcupp said:**
> My only concern is that you aren't thinking that the GPL will allow anyone in the world to take what you put out there and "fork" it. The only restriction is that it still has to be GPL. What the GPL does is the opposite of what you need. It gives permission to everyone to do what they want with it. But if it's really not that important to you, then there's nothing wrong with GPLing it until you figure it out. I just think putting it under GPL is worse than doing nothing until you figure it out. 

Also, I'm pretty sure that the creator is allowed to change the license, but I'm not totally sure about that. You'd better make sure that once you release it as GPL that you aren't bound to that forever. I'm sure you can revise it and change the license, but you may be stuck with your original protocol out there bound to GPL where anyone can do anything they want with it.

But I guess it's not my business.


That's actually a great idea.

That's actually what I wanted. I wanted the protocol itself to be open. All projects which fall off of my project must reference my original, and must be renamed (while they also must be open <giving the protocol the ability to adapt>) It's not that I don't care about it, as much as I just care about what it achieves. I want to make it where users can modify the protocol however they like. I could do it by simply claiming ownership and allowing people to do what ever they wish to it I guess, the only thing I want to have control over dealing with it though is the CAPPs section of the document (Commonly Accepted Protocol Practices). So yeah, I was thinking that they'd be able to fork it and leave it under the GPL.

But, you're right, I wasn't thinking all the options completely through. If I GPL the protocol, it will be hard to have control over the CAPP, because everyone will be running it over anyway. I just wanted to be able to allow anyone to suggest corrections, without having to go through legal mumbo-jumbo all the time.

P.S. by posting this on this forum, I have made it your (and everyone here) business. I posed a question and asked for responses. Say what you gotta say :-) The protocol is just an intellectual exercise for me, it's all in the name of fun. I don't even expect it to make it past beta stage (don't even know what stage I'm in right now :-) )

---

### Post by forrestcupp on 2011-07-26
> **ki4jgt said:**
> That's actually what I wanted. I wanted the protocol itself to be open.Ok. I misunderstood what you are doing. I thought you were creating some kind of standard procedure where implementations of it can be different, but the actual procedure followed is unchangeable.

> **ki4jgt said:**
> The protocol is just an intellectual exercise for me, it's all in the name of fun. I don't even expect it to make it past beta stage (don't even know what stage I'm in right now :-) )Then you probably don't need to go spending a bunch of money on lawyers. ;)

---

### Post by ninjaaron on 2011-07-26
> **zekopeko said:**
> I'm pretty sure that pretty much anything that person creates can be copyrighted.

I am 100% sure this is not accurate.  Images, text, physical design (to some extent), can be copyrighted; pretty much anything you can print.  Audio recordings may also be copyrighted.  Ideas cannot be copyrighted; only the words in which they are expressed.  The patent is the legal mechanism for protecting an idea, and the two are governed by different sets of laws. A copyright lasts for seventy years, and a patent lasts for twenty (I think), and they afford their holders  different rights.

I am not a lawyer, but I am a DIY guitar effects hobbiest.  What is wonderful for me (and less wonderful for professional effects designers) is that the only thing which is a builders intellectual property is the name and the circuit-board layout.  They are print media.  The actual circuit can be reverse-engineered and published with complete impunity, though there is sometimes backlash in the community (only when it's a smaller builder.  Nobody cares when you rip off the industry giants).  An effect builder could get patent if he, say, invented an component that processed electrons in a completely new way.  Nobody every does this.

With this background, the whole software patent thing is absurd to me.

---

### Post by psusi on 2011-07-26
The protocol itself is not covered by copyright, so if you want to license that, then you will need a patent.  The specification of the protocol is copyright so you can choose how to license that without needing a patent.

The GPL is a license for software.  It makes no sense to publish a specification under the GPL, since a specification is not software.  You can publish the specification under a license that is similar to the GPL in that it grants people the right to modify and redistribute it, but if it is a standard, then you probably don't want people modifying it.  Instead you probably just want to grant unlimited permission to copy and distribute the specification, unmodified.

---

### Post by ki4jgt on 2011-07-27
The initial post has a copy of the protocol attached now. It's part of the GNU FDL. I do want people to be able to modify it, but I want the common practices to be decided by this document basically. Thanks guys for all your help. If you have any questions or suggestions, please PM me. The E2 protocol was already taken, so I went with E3.

---

