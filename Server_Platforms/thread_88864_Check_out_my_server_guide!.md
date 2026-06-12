---
title: "Check out my server guide!"
date: 2005-11-11
forum: Server Platforms
---

### Post by Zensunni on 2005-11-11
This is for absolute beginners. A good place for really new people to go.

(no need to correct my spelling. I'm in the process of doing it now.)

[http://thehiddengrotto.com/server.php](http://thehiddengrotto.com/server.php)

*hang head* ops, wrong forum....

---

### Post by heftigrat on 2005-11-11
[FONT="Courier New"][COLOR="Black"]Nice avatar.

And that is some guide.  I'll have to read through that when I have some spare time.[/COLOR][/FONT]

---

### Post by LordHunter317 on 2005-11-11
Your information on DNS is misleading.  google.com isn't a server name, it's a domain that happens to also point to a server.  A DNS entry refers to a server only if it doesn't contain a SOA RR.

Speed is only measured in units of bits per second.  Many programs, including webbrowsers, show speed in units of bytes per second, but that's not actually used in the networking world for measuring bandwidth.

Commerical routers can be attached to many hundreds of networks at once, and usually have many more than two interfaces on them.

Your ranting about Microsoft extending standards is both wrong and childish.

---

### Post by heftigrat on 2005-11-11
[QUOTE=LordHunter317]Your information on DNS is misleading.  google.com isn't a server name, it's a domain that happens to also point to a server.  A DNS entry refers to a server only if it doesn't contain a SOA RR.[/QUOTE]

google.com can be thought of as a server name, or can at least be referred to as a "host name" for a server.  Sure, it is also the domain name, but it can still point to the IP of a server.  More commonly this is referred to as the "default record" and must point to an IP address and not a CNAME.  In this regard, Zensunni's guide works for "absolute beginners", which he states his guide is aimed at.

[QUOTE=LordHunter317]Speed is only measured in units of bits per second.  Many programs, including webbrowsers, show speed in units of bytes per second, but that's not actually used in the networking world for measuring bandwidth.[/QUOTE]

I agree, this could be a bit more clear on the distinction between bits and bytes.  Bits should definitely be explained first, or at least the units of Internet bandwidth and utilization should be defined as Kbps (kilobits per second).  Then bring up that some apps might measure in KB.

[QUOTE=LordHunter317]Commerical routers can be attached to many hundreds of networks at once, and usually have many more than two interfaces on them.[/QUOTE]

Again, as Zensunni states this guide is for beginners, most of them will deal with CPE-type routers, which will have an average of 3-4 ports in most cases.  There will always be one Serial port and possibly 2 or more Ethernet ports, but usually only one or two for routers without built-in switches.  This is common for commercial grade CPE's, unless you're doing something like multi-homing, bonding, BGP, etc.  The only routers that would have hundreds of connections would be distribution and core routers, which most beginners won't have any clue about.

[QUOTE=LordHunter317]Your ranting about Microsoft extending standards is both wrong and childish.[/QUOTE]

I only took a quick look at the "rant", but the key points I noticed sounded about right based on my experience - but then I'm no expert.  It seems overall that your response is more like an attack than constructive criticism, which is just as childish.  Ever heard of tact?

---

### Post by heftigrat on 2005-11-11
It must have taken you a while to write this guide!  It's not bad as a beginner's guide, but there are a few things that could be cleared up if you don't mind a few pointers.  LordHunter317 does have a few good points and you should probably disregard the condecending tone of his post.  A few things I noticed:

The ".dom" part of a domain name can also be referred to as the "root domain".  As a whole, "domain.dom" is commonly just referred to as the "domain name", though you can specify that DNS can associate a default record (@), essentially making "domain.dom" the name of the server.

ISP = Internet Service Provider

DNS = Domain Name Service, so say "DNS server"

Those were just a few things I noticed.  If you polish this guide a bit it could end up being very useful to many.  Just be careful that you get all the "facts" exactly right - that is, make sure you're not confusing issues.  Also, be careful about "ranting" on MS 'cuz some ppl take offense.

I hope this helps!  :D

---

### Post by LordHunter317 on 2005-11-11
> **heftigrat]google.com can be thought of as a server name, or can at least be referred to as a "host name" for a server.[/quote]Yes, I said it was both.  But callingi it by the latter, not former is misleading.  Saying, it can be both is less so.

> Again, as Zensunni states this guide is for beginners, most of them will deal with CPE-type routers, which will have an average of 3-4 ports in most cases.Fine, then he needs to talk about consumer, not commercial grade stuff.  He started out talking about  commerical grade stuff.  Perhaps he meant consumer, it's hard to tell.

> I only took a quick look at the "rant", but the key points I noticed sounded about right based on my experience - but then I'm no expert.It's just not.  For Internet based activties, IIS is no different from Apache said:**
> It seems overall that your response is more like an attack than constructive criticism, which is just as childish.No, it isn't.  If I wanted to attack him, I'd tell him his document sucks.

> Ever heard of tact?Yes, and frankly I don't feel it's very appropriate here.  If you don't want public critique, don't post it publically.

---

### Post by heftigrat on 2005-11-11
> **LordHunter317]Yes, I said it was both.  But callingi it by the latter, not former is misleading.  Saying, it can be both is less so.[/QUOTE]

OK, true.  However, I didn't really understand the correlation you made between the SOA and the default @ record, would you mind explaining?

> Fine, then he needs to talk about consumer, not commercial grade stuff.  He started out talking about  commerical grade stuff.  Perhaps he meant consumer, it's hard to tell.

Small to mid-sized businesses are still "commercial", that's the angle I was coming from.  Usually core/dist routers are reserved for ISPs and large businesses.  And trust me, there are plenty of "beginners" posing as LAN & server admins, so the guide could come in handy then.   said:**
> It's just not.  For Internet based activties, IIS is no different from Apache; Exchange no different from postfix or sendmail (ignorning some small things); DNS server no different from bind;

I seem to remember parts referring to instability and the need for patches and such, which is accurate.  Dealing day to day with a well-seasoned Linux & IIS admin I can testify that he has MANY more problems with the IIS server.

> No, it isn't.  If I wanted to attack him, I'd tell him his document sucks.

Well, you basically did.  You didn't have anything good to say about it.  It just seemed a bit harsh at first glance, but what the hey.

> Yes, and frankly I don't feel it's very appropriate here.  If you don't want public critique, don't post it publically.

Again, I prefer to use tact when I can, that's all I was saying.  I know I can't change your style.

---

### Post by LordHunter317 on 2005-11-11
[QUOTE=heftigrat]However, I didn't really understand the correlation you made between the SOA and the default @ record, would you mind explaining?[/quote]If an entry has an SOA RR, it is a domain/subdomain entry.  If an entry has an A RR, then it is a host entry.  Domain entries that have a default record have both an SOA and an A RR, so it's best to call them both.

> Small to mid-sized businesses are still "commercial", that's the angle I was coming from.And the routers they use support way more than two interfaces.  The only non-homegrown units I've seen that only support two interfaces are consumer grade equpiment.  Anything that's entry-level commerical made by Cisco, Juniper, et al. will be able to support more than 2 IFs.

> I seem to remember parts referring to instability and the need for patches and such, which is accurate.We just have had a discussion about this over at Ars Technica.  Win 2K3 over it's lifetime has had a comparable amount of patches to any Linux distribution.  And certain parts, like IIS, have had very few.  IISv6 has had a DAV vulnerability and I believe one other, while Apache has had a host of problems in the past year.

> Dealing day to day with a well-seasoned Linux & IIS admin I can testify that he has MANY more problems with the IIS server.I'm not sure that doesn't say somethign about the quality of your administrator on Windows, not the platform itself.

Seriously, bashing Windows as "less secure" or "more patch work" or anything of the sort is really just ignorant and serves to drive people away.  It's just mudslinging, and it's just not really true.

