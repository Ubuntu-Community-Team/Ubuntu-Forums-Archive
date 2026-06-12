---
title: "Will &quot;Trusted Computing&quot; matter?"
date: 2005-11-30
forum: The Cafe
---

### Post by hizaguchi on 2005-11-30
Being a longtime Windows user who is only recently seeing the point of open source (beyond freedom in the "freeware" sense), I've been trying to learn more about things like "Trusted Computing" and DRM.  From my new point of view, these things seem horrible.  But what I wonder is, do you think these increasingly imposing digital restrictions will really make much difference to the average Windows user?  Do you think they'll make much difference (aside from piracy and file sharring) to the way computers are used in general?  What are the real, practical implications (not just the ideological problems)?

A big part of me hates the idea of having any more restrictions placed on my own property, especially when the restrictions come from private industry rather than government.  I want to declare that I'll make a more dilligent effort to move completely away from Microsoft products from now on, and never purchase another Windows OS.  But I wonder if all of this is because the restrictions really have a practical impact on me, or if I just feel this way because of my ideals.  I'm not well enough informed about this technology to know the difference in paranoia and an actual problem.

---

### Post by GeneralZod on 2005-11-30
The TPM allows a server to request and receive an (effectively) unforgeable hash of the programs on your system - this will enable e.g. websites to not provide content to your machine unless it knows that it will be encrypted and keyed to your machine so that it cannot be copied elsewhere.

Some have donned their tinfoil hats and said that eventually, ISPs may simply just refuse Internet access to anything but a Trusted machine running a Trusted OS, and that this OS will definitely not be Linux - more likely, it will be a DRM-laden version of Windows.  This will pretty much kill off the Free Software movement once and for all, or at least marginalise it so much that it will never be any kind of competition for proprietary stuff.  Someone mentioned that Bush eventually wants all online computers to be Trusted, but didn't provide a link, so this may not be true.

Anyway, I have a sneaking suspicion that Linux users may well end up suffering every bit as much (or perhaps more) than our Windows using brethren.  But then, I always tend to assume the worst, so don't mind me ;)

Edit:

If you want some even more dystopian views on the implications of the adoption of this technology, read this:

[http://www.cl.cam.ac.uk/~rja14/tcpa-faq.html](http://www.cl.cam.ac.uk/~rja14/tcpa-faq.html)

---

### Post by 23meg on 2005-11-30
Let me start by stating my stance: I find TC disgusting, I won't run Windows Vista or any other TC-enabled OS on any computer I own, I won't even check my email on a TC-enabled system, I'll take every chance to avoid buying anything produced by TCPA member companies, and I try my best to raise awareness about the issue.

But judging by the relative ignorance of the masses so far, and the weakness of the protests that do exist, I sadly think it won't make a big difference. You read right; the sad part of it is that it won't make a big difference. It won't make a big difference in the profits software companies make by reducing piracy (it WILL be cracked, even though less practically than software only copy protection), it won't make a difference on how Joe Average sees his ownership rights on his computer and his data, it won't make a difference to companies and institutions shelling out tens of thousands of dollars to Microsoft to blindly update their copies of XP without knowing the massive change in the underlying technology. It won't make a difference to the unwashed masses.

But it will change the ethical climate of the world of everyday computing irreversibly. 

On the other hand, many ethically sensitive people who haven't been turned to the issue so far will understand the true consequences of adopting TC, even though late, and concentrate on adopting a FOSS scheme as soon as possible. Linux and BSD will gain an addition to their user base, which will be the people who have been waiting at the margin of the proprietary software world for a killer reason to totally abandon it.

[QUOTE=hizaguchi]
But I wonder if all of this is because the restrictions really have a practical impact on me, or if I just feel this way because of my ideals.[/QUOTE]
It shouldn't matter. Even if there are no practical restrictions placed on you (since you're not using a TC-enabled OS for example), if it's against your ethical stance on how computing should be in general, if you find it ideologically incorrect in its essence, you should oppose it. 

If you haven't already, take time to read [Ross Anderson's TC FAQ]("http://www.cl.cam.ac.uk/~rja14/tcpa-faq.html"). It's the best half hour you can invest in getting informed on computing ethics, and now is the time to get informed.

---

### Post by Malphas on 2005-11-30
Doesn't the Linux kernel already have TPM support?

---

### Post by 23meg on 2005-11-30
[QUOTE=Malphas]Doesn't the Linux kernel already have TPM support?[/QUOTE]Support doesn't necessarily mean utilization; even if there is support, as long as you have control on the code that operates on the hardware and are sure it doesn't do anything "evil", you're on the safe side. And open source being open source, you'll always be able to throw away the evil code if you wish, whereas proprietary operating systems are stuck with it from now on.

