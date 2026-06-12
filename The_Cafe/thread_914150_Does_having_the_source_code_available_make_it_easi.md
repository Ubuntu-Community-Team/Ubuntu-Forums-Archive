---
title: "Does having the source code available make it easier for crackers?"
date: 2008-09-08
forum: The Cafe
---

### Post by aysiu on 2008-09-08
And, if so, does the security of open source depend solely on whether the "white hats" for any given software outnumber the "black hats"?

I've often heard it this way:
[quote=Anti-open source person]If hackers [meaning malicious parties, not people who just hack code for fun to tweak things] can see the source code, it's easier for them to discover and take advantage of vulnerabilities.[/quote]

[quote=Pro-open source person]But having the code open source means that there are millions of eyes examining it for vulnerabilities and patching them accordingly.[/quote] So my questions are:

1. Is what the first person says true? Is it, in fact, easier to discover vulnerabilities in open code?

2. Is what the second person also says true? Are there really that many non-malicious parties looking also at the code to patch vulnerabilities?

3. How do malicious parties find vulnerabilities in closed source software? Trial and error? Reverse engineering?

I know from experience that open source is not more vulnerable than closed source software (if anything, I've seen the opposite), but it doesn't make logical sense to me.

If I want to discover a vulnerability in a house, wouldn't I benefit from having its architectural blueprints?

---

### Post by billgoldberg on 2008-09-08
That's a good question.

I have been wondering the same for some time.

But experience tells me open source is safer.

---

### Post by aysiu on 2008-09-08
> **billgoldberg said:**
> 
But experience tells me open source is safer. Same here. But I'd like to know if it is...

1. Having the source code is irrelevant. It's equally easy to find vulnerabilities with and without the source code.

or

2. Having the source code makes it easier to exploit vulnerabilities, but it's off-set by the efforts of people patching those vulnerabilities.

or both. Or something else entirely.

---

### Post by GeneralZod on 2008-09-08
> **aysiu said:**
> Same here. But I'd like to know if it is...

1. Having the source code is irrelevant. It's equally easy to find vulnerabilities with and without the source code.

or

2. Having the source code makes it easier to exploit vulnerabilities, but it's off-set by the efforts of people patching those vulnerabilities.

or both. Or something else entirely.

Anecdotally: I've seen someone spot a flaw and craft an obscure exploit (the kind one would be very unlikely to dream up without the source) within a few minutes of being shown it, purely through static analysis of the source code.  So I'd definitely dispute 1.  He also shared the flaw and its cause, so this also supports 2.  So I'll throw in a vote for "both" :)

---

### Post by p_quarles on 2008-09-08
> **aysiu said:**
> 1. Is what the first person says true? Is it, in fact, easier to discover vulnerabilities in open code?
Yes. That, of course, doesn't in any way make those vulnerabilities easier to exploit, but it does mean that more people are capable of patching them.

> 2. Is what the second person also says true? Are there really that many non-malicious parties looking also at the code to patch vulnerabilities?
Yes. Given the amount of open source code which is central to the internet's infrastructure, it's guaranteed that certain projects will get an abundance of attention. 

Projects that are less important to the business world will probably have fewer eyeballs. That is equally true, though, of closed-source software.

> 3. How do malicious parties find vulnerabilities in closed source software? Trial and error? Reverse engineering?
Both of those things, as well as social engineering and brute force. 

Encryption is a good analogy. A good algorithm can be known by all and completely uncrackable. A bad one can be unknown but easily broken by a statistical analysis program. Given the amount of computing power available to those who want to use the internet for criminal enterprises, brute force and social engineering are the things one really has to worry about. For the latter, education is the only solution. For brute force attacks, however, it has been well established that obscurity only prolongs the attack, and does not prevent it from succeeding in the end.

---

### Post by KillerSponge on 2008-09-08
I read an article a couple of weeks ago about the numer of critical bugs in browsers. IE had the most, then came FF, and after that Opera. Out of these three, only FF is open source. Both IE and Opera are closed source. 

From this you could conclude that it doesn't really matter if the program is open source or not. I'm not sure about this (maybe the number of _known_ bugs has more to do with the browser popularity?), but it might give some insight :)

---

### Post by drubin on 2008-09-08
> **aysiu said:**
> And, if so, does the security of open source depend solely on whether the "white hats" for any given software outnumber the "black hats"?

Your first comment answers a lot I think. Are they submitting bug fixes faster then users can write expliots for. 