> Well, you basically did.No, I didn't.  You're *assuming* (falsely, I might add) that because I pointed out technical errors, I think it sucks.  In fact, I've passed no value judgement of any sort on the document, because I don't feel it's appropriate to do so until the errors are corrected.  I still view it in the draft stage, if you will, and won't say, "This is a good document," or, "This is a bad document," until he takes what errors I've pointed out into consideration, and fixes them.  

> You didn't have anything good to say about it.That doesn't mean I think it sucks or is bad, either.  And as I said, I don't think it's fair or wrothwhile to make a value judgement until the errors are corrected.

> It just seemed a bit harsh at first glance, but what the hey.Well, perhaps, but I don't particularly see the need to be encouraging about such things.  Everyone's wrong, usually quite often.  You can either make a big deal about and get discouraged; or accept it as a fact of life, fix the mistakes, and move on.  I don't see it as a particularly big deal (none of the errors are dangerous, just misleading) so I don't see a need to make a fuss, just merely point out where his mistakes lie.  And that's what I did.

In the same turn, I don't feel the need to say, You're doing a good job in spite of your mistakes, because as I said, it's not a big deal unless someone chooses to make it one.

---

### Post by Zensunni on 2005-11-11
Thanks for all the feedback. I'll be sure to fix anything that's amiss. I had originally written most of it a while back and didn't get around to completing it. When I came back there were some things where I thought: "That's dead wrong. What was I thinking?". Part two was also kind of rushed (especially the windows server, but that's okay).

Oh, and by all means, if there are links you know about linux or anything to do with servers, just list them and I'll put them in my reference guide.

My next guide will be on web-development. It will talk about all kinds of web languages like php, html, xhtml and so on. I'd like to make the same setup with a reference guide too.

Keep in mind that these guides are not for paticular knowlege per se. You could call it a cop-out, but I'd rather create something more general to show people all of whats out there. Many people shy away from specific how-to's just because they don't know about alternitaves. If they can't decipher if standards they will use are for the best sometimes they won't get their hands wet.

Edit: Heh, I think people are putting arguements in my mouth. I don't defend this guide at all. Why bother defending something that's not right when I'm only delaying it's progress? If there is something that's bad about it and you say it sucks, what'd be the difference between that and somebody who says it nicely? Call me listless, but I don't think critisizm should be received with emotion. I'm all for improvement!

Thanks about the avatar - Power to the people man!

---

### Post by heftigrat on 2005-11-11
Thanks for the info on DNS.  I personally never refer to them together in practice, but I see your point.

[QUOTE=LordHunter317]And the routers they use support way more than two interfaces.[/QUOTE]

I wouldn't say WAY more.  Maybe a couple or a few more.  I know this is a bad example, but Adtran NetVanta3200 routers have 1 WAN int and 1 Eth int and are used for business class T1's.  Most Cisco's I work with regularly have a 1 or 2 WIC cards installed and a couple Eth interfaces.  These are also bus-class T1 routers, and the way they're viewed by most EU's is that there's 1 WAN port and 1 LAN port.  My comment on this was again spurred by the fact that this is a beginner document and that's all that really needs to be referenced, my opinion.


> We just have had a discussion about this over at Ars Technica.
...
I'm not sure that doesn't say somethign about the quality of your administrator on Windows, not the platform itself.

Doubtful.  He's the head admin running both a Linux/Apache and a Win/IIS server, hosting tens of different domains' sites.

I have a feeling all the "mudslinging" that does go on is based on something.  All the same I'll have to check out Ars Technica.

I never said you pointing out technical errors implied that you thought it sucked.  It's just the feeling I got from reading what you posted.  If it had been a purely technical critique I wouldn't have thought so, but the word "childish" is what did it for me really.  That's what made it personal, in my eyes.  I don't think it's a question of encouraging someone to be wrong, it's a question of encouraging them about what they did right.

Sorry to have made a big deal out of it, but as I said before I just thought your initial post was tactless and possibly insulting.  I'm not sure if Zensunni took it that way or not, so I guess it's irrelevant.

Either way our back and forth isn't helping Zensunni at all, so let's drop it, or maybe take it to the backyard.

---

### Post by Zensunni on 2005-11-11
Changes:

> Google.com" is the domain name which takes you to their server, but....

I wasn't too sure about this line, but I left it in:

> Ultimately, you can become a DNS server that other people use to access for all your sub-domains. However, making a DNS system can be very difficult and probably isn't needed for any internet services you intend to provide.

For the whole "internet speeds is mesured in bits" thing, I only reiterated my statements slightly. I stated that the speed is usually measured in bits and that sometimes other programs will use the other type. I think it's important to mention both and how to compare them because most new people will be thinking about their p2p programs and browser download managers when they think of speed. Not only will they know how to compare them, they will also have a reference point for how good a certain megabit speed is.

> Speed on the internet is usually measured in Megabits per second (Mbps); a megabit is a million bits. However, some programs and applications use kilobytes per second (kB/s, or K/s); a kilobyte is a thousand bytes. If you want to compare the two, just remember that one byte is eight bits.

My changes concerning routers were also very subtle:

> A router is like a miniture computer. However, unlike most computers, it has more than one network. Usually, one is a wide area network (WAN) and the other is a local area network (LAN).

As far as the "rant" goes, I changed a few openly agressive words, but I didn't change a lot. I said microsoft was natorious for it security and such, suggesting that it has a bad reputation. It has a lot of good points. I just listed them later on. If it's that big of deal, I could list the good points first.....

I also don't want to tell people about microsoft applications without stating that they are quite proprietary. There are a lot of services, like WMP's radio and IIS that you have to jump through hoops to use on different systems, if at all. Also, being proprietary, it is illegal to fix any of their bugs yourself. You have to pay for any upgrades too. So, I think it would be doing them more harm to leave that out. Having said that, I may decide to tone it down a little if my better judgement proceeds me later on.

---

### Post by dalani on 2005-11-11
Hats off to you for objectivity in comparing server OS and explaining all those protocols. I have to wear the IT hat at work were we use MS2000. I would like shared email on our small LAN. Right now we have a 'hardened' workstation that serves as sole POP account email recipient operating behind router and firewall. Unfortunatly Outlook Epxress does nor allow sharing email from a centralized message store. In reading your tutorial it got me wondering if there was a TURNKEY solution with a userfriendly distros like Ubuntu? Ie. 

step 1? Samba??
step 2 ?configure x
step 3 ?configure y
....
result: all LAN boxes can access and send mail with Inbox archived on one computer

----PostScript: I had a quick look at your link to Webmin list of modules and it seems Webmin is the kind of GUI frontend for a linux turnkey (quick setup and simple admin) solution.

---

### Post by LordHunter317 on 2005-11-11
[QUOTE=Zensunni]As far as the "rant" goes, I changed a few openly agressive words, but I didn't change a lot. I said microsoft was natorious for it security and such, suggesting that it has a bad reputation.[/quote]They don't, though.  Their track record is about the same as everyone else's.

> I also don't want to tell people about microsoft applications without stating that they are quite proprietary. There are a lot of services, like WMP's radio and IIS that you have to jump through hoops to use on different systems, if at all.And that's not really a big deal.  The ability of any piece of software to run cross-platform is generally not that interesting.

> Also, being proprietary, it is illegal to fix any of their bugs yourself.That's not true.  Certain people have access to the source to various MS products under shared source arrangments.  I'm not privy to all what that allows, but I have to imagine some modifications are allowed, as it'd be mostly senseless otherwise.

> Having said that, I may decide to tone it down a little if my better judgement proceeds me later on.Better judgment would be to remove anythign negative whatsoever and keep a neutral tone.

---

### Post by LordHunter317 on 2005-11-11
[QUOTE=Zensunni]Speed on the internet is usually measured in Megabits per second (Mbps); a megabit is a million bits. However, some programs and applications use kilobytes per second (kB/s, or K/s); a kilobyte is a thousand bytes. If you want to compare the two, just remember that one byte is eight bits.[/quote]And I nearly forgot: a kilobyte (as used by said applications) is 1024 bytes, not 1000.

