---
title: "&quot;or any later version&quot; legal problem in GPL?"
date: 2010-09-10
forum: The Cafe
---

### Post by leorolla on 2010-09-10
I have a naïve question, and I hope it's also harmless.

I did google for an answer or forum where this has been discussed but haven't found.

The raw question is:

[I]How can you modify and release copyrighted material without even knowing the terms of the license that would allow that?
[/I]
I couldn't think of an answer myself, and [FSF's answer]("http://www.gnu.org/licenses/gpl-faq.html#v2OrLaterPatentLicense") doesn't make any sense to me.

The same doubts apply for GPLv3+ ==> GPLv4+ ==> GPLv5+, etc., but to give a concrete problematic example, let's imagine GPLv3 doesn't exist yet.

**Licenses are pieces of text and, like arts, they stop belonging to their  creator at the instant when they are released.** (Not the copyright of the  text, but their idea and interpretation.) I know FSF wrote the GPLs, but the interpretation of them must come from the text, there is no prerogative to explain, clarify, or amend the licenses.

Let's see...
[I]Q: My company owns a lot of  patents. Over the years we've contributed code to projects under “GPL version 2 or any later version”, and the project itself has been distributed under the same terms. If a user decides to take the project's code (incorporating my contributions) under GPLv3, does that mean I've automatically granted GPLv3's explicit patent license to that user?
A: No.  When you convey GPLed software, you must follow the terms and conditions of one particular version of the license.  When you do so, that version defines the obligations you have.  If users may also elect to use later versions of the GPL, that's merely an additional permission they have—it does not require you to fulfill the terms of the later version of the GPL as well. [...][/I]

I don't see how this can hold in practice.

Did this company have the right to release code under GPLv2+? They were not fulfilling the requirements to release it under GPLv3, and probably not those of GPLv4 either.

Did the author of the original code that they used give them explicit permission to release their derivative work under GPLv3 without fulfilling its requirements?

Where is it written? 

Is there any part of the copyright statement that allows it?

The copyright statement says "*you can redistribute it and/or modify it under the terms of [GPL]; either version 2 [...] or [...] any later version*".

The GPLv2 text says: "*If the Program specifies [...] "any later version", you have the option of following the terms and  conditions _either_ of that version or of any later version [...]*"

The author did _not_ grant a copyright license saying "*If you fulfill the requirements of GPLv2 then you can release this software under GPLv2+*". It clearly says "*I'm making multiple releases of this very same work, under several licenses, some of which have not been written yet. Choose one.*" Well, none of these licenses (GPLv2,3,4,...) did grant the licensee the right to release derivative works under GPLv3 without fulfilling the requirements of GPLv3. When this company releases modified code and attaches a copyright notice saying "*you can redistribute it and/or modify it under the terms of [GPL];  either version 2 [...] or [...] any later version*", they are in particular releasing it under GPLv3.

What am I missing here?

---

