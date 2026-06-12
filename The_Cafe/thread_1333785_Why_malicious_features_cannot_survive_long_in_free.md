---
title: "Why malicious features cannot survive long in free software"
date: 2009-11-21
forum: The Cafe
---

### Post by youbuntu on 2009-11-21
I just wrote this for a friend, who recently challenged me to explain how malicious code can be prevented or ousted from free software. I like what I have write, so I thought I would share it. Please correct anything which is missing or incorrect, and post your version back here, with your improvements clearly marked. Thanks.


#################################################################


Imagine a program that has 1,000,000 users. Of those 1,000,000 users, let's say that 1,000 or more can program software. Let us say that there are ten improvements made to the program, by those 1,000 programmers, which introduce brilliant new features to the software. The news will soon spread to the majority of the 1,000,000 users of this program; "Have you heard about the new feature?... you can do X much more easily now, oh, and also you can export to Y format" - once the word has spread, a good percentage of these 1,000,000 users will download the improved, updated version, and the knowledge of the few, can now benefit the MANY - this is wonderful. News may spread further, to those who would have previously used the software, if it had included the now added features, having been missing from the programs functionality, previously.

Now imagine that you are a malicious programmer, and you purposefully introduce a nasty, malicious feature into the code of the program, in order to spy on the users or do nasty things to their computers or data. Imagine that you publish your own, malicious version of this "improved" software, and many people download it - let us say the very same 1,000,000 users as before. Of those 1,000,000 users, we have a maybe greater number of sharp-witted people, a great deal of which cannot program, but report something nasty having happened to their computer, data or privacy.

The 1,000 programmers out of the 1,000,000 users will now examine the source code (the open and human-readable, un-compiled form of any software) that is supplied with the "improved" malicious variant of the program, and inspect it thoroughly to see if there is anything which looks as if it will perform the malicious mis-functionality that the people have reported has happened to them. If the code is dirty and has malicious parts, the community of 1,000 will  collectively remove the malicious portions, compile the software, test it to ensure that the software still functions as expected, along with the improvements made previously, and then re-submit the cleaned version back to the community with a "safe to use" notice of some sort or other, and mark the dirty & malicious source code for deletion.

If the source code of the program does *not* contain malicious code, and it compiles properly (compilation is the transformation from human-readable source code, to binary, human non-readable code that the computer knows how to use and execute, producing the final "executable" software) the programmers will test it to ensure that the software still functions as expected, along with the improvements made previously, and then they will re-submit the cleaned and checked "safe" binary file + source code of their original "improved functionality" version of the software, and the binary executable that was reported to cause harm, will be tagged with some sort of checksum (MD5 has or SHA1 are the usual means - SHA1 is more secure). They will know that their version is clean, as they will have checked the source code, and compiled the software, before uploading it back to the download server as "safe to use"

Malicious software cannot exist for long in a free society, with such massive peer review of the source code. If the programmer who introduced the nasty features *refuses* to submit the source code for his version, that version will likely be rejected outright, and removed from the server/s.

Malicious code would find it *very* hard to survive in an open and peer-reviewed society such as that of free software.



#################################################################



Sunday 22/11/2009 Matt Foot

You may distribute and enhance this article by whatever means you deem necessary and appropriate - there is no copyright attached, and you may copy and change it as you wish :-).


[SIZE=2][COLOR=Red]**Before you reply, read this**[/COLOR][/SIZE]: [http://www.gnu.org/philosophy/can-you-trust.html](http://www.gnu.org/philosophy/can-you-trust.html)

---

### Post by HeadHunter00 on 2009-11-21
I agree.

---

### Post by youbuntu on 2009-11-21
> **headhunter00 said:**
> i agree.
:)

---

### Post by jrusso2 on 2009-11-21
Now imagine that you are a malicious programmer, and you purposefully introduce a nasty, malicious feature into the code of the program, in order to spy on the users or do nasty things to their computers or data. Imagine that you publish your own, malicious version of this "improved" software, and many people download it - let us say the very same 1,000,000 users as before. Of those 1,000,000 users, we have a maybe greater number of sharp-witted people, a great deal of which cannot program, but report something nasty having happened to their computer, data or privacy.

The 1,000 programmers out of the 1,000,000 users will now examine the source code

Who says 1000 people are going to look at the source code?

There have been security issues for years that no one found or noticed.

---

### Post by Abadon125 on 2009-11-21
And the reason there are problems with closed source operating systems is because that peer review is missing.  Users execute closed source applications or applications execute themselves unknowingly.  Because of the closed nature of everything, it is up the the companies that own the code to sort the problems out with much less man power than an entire community can give.

---

### Post by youbuntu on 2009-11-21
> **jrusso2 said:**
> Now imagine that you are a malicious programmer, and you purposefully introduce a nasty, malicious feature into the code of the program, in order to spy on the users or do nasty things to their computers or data. Imagine that you publish your own, malicious version of this "improved" software, and many people download it - let us say the very same 1,000,000 users as before. Of those 1,000,000 users, we have a maybe greater number of sharp-witted people, a great deal of which cannot program, but report something nasty having happened to their computer, data or privacy.

The 1,000 programmers out of the 1,000,000 users will now examine the source code

Who says 1000 people are going to look at the source code?

There have been security issues for years that no one found or noticed.

Who says it *needs* a precise 1,000 people?. That is just an example. It may only take 10 people, maybe you are missing the point?.