---

### Post by Zensunni on 2005-11-12
I forgot about the whole 1=1024 thing. It's annoying putting such arbitrary information in just to make your guide technically perfect. It makes the whole thing too convoluted. But, I might as well do it, because everyone else will say the same.

And, I'm simply not going to say linux and windows are on par concerning security.  With linux's file permission system and almost complete freedom of viruses, it's simply not true. Unless the whole industry changes their minds and people start telling me differently, I'm not going to say otherwise. Post a topic about it on the forums if you want...

> And that's not really a big deal. The ability of any piece of software to run cross-platform is generally not that interesting.

When someone is trying to decipher what platform to use for their server software on, it's pretty important what software can go on it. It's kind of weird saying something isn't important if it pertains to the subject at hand. Unless I misunderstood you.....

> That's not true. Certain people have access to the source to various MS products under shared source arrangments. I'm not privy to all what that allows, but I have to imagine some modifications are allowed, as it'd be mostly senseless otherwise.

If you show me the whole thing and if it's legitimate and considerably easy to do, I'll mention it on my guide. However, it seems unlikely that microsoft allows exceptions just because you are a business. I'm guessing it's a very controled and leanthy process that you'd have to pay an incredible amount for. In which case, it would go beyond the jurasdiction of a Neophyte's guide.

> Better judgment would be to remove anythign negative whatsoever and keep a neutral tone

I'm definately not going to remove cons from my guide. Silencing any contravening details is not only flat, it's also not informative. This is starting to feel beyond simple critisism and turning into a debate. If you want to take this somewhere else, start a topic about it and show me that enough people think you are on to something. Or, if you feel microsoft hasn't been properly represented, make your own server guide. Otherwise, I'm not going to discuss this anymore.

Edit: Now I fully understand why these kinds of posts aren't supposed to be in this forum section.

---

### Post by LordHunter317 on 2005-11-12
[QUOTE=Zensunni]And, I'm simply not going to say linux and windows are on par concerning security.[/quote]But they are.  People way smarter than you say the maturity of both models and implementations is more or less equal.  People like NIST.  Actually, Win2K server has a higher EAL rating, FWIW.

> With linux's file permission systemWhat?  Windows has both finer-grained and more flexiable permissions, as NTFS always forces you to use ACLs.

> and almost complete freedom of viruses, it's simply not true.I don't know what complete freedom of viruses you're talking about.  They don't, unless they find an exploit that gives them SYSTEM privileges.  Which, as I said before, has had about an equal track record on Windows and Linux, overall.  

> Unless the whole industry changes their mindsIt has, IIS has significant enough marketshare to show people are willing to run production web platforms on Windows.

Moroever, guess how many exploits IISv6 has had?  2, and both aren't applicable to most web setups.  Guess how many Apache 1.3 and 2.x have had in the past two years or so?  Way more than two.

So no, there's plently of support to show Windows isn't less secure than Linux.

> When someone is trying to decipher what platform to use for their server software on, it's pretty important what software can go on it.And?  You can get whatever software you need to run on Windows.   It's not like MS decieves you with the fact that if you use IIS-specific features, you'll be stuck on Windows.

> It's kind of weird saying something isn't important if it pertains to the subject at hand. Unless I misunderstood you.....It's not because usually once people pick a platform, they stay with it for a very long time.  Certainly longer than the life of the software they run on it.  So, cross-platform software for running your Internet platform frequently matters little because you're not going to switch anyway.


> If you show me the whole thing and if it's legitimate and considerably easy to do, I'll mention it on my guide. It's not.  However, the point is, being negative about that is a) not always true, b) just plain silly.  So stop.  You're not helping anyone by saying that.


> I'm definately not going to remove cons from my guide.Why?  They're wrong.

> Silencing any contravening details is not only flat, it's also not informative.Yes, but it's bad advocacy, and that's what you're trying to attempt.  You're not helping anyone by saying, "Windows is less secure,".  People aren't going to flock to Linux because you say that.  They're going to say, "This guy doesn't know what he's talking about," and continue to run their platform of choice.

That's ignoring the fact your support as to why it's insecure doesn't jive with actual facts whatsoever.

---

### Post by Zensunni on 2005-11-12
Why do you insist? If you're that convinced that you're right, just start up a thread on the general chat forum (but I'm sure they'll all agree with me). If you just want people to agree with you, then go to a windows forum. What I say reflects that of this community. All your arguements are basically just up to an individual's prerogative, as are mine.

If you're trying to make an arguement against something that's generally the consensus here, do it somewhere else. There's a line. You've crossed it. Go take your "good" fight to the appropriate place. I'm not going to write up some huge debate because I'm too insecure to let arbitrary arguements hang.

---

### Post by LordHunter317 on 2005-11-12
[QUOTE=Zensunni]Why do you insist? If you're that convinced that you're right,[/quote]I am right.  This isn't a highly subjective thing here.  It's pretty easy to support a position here with facts, which I've done many times.  You've failed to do it once.  "Security" isn't a tautology, after all.

> just start up a thread on the general chat forum (but I'm sure they'll all agree with me).That doesn't mean a thing.  It was only a few hundred years ago the people claiming the world was round were in a minority.

> All your arguements are basically just up to an individual's prerogative, as are mine.Funny, I don't think I make CERT data up, or the count of exploits released for a piece of software.  Nor do I think I have any effect on the evaluations NIST makes for common criteria.

> If you're trying to make an arguement against something that's generally the consensus, do it somewhere else.**But it's not the consensus** anymore, and that's the point.  And even if it was, it means the masses are just ignorant, I'm afraid.

Why do you have a hard time accepting the facts I've presented here?  You're reducing to saying, "It's a matter of opinion," but there's no opinion about number of exploits found in a year.

---

### Post by Zensunni on 2005-11-12
Are you that insecure that you just have to re-post your arguements again and again? Trust me, I heard them the first time and have given them a great deal of thought and research. I've also looked at other contravening points as well. I'm not going to post them because it'll just give you something to nit-pick at. If you were somebody else, I might take pleasure in a stoic debate. But you're obviously on a mission to prove your point, no matter the cost. So, why don't you just think yourself as right and go away thinking that you've won, because obviously in your mind you have.

You might think yourself a hero, but all you're doing is creating angered arguements and short fuses. It's just greifing when you have to re-post again and again.

I'm sure you're going to pick this apart with your little quotes, making arbitrary conjectures about my every point. But before you do, think of the maturaty of it. Why not just grow up instead?

> because I'm right!

Yea, yea, I'm sure you are.

Edit: I can already hear the conjectures brewing now....here, I'll do you a favor and write them.

> 
-Well, it's not mature to be ignorant either!
-Well, fine, I'm not going to waste my time on ignorant people!
-I think you're just not going to post you're contriving points because you're afraid I'll prove them wrong!
-You have to change because you're wrong. I'll do everything in my power to make you change!


All you're being is a martyr. Why go down that road?

> because I'm right!

---

### Post by LordHunter317 on 2005-11-12
[QUOTE=Zensunni]Are you that insecure that you just have to re-post your arguements again and again?[/quote]There's nothing insecure about my position or manner, because I can use facts in my defense.

> Trust me, I heard them the first time and have given them a great deal of thought and research.Then why did you continue to respond with non-truths?  It's not like we've been engaged in a debate on the validity of said facts or an actual subjective matter like exact impact of one exploit over another: I've posted facts and you've continued to respond with, "My opinion is as good as your facts," which just doesnt' hold water when your business is dependent on the choices made.

> But you're obviously on a mission to prove your point, no matter the cost.No, I'm not.  If you made an attempt at being reasonable, then we'd have a reasonable discussion.