Where as with the closed source alternatives once a security flaw is found it takes weeks for a fix to be released. 

Also with open source applications the bugs are often found before the full release is made with the advanced users taking a peak at the source code of the newly written software (mostly out of interest and learning).

It reminds me of when the Debian random bug was recovered that affected the validity of certificates. a patch was released with in hours... Would some one even answer a report with in days on the closed source system?

---

### Post by Dr Small on 2008-09-08
The attacker who has the source code and can modify it, does not endanger the user who runs the software, because the attacker can only change his code. Of course, he can view the source, but if it was programmed securly, viewing it will not do anything. Of course, an attacker can edit his source code and create a vulnerbility in it, but this doesn't do anything for the user who is running it.

Ultimately, if a cracker has the source, it does not enable his to weild his mighty mystical sword of destruction upon those who use that program. Experience has proven this to us. Having something opensource allows the community to report bugs, fixes and patch any holes faster than any Microsoft team can.

Having opensource does enable a cracker to search the source code for holes, and if he finds one, tests it, and it works, he has found a hole. But crackers generally don't like to keep secrets to themselves for very long. The hole will become public for other crackers, or he will sell it. The opensource community hears about it, studies the exploit and patches it within days of it's release.

Does having the source code make it easier for crackers? Well, in a sense, but it surely doesn't last long. I believe opensource is more secure.

---

### Post by clanky on 2008-09-08
Very interesting, I think there is probably some truth in both arguments, in reality how many people actually scrutinise the source code looking for security vulnerabilities?

---

### Post by p_quarles on 2008-09-08
> **rubinboy said:**
> It reminds me of when the Debian random bug was recovered that affected the validity of certificates. a patch was released with in hours... Would some one even answer a report with in days on the closed source system?
That's kind of a bad example of the effectiveness of the open source model. In reality, that "bug" was the result of an extremely sloppy patch that should never have been applied, and would not have been applied by anyone who fully understood the code in question. 

Personally, I don't buy the line that such problems are unique to open source or community-based development. It was a result of poor organization and delegation, which can happen as easily in a corporate environment. But it's certainly not an example of open source succeeding at something. 

As for the speediness of the patch, I would point out that it was in fact *not* released to the public immediately. The maintainer who discovered the flaw was (appropriately) secretive about it until a patch could be issued. Moreover, the time it took to actually apply the patch was immense.

---

### Post by drubin on 2008-09-08
> **p_quarles said:**
> That's kind of a bad example of the effectiveness of the open source model. In reality, that "bug" was the result of an extremely sloppy patch that should never have been applied, and would not have been applied by anyone who fully understood the code in question.

Maybe it was not the greatest example.... I should have researched that a bit more before posting it.

---

### Post by koenn on 2008-09-08
> **aysiu said:**
> Same here. But I'd like to know if it is...

1. Having the source code is irrelevant. It's equally easy to find vulnerabilities with and without the source code.

or

2. Having the source code makes it easier to exploit vulnerabilities, but it's off-set by the efforts of people patching those vulnerabilities.

or both. Or something else entirely.

It's both, and something else entirely. 

Having access to source could makes it easier to find exploitable flaws, but if those flaws get exploited, they're also exposed, so the good guys find out about them and get them fixed.
 
So it's not really a matter of whether the good guys outnumber the bad guys. The bad guys serve as testers that "submit bug reports" in the form of exploits.  That they can do this faster than with closed source,  helps speed up the "bug" fixing process, and contributes to the overall quality of the code : more flaws fixed, less exploitable flaws remaining. 

Of course,  having source available to many programmers helps to get the fixes developed fast. And there's always a change of a flaw being discovered (by one of the good guys) before it gets exploited. 
Throw all of that together, and you can probably safely assume that open source is less exploitable, generally speaking.

---

### Post by aysiu on 2008-09-08
Thank you all for your insights. This discussion has been helpful to me as a non-programmer.

If others have further insights, I'd like to read those as well.

---

### Post by Lostincyberspace on 2008-09-08
Open source also has the advantage of being a community effort and most contributions to code are reviewed by others writing code for the same project, either that day or the next few days, before the public release. Checking to see about various things and most large bugs, defects, and what ever other problems are fairly easy to spot and are fixed before it is even released.

---

### Post by Hilipatti on 2008-09-08
What I like to think, is that:

The open-source programmers do it for fun and their own good and they want to use the results themselves and nobody is rushing them to do anything, they make the software the way they want to, on their own schedule, for fun.