Furthermore, if the TPM can be used for high quality open-source, non-vendor-locked encryption, that's only a gain for open source.

---

### Post by Malphas on 2005-11-30
[QUOTE=23meg]Support doesn't necessarily mean utilization; even if there is support, as long as you have control on the code that operates on the hardware and are sure it doesn't do anything "evil", you're on the safe side. And open source being open source, you'll always be able to throw away the evil code, whereas proprietary operating systems are stuck with it from now on.[/QUOTE]
Well in the very FAQ you linked to it actually says that you have the option to switch TC off (and it appears to be saying that in the context of Windows).

---

### Post by 23meg on 2005-11-30
[QUOTE=Malphas]Well in the very FAQ you linked to it actually says that you have the option to switch TC off (and it appears to be saying that in the context of Windows).[/QUOTE]You do, but if you do, you won't be able to run apps that will require TC to be on (which will be pretty much every major software package for Windows, since the TCPA includes pretty much every major Windows software vendor), you won't be able to play your media files acquired from a TC-using vendor, you won't be able to connect to services that require TC, you won't be able to use certain Windows features, so on. Turning TC off will defeat the purpose of running Windows for most people. And even when you turn it off, you can't be 100% sure that it's turned off, since you don't know what the closed source software that says it has turned it off is actually doing.

---

### Post by Malphas on 2005-11-30
Yes, but that exact same situation is equally possible under Linux.  Again, it says this in the FAQ.

---

### Post by 23meg on 2005-11-30
[QUOTE=Malphas]Yes, but that exact same situation is equally possible under Linux.  Again, it says this in the FAQ.[/QUOTE]It's theoretically possible in any OS, but as I've said before, it will be mandatory in closed-source systems that utilize it whereas in open source you have exact control on what your kernel and your userspace apps are doing with the TPM, and if you don't want to utilize the TPM at all, if you want to disable all access to it, you can do so without any silly restrictions such as being unable to run the majority of your apps. It comes down to the basic difference between open source and proprietary.

---

### Post by Malphas on 2005-11-30
Now we're going round in circles.  Yes, it's possible in any OS, agreed; and as you said it'll be mandatory in closed-source systems such as Windows, and as I already said the FAQ that you linked to actually contradicts you on this point.  I'm not saying I agree 100% with the FAQ either, mind you.

Now you're saying that if Linux does come with TC, you'll simply be able to disable it with no restrictions as consequence.  As far as I can see this is completely unsubstantiated and most likely false.  If you're running a Linux application that requires TC and you disable it, then it won't work - exactly the same as the situation in a closed-source system.  If you're trying to play TC media files in Linux and you disable TC, it won't work - again, exactly the same as in a closed source system.  The basic difference between open-source and proprietary is completely irrelevant.

Of course, all this is mostly speculation and don't think anyone can really claim at this stage to know how this is actually going to unfold itself.

---

### Post by newbie2 on 2005-11-30
"Open source software, if used, needs to be identified as such, so that it can be freely shared with others. Developers on Slashdot.org and other Internet bulletin boards could not find an open source reference in the copy-protection software."
"That‘s the flipside of open source: If you don‘t respect the open source rules, the old regime of copy protection comes back in full force," said attorney and Internet specialist Christiaan Alberdingk Thijm at law firm SOLV in the Netherlands.
There was LAME and other LGPL code in the program, and significant amounts were tightly integrated into the executable program, Saber Security said. "
[http://www.heraldnewsdaily.com/stories/news-00106363.html](http://www.heraldnewsdaily.com/stories/news-00106363.html)
:rolleyes:

---

### Post by 23meg on 2005-11-30
It's theoretically possible in any OS, but when you run Microsoft's OS and, say, Adobe's software, since both are TCPA members, you're in a TCPA lock-in; you're at the mercy of these companies in terms of what your apps do with your TPM, and even your CPU, since the new generation CPUs have TC components as well. Plus since Adobe is already pretty much a monopoly and there's no real alternative to, say, Photoshop for most uses, you're stuck with Adobe + Microsoft.

Whereas when you run Linux/BSD and free software, since there's no singular Linux Corporation or BSD International that's a TCPA member, and software production is decentralized and non-commercial, you have the choice and control on whether you want to opt into TC or not without suffering serious consequences.

TC-enabled open source software will definitely exist, but you'll be able to know how exactly they make use of TC, and except for certain software niches, there will be no real need for TC. For software that does not absolutely rely on online transactions with a central vendor to perform its duties, TC is only meant for copy protection, and who needs copy protection in the free software world? And vendor-reliant services will already be paid ones where you'll gain as much rights on your media files as you pay, and if you are to oppose this scheme, you should oppose DRM in the first place, not TC. TC only gives DRM using vendors more powerful weapons. 

So the basic difference between FOSS and proprietary is not irrelevant at all.

---

### Post by Malphas on 2005-11-30
> **23meg]It's theoretically possible in any OS, but when you run Microsoft's OS and, say, Adobe's software, since both are TCPA members, you're in a TCPA lock-in said:**
> 
Well I could run GIMP instead, which is the exact same alternative I'd have supposing I were running Linux, so really no difference there (aside from the fact that the GIMP doesn't work as well in Windows as it does natively).


