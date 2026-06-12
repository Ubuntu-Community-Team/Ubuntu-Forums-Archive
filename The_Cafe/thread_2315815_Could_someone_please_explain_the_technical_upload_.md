---
title: "Could someone please explain the technical upload restrictions with DSL?"
date: 2016-03-02
forum: The Cafe
---

### Post by Neko_no_Nya on 2016-03-02
I hope this is an okay place to post this. It seemed like the most appropriate place since it isn't really OS or PC hardware related.

I live a mile from my ISP's junction box in a rural area. Currently, DSL is my only option from this single provider. They offer up to 100 Mbps down and 50 Mbps up. I currently have 10 Mbps down and 1 Mbps up. I called them today hoping to increase my down to 15 Mbps and they said I am just too far from the box to get that speed with DSL. Apparently, if I was closer to the box they could. Since I'm too far, they said this is only possible if they run a fiber optic cable down my road. They said they are actually in the process of determining if they will do so because apparently they want to expand their coverage area and I am one of the last houses the current line extends to. But for today, I'm stuck. Okay, so I get that I can't get any more down right now.

This is where I get confused. I also wanted to upgrade my upload speed from 1 Mbps to 5 Mbps. Again, they are telling me I am at the max upload speed because of the DSL restriction and distance from the box. Okay, I get that I couldn't have an active 10 Mbps down and be uploading 5 Mbps at the same time but if I was only uploading, why can't I do so at 5 Mbps? If the line can handle 10 Mbps down, shouldn't it be able to handle 5 Mbps up if that is all it is doing? Or even 5 Mbps down while uploading at 5 Mbps?

Is there an actual technical reason as to why I am limited to a measly 1 Mbps up when I get 10 Mbps down? Is this just a matter of the customer support person not knowing what they are talking about? Or is this just a matter of them not wanting to do it because they don't want to deal with people who won't understand why they are paying for 10 Mbps down and 5 Mbps up but can't do both simultaneously? If the latter is the issue, I am more than willing to pay for both even if I can't do both at the same time.


If the line can indeed handle more up than they are telling me, I am going to call back and try to reason with them. This 1 Mbps is just killing me. I do get a decent ping at around 40-43 ms though. Not the best but I have had much worse. I used to get over 80 ms but I think they did an upgrade on the lines a number of years ago, right around the time I was finally able to go up to 10 Mbps. I can't quite remember, it was years ago. I just know they dug my backyard up and my ping got better and I had new speed options. I'm not sure if that is relevant but the more information the better.

I'm hoping someone can enlighten me. Thanks in advance!

UPDATE: 

