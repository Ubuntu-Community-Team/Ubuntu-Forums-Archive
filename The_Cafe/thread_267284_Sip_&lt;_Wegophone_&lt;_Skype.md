---
title: "Sip &lt; Wegophone &lt; Skype ?"
date: 2006-09-28
forum: The Cafe
---

### Post by DoctorMO on 2006-09-28
Skype is propritory, we all know that it's a bad way to lock yourself into a systems that releases software only when it likes and controls the network in a way which many would consider to be too much.

Wengophone is open source, but I notice the network is still pritty closed.

Ekiga which uses the open sip protocall is just a client to an open network. shouldn't we be recomending the use of Ekiga and other sip based clients?

---

### Post by angkor on 2006-09-28
> **DoctorMO said:**
> shouldn't we be recomending the use of Ekiga and other sip based clients?

I already am. But a lot of my friends don't have sip accounts (yet) but use Skype. I don't use skype that much anymore but use Ekiga to call land lines very cheap with my ISPs sip account.

---

### Post by jason.b.c on 2006-09-28
> **DoctorMO said:**
> Skype is propritory, 


Why does that matter..? , Who care's if it's propritory..:confused:

---

### Post by angkor on 2006-09-28
> **jason.b.c said:**
> Why does that matter..? , Who care's if it's propritory..:confused:

Well it matters to me because I can't use any *other* pc-phone application to call Skype users because their protocol is closed. I prefer SIP because it is open and gives me better sound quality on linux than skype does.

---

### Post by arkangel on 2006-09-28
here we have a problem , i have to call some family , and they have no clue  what  linux is , or even windows ,  they only know how to click in the skype icon and how to  answer when i call ,  then  no other way  than using skype ,  i hope one day  there will be  a free version of  skype-compatibel app  , meanwhile  use what fits you  better

---

### Post by skymt on 2006-09-28
> **arkangel said:**
> here we have a problem , i have to call some family , and they have no clue  what  linux is , or even windows ,  they only know how to click in the skype icon and how to  answer when i call ,  then  no other way  than using skype ,  i hope one day  there will be  a free version of  skype-compatibel app  , meanwhile  use what fits you  better

Get them onto SIP! I'm sure there's some easy, open-source SIP software on Windows.

---

### Post by ago on 2006-09-28
> **arkangel said:**
> here we have a problem , i have to call some family , and they have no clue  what  linux is , or even windows ,  they only know how to click in the skype icon and how to  answer when i call ,
They can install openwengo on windows and have an icon exactly like skype. It is also very similar

---

### Post by ago on 2006-09-28
> **DoctorMO said:**
> Wengophone is open source, but I notice the network is still pritty closed.

Are you sure about that? My understanding was that OW uses SIP and that means their network is open. But I am not expert.

---

### Post by arkangel on 2006-09-28
the point was  , there are some people  you have to communicate  with  and they dont want (know how)to install,  they in turn have also other people to talk to... I actively try to convince other people to use linux or at least to give it a try ,  however not always is possible...

---

### Post by ago on 2006-09-28
> **arkangel said:**
> the point was  , there are some people  you have to communicate  with  and they dont want (know how)to install
They somehow installed skype in the first place. I am sure they can do the same with OW, GoogleTalk or other SIP software. 

> they in turn have also other people to talk to...
They can either convince their friends or use two applications.

This is the network effect of closed standards I was discussing about on another thread... Unfortunately you need to take the plunge. You may offer to help them out (and probably their friend too). If you never start to make the switch happen, it will become more and more difficult to do so as time passes by and people will be completely locked-in with Skype.

---

### Post by weatherman on 2006-09-28
> **ago said:**
> Are you sure about that? My understanding was that OW uses SIP and that means their network is open. But I am not expert.
that's my understanding as well :)
quote from the openwengo faq:
> Can WengoPhone NG be used with any SIP provider? 
Not right now. However, it is the item with the highest priority on our todo list, apart from having a 2.0 release. So expect to see this feature implement right after the first NG release.