Okay, so security issues that noone found or noticed?. Well obvious they did, eventually, because if they hadn't been found, then why would you have brought up the fact that they hadn't been found?. You can't know about something you don't know about, until you *do*!. ;)

We're only human, and I am making an explicit example of how peer review works for the uninformed.

---

### Post by jrusso2 on 2009-11-21
Who says even ten will look at it?  Who says anyone but the coder will?

---

### Post by youbuntu on 2009-11-21
> **jrusso2 said:**
> Who says even ten will look at it?  Who says anyone but the coder will?

If nothing bad happens to user's computers, then I agree. You miss the point, that the bad things happening would cause people to look into the code. Chances are that *someone* will, regardless.

---

### Post by lswb on 2009-11-21
There have been non-malicious coding errors in OSS/FOSS software that have existed for years or even decades. A malicious programmer could obfuscate his purposes making it difficult to detect. 

Take a look at [http://www.c-program.com/kt/reflections-on-trusting.html](http://www.c-program.com/kt/reflections-on-trusting.html)

---

### Post by youbuntu on 2009-11-21
> **lswb said:**
> There have been non-malicious coding errors in OSS/FOSS software that have existed for years or even decades. A malicious programmer could obfuscate his purposes making it difficult to detect. 

Take a look at [http://www.c-program.com/kt/reflections-on-trusting.html](http://www.c-program.com/kt/reflections-on-trusting.html)

Difficult is far better than impossible. Source is source, and it can be read, no matter if it is difficult to understand or clear, it is readable, and someone clever can eventually find the flaw and fix it. This is my point, and you are correct I am sure, but you are pointing out an exception, *not* the rule.

---

### Post by jrusso2 on 2009-11-21
How about the kernel error that was an added coma that caused an exploit to be possible for years that no one noticed and was fixed last year?

---

### Post by youbuntu on 2009-11-21
> **jrusso2 said:**
> How about the kernel error that was an added coma that caused an exploit to be possible for years that no one noticed and was fixed last year?

Again, you're cherry-picking abstract and one-off cases to try and disprove my point. Why?. I have outlined the way that peer review works, and this is the whole basis of free software, right?. Highlighting a *few* cases to perhaps try and say that the free software ethos does not work, is just silly; we're all human, and of *course* a few fish will slip through the net. I know you can see my points, but would prefer to try and disprove a tried and tested way of working, to what end?...

As humans, not all errors and bugs are as easily as detectable as others. So would you state that this is an empirical example of why free software fails?. Thought not.

---

### Post by jrusso2 on 2009-11-21
> **glossywhite said:**
> Again, you're cherry-picking abstract and one-off cases to try and disprove my point. Why?. I have outlined the way that peer review works, and this is the whole basis of free software, right?. Highlighting a *few* cases to perhaps try and say that the free software ethos does not work, is just silly; we're all human, and of *course* a few fish will slip through the net. I know you can see my points, but would prefer to try and disprove a tried and tested way of working, to what end?...

As humans, not all errors and bugs are as easily as detectable as others. So would you state that this is an empirical example of why free software fails, every time?. Thought not.

The peer review process doesn't work the way people think is my point.  No more no less.

---

### Post by youbuntu on 2009-11-21
> **jrusso2 said:**
> The peer review process doesn't work the way people think is my point.  No more no less.

No matter what they think, it evidently *works* on the whole, due to the stability of GNU/Linux and the software you are no doubt using this very moment, right?.

So enlighten us to how it does work, and your reason for input here - that would be more useful than picking out odd examples of the failure of humans to find *every* single bug.

Thanks :)

---

### Post by BuffaloX on 2009-11-21
Your story is good, but I don't think it entirely describes the power of open source security.

First if a program with 1 mil users detect a security issue in a certain program the following is likely to happen:

½% = 5.000 are programmers, and may narrow down the problem a lot,
they are able to file much better error reports, because they can examine the source. ( This has been proven, by comparing security error reports by programmers for closed and open source projects. )

Of the ½% that are programmers, a significant part will actually try to hunt down the malicious element, to fix their own system.
This can easily exceed the total number of developers normally working on the program by a huge factor.

The possibility of open communication between everybody working on a solution accelerate the process further.

But first the malicious code must be accepted.
If you are new on a project, your code will be both examined and tested.
If it's a large project, this will happen through a development tree, it's very unlikely that decidedly malicious code will pass even this bump on the road to release.
To prevent detection before release, the malicious code may wait for a certain time to activate itself.
The longer the delay, the greater the risk of being detected before actual activation, and the shorter the delay, the greater the risk for being detected by slow progress through the development tree.

> jrusso2:
"Who says even ten will look at it? Who says anyone but the coder will?"

Theoretically a project may be completely corrupt, either by all involved being corrupt, or if the program is being developed by only one person.
In that case, it is especially beneficial to have access to the source code. It would be very stupid for such a person or group to make to Open Source Software at all.

---

### Post by BuffaloX on 2009-11-21
> **jrusso2 said:**
> How about the kernel error that was an added coma that caused an exploit to be possible for years that no one noticed and was fixed last year?

How about all those added comas in closed source that are never detected, or when detected, nobody ever hears about.

How about actually detected and utilized security holes in closed source software that goes unfixed for years, because the closed source developer doesn't care, and the affected customers can do nothing!

Nobody said that the Open source model made mistakes impossible.
But closed source make mistakes impossible to fix.

> **jrusso2 said:**
> The peer review process doesn't work the way people think is my point.  No more no less.

Yes it does.

---

### Post by 3rdalbum on 2009-11-21
The original developer will look at the source code of the "new improved fork" to see what makes it so much better, to possibly implement the changes in their own project. They notice the malicious nature of the modification and they raise the alarm. Easy.

---

### Post by Chronon on 2009-11-21
> **3rdalbum said:**
> The original developer will look at the source code of the "new improved fork" to see what makes it so much better, to possibly implement the changes in their own project. They notice the malicious nature of the modification and they raise the alarm. Easy.

This would be easily done with diff.

---

### Post by Frak on 2009-11-21
Open source != Secure. You can reason with (somewhat flawed) logic all day, but there have been problems in many open source programs that existed for a long time. Firefox, for instance, [Bug #350 went unpatched for years]("https://bugzilla.mozilla.org/show_bug.cgi?id=350"). Even though Mozilla and Firefox were open source, it took a while for somebody to release a working patch. When people aren't paid, there's not reason to be speedy in a fix.

Also, there's the "Too many people in the kitchen" problem. You can have 1,000 people watching the source code, and they can all find a bug, and they can all interpret it in different ways, and release 1,000 different fixes for the bug. All 1,000 fixes could be perfect in their own, but together than could introduce new bugs. Say you're working on a Client/Server type project and somebody fixes a bug in the Client, that doesn't mean there isn't now a problem in the Server introduced by the Client patch. If people aren't constantly going over every part of the project, there's no guarantee that new bugs won't be introduced or reintroduced.

There are great things about Open Source software, and there are good reasons to keep your source closed (see: Folding@Home, uses open source components, but released as a proprietary application). Neither implementation is perfect. Proprietary isn't fully secure just because nobody can see the source, but Open Source, even if wildly popular, isn't fully secure because it still opens up the source for "bad" people to see (don't deny it, it's perfectly true) and it doesn't guarantee speedy fixes.

---

### Post by KiwiNZ on 2009-11-21
> **glossywhite said:**
> Again, you're cherry-picking abstract and one-off cases to try and disprove my point. Why?. I have outlined the way that peer review works, and this is the whole basis of free software, right?. Highlighting a *few* cases to perhaps try and say that the free software ethos does not work, is just silly; we're all human, and of *course* a few fish will slip through the net. I know you can see my points, but would prefer to try and disprove a tried and tested way of working, to what end?...

As humans, not all errors and bugs are as easily as detectable as others. So would you state that this is an empirical example of why free software fails?. Thought not.

After reviewing several recent threads I  will ask you make your responses more considered. Others are entitled to have opposing views to yours.

---

### Post by Simon17 on 2009-11-21
I'm sorry, but this is the most ridiculous thing I've ever heard. If "something bad happened to your computer or privacy", would you:

a) review every line of every open-source application you use on your computer
b) assume you are infected with malware or your data was compromised in some other manner?