Okay. I ended up getting in contact with someone from my ISP's tech support who seemed to be more knowledgeable. He said this is all a modem issue. I have an older modem and apparently it doesn't properly support anything over 1 Mbps. There is a setting to bump it up to 2 Mbps but the modem couldn't handle it. So I was told anyway. The tech tried remotely altering it and apparently it was having remote connection issues when he tried to alter it. He tried twice and at one point he was scared he fried my modem because it wouldn't connect (even though I told him sometimes when you unplug it and plug it back in, it won't connect so you have to do the process a second time). He said there are actually two things he can do for me. One is send me a newer modem but it will still only bump me up to 2 Mbps up. The second option is to pair bond my DSL and hook me up with a modem that supports pair bonding. He says this modem is capable of supporting 4 Mbps up.

He says although line distance does play a factor, the biggest issue here is that they don't offer any modems that are designed to support over 4 Mbps up! It wouldn't matter if I lived right next door to the junction box. My ISP simply doesn't offer a DSL modem that supports over 4 Mbps up. Only their fiber optic modems are designed to handle more than 4 Mbps up (up to 50 Mbps).  This is ridiculous. I have a copper line that will support speeds higher than 4 Mbps up but my ISP doesn't make (or source, whatever) any modems that will take advantage of this? Seriously?

Office hours were over so I couldn't schedule a service visit so I have to call back tomorrow.

I forgot to ask but if they are pair bonding my DSL, I should be able to jump up to 20 Mbps down if I wanted. Except knowing my ISP, they probably don't offer a DSL router than can handle speeds up to 20 Mbps. Hopefully I can at least get the 15 Mbps I wanted now.

Is any of this sounding sketchy to anyone?

---

### Post by Old_Grey_Wolf on 2016-03-02
The reason (A)DSL is asymmetric is because it was designed that way. What you have appears to be an Asymmetric Digital Subscriber Line (ADSL).

With ADSL, there are different frequency ranges for download and upload. The frequency ranges were divided up into bins. When the frequencies bins were split up, more were allocated to the downstream than the upstream. The reasoning was that the largest proportion of customers use the Internet for consumption and not publishing.

If you have ADSL you will always get faster speeds down.

---

### Post by Neko_no_Nya on 2016-03-02
> **Old_Grey_Wolf said:**
> The reason (A)DSL is asymmetric is because it was designed that way. What you have is an Asymmetric Digital Subscriber Line (ADSL).

There are different frequency ranges for download and upload. The frequency ranges were divided up into bins. When the frequencies bins were split up, more were allocated to the downstream than the upstream. The reasoning was that the largest proportion of customers use the Internet for consumption and not publishing.

If you have ADSL you will always get faster speeds down.

Yeah, sorry. I forgot to mention I have ADSL. I think it is ADSL2+. It would have to be to get 10 Mbps down at around a mile away, right? And actually, it turns out that while my house is only one mile from the box, the length of the copper cable is actually 9000 feet because of all the obstacles they had to go around. 

Okay, I think I'm getting the gist of what you are saying. So the copper wire itself isn't just a standard copper wire? It actually has certain properties that allow it to carry various frequencies at different quantities or bandwidths (for lack of a better word)? So the frequency that has the most bandwidth available is chosen for the download? Or are there actually multiple wires in a single line dedicated to each task?

Also, I posted an update to my post before you replied. I provided some new information from another phone call I had with them. At one point I was told distance was an issue and then at another point it was more of a limitation of the wire. At 9000 feet, I can't see distance not being an issue. He later said it wouldn't matter if I lived next to the distribution box because it was a modem issue. I suppose that is partially correct. I'm guessing they don't offer standard standard ADSL modems over 2 Mbps up because the ADSL line doesn't even support it. 

I thought in the early days ADSL2+ had a max upload of something around 7-7.9 Mbps. I consistantly get .75 - .85 Mbps up (sorry I know I said 1 Mbps, that is just what my plan is). I don't know much about this kind of stuff but haven't there been advancements that have allowed ADSL2+ to surpass the initial limitations? If so, my ISP must be using it for me to get these speeds so far from the box and according to them, to be capable of getting 2 Mbps with a new modem and 4 Mbps up by pair bonding the line.

---

### Post by Old_Grey_Wolf on 2016-03-02
> **Neko_no_Nya said:**
> ...So the copper wire itself isn't just a standard copper wire? It actually has certain properties that allow it to carry various frequencies at different quantities or bandwidths (for lack of a better word)? So the frequency that has the most bandwidth available is chosen for the download? Or are there actually multiple wires in a single line dedicated to each task?...

It is standard twisted pair copper wire. Copper wire has some properties that limit it's use; although, engineers are learning to get more speed out of it. The use of the frequencies for upload and download was chosen, and not limited by the wire itself. More of the frequencies were allocated for download, because, of the common use by customers. Customers downloaded a lot more data than they uploaded. There are no wires in the line dedicated to upstream or downstream use.

---

### Post by Neko_no_Nya on 2016-03-02
> **Old_Grey_Wolf said:**
> It is standard twisted pair copper wire. Copper wire has some properties that limit it's use; although, engineers are learning to get more speed out of it. The use of the frequencies for upload and download was chosen, and not limited by the wire itself. More of the frequencies were allocated for download, because, of the common use by customers. Customers downloaded a lot more data than they uploaded. There are no wires in the line dedicated to upstream or downstream use.

So the frequencies used are being done on the ISP end and the modem is programmed to properly interpret these frequencies. So basically, ADSL and SDSL are really using the same wires and mechanically are the same thing. So in SDSL where the upload and download are the same, it is simply a different allocation of the available bandwidth available to the different frequencies as determined by the ISP.

So that would mean my ISP could at any time decide to change over to SDSL and send everyone new modems? In theory of course. I'm guessing they may have to change some hardware on their end too.

And while we are on the topic of DSL, could I ask another question?

DSL basically just uses telephone lines, right? So, how much bandwidth can the telephone line actually handle? Let's say a line goes through 10 properties and each house gets 10 Mbps on ADSL. That means at a peak, max load, you are talking about 100 Mbps. Is that correct? Do additional lines have to be added at some point. I'm just confused as to how you can have numerous people tapped into the phone line and they are restricted in Mbps but the main lines themselves seem to handle way more than that. I don't know if I am phrasing this correctly but do you get what I'm trying to ask?

Is this Mbps limit due to having to distribute the bandwidth? Like, if they cut off internet to every house that connects from the same junction box, using the same main line, couldn't I theoretically be able to use the full bandwidth of the line for myself? This is all in theory of course. I'm just trying to understand the concept behind it.

But basically, the line can handle a lot of bandwidth but they split it up into chunks so each user gets a fair share. Right? Or are they running multiple phone lines? If they are able to pair bond me, then that means there is more than one phone line, right? And presumably someone isn't using their service so the line is free for me to use?

---

### Post by coldraven on 2016-03-03
> **Neko_no_Nya said:**
> So the frequencies used are being done on the ISP end and the modem is programmed to properly interpret these frequencies. So basically, ADSL and SDSL are really using the same wires and mechanically are the same thing. So in SDSL where the upload and download are the same, it is simply a different allocation of the available bandwidth available to the different frequencies as determined by the ISP.

So that would mean my ISP could at any time decide to change over to SDSL and send everyone new modems? In theory of course. I'm guessing they may have to change some hardware on their end too.

And while we are on the topic of DSL, could I ask another question?

DSL basically just uses telephone lines, right? So, how much bandwidth can the telephone line actually handle? Let's say a line goes through 10 properties and each house gets 10 Mbps on ADSL. That means at a peak, max load, you are talking about 100 Mbps. Is that correct? Do additional lines have to be added at some point. I'm just confused as to how you can have numerous people tapped into the phone line and they are restricted in Mbps but the main lines themselves seem to handle way more than that. I don't know if I am phrasing this correctly but do you get what I'm trying to ask?

Is this Mbps limit due to having to distribute the bandwidth? Like, if they cut off internet to every house that connects from the same junction box, using the same main line, couldn't I theoretically be able to use the full bandwidth of the line for myself? This is all in theory of course. I'm just trying to understand the concept behind it.

But basically, the line can handle a lot of bandwidth but they split it up into chunks so each user gets a fair share. Right? Or are they running multiple phone lines? If they are able to pair bond me, then that means there is more than one phone line, right? And presumably someone isn't using their service so the line is free for me to use?


The word you are looking for is contention.
[https://en.wikipedia.org/wiki/Contention_ratio](https://en.wikipedia.org/wiki/Contention_ratio)

---

### Post by Neko_no_Nya on 2016-03-03
> **coldraven said:**
> The word you are looking for is contention.
[https://en.wikipedia.org/wiki/Contention_ratio](https://en.wikipedia.org/wiki/Contention_ratio)

Yes! That is the term I was looking for but didn't know existed, lol.

Well, I did a bunch of research and had an interesting talk with my ISP's tech guy who actually turns out to be a cool dude. I think I finally get the gist of how DSL works. 

I see that contention is not an issue with ADSL because of the way it works. Awesome! Each household (or business) has its own dedicated line running from the junction box or node. So there are a ton of wires going in all kinds of directions. No wonder it is so expensive to lay (well, that and because of government regulations).

I also found out that I have ADSL2+M. I figured I'd have to have at least ADSL2+ given my speeds and I had a strong suspicion it was M due to the fact I can get close to 4 Mbps up now.

So get this. My ISP is coming out tomorrow morning to pair bond my connection and give me a new modem. They said I should be able to get close to 4 Mbps. They only offer Mbps up plans at 1, 2, 5 Mbps and up. At first they were only going to give me 2 Mbps because they didn't want to sell me the 5 Mbps plan because I wouldn't get 5 Mbps. But I told them I understand the situation and am more than willing to pay for the 5 Mbps up plan even if I get a little under 4. They said since I understand the limitations they will sell it to me. Yay!

I'm probably going to tell them to up my download speed to 20 Mbps down now too. I told them I had to think about it but now I realize, why do I need to think about it? lol

And my situation gets even better. My ISP is a rural ISP so one wouldn't expect fiber, right? Wrong! I already knew they offered fiber in certain areas but I thought it was just in bigger towns and cities. They told me they are actually in the process of converting their ENTIRE network to fiber. They said they pride themselves on being one of the few rural ISPs to offer fiber so they really want to get the whole network converted. They said I will be getting fiber, they just don't know exactly when. They said about 50% of the network is now converted.

Currently, they offer up to 200 Mbps down and 50 Mbps up on their fiber plan but once the entire network is converted, they are going to start offering gigabit! Gigabit! In the middle of the country. I'm in the middle of nowhere. This is so amazing. The tech guy said all their fiber modems are already capable of supporting gigabit so they are really just waiting for the whole fiber network to be finished and they can start "flipping switches". I really wanted to move but if I do, being in their coverage area will be a must. I won't even consider any property outside their coverage zone. I know I'm rambling a bit but I am so excited! I'm getting a nice speed boost tomorrow and in the future, I will be getting a ridiculous boost. :D

And thanks for helping clear some of this up for me guys! I appreciate it.

---

### Post by coldraven on 2016-03-04
You're lucky, I live in a remote area and get about 4MB down and a fraction of that up! I don't see fibre coming my way soon :(

---

### Post by grahammechanical on 2016-03-04
Ever heard of a microfilter? It is what makes it possible for me to connect to the internet using a DSL modem at the same time as my wife is making a telephone call.

[http://bt.custhelp.com/app/answers/detail/a_id/635/~/why-do-i-need-adsl-filters-%28microfilters%29-and-where-do-they-go%3F](http://bt.custhelp.com/app/answers/detail/a_id/635/~/why-do-i-need-adsl-filters-%28microfilters%29-and-where-do-they-go%3F)

The limits for broadband are caused by (a) using twin copper cable between the house and the telephone exchange. And (b) using cables to inter-connect exchanges that are not fibre optic but old style cables that are massive bundles of single strand copper wires.

Regards.

---

### Post by Neko_no_Nya on 2016-03-04
> **coldraven said:**
> You're lucky, I live in a remote area and get about 4MB down and a fraction of that up! I don't see fibre coming my way soon :(

I'm sorry to hear that. I live a pretty remote area and I never thought this day would come. I really feel your pain because for years I was stuck on dial-up, well into the age of DSL and cable. When my ISP finally brought DSL to me, it literally changed my life. They have been very pro-active in terms of delivering the fastest speeds possible. It is pretty awesome that even in the areas they don't yet have fiber, they are using ADSL2+ Annex M and support pair bonding. So many rural ISPs just do the bare minimum because they know people don't have much of a choice, if any and starting a new ISP is not an easy task so they are unlikely to get any real competition.

When the tech was here today, he told me that they will be laying fiber to my house this summer. He said they actually have fiber just over the hill from me so he isn't sure why they didn't just route it to my house as well. I'm guessing it is because of logistics and where the junction nodes are located and it made sense to just route from the same source as the DSL.

Now I'm getting 17.97 down and 2.86 up. That is definitely a marked improvement. They just couldn't get my upstream any higher but I'm still happy. This will hold me over quite nicely until fiber arrives. I can actually stream 1440p off YouTube now. 4k was soo close. It just had minor stutter every few seconds where the screen would freeze for maybe half a second. I never got the buffer indicator though. I only have a 1080p monitor anyway. I just wanted to try it out.

> **grahammechanical said:**
> Ever heard of a microfilter? It is what makes it possible for me to connect to the internet using a DSL modem at the same time as my wife is making a telephone call.

[http://bt.custhelp.com/app/answers/detail/a_id/635/~/why-do-i-need-adsl-filters-%28microfilters%29-and-where-do-they-go%3F](http://bt.custhelp.com/app/answers/detail/a_id/635/~/why-do-i-need-adsl-filters-%28microfilters%29-and-where-do-they-go%3F)

The limits for broadband are caused by (a) using twin copper cable between the house and the telephone exchange. And (b) using cables to inter-connect exchanges that are not fibre optic but old style cables that are massive bundles of single strand copper wires.

Regards.

Yes, I have heard of them but have never used one. We haven't had phone service for half a decade, easy. By the time we got DSL, we had dropped our phone service because, well, cell phones.

---

### Post by coldraven on 2016-03-13
This will only make sense for UK customers.
In the days of dial-up I was with OneTel. They had a scheme whereby you could use a charge-by-the minute connection so I used it sparingly. BT got a big chunk of money from the taxpayers to update exchanges. So they updated my exchange to 512kb! This was pretty useless as it could even not handle streaming from the BBC. But OneTel assured me that they could now connect me and even sent me a ADSL modem. I watched the LED on that thing flash away for months and still it did not connect. After many calls I got an engineer in Stornoway who told me to throw the modem into the bin as it was useless. <that's being polite>. Eventually BT upgraded to ADSL+ but did not tell anyone because they were making more money on the lower speed connection. Luckily I monitored Samknows and rang my new ISP <redacted> who told me that BT had not told them of the update. I cannot say here what I think of BT.

---

### Post by him610 on 2016-03-15
I think it is a shame that the ISP providers with deep pockets have virtually abandoned the more rural areas to the smaller ISPs. You probably get better personal service from a smaller ISP, but think of the speeds that one gets from Verizon with its fibre. Eventually, even the rural areas will get fibre or some other high-speed service. The copper in those phone lines lines will be reclaimed for higher priority purposes because it will be cheaper than mining for more copper.

---

### Post by coldraven on 2016-03-15
> **hgh9mrp said:**
> I think it is a shame that the ISP providers with deep pockets have virtually abandoned the more rural areas to the smaller ISPs. You probably get better personal service from a smaller ISP, but think of the speeds that one gets from Verizon with its fibre. Eventually, even the rural areas will get fibre or some other high-speed service. The copper in those phone lines lines will be reclaimed for higher priority purposes because it will be cheaper than mining for more copper.

Not entirely abandoned because **any** ISP that uses my exchange has to buy from BT Wholesale. Using my small ISP does have some advantages. When I call them for help the phone is answered by a human almost immediately. They charge 4p a minute for technical help and the longest call I've had was 5 minutes. The downside is that they don't have weekend staff so if my internet goes wrong on a Saturday I have to wait for them to fix it. Having said that it is usually their DNS server that breaks so I just change my router settings.
I have never hit a download limit, I don't think they care if I use a lot of bandwidth :)

---