[QUOTE=23meg]Whereas when you run Linux/BSD and free software, since there's no singular Linux Corporation or BSD International that's a TCPA member, and software production is decentralized and non-commercial, you have the choice and control on whether you want to opt into TC or not without suffering serious consequences.
Like I said previously, the consequences are exactly the same.


[QUOTE=23meg]TC-enabled open source software will definitely exist[/QUOTE]
Don't know how you can claim that.  Seems more like speculation and opinion than fact.


[QUOTE=23meg]TC is only meant for copy protection, and who needs copy protection in the free software world?[/QUOTE]
Free software isn't just some hobbyist niche, it's used every day in real world enterprise situations.  Why do you think TPM support has been added to the kernel?  It's because right now enterprise is where Linux is at, not the home desktop market.  And for all we know enterprise customers may well want or need TPM support for a variety of reasons.


[QUOTE=23meg]And vendor-reliant services will already be paid ones where you'll gain as much rights on your media files as you pay, and if you are to oppose this scheme, you should oppose DRM in the first place, not TC. TC only gives DRM using vendors more powerful weapons.[/QUOTE]
Personally I would never buy DRM protected media.  But in your original argument this was one of your points for why TC would be de-facto mandatory on Windows.  My argument was that the same would be true in Linux.  The fact that most Linux users oppose DRM anyway, isn't a valid argument for why TC need not affect Linux, whilst it does affect Windows.


[QUOTE=23meg]So the basic difference between FOSS and proprietary is not irrelevant at all.[/QUOTE]
Well supposing that were true, it still would mean that the difference between using a closed-source/Windows solution or a Linux one would be irrelevant considering that open-source software is available for Windows as well.  So the exact same arguments would apply.  And similarly, proprietary closed-source software exists for Linux.

---

### Post by 23meg on 2005-11-30
> **Malphas]Well I could run GIMP instead, which is the exact same alternative I'd have supposing I were running Linux, so really no difference there (aside from the fact that the GIMP doesn't work as well in Windows as it does natively.[/quote]The point is that you wouldn't be able to have GIMP as an alternative in Windows if it weren't for the FOSS community which isn't commercially minded like Adobe. Corporations such as Adobe become TCPA members to secure their commercial interests, and the basic difference between the FOSS world and the proprietary software world comes into effect here: no FOSS developer in his right mind will attempt to become a TCPA member (who will accept him anyway) and secure his software. Because free software doesn't need securing. This is the point you seem to be missing.

[quote=Malphas]Don't know how you can claim that.  Seems more like speculation and opinion than fact.[/quote]Like you say, why has TPM support been added to the kernel? For people to develop open source software that takes advantage of it.

[quote=Malphas]Free software isn't just some hobbyist niche, it's used every day in real world enterprise situations.  Why do you think TPM support has been added to the kernel?  It's because right not enterprise is where Linux is at, not the home desktop market.  And for all we know enterprise customers may well want or need TPM support.[/quote]More "open source" software than "free" software said:**
> Personally I would never buy DRM protected media.  But in your original argument this was one of your points for why TC would be de-facto mandatory on Windows.  My argument was that the same would be true in Linux.  The fact that most Linux users oppose DRM anyway, isn't a valid argument for why TC need not affect Linux, whilst it does affect Windows.I don't quite follow you; how exactly will it contribute to TC being a de facto mandatory in Linux, especially when, like you say, most Linux users oppose and do not use DRM? The most likely way in which TC will affect the FOSS world is the fact that it undermines the GPL, as stated in part 18 of the FAQ, even though a bit speculatively. 

[quote=Malphas]Well supposing that were true, it still would mean that the difference between using a closed-source/Windows solution or a Linux one would be irrelevant considering that open-source software is available for Windows as well.  So the exact same arguments would apply.[/QUOTE]Very wrong. Does the same amount and variety of open-source software as Linux/BSD exist for Windows? Are the Windows core components open source? Furthermore, open source does not necessarily mean free.

---

