---
title: "Beyond being different; Haiku has a superior License over the GPL?"
date: 2009-09-26
forum: The Cafe
---

### Post by HappinessNow on 2009-09-26
Beyond being different; Haiku has a superior License over the GPL?

> 
**Haiku (operating system)**

[License]("http://en.wikipedia.org/wiki/Software_license") [MIT License]("http://en.wikipedia.org/wiki/MIT_License")[http://en.wikipedia.org/wiki/Haiku_%28operating_system%29]("http://en.wikipedia.org/wiki/Haiku_%28operating_system%29")

> The **MIT License** is a [free software license]("http://en.wikipedia.org/wiki/Free_software_license") originating at the [Massachusetts Institute of Technology]("http://en.wikipedia.org/wiki/Massachusetts_Institute_of_Technology") (MIT), used by the [MIT X Consortium]("http://en.wikipedia.org/wiki/MIT_X_Consortium").
 It is a [permissive]("http://en.wikipedia.org/wiki/Permissive_free_software_licence") license, meaning that it permits reuse within [proprietary software]("http://en.wikipedia.org/wiki/Proprietary_software") on the condition that the license is distributed with that software. The license is also [GPL-compatible]("http://en.wikipedia.org/wiki/GNU_General_Public_License#Compatibility_and_multi-licensing"), meaning that the [GPL]("http://en.wikipedia.org/wiki/GPL") permits combination and redistribution with software that uses the MIT License.
 According to the [Free Software Foundation]("http://en.wikipedia.org/wiki/Free_Software_Foundation"), the MIT License is more accurately called the **X11 license**, since MIT has used many licenses for software[[1]]("http://en.wikipedia.org/wiki/MIT_License#cite_note-0") and the license was first drafted for the [X Window System]("http://en.wikipedia.org/wiki/X_Window_System").[http://en.wikipedia.org/wiki/MIT_License](http://en.wikipedia.org/wiki/MIT_License)

Note: Title ended in 'question mark' to inspire discussion and not meant as a proclamation, but after much research it does appear the X11 License is more versatile and superior overall?...this from a layman's perspective. It would be interesting what a law professional would have to say.

The X11 License is GPL compatible yet not as restrictive as a GPL standing on it's own. The Haiku dev. community has made a very wise choice in the X11 License (AKA MIT License).

---

### Post by saulgoode on 2009-09-26
From a user standpoint, there is no difference between the GPL and the MIT licenses. The only differences are from a developer/distributor standpoint, and different developers/distributors have different preferences between licenses.

---

### Post by gnomeuser on 2009-09-26
The GPL aims to enforce it's political goals on everyone else, it aims to enforce sharing instead of expecting it. From the stance of the length of the license text the GPL is very complex, it's text (for the GPLv2) means different things depending on which country you are in. It's also unintentionally incompatible with a few licenses. These are problems attempted to be fixed in the controversial GPLv3.

The GPL is fundamentally problematic in a number of scenerios, e.g. embedded vendors tend to have problems with some of it's requirements and often get in trouble because of it or elect to redo vast amounts of code to work around the GPLs requirements (e.g. Google does this with android to avoid glibc GPL license). Both situations I feel are undesirable for the user, legal problems tend to distract from development and redoing already well tested code tends to be the road to security and stability problems. Thus they tend to prefer more liberal licenses.

Personally I tend to prefer something like the MS-PL (Microsoft Permissive License). It's simple, elegant and handles the cases I care about. It is basically the MIT license with a patent grant clause. It doesn't enforce contributions like the GPL does with legal means, I think though that the pure technical and social benefits of contribution tends to be enough to encourage it.. at least thus seems to be the trend so far looking at projects like the BSDs which do get plenty contributions back from companies and people despite not demanding it. 

It is also far more compatible with other licenses, you do not get situations like the recent apple release of libdispatch (part of their grand central dispatch project). They elected the Apache license which is GPLv2 incompatible, meaning that a large part of the Linux userspace can't use it. Instead of focusing on the technically superior open solution a clearly unintended incompatibility (since it was removed in GPLv3) keeps the software ecosystem from benefiting. Being more compatible clearly has it's advantages.

---

### Post by HappinessNow on 2009-09-26
> **gnomeuser said:**
> The GPL aims to enforce it's political goals on everyone else, it aims to enforce sharing instead of expecting it. From the stance of the length of the license text the GPL is very complex, it's text (for the GPLv2) means different things depending on which country you are in. It's also unintentionally incompatible with a few licenses. These are problems attempted to be fixed in the controversial GPLv3.

The GPL is fundamentally problematic in a number of scenerios, e.g. embedded vendors tend to have problems with some of it's requirements and often get in trouble because of it or elect to redo vast amounts of code to work around the GPLs requirements (e.g. Google does this with android to avoid glibc GPL license). Both situations I feel are undesirable for the user, legal problems tend to distract from development and redoing already well tested code tends to be the road to security and stability problems. Thus they tend to prefer more liberal licenses.

Personally I tend to prefer something like the MS-PL (Microsoft Permissive License). It's simple, elegant and handles the cases I care about. It is basically the MIT license with a patent grant clause. It doesn't enforce contributions like the GPL does with legal means, I think though that the pure technical and social benefits of contribution tends to be enough to encourage it.. at least thus seems to be the trend so far looking at projects like the BSDs which do get plenty contributions back from companies and people despite not demanding it. 

It is also far more compatible with other licenses, you do not get situations like the recent apple release of libdispatch (part of their grand central dispatch project). They elected the Apache license which is GPLv2 incompatible, meaning that a large part of the Linux userspace can't use it. Instead of focusing on the technically superior open solution a clearly unintended incompatibility (since it was removed in GPLv3) keeps the software ecosystem from benefiting. **Being more compatible clearly has it's advantages.**

I couldn't agree more.

---

### Post by Dayofswords on 2009-09-26
i like the idea of [beerware]("http://en.wikipedia.org/wiki/Beerware") really, but i'd like a cheeseburger instead

---

### Post by HappinessNow on 2009-09-26
> **Dayofswords said:**
> i like the idea of [beerware]("http://en.wikipedia.org/wiki/Beerware") really, but i'd like a cheeseburger instead
Much better then the GPL. :P

---

### Post by gnomeuser on 2009-09-26
> **Dayofswords said:**
> i like the idea of [beerware]("http://en.wikipedia.org/wiki/Beerware") really, but i'd like a cheeseburger instead

Sadly the beerware license is also a poor choice, there are a number of situations where licenses like that has caused problems by being unclear about liability, patent licenses and so on. I have a few stories of companies reimplementing code to avoid it.

---

### Post by zolookas on 2009-09-26
ISC license is a bit shorter than MIT: [http://en.wikipedia.org/wiki/ISC_license](http://en.wikipedia.org/wiki/ISC_license).
According to Wikipedia "it is functionally equivalent to the 2-clause BSD license, with language "*made unnecessary by the Berne convention*" removed".

---

### Post by t0p on 2009-09-26
> **gnomeuser said:**
> The GPL aims to enforce it's political goals on everyone else, it aims to enforce sharing instead of expecting it.

What exactly is wrong with that?  The FSF is a political organization.  If you don't like the license you don't have to use it.

This is something I've never understood.  If you don't like the terms of the GPL, don't use it.  Nobody *forces* you to use GPLed code in your project.

> **gnomeuser said:**
> 
Personally I tend to prefer something like the MS-PL (Microsoft Permissive License). It's simple, elegant and handles the cases I care about. It is basically the MIT license with a patent grant clause. It doesn't enforce contributions like the GPL does with legal means, I think though that the pure technical and social benefits of contribution tends to be enough to encourage it.. at least thus seems to be the trend so far looking at projects like the BSDs which do get plenty contributions back from companies and people despite not demanding it. 

You're right: there are developers who share despite the fact that they're not forced to.  But there are also developers and companies who would happily take free code and make it proprietary.  However, if a dev wants to make sure his code remains free, he can of course choose a stricter license.  That's what freedom's all about.

But I completely disagree with you about software patents.  I'm not going to rehash here the whole argument  about software patents.  If anyone's interested, there's more on the subject [here]("http://www.nosoftwarepatents.com/en/m/basics/index.html").  And an instructive real-world example is described [here]("http://news.cnet.com/Small-patent-may-have-big-impact/2100-1023_3-214313.html").  I'll just say: software patenting is *wrong*; therefore any license that permits software patenting is* wrong*.

But at the end of the day, all of this argument about the terms of different licenses doesn't really mean much to the average end-user.  To the user, the GPL and MIT licenses are equally good. They both give the user the right to use, copy, modify, merge, publish, distribute, sublicense, and/or sell the software.    So both are preferable to proprietary licenses that give the user nothing.

---

### Post by Xbehave on 2009-09-26
GPL forces contributors to give back.
for my basic understanding MIT, like BSD does not.

I am a fan of forcing giving back as it is one of the things that makes linux strong, IBM, intel, sun etc all **have** to play nice.

I don't think arguments over forcing/not forcing can be won lost, and any argument of MIT v GPL will just be rehashing that.

---

### Post by gnomeuser on 2009-09-26
> **t0p said:**
> 

You're right: there are developers who share despite the fact that they're not forced to.  But there are also developers and companies who would happily take free code and make it proprietary.  However, if a dev wants to make sure his code remains free, he can of course choose a stricter license.  That's what freedom's all about.

But I completely disagree with you about software patents.  I'm not going to rehash here the whole argument  about software patents.  If anyone's interested, there's more on the subject [here]("http://www.nosoftwarepatents.com/en/m/basics/index.html").  And an instructive real-world example is described [here]("http://news.cnet.com/Small-patent-may-have-big-impact/2100-1023_3-214313.html").  I'll just say: software patenting is *wrong*; therefore any license that permits software patenting is* wrong*.

But at the end of the day, all of this argument about the terms of different licenses doesn't really mean much to the average end-user.  To the user, the GPL and MIT licenses are equally good. They both give the user the right to use, copy, modify, merge, publish, distribute, sublicense, and/or sell the software.    So both are preferable to proprietary licenses that give the user nothing.

Did you actually read the GPL?

I suggest you read section 11 aptly named "Patents" (GPLv3 used but the same concept applies to GPLv2). The GPL requires that any patents on the software be granted in full to anyone. It does NOT prohibit patenting as you seem to assume, it actively discourages them in the text but makes them available for implementation if they exist on a given code base covered by the GPL. The GPL even uses patents against license violators by removing the patent grant in such cases making you open to litigation.

The MS-PL likewise includes a software patent grant giving everyone full unlimited access to the patent. There is no fundamental difference in the way these two work with regards to patents.

---

### Post by keiichidono on 2009-09-26
What I want to know is, why did they choose MIT over BSD or ISC?

---

### Post by gnomeuser on 2009-09-26
> **Xbehave said:**
> GPL forces contributors to give back.
for my basic understanding MIT, like BSD does not.

I am a fan of forcing giving back as it is one of the things that makes linux strong, IBM, intel, sun etc all **have** to play nice.

I don't think arguments over forcing/not forcing can be won lost, and any argument of MIT v GPL will just be rehashing that.

You could also argue, with evidence mind you, that forcing contributions lesses cooperation and thus hurts security and standardization. 

Take the example of Android avoiding glibc because of it's license and it's strict requirement, is that a good or a bad situation for Linux as a whole. I would argue that more people using the same code and working on the same code is better (provided naturally that it is OSI compliant Open Source as a baseline). Even if we will have a few deviants who elect not to cooperate.

On the other hand there are scenerios where mandatory contribution is a good thing overall. Take the kernel, there have been relatively few cases of otherwise open technology being forced out based on the demands of the GPL. Most noteable and most saddening is probably the cases of dtrace and zfs. However when weighted up against the number of contributions from companies and people who happen to use Linux with modifications it is a worthwhile trade off. There are many reasons why it works for the kernel, I suspect the primary right now is that the kernel is one of the fastest moving projects in the world, it is simply more cost effective to be in than out. Given the multitude of uses the kernel sees you get a vibrant ecosystem and lots of varied contributions.

I think there is no one superior solution, I think though as a base it is good to assume altruism rather than to mandate it. There will be cases of abuse but as the codebase grows I think it will be found from such parties that the cost of maintaining their own patch in sync with upstreams rapid improvement is more costly than to contribute. Others will do it because of customer pressure or other business reasons such as consistent bad PR or a refusal from upstream to take bugs from this source. Others still will benefit from having their improvements reviewed and improved by their peers, they will gain development time free of charge from the community which is a savings. 

Still no one size fits all, it never will. Licenses should be carefully considered for their goals and their impact on the larger software ecosystem. The same goes for considerations of copyright assignment.

---