Corporate programmers are on a tight clock, they have to show results. Corporate policies affect the way they may or may not program software. They do not do software just for the joy of it. They do not make software because they want software that does a task for them. I guess there might also be some bozo that thinks something should be done in some way that isn't necessarily the best but the programmers aren't calling the shots.

Corporate programmers also have additional issues to worry about. They have the UI department that wants a pretty-pretty GUI, it doesn't matter if it will actually work, they want it their way. You have to use some specific stuff because you need DRM etc.

I think that affects the final end result, atleast in terms of pure software. On the other hand, open source programmers can just focus on making good quality software that works.

I think that is a reason why open source software will always be better than the corporate choice. There's no other interests mixed in, you only want to make software. Of course open source software has release schedules too, sometimes, and I think it isn't a good thing because it may affect the end result, the software quality. 

Which is why I think open source people should ditch the strict release dates and release stuff when it's ready. That way your software won't be full of bugs and it will be awesome. There's no need to cave in to pressure from the people, since you have to protect the people from themselves (by not releasing bad software even though they want it.)

I hope you catch my drift, I feel like I couldn't really translate my thoughts into words properly. Atleast I feel like that. I'm not a programmer either so I have no idea what I'm talking about, but I have this idea :P
This post doesn't really have much to do with the subject either, I guess.. This would fit better in some sort of "corporate vs open source programming".

I guess I could summarize it by saying that "it's a bad idea to mix other interests into making software because it affects the software quality".

---

### Post by p_quarles on 2008-09-08
> **Hilipatti said:**
> What I like to think, is that:

The open-source programmers do it for fun and their own good and they want to use the results themselves and nobody is rushing them to do anything, they make the software the way they want to, on their own schedule, for fun.

Corporate programmers are on a tight clock, they have to show results
That's a false dichotomy, though. Open source and corporate programmers are the same people, more often than not. Moreover, while I imagine that many programmers (both open source and closed source) enjoy their jobs, I still think that most programming is purpose-driven rather than just for kicks. 

This always needs to be said here, it seems, but: open source is *not* the opposite of commercial, corporate, or entrepreneurial. It the opposite of closed source, and nothing else.

---

### Post by aysiu on 2008-09-08
And to further p_quarles' point, there are a lot of closed source projects that have no corporate backing.

---

### Post by david_lynch on 2008-09-08
How about an analogy? Let's say you're a crook, looking to make a quick buck from a house robbery. Let's say there are two houses you could break into. House A is an open source unix OS, house B is ms windows.

You have access to the information for house A, so you know that behind the electric fence, there is a 20 foot wide moat filled with crocodiles. Inside the moat, there is another electric fence, and the yard inside the fence is patrolled by pit bulls. The windows in the house are all facades - behind them are the same 3 foot thick concrete walls as everywhere else. multiple video and infrared cameras provide a view of the outside world. There are also pit bulls inside the house. The front and back doors are military grade steel. The intrusion detection system inside the house will have a swat team onsite within 90 seconds.

You don't know anything about house B, but you do know that in the last year, it has been burglarized 67 times by various parties, and in each case they were able to make off with whatever they wanted, in broad daylight, and were never caught.

So, which house do you want to rob? the one where you know the layout, or the one where you don't know the layout, only that it's apparently very easy to break into?
:lolflag:

---

### Post by Hilipatti on 2008-09-08
> **david_lynch said:**
> How about an analogy? .... 

That's called [Security through obscurity, clicky]("http://en.wikipedia.org/wiki/Security_by_obscurity") :P

[QUOTE=p_quarles]That's a false dichotomy, though. Open source and corporate programmers are the same people, more often than not. Moreover, while I imagine that many programmers (both open source and closed source) enjoy their jobs, I still think that most programming is purpose-driven rather than just for kicks.

This always needs to be said here, it seems, but: open source is not the opposite of commercial, corporate, or entrepreneurial. It the opposite of closed source, and nothing else.[/QUOTE]

Well yeah, that's true. I guess my main point was that additional interests aren't good and I'd imagine that would happen (more often) with closed source, company driven commercial? software.

---

### Post by aysiu on 2008-09-08
> **david_lynch said:**
> How about an analogy? Let's say you're a crook, looking to make a quick buck from a house robbery. Let's say there are two houses you could break into. House A is an open source unix OS, house B is ms windows.