### Post by Malphas on 2005-11-30
You're going off on an unrelated tangent now.  What does the fact that GIMP came from the FOSS community have to do with your original assumption that Trusted Computing will only affect Windows?  This is the only thing I take issue with.  Personally I don't think that TC will affect Linux as much as Windows, but really it's hard to say how much effect it will have at all.  You were originally stating that in Windows TC will be mandatory whilst in Linux you'll simply be able to switch TC off and everything will work exactly the same as it did before.  Not only it is far too early to be making this kind of assumptions, but it's also complete garbage.  You're attempting to turn this into an open-source/free vs closed-source/proprietary debate, which isn't where we started out at all.  Equating Linux to free software and Windows to proprietary software only is a gross simplification of reality.  Like I already said, open-source software exists afor Windows and closed-source software exists for Linux.

---

### Post by 23meg on 2005-11-30
> **Malphas]You're going off on an unrelated tangent now.  What does the fact that GIMP came from the FOSS community have to do with your original assumption that Trusted Computing will only affect Windows?  [/quote]I only stated this because you presented GIMP as an example. It was a response to your argument, not part of my original argument. [quote=Malphas]You were originally stating that in Windows TC will be mandatory whilst in Linux you'll simply be able to switch TC off and everything will work exactly the same as it did before. [/quote]Please quote me saying this. Really, please do if I have said:**
> Not only it is far too early to be making this kind of assumptions, but it's also complete garbage.  You're attempting to turn this into an open-source/free vs closed-source/proprietary debate, which isn't where we started out at all.  I'm only responding to your arguments; I'm not trying to steer the discussion anywhere. And if you keep referring to my statements as garbage I'll have less of a motivation to discuss with you. [quote=Malphas]Equating Linux to free software and Windows to proprietary software only is a gross simplification of reality.  Like I already said, open-source software exists afor Windows and closed-source software exists for Linux.[/QUOTE]I did not do that equation; on the contrary I insisted on a clear separation of the terms "free" and "open source". I know there's open source for Windows, but is it comparable to the quantity and quality of the open source software that's available on open source platforms? I know there's proprietary in Linux but is it not outnumbered and mostly outperformed by open source alternatives?

---

### Post by poptones on 2005-11-30
*i must have thought it's obvious that non-commercial Linux software won't need to and shouldn't attempt to lock its user in via TC...*

There are countless (countless simply because we do not yet have this capability and so cannot imagine thre plethora of uses) for "locking in" people via tc **especially** in a free and open environment. Simplest example: tor. At present tor sets up multihop encrypted proxy chains. At any point in that chain a user can insert a hacked tor that allows eavesdropping on every packet. With a trusted architecture it would be possible to differentiate "trusted" proxies from untrusted. 

Similarly, cheating has been a problem in many of the distributed computing applications. Some have taken to distributing a hashed client but, especially with the recent advances in hash cracking, this is little meaningful security. Having a widely deployed trusted infrastructure would allow more cooperation between individuals in creating pooled computational resources of all varieties - from immersive games to virtual web server farms, the possibilities are vast.

*I know there's open source for Windows, but is it comparable to the quantity and quality of the open source software that's available on open source platforms?*

Show me the equivalent of avisynth for linux. Mplayer and mencoder are fantastic tools in their own right but are no match at all for the capabilities of avisynth. I've still not found a linux port of TomsMoComp deinterlacer, for example, which allows for professional quality deinterlacing/upsampling of conventional video.

---

### Post by 23meg on 2005-11-30
> **poptones]
There are countless (countless simply because we do not yet have this capability and so cannot imagine thre plethora of uses) for "locking in" people via tc **especially** in a free and open environment. Simplest example: tor. At present tor sets up multihop encrypted proxy chains. At any point in that chain a user can insert a hacked tor that allows eavesdropping on every packet. With a trusted architecture it would be possible to differentiate "trusted" proxies from untrusted.

Similarly, cheating has been a problem in many of the distributed computing applications. Some have taken to distributing a hashed client but, especially with the recent advances in hash cracking, this is little meaningful security. Having a widely deployed trusted infrastructure would allow more cooperation between individuals in creating pooled computational resources of all varieties - from immersive games to virtual web server farms, the possibilities are vast. [/quote]I'm not talking about practical non-evil uses said:**
> Show me the equivalent of avisynth for linux. Mplayer and mencoder are fantastic tools in their own right but are no match at all for the capabilities of avisynth. I've still not found a linux port of TomsMoComp deinterlacer, for example, which allows for professional quality deinterlacing/upsampling of conventional video.I can make countless specific cases starting with "Show me the Windows equivalent of.." but I don't need to take this further off topic since it must be obvious that we're talking in general terms here.

---

### Post by poptones on 2005-11-30
Then why did you ask the question in the first place? If it is off topic then it is you who led us there...

*I know there's open source for Windows, but is it comparable to the quantity and quality of the open source software that's available on open source platforms?*

