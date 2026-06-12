---
title: "Linux kernel: GPLv2 or GPLv3 poll"
date: 2006-11-15
forum: The Cafe
---

### Post by deanlinkous on 2006-11-15
Found this at another forum...

> Since we have heard from all the big guns about GPLv3 I thought a poll for Joe User to have a say about it would be cool. So here it is. Assuming that GPL v3 is possible of course! Feel free to post the link anywhere you wish.

[http://poll.pollcode.com/vR](http://poll.pollcode.com/vR)


---

### Post by deanlinkous on 2006-11-15
Just to clear up the issue. That is just a general poll site, nothing weird or anything. You do not have to register or anything at all. Just select which one and click.

---

### Post by shining on 2006-11-15
Do you have any links where this issue is explained and disputed?

---

### Post by deanlinkous on 2006-11-15
Explain the kernel GPLv2/GPLv3 dilema. Whew, where have you been. :D Just kidding. Hard to provide any links about it.
If you know what the GPL is and the differences in v2 and v3(still in draft) then you are likely on one side or the other. The Linux kernel is covered under v2 and has no (current) plans to move to v3. This poll gives the user a voice in the matter. A voice that probably will not make a squat bit of difference but something that at least says whether users as a whole would be interested in seeing the kernel move to v3.

oh okay some linky thingys, trying to be as impartial as possible
[http://www.groklaw.net/articlebasic.php?story=20060118155841115](http://www.groklaw.net/articlebasic.php?story=20060118155841115)
[http://www.fsfeurope.org/projects/gplv3/diff-gplv2-draft2.en.html](http://www.fsfeurope.org/projects/gplv3/diff-gplv2-draft2.en.html)

---

### Post by deanlinkous on 2006-11-15
Thanks to all who participate!

---

### Post by deanlinkous on 2006-11-16
Come on now! Roll out and vote...

---

### Post by Sushi on 2006-11-16
It's impossible for the kernel to move to V3, so the poll is meaningless.

---

### Post by deanlinkous on 2006-11-16
First, it isn't impossible at all.

Second of all it is just a poll for joe user to say to the kernel devs "hey I like v3" and maybe we can make them realize that at least some users are interested in v3.

---

### Post by Sushi on 2006-11-16
> **deanlinkous said:**
> First, it isn't impossible at all.

It would require a go-ahead from every single person who has code in the kernel. There are thousands of those people, many of them have vanished and/or died. If they can't get that approval (and they can't), the developers would have to re-write the "offending" code from scratch.

So they would have to get in touch with every single code-constributor. If they can't get in touch with them, or they refuse to move to V3, they would have to find the code they contributed, and re-write it from scratch.

Is it really worth it? Is there something wrong with V2?

---

### Post by deanlinkous on 2006-11-16
Well, if they have vanished or died then do you really think they care if the code goes to v3.

Move it to v3, wait for them to complain and then ask for permission if they say "no" THEN rewrite it. Honestly, why would anyone complain if they have "vanished"? And if they are dead....well I doubt they will complain to loudly.

Please remember that Linus only added the "v2 only" part about five years ago. I have no idea if those that have vanished more than five years ago meant for their code to be under "v2 or later" or "only v2" but somehow Linus did? None of them seemed to complain too loudly when he added specifically the "v2 only".

Is something wrong with v2? Yes, in a way. It was wrote a long time ago before the internet became popular and software went whizzing around in so many forms. It was wrote by one man that many people consider a nut instead of being influenced by the community as the current draft is. Most things change over time, I do not see why a license would not.

---

### Post by Sushi on 2006-11-16
> **deanlinkous said:**
> Well, if they have vanished or died then do you really think they care if the code goes to v3.

It doesn't work that way. The code stays licensed under it's license, even if it's original author dies.

> Move it to v3, wait for them to complain and then ask for permission if they say "no" THEN rewrite it.

So Microsoft could take Linux-kernel, and close it. And only if the Linux-developers complained, THEN they should stop abusing the license? If things worked like you suggested, then Linux-folks would spend all their times fighting copyright-violators. You do not violate the license and see if someone complains. You abide by the license, period.

> Honestly, why would anyone complain if they have "vanished"? And if they are dead....well I doubt they will complain to loudly.

The license of the software is not dependant on the status of the author. If the author dies, the copyright does not change to public domain.

---

### Post by argie on 2006-11-16
I guess it's okay to think there was a GPLv1? How did they switch that to GPLv2?

---

### Post by Rhapsody on 2006-11-16
> **argie said:**
> I guess it's okay to think there was a GPLv1? How did they switch that to GPLv2?

Wasn't much of a problem for Linux since Linux Torvalds only started work on it in 1991, the same year as the finalization of the GPLv2, and only GPLed it some time after he started. With a small project and only a handful of a programmers, it wouldn't be too hard.

Linux is a lot bigger now though, so moving it from the GPLv2 to the GPLv3 would be *much* harder. It wouldn't be impossible, though it would slow progress on it for a while as a lot of code got rewritten, and would need the cooperation of the top code contributors (who are mostly opposed from what I've heard).

I'm not too scared though, as I'm fairly confident everything will work out in the end. The people involved in this debate can be a bit weird at times, but none of them are stupid. Linux won't die.

---

### Post by SunnyRabbiera on 2006-11-16
I am not big on GPL v3, in some ways its good but in many others its bad.
Wose comes to wose we can shoot for a BSD liecence :P

---

### Post by deanlinkous on 2006-11-16
Well do you know how much code was written by those that have disappeared or passed away? I don't have any idea myself. I find it hard to believe that un-maintained code is still used after years and years.

> It doesn't work that way. The code stays licensed under it's license, even if it's original author dies.
Thats right. And if they submitted code without specifically stating "v2 only" then some people (myself included) take that to mean that the standard boiler plate applies which specifcially says "v2 or later". So technically the code may very well already be considered (by some at least) to be v2 or later code and Linus changing the copyright file to say "v2 only" is not valid for the whole work but only for his part.

> 
So Microsoft ....

Huh? Where did I mention microsoft. MS can take the work and follow the rules of the GPL if they wish.

> The license of the software is not dependant on the status of the author. If the author dies, the copyright does not change to public domain. Thats right but a license is different than copyright and the license provides me rights.

You seem to take it for granted that those dead coders only wanted v2 yet if it wasn't specifically stated by them then one could assume either way and be just as correct and legal in using the code.

---

### Post by shining on 2006-11-16
Well, I don't understand this part fully:
[http://lwn.net/Articles/169158/](http://lwn.net/Articles/169158/)

So I'm still without opinion.

---

### Post by deanlinkous on 2006-11-16
I like this one
[http://lkml.org/lkml/2006/1/30/100](http://lkml.org/lkml/2006/1/30/100)

The question is - why not move to GPLv3?

---

### Post by shining on 2006-11-16
> **deanlinkous said:**
> 
The question is - why not move to GPLv3?

Why would they spend a huge time switching if it isn't even clear the GPLv3 is better?
And even if it's better, it needs to be worth the effort.
Now maybe it is, and in this case, I hope it'll eventually move to GPLv3. But well, it doesn't seem to be obvious.

---

### Post by neowolf on 2006-11-16
I voted GPLv2, like the other 36%.
My reasoning is that the anti-DRM, anti-Patent and anti-Trusted Computing restrictions in GPLv3 will hinder Linux on mobile devices where there are likley to be alot of patents, and hardware systems to load only the approved kernel, so not being able to do this under new liscene terms will make Linux less viable in this area. Devices such as portable media players like MP3 players will in many cases have to deal with DRM to use content so anti-DRM clauses will also hinder Linux viability in this sector as well.
And as Linus et al say, it isn't the software dev's job to tell the hardware manufacturers what to do. Until the GPLv3 is tamed in these respects it would be better to keep the kernel under the GPLv2 in my humble opinion...

---

### Post by shining on 2006-11-16
> **Bells said:**
> Of course, the idea that more restrictions makes something more free is an idea you probably have to have a special kind of mindset to have. And by special i do mean disfunctional.

Isn't that exactly what open source licenses are?

---

### Post by snay on 2006-11-16
> **shining said:**
> Well, I don't understand this part fully:
[http://lwn.net/Articles/169158/](http://lwn.net/Articles/169158/)

So I'm still without opinion.
What Linus is saying in this email is that the part that specifies wherther the software can be used with v2 *or later* is only in the preamble. That is the introduction to the licence, its just thrown on top of the text files distributed with the source to make things clearer. However in this case it does a pretty poor job at clarifying the issue, as the actual legaly binding part of the licence does not specifically say that versions of the licence are interchangeable. Also some bits of it can be licenced under the GPLv3 if their author allows it, but by default they cannot. The contributor must specify to allow a path to use the GPLv3. IANAL.

IMO the whole DRM clause in the v3 is the sticking point. It isnt the job of a *free*. licence to dictate what the code can be implemented for. The job of a *free* licence is to specify how the code can be distributed. Its all just sour grapes from the TIVO incident AFAIK. I am against updating the licence to v3. If it aint broke dont fix it, and I dont agree with the DRM part of the licence. Plus Stallmans a bit creepy... copyleft? Seriously. Awful name.

---

### Post by deanlinkous on 2006-11-16
Yes Stallman is a bit creepy, and smelly, and hairy, and likes nasal sex too much....so please let that influence your decision regarding a new license.

v3 is not anti-anything it is pro-freedoms same as v2 if something has come along that attacks freedoms then that thing is anti-freedoms not the other way around. Blame the inventors of DRM for being anti-freedoms instead of v3 being anti-DRM please.

The fact that DRM is possible with v2 is not because v2 allowed it or was less restrictive but simply because when v2 was wrote it wasn't a possibility at all. v2 is still about users being able to get the code, modify the code and run the code yet at the time of writing all that was needed to do that was access to the code. DRM now makes that impossible.

The reason I posted a link to the draft differences is so people could realize that with draft 2 things have been changed and implemented that will allow for both sides position on the issue. DRM is posssible with draft 2 but still maintains basic software freedoms.

---

### Post by deanlinkous on 2006-11-16
here is a link to a OLDER v2 to v3 comparison
[http://www.groklaw.net/articlebasic.php?story=20060118155841115](http://www.groklaw.net/articlebasic.php?story=20060118155841115)

and here is a comparison of v3 draft 1 and v3 draft 2
[http://www.fsfeurope.org/projects/gplv3/diff-draft1-draft2.en.html](http://www.fsfeurope.org/projects/gplv3/diff-draft1-draft2.en.html)

These are simply side by side comparisons only...

---

### Post by Bells on 2006-11-16
> **deanlinkous said:**
> ignoring you since all the posts you make on these forums are offensive, rude and antagonistic...

Well, the premise depends i'd sy, i am antagonstic towars those vehemently opposed to CS, but i am very much a proponent of FLOSS.

OpenSuSE community and devs will do whatthey have always done regardless and i suggest you stop whining and start coding.

Don't mind me though, i am not involved in neither Ubuntu nor OpenSuSE.

Patrick V.

P

---

### Post by Bells on 2006-11-16
> **deanlinkous said:**
> ignoring you since all the posts you make on these forums are offensive, rude and antagonistic...

Apart from most devs disagreeing with the new vrsion most users of often software feel the same way, free sotware, not bound by restrictions set by a licence mor rstrictive than the MS EULA.

You want it free, you release it BSD, other licences are just wannabee free.

For real freedom, you use OpenBSD.

---

### Post by BWF89 on 2006-11-16
Gpl 2.0

---

### Post by deanlinkous on 2006-11-16
Vote on GPLv2 or GPLv3 for the linux kernel! Nothing official, just having a little fun.

[http://poll.pollcode.com/vR](http://poll.pollcode.com/vR)

---

### Post by deanlinkous on 2006-11-16
Good article about how v3 draft 2 has made some changes to address some of the concerns of the first draft.

[http://kerneltrap.org/node/7238](http://kerneltrap.org/node/7238)

---

### Post by Sushi on 2006-11-17
> **deanlinkous said:**
> Huh? Where did I mention microsoft. MS can take the work and follow the rules of the GPL if they wish.

Well, you said that the developers could take the code and switch licenses, and only worry if someone complains. By that logic MS could take the Linux-kernel, switch licenses and only react if someone starts to complain. Hell, any company could then take free software, close it up and see if someone complains. And if no-one did, then it would be A-OK? Breaking the law is OK if you don't get caught?

> Thats right but a license is different than copyright and the license provides me rights.

yes it does. However, changing the license at your own choosing is NOT among those rights. If it were, GPL would be meaningless, and we could just stick to BSD-license.

> You seem to take it for granted that those dead coders only wanted v2 yet if it wasn't specifically stated by them then one could assume either way and be just as correct and legal in using the code.

If their license does say "V2 or later", then there is no problem. But you seem to assume that their code does contain those magic words, "or later". There are no guarantees that it does.

---

### Post by Sushi on 2006-11-17
> **Bells said:**
> You want it free, you release it BSD, other licences are just wannabee free.

Well, that's a matter of opinion. If you had the right to beat up people who pass you by, would you be more free than you are now? In a way yes, since you could do something that you are not allowed to do now. But remember, that particular "freedom" would mean that others had the right to beat you up as well. Comparing BSD and GPL, that is the difference. BSD gives you more freedoms, including the freedom to screw people over (and be screwed over by others). GPL takes some freedoms away, but in ensure that the greater whole is more free, at the expense of freedoms of some individual.

> For real freedom, you use OpenBSD.

Why is OpenBSD better than NetBSD or FreeBSD? The license is exactly the same, so there is no difference.

---

### Post by deanlinkous on 2006-11-17
> Well, you said that the developers could take the code and switch licenses, and only worry if someone complains. By that logic MS could take the Linux-kernel, switch licenses and only react if someone starts to complain. Hell, any company could then take free software, close it up and see if someone complains. And if no-one did, then it would be A-OK? Breaking the law is OK if you don't get caught?
Nope, I wasn't talking about closing it up and changing license. That would mean violation of living  peoples works and so forth. I was talking about the intentions of the coders.

 I said (or at least meant to say) that it could be assumed that those people who have died or disappeared either submitted code with a license and it will clearly state what version OR it was submitted (if more than five years ago) when the kernel copying file stated "v2 or later" . So I would assume if they did not inlude any file of their own then they had to believe it was under the "v2 or later" part of the copying file already. 

So my point was, even though Linus says his intentions were always v2 only and any work submitted without specifically stating "v2 or later" means that it is v2 only, could be just as likely interpreted to be the opposite since the copying file said "v2 or later". Linus going in and changing it five years ago seems to lead even Linus to do something to make sure everyone knew it was v2 only, which if it already was v2 only then why change anything? Also, how can Linus change something 5 years ago and yet now says you cannot change anything. 


> However, changing the license at your own choosing is NOT among those rights.

Correct, but why are you taking Linus word when he says the code was "v2 only"? If you submitted code 8 years ago then you either included a license statement with it (few devs do that) or you felt that the kernel copying file covered your work, correct? Well if it said "v2 or later" then do you not feel that means exactly what it says? Especially since Linus decided later to go in and change it to make it clear it was "v2 only". Wouldn't him changing it mean that statement did apply? So if it says v2 or later then anyone can take it to v3.

> If their license does say "V2 or later", then there is no problem. But you seem to assume that their code does contain those magic words, "or later". There are no guarantees that it does.
Thats right. So once again assume you submitted code eight years ago. You either included your statement about your license (few devs do that) or I have to assume you feel that the kernel copying file covers your work also. Up until 5 years ago that file said "v2 or later" so what would that mean?

But Linus argument is that if you did the above then "v2 only" is the default. I do not understand why that would be the case. If he truly believes that is the case then why would he himself go and change it to state specifically "v2 only"?


So our discussion is the exact same one they were having.... :D

---

### Post by Sushi on 2006-11-17
> **deanlinkous said:**
> Nope, I wasn't talking about closing it up and changing license. That would mean violation of living  peoples works and so forth. I was talking about the intentions of the coders.

And the coders in question might have meant their code to be strictly under V2. We can't assume that they would accept V3, if their license does not have that "or later".

> Also, how can Linus change something 5 years ago and yet now says you cannot change anything.

Well, the code _was_ already under V2.

> Correct, but why are you taking Linus word when he says the code was "v2 only"?

I'm not. I have no idea that does the license have the "or later" or not. What I am saying is that we can't simply assume that it does.

---

### Post by deanlinkous on 2006-11-17
Linus isn't holding up examples and showing us the license of the "dead" copyright holders code. There (likely) is no license included with "dead" coders work. They intended their code to be a part of the kernel which has its own license statement. That license statement was changed by Torvalds 5 years ago to state specifically "v2 only". Not assuming anything - he changed something to specifically state "v2 only" so if he did that then what was it before.....???? :)

Isn't this discussion a good reason for v3? To clear up the ambiguity and define some points more clearly? Should we continue using a old license that causes misunderstandings like these? Keep using something that was wrote by Stallman himself without legal counsel? v2 is good, v3 is soooo much better :)

---

### Post by deanlinkous on 2006-11-17
Everyone Vote!

[http://poll.pollcode.com/vR](http://poll.pollcode.com/vR)

---

### Post by deanlinkous on 2006-11-17
Excellent article outlining why we really need v3.

[http://www.groklaw.net/article.php?story=20061116103031303](http://www.groklaw.net/article.php?story=20061116103031303)

> Would that not illustrate beautifully exactly why we need GPLv3? We need it because folks are starting to get cute with v2.

In regards to not only Tivo but novell/microsoft and others that skirt the GPL wording yet obvious have defeated the purpose and reason of the GPL.

Does anyone like loopholes? v3 seeks to close some of those loopholes that v2 didn't account for. What is wrong with that?

Do we really want this:
> "Only customers that use SUSE have paid properly for intellectual property from Microsoft," he said. "We are willing to do a deal with Red Hat and other Linux distributors." The deal with SUSE Linux "is not exclusive," Ballmer added.

Are you willing to not only pay microsoft for windows but also for linux? I am not!

---

### Post by rianquinn on 2006-11-17
Simple fact is the major Linux Distributions are pushing to make Linux a Desktop OS as well as a Server OS. For this to happen DRM has to be allowed. Otherwise it has no hope of making it. There are a lot of people in the schools that us Linux as their main OS but still use Windows for one purpose. And thats Music. No Music. No Linux. Sorry folks but you can argue that till your blue in the face. The Next Generation won't adopt anything that prevents Music. And GPLv3 has a specific clause saying no to DRM. Which is the same thing as saying no to people ever using Linux. 

All the major Music Download companies including Real have flat out said they will not give up DRM. And I wouldn't either. No one loves Linux more than I. But open-source is about making source available to the world to help the growth of all software by millions. Not making EVERYTHING free. GPLv3 will be a complete failure because people simply won't use it when GPLv2 has really nothing wrong with it.

Why fix something that is not broke.

---

### Post by shining on 2006-11-17
> **rianquinn said:**
> Simple fact is the major Linux Distributions are pushing to make Linux a Desktop OS as well as a Server OS. For this to happen DRM has to be allowed. Otherwise it has no hope of making it. There are a lot of people in the schools that us Linux as their main OS but still use Windows for one purpose. And thats Music. No Music. No Linux. Sorry folks but you can argue that till your blue in the face. The Next Generation won't adopt anything that prevents Music. And GPLv3 has a specific clause saying no to DRM. Which is the same thing as saying no to people ever using Linux. 

All the major Music Download companies including Real have flat out said they will not give up DRM. And I wouldn't either. No one loves Linux more than I. But open-source is about making source available to the world to help the growth of all software by millions. Not making EVERYTHING free. GPLv3 will be a complete failure because people simply won't use it when GPLv2 has really nothing wrong with it.

Why fix something that is not broke.

Can you play DRM music everywhere, on the platform and system of your choice? If not, it's broken and has to be fixed.

---

### Post by deanlinkous on 2006-11-17
> **rianquinn said:**
> Simple fact is the major Linux Distributions are pushing to make Linux a Desktop OS as well as a Server OS. For this to happen DRM has to be allowed. Otherwise it has no hope of making it. There are a lot of people in the schools that us Linux as their main OS but still use Windows for one purpose. And thats Music. No Music. No Linux. Sorry folks but you can argue that till your blue in the face. The Next Generation won't adopt anything that prevents Music. And GPLv3 has a specific clause saying no to DRM. Which is the same thing as saying no to people ever using Linux. 

All the major Music Download companies including Real have flat out said they will not give up DRM. And I wouldn't either. No one loves Linux more than I. But open-source is about making source available to the world to help the growth of all software by millions. Not making EVERYTHING free. GPLv3 will be a complete failure because people simply won't use it when GPLv2 has really nothing wrong with it.

Why fix something that is not broke.


Somebody took away your freedom of music and you want to continue paying them to do that? Do you enjoy being treated like a criminal? Something is definately broke....

Oh and the GPL does NOT have a clause that prevents encryption/protection of music, for the record. Why someone would want to use something like that, pay for something liek that and demand that they have their rights taken away I have no idea but the GPL could care less.

The GPL deals with DRM that is about making the source unusable, so how is that going to provide that growth you speak of if nobody can use the source?

By the way, I have music! I paid for every one of the songs and I will use it fairly and I will not allow anyone to take that right away from me. I listen to my music on the computer, burn me a cd and listen in the car, put it on my flash drive and take it with me for wherever I am, love my freedom and won't take less. :)

to each their own though...

---

### Post by shining on 2006-11-17
> **deanlinkous said:**
> 
By the way, I have music! I paid for every one of the songs and I will use it fairly and I will not allow anyone to take that right away from me. I listen to my music on the computer, burn me a cd and listen in the car, put it on my flash drive and take it with me for wherever I am, love my freedom and won't take less. :)

to each their own though...

Indeed, it's sad that people seem to be ready to give up on this freedom..

---

### Post by rianquinn on 2006-11-17
> **deanlinkous said:**
> Somebody took away your freedom of music and you want to continue paying them to do that? Do you enjoy being treated like a criminal? Something is definately broke....

Oh and the GPL does NOT have a clause that prevents encryption/protection of music, for the record. Why someone would want to use something like that, pay for something liek that and demand that they have their rights taken away I have no idea but the GPL could care less.

The GPL deals with DRM that is about making the source unusable, so how is that going to provide that growth you speak of if nobody can use the source?

By the way, I have music! I paid for every one of the songs and I will use it fairly and I will not allow anyone to take that right away from me. I listen to my music on the computer, burn me a cd and listen in the car, put it on my flash drive and take it with me for wherever I am, love my freedom and won't take less. :)

to each their own though...

[http://news.com.com/DRM+key+to+Linuxs+consumer+success/2100-7344_3-6058790.html](http://news.com.com/DRM+key+to+Linuxs+consumer+success/2100-7344_3-6058790.html)

If freedom is what you are striving for, you should have the freedom to give up your freedom of digital rights. I can use my DRM'ed music on anything I wish. I enjoy not having to pay $20 a CD to be able to listen to any music I wish. Yet I still own rights to all of this music by paying only $10 a month. Not to mention ratings, radio channels, and reviews. Its a service like any other and Millions use it. Millions who would love to give up this so called freedom to use iTunes or Rhapsody. I frankly don't really care about my digital rights freedom. I care about two things, the quality of Software and my ability to use that software in any way I choose (which is the most important kind of freedom). Currently I can't do this because Microsoft has no quality, just stock holders. And Linux has no freedom because I can't use it for what ever I want. Only programming and Internet. This I find to be most frustrating.

---

### Post by deanlinkous on 2006-11-17
Well, it is sad. But I honestly don't care about sad as much as I care about understanding it and I cannot manage to understand this. Yes, I know we all (almost) want music.  I always have something playing myself. But how did people get duped into thinking that if you want music you have to be locked into something to get it? By paying and willingly allowing DRM is EXACTLY why almost nothing else is offered anymore.

Next, they will require you to have your brain erased after seeing a movie so you will need to pay to see it again if you want to enjoy it. :)

---

### Post by deanlinkous on 2006-11-17
> **rianquinn said:**
> [http://news.com.com/DRM+key+to+Linuxs+consumer+success/2100-7344_3-6058790.html](http://news.com.com/DRM+key+to+Linuxs+consumer+success/2100-7344_3-6058790.html)

If freedom is what you are striving for, you should have the freedom to give up your freedom of digital rights. I can use my DRM'ed music on anything I wish. I enjoy not having to pay $20 a CD to be able to listen to any music I wish. Yet I still own rights to all of this music by paying only $10 a month. Not to mention ratings, radio channels, and reviews. Its a service like any other and Millions use it. Millions who would love to give up this so called freedom to use iTunes or Rhapsody. I frankly don't really care about my digital rights freedom. I care about two things, the quality of Software and my ability to use that software in any way I choose (which is the most important kind of freedom). Currently I can't do this because Microsoft has no quality, just stock holders. And Linux has no freedom because I can't use it for what ever I want. Only programming and Internet. This I find to be most frustrating.


Uh well, I wont argue with you. I would say that if those "rights" you think you have where taken away tommorrow I would bet that you would be upset. My sister-in-law use to think that having all that music was the coolest thing (windows media) and she didn't understand why I cautioned her against it. Computer crashed, hard drive died, she had the music on DVDS and even the backup license - all it kept saying was the license was corrupt and *poof* goodbye 4gigs worth of music.

I would also say that nothing that I know of prevents anyone from creating software that would protect content for linux. I mean Linspire wraps some software in encryption so I do not see what stops anyone from writing the software for it but I would say that nobody using linux WANTS that.

As I said, to each their own.

---

### Post by deanlinkous on 2006-11-17
Great thread guys...but I have goofed off on the forums for toooo long. I MUST get some stuff done. Thanks for the conversation. Hopefully will come back and argue more before too long. Enjoyed all the banter - even those I did not agree with! Take care!

(shameless canned post)

---

### Post by rianquinn on 2006-11-17
hahahahahaha. I'm gooofing off to. I keep procrastination because I have a huge Digital Logic Assignment to work on. Yuk!!!!!!

Honestly though if someone else offered a none DRM version of this service (downloads, radio and reviews) I would use it. Their simply is nothing out there. 

Also, using GPLv2 says its perfectly fine to have DRM. Why no one has done this I don't know. But GPLv3 makes this problem worse. Thats my point. I don't want to see people not use Linux because of the debate of Music Freedom.

Agreed.... great post. Without these debates know one would now how we all feel. 

:)

---

### Post by JayTee on 2006-11-17
Back in the day, when I actually wrote code I created a few shareware apps. A couple were pretty popular on the bulleting board systems and had heavy downloads. I never made my apps crippleware. It was based on the honor system like most early shareware. I found that I got more money from people in other countries than I did the US but the bulk of the downloads came from within the US. So many Americans scream about outsourcing and immigration, etc. etc. but then they go and pirate music or download a torrent of a movie and think nothing of it. "Everybody does it!" is neither a convincing arguement nor does it make it ok. The next generation of the GPL, GPL3 will IMHO, only stifle innovation and while GPL2 is a good idea in some areas it is still very important for a vibrant economy to have protection for intellectual property and the ability to sell something you create, even software. In the spirit in which Linus Torvalds intended I think the Linux kernel should stay at GPL2.

---

### Post by rianquinn on 2006-11-17
> **JayTee said:**
> Back in the day, when I actually wrote code I created a few shareware apps. A couple were pretty popular on the bulleting board systems and had heavy downloads. I never made my apps crippleware. It was based on the honor system like most early shareware. I found that I got more money from people in other countries than I did the US but the bulk of the downloads came from within the US. So many Americans scream about outsourcing and immigration, etc. etc. but then they go and pirate music or download a torrent of a movie and think nothing of it. "Everybody does it!" is neither a convincing arguement nor does it make it ok. The next generation of the GPL, GPL3 will IMHO, only stifle innovation and while GPL2 is a good idea in some areas it is still very important for a vibrant economy to have protection for intellectual property and the ability to sell something you create, even software. In the spirit in which Linus Torvalds intended I think the Linux kernel should stay at GPL2.

I agree. Not everything needs to be free.

---

### Post by FISHERMAN on 2006-11-18
> **rianquinn said:**
> Simple fact is the major Linux Distributions are pushing to make Linux a Desktop OS as well as a Server OS. For this to happen DRM has to be allowed. Otherwise it has no hope of making it. There are a lot of people in the schools that us Linux as their main OS but still use Windows for one purpose. And thats Music. No Music. No Linux. Sorry folks but you can argue that till your blue in the face. The Next Generation won't adopt anything that prevents Music. And GPLv3 has a specific clause saying no to DRM. Which is the same thing as saying no to people ever using Linux. 

All the major Music Download companies including Real have flat out said they will not give up DRM. And I wouldn't either. No one loves Linux more than I. But open-source is about making source available to the world to help the growth of all software by millions. Not making EVERYTHING free. GPLv3 will be a complete failure because people simply won't use it when GPLv2 has really nothing wrong with it.

If I wanted the stability of a Unix-like OS combined with the (dis)advantages of DRM, I would have bought a Mac.
Well I didn't, I use GNU/Linux because it is the free OS without that DRM-crap.

And if Music Companies will only offer DRM-infested crap then they will lose me as a costumer(and I won't be the only one), there will always be (small) Music companies that will offer DRM-free Music.
It's good that GNU/Linux gets more popular, but if it will be infested with DRM(like Win or Mac) I will no longer want it.

---

### Post by Wolki on 2006-11-18
> **rianquinn said:**
> Also, using GPLv2 says its perfectly fine to have DRM. Why no one has done this I don't know.

Likely because noone who creates DRM software wants to hand out the source for free. It makes it much easier to crack, and much harder to sell it.

---

