---
title: "&quot;GPL v3 License marks GNU's decline&quot;"
date: 2007-06-30
forum: The Cafe
---

### Post by Adamant1988 on 2007-06-30
[http://www.thejemreport.com/mambo/content/view/317](http://www.thejemreport.com/mambo/content/view/317)

I would normally place a small excerpt from the article here to provoke you to read it but I think the title alone should be sufficient.  The man pretty much sums up my opinion of the FSF and the latest GPL. 

Thoughts?

---

### Post by thegnome87 on 2007-06-30
Yeah I think this might create more of a civil war-ish ecosystem than the Microsoft deals, though I mustn't forget it's closely related to it.

> 
So if a competitor goes to the store and buys your game console, then finds a cheaper way to make the same thing using the same software you created, they could make a case that you have no patent claims against them for copying your designs.

Isn't this what the GPL 2 is about?  You can copy and use the original source code/"design" and build upon it provided you keep it open and allow others to do the same to your modified source code?

The issue here is about patents, I know, but (correct me if I'm wrong) you aren't actually **giving away** rights to your design since the modifier can have his modified version copied/modified by you or someone else as well.


This article gave me a headache (the confusion, not disagreement with it)

Can anyone explain, (pardoning my ignorance and ADD-ish lack of ability to absorb big article rants into concise points), in bullet points what changes is the GPL 3 making to the GPL 2?  The main jist I get is that it seems to place serious complications/restrictions on the inclusion of closed source software (codecs, legal DVD decoders) in OSS.

---

### Post by needtolookatascreenshot on 2007-06-30
Pretty lame and dumb article, imho.

The author doesn't know anything about the GPL3, he just assumes all the time what he, obviously without any legal background, thinks it might mean and of course he always assumes the worst in his opinion. 

Now, as there are a lot of resources and discussions and legal opinions available on this matter, it's anybodies guess why the author chooses not to educate himself before writing his article.

To make matters worse, the author seems to think he can compensate for his obvious ignorance on his subject by using the strongest language available to him. I think it's pretty clear that this strategy doesn't work out.

To sum it up, it's a poorly written and even worse researched hit piece and nothing more, which, btw., is pretty sad, as a critical but informed debate about the newest version of the GPL would be very interesting indeed.

---

### Post by @trophy on 2007-06-30
> **Adamant1988 said:**
> [http://www.thejemreport.com/mambo/content/view/317](http://www.thejemreport.com/mambo/content/view/317)

I would normally place a small excerpt from the article here to provoke you to read it but I think the title alone should be sufficient.  The man pretty much sums up my opinion of the FSF and the latest GPL. 

Thoughts?

Yeah, I don't know what I think about that.  I'm no big fan of the GPL either.  But FUD about it doesn't do anybody any good.  Making a GPLv3 game console does not require you to "license all of your game console related patents, and possibly patents for other devices as well."  

Also, you *can* prevent cheating with open source software.  It requires designing the game in a secure fashion, though.  The server is god as far as the game is concerned.  Don't trust client machines at all.  Closed or open source, that's the only way to write a secure client-server system.  Anybody who says otherwise is either lying or has their head in the sand.  For an interesting essay about this very subject, check out [The Case of the Quake Cheats](http://www.catb.org/esr/writings/quake-cheats.html) by Eric S Raymond.

But basically my feelings on it are this:  there are people out there (Microsoft is chief among them) that want to scuttle open source.  Completely.  If given a chance, they will do so.  I think partly RMS sees that and is trying to  cover up anywhere that looks like a soft spot.  Cause if they find a single chink in our armor, we're done.  And I agree with that motive.  But I think also partly RMS thinks that *all* software should be free.  That software is essentially a complicated math problem, and is therefore as free as air.  This I disagree with quite strongly.  I think open programs are generally better, and that open source processes encourage better work out of developers, but I don't think that absolutely all software everywhere has to be free before I'll be happy. 

But there's a third motive to the GPL, and this one I wish people would pay more attention to.  It's there to avoid people being leeches.  It basically says "I'm writing this software and I'll let you use it/modify it/whatever, but you have to reciprocate."  Which is different from the BSD "Just don't come crying to us when it blows up, ok?" and closer to the idea of ubuntu.  We all benefit from the extremely rapid progress of development, which only happens if we share with each other.  And in that sense, I agree with RMS... though his methods make him seem like a poor spokesman for the cause.

---

### Post by Inc&#940;nus on 2007-06-30
> **needtolookatascreenshot said:**
> The author doesn't know anything about the GPL3, he just assumes all the time

I thoroughly agree. All made up off the top of his head, and all nonsense.


In the end, people can cry the sky is falling all they wish because Free Software scares them, but if the GPL cat is among the protectionist pigeons now, that's simply a logical consequence **of** that protectionism.

It's what happens when complex systems/environments/markets/whatever petrify through some influence getting total control - it's entropy, self-correction of the system.

At the point where free software had a stranglehold on the system, you can bet your bottom dollar the same thing would happen in another direction.

---

### Post by steven8 on 2007-06-30
The GPLv3 is designed to conteract an incredibly complicated situation, which is full of grey areas galore.  Very difficult.  It would require a great deal of verbal doubling-back, so to speak.  I think the GPLv3 is an excellent document, but people may just close their minds to it's real purpose as this writer has done, and yes. . .that will cause damage.

---

### Post by Erunno on 2007-06-30
I'm wondering what will happen now to all the companies which have made patent protection deals with Microsoft once the first batch of GNU tools are relased under the GPL3.

---

### Post by Polygon on 2007-06-30
people still have a choice

gplv2 is still a valid licence. if people dont like gplv3, then use v2. simple as that.

---

### Post by kripkenstein on 2007-06-30
> **@trophy said:**
> Also, you *can* prevent cheating with open source software.  It requires designing the game in a secure fashion, though.  The server is god as far as the game is concerned.  Don't trust client machines at all.  Closed or open source, that's the only way to write a secure client-server system.  Anybody who says otherwise is either lying or has their head in the sand. 

Well said, that is 100% right. Trusting the client to ensure fairness will always end up failing, just like DRM will always fail: the client software (or media, for DRM) is in the user's hands - a way will always be found to get around whatever technical restrictions you attempt. One amusing example I've heard discussed is to run a FPS game in virtualization, and have an app in the main OS help you out with aiming the weapon, that is, move the mouse to the target (this would require 3D acceleration to work well with virtualization, though, which is not quite here yet... but soon). This is exactly the same idea as playing DRMed media inside a virtual machine and copying the screen output in the main OS.

Regarding solutions for open-source games without cheating, yes, you need to basically have the server be 'god'. But there are other clever ideas as well. For example, you can change the network protocols on a daily basis and only allow clients that upgraded to the current version. This means that, even though you give out the source code, if would take a person several hours to integrate their cheat patches with the current source code (assuming the daily modifications are tricky enough). So cheating will become impractical.

Anyhow, as others have said, the author of the anti-GPL3 article isn't saying much new, and perhaps doesn't fully understand the GPL3, as hinted at by
> 
Restrictions aside, the aspect of the GPL version 3 that bothers me most is that it is totally impossible for a layman to understand.

Yes, it is hard - much harder than other licenses - for a layperson to understand. But then source code is hard for lawyers to understand. The GPL3 is a **legal** document; it shouldn't be made easily-understood by compromising on what it tries to achieve. Regarding the actual problem - developers not understanding the GPL3 - there are easy solutions. There is the GPL FAQ on the FSF's website, which is very clear, and in general there is only one GPL3 that will be used by many projects, so once you **do** understand the GPL3, that knowledge will serve you with respect to all of them.

---

### Post by Tomosaur on 2007-06-30
The GPL3 is more restrictive than GPL2, certainly, but as far as I'm concerned, the restrictions are obviously to prevent 'bad things'. People who have made a conscious decision to use the GPL obviously want what the GPL offers - a legal grounding on which they can prevent people abusing their hard work. All of the arguments in this article are fundamentally flawed when you realise that nobody forces anybody to use the GPL. The only time you 'have' to use it is if you have taken GPLd code for use in your project. If you don't want the GPL, you don't use GPLd code, it's as simple as that.

In my opinion - the whole system is fundamentally flawed. This article actually makes the argument that the GPL stops people making a monopoly, as if that's a bad thing. Surely it is better for everyone if companies are forced to compete? So what if the engineer can't stop people using his / her work? It forces every 'version' of that product, from different companies, to be the best that it can be, or find a niche where it can succeed. It's absolutely, categorically, not a bad thing that the GPL forces those who **VOLUNTARILY** use it to respect the freedom of others to alter, modify, and otherwise mess around with whatever it is they have bought / downloaded / acquired. If you don't like the GPL, don't use it. Don't hate the player, hate the game.

---

### Post by jiminycricket on 2007-06-30
As Eben Moglen said, "The GPLv2 became perfect the minute we started the GPLv3.  Even Microsoft loved it, even though only a few years earlier they were calling it un-American and Communist." (pp from a Google Talks video)

BTW to reply to that article, you can certainly include DRM in a GPLv3 product, just like Gstreamer has a DRM stack today, like in a userspace application or [four other possibilities]("http://technocrat.net/d/2007/3/22/16651").  And the GPLv2 also has a patent license, albeit implicit.  And rememeber, software patents are bad and pretty much only valid in the United States, good luck enforcing them in Europe.  However, lobbyists are certainly working very hard to get them in other countries so it's never a sure thing.

> GPLv3 also provides for explicit patent protection of the users from the program's contributors and redistributors. With GPLv2, users rely on an implicit patent license to make sure that the company which provided them a copy won't sue them, or the people they redistribute copies to, for patent infringement.

[http://www.groklaw.net/article.php?story=20060925204515114](http://www.groklaw.net/article.php?story=20060925204515114)
[http://www.groklaw.net/articlebasic.php?story=2007053116322326](http://www.groklaw.net/articlebasic.php?story=2007053116322326)

The GPLv2 patent license is apparently only valid in US law as well, whereas the GPLv3 explicit license is valid internationally.

---

### Post by forrestcupp on 2007-06-30
> **Adamant1988 said:**
> [http://www.thejemreport.com/mambo/content/view/317](http://www.thejemreport.com/mambo/content/view/317)

I would normally place a small excerpt from the article here to provoke you to read it but I think the title alone should be sufficient.  The man pretty much sums up my opinion of the FSF and the latest GPL. 

Thoughts?

I finally warmed up to GPLv2, but v3 is a little too much for me.  I don't think you need quite that much restriction to protect people's freedom.

But you know as well as I do that this isn't the popular stance around here.  I know our opinion won't change anything, but some people around here are so bullheaded and stubborn.  If anyone has an opinion other than theirs it makes that person horrible.  But even Linus prefers v2, and he's the guy that came up with this whole Linux thing.

I did think the TRIPS treaty thing was interesting.
> **Polygon said:**
> people still have a choice

gplv2 is still a valid licence. if people dont like gplv3, then use v2. simple as that.
Thank God we still have a choice.  But I don't have a choice about what other people do, and what someone else does can restrict what I want to do.

---

### Post by kripkenstein on 2007-06-30
> **forrestcupp said:**
> But even Linus prefers v2, and he's the guy that came up with this whole Linux thing.


Depends what you mean by 'this whole Linux thing'. If you mean the Linux kernel, then sure, he did. If you mean the entire operating system (sometimes called 'Linux'), of which the kernel is just one component (and not even the largest, necessarily), then no, he didn't.

---

### Post by deanlinkous on 2007-06-30
I love when a article uses the word "forced" and "restrictions" because it is obviously using sensational and dramatic words to convice someone instead of logical reasoning with practical examples....but that is par for the course with internet news anyway.

restriciton #1 dont make the code non-free
restriction #2 refer to restriction #1
^^^^^^^^^^^^^^^^^^^^^^^^^^
looks about the same as v2 to me ;)

---

### Post by koenn on 2007-06-30
> **Adamant1988 said:**
> [http://www.thejemreport.com/mambo/content/view/317](http://www.thejemreport.com/mambo/content/view/317)
I would normally place a small excerpt from the article here to provoke you to read it but I think the title alone should be sufficient.  The man pretty much sums up my opinion of the FSF and the latest GPL. 
Thoughts?
After I read the article you refer too, I read the GPL v3, and it's quite simple actually.
The GPL ensures that work which is released under the GPL, remains free to use, study, modify, and redistribute (either modified or not).  Basically, the FSF (in the GPL) says : give the people that use your software the same rights as the rights that you enjoyed when you decided to base you work on GPL'ed software. 

So far, nothing new compared to GPL v2. However, there are other ways (than restictive licensing) of limiting  the user's rignts, and GPL v3 tries to counter those as well :
a/ preventing the use of modified GPL'ed programs by means of activation keys, checksums, encryption etc ==> GPL v3 askes that these are released to the user that has obtained the binaries, together with the source code. 
b/ the (in)famous patent section which states that if you distribute  to **some** users  GPL'ed work which you claim are covered by patents, then you grant** all **users of that software the right to use it without being liable for patent infrigment. In other words : you can not grant users some rights through the GPL, then take those rights away again except for those who pay a patent license fee (or fall under one of those 'agreement not to sue for IP infringement" deals).

So, I'd say that, once you've made up your mind that free (to use, study, modify, and redistribute) software is a good idea, this makes sense. Software vendors/programmers/... who don't want to be "restritced" by these terms are still free to write their own stuff  in stead of building their work on  GPL'ed software.

---

### Post by needtolookatascreenshot on 2007-06-30
> **forrestcupp said:**
> I finally warmed up to GPLv2, but v3 is a little too much for me. 
What exactly is to much for you?

And please don't take the ramblings of the article seriously, they are quite simply wrong.

---

### Post by starcraft.man on 2007-06-30
I see what the author says in that piece. I understand (I believe) his misgivings about further restrictions ensuring freedom. I don't agree however.

First off, the legalese section is BS. I've read numerous licenses on occasions and even in recent months read over GPL 2 and 3 and other associated licenses (i equally understood that section, would be better in context of its section I imagine). They all seem the same thought out and well worded things to me, I understood all after thinking about what they said enough.

As for his other two points, first dealing with restriction to infer freedom and then with patents those are somewhat valid, I can address them.

There is one fact about freedom, in the strictest most defined sense of the word there are **NO** restrictions on your actions. In such a case, Anarchy always exists, you can (and people in general will, its proven) take anything you want, kill anyone who looks at you wrong, and do anything, anytime, anywhere without any fear of retribution except from another person with equal liberties to do anything they pleased. No matter what people say, that is the strictest definition of freedom, that however does not represent a very _functional_ version of freedom. Functional is the operative word, please take note.

Now, what has happened over the course of centuries of discussion about social contract (social contract is a term used to refer to any agreement of how people interact with each other, i.e. Capitalism, Marxism (do not confuse with Communism please), Nationalism the list goes on. It is popular in philosophic, economic and other such debates such as this one.) is that people eventually realized you have to restrict liberties in order to guarantee them to in an equal way. It sounds counter intuitive but its the only way. People have proven time and time again that without such firm guidance and regulation they will abuse the rights of others, and if not people, than corporations or other bodies.

Now that thats explained, I'm sure its fairly clear why restrictions on freedoms are needed in order to ensure a level of freedom for all affected (and why sensible people will voluntarily, when informed choose to give up a few freedoms). For examples, see the right to bear arms in the states. Imagine how it would be if any person without restriction could carry a weapon and use it without restriction. Then read how it actually is with registration and laws, pick which one you find most sensible. Oh and yes I know people break the rules (i.e. gangs have unlicensed and authorized weapons) they are not the majority of the population in these countries, who do respect the law.

These two opposites are also reflected (from what I've seen) in the BSD and GPL licenses. BSD being anarchist do anything you want freedom (with few if any clauses on that) and GPL being the enforced regulated everyone gets equal but lesser freedom. They are very incompatible views of freedom. Thusly, I don't see the authors point about giving trouble to BSD, BSD and GPL don't seem to be compatible to much of any degree at their core and its only natural that the two views would have trouble coexisting, even more so as GPL tries to improve its guarantees on the end user/developer's freedom.

Furthermore, on the matter of other proprietary technologies like DRM and game technologies, thats an unfortunate result from the crossfire of two opposing views of software (free and proprietary). That's tough luck as they say, so they'd best not use GPL 3 stuff if they intend to employ very end user restrictive technologies. That's just the way it goes it seems to me, sometimes tough stands have to be taken and inconvenience incurred.

Lastly, the patents section. His words here seem to reflect ignorance at least from what I see. Software and Hardware patents are fundamentally different, they aren't the same and shouldn't be thought of as. In the world of hardware, if I make some sort special cog that is amazing and functions better than anyone else's then thats that, patent and make money. It's hardware and thus it has its own physical limitations on distribution and other "physical" world things.

Software patents are different, they usually patent a process, a thought, a way of doing something. They have become very obnoxious and do hinder the development of software to a great extent, they have also been granted by people with very little knowledge of software (or who have been paid, at least it seems to me), amazon one click is a prime example. 

In the end, I see software patents more as patenting math (which has never been done to my knowledge). Math is free and open, all contributions by universities can be read and improved upon and fead back into the whole in an effort to further our understanding of the abstract art. This seems to me to be the closest I can make an analogy of software patents to. Imagine if you will, that someone patented the use of a square root. Sound ridiculous? Well, it seems to me thats no different than Amazon patenting one click buying or VMware patenting their snapshot technology (I believe they did from what I read) for VMs. These are obvious things that anyone in the business would want and develop separate or together, just like square roots are an obvious extension of mathematics (gradual evolution of the basics division and multiplication to the exponetial and roots).

Thats my views on his opinions, I believe that more or less quashes most of his arguments, feel free to correct me if my understanding of GPL, BSD or patents is misunderstood. I make no intentional effort to make mistakes or mislead, simply to present a well founded argument in response to the author. Nobody should have free reign to make such arguments without counter.

Oh and I won't even commend on the civil war thing, Linux holds many views and always has. Its no different. Thats it for me on the subject, if anyone has any corrections of what I said or wants to take me to task on one of my points, feel free.

---

### Post by jiminycricket on 2007-06-30
> **forrestcupp said:**
> 
I did think the TRIPS treaty thing was interesting.


He/she's wrong about TRIPS, it controversially says all technical inventions must be equally patentable, not what he's saying

> Another controversy has been over the TRIPS Article 27 requirements for patentability "in all fields of technology", and whether or not this necessitates the granting of software and business method patents.

[http://en.wikipedia.org/wiki/TRIPS#Software_and_business_method_patents](http://en.wikipedia.org/wiki/TRIPS#Software_and_business_method_patents)
[http://en.wikipedia.org/wiki/Software_patents_under_TRIPs_Agreement#Article_27_of_TRIPs](http://en.wikipedia.org/wiki/Software_patents_under_TRIPs_Agreement#Article_27_of_TRIPs)

---

### Post by @trophy on 2007-06-30
> **Tomosaur said:**
> Don't hate the player, hate the game.

LOL you had me up until this sentence.

And I know you didn't mean anything by it, but I hate this saying.  It's basically saying "Hey, the world is a crappy place where people will stab you in the back, but since I happen to be good at back stabbing, I'm going to exploit the system instead of endeavoring to change it even though I understand that its wrong."

You know, the kind of thing Microsoft might say.

---

### Post by argie on 2007-06-30
I understand little of what people complaining about GPL3 are complaining about. It's up to the author to choose the code. You want to use the code, work under his/her restrictions. As far as I can see, it's only the people who don't want to share who are having trouble. I haven't yet seen a single legitimate case against GPL3.

---

### Post by starcraft.man on 2007-06-30
> **argie said:**
> I understand little of what people complaining about GPL3 are complaining about. It's up to the author to choose the code. You want to use the code, work under his/her restrictions. As far as I can see, it's only the people who don't want to share who are having trouble. I haven't yet seen a single legitimate case against GPL3.

Me too really, maybe I don't look hard enough? It doesn't seem like many people are defending the other side in this argument either, thats no fun. Adamant, pop in and discuss with me, no one is countering my or other points >.>. 

I mean I know and think I understand why Linus is hesitant. He doesn't want to have incompatibilities with the licenses for his Linux kernel which is a very important part of Linux if not the most. If everyone collectively moves, there seems to be little problems though (as he suggested when Sun announced considering the v3 version of GPL for their products, he might be spurred to move if that happened).

---

### Post by Adamant1988 on 2007-06-30
> **starcraft.man said:**
> Me too really, maybe I don't look hard enough? It doesn't seem like many people are defending the other side in this argument either, thats no fun. Adamant, pop in and discuss with me, no one is countering my or other points >.>. 

I mean I know and think I understand why Linus is hesitant. He doesn't want to have incompatibilities with the licenses for his Linux kernel which is a very important part of Linux if not the most. If everyone collectively moves, there seems to be little problems though (as he suggested when Sun announced considering the v3 version of GPL for their products, he might be spurred to move if that happened).

I haven't had the time, nor the inclination, to become actively involved in this discussion.  I am watching it though, maybe later today I'll throw in my 2 cents. :)

---

### Post by needtolookatascreenshot on 2007-06-30
> **Adamant1988 said:**
> I haven't had the time, nor the inclination, to become actively involved in this discussion. 
Oh, so you just wanted to spread lies and disinformation and start a flamewar?

Well done.

---

### Post by Ultra Magnus on 2007-06-30
The problem with RMS and GNU/FSF is that due to the popularity of Linux and the GPL they have found themselves in a very powerful position, and from that position are trying to force people to do things the way they want. - The GPL was all about software freedom, if the new licence removes some of the freedom that isn't a good thing  (ie tivoisation isn't all that important)

---

### Post by needtolookatascreenshot on 2007-06-30
> **Ultra Magnus said:**
> The problem with RMS and GNU/FSF is that due to the popularity of Linux and the GPL they have found themselves in a very powerful position, and from that position are trying to force people to do things the way they want. - The GPL was all about software freedom, if the new licence removes some of the freedom that isn't a good thing  (ie tivoisation isn't all that important)

Please be specific.
Who exactly are they forcing?
Which freedoms specifically have been removed?

Thanks.

---

### Post by starcraft.man on 2007-06-30
> **Ultra Magnus said:**
> The problem with RMS and GNU/FSF is that due to the popularity of Linux and the GPL they have found themselves in a very powerful position, and from that position are trying to force people to do things the way they want. - The GPL was all about software freedom, if the new licence removes some of the freedom that isn't a good thing  (ie tivoisation isn't all that important)

The tivoisation clause is about giving you more freedom (i.e. ensuring since they use open source, that if they are GPLv3 you have rights to freely modify and look at whats in the Tivo). Isn't that more freedom to you? Admittedly, it means Tivo (if their software that is GPL moves to v3) will have to ensure they comply, and find new measures to DRM their product. IMO though, supporting DRM isn't a goal of any version of the GPL nor the software it supports. Whether that DRM is in Tivo, games or movies its not GPL problem. Tivo and these other companies supporting DRM are free to code their own DRM, just don't use _free software_ to support it as a base.

I'd argue Tivoisation is as important as you give it credit, just like some people find all FLOSS software to be irrelevant. And there is no forced component, they are encouraging it as a means of protecting the end users rights to Free Sofotware as I see, and to prevent exploitation by corporations (like Tivo) who use GPL software.

You might want to take another look at the GPL 3 changes.

> **Adamant1988 said:**
> I haven't had the time, nor the inclination, to become actively involved in this discussion.  I am watching it though, maybe later today I'll throw in my 2 cents. :)

Well ok >.>. Your the one that started it after all :p

---

### Post by Tundro Walker on 2007-06-30
I hate article writers like this.  Today's "now, now, now" society makes them think the first few seconds something comes out or starts up accounts for the total impact it will have in history.  Here's an analogy...

When the Wii & Playstation 3 first came out, the Playstation 3, while being far superior hardware-wise, didn't have many games to play on it.  Thus, like a week after it came out, all the media was saying it's "failed".  Granted, they made some stupid decisions (didn't ship enough, etc), but in the long run, due to better hardware, it will beat the pants off the wii and xbox 360.  It will take time though.  However, the media thinks all major happenings will occur in the first 10 days something comes out.  But, it's not that they're being short-sighted, they're just catering to todays "I don't want to follow this forever" populace.

This guy's doing the same thing.  The GPL 3 JUST CAME OUT (like, uh, YESTERDAY), and already he's doom-saying everything, like it's been out for years and has totally screwed everything up.  A lot of time and thought went into GPL 3, and it will take a lot of time and thought to realize if its accomplishing goals or not.  Until then, ignore arm-wavers like this, because they're just trying to us speculation and "sensationalist" news writing to get some attention (not for what they're writing about, but just for themselves).

---

### Post by koenn on 2007-06-30
> **starcraft.man said:**
> ... no one is countering my or other points >.>. 

well, if you're right, you're right.

---

### Post by starcraft.man on 2007-06-30
> **Tundro Walker said:**
> I hate article writers like this.  Today's "now, now, now" society makes them think the first few seconds something comes out or starts up accounts for the total impact it will have in history.  Here's an analogy...

When the Wii & Playstation 3 first came out, the Playstation 3, while being far superior hardware-wise, didn't have many games to play on it.  Thus, like a week after it came out, all the media was saying it's "failed".  Granted, they made some stupid decisions (didn't ship enough, etc), but in the long run, due to better hardware, it will beat the pants off the wii and xbox 360.  It will take time though.  However, the media thinks all major happenings will occur in the first 10 days something comes out.  But, it's not that they're being short-sighted, they're just catering to todays "I don't want to follow this forever" populace.

This guy's doing the same thing.  The GPL 3 JUST CAME OUT (like, uh, YESTERDAY), and already he's doom-saying everything, like it's been out for years and has totally screwed everything up.  A lot of time and thought went into GPL 3, and it will take a lot of time and thought to realize if its accomplishing goals or not.  Until then, ignore arm-wavers like this, because they're just trying to us speculation and "sensationalist" news writing to get some attention (not for what they're writing about, but just for themselves).

Agreed on the PS3 not being dead. It's got a lot and people just don't realize it. Not only does it play ps3 games, its natively an open media centre and it supports playing the Blu Ray format (which seems to be winning, they've had the most sales from what I seen and blockbuster went all Blu). It is a lot for just 700 dollars, its practically a whole computer with movie player and games to boot. People count things out to fast based on performance of first month or week.

Not to mention, I've seen reports that the Xbox failure rate is about 30% or more, the "red ring of death" has become so common from over heating of parts that it gets it own name, like BSoDs. That is sad. And, you need to buy the HD DVD add on separate, its not included in the price a lot of people think of when they think 360.

> **koenn said:**
> well, if you're right, you're right.

LOL! Such discussions (like this one) always have two sides, if everything just had a "right" answer we'd all do that and agree without any more talk :p.

---

### Post by Adamant1988 on 2007-06-30
> **needtolookatascreenshot said:**
> Oh, so you just wanted to spread lies and disinformation and start a flamewar?

Well done.

Actually I wanted to present an article and get thoughts on it.  Thanks for the completely unscheduled and unnecessary attack on my character. :) 

If I wanted to spread lies, FUD, and disinformation, I would post a thread about how Microsoft is trying to destroy Linux using patents.

> Well ok >.>. Your the one that started it after all :p

I know, and I'll put in a post, I've just been busy.  I have a job (now), a girlfriend, and an overly active family... it's starting to seriously cut into the amount of time I have to hold arguments with people over the internet.

---

### Post by starcraft.man on 2007-06-30
> **Adamant1988 said:**
> 
I know, and I'll put in a post, I've just been busy.  I have a job (now), a girlfriend, and an overly active family... it's starting to seriously cut into the amount of time I have to hold arguments with people over the internet.

Awwww, well I only have 1 out 3 there (active needing family) and I'm a happy bachelor so I guess its only 1 out of 2 for me (since I'm not looking). No worries, whenever you get a chance your most argumentativeness :p.

Besides, I wouldn't label them arguments, "discussions to get to a better understanding of the world" is a better name for it. Discourse, when done in a civil way, is a very worthy pursuit. Least I think so.

---

### Post by needtolookatascreenshot on 2007-06-30
> **Adamant1988 said:**
> Actually I wanted to present an article and get thoughts on it.  Thanks for the completely unscheduled and unnecessary attack on my character. :) 


Hm, let's look at the facts, shall we?

You post an article that is full of lies and misinformation about the GPL3, declare that the article reflects your opinion on the GPL3, top it of with an inflammatory headline taken from the article, only to not participate in the ensuing discussion.

Well, spreading lies and trying to start a flamewar seems to be a very good description for what you are doing.

---

### Post by Adamant1988 on 2007-06-30
> **starcraft.man said:**
> Awwww, well I only have 1 out 3 there (active needing family) and I'm a happy bachelor so I guess its only 1 out of 2 for me. No worries, whenever you get a chance your most argumentativeness :p.

B**esides, I wouldn't label them arguments, "discussions to get to a better understanding of the world" is a better name for it. Discourse, when done in a civil way, is a very worthy pursuit. Least I think so**.

I couldn't agree more.

Well, I'll first argue that "Free as in 'do as I say" is precisely how the GPL operates.  But the GPL's goal is anti-corporate and that's the truth.  Anyone I've ever talked to about the GPL believes it's pupose is to create a direct relationship between the developer and the user, and eliminate the middle-man (corporations).  So, even on it's basic purpose I disagree with the GPL.  

Now, my issue with the GPL is that it is a political weapon, and that it is subject to change at the whim of the FSF.  Yes they allow 'open-discussion' before the license is put into action, but frankly open-discussion (to me) means "You can say what you want, and maybe we'll even listen to you... maybe".  Any time companies start doing something to irritate the FSF the GPL will be used as a weapon to stop them.  We're all going to have to play by freedom according to the FSF's rules, in their world, and that's a world without software corporations. 

Now, getting down to technicalities, the GPL prohibits a lot of activity on the part of corporations.  The GPL encourages adoption with it's highly friendly "Look how free I am, you can take my code and alter me and do what you wish with me!" punch-line.  GPL'd software is one of those things that is looked at as a "low-cost software that makes sense", after all, why bother re-writing everything when the GPL'd software is available right?  

This GPL's licensing stops the middle man from effectively delivering a product to users.  Case in point?  Ubuntu can't allow us to use ZFS in the Ubuntu kernel because the licenses are incompatible.  Canonical now can't deliver a better file-system because the GPL restricts them, this puts the hurt on the users who could have benefitted from the addition storage space. 

Now, a common response has been "it's the developers choice what license they use, and if you don't like it, don't use it" which is a great response and good logic, which is why I'm not using Linux anymore.  I won't have my operating system being subject the the FSF's idea of freedom.  There are a lot of developers on this forum who think it's great to be using Free software because they can do what they want with it, and that's absolutely right.. kind of.  You can do whatever the GPL says you can do.  Consumers (people who buy software, subscribe to software, etc.) and corporations (Novell, etc.) get pinched by the GPL.  Those groups

---

### Post by Adamant1988 on 2007-06-30
> **needtolookatascreenshot said:**
> Hm, let's look at the facts, shall we?

You post an article that is full of lies and misinformation about the GPL3, declare that the article reflects your opinion on the GPL3, top it of with an inflammatory headline taken from the article, only to not participate in the ensuing discussion.

Well, spreading lies and trying to start a flamewar seems to be a very good description for what you are doing.

You seem the be the one trying to start a flamewar with me.  Well, if you wish: 

"Omg, you're so rude, did your father ever hug you as a child?"

---

### Post by needtolookatascreenshot on 2007-06-30
> **Adamant1988 said:**
> You seem the be the one trying to start a flamewar with me. 

Not at all. I just want you to confront the issues.
Why post an article full of lies?
Why say that you agree with it?

Now, unfortunately, you seem to be more comfortable trying to provoke me than trying to confront these issues.

---

### Post by Ireclan on 2007-06-30
needtolookatascreenshot, why are you so hostile? So what if he agrees with the article? And just where do you get off saying that the article is "full of lies"? The article is an OPINION piece. Opinions are very grey, and whether they are "lies" or not is often subjective. Please try to keep this in mind. And even if the article WAS full of UTTER NONSENSICAL DRIVEL, it still doesn't mean that the man doesn't have a right to express his own opinion. He's already stated why he couldn't participate in the discussion before hand, and the excuse he gives, which basically boils down to "real life is more important than the Internet" is a VERY valid excuse. Please stop flaming Adamant1988.

PS- Out of curiosity, Adamant1988, why are you still on these forums if you don't use Linux anymore? Made too many good friends?

---

### Post by needtolookatascreenshot on 2007-06-30
> **Ireclan said:**
> needtolookatascreenshot, why are you so hostile? So what if he agrees with the article? And just where do you get off saying that the article is "full of lies"?

Well, it's full of lies because it's full of lies. ;)
Just look at the part about the patent requirements in the GPL3. They are simply wrong, untrue. 
Simply reading the license and taking an honest effort to understand it should have convinced the author that what he is writing is untrue. 

And if that hadn't sufficed, doing 5 minutes of research about should have done the trick. I mean, it's not as if the FSF and others involved weren't trying to explain the issues.

And in the process of researching the author might have discovered that companies like IBM were part of the discussions and signed of on these provisions. You know, IBM, the company with the most software patents of them all. If anything, this should have convinced the author that he was wrong.

But the author didn't do this, he simply posts things that are untrue and proceeds to slam the GPL3 from there.

Now, for me, that doesn't look like a simple mistake, that looks like deliberate lying.

> **Ireclan said:**
> 
The article is an OPINION piece. Opinions are very grey, and whether they are "lies" or not is often subjective. 

See above. The problem are not the authors opinions, but that he bases them on lies. You know, either the GPL3 actually says what he claims, or it doesn't. That's not a matter of opinion.

> **Ireclan said:**
> 
He's already stated why he couldn't participate in the discussion before hand, and the excuse he gives, which basically boils down to "real life is more important than the Internet" is a VERY valid excuse. 
Oh, it is. But then you shouldn't start topics like these, should you? You know, there's a word for posting controversial topics on a forum, starting a flamewar, spreading lies and then sitting back and enjoying the mess.

---

### Post by Celegorm on 2007-06-30
> **Adamant1988 said:**
> Well, I'll first argue that "Free as in 'do as I say" is precisely how the GPL operates. But the GPL's goal is anti-corporate and that's the truth. Anyone I've ever talked to about the GPL believes it's pupose is to create a direct relationship between the developer and the user, and eliminate the middle-man (corporations). So, even on it's basic purpose I disagree with the GPL.
The FSF defines 4 fundamental software freedoms: the freedom to use the software as you wish, the freedom to modify the software, the freedom to redistribute the software, and the freedom to distribute modifications to it. That definition has in no way changed between versions of the license, nor has the goal of creating a software license which protects these freedoms in practice as well as principle. Corporate software is, to an extent, incompatible with these freedoms because of the way most corporations try to make money from software.

> 
Now, a common response has been "it's the developers choice what license they use, and if you don't like it, don't use it" which is a great response and good logic, which is why I'm not using Linux anymore.  I won't have my operating system being subject the the FSF's idea of freedom.  There are a lot of developers on this forum who think it's great to be using Free software because they can do what they want with it, and that's absolutely right.. kind of.  You can do whatever the GPL says you can do.  Consumers (people who buy software, subscribe to software, etc.) and corporations (Novell, etc.) get pinched by the GPL.  Those groups

Isn't it the right of the person who wrote the software to decide under what license or conditions he will distribute it? You say corporations are being hurt by restrictions on how they can use GPL'd software. Are consumers not hurt by their inability to modify proprietary software which they buy? It's not like the FSF can force the FOSS community to do their bidding. If they make a truly horrible version of the GPL, that many people object to for well substantiated reasons, they're not going to use it, and will surely even find ways to work around using software that is licensed under such a version of the GPL.

I really fail to see anything in the GPL v3 that is inherently more restrictive than in v2. It seeks to guarantee specific software freedoms to anyone who gets GPL'd code, though it's worded a bit differently from v2, and with a few extra clauses covering circumstances which were unforeseen when v2 was written. The GPL has not always been used for the purpose for which it was intended- preserving software freedoms -and I think that is where the largest number of people are upset over the new version (for instance when Linus Torvalds decided to use v2 because he saw it as a "tit for tat" license).

---

### Post by needtolookatascreenshot on 2007-06-30
> **Adamant1988 said:**
> 
Well, I'll first argue that "Free as in 'do as I say" is precisely how the GPL operates.  But the GPL's goal is anti-corporate and that's the truth.  Anyone I've ever talked to about the GPL believes it's pupose is to create a direct relationship between the developer and the user, and eliminate the middle-man (corporations).  So, even on it's basic purpose I disagree with the GPL.  


Who gave you this idea? Are you aware that companies like IBM, HP and SUN use the GPL? Are you aware that the FSF is even working with them and worked with them on the GPL3?

---

### Post by Tundro Walker on 2007-06-30
> **needtolookatascreenshot said:**
> Hm, let's look at the facts, shall we?

You post an article that is full of lies and misinformation about the GPL3, declare that the article reflects your opinion on the GPL3, top it of with an inflammatory headline taken from the article, only to not participate in the ensuing discussion.

Well, spreading lies and trying to start a flamewar seems to be a very good description for what you are doing.

(whispers to Adamant) ...tell them you were playing "Devil's Advocate" and were just "testing" how people would respond...if that fails, tell them you use the "Chewbacca Defense", and that denies all accountability for your state-of-mind at the time...

---

### Post by macogw on 2007-06-30
> **thegnome87 said:**
> Yeah I think this might create more of a civil war-ish ecosystem than the Microsoft deals, though I mustn't forget it's closely related to it.



Isn't this what the GPL 2 is about?  You can copy and use the original source code/"design" and build upon it provided you keep it open and allow others to do the same to your modified source code?

The issue here is about patents, I know, but (correct me if I'm wrong) you aren't actually **giving away** rights to your design since the modifier can have his modified version copied/modified by you or someone else as well.


This article gave me a headache (the confusion, not disagreement with it)

Can anyone explain, (pardoning my ignorance and ADD-ish lack of ability to absorb big article rants into concise points), in bullet points what changes is the GPL 3 making to the GPL 2?  The main jist I get is that it seems to place serious complications/restrictions on the inclusion of closed source software (codecs, legal DVD decoders) in OSS.
Pretty sure it bans Tivo's little "we'll use Linux but put a checksum so that if you DO use your GPL-granted rights to the software, the hardware will just reject it" since that gets rid of your right to modify it as you see fit.

---

### Post by deanlinkous on 2007-06-30
> **Adamant1988 said:**
> 

Well, I'll first argue that "Free as in 'do as I say" is precisely how the GPL operates.  But the GPL's goal is anti-corporate and that's the truth.  Anyone I've ever talked to about the GPL believes it's pupose is to create a direct relationship between the developer and the user, and eliminate the middle-man (corporations).  So, even on it's basic purpose I disagree with the GPL.  Actually, the first license that linux was under was anti-corporate not the GPL. You've talked to me about the GPL and I do not believe its purpose is to create a direct relationship.....what is that anyway??? 
> 
Now, my issue with the GPL is that it is a political weapon, and that it is subject to change at the whim of the FSF.
What *whim* has changed? What is a political weapon anyway???? Sure the FSF has a agenda but it isn't hidden, it isn't harmful, it isn't changing - whats so bad about software freedoms? That is what it has always been about. There is very little difference of intent between v2 and v3. The part that is different is that v3 is well-defined because there are well defined threats in this day and age whereas before was a different era as far as technology and software. 

> Yes they allow 'open-discussion' before the license is put into action, but frankly open-discussion (to me) means "You can say what you want, and maybe we'll even listen to you... maybe".  You can see the changes that have been made. No one can doubt the changes that have been made. 

I was going to respond more but I dont see the point......

Because ZFS cant go into Ubuntu....the GPL is to blame..... yea okay....

---

### Post by jiminycricket on 2007-06-30
> **thegnome87 said:**
> Yeah I think this might create more of a civil war-ish ecosystem than the Microsoft deals, though I mustn't forget it's closely related to it.



Isn't this what the GPL 2 is about?  You can copy and use the original source code/"design" and build upon it provided you keep it open and allow others to do the same to your modified source code?

The issue here is about patents, I know, but (correct me if I'm wrong) you aren't actually **giving away** rights to your design since the modifier can have his modified version copied/modified by you or someone else as well.


This article gave me a headache (the confusion, not disagreement with it)

Can anyone explain, (pardoning my ignorance and ADD-ish lack of ability to absorb big article rants into concise points), in bullet points what changes is the GPL 3 making to the GPL 2?  The main jist I get is that it seems to place serious complications/restrictions on the inclusion of closed source software (codecs, legal DVD decoders) in OSS.

No, GPLv3 doesn't restrict inclusion of codecs.  Kevin Carmony's Linspire Letter on that topic was a lie.

The patent grant on the GPL'd code someone distributes is necessary in this litigious world so that someone who distributes GPL'd software can't sue you for distributing it.

Changes in GPLv3:
--better language to increase enforcability, clearer separation of what's a derivative work
--internationalization
--explicit patent grant
--explicit Tivioisation fix for "USER PRODUCTS" only, so that medical devices etc. don't have this obligation
--WIPO/DMCA anti-circumvention rights to sue waived (which is good since the DMCA makes anti-circumvention charges CRIMINAL, trumped up charges and sentencing)
--makes Peer 2 Peer, eg., Bittorrent, transmission of GPL'd software not violate the GPL anymore as long as you say where the source is
--compatibility with Apache Software License
--reduces complexity
-- idea of "exceptions" in Section 7
--bans exclusionary patent licenses like the MS-Novell deal (except exclusionary deals prior to March 28 2007 are grandfathered in)
--any patents are (sub)licensed to distributors
--compatibility with Affero GPL (which enforces codesharing for people who modify AGPL'd software and run it on the public Internet)
--Section 8: softer termination of unintentional GPL violations, if you cure the violations within 60 days it's reinstated; if you cure the first violation in 30 days, it's reinstated

---

### Post by nrs on 2007-06-30
The majority of people that seem to be complaining are the ones that never really cared for the GPL in the first place (generalization) and tried to find ways to circumvent it They may be losing the freedom to screw me, but as it stands I feel my freedoms 0 - 3 have only been enhanced with v3.

---

### Post by koenn on 2007-06-30
I know you're not afaid to take a controversial view and defend not so popular positions, and I respect that. In this case, however, your arguments lack substance - or I'm missing something. 

> **Adamant1988 said:**
> Well, I'll first argue that "Free as in 'do as I say" is precisely how the GPL operates.  . Free as in "allow others the enjoy the same freedom(s) as the one(s) you enjoyed when you obtained this pîece of GPL'd software", that is. 

> **Adamant1988 said:**
> 
But the GPL's goal is anti-corporate and that's the truth.  ...  [it aims ]to create a direct relationship between the developer and the user, and eliminate the middle-man (corporations).
 Please explain how the right to **re-distribute** eliminates the middle-man / a software distributor.

> **Adamant1988 said:**
> 
Now, a common response has been "it's the developers choice what license they use, and if you don't like it, don't use it"  [...] There are a lot of developers on this forum who think it's great to be using Free software because they can do what they want with it, and that's absolutely right.. kind of.  You can do whatever the GPL says you can do.  Consumers (people who buy software, subscribe to software, etc.) and corporations (Novell, etc.) get pinched by the GPL
Yes, it's great for developers, bot on the publishing and on the receiving side, (and IT students, and people interested in how things work, ...), so it serves its purpose. 

By the way, the GPL grants you the right to use GPL'd sofware whether you agree with the license or not. So you can continue to use Linux etc. 
The "if you don't like it, don't use it" is for those who want to build on existing GPL'd software to create a proprietary product - basically denying the original author to see how his work has been modified / improved / ... I can imagine that a programmer would be interested in seeing how his code evolves.

---

### Post by deanlinkous on 2007-06-30
> **nrs said:**
> They may be losing the freedom to screw me, but as it stands I feel my freedoms 0 - 3 have only been enhanced with v3.
excellent....
sounds like my new signature... :D

---

### Post by Andrewie on 2007-06-30
I'm a little confused regrading the whole Tivo thing. Why should I be able to change the operating system on a tivo. They have the source fully available which is what they need, why do I need that "freedom"? 

This sounds like a flame but its a real question.

---

### Post by DoctorMO on 2007-06-30
I'm a programmer; my code will be GPLv3... After all it's _my_ code and the busy body businesses in the world from Novell, Microsoft to damn well orical can either _pay_ me for a license so they can use the software abusivly or they can abide by the damn terms.

No one forced these businesses to make buckets of money off other peoples work. and I think it's about time people started paying respect to the programmers and creators and after all the copyright owners of this whole eco-system.

We're not out to hurt people, or restrict people for the most part. we'd rather trust our users and distributors. but sometimes you can't do that and the company that has taken your work to save them selves a whole bank vault of money is now complaining because the rights you wanted maintained have a new license to help them.

Bah, let them make their own operating system and software tools where they need to distribute.

Reminder: the license doesn't apply to users, only to distributors.

---

### Post by psyopper on 2007-06-30
> **Andrewie said:**
> I'm a little confused regrading the whole Tivo thing. Why should I be able to change the operating system on a tivo. They have the source fully available which is what they need, why do I need that "freedom"? 

This sounds like a flame but its a real question.

The irony is that I wrote an opinion piece (a newb-ish one for sure) about GPLv3 and Tivoization. I finished it up this morning and then look what I find in the ubuntuforums...

It may answer a touch about tivoization for you...

[Copper Scroll post on GPLv3 and Tivoization]("http://psyopper.wordpress.com/?page_id=74").

It's kind of long so maybe we should be glad I didn't post it here instead. Please feel free to point out where I may have gone wrong, factually and opinionatically.

---

### Post by Andrewie on 2007-06-30
> **psyopper said:**
> The irony is that I wrote an opinion piece (a newb-ish one for sure) about GPLv3 and Tivoization. I finished it up this morning and then look what I find in the ubuntuforums...

It may answer a touch about tivoization for you...

[Copper Scroll post on GPLv3 and Tivoization]("http://psyopper.wordpress.com/?page_id=74").

It's kind of long so maybe we should be glad I didn't post it here instead. Please feel free to point out where I may have gone wrong, factually and opinionatically.

thanks, lol what are the chances...

---

### Post by Andrewie on 2007-06-30
its see if my luck is still working, I have another question.If the FSF converts all there tools into GPLv3 can the kernel still be compiled.

ok now this is my opinion: 

[http://www.fsf.org/iphone-gplv3](http://www.fsf.org/iphone-gplv3) I'm not sure what this article means but I think the free software foundation is over doing it a little. They are picking a choosing which companies get to use GPL software.

---

### Post by reyfer on 2007-06-30
> **Andrewie said:**
> its see if my luck is still working, I have another question.If the FSF converts all there tools into GPLv3 can the kernel still be compiled.

ok now this is my opinion: 

[http://www.fsf.org/iphone-gplv3](http://www.fsf.org/iphone-gplv3) I'm not sure what this article means but I think the free software foundation is over doing it a little. They are picking a choosing which companies get to use GPL software.

If you don't know what the article means, how can you say they are overdoing it?

The article just says that GPL v3 stands in the way of products that restrict the rights of users to review and modify the software as the iPhone does. The FSF doesn't choose who uses the GPL. Developers choose which license their work will be under. An if their product uses software released under GPL v3, then they can't put restrictions not present on that license. All the article hints is that there's suspicion that some of the iPhone software use GPL'd tools, that's all.

---

### Post by koenn on 2007-06-30
re. the iphone: "it will be interesting to see to what extent the iPhone uses GPLed software." - from the article you refer to. 

> **Andrewie said:**
>  I think the free software foundation is over doing it a little. They are picking a choosing which companies get to use GPL software.No, the companies choose wheter or not they will use software covered by the GPL

> **Andrewie said:**
> I have another question.If the FSF converts all there tools into GPLv3 can the kernel still be compiled.
in- and output to a program is not subject to the license so i'd say you can compile whatever you want and license it the way you want to. However, if during the compilation GPL'd work is added to the output (eg linking to libraries), the license on those libraries may apply. That's my understanding, but I don't know much about how compilers actually work so it could be more complex than that.

---

### Post by deanlinkous on 2007-06-30
> **Andrewie said:**
> I'm a little confused regrading the whole Tivo thing. Why should I be able to change the operating system on a tivo. They have the source fully available which is what they need, why do I need that "freedom"? 

This sounds like a flame but its a real question.

I'm a little confused regrading the whole computer thing. Why should I be able to change the operating system on a computer. They have the source fully available which is what they need, why do I need that "freedom"? 

This sounds like a flame but its a real question.

---

### Post by thisllub on 2007-06-30
> **@trophy said:**
> 

Also, you *can* prevent cheating with open source software.  It requires designing the game in a secure fashion, though.  The server is god as far as the game is concerned.  Don't trust client machines at all.  Closed or open source, that's the only way to write a secure client-server system.  Anybody who says otherwise is either lying or has their head in the sand.  For an interesting essay about this very subject, check out [The Case of the Quake Cheats](http://www.catb.org/esr/writings/quake-cheats.html) by Eric S Raymond.
.

A problem can have practical rather than absolute solutions.

In that example one solution might be for most of the information to be available to the client but a small critical piece may be missing.
Consider a phone number. You could conceivably find someone by dialing all  possible numbers however it is practically impossible. Getting the correct number makes contact simple. 

I think the critical issue with the licence is the utility of open source in a commercial market. Open source can give a developer a significant advantage in preparing a product for a client. If insufficient commercial reward can be obtained from that product business software will abandon any licence that risks that commercial return.
Products such as lamp would be abandoned in fear of a loss of reasonable return for IP.

---

### Post by Andrewie on 2007-06-30
> 
One major danger that GPLv3 will block is **tivoization**. **Tivoization** means computers (called “appliances”) contain GPL-covered software that you can’t change, because the appliance shuts down if it detects modified software. The usual motive for **tivoization** is that the software has features the manufacturer thinks lots of people won’t like. The manufacturers of these computers take advantage of the freedom that free software provides, but they don’t let you do likewise.
Some argue that competition between appliances in a free market should suffice to keep nasty features to a low level. Perhaps competition alone would avoid arbitrary, pointless misfeatures like “Must shut down between 1pm and 5pm every Tuesday”, but even so, a choice of masters isn’t freedom. Freedom means you control what your software does, not merely that you can beg or threaten someone else who decides for you. 

They are righting names of companies right into the GPLv3 and saying "you can't use it anymore". I'm not sure how correct psyopper article is but by the looks of this tivo had to do this to prevent themselves from getting sued it wasn't an "evil" act.

---

### Post by starcraft.man on 2007-06-30
Well, seems I'm a bit late to weigh in on your arguments and unfortunately it seems your somewhat alone but I will try to answer these in blue, and if I can, I will even raise counter points in red (form of bullets, I haven't time to play all sides :p) for others to ponder and take apart. I have no issue playing devil's advocate, even if my opinion is still set.

> **Adamant1988 said:**
> I couldn't agree more.

Well, I'll first argue that "Free as in 'do as I say" is precisely how the GPL operates.  But the GPL's goal is anti-corporate and that's the truth.  Anyone I've ever talked to about the GPL believes it's pupose is to create a direct relationship between the developer and the user, and eliminate the middle-man (corporations).  So, even on it's basic purpose I disagree with the GPL.

[COLOR="Blue"]Maybe it's time for the corporations (software) to be done away with? As I see it, corporations came about because in times long since past information was sectored and separated and stored so that only a few could learn it. People needed very special skills and learned them and then went to work for a company. The internet has eliminated this requirement, it is the greatest means of communication and interconnectedness ever conceived. Not only can it be a single unified repository for information from science to programming to philosophy, it can connect developers and their users directly. It, in its creation has singularly rendered corporations (at least for programming, the internet cannot produce hardware) moot. Maybe software companies are in denial, I mean the OS is even becoming increasingly irrelevant with the web browser taking its place. In the end though, the question to answer is who better to know what the users want then the users, and if they can interact directly with their developers is that not likely to lead to the best product? It eliminates all bureaucracy liked the layers and layers at MS (which, IMO, have made the company ineffective) [/COLOR]  

[COLOR="Red"]Corporations cannot as yet be replaced entirely in the realm of hardware, it still needs to be produced.
As such, perhaps hardware and software corporations are tied too close to be separated in some ways (Apple has blurred the lines incredible controlling all sectors).[/COLOR]

Now, my issue with the GPL is that it is a political weapon, and that it is subject to change at the whim of the FSF.  Yes they allow 'open-discussion' before the license is put into action, but frankly open-discussion (to me) means "You can say what you want, and maybe we'll even listen to you... maybe".  Any time companies start doing something to irritate the FSF the GPL will be used as a weapon to stop them.  We're all going to have to play by freedom according to the FSF's rules, in their world, and that's a world without software corporations. 
[COLOR="Blue"]
Ok, lets say I and you don't trust the FSF. Who then should be the protector of the GPL (or creator of a newer license)? Should we entrust it to a corporation, who may or may not be subject to its rules? To a government? Should we absolve all bodies from its oversight and release it to the public for management, how then would we ensure regulated changes? Attacking the FSF is nice, but without a feasible and sustainable replacement (unless your suggestion the BSD anarchist license?) it doesn't do much. 

I don't agree with the end though, nobody has to play by the FSF's GPL license. BSD for instance to my knowledge, has almost no GPL code in it, and even then it can be clearly separated and removed if the license poses a problem. In addition, you should be only too happy if the FSF ignores its users requests (in the creation of GPL 3 for instance) then none of its users base will be happy with the product, and no one will use it, thusly staying with 2. What if
[/COLOR]
Now, getting down to technicalities, the GPL prohibits a lot of activity on the part of corporations.  The GPL encourages adoption with it's highly friendly "Look how free I am, you can take my code and alter me and do what you wish with me!" punch-line.  GPL'd software is one of those things that is looked at as a "low-cost software that makes sense", after all, why bother re-writing everything when the GPL'd software is available right?  

[COLOR="Blue"]This is true. If a free solution to allow a company to get to a means exists, why code it again? Apple though made its foundation on BSD no? So its not as if the GPL is essential to continue developing software. In fact, since companies are part of the free market, if GPL becomes inaccessible to large companies wouldn't they then fill the void with their own replacement per the system. Band together and code their own? Just a thought.[/COLOR]

This GPL's licensing stops the middle man from effectively delivering a product to users.  Case in point?  Ubuntu can't allow us to use ZFS in the Ubuntu kernel because the licenses are incompatible.  Canonical now can't deliver a better file-system because the GPL restricts them, this puts the hurt on the users who could have benefitted from the addition storage space. 

[COLOR="Blue"]Not the best example, Sun is after all considering GPLv3 from what has been blogged by Sun. This however I believe like I mentioned above may be a moot point. Perhaps the future is to have no corporations controlling software. Do remember there was a time when craftsman made all things. They were replaced in the industrial revolution much to their dismay, and eventually phased out entirely. Perhaps we have come to another turning point? As for ZFS while your right it seems promising, Linux will survive without it, as it has for a time.[/COLOR]

Now, a common response has been "it's the developers choice what license they use, and if you don't like it, don't use it" which is a great response and good logic, which is why I'm not using Linux anymore.  I won't have my operating system being subject the the FSF's idea of freedom.  There are a lot of developers on this forum who think it's great to be using Free software because they can do what they want with it, and that's absolutely right.. kind of.  You can do whatever the GPL says you can do.  Consumers (people who buy software, subscribe to software, etc.) and corporations (Novell, etc.) get pinched by the GPL.  Those groups

[COLOR="Blue"]Well, that is your choice and of course Linux/Ubuntu wishes you all the best with your endeavour, making no effort to stop you from changing. Your using a Mac then (I believe you spoke of that)? So you've traded the tyrannical rule of the FSF over the freedoms your granted, for the draconian lock in of Apple, both in hardware and software? Pardon, if I don't find that to be a huge improvement.

One thing of I am confused on, how does the GPL hurt the consumer (you mention them getting pinched by GPL)? Doesn't the GPL guarantee them greater freedoms then say a proprietary license? Take the Visual Studio incident with MS for example. One of their own MVPs coded a product to improve it significantly and because words in MS license prevent (according to MS) him from enabling it in the free version, they are taking action against him. How is that better protection for the consumer than GPL software?

I do agree, corporations get pinched by the new GPL, but like I raised above perhaps thats time for them to make their own solution. Let them create a project for them to use, make their own license and make it so only they can use it, then distribute and license it amongst themselves. That seems to me to be the solution, and if they can't "bite that bullet" then they should find some way to use whatever is at their disposal. That's how the free market works, you use what you have and if you lose something you find something else to use. [/COLOR]

That is my rebuttal, sorry I kind of stopped the counter points. Was taking long enough writing all the answers. I am curious what your using now, and if you could clarify in what way it makes you happier/enables you to do more with your software than the GPL? Oh and I hope I didn't repeat to much of what others wrote in response, I just glanced at them.

---

### Post by jiminycricket on 2007-06-30
> **Andrewie said:**
> They are righting names of companies right into the GPLv3 and saying "you can't use it anymore". I'm not sure how correct psyopper article is but by the looks of this tivo had to do this to prevent themselves from getting sued it wasn't an "evil" act.

I don't see the word Tivo anywhere in the GPLv3.  Tivo's free to use GPLv3 code if they abide by it.

If Free Software is made proprietary, that can be a fate "worse than death" as RMS would say.

---

### Post by Adamant1988 on 2007-06-30
> **Ireclan said:**
> needtolookatascreenshot, why are you so hostile? So what if he agrees with the article? And just where do you get off saying that the article is "full of lies"? The article is an OPINION piece. Opinions are very grey, and whether they are "lies" or not is often subjective. Please try to keep this in mind. And even if the article WAS full of UTTER NONSENSICAL DRIVEL, it still doesn't mean that the man doesn't have a right to express his own opinion. He's already stated why he couldn't participate in the discussion before hand, and the excuse he gives, which basically boils down to "real life is more important than the Internet" is a VERY valid excuse. Please stop flaming Adamant1988.

**PS- Out of curiosity, Adamant1988, why are you still on these forums if you don't use Linux anymore? Made too many good friends?**

I happen to enjoy the community.  The community isn't limited to those who are users, I would like to think.

---

### Post by Andrewie on 2007-06-30
> **Adamant1988 said:**
> I happen to enjoy the community.  The community isn't limited to those who are users, I would like to think.

if you aren't running Linux or ubuntu what o.s. are you running?

---

### Post by starcraft.man on 2007-06-30
> **Adamant1988 said:**
> I happen to enjoy the community.  The community isn't limited to those who are users, I would like to think.

Nothing wrong with that. I need someone to have good long winded discussions with, else how would I exercise my two most important muscles, brain and fingers? :p

> **Andrewie said:**
> if you aren't running Linux or ubuntu what o.s. are you running?

Already beat ya to asking that. Still haven't gotten an answer, I wanted to know a bit more too... if ya don't mind sharing.

---

### Post by deanlinkous on 2007-06-30
GPLv3 marks linux decline....once sun licenses their kernel using the gplv3! :)

Actually I am thinking of going ahead and switching to a bsd kernel while I am waiting for the sun to come out....tommorrow....bet ya bottom dollar.....

---

### Post by Andrewie on 2007-06-30
> **deanlinkous said:**
> GPLv3 marks linux decline....once sun licenses their kernel using the gplv3! :)

Actually I am thinking of going ahead and switching to a bsd kernel while I am waiting for the sun to come out....tommorrow....bet ya bottom dollar.....

The sun'll come out
Tomorrow
Bet your bottom dollar
That tomorrow
There'll be sun!

Just thinkin' about
Tomorrow
Clears away the cobwebs,
And the sorrow
'Til there's none!

When I'm stuck a day
That's gray,
And lonely,
I just stick out my chin
And Grin,
And Say,
Oh!

The sun'll come out
Tomorrow
So ya gotta hang on
'Til tomorrow
Come what may
Tomorrow! Tomorrow!
I love ya Tomorrow!
You're always
A day
A way!

I tried bsd but I got kernel panics, I guess it didn't like something in my laptop, but around the time I tired Linux was also giving me trouble so maybe its better now.

---

### Post by Adamant1988 on 2007-07-01
> **starcraft.man said:**
> Well, seems I'm a bit late to weigh in on your arguments and unfortunately it seems your somewhat alone but I will try to answer these in blue, and if I can, I will even raise counter points in red (form of bullets, I haven't time to play all sides :p) for others to ponder and take apart. I have no issue playing devil's advocate, even if my opinion is still set.



That is my rebuttal, sorry I kind of stopped the counter points. Was taking long enough writing all the answers. I am curious what your using now, and if you could clarify in what way it makes you happier/enables you to do more with your software than the GPL? Oh and I hope I didn't repeat to much of what others wrote in response, I just glanced at them.

I am actually on my Windows laptop (as you may have noticed in my screenshot in the GPL v3 thread where I showed my Gmail account).  Soon I'll be on a Mac though, I figure.  As for what I gain, I think it's important to understand my position as a user on this matter.  Firstly, I am not a coder, I am not a developer, and I do not like to hack software.   This so called 'freedom' that the FSF offers doesn't apply to me,  I gain nothing from it, other than that most of the software under the GPL is completely free of cost.  

You asked me what I would rather do instead of the GPL, I think that 'open source' is a good development philosophy in general, but I don't agree with free software.  Firstly, I consider code to be a human readable text, so in a way, it's literature.  I believe that everyone should have every right to read any code they want to, to study it, to understand it, to learn from it.  I don't believe that every single person on the planet should be able to edit that code, or use it, any more than I feel that every single person in the world has every right to edit a book and redistribute that.   My ideal software license would reflect that.  

The FSF cannot be trusted anymore than we can trust any organization with a political agenda.  If you firmly believe in what the FSF is saying then you should absolutely support the GPL. 

Now, you asked me how the GPL hurts me as a consumer, that's a complex question.  It hurts me as a consumer because, a lot of normal business activity that benefits me as a user can't be done.  GPL-software distributors have very limited ability to behave as real businesses and make deals to offer products as such.  The law of the GPL is absolute, when you place your software under a GPL license it's only really yours to a certain extent.  It's my understanding that changing your software to a different license after you've GPL'd it is difficult, without re-writing new code from scratch, but I may be wrong on that.   In the end, the GPL blocks activity that would allow me to get a better product... be that in the form of patent/interoperability deals, or be that in the form of 'tivo-ization'.  As recent examples. 


I also completely disagree that corporations are made moot by the internet, they're still very needed and if you were to rid the world of every single corporation in existence right now, they would come back (maybe a bit differently).  Corporations are important in getting products to the user, and I think that software IS a product.

---

### Post by needtolookatascreenshot on 2007-07-01
> **Adamant1988 said:**
> 
The law of the GPL is absolute, when you place your software under a GPL license it's only really yours to a certain extent.  It's my understanding that changing your software to a different license after you've GPL'd it is difficult, without re-writing new code from scratch, but I may be wrong on that.  

You are wrong. The author can of course do with his work whatever he wants, including relicense it under any license he wants. 

> **Adamant1988 said:**
> 
In the end, the GPL blocks activity that would allow me to get a better product... be that in the form of patent/interoperability deals, or be that in the form of 'tivo-ization'.  As recent examples. 
No, it doesn't. It just gives authors of software the ability to restrict these kind of things, if and only if they don't want these things to happen with their code. And for example patent deals are still possible, but only in a form that the intend of the original authors is honored. 

> **Adamant1988 said:**
> 
I also completely disagree that corporations are made moot by the internet, they're still very needed and if you were to rid the world of every single corporation in existence right now, they would come back (maybe a bit differently).  Corporations are important in getting products to the user, and I think that software IS a product.
But then again, you still failed to show in any shape or form how the GPL is anti-corporations. I can only say it again, there are large corporations using the GPL.

---

### Post by koenn on 2007-07-01
> **Adamant1988 said:**
> ...   Firstly, I consider code to be a human readable text, so in a way, it's literature.  I believe that everyone should have every right to read any code they want to, to study it, to understand it, to learn from it.  I don't believe that every single person on the planet should be able to edit that code, or use it, any more than I feel that every single person in the world has every right to edit a book and redistribute that.   My ideal software license would reflect that. 
Ah, but software is never finished. Liturature doesn't require debugging. 
If, while you're reading and studying source code for a given program, you come across a paragraph where you think - hey, I see what the programmer's trying to do here, but I would have done it differently. Shouldn't you be allowed to see if your way works ? and if it actually improves the program, shouldn't you be able to publish the improved version ? And shouldn't the original author have the right to in turn read and study your  improvements, learn from it, and modify them again if he sees ways to improve it even more ? Isn't that how both open source and free software development works ? And doesn't GPLprovide the legal framework to ensure this is possible ?

---

### Post by Erunno on 2007-07-01
> **needtolookatascreenshot said:**
> You are wrong. The author can of course do with his work whatever he wants, including relicense it under any license he wants. 

Well, the license can be changed for newer versions by the copyright holder but the code that has been released under the GPL cannot be relicensed anymore (hint: Jörg Schilli).

---

### Post by needtolookatascreenshot on 2007-07-01
> **Erunno said:**
> Well, the license can be changed for newer versions by the copyright holder but the code that has been released under the GPL cannot be relicensed anymore (hint: Jörg Schilli).
Well, you can of course relicense it, however, you can't suddenly revoke the GPL for something you already distributed under the GPL. 

However, this is true for any license or contract for this matter.
If I, for example, sell you a software under a certain license that gives you the right to use the software after paying me a certain amount of money, I can't suddenly demand more money after the fact, can I?

---

### Post by az on 2007-07-01
> **Adamant1988 said:**
> I couldn't agree more.

In an effort to control trolling, I would suggest that all the threads you have made on the topic in the past few days be merged.  You seem to say the same things over and over in these threads.  

> **Adamant1988 said:**
> 

This GPL's licensing stops the middle man from effectively delivering a product to users.  Case in point?  Ubuntu can't allow us to use ZFS in the Ubuntu kernel because the licenses are incompatible.  Canonical now can't deliver a better file-system because the GPL restricts them, this puts the hurt on the users who could have benefitted from the addition storage space. 


We discussed this last week.  Either you forgot or you are willfully spreading misinformation.

Ubuntu can surely ship ZFS, just like they can ship all the non-free parts in linux-restricted-modules.  You are just prohibited from shipping them as part of the kernel.

You can't take the upstream source and combine it with non-free software and then pass it on.  You can (of course!) run them and pass them on if they are kept separate.

---

### Post by Tomosaur on 2007-07-01
> **@trophy said:**
> LOL you had me up until this sentence.

And I know you didn't mean anything by it, but I hate this saying.  It's basically saying "Hey, the world is a crappy place where people will stab you in the back, but since I happen to be good at back stabbing, I'm going to exploit the system instead of endeavoring to change it even though I understand that its wrong."

You know, the kind of thing Microsoft might say.

I can see how you would have taken it like that, perhaps I should have chosen my words more wisely!

What I was actually trying to say, is that although the GPL may appear more and more restrictive as time goes on, it is simply a response to the behaviour of key players in the industry. In the past,we simply didn't HAVE things like DRM. They didn't exist (at least not in the form which GPL3 tries to combat), and so the old versions of the GPL couldn't possibly have been expected to include passages about such technology. Thus, it is wrong to blame and lament the FSF for extending the GPL so that modern technology is taken into account. It is not that the FSF has become more draconian, it's that the industry in general has expanded, and the GPL has needed to play catch up to ensure that the intent of past versions of the GPL remains relevant today. So when I said 'don't hate the player, hate the game', I was meaning to say that it's not the FSF's fault if the GPL is more restrictive (even though this in itself is debatable), but it's the nature of the software industry that new technology appears, new methods of restricting users appear, and it is only to be expected that the GPL needs to evolve to take these factors into account.

---

### Post by forrestcupp on 2007-07-01
> **starcraft.man said:**
> 
In the end, I see software patents more as patenting math (which has never been done to my knowledge). Math is free and open, all contributions by universities can be read and improved upon and fead back into the whole in an effort to further our understanding of the abstract art. This seems to me to be the closest I can make an analogy of software patents to. Imagine if you will, that someone patented the use of a square root. Sound ridiculous? Well, it seems to me thats no different than Amazon patenting one click buying or VMware patenting their snapshot technology (I believe they did from what I read) for VMs. These are obvious things that anyone in the business would want and develop separate or together, just like square roots are an obvious extension of mathematics (gradual evolution of the basics division and multiplication to the exponetial and roots).

No one's arguing about whether or not software patents are a good idea.  Of course software patents are stupid, and they shouldn't be allowed.  But that doesn't mean they don't exist.  Murdering is stupid and *isn't* allowed, but it still exists, and we lock our doors to protect ourselves from things like that happening.  There should be strict rules in the GPL against people taking out software patents.  But there should not be strict rules against people who want to lock their doors to protect their users from *other* unruly people.

> **argie said:**
> I understand little of what people complaining about GPL3 are complaining about. It's up to the author to choose the code. You want to use the code, work under his/her restrictions. As far as I can see, it's only the people who don't want to share who are having trouble. I haven't yet seen a single legitimate case against GPL3.
That's absolutely *not* always true.  What if I want to author some code and I want to share it with *everyone*?  Well, I can't release it under GPLv3 because it says I'm not allowed to share my code with companies like Novell.

This is the only problem I have with GPLv3.

---

### Post by PriceChild on 2007-07-01
The author to software owns all rights to it unless he gives it up to another for any reason.

If you license a piece of code under the GPL for example... that instance of code is licensed under the GPL forever. Any of that release of code used in future must also be GPL.

However... whoever owns all rights to code could relicense it... that includes the same code he did GPL, or anything he improved himself with code he owns the rights to. So an author could randomly license the same code under MIT and GPL... and users do whatever they want with them.

---

### Post by needtolookatascreenshot on 2007-07-01
> **forrestcupp said:**
>   But there should not be strict rules against people who want to lock their doors to protect their users from *other* unruly people.

But are there? Which rules are you refering to?

> **forrestcupp said:**
> 
That's absolutely *not* always true.  What if I want to author some code and I want to share it with *everyone*?  Well, I can't release it under GPLv3 because it says I'm not allowed to share my code with companies like Novell.

But of course you can.

---

### Post by Adamant1988 on 2007-07-01
> **needtolookatascreenshot said:**
> 
But then again, you still failed to show in any shape or form how the GPL is anti-corporations. I can only say it again, there are large corporations using the GPL.

Actually, take a good look at those companies offering GPL'd software... what do they have in common?  

right off the top of my head vendors include: 

Red Hat
Novell
IBM

IBM is a solutions company... not  a software company.  Red Hat is a support company, the fact that they offer software is moot, without offering the service they wouldn't exist today.  Novell, well, they're about the same as Red Hat although they offer other products with their distribution, but those are closed-source.

---

### Post by Adamant1988 on 2007-07-01
> **az said:**
> In an effort to control trolling, I would suggest that all the threads you have made on the topic in the past few days be merged.  You seem to say the same things over and over in these threads.  



We discussed this last week.  Either you forgot or you are willfully spreading misinformation.

**Ubuntu can surely ship ZFS, just like they can ship all the non-free parts in linux-restricted-modules.  You are just prohibited from shipping them as part of the kernel.**

You can't take the upstream source and combine it with non-free software and then pass it on.  You can (of course!) run them and pass them on if they are kept separate.

Correct me if I'm wrong but isn't ZFS (currently) being forced to live in user-space thanks to it's licensing?  if Ubuntu shipped with ZFS the legal way, ZFS would be in user-space and have severely reduced performance.  You can correct me if I'm wrong, I'm just saying I haven't heard a single person say it was alright to offer ZFS with the distro, other than you.

---

### Post by needtolookatascreenshot on 2007-07-01
> **Adamant1988 said:**
> Actually, take a good look at those companies offering GPL'd software... what do they have in common?  

right off the top of my head vendors include: 

Red Hat
Novell
IBM

IBM is a solutions company... not  a software company.  Red Hat is a support company, the fact that they offer software is moot, without offering the service they wouldn't exist today.  Novell, well, they're about the same as Red Hat although they offer other products with their distribution, but those are closed-source.

And your point is?
That the economic model to make money with free software is in many cases different from the models for making money with propietary software? So?
And how does that make free software in any way anti-corporate and how this supposed to fit into your model of eliminating the middle man? If anything, you just showed us the middle man becoming more important with free software.

---

### Post by Adamant1988 on 2007-07-01
> **needtolookatascreenshot said:**
> And your point is?
That the economic model to make money with free software is in many cases different from the models for making money with propietary software? So?
And how does that make free software in any way anti-corporate and how this supposed to fit into your model of eliminating the middle man? If anything, you just showed us the middle man becoming more important with free software.

The point is that they're NOT making money off the software.  The software became a vehicle to do something else.  Red Hat and Novell could drop their GPL'd software RIGHT NOW and still make money with very slight modifications to the system they're currently using.  In fact, maybe even more money than they're currently making.

No, the middle man isn't more important, you can go right around Red Hat and Novell and get the exact same software from the Fedora or openSuSE communities... the code is all over the place, the middle man is unable to turn the code into a product (practically speaking) under the GPL.   Even with these companies, there is no middle-man, not for the software.  

If you'd like to get services associated with the software, well, there you go.

---

### Post by BoyOfDestiny on 2007-07-01
> **forrestcupp said:**
> No one's arguing about whether or not software patents are a good idea.  Of course software patents are stupid, and they shouldn't be allowed.  But that doesn't mean they don't exist.  Murdering is stupid and *isn't* allowed, but it still exists, and we lock our doors to protect ourselves from things like that happening.  There should be strict rules in the GPL against people taking out software patents.  But there should not be strict rules against people who want to lock their doors to protect their users from *other* unruly people.


That's absolutely *not* always true.  What if I want to author some code and I want to share it with *everyone*?  Well, I can't release it under GPLv3 because it says I'm not allowed to share my code with companies like Novell.

This is the only problem I have with GPLv3.

If you want to author some code and share it with everyone, you can. You don't lose your copyright on it if you GPL it. If you want to contribute your code to a GPLv3 project you could. That same code (since you wrote it) could be given to the public domain, or put under a more permissive license i.e. BSD/MIT/etc.

Example of dual licensing
[http://www.mysql.com/company/legal/licensing/faq.html](http://www.mysql.com/company/legal/licensing/faq.html)
[http://trolltech.com/products/qt/licenses/licensing](http://trolltech.com/products/qt/licenses/licensing)

GPLv3 makes no changes to block this. And frankly I don't think it could, unless you give your copyright to the FSF.

---

### Post by Adamant1988 on 2007-07-01
> **BoyOfDestiny said:**
> If you want to author some code and share it with everyone, you can. You don't lose your copyright on it if you GPL it. If you want to contribute your code to a GPLv3 project you could. That same code (since you wrote it) could be given to the public domain, or put under a more permissive license i.e. **BSD**/MIT/etc.

Example of dual licensing
[http://www.mysql.com/company/legal/licensing/faq.html](http://www.mysql.com/company/legal/licensing/faq.html)
[http://trolltech.com/products/qt/licenses/licensing](http://trolltech.com/products/qt/licenses/licensing)

GPLv3 makes no changes to block this. And frankly I don't think it could, unless you give your copyright to the FSF.

I may be wrong here, but it's my understanding that the GPL and BSD licenses are incompatible. Wasn't there an issue quite recently with one of the BSD's using some GPL'd code?

---

### Post by needtolookatascreenshot on 2007-07-01
> **Adamant1988 said:**
> The point is that they're NOT making money off the software. 

Only that they are. You have to pay for Red Hat and Novel, you know.
And even if they weren't making their money directly with the software, but indirectly, why exactly should this be a bad thing?

> **Adamant1988 said:**
> 
Red Hat and Novell could drop their GPL'd software RIGHT NOW and still make money with very slight modifications to the system they're currently using.  In fact, maybe even more money than they're currently making.

Why should that be the case? Anything to back up this assertion?

> **Adamant1988 said:**
> 
No, the middle man isn't more important, you can go right around Red Hat and Novell and get the exact same software from the Fedora or openSuSE communities...

Well, as both Fedora and opensuse are projects from Red Hat and Novell and as both companies sponsor these projects as they profit from them, how exactly should this be considered going around them?

> **Adamant1988 said:**
> 
 the code is all over the place, the middle man is unable to turn the code into a product (practically speaking) under the GPL.

Yet these and many other companies are.

> **Adamant1988 said:**
> 
Even with these companies, there is no middle-man, not for the software.  

Huh? But they are the middle-man. If I buy Red Hat Linux I effectively buy from a middle-man.

---

### Post by starcraft.man on 2007-07-01
> **Adamant1988 said:**
> I am actually on my Windows laptop (as you may have noticed in my screenshot in the GPL v3 thread where I showed my Gmail account).  Soon I'll be on a Mac though, I figure.  As for what I gain, I think it's important to understand my position as a user on this matter.  Firstly, I am not a coder, I am not a developer, and I do not like to hack software.   This so called 'freedom' that the FSF offers doesn't apply to me,  I gain nothing from it, other than that most of the software under the GPL is completely free of cost.  

[COLOR="Blue"]Ok, what I figured. Going to the Mac. Perfectly understandable position, your simply an end user and want the most functional products and your not shy to pay.[/COLOR]

You asked me what I would rather do instead of the GPL, I think that 'open source' is a good development philosophy in general, but I don't agree with free software.  Firstly, I consider code to be a human readable text, so in a way, it's literature.  I believe that everyone should have every right to read any code they want to, to study it, to understand it, to learn from it.  I don't believe that every single person on the planet should be able to edit that code, or use it, any more than I feel that every single person in the world has every right to edit a book and redistribute that.   My ideal software license would reflect that.  

[COLOR="Blue"]This I certainly disagree with. Literature and software are entirely different and cannot be compared. Literature as far as I have seen is a singular process, it requires only one mind (books can of course have multiple contributing authors and positions though, its simply not strictly required) with one position, it conveys knowledge from one with it (i.e. an expert in the field, experienced person's life, professor's views on a matter, etc...) to those without. It usually has purpose, meaning and in the end a goal, once it is finalized and edited to something workable it is printed and distributed. If the views are fact and have been checked, there isn't any need to ever look at the book again, if it is nonfiction, this step is irrelevant and it is done.

Software is an evolution, it never meets an end, ever. A book can sell 500 million copies of multiple prints and never change, it never needs to. Software cannot be like this, it must continue to meet ever present new demands of features and performance. Code, unlike a book, can never be perfect (or as close to it as author edits), code is constantly under revision with updates in an attempt to secure and improve its functions. While everyone should have access like you said to the source, everyone should also be able to edit. What if in staring at the code, some kid in his room figures out the answer to a problem that was bottlenecking the software at 60% efficiency? In your world, he's got nothing. He can't edit or redistribute he can only look. Should he phone up the company and just give the answer to them? That hardly seems effective or that right in my mind. Should he create a parallel project from what he's seen with the answer, maybe even patent it? Is that the solution?

The analogy seems very flawed from my position, maybe another is in order? If not, I suppose we will agree to differ on this.
[/COLOR]
The FSF cannot be trusted anymore than we can trust any organization with a political agenda.  If you firmly believe in what the FSF is saying then you should absolutely support the GPL. 
[COLOR="Blue"]
Well, say I agree that we cannot trust them any more than any other organization with an "agenda". How far are you going to take that? What exactly qualifies as an agenda and how do you quantify how much is too much? I'm not trying to be ridiculous, just putting it into terms I can see. I mean MS and Apple have agendas too. If you saw Steve Jobs key note (announcing safari on Windows) you know he'd like Safari and IE to be the **ONLY** two browsers in existence (it was not a slip, Jobs does not slip from everything I've seen, he did and meant it). That's also an agenda IMO, and it could be construed as political. IF MS and Apple were to become the duopoly controlling access to the net (through whatever means) they would represent an incredible force and from that position be able to create a duopoly on the OS front (an OS without NET access is thoroughly useless today).

I'm not saying thats going to happen tomorrow, or that it's even likely given how Firefox has already captured almost a quarter of the market from grass roots promotion and incompetence on the part of IE/MS. What I am saying is that many more organizations than just the FSF have an agenda, in fact I believe you'd be hard pressed to find one that hasn't got an agenda.

I do agree, I will support the GPL so long as its a license I find in my best interests (just like I only hold positions I can prove and believe to be best).[/COLOR]

Now, you asked me how the GPL hurts me as a consumer, that's a complex question.  It hurts me as a consumer because, a lot of normal business activity that benefits me as a user can't be done.  GPL-software distributors have very limited ability to behave as real businesses and make deals to offer products as such.  The law of the GPL is absolute, when you place your software under a GPL license it's only really yours to a certain extent.  It's my understanding that changing your software to a different license after you've GPL'd it is difficult, without re-writing new code from scratch, but I may be wrong on that.   In the end, the GPL blocks activity that would allow me to get a better product... be that in the form of patent/interoperability deals, or be that in the form of 'tivo-ization'.  As recent examples. 

[COLOR="Blue"]Can't comment on how hard it is to relicense software, I'll have to read into that. I see what you mean though. In the strictest sense the GPL does provide some limitations on what can and cannot be used to improve your end user experience by a company. In the end, it also tries to ensure you have freedoms that companies may not confer otherwise. I understand that you don't find it important to see and edit, you just want a very functional product (i.e. Mac) but thats not to say others don't find that important. I myself find it important that my OS not harbour and support DRM. Thats important to me, and thats why I'll never touch Apple because their lock in both in hardware and software (iTunes, AppleTV, etc...) are the greatest form of DRM in existence. On the flipside, all their software works very well together, exactly how Apple wants it to work (and no more, i.e. limits in how many iTunes authorized machines, etc...). So thats my 2 cents, I guess different priorities for different folks, mean different ways of going about it all.[/COLOR]

I also completely disagree that corporations are made moot by the internet, they're still very needed and if you were to rid the world of every single corporation in existence right now, they would come back (maybe a bit differently).  Corporations are important in getting products to the user, and I think that software IS a product.

Well there we differ, I guess we can't really argue it again, I already stated how I thought about that. Please note though, I didn't say rid us of all corporations (that would be chaotic and insane), only software ones. Hardware still as yet can't be made by coding on the internet, if that happens they will certainly become obsolete. So yes, corporations are important to delivering hardware to the end user, but as for software, that can since it is digital be delivered entirely separately and for free from the net. That is the beauty of the digital world, like it or not.

> **forrestcupp said:**
> No one's arguing about whether or not software patents are a good idea.  Of course software patents are stupid, and they shouldn't be allowed.  But that doesn't mean they don't exist.  Murdering is stupid and *isn't* allowed, but it still exists, and we lock our doors to protect ourselves from things like that happening.  There should be strict rules in the GPL against people taking out software patents.  But there should not be strict rules against people who want to lock their doors to protect their users from *other* unruly people.

[COLOR="Blue"]I'm not sure I follow this analogy. What is the "locked doors" bit equivalent in the GPL? Far as I can tell it certainly does afford protection from patent extortion/people. Are your referring to giving interoperability with these patents, i.e. paying protection money if you choose to? If so, I'd say thats a liberty one has to give up (just like I stated before, for all to have the greatest level of freedom, some liberties must be given while others are conveyed). Like the great idiom says "you can't have you cake and eat it too". The patent system has to be treated with a firm hand, just like any other threat would be treated if you were threatened. _IF_ the GPL allowed most Linux distros/companies to cut deals on patent protection (i.e. with MS or any other IP holder hostile to open source), all the while they publicly railed against the system and wanted it abolished we (the open source) would look like _incompetent hypocrites_. You can't have it both ways, thus, I'm satisfied the GPL has it the right way (supporting undoing the patent system).[/COLOR]

That's absolutely *not* always true.  What if I want to author some code and I want to share it with *everyone*?  Well, I can't release it under GPLv3 because it says I'm not allowed to share my code with companies like Novell.

This is the only problem I have with GPLv3.

[COLOR="Blue"]So you release it under another license if the GPL specifically restricts you too much. There are other licenses and who said the GPL would be the end all of licenses and cover every instance. There's the LGPL, the BSD license, the CCDL (is that right letters?). Life's about choices, and unfortunately making choices means you can't always do everything you want, only spoiled bratty rich kids get to do _everything_ they want. So in the end you have to pick whats most important, just like me picking that not supporting DRM in my OS or software (Valve, I'm looking at your Steam) is one of the fundamental things I believe in. Not only because I believe in the end users digital rights over media (i.e. fair use with DVDs and music, as well as games) but also because all these means have proven inept in preventing dedicated piracy at the cost of the end user.[/COLOR]

Blue is me again, I'm starting to really like blue :D. I believe I covered all the pertinent arguments after my last post, please point out if any were missed, I am sorry if I repeat others, not intentional.

---

### Post by Adamant1988 on 2007-07-01
> **starcraft.man said:**
> Blue is me again, I'm starting to really like blue :D. I believe I covered all the pertinent arguments after my last post, please point out if any were missed, I am sorry if I repeat others, not intentional.

I understand that you like blue and all, but could you please separate your comments from the quote?  It makes quoting a LOT easier.

---

### Post by needtolookatascreenshot on 2007-07-01
> **Adamant1988 said:**
> I may be wrong here, but it's my understanding that the GPL and BSD licenses are incompatible. Wasn't there an issue quite recently with one of the BSD's using some GPL'd code?

It's totally irrelevant if two licenses are incompatible. An author can release his work under as many licenses as he wants to, irregardless of them being compatible or not.

Really, I have to wonder how you think you're fit for a debate about the GPL if you obviously don't understand the most basic concepts of copyright.

---

### Post by BoyOfDestiny on 2007-07-01
> **Adamant1988 said:**
> The point is that they're NOT making money off the software.  The software became a vehicle to do something else.  Red Hat and Novell could drop their GPL'd software RIGHT NOW and still make money with very slight modifications to the system they're currently using.  In fact, maybe even more money than they're currently making.

No, the middle man isn't more important, you can go right around Red Hat and Novell and get the exact same software from the Fedora or openSuSE communities... the code is all over the place, the middle man is unable to turn the code into a product (practically speaking) under the GPL.   Even with these companies, there is no middle-man, not for the software.  

If you'd like to get services associated with the software, well, there you go.

They could? Considering that Novell and RedHat (especially) make contributions to GPL'd software and the Linux kernel better tell them that new business plan so they can rake in the dough.

Ultimately GPL'd codes saves them time and money. If they outsourced for a solution, it'd be costly. If they made their own in-house, it'd be costly. If they used a solution like MS, they'd get no code and could just build apps on top, always having a certain disadvantage since MS doesn't publish all the windows API details. IBM does this with websphere on Linux, nothing in the GPL stopping the building a proprietary app on a Free OS.

So the software is easy to get, or rather the code. Why is this bad? Does it stop commercial interests (I think not, since they can make plenty of money of this, why develop in house when you can use GPL'd code, and maybe get some changes integrated so your team of devs don't do have to re-integrate changes etc.)

If I get the gist of what you are saying, they can't sell the software as is, since you can get it for Free. The developers decided on that license for a reason, they can't get trampled. So the software is out there, and people pay for support, and updates what have you. 

Recipes are everywhere. Yet restaurants, chefs, bakers make a living. If everyone could compile and deal with source code, and handle all that, then I'd see these companies as a middle man. The thing is, many make valuable contributions in keeping with the GPL. It seems win/win from a user perspective...

---

### Post by Adamant1988 on 2007-07-01
> **needtolookatascreenshot said:**
> Only that they are. You have to pay for Red Hat and Novel, you know.
And even if they weren't making their money directly with the software, but indirectly, why exactly should this be a bad thing?

No, you pay for Red Hat's services, and the fact that Novell ships non-free software with their distribution as a feature. 


> Why should that be the case? Anything to back up this assertion?

It shouldn't be the case.  It's more like common sense.  Novell offers support services and non-free software... they don't need their distribution to do that. 


> Well, as both Fedora and opensuse are projects from Red Hat and Novell and as both companies sponsor these projects as they profit from them, how exactly should this be considered going around them?

You're right.. maybe I should just go get Red Hat's code from another distributor... CentOS looks appealing.  It's nearly a 100% copy of RHEL with changed art and anything trademarked taken out. 

> Yet these and many other companies are.


Huh? But they are the middle-man. If I buy Red Hat Linux I effectively buy from a middle-man.

You're not understanding, you don't buy Red Hat Enterprise Linux.  You buy support packages, services, etc. from Red Hat, and you just happen to get the software too.  If you need an example of this, here you go: 

[https://www.redhat.com/wapps/store/catalog.html;jsessionid=WG4dx6lzU0tdli2omAiSLBlenukyVkv1WRO.www01](https://www.redhat.com/wapps/store/catalog.html;jsessionid=WG4dx6lzU0tdli2omAiSLBlenukyVkv1WRO.www01)

---

### Post by BoyOfDestiny on 2007-07-01
> **Adamant1988 said:**
> I may be wrong here, but it's my understanding that the GPL and BSD licenses are incompatible. Wasn't there an issue quite recently with one of the BSD's using some GPL'd code?

You are right. But if the developers of the GPL'd code, gave their explicit permission (the devs still have the copyright on the code they individually wrote), then BSD could use it. They were never asked. You can't just take code from a GPL'd project and put it into BSD. Since BSD allows the code to be closed up, it wouldn't maintain the free to modify, distribute, etc the GPL requires.

---

### Post by starcraft.man on 2007-07-01
> **Adamant1988 said:**
> The point is that they're NOT making money off the software.  The software became a vehicle to do something else.  Red Hat and Novell could drop their GPL'd software RIGHT NOW and still make money with very slight modifications to the system they're currently using.  In fact, maybe even more money than they're currently making.

No, the middle man isn't more important, you can go right around Red Hat and Novell and get the exact same software from the Fedora or openSuSE communities... the code is all over the place, the middle man is unable to turn the code into a product (practically speaking) under the GPL.   Even with these companies, there is no middle-man, not for the software.  

If you'd like to get services associated with the software, well, there you go.
[COLOR="Blue"]
Maybe, this entire "middle man" model is dying. Not just software industry. I for instance know of many bands no longer signing to record labels (even giant names like bare naked and other bands are going their own, they are tired), they make and digitally distribute their own music, they still make money (Johnathan Coulton a good example). I know film makers who make their own independent films (IMO some better than the gutter trash Hollywood makes in cookie cutter molds) and sell/distribute it themselves. In both of these instances, there are examples using the creative commons license and still making money. I will agree, these two instances are more like literature (a creative singular product) but, it does prove the point that with technology and the internet readily available what used to impossible for an individual is now well within grasp. Look at the TWIT network by Leo Laporte, he produces numerous podcasts in his free time and while he does it more for a hobby, he could if he wanted to get more sponsors and get serious cash that way. There are others who start up entirely from the net and go.

Lastly of course software, maybe the entire software model was wrong to begin with? Maybe making a product out of software is an old idea, just like when the industrial revolution made the craftsman irrelevant. I can't help but see parallels in how they hold on in dying moments. You may want software to continue to be a product, but I also imagine many wanted craftsman to continue to make superior quality products than the industrial assembly line could.[/COLOR]

Thats that, I think thats enough countering for now, I'm off to other threads. Someone else feel free to continue.

> **Adamant1988 said:**
> I understand that you like blue and all, but could you please separate your comments from the quote?  It makes quoting a LOT easier.
[COLOR="Green"]Well, you could always pick another colour and write under and delete the previous. Then we could have a rainbow :p
[/COLOR]

Edit: Btw, we got to 9 pages and still being civil, unbelievable. I don't know many heated discussions on topics like this that have remained civil so long. I'm happy :).

---

### Post by Adamant1988 on 2007-07-01
> **BoyOfDestiny said:**
> 
Recipes are everywhere. Yet restaurants, chefs, bakers make a living. If everyone could compile and deal with source code, and handle all that, then I'd see these companies as a middle man. The thing is, many make valuable contributions in keeping with the GPL. It seems win/win from a user perspective...

Yes, recipes are EVERYWHERE.  Interesting thing about food though, it's not free to make.  It requires ingredients, and time, it has a cost.  Programs, and anything else that is digital aren't in the same boat.  I can create X program 1 time, and distribute infinite copies of that program, only limited by my ability to get that software to you (be it in a box, or a download form).  

I think a more accurate comparison is to a book.  Books are everywhere, they all use a language to produce a product and are unlimited in quantity once put in digital form.  Books are profitable because of laws that prevents them from being unfairly duplicated and copied.  

I think the largest portion of this argument obviously stems from what we believe software is.  Some people, like the FSF obviously agree with you that software is like a recipe and should be freely available to edit and so on as you see fit.  I feel that software is more like a literary work, and I'm probably not alone in that.

---

### Post by deanlinkous on 2007-07-01
> **forrestcupp said:**
> 
 What if I want to author some code and I want to share it with *everyone*?  Well, I can't release it under GPLv3 because it says I'm not allowed to share my code with companies like Novell.
Why cant you? You simply release it and if they respect the license they are free to use it. 

Do you think microsoft would care if you took code and decided to not respect the license? Companies gain from using free software....and the only "payment" is to respect the license - sounds reasonable to me. Devels that license code under v3 specifically want what the license provides. 

How would you feel if you give someone something in return for them doing something and they choose not to do it. Don't you feel like they stole from you?

---

### Post by starcraft.man on 2007-07-01
> **Adamant1988 said:**
> Yes, recipes are EVERYWHERE.  Interesting thing about food though, it's not free to make.  It requires ingredients, and time, it has a cost.  Programs, and anything else that is digital aren't in the same boat.  I can create X program 1 time, and distribute infinite copies of that program, only limited by my ability to get that software to you (be it in a box, or a download form).  

I think a more accurate comparison is to a book.  Books are everywhere, they all use a language to produce a product and are unlimited in quantity once put in digital form.  Books are profitable because of laws that prevents them from being unfairly duplicated and copied.  

I think the largest portion of this argument obviously stems from what we believe software is.  Some people, like the FSF obviously agree with you that software is like a recipe and should be freely available to edit and so on as you see fit.  I feel that software is more like a literary work, and I'm probably not alone in that.

Recipes are a good analogy. I'm gonna have to remember that one. It does make a good example. I do agree, it largely depends how you define software and what you want from it. Nothing much else to say, I've covered the book thing before >.>.

---

### Post by deanlinkous on 2007-07-01
> **Adamant1988 said:**
>    This so called 'freedom' that the FSF offers doesn't apply to me,  I gain nothing from it, other than that most of the software under the GPL is completely free of cost.   
The GPL (for the most part) does not apply to you in this case BUT you benefit from it in many ways.....not just the cost aspect.

> Firstly, I consider code to be a human readable text, so in a way, it's literature.  I believe that everyone should have every right to read any code they want to, to study it, to understand it, to learn from it.  I don't believe that every single person on the planet should be able to edit that code, or use it, any more than I feel that every single person in the world has every right to edit a book and redistribute that.  
But I am free to write a book using the same words. I am free to quote other persons exact words. I am free to take inspiration from that work... But that is a silly comparison anyway since books aren't functionally useful.


> The FSF cannot be trusted anymore than we can trust any organization with a political agenda.  
What is the 'political agenda'? Thay have a agenda which is software freedoms and I trust that a LOT more than a agenda of 'make money above all else'! Why cant they be trusted? 

> Now, you asked me how the GPL hurts me as a consumer, that's a complex question.  It hurts me as a consumer because, a lot of normal business activity that benefits me as a user can't be done.  GPL-software distributors have very limited ability to behave as real businesses and make deals to offer products as such.  The law of the GPL is absolute, when you place your software under a GPL license it's only really yours to a certain extent.  It's my understanding that changing your software to a different license after you've GPL'd it is difficult, without re-writing new code from scratch, but I may be wrong on that.   In the end, the GPL blocks activity that would allow me to get a better product... be that in the form of patent/interoperability deals, or be that in the form of 'tivo-ization'.  As recent examples. 
HIlarious...... Depends on how you define *better*
Nothing is better to me than free software....

---

### Post by deanlinkous on 2007-07-01
> **Adamant1988 said:**
> Correct me if I'm wrong but isn't ZFS (currently) being forced to live in user-space thanks to it's licensing?  if Ubuntu shipped with ZFS the legal way, ZFS would be in user-space and have severely reduced performance.  You can correct me if I'm wrong, I'm just saying I haven't heard a single person say it was alright to offer ZFS with the distro, other than you.
excuse me.....
So can you run ZFS on windows? What about any of the other filesystems?

---

### Post by BoyOfDestiny on 2007-07-01
> **Adamant1988 said:**
> Yes, recipes are EVERYWHERE.  Interesting thing about food though, it's not free to make.  It requires ingredients, and time, it has a cost.  Programs, and anything else that is digital aren't in the same boat.  I can create X program 1 time, and distribute infinite copies of that program, only limited by my ability to get that software to you (be it in a box, or a download form).  

I think a more accurate comparison is to a book.  Books are everywhere, they all use a language to produce a product and are unlimited in quantity once put in digital form.  Books are profitable because of laws that prevents them from being unfairly duplicated and copied.  

I think the largest portion of this argument obviously stems from what we believe software is.  Some people, like the FSF obviously agree with you that software is like a recipe and should be freely available to edit and so on as you see fit.  I feel that software is more like a literary work, and I'm probably not alone in that.

Definitely. I agree. The thing with the software/book analogy, and I honestly think that's the most accurate. Developers are authors, and I do feel copyright does the job, but sometimes he or she wants to tweak it. 

There are creative common licenses for example. Some books in print have free versions online in addition to printed form. When a developer picks the GPL, BSD, MIT, or just keeping it closed sourced, they are making the choice, if it's worth it, etc.

These licenses wouldn't work without copyright, what I like with the GPL is there is a catch. Every user down the line gets the same rights (what the FSF calls Freedoms)
You still get Fair Use rights of course too. I see it as a huge perk, even just from the end user perspective.

rant:
I don't think all software has to be GPL'd, it's my favorite though no question. Most of it stems from practicality. I can use my favorite software on various OS's and architectures. Checkout the download pages for Scummvm or Videolan. The other in terms of drivers, i can use devices the original manufacturer may not care about anymore, or an OS they don't bother making drivers for. 
From an ideological standpoint (which I think is practical too) software gets contributions back into it, so it keeps improving. The last being I hate registration codes, copy protection etc. Computers can be annoying even without this in place... Not to mention when the software is closed source, it's a "blackbox" so I can't be sure what it's doing. This of course doesn't apply to a book, unless you weren't allowed to open it. ;)

---

### Post by deanlinkous on 2007-07-01
> **Adamant1988 said:**
> The point is that they're NOT making money off the software.  The software became a vehicle to do something else.  Red Hat and Novell could drop their GPL'd software RIGHT NOW and still make money with very slight modifications to the system they're currently using.  In fact, maybe even more money than they're currently making.

No, the middle man isn't more important, you can go right around Red Hat and Novell and get the exact same software from the Fedora or openSuSE communities... the code is all over the place, the middle man is unable to turn the code into a product (practically speaking) under the GPL.   Even with these companies, there is no middle-man, not for the software.  

If you'd like to get services associated with the software, well, there you go.
What.....?????? this thread is off my subscribed list.....thanks for the fish...

---

### Post by Adamant1988 on 2007-07-01
> **deanlinkous said:**
> 
But I am free to write a book using the same words. I am free to quote other persons exact words. I am free to take inspiration from that work... But that is a silly comparison anyway since books are functionally useful.


Deanlinkous,  I respect yours and other's stances on the GPL, really I do.  Which is why I'm not out-and-out saying "YOUR WRONG!".  But you're right, you're free to quote the other person's exact words (with due credit) but you can't plagiarize them.

---

### Post by needtolookatascreenshot on 2007-07-01
> **Adamant1988 said:**
> No, you pay for Red Hat's services, and the fact that Novell ships non-free software with their distribution as a feature. 
Nope. You also pay for the distribution itself, not just for services and propietary software. But again, why should it matter what you pay for?

> **Adamant1988 said:**
> 
Novell offers support services and non-free software... they don't need their distribution to do that. 

Novel seems to disagree with you here...
Now, are they just idiots or could this mean that you, gasp, might be wrong here?

> **Adamant1988 said:**
> 
You're right.. maybe I should just go get Red Hat's code from another distributor... CentOS looks appealing.  It's nearly a 100% copy of RHEL with changed art and anything trademarked taken out. 

You are aware though that Red Hat does have no problem whatsoever with CentOS, are you? And btw., most of the software Red Hat ships with isn't from Red Hat, so it's already available from other sources anyway. May I suggest that Red Hat is merely acting as a middle-man?

---

### Post by deanlinkous on 2007-07-01
> **Adamant1988 said:**
> Deanlinkous,  I respect yours and other's stances on the GPL, really I do.  Which is why I'm not out-and-out saying "YOUR WRONG!".  But you're right, you're free to quote the other person's exact words (with due credit) but you can't plagiarize them.
Thats right....and with the GPL you are given the right to *plagarize*....and vice versa. Everyone benefits from everyones work - we all progress rapidly instead of working against each other. Actually it isn't plagarizing since you cite the source - the copyright notice. But once again, books are not software, books are not functionally useful, books are not software....

Hard to discuss anything with you when you pick and choose what you want to reply to, and the hard parts you just ignore and go on repeating so I do not enjoy discussing some things with you and this is one of them. Since, I really think you do not *get* free software...

So thanks for all the fish......

---

### Post by Adamant1988 on 2007-07-01
> **needtolookatascreenshot said:**
> Nope. You also pay for the distribution itself, not just for services and propietary software. But again, why should it matter what you pay for?

Unless you can prove this I think you're just rambling for the sake of arguing with me.  SLED comes with certain technologies from Novell, hence the price. 





> You are aware though that Red Hat does have no problem whatsoever with CentOS, are you? And btw., most of the software Red Hat ships with isn't from Red Hat, so it's already available from other sources anyway. May I suggest that Red Hat is merely acting as a middle-man?

Right, but if Red Hat was actually making money from Red Hat Enterprise Linux and NOT their services, they WOULD care.  Red Hat is acting as a middle-man to the extent that they distribute RHEL, but you can get the same code elsewhere.  If they relied on being the software middle-man for their business, the GPL would hurt them very badly. 

> Thats right....and with the GPL you are given the right to *plagarize*....and vice versa. Everyone benefits from everyones work - we all progress rapidly instead of working against each other. Actually it isn't plagarizing since you cite the source - the copyright notice. But once again, books are not software, books are not functionally useful, books are not software....

Hard to discuss anything with you when you pick and choose what you want to reply to, and the hard parts you just ignore and go on repeating so I do not enjoy discussing some things with you and this is one of them. Since, I really think you do not *get* free software...
So thanks for all the fish......

This is where you and I have to agree to disagree.  I try to limit my replies based on the amount of time I have to reply, and how many posts to reply to, sorry if I miss something.  You asked if Windows could use ZFS, I'm not sure, they might be able to swing that... I know that OS X can use ZFS though, and that it's being put into leopard in one form or another (I've heard lots of rumors concerning specifics).

---

### Post by needtolookatascreenshot on 2007-07-01
> **Adamant1988 said:**
>  SLED comes with certain technologies from Novell, hence the price. 

Then please prove that that's the case. Thanks.

> **Adamant1988 said:**
> 
Right, but if Red Hat was actually making money from Red Hat Enterprise Linux and NOT their services, they WOULD care.  Red Hat is acting as a middle-man to the extent that they distribute RHEL, but you can get the same code elsewhere.  If they relied on being the software middle-man for their business, the GPL would hurt them very badly. 

Well, first off, if it weren't for the GPL, they wouldn't have a business in the first place.
Second, you still didn't answer why it should matter if a company makes the money directly with the software or indirectly. 
Third, I fail to see your point. Just assuming you were right in your description (which you aren't, btw.), how does the GPL hurt a company that wants to sell it's software the way you obviously seem to think is the only valid way. If they just don't put their software under the GPL they are not effected at all. So what's the problem?


> **Adamant1988 said:**
> 
I try to limit my replies based on the amount of time I have to reply, and how many posts to reply to, sorry if I miss something. 
It's not that you miss something, it's that you constantly change the subject of the discussion at hand in order not having to confront certain questions.

For example, our little discussion does have absolutely nothing to do with your initial post and the article you linked to. The only connection is that in your anti-free-software-zeal you are constantly clasping at straws trying to show that free software is somehow evil.

That's why you didn't react to posting an article full of untruths after being called on it. That's why you didn't react on your repeated and false assertion that the GPL somehow disenfrenchizes the original author after being called on it.

Frankly, it's really tireing trying to keep something resembling a sane discussion going with you when you proved to be absolutely unable and unwilling so far to present anything even remotely resembling a coherent argument in your anti-free-software-crusade.

Tell you what, why don't we simply let this thread die and you start a new one in which you try to explain all the objections you have against the GPL?

---

### Post by Tomosaur on 2007-07-01
> **Adamant1988 said:**
> Unless you can prove this I think you're just rambling for the sake of arguing with me.  SLED comes with certain technologies from Novell, hence the price. 


Are you serious?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=36994&stc=1&d=1183306450[/IMG]


[https://www.redhat.com/apps/download/](https://www.redhat.com/apps/download/)

---

### Post by Adamant1988 on 2007-07-01
> **Tomosaur said:**
> Are you serious?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=36994&stc=1&d=1183306450[/IMG]


[https://www.redhat.com/apps/download/](https://www.redhat.com/apps/download/)

I stand corrected, I didn't see that in their store at all.  That's really odd that it wouldn't be there. I'll go re-check.

EDIT: I have double-checked and confirmed that I am still right.. that $80 is for a 'basic subscription'. 

See: [https://www.redhat.com/apps/store/desktop/](https://www.redhat.com/apps/store/desktop/)

---

### Post by az on 2007-07-01
> **Adamant1988 said:**
> Correct me if I'm wrong but isn't ZFS (currently) being forced to live in user-space thanks to it's licensing?  if Ubuntu shipped with ZFS the legal way, ZFS would be in user-space and have severely reduced performance.  You can correct me if I'm wrong, I'm just saying I haven't heard a single person say it was alright to offer ZFS with the distro, other than you.

There is a userspace port, but nothing would prevent there being a non-free port to the linux kernel in exactly the same way the nvidia and ati drivers are shipped with Ubuntu.  Those non-free video drivers are not GPL and are not GPLed.  You can never take the kernel and combine it with those drivers and release the whole thing under the GPL.  That's it.  That's the limit of your restriction.  You are free to use them and distribute them separately.  


> **Adamant1988 said:**
> I may be wrong here, but it's my understanding that the GPL and BSD licenses are incompatible. Wasn't there an issue quite recently with one of the BSD's using some GPL'd code?

Well, if you want to run a GPL-free version of BSD, some parts of the toolchain just won't be there  (I reckon the only non-gpl versions that exist have been taken away to proprietary land).  I wonder if you are able to compile BSD on a GPL-free system?


> **needtolookatascreenshot said:**
> 
Tell you what, why don't we simply let this thread die and you start a new one in which you try to explain all the objections you have against the GPL?

Isn't that what this thread is?  There was the same conversation going on in the "GPL v3 is released" thread from two days ago.  This thread was started for nothing.  Trolling?

---

### Post by Celegorm on 2007-07-01
> **Adamant1988 said:**
> I may be wrong here, but it's my understanding that the GPL and BSD licenses are incompatible. Wasn't there an issue quite recently with one of the BSD's using some GPL'd code?

Depends if you are talking about the BSD-new or the original. The original is incompatible with the GPL due to its advertising clause, while the new one is completely compatible with the GPL.
[http://www.opensource.org/licenses/bsd-license.php]("http://www.opensource.org/licenses/bsd-license.php")
[ftp://ftp.cs.berkeley.edu/pub/4bsd/README.Impt.License.Change]("ftp://ftp.cs.berkeley.edu/pub/4bsd/README.Impt.License.Change")


Adamant, it seems to me that what you dislike is not the GPL itself, but that there is a lot of very nice software licensed under it, and that companies cannot take advantage of it in certain ways that would benefit some of their customers, like using bits of GPL'd code in their proprietary programs to improve them, and still keep the source closed.

---

### Post by matthinckley on 2007-07-01
> **Celegorm said:**
> Adamant, it seems to me that what you dislike is not the GPL itself, but that there is a lot of very nice software licensed under it, and that companies cannot take advantage of it in certain ways that would benefit some of their customers, like using bits of GPL'd code in their proprietary programs to improve them, and still keep the source closed.

I see it this way too, and I find it very amusing.. how can you get upset that you can't use GPL'd code in your proprietary program? it is licensed code.. if the code was licensed under say a microsoft EULA you wouldn't be able to use it either.. in fact you wouldn't even be able to see it.. is the fact that you can see the code but can't use it what makes you upset?

---

### Post by jiminycricket on 2007-07-01
> **forrestcupp said:**
> No one's arguing about whether or not software patents are a good idea.  Of course software patents are stupid, and they shouldn't be allowed.  But that doesn't mean they don't exist.  Murdering is stupid and *isn't* allowed, but it still exists, and we lock our doors to protect ourselves from things like that happening.  There should be strict rules in the GPL against people taking out software patents.  But there should not be strict rules against people who want to lock their doors to protect their users from *other* unruly people.

The problem is that it hurts the people providing the actual software, because Novell instead of that other company reaps financial benefit from poisoning the well.  A lot of the code in SUSE is not owned by Novell.  If one wants assurance, there is the OIN or the OSRM insurance.




> What if I want to author some code and I want to share it with *everyone*?  Well, I can't release it under GPLv3 because it says I'm not allowed to share my code with companies like Novell.
 Maybe release into the public domain or GPLv2 only...with public domain, one can do anything they want, including denying freedom to the end user (user=developer in free software licenses, usually).  Or release GPLv2 or later so that the user can choose to use the GPLv3.

---

### Post by forrestcupp on 2007-07-01
> **jiminycricket said:**
> 
 Maybe release into the public domain or GPLv2 only...with public domain, one can do anything they want, including denying freedom to the end user (user=developer in free software licenses, usually).  Or release GPLv2 or later so that the user can choose to use the GPLv3.
But that was my point.  I know there are other licenses that I could use, but I cannot use GPLv3 in that case.  That was all I was saying.  I think probably using GPLv2 or later may be the best choice.

I know they were debating back and forth, but they ended up letting Novell get grandfathered in, didn't they?

---

### Post by jiminycricket on 2007-07-02
> **forrestcupp said:**
> But that was my point.  I know there are other licenses that I could use, but I cannot use GPLv3 in that case.  That was all I was saying.  I think probably using GPLv2 or later may be the best choice.

I know they were debating back and forth, but they ended up letting Novell get grandfathered in, didn't they?

Those companies can use GPLv3 code anytime they want if they modify the  agreement. GPLv3 section 11's "out" for these companies is to extend the patent license to everyone, though obviously these companies can't unilaterally do that so they'll have to modify or terminate the MS patent agreement if they don't sell it to customers individually like Linspire does).  It's especially stupid of a company to get into the same agreement as Novell did after the FSF stated their intent was to disallow such a loophole (I still remember the Xandros CEO saying that he didn't care about the GPLv3 - "If you are a businessperson, you can't worry about every eventuality").  Anyways, I'm not sure whether Linspire or Xandros are stuck by section 11 because their deals are little different than Novell's.  Linspire's idea was to sell a patent pack to customers individually.

So yes, all 'discriminatory' patent deals prior to March 28, 2007 are grandfathered in.  In Novell's case, because Microsoft agreed to distribute 70 000 SUSE coupons per year, they can turn the agreement on its head by getting GPLv3 code into SUSE and then MS's patent license to their customers is extended.  Of course, the contract that MS and Novell signed was explicity very open to modification and termination at anytime, and I don't think the patents it covers are very useful (no WINE, "Clone Products", OO.org, etc),

---

### Post by jrusso2 on 2007-07-02
Despite all this FUD about GPL v3 seems three major Linux company's are satisfied with GPL v3.

Novell, Red hat and IBM are all pleased with it

[http://www.builderau.com.au/news/soa/GPL3-welcomed-by-IBM-Red-Hat-Novell-MySQL/0,339028227,339279403,00.htm](http://www.builderau.com.au/news/soa/GPL3-welcomed-by-IBM-Red-Hat-Novell-MySQL/0,339028227,339279403,00.htm)

---

### Post by deanlinkous on 2007-07-02
> **jrusso2 said:**
> Despite all this FUD about GPL v3 seems three major Linux company's are satisfied with GPL v3.

Novell, Red hat and IBM are all pleased with it

[http://www.builderau.com.au/news/soa/GPL3-welcomed-by-IBM-Red-Hat-Novell-MySQL/0,339028227,339279403,00.htm](http://www.builderau.com.au/news/soa/GPL3-welcomed-by-IBM-Red-Hat-Novell-MySQL/0,339028227,339279403,00.htm)

and I know at least ONE user that is VERY pleased..... ;)

GREAT GREAT article by the way!

---

### Post by Starchild on 2007-07-02
> **jrusso2 said:**
> Despite all this FUD about GPL v3 seems three major Linux company's are satisfied with GPL v3.

Novell, Red hat and IBM are all pleased with it

[http://www.builderau.com.au/news/soa/GPL3-welcomed-by-IBM-Red-Hat-Novell-MySQL/0,339028227,339279403,00.htm](http://www.builderau.com.au/news/soa/GPL3-welcomed-by-IBM-Red-Hat-Novell-MySQL/0,339028227,339279403,00.htm)

You forgot Sun.

---

### Post by Andrewie on 2007-07-02
whats the problem with everyone, everything worked out perfectly. The kernel isn't changing, projects that want to change can change. Plus I still get my Suse Linux....good enough for me. Lets waste our time other places like the openmoko.

---

### Post by starcraft.man on 2007-07-02
> **Andrewie said:**
> whats the problem with everyone, everything worked out perfectly. The kernel isn't changing, projects that want to change can change. Plus I still get my Suse Linux....good enough for me. Lets waste our time other places like the openmoko.

The kernel may just be changing (linus has said if SUN moved to 3 for everything he'd be interested, its speculation but so is your statement), never assume just because something isn't so today that tomorrow won't bring surprises.

As for wasting time, there are worse things to do than posting about an important free software license. Discussions, are in my opinion a very worthy pursuit leading to better understanding of your world and how you fit in. Watching brainless reality television comes to mind, so I guess it matters whats important to you. You don't have to read if it bothers you that much.

---

### Post by Andrewie on 2007-07-02
> **starcraft.man said:**
> The kernel may just be changing (linus has said if SUN moved to 3 for everything he'd be interested, its speculation but so is your statement), never assume just because something isn't so today that tomorrow won't bring surprises.

As for wasting time, there are worse things to do than posting about an important free software license. Discussions, are in my opinion a very worthy pursuit leading to better understanding of your world and how you fit in. Watching brainless reality television comes to mind, so I guess it matters whats important to you. You don't have to read if it bothers you that much.

I've read tons of articles on his sun movement, he was rather mad cause they we're going to take drivers and not GPL any of their good stuff like zfs.

---

### Post by nphx on 2007-07-02
Geez, when did GNU become a game console? This article is too funny turns patents into game consoles and skateboards. Poor examples. GPL3 is as GPL2 except that those companies who wish to take the communities work and label it their own and apply any proprietary restrictions can't do so.

---

### Post by needtolookatascreenshot on 2007-07-02
> **forrestcupp said:**
> But that was my point.  I know there are other licenses that I could use, but I cannot use GPLv3 in that case.
But you can.

---