---

### Post by Exershio on 2009-11-21
Another thing people should understand is that open source software is often developed for the benefit of the community and is non-profit. What self-respecting developer would try to harm their own userbase that supports their program?

Of course it's not concrete that every open source developer has good intentions, but it's something to consider. ;)

---

### Post by Diluted on 2009-11-22
I don't see the point of your friend's question. Malicious features don't survive long in both free and proprietary software. Free software will not accept arbitrary code without looking over it. Proprietary software has some form of code review to catch bugs early and as a side benefit, stop malicious features which are not approved by the company.

I don't see how free software is better in this regard.

---

### Post by Tristam Green on 2009-11-22
> **Simon17 said:**
> I'm sorry, but this is the most ridiculous thing I've ever heard. If "something bad happened to your computer or privacy", would you:

a) review every line of every open-source application you use on your computer
b) assume you are infected with malware or your data was compromised in some other manner?

c) Re-flash the drive and be done with it.

---

### Post by youbuntu on 2009-11-22
Please read: [http://www.gnu.org/philosophy/can-you-trust.html](http://www.gnu.org/philosophy/can-you-trust.html)


> **Diluted said:**
> I don't see the point of your friend's question. Malicious features don't survive long in both free and proprietary software. Free software will not accept arbitrary code without looking over it. Proprietary software has some form of code review to catch bugs early and as a side benefit, stop malicious features which are not approved by the company.

I don't see how free software is better in this regard.

Free software is free, and the malicious code is open for *all* to see & remove if they so wish, not controlled by one company who say "trust us, we'll not harm you". See?. How do *you* know that X proprietary software has a bug, and they fix it from your bug reports?. Windows XP has backdoors in it, which spy on you and are widely known about - they have not been "fixed" yet. Every time you search for a file on your PC, Microsoft know about what you searched for, but yet this is okay?. I find your trust in an unknown quantity, the proprietary software vendor who makes you promises you cannot prove or disprove they will honour, a little worrying.



> **Simon17 said:**
> I'm sorry, but this is the most ridiculous thing I've ever heard. If "something bad happened to your computer or privacy", would you:

a) review every line of every open-source application you use on your computer
b) assume you are infected with malware or your data was compromised in some other manner?

Assumption is a dangerous thing, you'd obviously use a little common sense, and a process of deduction to ascertain when the problem arose; was it before or after the latest program you installed?. 

We are not talking about every single individual with a problem, examining *all* of the source code of every single application in their system - you've just taken this to a ridiculous extreme, but for what reason?.