You have access to the information for house A, so you know that behind the electric fence, there is a 20 foot wide moat filled with crocodiles. Inside the moat, there is another electric fence, and the yard inside the fence is patrolled by pit bulls. The windows in the house are all facades - behind them are the same 3 foot thick concrete walls as everywhere else. multiple video and infrared cameras provide a view of the outside world. There are also pit bulls inside the house. The front and back doors are military grade steel. The intrusion detection system inside the house will have a swat team onsite within 90 seconds.

You don't know anything about house B, but you do know that in the last year, it has been burglarized 67 times by various parties, and in each case they were able to make off with whatever they wanted, in broad daylight, and were never caught.

So, which house do you want to rob? the one where you know the layout, or the one where you don't know the layout, only that it's apparently very easy to break into?
:lolflag:
That's actually an interesting analogy, david_lynch. I like it.

---

### Post by oedipuss on 2008-09-08
I agree with david_lynch above, but there's also one more thing. Open source software is designed with the knowledge that it can be scrutinized for exploitable bugs, and I think takes greater consideration to not have any, or to create a system where this transparency does not matter. On the contrary , closed source software can and often does rely on security by obscurity. 
I remember a fuss some time ago, when EVE-online source code was leaked, and there was a "bug" in the in-game browser that allowed a crafted link to run ANYTHING locally on your pc. Including deltree -yes -imsure for example.  The programmers clearly thought that since no one is going to see it, it won't be exploited. (It wasn't, but I believe it's rather because no one thought it possible :P )

edit: too slow XD

---

### Post by lukjad on 2008-09-08
Here is my two cents worth. Having something open source does two things. It makes more people look at the code and it makes more people play with the code. 

Now, a person who is like I am, likes to look at things as I am curious. I like to find holes in a system, that is my idea of fun. (Sadly, I am not a programmer... yet.) But I don't want to break the law and look at the code. 

Let's say someone else's conscience is willing to let them do so. Well, even if they find a vulnerability in the code, who is he going to tell? The company? He can't do that. He would (possibly) get in trouble. So he says nothing. 

Next, someone who is a cracker doesn't care about the laws and sees the same vulnerability in the code. He turns around and exploits is. Meanwhile the company who made it is trying to figure out what the vulnerability is and how to patch it. Also, there is a tendency for people to not see their own errors. The more people looking, the more viewpoints there will be.

---

### Post by clanky on 2008-09-08
> **lukjad007 said:**
> Here is my two cents worth. Having something open source does two things. It makes more people look at the code and it makes more people play with the code. 

Now, a person who is like I am, likes to look at things as I am curious. I like to find holes in a system, that is my idea of fun. (Sadly, I am not a programmer... yet.) But I don't want to break the law and look at the code. 

Let's say someone else's conscience is willing to let them do so. Well, even if they find a vulnerability in the code, who is he going to tell? The company? He can't do that. He would (possibly) get in trouble. So he says nothing. 

Next, someone who is a cracker doesn't care about the laws and sees the same vulnerability in the code. He turns around and exploits is. Meanwhile the company who made it is trying to figure out what the vulnerability is and how to patch it. Also, there is a tendency for people to not see their own errors. The more people looking, the more viewpoints there will be.

In reality how many people outside of the development team would actually look at the source code, with the ability to find security vulnerabilities and report them for a piece of software?  Or for an OS?

---

### Post by swoll1980 on 2008-09-08
Can't Windows binary be converted back to source?

---

### Post by Tomosaur on 2008-09-08
I would say that the real benefit in terms of security is that the system for fixing bugs is fundamentally different within FOSS projects than it is for proprietary code.

When a serious security flaw is found within an open-source project, the offending code is patched as soon as somebody writes the patch (usually very, very quickly). This can happen at the distribution level, and then work upstream, so the bug is fixed 'from the bottom up'.

In a proprietary project, when a security flaw is discovered, the 'owner' of the code does everything within their power to keep the information from leaking while they work on a patch (and this is usually done by developers who will work on the code during their working day, and can be impeded by other goings-on within their working environment, and just the general system they have to work with). Then, the patch might be withheld until some specific release date, even if the patch addresses a security problem. Then you need people to take notice of the patch announcement and update their software. This is a 'top-down' method.

The bottom-up method is much quicker at addressing issues as they arise, because there are no real requirements other than the patch must fix something without breaking anything (or at least, not much) else. The top-down method is slow and prone to delays, often brought about by the inefficiencies of business.

---

### Post by p_quarles on 2008-09-08
> **swoll1980 said:**
> Can't Windows binary be converted back to source?
As I understand it, that would be kind of like un-digesting your food. Reverse engineering a binary could get you something *like* the source code, but it's not going to be exact.