But you're not being reasonable in the least.  First, it was, "My opinion is as valid as facts," now it's a veiled personal attack, claiming my person is preventing you from replying.  You're arguing style over substance, and that matters very little.

>  So, why don't you just think yourself as right and go away thinking that you've won, because obviously in your mind you have.No, I haven't.  Given reasonable proof as to why I'm wrong, and I'll consider it.  You've just failed to to that, thus far.  I don't understand why you have trouble with that.

> You might think yourself a hero, but all you're doing is creating angered arguements and short fuses.You're the one who feels the need to still respond.  If all I am is a troll, then why are still feeding material?  Your statements aren't just consistent with your actions in the least, I'm afraid, on any matter you've brought up, including this one.

> I'm sure you're going to pick this apart with your little quotes, making arbitrary conjectures about my every point.If they're arbitrary, show how they are.  You've failed to provide a defense for yourself, and "It's my opinion," just isn't a defense about such matters.

> But before you do, think of the maturaty of it. Why not just grow up instead?What's immature about what I've done?  You asked for feedback, you got it.  You were told the errors in your article, and when you continued to justify your writing style, you were told why it isn't smart.  You've yet to show any validity for what you're doing.

Certainly, I can't stop you and if you really want to write that way, go ahead.  I really could ultimately care little.  But don't respond to the critic saying, "It's my opinion and that's all that matters here," when that's not true in the least.  

What I said was very true: advocacy of any sort is baseless and even harmful without facts.  Slinging mud doesn't get you anywhere unless you're running for political office.

> All you're being is a martyr. Why go down that road?I'm being nothing of the sort.  However, I strongly believe in correcting this sort of mis-information wherever I can, hence my response to you to not make it.  If you really want to, I can't stop you, but don't expect to make posts saying, "Ubuntu is more secure than Win2K3" in the forums I frequent here and not get a response from me nothing I'm wrong, unless you further substaniate that statement.

I don't see what's so hard to understand about that.  Generalities are bad, mmkay?  Especially when they're really falsehoods.

What's so difficult to accept about the fact that they're equally secure?  It doesn't paint either in a negative light.

---

### Post by isaac_golding on 2005-11-13
I just spent some time looking it over and I think it's a great guide.  A few typos here and there and its nice to see a guide that isnt exactly "neutral"  contrary to what some would say being truly neutral isn't required.  

:KS

---

### Post by Zensunni on 2005-11-13
well, I salute your obstinance! You should be a politician!

Edit: Thank you isaac.

---

### Post by dalani on 2005-11-15
Zensunni,
There's is one more thing about the web guide on servers that should be included: prices. I did some checking about pricing to set up a box to sort and centralize email at work using W2K3 and EXchange and the price is staggering (by linux standards) 999.00+1300.00 just for the software ordered directly from MS website. That's not including the set-up fee. That is an important consideration even if it's not technical. With Ubuntu, Webmin and some IMAP server 'ware installed, the cost is of course considerably less for the OSS.

---

### Post by hostile on 2005-11-16
> Server 2003 is for people who know the computer basics, but can't be bothered with the logistics. Although costly, it's a way to jump into server technology with little knowledge of what you are doing. Provided that you use the windows programs for all your networking software, you'll never have to be bothered too much with a command line terminal. All the setup options are redily available and it's usually easy to go back to defaults in case you mess up. It's very ideal for small business and areas where functionality is priority over cost and security. Just remeber to make sure you have updated your system with the latest patch and make regular checks for updates.


**_Question:**_

Do actually have ***any experience*** administrating a Windows domain in an mid-size to enterprise-class environment?

Everything you have said here is both untrue and misleading, with the sole exception of the last sentence.

If you're trying to help people set up a Ubuntu server, then great, but it should focus on just that, not spreading FUD.

> If you have an old computer kicking around, that's all you need. Just make sure it meets the requirements for your server's operating system. For both operating systems you'll need:

    * Processor: 800 Mhz+
    * Memory: 256 MB
    * Hard disk: 3 GB
    * Media drive: CD-ROM drive
    * GPU: 64 MB card; Supports 1024X768 resolution (anything better than a Riva TNT2)
    * Network card: Any eithernet card that's 100MBit or higher is fine.

You can have Ubuntu linux system run only your webserver applications which will let you create a server with half of the aforementioned requirements. However, if you're just new, you probably want an Ubuntu desktop anyways. The minimum requirement list I have made is from my own judgement. I find the ones done by the companies and organizations to be laughably conceited.

If you are saying these are "from your own judgement", perhaps you could back them up with some statistics?


> f you want to have the OS X Server, you'll have to lay down a good thousand dollars for the software alone. It is also closed source, so you must wait on the company to release bug fixes and updates.

Actually, Darwin is GPL'd. Aqua is proprietary.

> Email

Most server operating systems have email server programs available right from the start. Windows and Mac OS X have their own proprietary programs and linux has many open source iterations to choose from. Microsoft's program is the Exchange server. Apple uses a compilation of open source services like SquirrelMail and postfix all put together to make one unified mail system. Linux has a whole bunch of stuff and arguably the best selection. You can chose from sendmail, postfix, fetchmail, qmail, imap, exim and a whole bunch of others. Postfix is generally used by most Linux administrators. 

Anything you can get for Linux, you can get for OS X - some of it pre-compiled, some of it you have to compile yourself.

> Database management

While databases don't actually work as an online agent, they are mostly used by web programs. Databases are used by email servers to store their email, by webforum programs for managing posts, by web page servers to keep track of browser input, by irc servers to keep track of logs and by php scripts to store variables and information. There are just too many internet programs that use them to not list it. As before, windows has their own database program called Access and Apple uses the open source programs which Linux uses. What is the best one? The one most commonly used is mySQL. It's the one that Apple comes with and is used by linux administrators everywhere. There are alternitaves, such as postgreSQL and oracle. It might be a good idea to research each one before you make the dive.

You actually mentioned Oracle in a "Neophyte" How-To?? I worked at an Oracle Dev Company for 2 years as a Sys Admin, and I'm STILL lost as to how to fully manage Oracle. Not to mention the *hundreds of thousands of dollars* we had to pay in annual licensing fees. I'm convinced Oracle was sent by Satan himself...

---

Overall, I can understand the point of the document, and appreciate your enthusiasm, but you really should not say things you don't have comprehension of, or experience with - stick to what you know. There is more here that is incorrect than I have mentioned.

It's better to admit ignorance on a subject, and help with what you have a clear grasp of.

You might want to run a spell check on it too.  ;)

---

### Post by thebigfatgeek on 2005-11-16
Thanks for taking the time to write the guide. Wrong or right is sooo overrated, it helped me ( a beginner, for whom the guide was written) and that is the important issue.

I wish these intellectual critics will just go away to any of the other "snobbish" Linux distros/forums etc.

Please Mr Moderator, the reason I am using Ubuntu is because this type of thread are so seldom seen. Can you please just make it go away?

---

### Post by prasys on 2005-11-25
Pretty good guide . I wish you would upgrade for Breezy and more add-ons..Nice !

---

### Post by Seventh on 2005-11-25
Thank you Zensunni for the guide, it has been a great help!

I've set up an oldworld PPC as a webserver using your guide as a side project in my company that is completely windows-minded. Beeing so happy with the results, i've been able to recycle 4 old PPCs that were gathering dust in our storage room into various server types. Your guide was so easy to follow that even a friend of mine from the economics department succeeded in setting up his own testserver.

Can't wait to get my hands on your webdev guide ;) Keep up the good work!

[I]@hostile, LordHunter317: 
If you pretend to have that much knowledge about servers i suggest you go write a guide/book yourself instead of bringing down the exemplatory effort Zensunni has made to the Ubuntu community![/I]

---

### Post by hostile on 2005-11-25
[QUOTE=Seventh][I]@hostile, LordHunter317: 
If you pretend to have that much knowledge about servers i suggest you go write a guide/book yourself instead of bringing down the exemplatory effort Zensunni has made to the Ubuntu community![/I][/QUOTE]