There is **zero** software in linux that can replicate this functionality - and it will remain thus until gstreamer has matured considerably from present. That isn't a small gap - it's the difference between "I can sorta do this" and "I can't do that **at all**."

How do you differentiate "non evil" from "evil?" The same way you differentiate "ignorant" from "informed?" By *opinion*? 

How is Sony locking up Alicia Keys inside a DRM platform that the user has willingly purchased with their own money (ie PS3 video, DVD or TCPA-compliant application) more evil (or eveil at all) compared to Sony hacking people's computers... computers that, because of their inherent design, are *incapable of detecting or preventing such intrusions?*

---

### Post by 23meg on 2005-11-30
> **poptones]Then why did you ask the question in the first place? If it is off topic then it is you who led us there...[/quote]Sometimes people use the question form of speech even when they're not really asking a question, but stating a fact they're confident about, as was the case here. In more straight terms, I wasn't asking a question said:**
> 
There is **zero** software in linux that can replicate this functionality - and it will remain thus until gstreamer has matured considerably from present. That isn't a small gap - it's the difference between "I can sorta do this" and "I can't do that **at all**."
Again specifics, again off-topic. If you'd like to discuss these points, please open an appropriately titled thread.
[quote=poptones]How do you differentiate "non evil" from "evil?" The same way you differentiate "ignorant" from "informed?" By *opinion*? [/quote]You almost hit it, by opinion and ideology. I reserve my right to speak against what I find evil, and I find unethical commercial applications of TC by TCPA member companies, as well as the overall ownership paradigm TC brings evil, and I speak against them.

[quote=poptones]How is Sony locking up Alicia Keys inside a DRM platform that the user has willingly purchased with their own money (ie PS3 video, DVD or TCPA-compliant application) more evil (or eveil at all) compared to Sony hacking people's computers... computers that, because of their inherent design, are *incapable of detecting or preventing such intrusions?*[/QUOTE]If you mean the Sony rootkit case, I see your point, neither is more or less evil than the other. I'm not necessarily saying "ALL TC IS EVIL"; but  I find both of your examples evil and wouldn't buy into either.

---

### Post by hizaguchi on 2005-11-30
Alot of what ya'll are saying is over my linux newbie head.  I read the FAQ and the conversation going on here, and what I'm getting is that the whole TC thing is basically going to screw over interoperability of Windows and anything else... for all I know maybe even old Windows programs and new ones, either in favor of security or monopoly (probably both).  There's the free speech and fair use stuff too, but interoperability is the issue that most people are going to notice.  So where does that put those of us who don't like this idea, say, 10 years from now?  Our office productivity software won't be compatable with other people, rendering it useless unless we are fortunate enough to only communicate with non-TC users?  We can't listen to our own CDs or watch our own DVDs on our own computers, even if we purchased them legally?  What can be done about all of this?  Is it going to be a situation where you either give in to TC (and thus give up your freedoms) or deal with having the functionallity of your computer eliminated?  Is there anything else that can be done?

---

### Post by blastus on 2005-11-30
TCPA is a consortium of many companies including Intel, AMD, IBM, Sun, Novell and others--not just Microsoft. NGSCB (a.k.a Palladium) is Microsoft's proprietary platform that will eventually make its way into Windows. Microsoft is the ONLY company that would be delighted if TCPA closed the hardware platform so that it can only run a NGSCB Windows OS and NGSCB application software. Essentially we would have "winhardware" to the exclusion of everything else. But that's not gonna happen. TCPA is not controlled by Microsoft and you can take it to the bank that IBM, Sun, Novell and the other Linux-friendly companies would never consent to such madness. IBM already has an open source GPL driver for the TCPA Fritz chip for Linux, and Sun is working on an open source GPL platform for DRM.

That said, what Microsoft does with TCPA and their proprietary NGSCB is their own business. But they are trying to market NGSCB as a panacea to the problems with Windows security such as spyware, viruses and all kinds of crap. They even changed the name from Palladium to NGSCB because of the bad publicity. Goto Microsoft's NGSCB website and they say that NGSCB will "help customers realize their full potential"--whatever that means. Really their marketing campaign is just a front.

I predict Microsoft will use TCPA and their NGSCB to further lock users into Windows and strip Windows users of their "rights." Microsoft, their partners, and the entire Windows software industry will gain more control over who uses their software and how users use their software. Microsoft's NGSCB will put the control into the hands of Windows software vendors to limit the use of their software, possibly expire software, and all kinds of funky stuff.

