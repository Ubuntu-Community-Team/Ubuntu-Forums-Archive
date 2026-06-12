---
title: "Contributor Agreement"
date: 2010-10-19
forum: The Cafe
---

### Post by Yeti can't ski on 2010-10-19
PJ of Groklaw, respectively a very respected blogger and website in the Legal Open Source Community, raises some very interesting points on Canonical's Contributor Agreement (it is a comment to one of her "latest news picks" section):

> Well, let's stop and think a minute. We just emerged recently from the MySQL drama. Dual licensing, we learned, can be a problem too. Greed causes many issues. Why can't businesses just stop trying to force FOSS to be what it isn't? And it's not so nice to use developers. By that I mean, why would a developer who cares about FOSS want to work for your business for free, and then his code gets relicensed as proprietary code to boot? Even if he still has a FOSS version of his contribution? Seriously. Give me a reason, please. Maybe there's one I can't think of, but I can't think of any reason at all. The motive for writing FOSS is gone. I can see if a developer wants to dual license his own code and if folks want to do this, who am I to say no? But why would he freely share it with your business so you can make big bucks? You are worried about your business model. But with dual licensing or open core, either one, what is the business model there for him? Kuhn may not have the right word, but he's got his finger pointing in the right direction, and here's why I think so.** Look at Canonical's assignment agreement. Do you see anything that would prevent Canonical from going completely proprietary? I don't. I'm not saying they would. But what stands in their way in that agreement? Your little piece might still be yours, but the project as a whole can be relicensed any way they want.** Ask your lawyer, because I could be off, but it doesn't, to my eyes, say that there will always be a project as a whole that will be available as FOSS, just that you can use your contribution any way you want. **In practical terms, unless you can find all the others who contributed and reproduce the entire Canonical code, what have you got compared to what Canonical has?** Is that what you call business?

If you want to take a look for yourselves, you can find the agreement here: 

