---
title: "Ubuntu repository and GPL licensed library"
date: 2013-09-22
forum: Ubuntu, Linux and OS Chat
---

### Post by tioui on 2013-09-22
Hi,

I was looking into the "Ubuntu component licence policy" at [http://www.ubuntu.com/about/about-ubuntu/licensing]("http://www.ubuntu.com/about/about-ubuntu/licensing"). In the requirement section, you can see this item:

> Must not discriminate against persons, groups or against fields of endeavour. The licence of software included in Ubuntu can not discriminate against anyone or any group of users and cannot restrict users from using the software for a particular field of endeavour - a business for example. So we will not distribute software that is licensed "freely for non-commercial use".

Then, I ask myself: Why is there GPL licenced libraries in the "Main" and "Universe" archive area? In my understanding of the GPL license, it restrict the selling of any software created with GPL licensed library if the source code of the software is not also ditributed. Is it not what they mean by "...restrict users from using the software for a particular field of endeavour...".

So, if somebody want to explain this to me, I would be glad.

Thanks!

Louis M

---

### Post by oldos2er on 2013-09-25
Moved to Ubuntu, Linux, & OS Chat.

---

### Post by grahammechanical on 2013-09-25
So, if your understanding is correct I can sell my code that I have licensed under the GPL provided I include source code as well. And do not forget to include details of the license also.  What is the problem? How hard is it to meet that requirement?

Did you see this in that link?

> [COLOR=#333333][FONT=Ubuntu]This policy only addresses the software that you will find in main and restricted, which contain software that is fully supported by the Ubuntu team and must comply with this policy.[/FONT][/COLOR]

No mention of "Universe" repositories. There is much in that Ubuntu statement that mirrors what is in the GPL. Ubuntu developers do not have any issue with software (including libraries) that are licensed under the GPL. That Ubuntu statement is in relation to software developers using licenses that in some way go against Ubuntu's free software philosophy. That statement makes certain assurances to us the user that protect our rights in regard to free and open source software.

This

> [COLOR=#333333][FONT=Ubuntu]Must include source code. The main component has a strict and non-negotiable requirement that application software included in it must come with full source code.[/FONT][/COLOR]


only applies to "main" and not to "restricted" because the restricted repository or archive contains proprietary software and the owners would not allow us the right to install it without charge if they were forced to provide the source code. Where would Linux users be if we were not able to use proprietary video drivers or audio and video codecs?

Imagine if the owners of proprietary video drivers only made their code available through Ubuntu with a license that restricted the video driver to single users and forbade businesses from using the driver. In this case the driver would not be available through Ubuntu because the license would restrict users in the business field of endeavour.

If you want to claim that the GPL in anyway discriminates against persons, groups, or against fields of endeavour then you must provide the evidence for such a claim. Or take it up with those who wrote the GPL.

Regards.

---

### Post by tioui on 2013-09-25
Thanks for the explaination. But no, I don't claim anything. I just ask. I'm curious.

Well, thanks again,

Louis M

---

### Post by ssam on 2013-09-26
The difference between main and universe is to do with support from canonical, which developers can upload and dependancies between packages.

> **tioui said:**
> 
Then, I ask myself: Why is there GPL licenced libraries in the "Main" and "Universe" archive area? In my understanding of the GPL license, it restrict the selling of any software created with GPL licensed library if the source code of the software is not also ditributed. Is it not what they mean by "...restrict users from using the software for a particular field of endeavour...".


This to prevent licences that say things like 'free for educational use' or 'free for non-comercial use' or 'this software can't be used for millitary use'.

The GPL is quite clear that anyone should be able to use a program for any purpose. (if they want to distribute the software they must ensure the freedoms are passed on). see [https://www.gnu.org/philosophy/free-sw.html](https://www.gnu.org/philosophy/free-sw.html)

I think ubuntu's definition is inherited from [http://www.debian.org/social_contract#guidelines](http://www.debian.org/social_contract#guidelines)

---

### Post by tioui on 2013-09-26
Thanks ssam for your answer.

You will forgive me if I continue the discussion. 

In fact, the point is, I want to create a debian/ubuntu package of an application. It is a GPL compiler for a certain language. The problem is, when the compiler is building an executable, it link a GPL run-time library to the executable. So, because of this, every application created with this compiler has to be GPL (or compatible). That make it almost impossible to use it in a commercial use (selling close software). You cannot even decide to license your own application with a more permissive OpenSource license like the original BSD license.

So, before I put time on this package, I want to know if one day it can be add in one of the main, restricted, universe or multiverse archive repository. Because there is no doubt that it "restrict" the users on what license they will use for there applications.

---

### Post by ian-weisser on 2013-09-26
> **tioui said:**
> I want to create a debian/ubuntu package of an application. It is a GPL compiler for a certain language. The problem is, when the compiler is building an executable, it link a GPL run-time library to the executable. So, because of this, every application created with this compiler has to be GPL (or compatible).

I don't think software built using the tool needs to be GPL.
However, the run-time library source and license must be made available to any of your customers per the conditions of the GPL. Since you didn't write the library, and it is GPL, you cannot hide the fact that you used it.

You can use or create an alternative library, if you wish, that has a different license. You can also contact the authors of the required library and ask them to license it for use in your product under a different license.


> **tioui said:**
> That make it  almost impossible to use it in a commercial use (selling close  software). You cannot even decide to license your own application with a  more permissive OpenSource license like the original BSD license.

You can definitely sell GPL software. It's specifically permitted! You must merely, upon request, make the source code available to your customer. You are not required to make the source available to non-customers.

You can also sell mixed-license software, as long as long as you entirely comply with all the various licenses. I have seen companies do that, too.



> **tioui said:**
> So, before I put time on this package, I want to know if one day it can  be add in one of the main, restricted, universe or multiverse archive  repository. Because there is no doubt that it "restrict" the users on  what license they will use for there applications.

Yes, it can be in the Ubuntu repositories. The key is understanding who maintains the software *and* the license. For example, software in main and restricted are officially supported. If a Canonical engineer cannot see the source and maintain the package, it won't be in those repositories regardless of the license.

No,I don't think GPL is restricting your freedom to develop under any license you wish. It really only restricts you from arbitrarily closed-sourcing the elements of your product that somebody else created open. But you certainly can sell software with GPL components, and you certainly can create closed-source packages that depend upon open-source software.

---

### Post by tioui on 2013-09-26
> **ian-weisser said:**
> No,I don't think GPL is restricting your freedom to develop under any license you wish. It really only restricts you from arbitrarily closed-sourcing the elements of your product that somebody else created open. 

On the FAQ of the GPL library ([http://www.gnu.org/licenses/gpl-faq.en.html#WhatCaseIsOutputGPL](http://www.gnu.org/licenses/gpl-faq.en.html#WhatCaseIsOutputGPL)), you can see:

> **In what cases is the output of a GPL program covered by the GPL too**
Only when the program copies part of itself into the output.

Also there ([http://www.gnu.org/licenses/gpl-faq.en.html#IfLibraryIsGPL](http://www.gnu.org/licenses/gpl-faq.en.html#IfLibraryIsGPL)):

> **If a library is released under the GPL (not the LGPL), does that mean that any software which uses it has to be under the GPL or a GPL-compatible license?**
Yes, because the software as it is actually run includes the library.

This is why I was confuse. But your comments help me a lot. Thanks.

Louis M

---

### Post by ssam on 2013-09-26
There are plenty of GPL libraries, that if some body used for developing an application would force that application to have a GPL compatible licence. That does not count as a restriction on who can use the software from the point of view of the debian/ubuntu guidelines. Plenty of companies work on and release GPL software (see [https://lwn.net/Articles/563977/](https://lwn.net/Articles/563977/) ).

Also even if you compiler forces the output application to be GPL, if the person using it does not distribute that compiled program, they do not have to distribute the source code to it.

---