I liken Microsoft's NGSCB to a frog in a pot of hot water. The frog is a Windows user and Microsoft is trying to increase the temperature of the water so that the frog can "realize its full potential." But unlike the real world, increasing the temperature of the water makes it more difficult for the frog to get out of the pot. The frog may feel uncomfortable at first but then he gets used to it. So too I predict that Microsoft's NGSCB will be met with much opposition, but eventually Windows users will accept it just like they accepted Windows Product Activation, the binding of Internet Explorer to Windows, and other insanity from Redmond. 

Microsoft has a monopoly on desktop operating systems, and because of that monopoly they can unilaterally foist whatever they want on the world--the Windows world. All they have to do is bind, bundle, or integrate whatever they want into Windows and eventually over 90% of the world's desktop computers will be exposed to it. So they will likely succeed in pushing their NGSCB onto the Windows world. Microsoft's Palladium/NGSCB was one of the reasons I switched to Linux. The way I see it, there is a high potential for abuse. Whether Windows vendors take advantage of the system and abuse it is irrelevant.

All this really doesn't affect us Linux users except maybe when it comes to DRM and multimedia I'm not sure. I don't think anyone really knows yet. This is one of the reasons why we really have to push for the creation, development, improvement, and adoption of open standards and open formats for all kinds of data.

---

### Post by Malphas on 2005-11-30
But in actuality I really think that Trusted Computing isn't going have as much impact as people previously predicted, at least not in the medium term.  Microsoft have had to scale back a lot of the TC they had planned for Vista due to technical limitations.

---

### Post by poptones on 2005-11-30
This is why you'll never gain any headway: because you state lots of stuff as if it's "fact" when it is easily disproven as such. Then you insist **freedom and choice are evil**. 

Not going to make many points like that. Perhaps your "ideology" would meet a more receptive audience from the sabbath pulpit.

*If you mean the Sony rootkit case, I see your point, neither is more or less evil than the other. I'm not necessarily saying "ALL TC IS EVIL"; but I find both of your examples evil and wouldn't buy into either.*

Do you have decss on your pc? Any ripped Hollywood programs or films? Do you have any Warner or Sony DVDs? How about Disney, Miramax, or any of those subsidiaries? Do you have a videogame system? Unless you can honestly answer no to all these questions then why are you supporting something that is, by your ethic, "evil?"

Evil and good are for religious zealots. Do you have any *objective* rationale at all for objecting to tcpa?

---

### Post by Malphas on 2005-11-30
I don't believe in good and evil but I'm most certainly opposed to Trusted Computing, mainly because I find things like DRM, copyright protection and product activation a nuisance.

---

### Post by 23meg on 2005-11-30
> **poptones]This is why you'll never gain any headway: because you state lots of stuff as if it's "fact" when it is easily disproven as such. Then you insist **freedom and choice are evil**. [/quote]Where have I stated that freedom and choice are evil? And what did I state as a fact that has been disproven?
[quote=poptones]
Not going to make many points like that. Perhaps your "ideology" would meet a more receptive audience from the sabbath pulpit.[/quote]I've stated my reluctance to discuss ideological matters with you multiple times in different threads said:**
> 
Do you have decss on your pc? Any ripped Hollywood programs or films? Do you have any Warner or Sony DVDs? How about Disney, Miramax, or any of those subsidiaries? Do you have a videogame system? Unless you can honestly answer no to all these questions then why are you supporting something that is, by your ethic, "evil?"I can honestly answer no to all those questions. I just bought two Sony CDs a few weeks ago (by local artists, on a local branch of Sony) and when I couldn't play them on Breezy, I gave them back and got a full refund after some debate. 

Even if I couldn't answer all those questions with a confident "no", even if I had bought hundreds of Sony or Warner or whatever CDs/DVDs, what would matter would still be that I have the awareness that these companies are "evil" now. I won't buy their products, period. I'm quite clear and straight edge here, and I've expressed this attitude elsewhere as well. And I know very well that I'm not alone.

> **popt&#305 said:**
> Evil and good are for religious zealots. Do you have any *objective* rationale at all for objecting to tcpa?I'm not using the word "evil" in the religious or fanatic sense, which again should have been obvious. And I'm not a fan of objectivity either; I don't believe such a thing as objectivity is possible. Note that all views I have expressed are subjective. I've always spoken just for myself.

---

### Post by poptones on 2005-11-30
*Where have I stated that freedom and choice are evil?* 

Here:

*How is Sony locking up Alicia Keys inside a DRM platform that **the user has willingly purchased with their own money** more evil (or evil at all) compared to Sony hacking people's computers... computers that, because of their inherent design, are incapable of detecting or preventing such intrusions?*

You stated categorically that you would define "both" these behaviors as "evil." 

I have the right to **publish** any damn thing I see fit in any manner I see fit. It is no one's concern so long as I do not violate the physical person or property of others in doing so. That is my "opinion." You either believe in freedom of speech or you do not... apparently such *freedom* is, to you, "evil."