### Post by limestone on 2010-09-10
GNU General Public License [http://www.gnu.org/licenses/gpl-3.0.txt](http://www.gnu.org/licenses/gpl-3.0.txt)
You have to add that to a txt file with your program named LICENSE.
You also state the comment first in your application code that it's licensed under GPL.


> [I]How can you modify and release copyrighted material without even knowing the terms of the license that would allow that?
[/I]
You will have to read the licenses for the software you're going to modify..

Copyright is automatically added to an original work done by anyone. It says that you are the creator and owner of that.
You CAN NOT change or redistribute anything that's copyrighted. The GPL is external "terms" that extend the copyright, and says
that you may redistribute and/or modify this under this (GPL) terms.

---

### Post by leorolla on 2010-09-10
> **pont.andersson said:**
> Gnu General Public License [http://www.gnu.org/licenses/gpl-3.0.txt](http://www.gnu.org/licenses/gpl-3.0.txt)
You have to add that to a txt file with your program named LICENSE.
You also state the comment first in your application code that it's licensed under GPL.

The GPL says that you still have the copyright to your work but lets others to practically do what they want with it.
exept change the license or original copyright.


You will have to read the licenses for software you going to modify..

Did you **really** read my whole post?

I'm talking about licenses that are not even written yet.

I'm talking about releasing it under *any possible future version of GPL* (or even versions, or prime-numbered versions) without knowing whether you fulfill the requirements of such licenses.

I do understand how you can change GPLv3 software and release it under  GPLv3..., that's not my question.

---

### Post by limestone on 2010-09-10
Oh, sorry.. Well it would be possible it practically says that the code or whatever upgrades to latest GPL
To bad for that person if he don't agree with the new terms in the future.

I don't think you can change the license version of a program thats already set to one.
But here [http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html) you can read about how it works..

---

### Post by leorolla on 2010-09-10
> **pont.andersson said:**
> Oh, sorry.. Well it would be possible it practically says that the code or whatever upgrades to latest GPL
To bad for that person if he don't agree with the new terms in the future.

I don't think you can change the license version of a program thats already set to one.
But here [http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html) you can read about how it works..

1. I'm making a general question. Forget about GPL and links to GPL texts. It could be any other license that is updated and future versions.

2. "Too bad for that person if he don't agree with the new terms in the  future." That's not how copyright works. If he released derivative work under a certain license (GPLv3 for _example_), he is violating the copyrights of the original work unless there is a license permitting it. _There is no license permitting it._ Think.

It's not "practically says", "the code or whatever", I'm talking about delicate questions like valuable patents and copyright infringement of valuable work.

When you receive a work with a copyright notice and a copyright license written on it, you can do with that work only what the license allows. Anything else is violation. And, as I said in the first post, the license is exactly what is written there, not what FSF's FAQ says.

---

### Post by grahammechanical on 2010-09-10
Just for the record I have read your first post and I am trying to understand your point. I think that the comment :

> or any later version is a kind of legalistic wording. I note the following point in the FAQ:

> It does not require you to fulfill the terms of the later of the later GPL as well

By granting a license you not only grant certain freedoms/permissions to the other person but you place on yourself certain restrictions/obligations  (such as demanding royalties or licence fees, if that is part of the agreement). A new version of the licence might modify these freedoms and restrictions in some way. It might not. Perhaps the licence should read something like:

or any later version *that does not diminish the rights or increase the liabilities of the person/persons granting the licence beyond the terms of the present licence*.

Now, try to get the FSF to admit that they left something out!

regards

---

### Post by red_Marvin on 2010-09-10
As I understand it, from the wording [here](http://www.gnu.org/licenses/gpl.html), "How to Apply These Terms to Your New Programs"

You don't realease your code under v2+, but under v2, and grand the licencee the right to distribute/modify it under v2+.

*Your* obligations only goes as far as the v2 license states, if somebody redistributes it, *their* obligations depend on what version they choose, but cannot reflect back on you.

---

### Post by leorolla on 2010-09-10
> **grahammechanical said:**
> Just for the record I have read your first post and I am trying to understand your point. I think that the comment :

 is a kind of legalistic wording. I note the following point in the FAQ:

By granting a license you not only grant certain freedoms/permissions to the other person but you place on yourself certain restrictions/obligations  (such as demanding royalties or licence fees, if that is part of the agreement). A new version of the licence might modify these freedoms and restrictions in some way. It might not. Perhaps the licence should read something like:

or any later version *that does not diminish the rights or increase the liabilities of the person/persons granting the licence beyond the terms of the present licence*.

Now, try to get the FSF to admit that they left something out!

regards

But

[I]that does not diminish the rights or increase the liabilities of the  person/persons granting the licence beyond the terms of the present  licence

[/I]would basically mean no other license.

That's the whole point.

That's why strong copyleft licenses are incompatible.

A copyleft license that apparently grants more rights to the licensee at the same time enforces him to release under this license, which means it's more restrictive (unless it has exceptional clauses allowing re-licensing, and if you add clauses allowing GPL downgrade then this whole license-version strategy makes no sense).

People behave like GPL K+ said:
For any N bigger than the K of this license, you can release derivative works under GPL N+ as long as you fulfill the conditions stated under GPL N.

This would mean: "pick the later version that you like, make sure you obbey the requirements, and re-license my work under that version or later".

But in fact what GPL K+ says is:
For any N bigger than the K of this license,  you can convey this software under the terms of GPL N. Period.
And GPL N says:
You can only convey this software if you release it with this same license. No more restrictions, no less. (Except for the few exceptions.)

So it sounds to me that the correct interpretation is that you can only convey and release GPLv2+ software under GPLv2+ if you fulfill the condition of each single future version of GPL.

This is of course impossible as you don't know the terms of such licenses yet.

As I said, it's a license, and its legal implications come solely from its text. The FAQ may help you reading and interpreting, but it is otherwise irrelevant. FSF has no authority to tell you that the license means something if the text is saying something else.

---

### Post by leorolla on 2010-09-10
> **red_Marvin said:**
> As I understand it, from the wording [here]("http://www.gnu.org/licenses/gpl.html"), "How to Apply These Terms to Your New Programs"

You don't realease your code under v2+, but under v2, and grand the licencee the right to distribute/modify it under v2+.

*Your* obligations only goes as far as the v2 license states, if somebody redistributes it, *their* obligations depend on what version they choose, but cannot reflect back on you.

Again, what counts is the copyright notice and the license, nothing else.

*"Your* obligations only goes as far as the v2 license states, if  somebody redistributes it, *their* obligations depend on what  version they choose, but cannot reflect back on you."

That's what I don't see happening. When you release conveyed work under GPLv2+, you are in  particular  granting people a license to use/etc under GPLv3.

Aren't you?

In what right did you award other people the choice to use under GPLv3?

Where in the standard GPLv2+ notice/license did you get permission to distribute it under GPLv3 without fulfilling the requirements of GPLv3?

---

### Post by Dr. C on 2010-09-10
The full question and answer from the [FSF]("http://www.gnu.org/licenses/gpl-faq.html#v2OrLaterPatentLicense") is as follows:
> My company owns a lot of patents. Over the years we've contributed code to projects under “GPL version 2 or any later version”, and the project itself has been distributed under the same terms. If a user decides to take the project's code (incorporating my contributions) under GPLv3, does that mean I've automatically granted GPLv3's explicit patent license to that user?

    No. When you convey GPLed software, you must follow the terms and conditions of one particular version of the license. When you do so, that version defines the obligations you have. If users may also elect to use later versions of the GPL, that's merely an additional permission they have—it does not require you to fulfill the terms of the later version of the GPL as well.

    Do not take this to mean that you can threaten the community with your patents. In many countries, distributing software under GPLv2 provides recipients with an implicit patent license to exercise their rights under the GPL. Even if it didn't, anyone considering enforcing their patents aggressively is an enemy of the community, and we will defend ourselves against such an attack. The second part, omitted by the OP, clarifies this patent issue and actually the ***whole*** response from the FSF actually makes a lot of sense.

---

### Post by leorolla on 2010-09-10
> **FineE said:**
> The full question and answer from the [FSF]("http://www.gnu.org/licenses/gpl-faq.html#v2OrLaterPatentLicense") is as follows:
 The second part, omitted by the OP, clarifies this patent issue and actually the ***whole*** response from the FSF actually makes a lot of sense.

1. It was in my first post. I removed it as it is obviously just a remark, the clear-cut answer "*No, it doesn't*", and the reason why according to the FSF it doesn't, are in the first paragraph.

2. Anyway, with one or two paragraphs, the answer is just the opinion from FSF, by no means is it absolute truth.

3. The whole point is not patent. Patent is just a great example, but that's not the point. The point is about the licensee not having the right to pass the "any later version" wording forward without obbeying the requirements of all "the later versions".

For the 6th time: **what counts is the copyright notice and the license text, not the FAQ. The FSF has no prerogative to explain, clarify, or amend the notice/license under which people release their creative works.**

That said, could you then develop the argument a little more and defend what is written in the text you  copied?

Just a clear "No" from the FAQ doesn't mean that in the real world you had the write to convey and release under GPLv2+ without fulfilliing GPLv3 terms.

---

### Post by red_Marvin on 2010-09-10
> **leorolla said:**
> Again, what counts is the copyright notice and the license, nothing else.

*"Your* obligations only goes as far as the v2 license states, if  somebody redistributes it, *their* obligations depend on what  version they choose, but cannot reflect back on you."

That's what I don't see happening. When you release conveyed work under GPLv2+, you are in  particular  granting people a license to use/etc under GPLv3.

Aren't you?

In what right did you award other people the choice to use under GPLv3?

Where in the standard GPLv2+ notice/license did you get permission to distribute it under GPLv3 without fulfilling the requirements of GPLv3?

The part I wrote about is part of what they recommend you to use as a copyright notice. So it counts.
Also, you licensing it as GPLv2 and granting the licencee the right to *relicense* it under GPLv2+ is *not* the same thing as you releasing it under GPLv2+.

Note the actual text, part of the copyright notice, emphasis mine:
[quote=fsf]
    This program is free software: you can **redistribute** it and/or **modify**
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.
[/quote]

---

### Post by saulgoode on 2010-09-10
The question is whether the author of the original GPLv2-licensed should be considered a "Contributor" to a GPLv3-licensed project which incorporates that code. As defined by GPLv3:
> A "contributor" is a copyright holder who authorizes use under this License of the Program or a work on which the Program is based. The work thus licensed is called the contributor's "contributor version".

While intuitively this suggests that someone who permits distribution of code under GPLv3 is "authorizing" that usage, I would submit that the legal interpretation of this definition runs contrary to intuition. In other words, a programmer who offers his code under GPLv2 but permits derivations to use "any later version" of the license is not legally considered a "Contributor" to the derivation (just as a programmer using the BSD or MIT licenses is not considered a "Contributor" to the derivation incorporating that code). Consequently, the original programmer is not expected to fulfill the obligations of GPLv3; he only needs to meet the obligations of GPLv2.

For what it's worth, I'm not personally very keen on such talmudic reasoning, though the legal profession seems to thrive on it. I also shouldn't think it too egregious if the "or later version" option was construed as "authorizing use" to the extent of being considered a "Contributor" of the derived work. Releasing with the "or later version" implies that you have faith in the Free Software Foundation -- and in their legal obligations as a non-profit, public-benefit corporation -- to ensure that subsequent versions of licenses adhere to the same tenets as their predecessors. If you don't hold this faith then you should probably not include the "or later version" option.


Finally, I would add that I had posed a similar question about patent grants and the GPLv3 to the Software Freedom Law Center over a year ago; to which they responded in [Episode 0x0F of their OGGcast]("http://www.softwarefreedom.org/podcast/2009/jun/09/0x0F/"). My question was specifically about including permissively licensed code into a GPLv3-licensed project, but the response (which appears about 19 minutes into the OGGcast) somewhat bears upon the issue being discussed.


EDIT: I have extracted the segment of the OGGcast which covers the GPLv3 patent question and posted it to [http://www.flashingtwelve.brickfilms.com/Players/GPLv3question/]("http://www.flashingtwelve.brickfilms.com/Players/GPLv3question/")

---

### Post by Dr. C on 2010-09-10
IANAL Patent is a poor example because of the implicit patent license in GPL v2, may actually make the difference between GPL v2 and GPL v3 with respect to patents moot.

Let think about this. Does it make any sense for person A to license some software to person B, and then successfully sue person B for patent infringement, even though person B followed all the terms and conditions of their software license agreement?

I would like to see an actuall case where a person A has successfully pulled this off in a court of law.

---

### Post by leorolla on 2010-09-10
> **red_Marvin said:**
> The part I wrote about is part of what they recommend you to use as a copyright notice. So it counts.
Also, you licensing it as GPLv2 and granting the licencee the right to *relicense* it under GPLv2+ is *not* the same thing as you releasing it under GPLv2+.

Note the actual text, part of the copyright notice, emphasis mine:

Indeed, I'm referring to situations where people follow their recommendations and use a verbatim copy of their copyright notice.

But when it says "*you can redistribute it and/or modify it under the terms of [GPL];  either version 2 [...] or [...] any later version"*, it doesn't mean you can do whatever you want and distribute it under whichever license you choose. It means you are bound to obbey the terms of the chosen license.

And if you choose one of them, you don't have the right to forward the same notice allowing people to release under other licenses.

But, if you wanto to use/modify/redistribuite it under GPLv3, or even worse, use/modify/redistribuite it under GPLv2+, which includes redistribution under GPLv3, then you must use/modify/redistribuite under the terms of GPLv3.

---

### Post by leorolla on 2010-09-10
> **FineE said:**
> IANAL Patent is a poor example because of the implicit patent license in GPL v2, may actually make the difference between GPL v2 and GPL v3 with respect to patents moot.

Let think about this. Does it make any sense for person A to license some software to person B, and then successfully sue person B for patent infringement, even though person B followed all the terms and conditions of their software license agreement?

I would like to see an actuall case where a person A has successfully pulled this off in a court of law.

It's getting OFF TOPIC.

It hasn't happened yet, but as I understood it's part of the patent cold war between software empires and Free Software.

Think of something, more reasonable example: my company is releasing a Linux distro with many patented software in the middle. But I keep the patent. But since the software is Free Software, and it couldn't be otherwise as I used other people's GPLed software in it of course not only the users of my Linux distro, but other projects may as well use that code in their software. Now, I don't like that project, it is a threaten to my business, and guess what... they are using algorithms that I have patented! So I sue them for patent infringement.

GPLv3 gives more protection in this hypothetical case.

But companies that developed under GPLv2+ in the past, releasing code under GPLv2+, and using code from other people, according to the FSF are not bound to the terms of GPLv3.

My point is that they are. Either they obbey GPLv3 terms, or they didn't have the right to release a convey of my software under GPLv2+ (which includes GPLv3) in first place, so they violated my copyrights.

---

### Post by Dr. C on 2010-09-10
> **leorolla said:**
> It's getting OFF TOPIC.

It hasn't happened yet, but as I understood it's part of the patent cold war between software empires and Free Software.

Think of something, more reasonable example: my company is releasing a Linux distro with many patented software in the middle. But I keep the patent. But since the software is Free Software, and it couldn't be otherwise as I used other people's GPLed software in it of course not only the users of my Linux distro, but other projects may as well use that code in their software. Now, I don't like that project, it is a threaten to my business, and guess what... they are using algorithms that I have patented! So I sue them for patent infringement.

GPLv3 gives more protection in this hypothetical case.

But companies that developed under GPLv2+ in the past, releasing code under GPLv2+, and using code from other people, according to the FSF are not bound to the terms of GPLv3.

My point is that they are. Either they obbey GPLv3 terms, or they didn't have the right to release a convey of my software under GPLv2+ (which includes GPLv3) in first place, so they violated my copyrights.

There is still an implicit patent grant. A really interesting example however is the "anti DMCA" clauses in [GPL v3]("http://www.gnu.org/licenses/gpl.html"). > 3. Protecting Users' Legal Rights From Anti-Circumvention Law.

No covered work shall be deemed part of an effective technological measure under any applicable law fulfilling obligations under article 11 of the WIPO copyright treaty adopted on 20 December 1996, or similar laws prohibiting or restricting circumvention of such measures.

When you convey a covered work, you waive any legal power to forbid circumvention of technological measures to the extent such circumvention is effected by exercising rights under this License with respect to the covered work, and you disclaim any intention to limit operation or modification of the work as a means of enforcing, against the work's users, your or third parties' legal rights to forbid circumvention of technological measures.

So does this protection extend to LGPL V2.1. code or GPL V2 or later code?

---

### Post by leorolla on 2010-09-10
> **saulgoode said:**
> While intuitively this suggests that someone who permits distribution of code under GPLv3 is "authorizing" that usage, I would submit that the legal interpretation of this definition runs contrary to intuition. In other words, a programmer who offers his code under GPLv2 but permits derivations to use "any later version" of the license is not legally considered a "Contributor" to the derivation (just as a programmer using the BSD or MIT licenses is not considered a "Contributor" to the derivation incorporating that code). Consequently, the original programmer is not expected to fulfill the obligations of GPLv3; he only needs to meet the obligations of GPLv2.

If this person (the non-contributor) is the original author, they can do anything they want with their work, they can even release it under GPLv2 and disobbey its clauses.

But is this person wrote the program as a derivative work of another program, then he has absolutely no right to authorize other people to use it under GPLv3.

He is bound to release any derivative work under GPLv2, or he will be violating the original author's copyrights. Without havin written permissio from the first author, he could possibly give such authorization only if (i) the original work had been released under GPLv2+ or at least dual-licensed under GPLv2 and GPLv3 **and** (ii) this non-contributor fulfills GPLv3 requirements.

The MIT comparison is unfortunate because MIT license basically gives away all the reserved rights. It requires you to copy-paste those lines and you're done. GPL gives away some rights but comes with tight restrictions on people who want to be granted those rights, including restrictions on how tha derivative works will be released.

(I can't hear the audio.)

---

### Post by Shining Arcanine on 2010-09-10
These sorts of issues are why I like BSD licensing. BSD licenses make it very clear that the original author is to be left alone.

---

### Post by grahammechanical on 2010-09-10
Hi Leorolla

I do get your point. I tend to agree with you. I think that "or any later version" should be omitted from the licence. If a copyright holder or someone releasing under a GPL (I am not familiar with the jargon) chooses a certain licence to release it under, then that should be the licence used until the copyright holder chooses the release under an different licence.

The FSF seems to be giving those it calls recipients the freedom (elect to use) bits from the later version of the GPL as they see fit and not as the person issuing the licence sees fit. Electing to use a later version of the GPL should give not only "additional permissions" but also additional responsibilities. Otherwise a person could change licences by just distributing some one's code.

regards.

---

### Post by Chronon on 2010-09-10
> **leorolla said:**
> Did you **really** read my whole post?

I'm talking about licenses that are not even written yet.

I'm talking about releasing it under *any possible future version of GPL* (or even versions, or prime-numbered versions) without knowing whether you fulfill the requirements of such licenses.

I do understand how you can change GPLv3 software and release it under  GPLv3..., that's not my question.

I don't have to worry about that.  If you take a piece of software that I have released with a permissive distribution license X "version 2 or any later version", then I only have to fulfill the conditions of the version 2.  If you decide to change the license of your copy to a later version and release that then it is your responsibility to uphold the terms of the new license, not mine.  Anyone who gets their code from you and releases a version based on that must abide by the version you released the code under (unless you also specify that they have a right to release under later versions of the license than the one you used).

With the GPL, when the license says that the user may release as version 2 or any later version, the text of the license contains terms consistent with GPLv2.  The user has a right to (fork and) relicense this code under a later version if they choose, but this doesn't affect me in any way.  I only have to fulfill the terms of the specific license that I released under.

---

### Post by Chronon on 2010-09-10
> **grahammechanical said:**
> Hi Leorolla

I do get your point. I tend to agree with you. I think that "or any later version" should be omitted from the licence. If a copyright holder or someone releasing under a GPL (I am not familiar with the jargon) chooses a certain licence to release it under, then that should be the licence used until the copyright holder chooses the release under an different licence.

Then release code under a specific version of the license and remove that clause that permits relicensing.

---

### Post by perspectoff on 2010-09-11
> **leorolla said:**
> I have a naïve question, and I hope it's also harmless.

I did google for an answer or forum where this has been discussed but haven't found.

The raw question is:

[I]How can you modify and release copyrighted material without even knowing the terms of the license that would allow that?
[/I]
I couldn't think of an answer myself, and [FSF's answer]("http://www.gnu.org/licenses/gpl-faq.html#v2OrLaterPatentLicense") doesn't make any sense to me.

The same doubts apply for GPLv3+ ==> GPLv4+ ==> GPLv5+, etc., but to give a concrete problematic example, let's imagine GPLv3 doesn't exist yet.

**Licenses are pieces of text and, like arts, they stop belonging to their  creator at the instant when they are released.** (Not the copyright of the  text, but their idea and interpretation.) I know FSF wrote the GPLs, but the interpretation of them must come from the text, there is no prerogative to explain, clarify, or amend the licenses.

Let's see...
[I]Q: My company owns a lot of  patents. Over the years we've contributed code to projects under “GPL version 2 or any later version”, and the project itself has been distributed under the same terms. If a user decides to take the project's code (incorporating my contributions) under GPLv3, does that mean I've automatically granted GPLv3's explicit patent license to that user?
A: No.  When you convey GPLed software, you must follow the terms and conditions of one particular version of the license.  When you do so, that version defines the obligations you have.  If users may also elect to use later versions of the GPL, that's merely an additional permission they have—it does not require you to fulfill the terms of the later version of the GPL as well. [...][/I]

I don't see how this can hold in practice.

Did this company have the right to release code under GPLv2+? They were not fulfilling the requirements to release it under GPLv3, and probably not those of GPLv4 either.

Did the author of the original code that they used give them explicit permission to release their derivative work under GPLv3 without fulfilling its requirements?

Where is it written? 

Is there any part of the copyright statement that allows it?

The copyright statement says "*you can redistribute it and/or modify it under the terms of [GPL]; either version 2 [...] or [...] any later version*".

The GPLv2 text says: "*If the Program specifies [...] "any later version", you have the option of following the terms and  conditions _either_ of that version or of any later version [...]*"

The author did _not_ grant a copyright license saying "*If you fulfill the requirements of GPLv2 then you can release this software under GPLv2+*". It clearly says "*I'm making multiple releases of this very same work, under several licenses, some of which have not been written yet. Choose one.*" Well, none of these licenses (GPLv2,3,4,...) did grant the licensee the right to release derivative works under GPLv3 without fulfilling the requirements of GPLv3. When this company releases modified code and attaches a copyright notice saying "*you can redistribute it and/or modify it under the terms of [GPL];  either version 2 [...] or [...] any later version*", they are in particular releasing it under GPLv3.

What am I missing here?

I'll tell you the answer if you send me a dollar every month for the rest of my life, or the adjusted value of a dollar at each month in the future, whichever is greater.

Sure you can make a contract for conditions in the future that don't yet exist. Many, many contracts do that. Licenses, too.

They are completely legal and completely binding.

You question is whether the GPL language said that or whether the person who wrote your software license merely added the nugget on their own volition. You probably can read it better than us.

Do you work for Oracle or something? Planning to wiggle out of a few open source licenses, are we?

---

### Post by leorolla on 2010-09-14
> **Chronon said:**
> I don't have to worry about that.  If you take a piece of software that I have released with a permissive distribution license X "version 2 or any later version", then I only have to fulfill the conditions of the version 2.  If you decide to change the license of your copy to a later version and release that then it is your responsibility to uphold the terms of the new license, not mine.  Anyone who gets their code from you and releases a version based on that must abide by the version you released the code under (unless you also specify that they have a right to release under later versions of the license than the one you used).

With the GPL, when the license says that the user may release as version 2 or any later version, the text of the license contains terms consistent with GPLv2.  The user has a right to (fork and) relicense this code under a later version if they choose, but this doesn't affect me in any way.  I only have to fulfill the terms of the specific license that I released under.

The problem is not with You, but with Me.
*(I'm inverting You and Me in your example as You for you is Me for me.)*

You release the code.

I modify it and release the modified version.

I agree that "I have the right to choose any other version and it doesn't affect You in any way".

It affects Me. Because if I release it under GPLv3, the only possible way I can do that without violating Your copyrights is by respecting the requirements stated in GPLv3. And if I release it under the traditional GPLv2+, that implies that I am releasing it under GPLv3 as well.

---

### Post by leorolla on 2010-09-14
> **perspectoff said:**
> I'll tell you the answer if you send me a dollar every month for the rest of my life, or the adjusted value of a dollar at each month in the future, whichever is greater.

Sure you can make a contract for conditions in the future that don't yet exist. Many, many contracts do that. Licenses, too.

They are completely legal and completely binding.

You question is whether the GPL language said that or whether the person who wrote your software license merely added the nugget on their own volition. You probably can read it better than us.

Do you work for Oracle or something? Planning to wiggle out of a few open source licenses, are we?

I don't work for any software-related company. Not even for copyright-related stuff.

Licenses are not contract, maybe you know all that bla bla bla about licenses not being contracts. But anyway, without going to corner cases, let us think of licenses as being contracts.

So, the contract with future, unknown clauses said: That's my software. It's mine. All rights reserved. I grant you some rights under certain conditions, some of which are not written yet. You may even choose, you can choose GPLv2, GPLv3, GPLv4, GPLv5,..., at your will.

You can even choose more than one form the list, since I gave you all those choices. But each one will give you some rights bound to some requirements, and they are independent of each other. Following the terms of GPLv5 doesn't grant you the permissions stated under GPLv2, including the permission to release modified versions under GPLv2.

If you choose GPLv3 from my list, you are bound to the terms of the contract. If you don't choose GPLv3, then you don't have the right to release modifications of my code under this license, let alone release it under the whole set GPLv{2,3,4,...}.

Again, I don't work for any software-related company. I just thought of the question by myself and found that FSF's answer was evasive an incorrect. They would love the "company" in the FAQ to give away their patents, but they don't want to spread the fear that releasing conveyed code under future licenses bind you to the terms of the license. They want everyone to just ignore this "little" detail and keep the "any later version" that they need to release future GPL's. My personal opinion is that of someone worried about copyleft becoming freak and license proliferation becoming a real obstacle after so much education in the community to prevent it. But I'm not sure whether giving evasive answers and pushing people to release their hard work under future licenses is the best solution. I think the next versions should at least allow dynamic and static linking with upcoming ones, instead of saying that the solution to this "little" problem is that the copyright holders "upgrade" their licenses.

---

### Post by gnufreex on 2010-09-15
Hi leorolla. 

I think you got it all wrong. FAQ is not 'incorrect' and 'evasive', it  is straight and correct answer. "or any later version" doesn't make any  legal problem. Also, FSF would maybe love that patent don't exist, but  GPLv3 can't force companies give them patents. Only to agree not to sue  community. That is big difference. They can still sue proprietary  competition. 

Section 9 of GPLv2 says:

> 
 **9.**  The Free Software Foundation may publish revised and/or new  versions of the General Public License from time to time.  Such new  versions will be similar in spirit to the present version, but may  differ in detail to address new problems or concerns. 
   Each version is given a distinguishing version number.  If the  Program specifies a version number of this License which applies to it  and "any later version", you have the option of following the terms and  conditions either of that version or of any later version published by  the Free Software Foundation.  If the Program does not specify a version  number of this License, you may choose any version ever published by  the Free Software Foundation. 
So FAQ is not wishful thinking, it is based on the text of the license. GPLv3 is even better on this regard:

> **14. Revised Versions of this License.**

  The Free Software Foundation may publish revised and/or new versions  of the GNU General Public License from time to time.  Such new versions  will be similar in spirit to the present version, but may differ in  detail to address new problems or concerns.

  Each version is given a distinguishing version number.  If the Program  specifies that a certain numbered version of the GNU General Public  License “or any later version” applies to it, you have the option of  following the terms and conditions either of that numbered version or of  any later version published by the Free Software Foundation.  If the  Program does not specify a version number of the GNU General Public  License, you may choose any version ever published by the Free Software  Foundation.

  If the Program specifies that a **proxy can decide** which future  versions of the GNU General Public License can be used, that proxy's  public statement of acceptance of a version permanently authorizes you  to choose that version for the Program.

  Later license versions may give you additional or different permissions.  However, **no additional obligations are imposed on any author or copyright holder** as a result of your choosing to follow a later version.
Notice that version 3 has clarification that no  additional obligations are imposed. And if you don't trust FSF that  GPLv4 will be in interest of software freedom, you might decide to use  "or (at proxy's option) some later version" instead of regular "or (at  your option) any later version". In that case, you assign someone to  make public statement whether project will move to version 4 or not. 

So if you didn't trust FSF FAQ, I hope you trust text of GPL.


Some reasons why using "later version" clause is good idea:

-If  certain version of GPL gets invalidated in court, FSF will in this  situation release new (fixed) version. In order to easily upgrade to new  version, you need to either have permission of all copyright holders,  or have "or later version" clause. It is obvious that later is easier. 

-In order to link GPLv3 program with GPLv2 one, later needs to have "GPLv2 or later" clause. 

-Obviously,  moving to new version is easier with "any later" clause and GPLv3 have  additional clarifications (as shown above), better patent clause, Apache  v2 compatibility, and it is generally better license. 

So  generally, I think it is smart decision to use "any later" clause. I  don't think FSF has some hidden motives that you seem to imply. They  were always predictable and honest about what they are doing. 

Cheers.

---

### Post by leorolla on 2010-09-15
> **gnufreex said:**
> Hi leorolla. 

I think you got it all wrong. FAQ is not 'incorrect' and 'evasive', it  is straight and correct answer. "or any later version" doesn't make any  legal problem. Also, FSF would maybe love that patent don't exist, but  GPLv3 can't force companies give them patents. Only to agree not to sue  community. That is big difference. They can still sue proprietary  competition. 

Section 9 of GPLv2 says:

So FAQ is not wishful thinking, it is based on the text of the license. GPLv3 is even better on this regard:

Notice that version 3 has clarification that no  additional obligations are imposed. And if you don't trust FSF that  GPLv4 will be in interest of software freedom, you might decide to use  "or (at proxy's option) some later version" instead of regular "or (at  your option) any later version". In that case, you assign someone to  make public statement whether project will move to version 4 or not. 

So if you didn't trust FSF FAQ, I hope you trust text of GPL.


Some reasons why using "later version" clause is good idea:

-If  certain version of GPL gets invalidated in court, FSF will in this  situation release new (fixed) version. In order to easily upgrade to new  version, you need to either have permission of all copyright holders,  or have "or later version" clause. It is obvious that later is easier. 

-In order to link GPLv3 program with GPLv2 one, later needs to have "GPLv2 or later" clause. 

-Obviously,  moving to new version is easier with "any later" clause and GPLv3 have  additional clarifications (as shown above), better patent clause, Apache  v2 compatibility, and it is generally better license. 

So  generally, I think it is smart decision to use "any later" clause. I  don't think FSF has some hidden motives that you seem to imply. They  were always predictable and honest about what they are doing. 

Cheers.

> So if you didn't trust FSF FAQ, I hope you trust text of GPL.

I'm not pro or against FSF. I see you're pro but I'm glad that anyway you understand that we must discuss this taking into account nothing but the  sandard copyright notice and the text of GPL.

What I don't see in these texts is on which right someone can modify my work and release the modifications under GPLv2+ if they are not obbeying the GPLv3 requirements. What part of my GPLv2+ copyright notice gave them such permission?

The "no additional obligations" that you highlight does not imply that the person who modified my work had the right to release the modifications under other licenses. _It means I grant them the extra permission to use the program under the terms of other licenses if they like it._ **My copyright notice does not ****in itself ****give explicit consent to pass forward this extra permission.** The notice does not even give *in itself* permission to redistribute the program in first place. It refers the licensee to another text, for instance GPLv2, and the license *itself* allows them to (modify and) redistribute it _under GPLv2 (with not more, nor less restrictions)_, and only after they have fulfilled important requirements. If they want to pass forward the permission to use the program under other licenses, they must therefore aquire the right of releasing the modified programs under these licenses, which means fulfilling the GPLv3 along with several many other requirements, otherwise they will be violating my copyrights.

Cheers \o/

---

### Post by forrestcupp on 2010-09-15
> **leorolla said:**
> 
It affects Me. Because if I release it under GPLv3, the only possible way I can do that without violating Your copyrights is by respecting the requirements stated in GPLv3. And if I release it under the traditional GPLv2+, that implies that I am releasing it under GPLv3 as well.

I don't think you're right about that.  If you release it under the traditional GPLv2+, it implies that you are releasing it under version 2, but giving yourself the option to easily change to version 3 or greater if you so desire in the future.

But even if you're right and that means that you're forced to automatically be obligated under whatever is the latest version, it's the distributor's decision on what license to use.  Anyone who chooses to add the + on the end must know what they're getting themselves into, so it's their choice to get themselves into that predicament.

---

### Post by saulgoode on 2010-09-15
> **leorolla said:**
> What I don't see in these texts is on which right someone can modify my work and release the modifications under GPLv2+ if they are not obbeying the GPLv3 requirements. What part of my GPLv2+ copyright notice gave them such permission?
There is no GPLv2+ license. In your hypothetical, you've released your code under the GPLv2 but offer the option for others to release derivatives under terms of (either the GPLv2 or) a subsequent GPL license. 

If someone releases a derivative and retains the "or any later version" language then *they* are not releasing it under a "GPLv2+" license, they are releasing it under GPLv2 but offering the option for others to release derivatives under terms of (either the GPLv2 or) a subsequent GNU license.

The same is true for any LGPLed software -- persons distributing it under the LGPL do not need to abide by the terms of the GPL **even though the LGPL permits the code to, at any time, be released as GPL** (Section 3 "*You may opt to apply the terms of the ordinary GNU General Public License instead of this License*").

---

### Post by forrestcupp on 2010-09-15
> **saulgoode said:**
> There is no GPLv2+ license. In your hypothetical, you've released your code under the GPLv2 but offer the option for others to release derivatives under terms of (either the GPLv2 or) a subsequent GNU license.

This is right. [Here is a great web page](http://hritcu.wordpress.com/2007/01/06/gplv2-or-later/) that explains the whole thing.  If you include the "or later" in your license version, your software license is not automatically changed when a new version comes out.  The "or later" just makes it easier to switch to a later version if that is what is desired.

My link explains the benefits pretty well.

---

### Post by leorolla on 2010-09-15
> **forrestcupp said:**
> I don't think you're right about that.  If you release it under the traditional GPLv2+, it implies that you are releasing it under version 2, but giving yourself the option to easily change to version 3 or greater if you so desire in the future.

But even if you're right and that means that you're forced to automatically be obligated under whatever is the latest version, it's the distributor's decision on what license to use.  Anyone who chooses to add the + on the end must know what they're getting themselves into, so it's their choice to get themselves into that predicament.

If it's my software I can change the license as I want.  I can release it under BSD next year if I feel like it. The question is other people modifying it and distributing modified versions...

Adding a + that was not there before is plain clear copyright violation. My point is that passing forward the + binds them to following GPLv3 requirements.

> **saulgoode said:**
> There is no GPLv2+ license. In your hypothetical, you've released your code under the GPLv2 but offer the option for others to release derivatives under terms of (either the GPLv2 or) a subsequent GNU license. 

If someone releases a derivative and retains the "or any later version" language then *they* are not releasing it under a "GPLv2+" license, they are releasing it under GPLv2 but offering the option for others to release derivatives under terms of (either the GPLv2 or) a subsequent GNU license.

The same is true for any LGPLed software -- persons distributing it under the LGPL do not need to abide by the terms of the GPL **even though the LGPL permits the code to, at any time, be released as GPL** (Section 3 "*You may opt to apply the terms of the ordinary GNU General Public License instead of this License*").

There is no GPLv2+ *license*. My example is about a GPLv2+ *copyright notice* as broadcast at FSF's website.

*> you've released your code under the GPLv2 but offer the option for others to  release derivatives under terms of (either the GPLv2 or) a subsequent  GNU license...*

I don't agree. I have not written "if you fulfill the  requirements of GPLv2 to distribute my program then you can choose under  which GPL you can release it" in my copyright notice. It's different. I have first stated my  copyrights over the program and then offered the person that received that copy the choice use it under the terms of GPLv2 or any later version. Using it under the terms of GPLv2 doesn't allow them to distribute it under any of GPLv3, GPLv6+, GPLv4, GPLv{even number}, even worse for GPLv2+. Using it under the terms of GPLv2 allows you to redistribute it under the terms of GPLv2, not more.

LGPL is more like what I think would solve this doubt I'm referring to   since the beginning. 

It's a bit like including the "pick the later version that you like,  make sure you obbey the  requirements, and re-license my work under that  version or later" from my previous post.
> **forrestcupp said:**
> This is right. [Here is a great web page]("http://hritcu.wordpress.com/2007/01/06/gplv2-or-later/") that explains the whole thing.  If you include the "or later" in your license version, your software license is not automatically changed when a new version comes out.  The "or later" just makes it easier to switch to a later version if that is what is desired.

My link explains the benefits pretty well.

My point is not about how licenses are upgraded. It's about other people being bound to the terms of the licenses under which they release conveyed work. If they want to release under GPLv2+, they are boung to GPLv3 as well.

---

### Post by saulgoode on 2010-09-15
> **leorolla said:**
> If it's my software I can change the license as I want.  I can release it under BSD next year if I feel like it. The question is other people modifying it and distributing modified versions...

Adding a + that was not there before is plain clear copyright violation. My point is that passing forward the + binds them to following GPLv3 requirements.

Have you included the "or any later version" language in your copyright notice? If not, then I would agree that no one but you has the right to add it to derivative distributions. But if you have included it then on what basis would you think that an author of a derivative can not likewise offer that option to recipients? If you've provided the "+" option for your copyrighted contribution, and the derivative's distributor offers the "+" option for his copyrighted contributed portion, then why would the recipient not have the "+" option?

> **leorolla said:**
> I don't agree. I have not written "if you fulfill the  requirements of GPLv2 to distribute my program then you can choose under  which GPL you can release it" in my copyright notice. It's different. I have first stated my  copyrights over the program and then offered the person that received that copy the choice use it under the terms of GPLv2 or any later version. ...

Perhaps you could provide the exact text of your copyright notice? It does not seem productive to engage in critical grammatical analysis of statements without actually knowing what was stated.

---

### Post by forrestcupp on 2010-09-15
> **leorolla said:**
> 
My point is not about how licenses are upgraded. It's about other people being bound to the terms of the licenses under which they release conveyed work. If they want to release under GPLv2+, they are boung to GPLv3 as well.

No.  If I release my own software under the GPLv2 "or later", I'm bound to version 2.  Then let's say someone else takes my code, alters it a little and releases it under the GPLv3 because I gave them that permission with the "or later".  I am still only bound to version 2, while the version of software that they release is now bound to version 3.

Just because they legally re-released it under a later version doesn't mean that I am bound to that later version with my release.  The point of the "or later" thing isn't so people can screw each other over, but to make it easier to upgrade the license in a case like one of the devs dying and not being able to give permission.

---

### Post by leorolla on 2010-09-16
```
    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 2 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
```

---

### Post by KiwiNZ on 2010-09-16
> **leorolla said:**
> ```
    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 2 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
```

Interesting, if that was attached to any software sold in New Zealand it would illegal under the Consumer Guarantee Act.

---

### Post by saulgoode on 2010-09-16
> This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 2 of the License, or (at your option) any later version.

The statement is only about what others are permitted to do, it does NOT assert that the software is currently being distributed under the terms of any later licenses. If a project were actually distributed under the terms of GPLv3 then the GPLv3 license would be included with the software package, not the GPLv2.


> **KiwiNZ said:**
> Interesting, if that was attached to any software sold in New Zealand it would illegal under the Consumer Guarantee Act.

:roll:

---

### Post by leorolla on 2010-09-16
> **forrestcupp said:**
> No.  If I release my own software under the GPLv2 "or later", I'm bound to version 2.  Then let's say someone else takes my code, alters it a little and releases it under the GPLv3 because I gave them that permission with the "or later".  I am still only bound to version 2, while the version of software that they release is now bound to version 3.

Just because they legally re-released it under a later version doesn't mean that I am bound to that later version with my release.  The point of the "or later" thing isn't so people can screw each other over, but to make it easier to upgrade the license in a case like one of the devs dying and not being able to give permission.

You are not bound to anything. It's Your work. They are bound to GPLv3.

The point is that if they release under GPLv2+, they are as well releasing it under GPLv3, in the sense that they are giving the to the downstream recipient the right to use it under the terms of that license. They are giving the recipient many other permissions, such as use it under GPLv4, GPLv2, etc.

Your copyright notice *in itself* did you authorize them to give anyone such permissions. 
Your copyright notice *in itself* didn't say they can do whatever they want to your program as long as they keep the same license.
Your copyright notice instead refers them to *external texts* which *themselves* say that they may redistribute your code once strict requirements are fulfilled.

[I] The [goal] of the "or later" thing isn't so people can screw each other  over, but to make it easier to upgrade the license in a case like one of  the devs dying and not being able to give permission.
[/I]
I agree. My point is that the text of the copyright notice together with the text of the licenses have not achieved this goal. It may be common practice that people will not enforce copyrights on a third party that conveyed their work and released it under GPLv2+, but I don't see why they don't have such right.

---

### Post by leorolla on 2010-09-16
> **saulgoode said:**
> The statement is only about what others are permitted to do, it does NOT assert that the software is currently being distributed under the terms of any later licenses. If a project were actually distributed under the terms of GPLv3 then the GPLv3 license would be included with the software package, not the GPLv2.


There was no  license included with your software. Just a copyright notice.

*it does NOT assert that the software is currently being distributed  under the terms of any later licenses*

I can't see that. The software is being distributed with a permissive copyright notice that gives the recipient the option to choose under which version of GPL they can use it.

If "the software is not being distributed under later licenses", what are the requirements John would have to fulfill if he wants to distribute your work to Bob giving Bob permission to use it under the terms of GPLv3? No condition whatsoever? GPLv2? Some abstract common-sense unwritten requirement?

I guess the answer is that in this case John has to fulfill the requirements of GPLv3 as "he decided to upgrade".

But wait... if John distributes it with a similar v2+ copyright notice, isn't he giving Bob permission to use it under the  terms of GPLv3 amongst other permissions?

---

### Post by leorolla on 2010-09-16
> **KiwiNZ said:**
> Interesting, if that was attached to any software sold in New Zealand it would illegal under the Consumer Guarantee Act.

OFF TOPIC
By "illegal" you probably mean that the notice would produce some of its legal effects, unless the Act explicitly forbids the reproduction of texts containing such words (including the Act itself :p).
I sort of agree. If you want to sell stuff with my GPL'ed software inside, maybe you as a manufacturer or shopkeeper will be bound to give the consumer some guarantee, not me. I have never seen a penny from such consumer.

---

### Post by red_Marvin on 2010-09-16
> **leorolla said:**
> I can't see that. The software is being distributed with a permissive copyright notice that gives the recipient the option to choose under which version of GPL they can **use** it.

If "the software is not being distributed under later licenses", what are the requirements John would have to fulfill if he wants to distribute your work to Bob giving Bob permission to **use** it under the terms of GPLv3? No condition whatsoever? GPLv2? Some abstract common-sense unwritten requirement?

I guess the answer is that in this case John has to fulfill the requirements of GPLv3 as "he decided to upgrade".

But wait... if John distributes it with a similar v2+ copyright notice, isn't he giving Bob permission to **use** it under the  terms of GPLv3 amongst other permissions?

**No.** The copyright talks about *redistribution* and *modification*, not use. (I would say there is a difference, but you are talking about redistribution acts, so nevermind at your choice)

The "or later" part is a promise that if developer A releases something as GPLv2, with the permission to the user to *redistribute/modify* it under the GPLv3 it means that developer B, can use that code to build new software, and distribute it under GPLv2/3/whatever he chooses without clashing with the copyright of the program that dev A worked on.

If the GPLv3 has some extra requirements on the developer, they are only
concerning developer B, since it was developer A distributed his/her work under the GPLv2, the code distributed under GPLv3 was all developed by developer B, or GPLv2 code redistributed under the GPLv3 _by developer B_ not developer A.

---

### Post by leorolla on 2010-09-16
> **red_Marvin said:**
> **No.** The copyright talks about *redistribution* and *modification*, not use. (I would say there is a difference, but you are talking about redistribution acts, so nevermind at your choice)

The "or later" part is a promise that if developer A releases something as GPLv2, with the permission to the user to *redistribute/modify* it under the GPLv3 it means that developer B, can use that code to build new software, and distribute it under GPLv2/3/whatever he chooses without clashing with the copyright of the program that dev A worked on.

If the GPLv3 has some extra requirements on the developer, they are only
concerning developer B, since it was developer A distributed his/her work under the GPLv2, the code distributed under GPLv3 was all developed by developer B, or GPLv2 code redistributed under the GPLv3 _by developer B_ not developer A.

There is no such a thing as "by developer B". His work was done on the top of the work of developer A, and he only had the right to do so because a copyright notice gave him the permission to modify/and redistribute it under the terms of some licenses, and the license gave him such permission but after he would have fulfilled certain requirements including requirements about the terms under which he would redistribute it.

My point is that developer B is bound to GPLv3 if he wishes to modify and redistribute it even if he wants to keep the standard copyright notice that I pasted above.

---

### Post by red_Marvin on 2010-09-16
> **leorolla said:**
> There is no such a thing as "by developer B". His work was done on the top of the work of developer A, and he only had the right to do so because a copyright notice gave him the permission to modify/and redistribute it under the terms of some licenses, and the license gave him such permission but after he would have fulfilled certain requirements including requirements about the terms under which he would redistribute it.

My point is that developer B is bound to GPLv3 if he wishes to modify and redistribute it even if he wants to keep the standard copyright notice that I pasted above.

Developer B does indeed exist, it is he/she who wrote the code that extends the code that develeoper A released.
If developer B, used the quoted copyright notice, I am sure that he released his code under the GPLv2, since AFAIK you cannot release something as GPLvX and permit redistribution under a version less than X (unless you dual-license, but that is a whole different topic), and your quote talks about GPLv2, not 3.

However, had developer B used a copyright notice for the GPLv3, of course he would be bound by the requirements of GPLv3, since that is what he released the code under. Surely *that* can't be the evasive problem in this topic?

---

### Post by leorolla on 2010-09-16
Two possible interpretations:

1. you can (use/modify/redistribute this software) under the terms of the GPL, either version 2, or any later version.

2. you can use/modify/redistribute (this software under the terms of (the GPL, either version  2, or any later version)).

I think we are used to make a distorted interpretation that mixes both.

The second is wrong and I don't think it would stand in court. I hope it wouldn't.

Otherwise people are not bound to anything. They can link to prprietary libraries, make tivoizaiton, whatever. There is no requirement being made whatsoever. It's not the GPL text that authorizes you to redistribute, it's the copyright notice. It's like "do whatever you want, just stick the same copyright notice to it and you are fine with my copyrights". (After writing  and re-reading this paragraph, it reminded me of some other licenses that are more free and less copyleft.)

The first interpretation is what I am saying. You can choose the license:

- If you choose v2, fine, but then you don't have the right to release it under any other conditions rather than GPLv2, you don't have the right to give your recipients further permissions.

- If you choose v3, even better, give away your keys and patents.

- If you choose them all, that's really great, you can pass to your recipients the permission to choose amongst them all, assuming that the future versions will allow you to do that and assuming that you will fulfill the upcoming requirements to do so.

----

It may sound a bit ackward to write like this, but for example, cutting a long story short, Debian has classified the mail client pine as non-free after the author told them that "permission to modify and redistribute" was meant for "permission to (modify) and (redistribute)" and not "permission to (modify and redistribute)".

---

### Post by leorolla on 2010-09-16
> **red_Marvin said:**
> Developer B does indeed exist, it is he/she who wrote the code that extends the code that develeoper A released.
If developer B, used the quoted copyright notice, I am sure that he released his code under the GPLv2, since AFAIK you cannot release something as GPLvX and permit redistribution under a version less than X (unless you dual-license, but that is a whole different topic), and your quote talks about GPLv2, not 3.

However, had developer B used a copyright notice for the GPLv3, of course he would be bound by the requirements of GPLv3, since that is what he released the code under. Surely *that* can't be the evasive problem in this topic?

I know B exists. What I am saying is that there is no "work done by B". There is "work done by A", which is the oritinal copy, and "work done by B on the top of the work by A". And B dind't have the right to do anything with the work by A in first place, unless there is a license authorizing that and the license in this case imposes conditions.

You are attached to thinking like "released under this or that GPL". **There is no such a thing.** You release it with a copyright notice that gives away some rights, which are otherwise all reserved to you according to the copyright laws. What this copyright notice says is "you can use (the word use here has the sense of anything that would be forbidden by copyright laws) it under the terms of a license you will find at this webpage, or any of those other licenses listed in this other webpage, at your choice".

Now the text my copyright notice pointed to (GPLv2) never gave you the right to redistribute my work to another recipient giving this recipient other rights than those stated in GPLv2.

It is nowhere written in this copyright notice that you have the broad right to give the recipient the permission to follow a later version. Only GPLv2 gives you the right to give the recipient the permission to follow GPLv2 and only GPLv3 gives you the right to give the recipient the permission to  follow GPLv3. Hopefully GPLv4 will give you the right to give the recipient the permission to  follow GPLv4.

---

### Post by forrestcupp on 2010-09-16
I really don't see what the problem is.  People who use the "or any later version" clause don't have a problem with people downstream choosing to use later versions, or they wouldn't have used that clause.  People who *do* have a problem with people downstream choosing a later version simply do not use that clause, and everyone is stuck to one specific license version.  Your complaint is kind of like you being mad at me for eating spinach because you don't like it.

Remember that everyone upstream and downstream are only bound to the version that *they* release their version of the software under.  The only limitations are to the downstream people, and that is that they can only choose to use a later version of the current license.  If dev A releases it under the v2+ license and dev B modifies it and releases it under the v3 license, then dev C comes along and doesn't like v3, he still has the choice to use the v2+ release from dev A.

If I really don't want someone to modify my software and release it under a later version of the GPL, then it would be silly for me to put the "or later" clause in there.  If I had that kind of attitude about my software, I might even choose to just make it proprietary.

Also, free software licenses don't have much to do with software *use* but with the distribution and modification of software.

If I'm misunderstanding your complaint, then why don't you clarify which person in the chain of development you think would have a problem with this?

---

### Post by leorolla on 2010-09-16
> **forrestcupp said:**
> I really don't see what the problem is.  People who use the "or any later version" clause don't have a problem with people downstream choosing to use later versions, or they wouldn't have used that clause.  People who *do* have a problem with people downstream choosing a later version simply do not use that clause, and everyone is stuck to one specific license version.  Your complaint is kind of like you being mad at me for eating spinach because you don't like it.

Remember that everyone upstream and downstream are only bound to the version that *they* release their version of the software under.  The only limitations are to the downstream people, and that is that they can only choose to use a later version of the current license.  If dev A releases it under the v2+ license and dev B modifies it and releases it under the v3 license, then dev C comes along and doesn't like v3, he still has the choice to use the v2+ release from dev A.

If I really don't want someone to modify my software and release it under a later version of the GPL, then it would be silly for me to put the "or later" clause in there.  If I had that kind of attitude about my software, I might even choose to just make it proprietary.

Also, free software licenses don't have much to do with software *use* but with the distribution and modification of software.

If I'm misunderstanding your complaint, then why don't you clarify which person in the chain of development you think would have a problem with this?

First of all, I agree with your values and intention. My point is that this is not really what is in the text.

The person in the chain who would have a problem:

A develops software. B modifies it and gives a copy to C.

Now C has the right to use, modify and distribute it under the terms of GPLv3. Why? Because C received a copy of the program with a copyright notice saying that he has permisson to choose a license from a list that includes GPLv3.

Who gave C this permission? B. Who gave B the permission to give such permission to C? Nobody! B got a copy from A saying that B could choose a list from the license and "distribute it under the terms of the chosen license".

It doesn't exlicitly grant B permission to give C the permission to follow GPLv3. The only thing that might grant him such permisson is the text of GPLv3 itself, **provided B fulfill its requirements**. This is **just as true** as the only thing that might possibly grant B the permission to give C the permission to use it under GPLv2 is the text of GPLv2 itself and not the copyright notice. Each of the GPLvN has a set or permissions and requirements for redistribution. _I don't see why B would be bound to GPLv2 more than he is bound to GPLv3 if he is giving C the permission to choose either license_, and the only way he could possibly grant both permissions without violating A's copyright is by fulfilling both the requirements of GPLv2 and GPLv3.

The copyright note says "(distribute it) under the terms of the chosen license" and not "distribute (it under the terms of the chosen license)". The second interpretation means there are no rules to follow whatsoever: "Just stick this notice and you are fine".

So, to answer your question:
The person in the chain of development I think could have a problem with  this is B.

It's like I tell you: "I give you meat, chicken, lettuce and spinach, you can eat chicken with lettuce or meat with spinach". Of course it is ridiculous that I get mad at you for eating chicken with spinach, but you didn't really have permission for that.

---

### Post by KiwiNZ on 2010-09-16
> **leorolla said:**
> ```
    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 2 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
```

What I am saying about this hybrid version of  of clause 15 is that is any Software issues under GPLv3 in New Zealand is covered by the Consumer protection legislation and as such has a minimum one year statutory warranty that cannot be contractually excluded. So if the product is faulty a claim may be made against the agent or the manufacturer.

---

### Post by forrestcupp on 2010-09-16
> **leorolla said:**
> 
Who gave C this permission? B. Who gave B the permission to give such permission to C? Nobody! B got a copy from A saying that B could choose a list from the license and "distribute it under the terms of the chosen license".Not true.  If A distributes it under what you call GPLv2+, then obviously A is giving permission to B to distribute B's version under the exact same license, which is GPLv2+.  So in effect, A is giving B permission to give C permission to do what GPLv2+ allows, which includes C choosing to release under GPLv3.  If A didn't want C to have that permission, then A wouldn't have released it under GPLv2+ in the first place.  Why wouldn't B be allowed to release the software under the exact same license?  That argument doesn't make sense.

> **leorolla said:**
> So, to answer your question:
The person in the chain of development I think could have a problem with  this is B.
B doesn't have to be bound to anything C does.  B only has to be bound to what B chooses to do within the limitations that A sets.  C is bound to what C does within the limitations that B sets which has to be within the limitations that A set in the beginning.  That's just how licenses work.

I really think you're misinterpreting this.

---

### Post by jwbrase on 2010-09-16
> **leorolla said:**
> First of all, I agree with your values and intention. My point is that this is not really what is in the text.

The person in the chain who would have a problem:

A develops software. B modifies it and gives a copy to C.

Now C has the right to use, modify and distribute it under the terms of GPLv3. Why? Because C received a copy of the program with a copyright notice saying that he has permisson to choose a license from a list that includes GPLv3.

Who gave C this permission? B. Who gave B the permission to give such permission to C? Nobody! B got a copy from A saying that B could choose a list from the license and "distribute it under the terms of the chosen license".

It doesn't exlicitly grant B permission to give C the permission to follow GPLv3. The only thing that might grant him such permisson is the text of GPLv3 itself, **provided B fulfill its requirements**. This is **just as true** as the only thing that might possibly grant B the permission to give C the permission to use it under GPLv2 is the text of GPLv2 itself and not the copyright notice. Each of the GPLvN has a set or permissions and requirements for redistribution. _I don't see why B would be bound to GPLv2 more than he is bound to GPLv3 if he is giving C the permission to choose either license_, and the only way he could possibly grant both permissions without violating A's copyright is by fulfilling both the requirements of GPLv2 and GPLv3.

The copyright note says "(distribute it) under the terms of the chosen license" and not "distribute (it under the terms of the chosen license)". The second interpretation means there are no rules to follow whatsoever: "Just stick this notice and you are fine".

So, to answer your question:
The person in the chain of development I think could have a problem with  this is B.

It's like I tell you: "I give you meat, chicken, lettuce and spinach, you can eat chicken with lettuce or meat with spinach". Of course it is ridiculous that I get mad at you for eating chicken with spinach, but you didn't really have permission for that.

The thing is that it's only a problem if GPL v2 forbids things that GPL v3 allows, or requires things that v3 forbids, which I do not believe is the case. I believe GNU is trying to write later versions of the GPL so that anything that conforms with them conforms with earlier versions.

---

### Post by jwbrase on 2010-09-16
> **KiwiNZ said:**
> What I am saying about this hybrid version of  of clause 15 is that is any Software issues under GPLv3 in New Zealand is covered by the Consumer protection legislation and as such has a minimum one year statutory warranty that cannot be contractually excluded. So if the product is faulty a claim may be made against the agent or the manufacturer.

I can still only see that applying if the software is actually sold, rather than given away for free.

---

### Post by leorolla on 2010-09-17
> **jwbrase said:**
> The thing is that it's only a problem if GPL v2 forbids things that GPL v3 allows, or requires things that v3 forbids, which I do not believe is the case. I believe GNU is trying to write later versions of the GPL so that anything that conforms with them conforms with earlier versions.

It is exactly the case. Both of these happen. GPL v2 forbids things that GPL v3 allows AND requires things that v3  forbids. That's why licenses are incompatible.

---

### Post by leorolla on 2010-09-17
> **jwbrase said:**
> I can still only see that applying if the software is actually sold, rather than given away for free.

OFF TOPIC

Of course! First of all, a license is not a contract. This program is my work. Mine!. It belongs to me. "All rights reserved." You don't even have the right to read it in first place. If there is a copyright notice attached to it and a license draft refered, you can read the license and it may grant you some permissions. Indeed GPL grants you permission to do a few stuff provided you fulfill some requirements. The license does not legally enforce requirements over anybody. But without fulfilling its requirements there is nothing else that grants you the right to read the source code, redistribute copies, or even run binarys. Again, it's my work. Copyrighted. All rights reserved.

And yes, a Consumer Guarantee Act obviously refers to Consumers, which means people who buy products. Not people who download my work (with all rights reserved) from a website.

This Act implies that peolple cannot *sell* Free Software in New Zealand, or at least that *people who sell it* must give Guarantee, not the author.

If a person at her own will downloads it directly from a repository, without giving any credit card number, she is not a Consumer in first place. Even if both the person and my website are in New Zealand. If I send this software to this person independently of the person's will, that doesn't make her a Consumer either.

---

### Post by leorolla on 2010-09-17
> **forrestcupp said:**
> Not true.  If A distributes it under what you  call GPLv2+, then obviously A is giving permission to B to distribute  B's version under the exact same license, which is GPLv2+.  So in  effect, A is giving B permission to give C permission to do what GPLv2+  allows, which includes C choosing to release under GPLv3.  If A didn't  want C to have that permission, then A wouldn't have released it under  GPLv2+ in the first place.  Why wouldn't B be allowed to release the  software under the exact same license?  That argument doesn't make  sense.

B doesn't have to be bound to anything C does.  B only has to be bound  to what B chooses to do within the limitations that A sets.  C is bound  to what C does within the limitations that B sets which has to be within  the limitations that A set in the beginning.  That's just how licenses  work.

I really think you're misinterpreting this.

[I]If A distributes it under what you  call GPLv2+, then **obviously** A is giving permission to B to distribute  B's version under the exact same license, which is GPLv2+.
[/I]
It sounds like religous dogma to me.

First, when I say GPLv2+, this is just a short name for attaching the standard copyright notice to the software we all know very well.

Whatever implications this copyright notice has when B receives a copy the program from A, which is otherwise protected by copyright laws, B needs to get it from the copyright notice. By copyright laws, B doesn't have the rights to read the code in first place. So one should  explain how the first phrase of the copyright notice is giving B permission to do anything that B is doing, from reading it to redistributing it, and in case B decides to redistribute it, under what conditions ("conditions" meaning both the conditions B must fulfill to distribute and the conditions under which B will release it to C).

Whatever B is doing with the code, B must read this one-sentence copyrioght notice and explain why A is giving such permission.

That's whay I mean by GPLv2+. If has another legal meaning to you, I  would like to know what it is and why it is so.

So, here I go again, point by point. I would be happy to know which points you think are correct and which ones are not.

1. B is giving C the permission to read/use/run/modify/redistribute it under GPLv2.

2. B is giving C the permission to read/use/run/modify/redistribute it  under GPLv3.

3. B is giving C even more permissions than these two, just for example, "use" it under GPLv8.

4. The only thing that might  grant B the permission to give C the permisson to "use" it under GPLv2 is _by no means the poor one-phrase copyright notice in itself,_ but rather the text of GPLv2 that B will download from FSF's website, **provided B  fulfill its requirements**.

5. The only thing that might  grant B the permission to give C the permisson to "use" it under GPLv3 is _by no means the poor one-phrase copyright notice in itself,_  but rather the text of GPLv3 that B will download from FSF's website, **provided  B  fulfill its requirements**.

6. There is no such asymmetry in the copyright notice clearly implying that point "4" is any more true than point "5" above. Maybe common practice, or the fact that "2 or later" made the number 2 appear in the notice unlike the number 3 are giving you this feeling. But otherwise, as long as the legal permissions A is giving to B are concerned, there is no such asymmetry.

7. Therefore, either you agree that "5" is true and you agree with my whole point, or you claim that "4" is not true, or else you claim "6" is not true. If "4" is wrong, then B doesn't even need to disclose its source code. B is s givng C permission use the program under what you think GPLv2+ means, period. B had no direct obligations to C in any case, and assuming "4" is wrong, B has fulfilled the A's requirements by simply leaving the copyright notice unchanged. So the only reasonable option left is that "6" would be wrong, and you need to better explain why there is such asymmetry.

---

### Post by forrestcupp on 2010-09-17
> **leorolla said:**
> [I]If A distributes it under what you  call GPLv2+, then **obviously** A is giving permission to B to distribute  B's version under the exact same license, which is GPLv2+.
[/I]
It sounds like religous dogma to me.It sounds more like the transitive property to me.

If A=B and B=C, then also A=C.


> **leorolla said:**
> Whatever implications this copyright notice has when B receives a copy the program from A, which is otherwise protected by copyright laws, B needs to get it from the copyright notice. By copyright laws, B doesn't have the rights to read the code in first place.That's why they call free software licenses "Copyleft" instead of "Copyright".  You're still thinking with a proprietary mindset.  The whole purpose of copyleft is so that we can still have some limitations, but not be bound by some of the restrictions of copyright.  It's freedom with some restrictions.

A uses GPLv2+, B releases under the exact same license without changing anything about the license, so C gets the benefits of the permissions set forth by A.  If B would have legally changed to v3, C would be bound by v3.

Lotus Symphony is a great example of someone taking a copylefted software (OpenOffice.org 1.1.4), modifying it, and legally releasing it under a different license.  You're only bound by the specific limitations that the original license sets.  

That's the difference between copyleft and copyright.  People who don't identify with that have the option to use a proprietary license.

---

### Post by leorolla on 2010-09-17
> **forrestcupp said:**
> It sounds more like the transitive property to me.

If A=B and B=C, then also A=C.

That's why they call free software licenses "Copyleft" instead of "Copyright".  You're still thinking with a proprietary mindset.  The whole purpose of copyleft is so that we can still have some limitations, but not be bound by some of the restrictions of copyright.  It's freedom with some restrictions.

A uses GPLv2+, B releases under the exact same license without changing anything about the license, so C gets the benefits of the permissions set forth by A.  If B would have legally changed to v3, C would be bound by v3.

Lotus Symphony is a great example of someone taking a copylefted software (OpenOffice.org 1.1.4), modifying it, and legally releasing it under a different license.  You're only bound by the specific limitations that the original license sets.  

That's the difference between copyleft and copyright.  People who don't identify with that have the option to use a proprietary license.

This kind of statement won't become true by being repeated over and over.

Copyleft only exists because it's protected by the same laws that protect proprietary or semi-free software. If you want it it have any practical effect you have to analyse it from a pure copyright point of view. FSF should battle against people referring to copyleft as opposed to copyright because this generates such misunderstandings. From a legal point of view, copyleft is nothing but a clever use of copyrights.

You say I'm attached to a proprietary mindset. I'm not, I'm just trying to argue that the legal implications of the content of that copyright notice may not be what we want it to be, in spite of common practice.

Maybe you are attached to this "transitive" mindset.

Please read the remainder of the post you have just replied to and tell me which claims you think are right and which are not.

From the copyright notice, B would have the right to distribute code under GPLv2+ if GPLv2 contained a clause like "Each version is given a distinguishing version number.  If the Program specifies a version number of this License which applies to it and "any later version", you can redistribute this program with or without modifications under any later version provided you fulfill the requirements stated in section 2 of the present license". But that's not what it says there. This problem could have been fixed in GPLv3 if they said "If you received a copy with permissions to use this work under GPLv2 as well, you can distribute conveyed work under the terms of this license provided you fulfill the requirements stated in section 2 of that license." But that's not what it says there either.

---

### Post by saulgoode on 2010-09-17
> **leorolla said:**
> So, here I go again, point by point. I would be happy to know which points you think are correct and which ones are not.
:
:
:
5. The only thing that might  grant B the permission to give C the permisson to "use" it under GPLv3 is _by no means the poor one-phrase copyright notice in itself,_  but rather the text of GPLv3 that B will download from FSF's website, **provided  B  fulfill its requirements**.

"B" is vested with the power to grant "C" permission to distribute under the terms of the GPLv3 because "B" has made a copyrighted contribution to the joint work and is recognized under copyright law (in the U.S., anyway) as having the prerogative of granting to others any and all exclusive rights to the joint work *as long as he has permission from the other co-authors of the joint work*. In your scenario, this permission from the other co-authors has been granted by the notice included with the original, unmodified software that "B" received from "A". 

In the event that "B" is providing "C" with unmodified software (from "A"), then "B" is NOT a co-author of the work and the authority for "C" to distribute under the terms of the GPLv3 is not necessarily being *granted* by "B", yet "C" is receiving it; the authority under which "C" can distribute under GPLv3 has been granted by "A".

Under the GPL, it does not matter how you obtain the software. You can receive a copy from "A", "B", "C", or any other letter of the alphabet and the licensing grants you receive are the ones specified in the copy you receive. It does not matter if "C" receives GPLed software from someone who is not complying with terms of the GPL -- or is complying with the terms of a different version of the GPL. It does matter if the software was sold, rented, borrowed, or stolen. The terms of the included GPL licensing apply to anyone who obtains a copy of the software. 

If "C" has obtained an unmodified copy of "A"'s software then it does not matter whether "C" received it from "A" or from "B"; the permissions that "C" obtains are the same. 

Even if your argument is that "B" does not have the right to distribute "A"'s unmodified GPLv2+ software as GPLv3-**only** (because "B" is then not a co-author of the work), I still don't think any court would agree. "A"'s copyright notice explicitly grants "B" the right to do this; and as the copyright holder of the work, "A" is authorized by copyright law to pass his exclusive rights to others (and one of those exclusive rights is the right to pass on exclusive rights to others). Either way, the point is somewhat moot. Being as it's GPLed, "C" should have little problem obtaining a copy of "A"'s software which has the original licensing terms intact.

---

### Post by leorolla on 2010-09-17
> **saulgoode said:**
> "B" is vested with the power to grant "C" permission to distribute under the terms of the GPLv3 because "B" has made a copyrighted contribution to the joint work and is recognized under copyright law (in the U.S., anyway) as having the prerogative of granting to others any and all exclusive rights to the joint work *as long as he has permission from the other co-authors of the joint work*. In your scenario, this permission from the other co-authors has been granted by the notice included with the original, unmodified software that "B" received from "A". 

In the event that "B" is providing "C" with unmodified software (from "A"), then "B" is NOT a co-author of the work and the authority for "C" to distribute under the terms of the GPLv3 is not necessarily being *granted* by "B", yet "C" is receiving it; the authority under which "C" can distribute under GPLv3 has been granted by "A".

Under the GPL, it does not matter how you obtain the software. You can receive a copy from "A", "B", "C", or any other letter of the alphabet and the licensing grants you receive are the ones specified in the copy you receive. It does not matter if "C" receives GPLed software from someone who is not complying with terms of the GPL -- or is complying with the terms of a different version of the GPL. It does matter if the software was sold, rented, borrowed, or stolen. The terms of the included GPL licensing apply to anyone who obtains a copy of the software. 

If "C" has obtained an unmodified copy of "A"'s software then it does not matter whether "C" received it from "A" or from "B"; the permissions that "C" obtains are the same. 

Even if your argument is that "B" does not have the right to distribute "A"'s unmodified GPLv2+ software as GPLv3-**only** (because "B" is then not a co-author of the work), I still don't think any court would agree. "A"'s copyright notice explicitly grants "B" the right to do this; and as the copyright holder of the work, "A" is authorized by copyright law to pass his exclusive rights to others (and one of those exclusive rights is the right to pass on exclusive rights to others). Either way, the point is somewhat moot. Being as it's GPLed, "C" should have little problem obtaining a copy of "A"'s software which has the original licensing terms intact.



[I]In your scenario, this permission from the other co-authors [to distribute under the terms of the GPLv3] has been granted by the notice included with the original, unmodified software that "B" received from "A".
[/I]
If you claim that the one-sentence copyright notice gave "B" such permission, then why does "B" need to disclosure source code? That's my point "6" above.


[I]It does not matter if "C" receives GPLed software from someone who is not complying with terms of the GPL -- or is complying with the terms of a different version of the GPL.
[/I]
"C" is fine. It's "B" who may be in trouble here. (See previous posts.)


[I]If "C" has obtained an unmodified copy of "A"'s software then it does not matter whether "C" received it from "A" or from "B"; the permissions that "C" obtains are the same. ... "C" should have little problem obtaining a copy of "A"'s software which has the original licensing terms intact.
[/I]
What if "C" is a guy who got a copy of this software installed inside an electronic device he has just bough, and "B" is Tivo? For "C", it doesn't matter whether the copy came from "A" or "B" since it is the same. But if it came from "B", it binds "B" to the license. If "B" is propagating the work, the fact that "C" could've got a copy from "A" doesn't exempt "B".

---

### Post by forrestcupp on 2010-09-17
> **leorolla said:**
> 
If you claim that the one-sentence copyright notice gave "B" such permission, then why does "B" need to disclosure source code? That's my point "6" above.
B needs to disclose source code because B is bound to GPLv2+, and one of the regulations of GPLv2+ is that anyone distributing the software *has* to disclose the source code.  Why is that a question?

> **leorolla said:**
> What if "C" is a guy who got a copy of this software installed inside an electronic device he has just bough, and "B" is Tivo? For "C", it doesn't matter whether the copy came from "A" or "B" since it is the same. But if it came from "B", it binds "B" to the license. If "B" is propagating the work, the fact that "C" could've got a copy from "A" doesn't exempt "B".
If B is Tivo and Tivo used GPLv2+ software, then unless B is ignorant, B is going to choose to be bound to version 2 instead of version 3.  It doesn't matter that C takes the software and chooses to be bound by GPLv3; B is still only bound to GPLv2 because that's what *B* chose to be bound by.

---

### Post by saulgoode on 2010-09-17
> **leorolla said:**
> What if "C" is a guy who got a copy of this software installed inside an electronic device he has just bough, and "B" is Tivo? For "C", it doesn't matter whether the copy came from "A" or "B" since it is the same. But if it came from "B", it binds "B" to the license. If "B" is propagating the work, the fact that "C" could've got a copy from "A" doesn't exempt "B".

"B" is obligated to fulfill the terms and conditions of the license so that he can engage in activities which would otherwise be prohibited by copyright law. Neither "B"'s obligation nor the terms which he must satisfy are affected by any transaction that might occur between "A" and "C"; nor would it be affected by any transaction between "C" and "D", nor "A" and "D", ...

"B" doesn't have to fulfill the terms of ALL licenses attached (attachable?) to the software, if he satisfies the terms and conditions of just one of them then he can distribute copies without infringing upon "A"'s copyrights. "B" can even (and IIUC this is the part you contend) offer recipients the option of distributing copies under one of the other available licenses than the one upon which he himself is relying (e.g., a later version).

---