I'd probably review the source code of every "free software" application on my system, too ;) were I so naive as to think that this would be an intelligent and efficient way to fix my problem/s as an individual



People, I am not saying free software is *perfect*, but I *am* saying that it is a *lot* more secure and bug/back-door free than proprietary programs. This is not even a point which I need to prove to you - you have proven it to yourselves by choosing GNU/Linux.

---

### Post by Diluted on 2009-11-22
I didn't say I completely trust proprietary vendors. I merely said it is difficult to inject unsanctioned malicious code in both software models and not be discovered. To use your example, the malicious fork was created and had credibility because it was open source and the programmer was able to produce a working product and claim it is better than the official version. In a proprietary model, I certainly wouldn't expect someone to be able to take the Windows source code, inject malicious features and then announce it to be a better Windows in some way to get people to use it. It's going to have to be an inside job, and that's assuming if they can get past code review.

Of course, this is comparing apples to oranges, so I can't say one is better than the other, which is why I said I don't see how free software is better in the context of preventing malicious features.

As for detecting malicious code, I'm sure there are plenty of ways to do that without looking at the source code. I'm not sure how security researchers do it, but they seem to be able to find all these security bugs without the source code.

How do I know if a proprietary software has a bug? When I encounter it during my usage. How do I know if they fix it? When the problem goes away after an update?

As for all these backdoor stuff, do you have any evidence to back it up?

---

### Post by youbuntu on 2009-11-22
> **Diluted said:**
> I didn't say I completely trust proprietary vendors. I merely said it is difficult to inject unsanctioned malicious code in both software models and not be discovered. To use your example, the malicious fork was created and had credibility because it was open source and the programmer was able to produce a working product and claim it is better than the official version. In a proprietary model, I certainly wouldn't expect someone to be able to take the Windows source code, inject malicious features and then announce it to be a better Windows in some way to get people to use it. It's going to have to be an inside job, and that's assuming if they can get past code review.

Of course, this is comparing apples to oranges, so I can't say one is better than the other, which is why I said I don't see how free software is better in the context of preventing malicious features.

As for detecting malicious code, I'm sure there are plenty of ways to do that without looking at the source code. I'm not sure how security researchers do it, but they seem to be able to find all these security bugs without the source code.

How do I know if a proprietary software has a bug? When I encounter it during my usage. How do I know if they fix it? When the problem goes away after an update?

As for all these backdoor stuff, do you have any evidence to back it up?

You obviously care about this issue, so I am going to ask you to watch some videos - Google this man - "Richard Stallman" - and take some time out to digest his lectures. He is better qualified than me, to explain all the finer details, and no, personally I do not have proof that the XP back door exists, but then, do you have proof to the contrary?. ;)

It is widely known that Richard Stallman is very outspoken but rarely wrong. All will become clear.

---

### Post by Diluted on 2009-11-22
Um, I started off giving an opinion on your piece and I'm just replying to the points you've directed at me.

Unfortunately, I do not have time to look up Richard Stallman. Can you give me a summary of his ideas which apply to the discussion?

As for the XP backdoor, it's been out for around 8 years and I'm sure it's been hammered by all sorts of people and things over the years. If there was truly a backdoor being utilized, I'd expect we'd be hearing about it long ago.

Furthermore, I don't believe Microsoft has any incentive to utilize these backdoors, since they would risk driving the business world to other operating systems.

---

### Post by koenn on 2009-11-22
> **Diluted said:**
> I didn't say I completely trust proprietary vendors. I merely said it is difficult to inject unsanctioned malicious code in both software models and not be discovered. To use your example, the malicious fork was created and had credibility because it was open source and the programmer was able to produce a working product and claim it is better than the official version. In a proprietary model, I certainly wouldn't expect someone to be able to take the Windows source code, inject malicious features and then announce it to be a better Windows in some way to get people to use it. It's going to have to be an inside job, and that's assuming if they can get past code review.

Of course, this is comparing apples to oranges,
One of the claims that people often make against open source, is that "if everyone can freely modify the program, what's to stop anyone from making a booby-trapped, backdoored version ?" glossywhite is countering this by explaining how those things would not go unnoticed, and will consequently get fixed.

Since proprietary programs can only be modified by the person/company that owns them, the "3rd party malicious modification" case doesn't apply to them. However
- they may contain malicious components anyway, on purpose. Freeware programs acting as trojans, for instance
 -they may contain exploitable bugs and the only option to have them fixed is wait for the vendor to release a fix. The assumption is that an open source process can deliver fixes way faster than a proprietary vendor.

So the availability of source code does not make open source programs inherently less secure.

---

### Post by youbuntu on 2009-11-22
> **Diluted said:**
> Um, I started off giving an opinion on your piece and I'm just replying to the points you've directed at me.

Unfortunately, I do not have time to look up Richard Stallman. Can you give me a summary of his ideas which apply to the discussion?

As for the XP backdoor, it's been out for around 8 years and I'm sure it's been hammered by all sorts of people and things over the years. If there was truly a backdoor being utilized, I'd expect we'd be hearing about it long ago.

Furthermore, I don't believe Microsoft has any incentive to utilize these backdoors, since they would risk driving the business world to other operating systems.

Richard Stallman is the founder of the FSF (Free software foundation) and the founder of the GNU project. I suggest you may like to find the time to visit: [http://www.fsf.org]("http://www.fsf.org/")
as I also do not have time to sit here and explain it all to you, when you could just click the link and read :)