First off, he asked the community to review his guide. We did. If you ask for constructive criticism, you're going to get it. **If one doesn't want to hear people's opinions, then one shouldn't ask**. 

Second, a how-to guide should not include bashing other platforms, **especially when the "facts" used to disparage said platforms are pure conjecture**.

Third, **I did not once say that Zensunni's effort in putting forth the guide was not welcomed**, quite the contrary, I did applaud it.

So, perhaps you should actually READ as well as COMPREHEND what Lord and I had to say about things first, before you put finger to keyboard.

If one is writing a valid guide for the community regarding the implementation of Ubuntu, STICK TO THE TOPIC. Nothing does more damage to Linux users as a community than us sitting here and wagging our proverbial fingers at the apparent shortcomings of other platforms, which were in ABUNDANCE in Zensunni's "guide". If he wanted to rant about other platforms, he should have taken it to a blog or something.

Now as far as me writing a "how-to" guide? Why would I bother? I have three things at my disposal which seldom fail me, and I only hit up the community for help when these have hit a point of failure: I RTFM, then I re-RTFM, then I  STFW. Those usually work for me.

Btw, I believe the word you were looking for is "exemplary"...

---

### Post by LordHunter317 on 2005-11-25
[QUOTE=Seventh]If you pretend to have that much knowledge about servers i suggest you go write a guide/book yourself[/quote]I've contributed to severally techincally correct guides in many places.  Besides, I find it far more helpful to post on forums answering specific questions, as a general rule.  Writing good technical documentation that's both correct and useful is really, really hard, and takes more time then I generally have to give.

> instead of bringing down the exemplatory effort Zensunni has made to the Ubuntu community!It's not, it's a bad effort.  That's the whole problem here.  His guide is poor in several respects.  What's far worse however, is his obstinate attitude to changing things for no other reason than his silly, elitest, antiquated notions of what operating system is more secure and therefore, superior.

---

### Post by hostile on 2005-11-25
[QUOTE=Seventh][I]@hostile, LordHunter317: 
If you pretend to have that much knowledge about servers i suggest you go write a guide/book yourself instead of bringing down the exemplatory effort Zensunni has made to the Ubuntu community![/I][/QUOTE]


If you want to read an ***exemplary*** guide, look at this:

[Ubuntu Guide]("http://www.ubuntuguide.org/")

THAT is a fine piece of work.

[quote=LordHunter317]I've contributed to severally techincally correct guides in many places. Besides, I find it far more helpful to post on forums answering specific questions, as a general rule. Writing good technical documentation that's both correct and useful is really, really hard, and takes more time then I generally have to give.[/quote]

**No kidding**. Good tech writers are a rare breed, to be sure.

---

### Post by dalani on 2005-11-25
> The minimum requirement list I have made is from my own judgement. I find the ones done by the companies and organizations to be laughably conceited.

He's correct. I have an old PentiumII with 5.04 and it's damn slow with Gnome as GUI. I found no official recommendation on this site about minimum requirements for an Ubuntu desktop or server. Except his.

---

### Post by hostile on 2005-11-26
> I found no official recommendation on this site about minimum requirements for an Ubuntu desktop or server. Except his.

[*ahem*]("http://www.ubuntulinux.org/support/releasenotes510#1.0").

Besides, if you're installing on an "old P-II", I certainly hope you would not expect it to magically become some sort of speed demon...

---

### Post by Zensunni on 2005-11-26
Okay, okay...

First of all, people are getting way too uptight about this. I mean,  people are drawing enemy lines here. Take the hostility level down a notch.

This isn't a book. It's not certified. Nor should it be. It's just some guy who's studying open soure programs and putting what he knows in writing. If it doesn't meet your standards, then you're probably looking in the wrong place.

That's the trouble with writing a non-specific guide. Much of it is opinion and can't really be nailed down to the floor.

For instance:

This is what I did reguarding system requirements: I grabbed an old computer with just enough power that ubuntu could work nicely on. Then I typed in the specs. If you're that conceited about specifics, then you should probably be in a bookstore.

"First off, he asked the community to review his guide. We did. If you ask for constructive criticism, you're going to get it. If one doesn't want to hear people's opinions, then one shouldn't ask."

Actually...at no point did I  ask for critisizm. It's not that I mind it. I'm just getting a full mouth from getting words put in it.

As to your commens on oracle, I have only heard about oracle and I only mentioned it. I think it's pretty picky, but if it's that bad, I might just take it out....

"Actually, Darwin is GPL'd. Aqua is proprietary."

Will everything that runs with unix run on darwin? If so, that's really good to know....and worth mentioning.

"Do actually have any experience administrating a Windows domain in an mid-size to enterprise-class environment?"

Since when do companies who have thousands and thousands of dollars on the line start looking at beginner tutorials from the internet? If this is the expectations of my guide, I'm honered.....but you'll just be sadly dissapointed. 

And....

everything from "domain name" to "server hardware" is completely wrong? This sounds a lot more like a personal attack than plain critisizm here. I'm not usually one to refute critisizm as long as it is civil and without motivation of anger. That's why I stopped talking to the other guy. I'm not going to argue with somebody who's sole purpose is to stomp their resolve onto everybody else.

And, as for lord's pages of arguements:

I consider spending a whole page, just trying to convince me to argue with you to be pretty arbitrary. But since there are more people on this form than this guy, I'll give my conjecture....

Now, I'm no expert, but I don't think ACLs are integrated right into the system like linux permission system (if it is, then excuse my ignorance). If you look at a big company (and I'm talking outside the jurasdiction of my beginner's guide), there's bound to be password vunerabilities. Hacking 101 says that most attacks start without a computer. If someone were to get a lower level user's privilage (heh, office space...) that allows access past the ACL restrictions, the user can download a file and return it as a trojan. When somebody with higher access privliges (or on an internal computer) opens it, it gives the program a chance to attach code to another file. Provided that the hacker can think far enough ahead, his program can then jump up the ladder until the trojan is granted access to the registry (or whatever else the hacker wants at). Unlike linux, files don't need root permissions to do things. Once something gets in, it can be nasty.

If you go on just the basis of exploits, sure, you're right. However, there's much more to getting in, than computerized attacks. Once an attacker has obtained a password, damages after the fact can be devistating on windows systems, where as with linux, the assailant can only go as far as the user's permissions.

I might be ignorant on my thinking, but I also think that linux's bad scores in incident ratings can be contributed to people not knowing as much about the OS. Maybe try comparing it to Unix. It's the same thing, only Unix is very regimented. Could it be that the more professional people have opted for Unix's support? If so, wouldn't it be best to start with something that's almost identical?

Now, that I've given a response, you can do two things:

Rip my response to threads with hostile, nit-picking arguements for every line.

or

Just put your arguement into a well rounded paragraph with respect and decency.

You might be the master of windows, but in social respects, you have no give. Why jump on forums if your tolerance is that lacking?

Edit: Thanks everyone else for the support and not jumping into the geurilla warfare battle.

---

### Post by LordHunter317 on 2005-11-26
> **Zensunni]That's the trouble with writing a non-specific guide. Much of it is opinion and can't really be nailed down to the floor.[/quote]**That's just it though: *The overwhelming majority of things about computers ARE NOT OPINIONS***.

They're fact.  Cold, hard facts.  People don't like to accept that because it shatters their little worlds they setup, but that's the reality.

Computers are detriministic machines running mainly deteriminstic code.  What does that mean?  It means given the same inputs, they'll do the same thing every time.

From that, one can conclude that their behavior can be repeatedly observed, and *measured*.  And if we can measure something, we can make comparsions that have no room for error.

Where things like security get objective is in weighting one criteria over another: is number of exploits more important than average time to install a patch?  Such things have room for debate in them.  However, the fact that both can be measured and verified and *are facts* isn't up for debate.

