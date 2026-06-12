---
title: "Is there any public information on how wifi works?"
date: 2011-10-27
forum: The Cafe
---

### Post by ki4jgt on 2011-10-27
Is there any public information (tried searching google) information on how wifi works that isn't a tutorial for the computer ignorant people? Something that covers the inner workings of wifi without requiring me to read open source code until my eyes pop out, just a plain and simple


Chapter 1: How networks are discoverable
Chapter 2: ARP
Chapter 3: . . .

I would even settle for something a little more concentrated, just as long as I don't have to read another (This is a wireless phone. Wifi works just like this wireless phone. Your computer is the phone and the router is the base) I mean, yes this is a great analogy but when the Internet is peppered with it to the point of no one being able to find specifics, it kind of drives people insane. I've asked this online before (for documentation) and all I got was someone believed it did spreadspectrum hoping between three frequencies. Is there a play by play online somewhere that I could read (preferably in a concentrated quicknotes version)? I'm currently in the middle of the wikipedia (802.11) article now, but it doesn't say how the connections are achieved (The protocol) Anyone who can help with this, it would certainly be appriciated. Thanks guys.

---

### Post by haqking on 2011-10-27
> **ki4jgt said:**
> Is there any public information (tried searching google) information on how wifi works that isn't a tutorial for the computer ignorant people? Something that covers the inner workings of wifi without requiring me to read open source code until my eyes pop out, just a plain and simple


Chapter 1: How networks are discoverable
Chapter 2: ARP
Chapter 3: . . .

I would even settle for something a little more concentrated, just as long as I don't have to read another (This is a wireless phone. Wifi works just like this wireless phone. Your computer is the phone and the router is the base) I mean, yes this is a great analogy but when the Internet is peppered with it to the point of no one being able to find specifics, it kind of drives people insane. I've asked this online before (for documentation) and all I got was someone believed it did spreadspectrum hoping between three frequencies. Is there a play by play online somewhere that I could read (preferably in a concentrated quicknotes version)? I'm currently in the middle of the wikipedia (802.11) article now, but it doesn't say how the connections are achieved (The protocol) Anyone who can help with this, it would certainly be appriciated. Thanks guys.

some contradictions there, you want it plain and simple, but the inner workings and not for computer illiterate people.

You cant have both ;-)

and you have searched google and havent found anything ? your google-fu is weak young padawan.

also wifi is a large subject.

I would recommend the RFC's if you want the internal workings.