[http://www.openwengo.org/index.php/openwengo/public/homePage/openwengo/public/projectsNg](http://www.openwengo.org/index.php/openwengo/public/homePage/openwengo/public/projectsNg)

---

### Post by ago on 2006-09-29
I think that they refer to the fact of using a SIP provider within OW itself. That means that when you want to make a paid-for call to land line they do not even force you to use their own service. That does not mean that you have to wait for NG in order to call another SIP phone, you should be able to that already (I have not tried it) since the protocol is SIP. 

Again, I may be wrong, but the above looks to me like a sign of great "openess".


DrMo can you please explain what you mean? I was planning of moving the rest of the family that uses Windows to OW...

---

### Post by Kayne on 2006-09-29
It may sound ignorant but I use Skype and I don't have a guilty conscience using it.
May it be closed sourced or not, I use what works best for me and on top of that all of my friends happen to use it, too.

And frankly, Skype is not THAT bad a software. Actually I really like it.

---

### Post by Buffalo Soldier on 2006-09-29
Copied from [ Why thou shall not use Skype!](http://fossvoip.blogspot.com/2005/12/why-thou-shall-not-use-skype.html)

This is a blog focused on FOSS so I shouldn't be talking too much about proprietary stuff.

The only problem is not too much that Skype is proprietary (though it is), the real issue is that it uses a closed and proprietary protocol. Now, what does that mean? It means that Skype users are only allowed to communicate with... well, other skype users.

**What's the big deal?**
Try to apply that concept to real landline phones, say you're a Verizon subscriber and you want to call a friend that is a subscriber to another company that is not Verizon, what would happen? Your friend would need to buy a special phone from Verizon or subscribe to their service to be able to communicate with you. Sounds annoying right?

In the software world, softphones that use open and free standards such as SIP can communicate with one another, this is impossible with Skype.

**Who cares? Downloading Skype won't cost me a penny!**
You might be right for now but what if Skype gets almost all VoIP users and that all VoIP hardware phones get Skype compatible only. Skype might decide to charge too much for its hardware license and turn its gratis softphone as we know it today into a fee based service!

This is called Vendor lock-in, it is common practice among software companies. It consists of tricking users into using a technology for free and then charge unfair fees for it once it has become a standard because it's costly to move away from a de facto standard see this wikipedia article about that problem (Vendor lock-in is what Microsoft did with its API and Franhofer with MP3).

Most importantly, letting the means of communication in the hands of only one entity is undemocratic especially when this entity uses a secret protocol that can only be controlled by that entity (a profit driven company). Are you OK with losing your freedom and privacy for a bit of commodity from Skype? Is your freedom that cheap?

**Who cares? I'll just stop using Skype and start using a gratis alternative!**
Well, look at what happened in the office world. OpenOffice and GNU/Linux are free and gratis and yet no one is switching or at least slowly. Why is that? Switching technology in the corporate world is costly especially when it comes to hardware (think of all those Skype-compatible hardware phone your boss invested in...). So using Skype now is like getting addicted to some bad drug, it will be hard and costly to stop using it even if the dealer decides to raise unfair fees on you. Using Skype now is putting your future in the good will of Ebay Inc and Skype Corp.

**OK I'm kind of convinced :) How can I avoid that?**
Just don't use Skype or stop using it NOW. There are lots of alternatives that use standard protocol such as SIP and AIX. Tell your friends about alternatives. This is a blog focused on Free and Open Source alternatives so I will advise you this alternative.

Hope that post will help you make the switch to the free world of VoIP :)

---

### Post by ago on 2006-09-29
They are called [network externalities](http://en.wikipedia.org/wiki/Network_effects), and like [economies of scale](http://en.wikipedia.org/wiki/Economies_of_scale) (another form of [externality](http://en.wikipedia.org/wiki/Externality)), they create barriers to competition and allow a company to operate as a monopolist.

Whenever network externalities play a role in a market, companies intentionally break compatibility with other products to create a network effect. If they manage to get enough momentum,  they can enjoy a monopolistic position until the antitrust intervenes, since the barriers created by the network effect are extremely difficult to overcome. Note that network externalities apply to many sectors, not just telephony, they simply are not as "obvious" (for instance a browser that sets a broken de-facto web standard is exploiting network externalities, incompatible office document formats, incompatible IM networks...).

There are 3 ways to break them:

* create a (legally) compatible product (but the company will try to avoid that, legally or by changing the network protocol if necessary)
* force the company to open up its network 
* create an alternative network (possibly open) and make it reach critical mass by having several people join it.

The 3rd one is often the only viable alternative, but it is "difficult", as shown by the posts above, when the closed network has already reached a certain size. The sooner you react, the better.

Open standards and open formats ensure that companies cannot exploit the network effect to achieve a monopolistic status, this is one of the main reasons why open standards and formats are important for everybody.

---

### Post by Typhoon on 2006-09-30
I also think that open standards are important. I have managed to get most of my Windows friends and family to install Gizmo Project. A very good alternative to Skype and easy for Windows users to install.

[http://www.gizmoproject.com/](http://www.gizmoproject.com/)

Typhoon

---

### Post by AgenT on 2006-10-04
Wengophone (the software) will not, as of now, allow you to call other SIP networks. This is *not* a Wengo (SIP service provider) limitation, rather a Wengophone one. The programmers have not managed to code this into the program yet. 

However, you are free to use any SIP program with the Wengo network. If the SIP program you choose allows you to call out of the network (most will), then you will be able to call non-Wengo users using from your Wengo network account. You may also call Wengo users from other SIP networks.

---

### Post by DoctorMO on 2006-10-04
> DrMo can you please explain what you mean? I was planning of moving the rest of the family that uses Windows to OW...

Perhaps I was wrong about wengo phone being closed, but their software I don't think compares to Gizmo; but since it's all based on SIP the client we all use doesn't really matter and you should offer anyone the choice between them to see which ones suites.

---

### Post by henriquemaia on 2006-10-04
How do I make landline calls through ekiga, for example?

---

### Post by henriquemaia on 2006-10-04
I found inside ekiga what I need to do. If I have further questions, then I'll ask you. Thanks anyway.

---

### Post by banjobacon on 2006-10-04
> **jason.b.c said:**
> Why does that matter..? , Who care's if it's propritory..:confused:

Imagine T-Mobile customers could only call other T-Mobile customers. Or Yahoo Mail users could on'y email other people that used Yahoo email. Does that sound good to you?

---

### Post by cvmostert on 2006-10-25
> **henriquemaia said:**
> I found inside ekiga what I need to do. If I have further questions, then I'll ask you. Thanks anyway.

I know you found out... but i am gonna tell you anyway, there might be someone else needing it.

I use a voipbuster account to call to landline via ekiga. [www.voipbuster.com](www.voipbuster.com)

it is not difficult to set up the account in ekiga, and then you can call lots of countries for free... up to now, it is the cheapest one I have found for my purposes... South Africa and Switzerland.

cheers

---

### Post by patrick295767 on 2006-11-15
> **arkangel said:**
> here we have a problem , i have to call some family , and they have no clue  what  linux is , or even windows ,  they only know how to click in the skype icon and how to  answer when i call ,  then  no other way  than using skype ,  i hope one day  there will be  a free version of  skype-compatibel app  , meanwhile  use what fits you  better

it is indeed right. Is there now sthg compatible with skype accounts ? 
:KS  Or a way somehow ...

---

### Post by danielph on 2006-12-24
> **patrick295767 said:**
> it is indeed right. Is there now sthg compatible with skype accounts ? 
:KS  Or a way somehow ...
Something compatible - no, something to challenge - that is where the likes of Wengophone and Ekiga step in using open protocols such as SIP.

There was a report that a Chinese based company reverse engineered the code of the skype app to make calls through the Skype network, but the point is if you use something Skype compatible, you are on their network and tied to there conditions as has already been mentioned.
[http://www.vnunet.com/vnunet/news/2160383/skype-protocol-hacked](http://www.vnunet.com/vnunet/news/2160383/skype-protocol-hacked)

---