[http://www.canonical.com/system/files/Canonical%20Contributor%20Agreement,%20ver%202.5.pdf]("http://www.canonical.com/system/files/Canonical%20Contributor%20Agreement,%20ver%202.5.pdf")

I would really like to know the views of other Ubuntuers out there, more informed than I am, about this issue.

---

### Post by Yeti can't ski on 2010-10-19
Two articles on this issue: 

[http://www.networkworld.com/community/node/67554]("http://www.networkworld.com/community/node/67554")

[http://blogs.the451group.com/opensource/2010/10/18/fear-and-loathing-and-open-core/]("http://blogs.the451group.com/opensource/2010/10/18/fear-and-loathing-and-open-core/")

---

### Post by Yeti can't ski on 2010-10-19
From Canonical's FAQ on the issue: 

> Does clause 6 allow Canonical to potentially lock away my contributions under a proprietary license?

No — Canonical can't lock away your contributions under this agreement, because of clause 2. **Canonical could use your contributions in a proprietary program**, but the contributions would remain distributable by you under other licenses (thanks to clause 2), and thus be available for use elsewhere.


[http://www.canonical.com/contributors/faq]("http://www.canonical.com/contributors/faq")

Why keep the right to re-license code under proprietary terms?

---

### Post by alexfish on 2010-10-19
also interesting

[http://www.ifosslr.org/ifosslr/article/view/37/65](http://www.ifosslr.org/ifosslr/article/view/37/65)

---

### Post by Oxwivi on 2010-10-19
Code makes their things work, and if a contributed code is needed to make a proprietary software work, of course they'd keep the right to re-license it. Whatever contribution we make to Ubuntu, it's going directly to their hands - you are not spreading it independently. GNU license allows you to take to the code and release it proprietarily anyway Canonical isn't at fault.

---

### Post by Yeti can't ski on 2010-10-19
> **Oxwivi said:**
> GNU license allows you to take to the code and release it proprietarily anyway Canonical isn't at fault.

Could you please elaborate on that? You refer to GPL3? 

The original holder of copyright has obviously the right to double license his/her/its own code under any number of licenses. It is a part of the legal system. It is not the GPL that "allows" it.  

Still, inviting people to contribute to a project under the Free Software flag and then take their code and distribute it under a proprietary license seems IMHO just morally wrong.

Canonical is not doing it, as far as I know, but I don't understand why they reserve the legal right to do so.

---

### Post by zekopeko on 2010-10-19
> **Yeti can't ski said:**
> From Canonical's FAQ on the issue: 

[http://www.canonical.com/contributors/faq]("http://www.canonical.com/contributors/faq")

Why keep the right to re-license code under proprietary terms?

So that the GPL doesn't stop you from entering lucrative markets simply because of some legal technicality.

It's really an non issue. The agreement only applies to Canonical created project not general Ubuntu development. Even if for some reason Canonical decided to close those projects the code released up to that point would still remain under a FOSS licence.

---

### Post by zekopeko on 2010-10-19
> **Oxwivi said:**
> GNU license allows you to take to the code and release it proprietarily anyway Canonical isn't at fault.

The only three ways to close GPL code is by having it run on server (since you aren't distributing the GPL doesn't kick in), by using a hardware solution to only allow your modified GPL code to run (TiVo does that; that loop hole was closed in GPLv3) and by owning all the copyright on the code (since you would be the sole owner you can do with your property what you like).

---

### Post by Yeti can't ski on 2010-10-19
> **zekopeko said:**
> So that the GPL doesn't stop you from entering lucrative markets simply because of some legal technicality.

It's really an non issue.

Having code created and contributed under the FOSS spirit re-licensed and finishing under a proprietary license does not sound, once again IMHO, as a "legal technicality". And it also does not seem a non-issue to me (or to PJ, by the way).

It is an erosion of copyleft. Nothing more, nothing less. Only if you consider copyleft non-important you may regard this as a non-issue.

---

### Post by zekopeko on 2010-10-19
> **Yeti can't ski said:**
> Having code created and contributed under the FOSS spirit re-licensed and finishing under a proprietary license does not sound, once again IMHO, as a "legal technicality". And it also does not seem a non-issue to me (or to PJ, by the way).

It is an erosion of copyleft. Nothing more, nothing less. Only if you consider copyleft non-important you may regard this as a non-issue.

That's because you only think of re-licencing in the terms of proprietary licences. What if somebody wants to re-licence the project under a more liberal licence ala MIT or Apache2 or simple give an exception to a part of the GPL for one specific platform?

BTW PJ isn't exactly a unbiased source. She is going to chastise Canonical for this but will defend IBM if they do something similar (which they do).

---

### Post by Yeti can't ski on 2010-10-19
> **zekopeko said:**
> That's because you only think of re-licencing in the terms of proprietary licences. What if somebody wants to re-licence the project under a more liberal licence ala MIT or Apache2 or simple give an exception to a part of the GPL for one specific platform?

Ok, good point. But then again, why not establish in the Contributor Contract that Canonical will only re-license contributed code under a GPL-Compliant license, as from time to time published by FSF ([http://www.gnu.org/licenses/license-list.html#GPLCompatibleLicenses]("http://www.gnu.org/licenses/license-list.html#GPLCompatibleLicenses"))? 

As for the word "proprietary", is Canonical that uses it in its FAQ on Contributor Agreements.  

> **zekopeko said:**
> BTW PJ isn't exactly a unbiased source. She is going to chastise Canonical for this but will defend IBM if they do something similar (which they do).

Very good point indeed. She is also very kind with Apple most of the time, in spite of their obnoxious FOSS track-record. My mistake to take the path of "argument from authority". Sorry for that. What I intended to underscore was her point. Which seems very solid in this case.

---

### Post by Half-Left on 2010-10-19
Aaron Seigo shares his views.

[http://aseigo.blogspot.com/2010/09/copyright-assignments-gone-wild-or-why.html](http://aseigo.blogspot.com/2010/09/copyright-assignments-gone-wild-or-why.html)

---

### Post by zekopeko on 2010-10-19
> **Yeti can't ski said:**
> Ok, good point. But then again, why not establish in the Contributor Contract that Canonical will only re-license contributed code under a GPL-Compliant license, as from time to time published by FSF ([http://www.gnu.org/licenses/license-list.html#GPLCompatibleLicenses]("http://www.gnu.org/licenses/license-list.html#GPLCompatibleLicenses"))?

Fair point. I think that is the crux of the matter. Something like that should be added to the agreement. 

But you really don't want to depend on the FSF for the legal definition of what is free. What if they release GPLv[4-5-6...] which puts extreme restrictions that don't allow the GPL version to be commercially exploited in one specific but lucrative are because of purely ideological reasons? Canonical would then have an unfair advantage since it could commercially operate in that area with their proprietary licence.

What would be better is for them simply to say they will make a FOSS version of the software always available in the future under a licence that satisfies the four freedoms.

> As for the word "proprietary", is Canonical that uses it in its FAQ on Contributor Agreements.

Because it is the most extreme case. You can only go free-er from there.

> Very good point indeed. She is also very kind with Apple most of the time, in spite of their obnoxious FOSS track-record. My mistake to take the path of "argument from authority". Sorry for that. What I intended to underscore was her point. Which seems very solid in this case.

Well she drew a parallel to MySQL. The MySQL codebase is still GPL and there are plenty of forks out there. Heck the majority of MySQL development was from MySQL AB company that owned the copyright to it. But anyway I think that it's a simple fix and even without that fix Canonical would be heavily damaged in the communtiy if they ever did something like closing the entire code base of their FOSS projects.

---

### Post by Yeti can't ski on 2010-10-19
> **zekopeko said:**
> What would be better is for them simply to say they will make a FOSS version of the software always available in the future under a licence that satisfies the four freedoms.


I understand and completely agree with your point. 

My reference to FSF's definition was just an example of many different ways to give a minimum level of safety to contributors. 

I am quite sure that Canonical's legal guys can draft a reasonable definition of FOSS, acceptable to the largest part of the community, and add it to their Contributor Agreement. 

I really hope they will do something like that and spell out any doubts.

---

### Post by Oxwivi on 2010-10-19
> **Yeti can't ski said:**
> Still, inviting people to contribute to a project under the Free Software flag and then take their code and distribute it under a proprietary license seems IMHO just morally wrong.
Wrong or not, contributors are informed.

> **Yeti can't ski said:**
> Canonical is not doing it, as far as I know, but I don't understand why they reserve the legal right to do so.
Is it really legal to reserve the right to do so?

---

### Post by Oxwivi on 2010-10-19
> **Yeti can't ski said:**
> I am quite sure that Canonical's legal guys can draft a reasonable definition of FOSS, acceptable to the largest part of the community, and add it to their Contributor Agreement. 
Draft a reasonable definition of the FOSS? The whole patenting mess with softwares are the varying interpretation of the laws governing software. What we need is a solid definition, which is universal instead of meaning being adapted to suit someone and take advantage of it.

---

### Post by Yeti can't ski on 2010-10-19
> **Oxwivi said:**
> Draft a reasonable definition of the FOSS? The whole patenting mess with softwares are the varying interpretation of the laws governing software. What we need is a solid definition, which is universal instead of meaning being adapted to suit someone and take advantage of it.

Dear Oxwivi, attention please not to read my phrase out of its context. 

We were specifically discussing a possible clause for Contributor Agreements that would prevent Canonical from re-licensing contributed code under an non-FOSS license and, thus, would preserve the spirit of copyleft. Nothing else. 

Patents are a whole different (and more dangerous and tragic) ball game. 

> **Oxwivi said:**
> Wrong or not, contributors are informed.

You are right but, well, it is a quite a lawyerish way of thinking. Which is OK for going to court, but not really the best way to build a healthy FOSS community. 

> **Oxwivi said:**
> Is it really legal to reserve the right to do so?

I don't see why the clause could be seen as invalid. If the assignment is unrestricted, Canonical does whatever it wants with the code. That is precisely why I humbly believe that the assignment should be limited to FOSS-compliant use of contributed code.

---

### Post by Oxwivi on 2010-10-19
> **Yeti can't ski said:**
> Dear Oxwivi, attention please not to read my phrase out of its context. 

We were specifically discussing a possible clause for Contributor Agreements that would prevent Canonical from re-licensing contributed code under an non-FOSS license and, thus, would preserve the spirit of copyleft. Nothing else. 

Patents are a whole different (and more dangerous and tragic) ball game. 
Yes, but I am highlighting what caused such a mess, it's not impossible for a similar effect on the interpretation to occur in the FOSS community. If each have their own sets of limitation to a rule, they'll differ, oppose each other and cause fragmentation all over the FOSS community.

> **Yeti can't ski said:**
> You are right but, well, it is a quite a lawyerish way of thinking. Which is OK for going to court, but not really the best way to build a healthy FOSS community. 
Lawyerish or not, Canonical set up Ubuntu, so contributors play by their rules. Expats doesn't have a say in a foreign country, it's the leaders and the citizens of that country.

> **Yeti can't ski said:**
> I don't see why the clause could be seen as invalid. If the assignment is unrestricted, Canonical does whatever it wants with the code. That is precisely why I humbly believe that the assignment should be limited to FOSS-compliant use of contributed code.
That's not my question. How does license relate to judicial laws? If I create a software and apply my own license, does the law take into account or is there a legal procedure to legalise a license?

---

### Post by zekopeko on 2010-10-19
> **Oxwivi said:**
> That's not my question. How does license relate to judicial laws? If I create a software and apply my own license, does the law take into account or is there a legal procedure to legalise a license?

Licenses are a form of contract so you don't need to "legalize" them. They simply must not go against the laws of country. If they do then they are void.

---

### Post by Oxwivi on 2010-10-19
Then how is dual license possible if they contradict each other?

---

### Post by Yeti can't ski on 2010-10-19
> **Oxwivi said:**
> Then how is dual license possible if they contradict each other?

I will try to explain it in a light, simple and humorous manner, but I am sincerely not making fun of anyone, ok? 

If Bob had a house in the beach he could either lend it to his cousin Joe for free or lease it to his friend Jim for a certain amount. 

Now, if Bob’s house is an immaterial object – just like any intellectual property, including software – any number of people could use it at the same time. Joe and Jim could, therefore, “use” Bob’s virtual “beach house” at the same time, under different legal entitlements, without even taking notice of each other’s existence. 

Remember, it is an immaterial and, thus, infinite house. It can accommodate any number of people that Bob decides to take in and that accept his proposed conditions (which can vary from person to person). As long as it is Bob’s house, he decides who uses it and under which title. Bob is dual “licensing” it to Joe and Jim. There is no (legal) contradiction on that.

---

### Post by zekopeko on 2010-10-19
> **Oxwivi said:**
> Then how is dual license possible if they contradict each other?

Because they are separate and their effects are separate. Lets say I have some software called "Foomatic" under FOSS license (you have to release all the changes you make to it) and under a proprietary license (you can use it how you like it but have to pay me money).

Now if you make a product with the FOSS version of Foomatic you have to release all the changes you made back to me. But if you make it with the proprietary version you don't have to since it's a different license.

The licenses don't clash since you were the one who made the choice of which one you will use and unless you paid me it is always assumed that you used the FOSS version.

---

### Post by Yeti can't ski on 2010-10-21
A good sign: 

[http://www.itwire.com/business-it-news/open-source/42553-shuttleworth-denies-move-toward-open-core?start=1](http://www.itwire.com/business-it-news/open-source/42553-shuttleworth-denies-move-toward-open-core?start=1)

I look forward to Shuttleworth's answer (usually complete, candid and reasonable), but would really like to see some concrete changes in the contributor agreements. 

If Canonical can't live without copyright assignment, they should at least preserve the spirit of copyleft in any re-licensing, as discussed above in the thread.

---

### Post by Oxwivi on 2010-10-21
I find dual-licensing unfair, to say the least. Sell to someone and share the same thing for free? That's stupid.

---

### Post by Yeti can't ski on 2010-10-21
> **Oxwivi said:**
> I find dual-licensing unfair, to say the least. Sell to someone and share the same thing for free? That's stupid.

Dual-licensing as a concept covers a lot of different practices, some of which are both legally and morally acceptable. 

If you are selling support to your FLOSS software, some of your corporate clients might want to purchase a "normal business license" (non-GPL) to have a statutory right of warranty. So, yes, in that case, you have clients willing to buy (together with training and support) a license for something that they could get for free. 

What I personally find unacceptable, in any event, is to take code from the community under the flag of Free Software and then reuse it in proprietary projects. That kills the principle of copyleft and allows proprietary projects to free-ride on community efforts without giving back.

---

### Post by Oxwivi on 2010-10-21
Yes, in case of support and training, that's fine I suppose. But just selling the software and be done with it is unacceptable.

In Canonical's case the money earned in proprietary projects would be raked back into Ubuntu, I think. But yes, the developer himself gains nothing when it's taken advantage of. I think a contract that lets the developer earn something proportional to the amount of his code used in a proprietary software a reasonable solution. That way, the developers would be encouraged to keep going and help the community with further contributions.

---

### Post by Yeti can't ski on 2010-10-21
> **Oxwivi said:**
> I think a contract that lets the developer earn something proportional to the amount of his code used in a proprietary software a reasonable solution. That way, the developers would be encouraged to keep going and help the community with further contributions.

Well, that would be fairer, but would still be an erosion of copyleft. 

Less importantly, it would be so hard to manage such a system. Imagine measuring the precise contribution of each developer. A few lines of code may require more time and skill than whole section of a program. And then, one must keep track of developers to pay them. It would be hell.

---

### Post by Oxwivi on 2010-10-21
Well, if the developers were paid without consideration to importance, an automated system could easily take care of it.

But if copyleft is the concern, then the solution would be not to even attempt a proprietary solution out of community contributions.

---