And most of what you stated wasn't opinion, it was fact masquerading as such.  

> Will everything that runs with unix run on darwin? If so, that's really good to know....and worth mentioning.Seeing as it's BSD-based, yes, just about anything that runs on FreeBSD 4 will run on Darwin.  Not that you'd want to.  Mentioning Darwin is roughly akin to integrating children with learning disabilities with the honors students, FWIW.

> Since when do companies who have thousands and thousands of dollars on the line start looking at beginner tutorials from the internet?His point is, you lack the expertise and experience to make *any* comments on the Windows Server platform if you don't have such expertise.  And it's clearly obvious you lack both the experience and expetise.

> everything from "domain name" to "server hardware" is completely wrong?That's about consistent with my post, yes.  Go back and read it, where I more or less pointed out obvious technical errors.

> That's why I stopped talking to the other guy.The only anger here is disappointment at the fact you refuse to change your opinion for no reason but because you refuse to listen to reason.

> Now, I'm no expert, but I don't think ACLs are integrated right into the system like linux permission system (if it is, then excuse my ignorance).Yes, they are.  Go read the Server Resource kit on NTFS.  The only permission system in use is ACLs, and they're active all the time.

>  If you look at a big company (and I'm talking outside the jurasdiction of my beginner's guide), there's bound to be password vunerabilities.That's a social, not a technological problem.  Something computers can't do anything about.  If I deployed Linux machines across a whole company, I'd still have the same problem.

Windows, properly configured, can store passwords in a nearly as secure form as what Linux currently does.  It's only real vulnerability(s) is that it's more vulernable to rainbow table attacks if the password databases are stolen and that replay attacks can occur against NTLMv2 if you're not using secure authentication.  The one can be mitigated in necessary circumstances by long passwords and using non-printable characters said:**
> Hacking 101 says that most attacks start without a computer.No, it doesn't.  Frankly, this is just another subject you're making apparent you have no idea what you're talking about.  And that's the issue here: you're making statements because you believe they're tatuologies when they're not, and you'll find the real world doesn't agree with you, even though your little circle of communities you hang out in wrongly espouses the same beliefs.

> If someone were to get a lower level user's privilage (heh, office space...) that allows access past the ACL restrictions,What?  This statement makes no sense.


> the user can download a file and return it as a trojan. When somebody with higher access privliges (or on an internal computer) opens it, it gives the program a chance to attach code to another file.Wonderful.  Good for you.  Assuming I understand what you're attempting to say (compromising unprivileged accounts to attack privileged ones) **Linux is no less vulernable to such attacks, *so this is irrelevant***.