> **koenn said:**
> One of the claims that people often make against open source, is that "if everyone can freely modify the program, what's to stop anyone from making a booby-trapped, backdoored version ?" glossywhite is countering this by explaining how those things would not go unnoticed, and will consequently get fixed.

Since proprietary programs can only be modified by the person/company that owns them, the "3rd party malicious modification" case doesn't apply to them. However
- they may contain malicious components anyway, on purpose. Freeware programs acting as trojans, for instance
 -they may contain exploitable bugs and the only option to have them fixed is wait for the vendor to release a fix. The assumption is that an open source process can deliver fixes way faster than a proprietary vendor.

So the availability of source code does not make open source programs inherently less secure.

Indeed so - that is exactly it!.

---

### Post by cascade9 on 2009-11-22
Umm...it all depends on what you call malicious software. Just cause its open source doesnt stop spyware, and I count that as malicious. See Google Chrome and the RLZ identifier, + other optional 'features' (Client ID, Suggest, etc). 

Of course, being open source, there is at least a version with all of that stripped out.

[http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php)[B]
[/B]

---

### Post by Diluted on 2009-11-22
> **koenn said:**
> One of the claims that people often make against open source, is that "if everyone can freely modify the program, what's to stop anyone from making a booby-trapped, backdoored version ?" glossywhite is countering this by explaining how those things would not go unnoticed, and will consequently get fixed.

Since proprietary programs can only be modified by the person/company that owns them, the "3rd party malicious modification" case doesn't apply to them. However
- they may contain malicious components anyway, on purpose. Freeware programs acting as trojans, for instance
 -they may contain exploitable bugs and the only option to have them fixed is wait for the vendor to release a fix. The assumption is that an open source process can deliver fixes way faster than a proprietary vendor.

So the availability of source code does not make open source programs inherently less secure.

To be honest, I don't think open source is less secure than it's proprietary counterpart. Both has its advantages and disadvantages and it would be difficult to compare both of them fairly. However, I don't think one is better than the other. In my opinion, the way to provide secure programs is to follow the approach of OpenBSD or the Microsoft SDL.

As for software containing malicious components on purpose, I'm sure someone will notice something is amiss at some point. It's just like the example mentioned by glossywhite, where people reported something bad has happened as a result of the malicious program. The only advantage I can think of for open source is that programmers can proactively look for malicious features. But I don't think they would be willing to proactively comb through the source of an OpenOffice fork just to see if there's anything bad in it.