*...I just bought two Sony CDs a few weeks ago (by local artists, on a local branch of Sony) and when I couldn't play them on Breezy, I gave them back and got a full refund after some debate.*

This debate is far more than a mere two weeks old. Yet you willingly purchased Sony CDs and returned them only because you couldn't play them on your computer.... how many *other* Sony music CDs do you own? Do you even know what labels they own? And what difference does it make if it is a local artist or not? The artist could live next door to you, that wouldn't make Sony any less (to use your own terminology) "evil."

---

### Post by 23meg on 2005-11-30
[QUOTE=poptones]
You stated categorically that you would define "both" these behaviors as "evil." [/quote]I stated that I find Sony's act evil, not that of the purchaser. Note how you made that sentence: "Sony locking up Alicia Keys inside a DRM platform". I merely state that I won't be the purchaser. You can publish it however you please; as long as you're Sony, I'm no longer your customer.

---

### Post by Malphas on 2005-11-30
But Sony's rootkit fiasco was violating other people's property surely?  By making their computers less secure.

---

### Post by 23meg on 2005-11-30
[QUOTE=poptones]This debate is far more than a mere two weeks old. Yet you willingly purchased Sony CDs and returned them only because you couldn't play them on your computer.... how many *other* Sony music CDs do you own? Do you even know what labels they own? And what difference does it make if it is a local artist or not? The artist could live next door to you, that wouldn't make Sony any less (to use your own terminology) "evil."[/QUOTE]
I'm quite sensitive on what I buy; I know what labels Sony and the other big boys own and I won't buy from them either, don't worry about me. But this isn't about me or someone else being 100% RIAA-free, as I stated. You could have a thousand Sony CDs, and have just become aware of Sony's "evil"ness and decided not to buy from them again, and I'd respect your stance the same way I'd respect the stance of someone who has no Sony CDs and won't buy any. We're not born with ethical awareness, we gain it.

The artists being local makes no difference in terms of feeding Sony; it's just that local CD's are one fourth of the price of foreign ones, so it was a bit more convenient for me. I bought the CDs, and I had a reason for so doing: I wanted to see whether all the hype about copy protection crippling Linux players and rippers was true first hand. I knew I could somehow get a refund and not feed Sony in the end. And it turned out that I was totally unable to play the CDs or rip them under Breezy, Mepis and SLAX, and I could only play them in Windows if I was connected to the internet.

---

### Post by poptones on 2005-11-30
*I stated that I find Sony's act evil, not that of the purchaser. *

If Sony is "evil" in their action then how can the consumer NOT be "evil" in lending support, through their purchase, to this "evil" act?

Keep trying to cop out... you'll get it eventually.

---

### Post by poptones on 2005-11-30
*But Sony's rootkit fiasco was violating other people's property surely?*

Of course it was... just as ripping an *encrypted* Alicia keys dvd to your hard drive is a violation of *Sony's* property...

---

### Post by Malphas on 2005-11-30
Is it though?  When I fork out for a DVD I consider it my property (within reason), I know in the eyes of the law the DMCA now over-rules this (were I living in the US), but I consider it corrupt and would also consider it a violation of my fair-use rights (again, were I living in the US).  We have the EUCD and fair-dealing equivalents but they're not as clear cut.  Obviously distributing pirate copies is going too far but I feel I should be entitled to make a backup of the media that I've paid for, right now the law is tilted far too much in favour of the copyright holder rather than the consumer.

---

### Post by poptones on 2005-11-30
*Is it though? *

Yes, it is.

---

### Post by Malphas on 2005-11-30
Under US law and your opinion.  Not in mine.

---

### Post by poptones on 2005-12-01
ROTFL. Well, I guess that makes you wrong...

---

### Post by Malphas on 2005-12-01
Why?  Decrypting a DVD is perfectly legal in many countries outside the US.

---

### Post by poptones on 2005-12-01
Since when is legality the benchmark of right and wrong?

---

### Post by mdsmedia on 2005-12-01
[QUOTE=poptones]*I stated that I find Sony's act evil, not that of the purchaser. *

If Sony is "evil" in their action then how can the consumer NOT be "evil" in lending support, through their purchase, to this "evil" act?

Keep trying to cop out... you'll get it eventually.[/QUOTE]

Keep trying to drill this down to a single word making someone guilty of some obscure crime or evilness. You're almost there.

---

### Post by mdsmedia on 2005-12-01
[QUOTE=poptones]ROTFL. Well, I guess that makes you wrong...[/QUOTE]

Since when is US law the definition of right or wrong?

---