[http://www.faqs.org/rfcs/rfc-titles.html](http://www.faqs.org/rfcs/rfc-titles.html)

and the links to each of a,b,gn etc here [http://en.wikipedia.org/wiki/IEEE_802.11](http://en.wikipedia.org/wiki/IEEE_802.11)

If you want a good book then [http://www.amazon.com/Wi-Foo-Secrets-Wireless-Andrew-Vladimirov/dp/B005HKO1PS/ref=pd_sim_b_8](http://www.amazon.com/Wi-Foo-Secrets-Wireless-Andrew-Vladimirov/dp/B005HKO1PS/ref=pd_sim_b_8) 

and [http://www.amazon.com/802-11-Wireless-Networks-Definitive-Second/dp/0596100523/ref=pd_sim_b_3](http://www.amazon.com/802-11-Wireless-Networks-Definitive-Second/dp/0596100523/ref=pd_sim_b_3)

---

### Post by ki4jgt on 2011-10-27
> **haqking said:**
> some contradictions there, you want it plain and simple, but the inner workings and not for computer illiterate people.

You cant have both ;-)

and you have searched google and havent found anything ? your google-fu is weak young padawan.

also wifi is a large subject.

I would recommend the RFC's if you want the internal workings.

[http://www.faqs.org/rfcs/rfc-titles.html](http://www.faqs.org/rfcs/rfc-titles.html)

and the links to each of a,b,gn etc here [http://en.wikipedia.org/wiki/IEEE_802.11](http://en.wikipedia.org/wiki/IEEE_802.11)

If you want a good book then [http://www.amazon.com/Wi-Foo-Secrets-Wireless-Andrew-Vladimirov/dp/B005HKO1PS/ref=pd_sim_b_8](http://www.amazon.com/Wi-Foo-Secrets-Wireless-Andrew-Vladimirov/dp/B005HKO1PS/ref=pd_sim_b_8) 

and [http://www.amazon.com/802-11-Wireless-Networks-Definitive-Second/dp/0596100523/ref=pd_sim_b_3](http://www.amazon.com/802-11-Wireless-Networks-Definitive-Second/dp/0596100523/ref=pd_sim_b_3)

Well, I'm on the quest for another invention (crazy idea according to some) I know the proper way to go about it is to learn it fully. That's why I asked for something concentrated. I want the idea to be developed but I don't want to spend a decade learning how to do it :-(.

EDIT: I'm mainly looking into how to build a wireless router.

---

### Post by cguy on 2011-10-27
> **ki4jgt said:**
> Well, I'm on the quest for another invention (crazy idea according to some) I know the proper way to go about it is to learn it fully. That's why I asked for something concentrated. I want the idea to be developed but I don't want to spend a decade learning how to do it :-(.

EDIT: I'm mainly looking into how to build a wireless router.

Kids are getting more ambitious by the day! :D

---

### Post by haqking on 2011-10-27
> **ki4jgt said:**
> Well, I'm on the quest for another invention (crazy idea according to some) I know the proper way to go about it is to learn it fully. That's why I asked for something concentrated. I want the idea to be developed but I don't want to spend a decade learning how to do it :-(.

EDIT: **I'm mainly looking into how to build a wireless router.**

So you are an electronic engineer ?

Using your own PCB design and componentry or existing ?

You want to design your own software for use with it ?

Wouldnt wanting to do all this and planning to do it pre-suppose the existence of the knowledge of 802.11 in the first place ?

---

### Post by F.G. on 2011-10-27
so, perhaps not really what your looking for, but quite a good way to  pick up basic ideas about the security and transmission protocols i  found was the intro book for backtrack 5. it's pretty readable, and  while the emphasis is on practicing/learning the tools, it does cover  some bits about data/management/control frame structures and that kind  of thing:

~snip~

i'm curious as to why you want to build a router (rather than buy or adapt one) and what the project is you have in mind.

---

### Post by ki4jgt on 2011-10-27
> **haqking said:**
> So you are an electronic engineer ?

Using your own PCB design and componentry or existing ?

You want to design your own software for use with it ?

Wouldnt wanting to do all this and planning to do it pre-suppose the existence of the knowledge of 802.11 in the first place ?

> **F.G. said:**
> so, perhaps not really what your looking for, but quite a good way to  pick up basic ideas about the security and transmission protocols i  found was the intro book for backtrack 5. it's pretty readable, and  while the emphasis is on practicing/learning the tools, it does cover  some bits about data/management/control frame structures and that kind  of thing:

~snip~

i'm curious as to why you want to build a router (rather than buy or adapt one) and what the project is you have in mind.

No, I'm not an electronics engineer either. Might as well say it though, get the criticisms out of the way. :-)

In my quest to create an internet free of government interference and of being able to be shut down by the government, I have devise a horrid first draft of a completely p2p based Internet.

In my system, there are two wifi frequency segments. There is short range (what we use with our current devices) and there is long range (what the routers will use to communicate with one another) Long range consists of 15 mile coverage radiuses and use wifi networking (except with frequencies which are able to travel farther distances) long range networking is ONLY between routers. The routers use DD-WRT repeat functionality (on the long range side). All the wifi routers having cloned mac addresses and access names on the short range side ONLY to insure ease of going from router to router with wifi devices.

The devices using the newtork each receive a standard access address from a system similar to a Tor .onion address. (that would be the device's IP each time it connected to the network, it would get a new one <unless the user wanted a static one>). DNS would be handled by anyone who wanted to setup and DNS server, of course there would be a central DNS server, but users would be free to create their own.

And, Let the criticisms begin. . . :-)

EDIT: Also, everyone would have to purchase their own router. (Unless they had neighbors who were in low wifi range)

---

### Post by mips on 2011-10-27
[http://www.howstuffworks.com/wireless-network.htm](http://www.howstuffworks.com/wireless-network.htm)

---

### Post by haqking on 2011-10-27
> **ki4jgt said:**
> No, I'm not an electronics engineer either. Might as well say it though, get the criticisms out of the way. :-)

In my quest to create an internet free of government interference and of being able to be shut down by the government, I have devise a horrid first draft of a completely p2p based Internet.

In my system, there are two wifi frequency segments. There is short range (what we use with our current devices) and there is long range (what the routers will use to communicate with one another) Long range consists of 15 mile coverage radiuses and use wifi networking (except with frequencies which are able to travel farther distances) long range networking is ONLY between routers. The routers use DD-WRT repeat functionality (on the long range side). All the wifi routers having cloned mac addresses and access names on the short range side ONLY to insure ease of going from router to router with wifi devices.

The devices using the newtork each receive a standard access address from a system similar to a Tor .onion address. (that would be the device's IP each time it connected to the network, it would get a new one <unless the user wanted a static one>). DNS would be handled by anyone who wanted to setup and DNS server, of course there would be a central DNS server, but users would be free to create their own.

And, Let the criticisms begin. . . :-)

EDIT: Also, everyone would have to purchase their own router. (Unless they had neighbors who were in low wifi range)

So let me get this straight.

You want to learn the inner workings of 802.11 to build your own wireless router so you can build a new Internet ?

---

### Post by F.G. on 2011-10-27
sorry, i got done for that link. so here's one to the actual publisher, packt:
[http://www.packtpub.com/backtrack-5-wireless-penetration-testing-beginners-guide/book](http://www.packtpub.com/backtrack-5-wireless-penetration-testing-beginners-guide/book)

so, you planning on having the signal leap frogging from router to  router, to connect machines, rather than having a wired connection (just power)?  and not having an ISP. (have i got that right?). sounds plausible. if you can use airbase to do that with a computer I don't see why you  couldn't setup a super light weight distro (eg TinyOS) on a small chip  dedicated to doing that (though that may be a bit of a hack way to do  it).

certainly sounds like quite an ambitious project. you'd have to convince everyone else who uses the internet to join up for it to work.

---

### Post by mips on 2011-10-27
> **ki4jgt said:**
> 
In my quest to create an internet free of government interference and of being able to be shut down by the government, I have devise a horrid first draft of a completely p2p based Internet.

In my system, there are two wifi frequency segments. There is short range (what we use with our current devices) and there is long range (what the routers will use to communicate with one another) Long range consists of 15 mile coverage radiuses and use wifi networking (except with frequencies which are able to travel farther distances) long range networking is ONLY between routers. The routers use DD-WRT repeat functionality (on the long range side). All the wifi routers having cloned mac addresses and access names on the short range side ONLY to insure ease of going from router to router with wifi devices.


Someone asked a similar question some time ago to which I replied and provided some links. Maybe try and do a search for it.

What you are proposing has financial & technical limitations. The longer distances you wanna go the lower the frequency has to be and in the process you lose bandwidth. You can go long range but the speeds will be VERY low. The costs of this venture will put it out of reach of most people.

---

### Post by ki4jgt on 2011-10-27
> **mips said:**
> Someone asked a similar question some time ago to which I replied and provided some links. Maybe try and do a search for it.

What you are proposing has financial & technical limitations. The longer distances you wanna go the lower the frequency has to be and in the process you lose bandwidth. You can go long range but the speeds will be VERY low. The costs of this venture will put it out of reach of most people.

Yeah, I knew about the frequency to bandwidth ratio (which is why I suggested a small distance around 15 miles. I originally was going to do 30). I know the power consumption would be horrible though. The government would have to step in where citizens couldn't purchase their own boxes (between cities they could possibly put solar powered, weather resistant boxes.), Though with a VHF transceiver, I can transmit all over town with 5 watts on ham bands (no repeater used at all). However, I've never actually tried data transmissions on 2M. I would assume it to be very sluggish at best.

---

### Post by Dangertux on 2011-10-27
Wait so you want an internet free of government but you want the government to help build it? That's a little... I don't even know but there is definitely something wrong with that concept.

Besides, truth be told making it based off Wireless technology would make it much easier for any party (government included) to listen in on traffic. So I'm not entirely sure that this plan has a successful outcome.

---

### Post by mips on 2011-10-27
> **ki4jgt said:**
> Yeah, I knew about the frequency to bandwidth ratio (which is why I suggested a small distance around 15 miles. I originally was going to do 30). I know the power consumption would be horrible though. The government would have to step in where citizens couldn't purchase their own boxes (between cities they could possibly put solar powered, weather resistant boxes.), Though with a VHF transceiver, I can transmit all over town with 5 watts on ham bands (no repeater used at all). However, I've never actually tried data transmissions on 2M. I would assume it to be very sluggish at best.

Ah, I only noticed your call sign now. You probably know more about radio than me. When I studied electronic engineering I came to the conclusion that radio engineering involves a lot of black magic, what you design on paper does not always materialise in the real world so i decided to stick with digital electronics :biggrin:

As you mentioned the speeds would be really sluggish and all the protocol overheads and routing traffic would just make it worse. There are examples of rural meshed networks out there using radio but they are mostly for 3rd world scenarios where there are nothing else and anything is better than nothing I suppose.

I wish I could find that post of mine as it was full of links & examples.

Even if you do manage something like this and it takes off against all odds the chances of the gov. stepping and trying to regulate it would be very high I suspect, it's the way governments are unfortunately. Without going into politics we would be better off voting governments into power that want less power and do what they were voted in to do, stay out of peoples lives.

---

### Post by F.G. on 2011-10-27
surely there are two issues here. first is ISPs and their relationships with local governments (eg R.I.P.A. in the UK) and basically abolishing them, and thereby that aspect of control over traffic by circumventing the need for ISPs. and also the use of something like Tor to inhibit the ability to eavesdrop / monitor network traffic.  (as well as the technical aspect of designing the routers).

also I would have thought that in urban areas wifi networks overlap enough that this might be able to be implemented without new hardware.

so, here's another thought if mobile internet devices (eg samsung galaxy phone/laptops) can act as routers you could also chuck them into the mix (battery power would be an issue though)

ps disclaimer - i don't really know what i'm talking about, so beware.

---

### Post by ki4jgt on 2011-10-27
> **mips said:**
> Ah, I only noticed your call sign now. You probably know more about radio than me. When I studied electronic engineering I came to the conclusion that radio engineering involves a lot of black magic, what you design on paper does not always materialise in the real world so i decided to stick with digital electronics :biggrin:

As you mentioned the speeds would be really sluggish and all the protocol overheads and routing traffic would just make it worse. There are examples of rural meshed networks out there using radio but they are mostly for 3rd world scenarios where there are nothing else and anything is better than nothing I suppose.

I wish I could find that post of mine as it was full of links & examples.

Even if you do manage something like this and it takes off against all odds the chances of the gov. stepping and trying to regulate it would be very high I suspect, it's the way governments are unfortunately. Without going into politics we would be better off voting governments into power that want less power and do what they were voted in to do, stay out of peoples lives.

I wouldn't go as far as knowing more than you, I just studied the questions. I studied the general ideas behind them to remember them (not like some people I know who have no actual idea as to how it works at all and just studied the questions and almost got me kicked out of the exam by asking me questions during the exam LOL) but I only know general concepts. I'm losing more of that every day. I've been trying to further my knowledge, but with a hectic lifestyle I've fallen short :-(. I'll try to find your post though.

---

### Post by ki4jgt on 2011-10-27
> **F.G. said:**
> surely there are two issues here. first is ISPs and their relationships with local governments (eg R.I.P.A. in the UK) and basically abolishing them, and thereby that aspect of control over traffic by circumventing the need for ISPs. and also the use of something like Tor to inhibit the ability to eavesdrop / monitor network traffic.  (as well as the technical aspect of designing the routers).

also I would have thought that in urban areas wifi networks overlap enough that this might be able to be implemented without new hardware.

so, here's another thought if mobile internet devices (eg samsung galaxy phone/laptops) can act as routers you could also chuck them into the mix (battery power would be an issue though)

ps disclaimer - i don't really know what i'm talking about, so beware.

It's just a discussion. We all have to start somewhere LOL. The problem (in my eyes) with allowing the devices to do the dirty work is (besides batteries) handheld devices go on and off frequently. Routers on the other hand, stay on 24/7 for ease of use. If we could couple solar power into the router with the current AC system, it may cut back on power. Of course, all router would have to be weather resistant and thus add to price.
The problem with no long range frequency support is going city to city and the problem with all of it would be the sluggishness of going city to city. :-( It would be fine for local businesses and houses, but going out of city, one city over may not be that bad, but try 2 or 3 and you'd have a horrible slowness.

---

### Post by mips on 2011-10-27
> **ki4jgt said:**
> (not like some people I know who have no actual idea as to how it works at all and just studied the questions and almost got me kicked out of the exam by asking me questions during the exam LOL).

What, they asked you questions during a exam? Lol, who does that.

---

### Post by Tristam Green on 2011-10-27
> **haqking said:**
> So let me get this straight.

You want to learn the inner workings of 802.11 to build your own wireless router so you can build a new Internet ?

I'll admit, I laughed.

> **mips said:**
> What, they asked you questions during a exam? Lol, who does that.

Honey Badgers, that's who.  Know why?  Yeah, you know why.





*edit* OP:  why wouldn't you just propose a massive mesh network?  Kinda the same way the OLPC XO had intended?

---

### Post by ki4jgt on 2011-10-27
> **Tristam Green said:**
> I'll admit, I laughed.



Honey Badgers, that's who.  Know why?  Yeah, you know why.





*edit* OP:  why wouldn't you just propose a massive mesh network?  Kinda the same way the OLPC XO had intended?

Nope because you don't have intercity connections and I'm contemplating on whether this would be better served as just a message delivery system. People have actually been looking for a way to do this over radio networks for years. The computer networking would get it all connected (15 miles of it) and the computers would actually hold the software. The slowness would hold messages from being delivered, but it would be expected for mere messages. The Tor overlay of the network would be great in that messages would get to their destinations (multiple delivery routes) and they will be freely available to everyone who had the boxes. If communications went down, people could deliver their messages still because the network would be wireless.

---

### Post by andras artois on 2011-10-27
There was a really good article on ars about it. I'm just going to find it now.

EDIT: [Here it is.]("http://arstechnica.com/gadgets/news/2011/10/cutting-the-cord-how-the-worlds-engineers-built-wi-fi.ars") It's more about how it was created but it gives a pretty good insight into how it works.

---

### Post by haqking on 2011-10-27
point to point networks free of govt control...mmmmmmmm

what type of information is it you want to share ;-)

---

### Post by ki4jgt on 2011-10-27
> **haqking said:**
> point to point networks free of govt control...mmmmmmmm

what type of information is it you want to share ;-)

It's not the government control I'm worried about. It's when comms go down (cell toweres, Internet) the government thwarting is just an added bonus.

---

### Post by forrestcupp on 2011-10-27
Wifi works because of intelligent symbiont Midi-chlorians. The wifi adapters have a high Midi-chlorian count that can contact The Force, which is all around us.

That's pretty much all you need to know. It just works on its own from there.

---

### Post by mcduck on 2011-10-27
So you are basically just looking to create a new type of wireless ad-hoc network? Have you looked into the existing ad-hoc and mesh network protocols?
[http://en.wikipedia.org/wiki/Wireless_ad_hoc_network]("http://en.wikipedia.org/wiki/Wireless_ad_hoc_network")
[http://en.wikipedia.org/wiki/List_of_ad-hoc_routing_protocols]("http://en.wikipedia.org/wiki/List_of_ad-hoc_routing_protocols")

The idea is interesting, and this kind of stuff is already used for some purposes (military would be where I've used such networks IRL), the trouble would be that it only works well if there are enough connected systems in your area, or if the range of each node is large enough (which would quickly became a problem considering things like the size and power use of the devices).

...and in the end, if you want Internet connection, then you need enough of the network nodes to be connected there (with enough bandwidth, of course) to be able to sustain the Internet usage of all the others. At least at the moment this kind of networks really seem to be only suitable as a fallback solution when all the better connection methods have failed or can't be used for some other reason.

---

### Post by KiwiNZ on 2011-10-27
If you were to get something off the ground it would still be subject to law unless you are going to operate it and use it in space. If used on Earth it is subject to sovereignty.

Also if it is Wireless and therefore using radio it is subject to approval and standards compliance.

What Frequency would you use? These are a finite resource and are controlled and allocated.

---

### Post by ki4jgt on 2011-10-27
> **mcduck said:**
> So you are basically just looking to create a new type of wireless ad-hoc network? Have you looked into the existing ad-hoc and mesh network protocols?
[http://en.wikipedia.org/wiki/Wireless_ad_hoc_network]("http://en.wikipedia.org/wiki/Wireless_ad_hoc_network")
[http://en.wikipedia.org/wiki/List_of_ad-hoc_routing_protocols]("http://en.wikipedia.org/wiki/List_of_ad-hoc_routing_protocols")

The idea is interesting, and this kind of stuff is already used for some purposes (military would be where I've used such networks IRL), the trouble would be that it only works well if there are enough connected systems in your area, or if the range of each node is large enough (which would quickly became a problem considering things like the size and power use of the devices).

...and in the end, if you want Internet connection, then you need enough of the network nodes to be connected there (with enough bandwidth, of course) to be able to sustain the Internet usage of all the others. At least at the moment this kind of networks really seem to be only suitable as a fallback solution when all the better connection methods have failed or can't be used for some other reason.

I've already ruled out internet connection. I don't see the need for such a network, if all you're going to do is include the already (possibly fallible one in the first place) all you'll be doing in that situation is getting people use to using it, but instead of paying for it, they'll have it for free. That'll really go away from what I'm wanting to accomplish.

---