In fact, there are some Windows software repositories (Softpedia, but I don't know others) which tells you whether there are any spyware or unwanted things for a particular software. If you're really paranoid, you could use a packet sniffer or an HIPS to detect when a program is acting strangely.

As for waiting for the vendor to fix bugs, it depends on the severity of it. If it was truly severe, then I don't think there is any reason for the vendor not to publish an update as fast as they can. I don't see how this differs in open source. Developers have to determine the severity of bugs and whether it warrants a fix, as you can see in bug trackers all the time.

I'm sure every vendor has an interest in fixing bugs in the programs. After all, every bug a customer encounters can potentially turn them away for life. However, I think you're forgetting that patches need to undergo testing to make sure there are no regressions. Open source being able to deliver a fix faster does not mean it is better.

This is a reason why Microsoft may not seem to patch as fast as they should. They know if they pushed an update which breaks things, their customers would simply not apply the update, which is bad especially for security vulnerabilities. As a company specializing in backward compatibility, they need to do their best to make sure every fix does not break something else.

> **glossywhite said:**
> Richard Stallman is the founder of the FSF (Free software foundation) and the founder of the GNU project. I suggest you may like to find the time to visit: [http://www.fsf.org]("http://www.fsf.org/")
as I also do not have time to sit here and explain it all to you, when you could just click the link and read :)
I'm afraid I really don't have the time to read through a website. I'm supposed to be finishing my assignment. :(

---

### Post by youbuntu on 2009-11-22
> **Diluted said:**
> ...I'm afraid I really don't have the time to read through a website. I'm supposed to be finishing my assignment. :(

You obviously have time, because you're here, posting comments. You could have spent that time clicking & reading ;)

---

### Post by Diluted on 2009-11-22
> **glossywhite said:**
> You obviously have time, because you're here, posting comments. You could have spent that time clicking & reading ;)
I have time, but not the quantity that would allow me to read through FSF. A post from this forum has much less text than one of the GNU licenses. As for my replies, it is not difficult to regurgitate what I know. Reading through FSF would mean absorbing new knowledge and even then, I might not understand or be familiar with it enough to be qualified to talk about it.

---

### Post by Digikid on 2009-11-22
....

My Brain Hurts.

---

### Post by red_Marvin on 2009-11-22
As I see it, open source software is not *inherently* more secure than closed source software. It is possible to for projects in both domains to have good and bad code review and bug fixing.

However, when it comes to css, there are bounds on the quality of the testing of the software, ranging from none to a very skilled qc department.
But for oss, another dimension of of qc is added because even people not really involved in the project can still provide input.

So an oss project has the possibility of having good qc, even if the "official" qc team is incompetent, while css does not.

---

### Post by Diluted on 2009-11-22
> **red_Marvin said:**
> As I see it, open source software is not *inherently* more secure than closed source software. It is possible to for projects in both domains to have good and bad code review and bug fixing.

However, when it comes to css, there are bounds on the quality of the testing of the software, ranging from none to a very skilled qc department.
But for oss, another dimension of of qc is added because even people not really involved in the project can still provide input.

So an oss project has the possibility of having good qc, even if the "official" qc team is incompetent, while css does not.
Indeed. I think OpenBSD and Microsoft are examples of how security is not determined by whether it is open sourced or not, but what they are doing to secure their software.

I will however, have to disagree with you on quality control, because proprietary software do have alpha/beta releases, so the public can get hold of them and provide input as well.

---

### Post by koenn on 2009-11-22
> **Diluted said:**
>   ... 
Again, what glossywhite and I were doing was merely drawing a rough sketch to counter the FUD.

As for all vendors having an interest in fixing bugs, your reasoning does not apply to vendors with a monopoly. IE used to be notorious for its long-standing critical bugs.

---

### Post by youbuntu on 2009-11-22
> **Diluted said:**
> Indeed. I think OpenBSD and Microsoft are examples of how security is not determined by whether it is open sourced or not, but what they are doing to secure their software.

I will however, have to disagree with you on quality control, because proprietary software do have alpha/beta releases, so the public can get hold of them and provide input as well.

Input does not guarantee that the company *will* listen to you *or* fix the bugs, as you have no *proof* they have done this.

---

### Post by RiceMonster on 2009-11-22
> **glossywhite said:**
> Input does not guarantee that the company *will* listen to you *or* fix the bugs, as you have no *proof* they have done this. 

Are you suggesting bugs in FOSS always get fixed? It's the same thing; you can't guarantee that bug reports will result in a bug fix, or  a patch being accepted. Read [this]("http://www.fewt.com/2009/10/i-give-up.html") to get an idea of what I'm talking about, or read up on some of the history behind the pidgin devs.

Also, your proof that the bug got fixed in proprietary software is that it doesn't occur anymore.

---

### Post by Diluted on 2009-11-22
> **koenn said:**
> Again, what glossywhite and I were doing was merely drawing a rough sketch to counter the FUD.

As for all vendors having an interest in fixing bugs, your reasoning does not apply to vendors with a monopoly. IE used to be notorious for its long-standing critical bugs.
I see. Although I haven't seen this particular FUD of malicious features. Maybe I need to read more.

That depends on what type of bugs you're talking about. Rendering bugs? Security bugs? I'd like to think currently the latest version of IE is fairly secure (although not the most secure).

> **glossywhite said:**
> Input does not guarantee that the company *will* listen to you *or* fix the bugs, as you have no *proof* they have done this.
That is true. But the same applies to open source. Developers will not guarantee that they will fix whatever you've told them. An example would be Pidgin with its resizable text field. In both development models, you still need to convince the developers that it is a bug worth fixing.

As for proof, RiceMonster has answered that. If you know the steps needed to trigger a bug, in order to report it, then you can try those steps again to see if it's fixed.

---

### Post by youbuntu on 2009-11-22
> **RiceMonster said:**
> Are you suggesting bugs in FOSS always get fixed? It's the same thing; you can't guarantee that bug reports will result in a bug fix, or  a patch being accepted. Read [this]("http://www.fewt.com/2009/10/i-give-up.html") to get an idea of what I'm talking about, or read up on some of the history behind the pidgin devs.

Also, your proof that the bug got fixed in proprietary software is that it doesn't occur anymore.

No, *you* are implying that I have said that, by assumption, and we all know what assumption is the mother of!. So a proprietary software bug is fixed, but how do you know what other nasty code is hiding in there, spying on you?... answer: you *don't* and probably never would. You are making the blind assumption that it is *only* bugs we need to look out for. How can you identify that nasty spying feature, if it doesn't exhibit any traits?. Do I need to explain the very purpose of spying?... hopefully not. :rolleyes:

My thread details *malicious features*, not bugs - maybe you could read the thread title again?

Bottom line: noone can guarantee ANYTHING, but we have a greater chance of seeing nasty code in free software, as it is open and not down to trusting the corporation and their "word" (whatever that is worth, is equal to zero).

---

### Post by RiceMonster on 2009-11-22
> **glossywhite said:**
> No, *you* are implying that I have said that, by assumption, and we all know what assumption is the mother of!. So a proprietary software bug is fixed, but how do you know what other nasty code is hiding in there, spying on you?... answer: you *don't* and probably never would. You are making the blind assumption that it is *only* bugs we need to look out for. How can you identify that nasty spying feature, if it doesn't exhibit any traits?. Do I need to explain the very purpose of spying?... hopefully not. :rolleyes:

My thread details *malicious features*, not bugs - maybe you could read the thread title again?

Bottom line: noone can guarantee ANYTHING, but we have a greater chance of seeing nasty code in free software, as it is open and not down to trusting the corporation and their "word" (whatever that is worth, is equal to zero).

You know, reading the source code is not the only way to know a program is spying on you. It would be much better to use a packet logger like wireshark, which can be done with proprietary software, rather than reading through tens of thousands of lines of source code. There's other ways too. Did you here about when Sony got caught putting rootkits on people's computers? Guess who had access to the source code? Sony, and that's it.

---

### Post by youbuntu on 2009-11-22
> **RiceMonster said:**
> You know, reading the source code is not the only way to know a program is spying on you. It would be much better to use a packet logger like wireshark, which can be done with proprietary software, rather than reading through tens of thousands of lines of source code.

"Better"? how?.

You read the source if it is free software, or you use the packet sniffer if it is proprietary software. Your use of the word "better" makes no sense. So what if the proprietary software is spyware - I wouldn't be using it in the first place to put myself at risk or compromise my freedoms, so why should I care?. Do you not realize this is one of the reasons *why* people use GNU/Linux?.

Rootkit? old news... and did you honestly think that, even IF Sony had admitted the rootkit and IF the code were not spying on people in their audio CDs, that Sony would have released the source code anyway, as a proprietary company (and that is an UNDERSTATEMENT - miniDISC anyone?... no?... how about a UMD drive?... no? :(, well how about a memory stick?!) rofl. So do you think that Sony should have made the source available, and have told their "customers" (?!) about the rootkit, to be fair to them?. I can see people with their packet sniffer, looking for the rootkit every time they played a CD, because of course... they knew about it, right, because it was announced and easily detectable?.

Sony are possibly one of *the* biggest examples of "fail" & "facepalm" ever.

:rolleyes:

You really do make some irrelevant comments.

---

### Post by RiceMonster on 2009-11-22
> **glossywhite said:**
> "Better"? how?.

You read the source if it is free software, or you use the packet sniffer if it is proprietary software. Your use of the word "better" makes no sense.

 Better, as in faster. Either way, you just agreed with me that you don't need the source code to detect spying behaviour.

---

### Post by Diluted on 2009-11-22
> **glossywhite said:**
> No, *you* are implying that I have said that, by assumption, and we all know what assumption is the mother of!. So a proprietary software bug is fixed, but how do you know what other nasty code is hiding in there, spying on you?... answer: you *don't* and probably never would. You are making the blind assumption that it is *only* bugs we need to look out for. How can you identify that nasty spying feature, if it doesn't exhibit any traits?. Do I need to explain the very purpose of spying?... hopefully not. :rolleyes:
As I've said before, if there's malicious features, then someone will be affected by it in some way or another. Their computer may act strangely, or they may find private information available to strangers. In this case (and for open source, as you state in your example), the public can be alerted and even if the code is proprietary, things like firewall and packet sniffers may confirm these malicious features. Some may even disassemble it if necessary.

Just because the spying feature needs to be hidden, that doesn't mean it won't exhibit any traits. It needs some way to transmit the information elsewhere. A firewall may be able to detect the outbound connection and you can block it before it goes anywhere.

> **glossywhite said:**
> My thread details *malicious features*, not bugs - maybe you could read the thread title again?
I believe RiceMonster's quote contained a post of you talking about companies not guaranteeing to fix a big.

> **glossywhite said:**
> Bottom line: noone can guarantee ANYTHING, but we have a greater chance of seeing nasty code in free software, as it is open and not down to trusting the corporation and their "word" (whatever that is worth, is equal to zero).
Yes, that is an advantage for open source. However, that requires proactive action and the larger the codebase, the less incentive for programmers to go through the codebase just to look for these nasty code. I believe it is more reliable to rely on users experiencing bad things as a result of using the program.

> **glossywhite said:**
> "Better"? how?.

You read the source if it is free software, or you use the packet sniffer if it is proprietary software. Your use of the word "better" makes no sense.
I can see RiceMonster's point of view. If there was an application phoning home, it would be much faster to log where the packets are transmitted to than to read a million lines of source code just to find the relevant piece of code responsible.

---

### Post by koenn on 2009-11-22
> **Diluted said:**
>  Although I haven't seen this particular FUD of malicious features. 
It comes up occasionaly in conversations with people who don't fully understand what open source  or free software is, although it's diminishing. It used to be more common 5 years or so ago. 

I suppose it came from people's experience with freeware that carries viruses and stuff, and then they get those strange ideas about free software (or open source) such as that it would be easier to create such malware if "anyone can freely modify any program".

An other common misconception, along the same lines, was that open source programs would be easy to exploit, because you can look at the source code and see how it works or find exploitable bugs more easily.

---

### Post by youbuntu on 2009-11-22
> **RiceMonster said:**
> Better, as in faster. Either way, you just agreed with me that you don't need the source code to detect spying behaviour.

So you're basically just looking for people to agree with you?. No, you don't NEED the source code, but I think you are just here to be pedantic - again, how is that relevant in the context of free software?.

[IMG]http://4.media.tumblr.com/0LOD7ELvfkb7ceppKRSsR1epo1_500.jpg[/IMG]

---

### Post by Diluted on 2009-11-22
> **koenn said:**
> It comes up occasionaly in conversations with people who don't fully understand what open source  or free software is, although it's diminishing. It used to be more common 5 years or so ago. 

I suppose it came from people's experience with freeware that carries viruses and stuff, and then they get those strange ideas about free software (or open source) such as that it would be easier to create such malware if "anyone can freely modify any program".

An other common misconception, along the same lines, was that open source programs would be easy to exploit, because you can look at the source code and see how it works or find exploitable bugs more easily.
In that case, I think it might be easier to talk about how distributions won't accept arbitrary packages and they're fine as long as they stick to them. I do think it's almost impossible to get people to download these malicious software since it doesn't go through their package management system and it is not officially supported by anyone credible.

As for open source being easier to exploit, I don't think their fears are unfounded, but I'd say it depends on how skilled the white and black hackers are at the moment. Open source does make it easier to find exploits, but then it depends on who found it first. I'm just speculating here so it may work differently in the real world.

---

### Post by youbuntu on 2009-11-22
Folks, please read this carefully, as there seems to be a lot of mixing up of the terms "free software" and "Open-source" (and also the dreaded "FOSS").

[http://en.wikipedia.org/wiki/Open_source_software#Open_source_software_vs._free_software](http://en.wikipedia.org/wiki/Open_source_software#Open_source_software_vs._free_software)

This is *not* a nitpick - they are similair in their mechanics, but a world apart in their ethics, and I think people *need* educating as to what the differences are.

Thanks.

---

### Post by Diluted on 2009-11-22
> **glossywhite said:**
> Folks, please read this carefully, as there seems to be a lot of mixing up of the terms "free software" and "Open-source" (and also the dreaded "FOSS").

[http://en.wikipedia.org/wiki/Open_source_software#Open_source_software_vs._free_software](http://en.wikipedia.org/wiki/Open_source_software#Open_source_software_vs._free_software)

This is *not* a nitpick - they are similair in their mechanics, but a world apart in their ethics, and I think people *need* educating as to what the differences are.

Thanks.
Um, are we discussing the four freedoms of free software? I was under the impression we were talking about the technical merits of open source and proprietary development.

In fact, I've just read the first post in the topic again and I don't see any mention of the four freedoms. I see the mention of being able to see the source code, so I assume open source is applicable to this discussion.

---

### Post by RiceMonster on 2009-11-22
> **glossywhite said:**
> So you're basically just looking for people to agree with you?.

And you aren't? If not, then why do you make long threads asserting your views on free software?

> **glossywhite said:**
> No, you don't NEED the source code, but I think you are just here to be pedantic

I disagreed with you, and this board is for discussion. AM I not allowed to state my opinion?

> **glossywhite said:**
> again, how is that relevant in the context of free software?.

How is it not? The argument about "thousands of eyes viewing the source code" suggests that you can get away with malicious features in proprietary software, which you claimed [here](http://ubuntuforums.org/showpost.php?p=8366274&postcount=42) by stating "but how do you know what other nasty code is hiding in there, spying on you?... answer: you *don't* and probably never would". I was saying you're wrong, and you agreed with me.

---

### Post by koenn on 2009-11-22
> **Diluted said:**
> 
As for open source being easier to exploit, I don't think their fears are unfounded, but I'd say it depends on how skilled the white and black hackers are at the moment. Open source does make it easier to find exploits, but then it depends on who found it first. I'm just speculating here so it may work differently in the real world.
The main difference,imo, is that the open source developer knows his source will be open, so he can't rely on obscurity, he needs to know his protocols, algorithms, and his implementation, are inherently secure. Closed source can be more easily tempted in taking shortcuts and rely on the obscurity of their design and implementation (and then find out that some people are capable of breaking it nonetheless). 

It's somewhat similar to cryptography using open, public, peer-reviewed algorithms and protocols.

---

### Post by Mornedhel on 2009-11-22
I'll just leave [this link](http://cm.bell-labs.com/who/ken/trust.html) here.

For those not interested in reading it, or those who don't have the first clue about programming (basic notions required only), or those whose brain hurts after reading it and still haven't understood (it's kind of mind-blowing when you finally understand), here's the gist of it.

> You can't trust code that you did not totally create yourself. [...] No amount of source-level verification or scrutiny will protect you from using untrusted code.

(the rest of the page presents a clever way to introduce trojan code into a project, such that the code in question will never show *anywhere* in the source)

This includes open-source software. Emphasis on "totally". To place 100% trust in code (assuming for now it's bug-free), you'll need to have personally written the code, the compiler, all other utilities in your toolchain (linker etc), *and* the platform they're running on. You're probably safe once you've gotten to the compiler that produced that platform, or the hardware level, whichever comes first.

Of course, you can also place a certain level of trust into the programmers of the other parts you're depending on. This is probably why FOSS works: because you're trusting the other participants to some degree, and if not, you're trusting the guys who review code, or the project leader who welcomed the other participants in.

---

### Post by Diluted on 2009-11-22
> **koenn said:**
> The main difference,imo, is that the open source developer know his source will be open, so he can't rely on obscurity, he needs to know his protocols, algorithms, and his implementation, are inherently secure. Closed source can be more easily tempted in taking shortcuts and rely on the obscurity of their design and implementation (and then find out that some people are capable of breaking it nonetheless). 

It's somewhat similar to cryptography using open, public, peer-reviewed algorithms and protocols.
The examples you've mentioned could probably be implemented using existing libraries, so obfuscation may not be required there. For other code, I'd agree with you, although I think it depends on how good the developer is. A developer may use workarounds regardless of an open source or closed source model because he/she could not think of a proper implementation or because of time constraints. Perhaps a developer has its reasons for using obscurity? It depends on the circumstances.

---

### Post by Frak on 2009-11-22
> **glossywhite said:**
> It is widely known that Richard Stallman is very outspoken but rarely wrong. All will become clear.

[IMG]http://4.media.tumblr.com/0LOD7ELvfkb7ceppKRSsR1epo1_500.jpg[/IMG]

---

### Post by youbuntu on 2009-11-22
> **Diluted said:**
> Um, are we discussing the four freedoms of free software? I was under the impression we were talking about the technical merits of open source and proprietary development.

In fact, I've just read the first post in the topic again and I don't see any mention of the four freedoms. I see the mention of being able to see the source code, so I assume open source is applicable to this discussion.

I was pointing out the way people use one term, and mean the other, if they even know the difference, that is. There is an important distinction, and yes, it is relevant.

---

### Post by KiwiNZ on 2009-11-22
glossywhite please read again post #20

Thread closed

---