### Post by Malphas on 2005-12-01
[QUOTE=poptones]Since when is legality the benchmark of right and wrong?[/QUOTE]
Well it's either a legal or moral issue, and so if you're saying it's not a legal issue it must come down to morals - which are relative.  For someone who critised someone else for talking in terms of good and evil it's rather hypocritical of you to then start talking in terms of "right and wrong" (which isn't too far away from just saying "good and evil") and asserting that your definition of what's moral is the only correct one and anyone else's moral stance is just outright "wrong".  It's hard to take anything you say seriously if you're going to contradict yourself so blatantly.

---

### Post by 23meg on 2005-12-01
[QUOTE=poptones]*I stated that I find Sony's act evil, not that of the purchaser. *

If Sony is "evil" in their action then how can the consumer NOT be "evil" in lending support, through their purchase, to this "evil" act?

Keep trying to cop out... you'll get it eventually.[/QUOTE]If you read the rest of the sentence as well, you'd see that **I** insist on not taking part in this "evil" act by buying Sony's goods. The very reason I'm not calling someone else's act of buying "evil" is that I respect their decision to do so, which debases your main concern about my "morality".

---

### Post by poptones on 2005-12-01
Man, you give yourself waaaay too much credit. I'm not at all "concerned" about any morality you may or may not imagine yourself to have. I'm simply pointing out the obvious hypocrisy in your statements. By casting a *corporation* as "evil" you are also making a statement about those who work for the corporation and those who purchase goods from it. You can backpedal all you like, but the street has two sides and there's a curb waiting to trip you up on both of them.

---

### Post by 23meg on 2005-12-01
[QUOTE=poptones] By casting a *corporation* as "evil" you are also making a statement about those who work for the corporation and those who purchase goods from it. [/QUOTE]I'm not casting the corporation as "evil"; just read the sentences. I'm saying that Sony's ACT is "evil" (and not "SONY = EVIL") and that I won't buy from them again because of this act. And I couldn't care less what you do or what someone else does about this; I'm just speaking for myself. 

Like just about every thread you post to, this one has degenerated to personal debates focused on the attitudes and of certain persons and specifics you try to zoom in on to ignore the overall case being made. I've answered the original poster's question, my discussion with Malphas is over, so I'm out of this thread as well. And I won't respond to anything you post once again anywhere in these forums. Forgive the one and only personal statement I'll ever make about you, but I find it impossible to discuss with you, since you seem totally unwilling to consider let alone accept any opposing opinion but just restate those of your own in different ways, and attack individuals by taking their certain statements out of context.

---

### Post by poptones on 2005-12-01
Duuuude... if you want someone to *consider* your opinion then you might try stating some *sound basis* for that opinion. All you did was keep saying "this is my opinion" and "this is how it is." At that point there's nowhere to go BUT "personal" because you're stating nothing but *beliefs*; you are **making the discussion personal** and then bitching about someone obliging you in your endeavour.

---

### Post by david_e on 2005-12-30
Look @ this:

> Let's look at spam first. There has been plenty of research on techniques to automatically reject spam e-mail or restrict the ability of spammers to generate it in the first place. These techniques include the following:
•	

Simply rejecting e-mail that isn't authenticated or digitally signed with a "validated" identity (which would block all anonymous e-mail, including desired anonymous e-mail)
•	

Forcing spammers to perform some nontrivial computation for each message they wish to send
•	

Maintaining per-user lists of approved and nonapproved senders
•	

Scoring every inbound e-mail message using heuristics that look for common characteristics of spam messages

Systems built on NGSCB architecture could certainly be used to improve signing-required or computation-required regimes, compared with what is possible today on conventional hardware (the latter is probably more interesting because NGSCB provides facilities that could allow a sender to prove to a recipient that the sender performed a particular computation within the nexus-aware environment.) Clearly, the realm of possibilities for antispam measures on PCs designed to the NGSCB architecture is a topic deserving of further study.

With respect to viruses, the contribution from the NGSCB architecture is more straightforward. Since the nexus and NCAs do not interfere with the operation of any program running in the regular Windows environment, everything, including the native operating system and viruses, runs there as it does today. Therefore, users are still going to need antivirus monitoring and detection software in Windows as well. However, the NGSCB architecture does provide features that can be used by an antivirus program to help guarantee that it has not been corrupted. The antivirus software can be grounded in such a way that it can bootstrap itself into a protected execution state, something it cannot do today

Is taken from:
[http://www.microsoft.com/technet/archive/security/news/ngscb.mspx](http://www.microsoft.com/technet/archive/security/news/ngscb.mspx)

They say that this software is designed only to improve computer security, but look at the features of NGSCB. It's absolutely [SIZE="4"][COLOR="Red"]useless[/COLOR][/SIZE].... This NGSCB will do...something that can already  be done!

---