As I said eariler, Windows and Linux both use the same security model: DAC.  They both have roughly the same common criteria certification (I'm awaiting Win2K3 rather eagerly, but I don't know if it'll happen) when properly configured and setup.

And both, properly setup, are still vulnerable to such attacks.  One of the assumptions of DAC is that the Administrator never performs any wrong or harmful actions.  

> Unlike linux, files don't need root permissions to do things.Yes, they do.  You can't do tons of things in Windows if you're not Administrator.  And in reality, you can't do everything even if you are Administrator.  You'd have to be LOCAL SYSTEM for a total compromise.

> Once something gets in, it can be nasty.Linux is no different.  You've yet to show a scenario that Linux isn't vulnerable to.  To prove it, let's pretend you "hack" my hunter account on my laptop.  You leave a trojan there called 'runme' that when run as root, will "pwn" my system.  To have the same problem, all I have to do is run as root:```
/home/hunter/runme
``` and we're done.

Hey wait, that's no different from Windows.  Well, I'd probably double-click in Windows.  But the concept's exactly the same.

So you're wrong, via proof by counterexample. Come back when you actually you know, understand security basics.  I highly recommend going to the common criteria site, reading the evaluations of Win2K Server and some of the linux distributions, and reading the documents on CAPP, which is the specific model they're evaluated to.  As it's clear you don't understand *any* of the ramifications of it, and you're just spouting mistruths.

> damages after the fact can be devistating on windows systems, where as with linux, the assailant can only go as far as the user's permissions.Windows is no different.  Users don't have privilege all the time unless they run in account that has privilege.

Running as administrator all the time is really not that much different than running as root all the time.  If you run as an account in the regular 'Users' group, you'll find your privileges to freely do things on Windows severly curtailed.

> I might be ignorant on my thinking,You're not just ignorant, you're arrogant and ***refuse to listen to reason and FACTS***.  Which is the real travesty here.  You're being zealous about something you're not only obviously and clearly wrong about, you refuse to even really recogonize the fact you're doing so, and come up with the wildest, illogical excuses for your actions and reasoning.

> but I also think that linux's bad scores in incident ratings can be contributed to people not knowing as much about the OS.I think the groups that do this sort of stuff, like SANS, know more about both operating systems than you can possibly imagine.  Nevermind the fact doing things like counting vendor exploits doesn't really require that much OS knowledge...

>  Maybe try comparing it to Unix. It's the same thing, only Unix is very regimented.You've clearly never used commerical UNIX, either.


> Just put your arguement into a well rounded paragraph with respect and decency.There is no possible way I could respond to all your misinformation in a single paragraph.  Hence, I write multiple ones, addressing each error in turn.  It's clearer and far more efficent.

> You might be the master of windows, but in social respects, you have no give.You're the one who's failing to realize the ***factual errors*** you're making, ***and when confronted with them by MULTIPLE PEOPLE, you outright refuse to correct them***.  No give indeed :rolleyes:

> Why jump on forums if your tolerance is that lacking?You're the one who apparently can't tolerate having your "opinions" :rolleyes: shattered.  If you could, you would have stopped replying at this point.

---

### Post by Kronocide on 2005-11-26
Lord, I've visited this forum perhaps three times, read maybe a dozen posts by you, and you consistently come through as a not very friendly person, more interested in demonstrating your superiority than being of assistance. Maybe that is not the way you intend it, but it's how it comes out. Just a friendly pointer.

---

### Post by dalani on 2005-11-26
[QUOTE=hostile][*ahem*]("http://www.ubuntulinux.org/support/releasenotes510#1.0").

Besides, if you're installing on an "old P-II", I certainly hope you would not expect it to magically become some sort of speed demon...[/QUOTE]

I checked your link and there's no mention of minimum requirements of CPU. It only mentions RAM and HD (of which I have 196meg and plenty of gigs).

And yes I do expect my Pentium2 to run faster. I was told the only to do that is if the kernel is compiled in situ on my machine or load up a lighter GUI like Xfce. BTW how do I get Ubuntu to use Xfce by default?????

---

### Post by dalani on 2005-11-26
>  "Hacking 101 says that most attacks start without a computer."
No, it doesn't. Frankly, this is just another subject you're making apparent you have no idea what you're talking about. And that's the issue here: you're making statements because you believe they're tatuologies when they're not, and you'll find the real world doesn't agree with you, even though your little circle of communities you hang out in wrongly espouses the same beliefs.

Lord you erred badly there by overlooking the glaring obvious: Hacking can only begin outside a computer...a computer is just a tool remember? Obvliously your overzelaous ranting has clouded your grasp of the obvious. In the real, computers don't hack into other computers. HAckers just exploit the weaker links. 

I would prefer a more secure box then please myself with the ease with which I can apply a patch.

---

### Post by LordHunter317 on 2005-11-26
[QUOTE=dalani]Hacking can only begin outside a computer...a computer is just a tool remember?[/quote]You need to take his statement in the context of the whole paragraph.  He was referring to the near-mythical "social engineering" attacks, where systems are compromised by getting a human to reveal information they shouldn't, like their account password.

Many attacks on systems these days are automated, and do begin with a computer comprimsing another computer.  Sure the attacking computer's code was written by a human, but that's not what he was talking about.  He was talking about the attacker using a human to get information to compromise the computer, instead of attacking the machine directly.

> Obvliously your overzelaous ranting has clouded your grasp of the obvious.First, I'm not the one who's unwilling to change his opinion when presented with actual facts or proper logic.  Second, your intrepretation of his statement is a total non-sequitur and inconsistent with the reality we live in. 

> In the real, computers don't hack into other computers.So automated worms like Slammer, IIS Code Red, etc. don't exist?  :rolleyes:  No, I'm sorry, automated exploitation of computers is quite common these days.

The only human involvement is the author who wrote the worm and ran it.  It's not what he was talking about: the hacker getting a human to give up information allowing him to attack.  He was clearly talking about social engineering.  Which is still a concern, to be certain.  But it's not the first and foremost means of attack these days.

Most attacks are automated, otherwise virus scanners, spyware tools and their ilk wouldn't be so effective.

> HAckers just exploit the weaker links. Which include exploits on vulerabilites on code, which are usually performed through automated means these days.  

> I would prefer a more secure box then please myself with the ease with which I can apply a patch.When you can show me the 100% secure box that never needs a patch, sure.  In the meanwhile, NIST will stil continue to do ALC_FLR evaluations, I'm quite certain.

For those who don't know, ALC_FLR is the evaluation process used to measure an operating system's ability to apply security patches after install.  This includes looking at things like Windows Update or RedHat Network.  Both Windows and RHEL3/4 have been successfully evaluated to the same level.

---

### Post by Zensunni on 2005-11-26
Well, since I'll get no peace from you, then suggest what I should change in my guide. If I'm going to say "linux is just as sucure as windows", then I need something so that I won't have your counterpart trying to stomp the other way. Throwing out a bunch of acronym's won't help either. It'll need to be something that a beginner can understand.

I'm not going to read through your page long posts filled with arguements like:

"You're not just ignorant, you're arrogant and refuse to listen to reason and FACTS. Which is the real travesty here. You're being zealous about something you're not only obviously and clearly wrong about, you refuse to even really recogonize the fact you're doing so, and come up with the wildest, illogical excuses for your actions and reasoning."

....doesn't even deal with anything about computers. It's just name calling. That won't help in any social situation.

---

### Post by Zensunni on 2005-11-26
Dang, double post...

---

### Post by LordHunter317 on 2005-11-26
[QUOTE=Zensunni]Well, since I'll get no peace from you, then suggest what I should change in my guide. If I'm going to say "linux is just as sucure as windows", then I need something so that I won't have your counterpart trying to stomp the other way.[/quote]Don't say anything beyond that.  Really, just removing the negative comments about Windows woul make everything neutural and draw no comments.

Specifically, remove:[list][*]> Instead, they create their own versions of existing standards that often convolute the industry.[*]> Microsoft is also natorious for security and stability issues. Instead of creating new solutions for security issues and pooling their resources to develop a more stable system, they often just throw security and stability to the wind as a solution to compadability issues.At most, you could say something akin to, "In the past, Microsoft placed less focus on security than other operating system vendors, but this is something they've rectified with their current line of products"  I'm not sure I'd even go that far.[*]> As a result, their software always has a need for patches and updates. Even though the company gives out a fair share of updates and patches, one would wonder if the end justifies the means.This should be replaced with: "Like all other operating systems, keeping up with security patches is crucial." [*]> Server 2003 is for people who know the computer basics, but can't be bothered with the logistics. Although costly, it's a way to jump into server technology with little knowledge of what you are doing. is gone[*]> It's very ideal for small business and areas where functionality is priority over cost and security.as is that.[/list]


> ....doesn't even deal with anything about computers.Well, like it or not, the way you've approached the situation is the bigger problem here now.

You're the one, when told you were wrong on multiple issues, essentially claimed you were going to take your ball and go home, and that you didn't care.

> It's just name calling. That won't help in any social situation.:rolleyes:  Like you're from any moral position to make such judgements here.  Perhaps if you didn't commit the same, but hey, I've tried to be more than civil with you.  You're the one who, when told your facts masquerading as opinions were wrong, stopped acting in a civil manner and refused to listen to any reason.

As I've said before here, it's only a big deal if you choose to make it a big deal.  I could really care less, as long as truth prevails.  And as long as you post obvious mistruths here, I will correct them to the best of my ability.

---

### Post by hostile on 2005-11-27
[quote=Zensunni]Actually...at no point did I ask for critisizm. It's not that I mind it. I'm just getting a full mouth from getting words put in it.[/quote]

Well, I beg to differ.

Although you did not *directly* ask for a critiqe of your work, by posting such a document to the community, when it is for the community, a review of your work is implied. You honestly think that kernel revisions are issued and the new kernel is just "taken as is"? Absolutely not. The same goes for this sort of guide.

[quote=Zensunni]As to your commens on oracle, I have only heard about oracle and I only mentioned it. I think it's pretty picky, but if it's that bad, I might just take it out...[/quote]

One of my main issues with your guide was your "Firehose" approach. If you are going to talk about building a birdhouse, talk about building a birdhouse. Don't go off and start glossing over apartment building, condos, dog houses, barns... stick to the topic. If you're going to mention db's, then mention the two main contenders included in nearly every Linux distro, and research the pros/cons of them. There's little need to start talking about hellspawns such as Oracle (sorry... I still have flashbacks from working with it).

[quote=Zensunni]Will everything that runs with unix run on darwin? If so, that's really good to know....and worth mentioning.[/quote]

No, it won't. If you can get the source code for most apps/packages, and they depend on the same libraries which OS X has and was built against, then you most likely can compile the source of said packages yourself to run on OS X - but by no means is it a "slam dunk" in all cases.

Like Lord said, if it's compatible with FreeBSD 4, it will generally work on OS X.

[quote=Zesunni]Since when do companies who have thousands and thousands of dollars on the line start looking at beginner tutorials from the internet? If this is the expectations of my guide, I'm honered.....but you'll just be sadly dissapointed.[/quote]

LOL! You missed my point entirely.

My point is that you said in your guide:

[quote=Zensunni]Server 2003 is for people who know the computer basics, but can't be bothered with the logistics. Although costly, it's a way to jump into server technology with little knowledge of what you are doing.[/quote]

You could not be farther from the truth. Setting up a Windows server is not in any way, shape, or form a trivial task, if it is to be done securely.

You have to know what holes need to be plugged, what holes to unplug, and how to tighten the evironment accordingly. It is npt easy to have a secure and functional Active Directory structure in place, with appropriate, and more important, USEABLE, Group Policies in place. If all you want to do is share a file or two, you don't need Windows Server to do that. Hell, you don't even need Windows Server to run IIS. The need for Windows Server implies a much larger mandate than a simple file/web server.

Much like any OS which is to be used as a server environment, you have to know what you're doing to implement it effectively, and SECURELY.

[quote=Zensunni]everything from "domain name" to "server hardware" is completely wrong? This sounds a lot more like a personal attack than plain critisizm here.[/quote]

Honestly, you have a lot of information which is very incorrect. Before leading newbies down the proverbial garden path with your guide, you really should have done some research. I think the whole point that Lord and I are making is that your information is based not on fact, but on conjecture and personal assumptions/opinion - that does not a guide make. Sorry to be so blunt.

[quote=Zensunni] Once something gets in, it can be nasty.[/quote]

To give a more extreme example than Lord...

Install Ubuntu as a test (meaning this must be a non-production, disposable install). Log in as root (pretending to be a hacker who has gained root priviledges). Issue this command:

rm -rf /*

See what happens and tell me that isn't a potentially devastating senario if that command was contained in some sort of hack or trojan...


[quote=Zesunni]then suggest what I should change in my guide[/quote]

My suggestion would be starting from scratch with a mindset of providing information about implementing Ubuntu, which was your original intent.

Don't make any suppositions about Windows. None about Apple. If you want to mention either of these two, direct people to Google, and tell them Windows and Apple "are beyond the scope of this guide". Remove any and all sentences regarding either of these two. Easy as that.

Second, every sentence which is a declaration of fact, research it.

You actually say this in your guide:

[quote=Zesunni]Linux is best for people who are working directly with their servers and cannot tolorate ignorance. It's also good for people who... aren't afraid of reading a few books on the subject.[/quote]

At the risk of sounding rude, you should heed your own advice. May I suggest the O-Reilly series? Quite often they have been my bibles on many things.

[quote=dalani]And yes I do expect my Pentium2 to run faster. I was told if the kernel is compiled in situ on my machine or load up a lighter GUI like Xfce.[/quote]

Faster than what?? Sure it will run faster with Xfce over Gnome, but expecting your P-II to magically be given some sort of phenomenal speed blast, I'm sorry, but your sadly mistaken.

P-II's are rapidly approaching 10 years old. 10 YEARS! That's a HUGE amount of time in the computer industry. I think they're leaving the judgement call on hardware for application up to the individual user.

[quote=dalani]I checked your link and there's no mention of minimum requirements of CPU. It only mentions RAM and HD (of which I have 196meg and plenty of gigs).[/quote]

So? The thing about any distribution (btw Zensunni, different Linicies (Linuxes?) are called "Distributions", not "Versions") of Linux, dalani, is that it is so flexible in it's potential applications, that it will run on anything from the bottom architecture for which it is written up to the top architecture.

[quote=LordHunter317]Mentioning Darwin is roughly akin to integrating children with learning disabilities with the honors students, FWIW.[/quote]

Oh c'mon! That's a little harsh, isn't it?  =) You big meanie.

---

### Post by davebradford on 2005-11-27
looks like it's got a lot of information and a lot of effort has been put in.. but as a noobie myself the content looks a little too "heavy" and it kinda puts me off..

---

### Post by dalani on 2005-11-28
> P-II's are rapidly approaching 10 years old. 10 YEARS! That's a HUGE amount of time in the computer industry. I think they're leaving the judgement call on hardware for application up to the individual user.

10 years?so? if linux desktop niche is to accomodate legacy machines, then it better work on older machines. MS and Apple can afford to hike up their minimum requirements for their OS since they expect users to dump their boxes for newer gear (esp. Apple who stands to gain most with hardware upgrades). 

Otherwise what's the point If someone purchases  a newer box, he usualy gets MS pre-installed right?

---

### Post by hostile on 2005-11-28
[quote=dalani]10 years?so? if linux desktop niche is to accomodate legacy machines, then it better work on older machines. MS and Apple can afford to hike up their minimum requirements for their OS since they expect users to dump their boxes for newer gear (esp. Apple who stands to gain most with hardware upgrades).

Otherwise what's the point If someone purchases a newer box, he usualy gets MS pre-installed right?[/quote]

Accomodate legacy, it already does. **Cater to?** No way. The point of Linux is not to provide a state-of-the-art OS for every Tom, Dick, and Harry out there who wants a "faster" alternative to his Windows 3.1 install on his 486SX. It's competing for the current desktops and server markets. Why do you think it's available for the x64 or PPC platforms? 

If you want Linux to run well on your machine, you're going to have to:

1) Accept the fact that Ubuntu is a leading-edge distro that will not run "quickly" on vastly outdated hardware without some serious tweaking.
2) Use the **[Search](http://www.ubuntuforums.org/search.php)** function on this BBS, roll up your sleeves, and be prepared to learn and do some serious work to get it to run the way you want it.

Expecting *any* current distro to run in a "fast" manner on old hardware is the same as expecting Windows XP or Vista to do the same - you're going to have to strip them all down to their skivvies to get the speed out of them you want.

Try **[this](http://www.ubuntuforums.org/showthread.php?t=54476&highlight=eye+candy)** for starters. It's a how-to for removing Metacity from Gnome and use Enlighten instead. Read the whole thing, as it's filled with many caveats.

Good luck.

---

### Post by dalani on 2005-11-29
Ubuntu is ahead of you there with [Xubuntu]("http://www.distroreviews.com/index.php?view=310").

As for Ubuntu competing head on with desktop and server markets, that depends on many factors. The curio market is only a fraction of a fraction of those computer enthousiasts willing to tweak linux ad finitum. 

How would for ,eg. a server, market Ubuntu have a leg up on the competetion???

---

### Post by dalani on 2005-11-29
>  He was referring to the near-mythical "social engineering" attacks, where systems are compromised by getting a human to reveal information they shouldn't, like their account password.

Social engineering? that's a high falutin' term for something trivial.

---

### Post by TeeSeeJay on 2005-12-02
[QUOTE=dalani]Social engineering? that's a high falutin' term for something trivial.[/QUOTE]

It may be "trivial" or "high-falutin'", but that's what the technique is called, all the same.

---

### Post by TeeSeeJay on 2005-12-02
A couple of comments about this server guide.

1. Run it through a spell-checker. Read Strunk & White's _The Elements of Style_. Writing != typing, unless you're Jack Kerouac.
2. Platform editorializing has no place in technical writing. I suggest you completely eliminate your mentions of Windows and focus on developing a Linux-specific server guide.

A couple of comments about the comments in this thread.

1. What you can compile to run on OS X is trivial. If all you want is a BSD server, you're going to run a BSD server. If you run OS X Server, you're doing it because you a have OS X clients you need to support or manage using the proprietary tools that they bundle with the platform (which are based, in turn, on open-source tools like openLDAP, apache, mysql, etc.).

2. If you haven't read Cliff Stoll's _The Cuckoo's Egg_ you really shouldn't be talking about what is or what isn't a vulnerability on *nix. :)

---

### Post by heftigrat on 2005-12-02
[QUOTE=Kronocide]Lord, I've visited this forum perhaps three times, read maybe a dozen posts by you, and you consistently come through as a not very friendly person, more interested in demonstrating your superiority than being of assistance. Maybe that is not the way you intend it, but it's how it comes out. Just a friendly pointer.[/QUOTE]

So I'm not the only one.

---

### Post by Zensunni on 2005-12-05
I've done a bunch of changes.....

Is this true?

"Even though much of it is open source, you usually have to wait on the company to release bug fixes and updates."

Or is there a large community that works on the open source parts of server OSX, like darwin?

Also, is this true?

"The software [windows server] requires a lot of resources, but not as much as the OS X Server. "

---

### Post by TeeSeeJay on 2005-12-05
[QUOTE=Zensunni]I've done a bunch of changes.....

Is this true?

"Even though much of it is open source, you usually have to wait on the company to release bug fixes and updates."

Or is there a large community that works on the open source parts of server OSX, like darwin?

Also, is this true?

"The software [windows server] requires a lot of resources, but not as much as the OS X Server. "[/QUOTE]

For the core components of OS X Server, you're going to want to wait for apple to release update packages. You can research these packages at apple.com/support, as there was a security package released a week or two ago. Although the underpinnings are open source packages, there is an awful lot of Apple customization, not to mention proprietary front-ends and interfaces.

I've said this before, maybe in this thread, or maybe not: if you want to run a BSD server wtih open source software, you're not going to choose OS X. If you want to  manage a group of Macs, you will.

For your second question, I have one suggestion: eliminate abstract language from your writing. "A lot of resources" is an abstract phrase that is essentially meaningless. The fact is you can "run" OS X server on any G3 and better mac, and you can "run" Windows Server on any equivalent two-generation-old x86 hardware, but whether you are successful in these endeavors has much more to do with what your goals with the server are. Minimum requirements for both of these platforms are easily available on the vendor websites. There is no reason you can't do your homework and draw your own conclusions.

---

### Post by TeeSeeJay on 2005-12-06
Also, your discussion of subnet masking is almost completely incoherent. You might want to do some additional research on that topic. For instance, subnet masks have absolutely nothing to do with "privacy and security."

---