---

### Post by SunnyRabbiera on 2008-09-08
The thing is that most people who crack and break software actually use open source software to do it, the appeal for hackers and crackers goes down I feel for open source software.

---

### Post by lukjad on 2008-09-08
> **clanky said:**
> In reality how many people outside of the development team would actually look at the source code, with the ability to find security vulnerabilities and report them for a piece of software?  Or for an OS?
I am interested in computers in a big way. Eventually I hope to be a programmer. With or without the source code the crackers can still get access to vulnerabilities. I also remember reading that most of the crackers out there only use the code of others. That means that they don't actually know what they are doing (according to this article). So, while I see that there may be a greater risk in detection of a flaw, there is also a greater chance in the detection and reparation of the flaw.

I have an analogy if you will permit me. It's like a building. If you don't have anyone in the building other then a couple of security guards, then after they are bypassed or overrun, there is no one left to sound the alarm. If you let people use the building and walk around, then even if there is a break in people will probably be able to call the police on their cell phone. Also, even if the thieves come in to "case the joint", there will still be others that will have come in and looked at the security system for holes before. I have done this (the looking, not the casing). 

Now, the problem is that while there are few people in the real world that know, or even care about the security system, the people who are on the Internet are more likely to know something about programming. And in a regular building, you usually cannot go up to the manager and tell him of the security flaw. On the Internet you can.

---

### Post by happysmileman on 2008-09-08
Both, but there will generally be more "good guys" than "bad guys" looking at the code of an open source project, so generally it would be safer.

With closed source software you still have "bad guys" looking for exploits, but NO "good guys" looking to help the security (outside the developers who have access to the code).

EDIT: Yeah "bad guys" and "good guys" makes it a lot easier to explain it, so I use those terms

---

### Post by Dr Small on 2008-09-08
> **lukjad007 said:**
> I also remember reading that most of the crackers out there only use the code of others. That means that they don't actually know what they are doing (according to this article).

These n00bz are called 'scriptkiddies'. They don't write they own code, they just run an exploit that someone else wrote. Thus, they run the scripts and generally have no idea what they are doing.

---

### Post by p_quarles on 2008-09-08
> **Dr Small said:**
> These n00bz are called 'scriptkiddies'. They don't write they own code, they just run an exploit that someone else wrote. Thus, they run the scripts and generally have no idea what they are doing.
And, it should be pointed out, aren't the ones anyone is really worried about. The ones to worry about are the types of people that run the storm botnets and things like that. In other words, criminals in it for big money, and not just bored kids.

---

### Post by cardinals_fan on 2008-09-08
> **p_quarles said:**
> And, it should be pointed out, aren't the ones anyone is really worried about. The ones to worry about are the types of people that run the storm botnets and things like that. In other words, criminals in it for big money, and not just bored kids.
In other words, the Russian Mafia.

---

### Post by Dr Small on 2008-09-08
> **cardinals_fan said:**
> In other words, the Russian Mafia.
That would be comprising 80% of the world's scriptkiddies ;)

---

### Post by p_quarles on 2008-09-08
> **Dr Small said:**
> That would be comprising 80% of the world's scriptkiddies ;)
It's true that a lot of people who wouldn't be a threat by themselves get used as pawns in these larger networks. Of course, this is true both of scriptkiddies and innocent suburban families who are unwittingly running zombies.

---

### Post by -grubby on 2008-09-08
> **swoll1980 said:**
> Can't Windows binary be converted back to source?

I believe so, but it's in assembly, and copying it will get you into trouble

---

### Post by swoll1980 on 2008-09-08
> **nathangrubb said:**
> I believe so, but it's in assembly, and copying it will get you into trouble

If cracking an open source program is illegal( I was assuming it was, but really have no idea) then I don't think they would care either way. It's one of those "in it for a dime, in it for a dollar" things. This would negate any advantage the cracker would see in cracking a open source program as opposed to a closed source program.

---

### Post by Trail on 2008-09-09
Well I haven't read *all* of the posts, but I'll go ahead in any case :)

Another probable factor is that open source might make it *easier* for a cracker to exploit a system. Hobbyist crackers are probably motivated by seeking fame, so they'd want to crack something difficult and through means other than looking at the source-code (which pretty much any programmer could do).

It wouldn't feel special to crack something open-source I imagine (unless the damage caused is a bit hacky), but it might be more challenging to crack something proprietary.

I guess.

---

