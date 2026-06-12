---
title: "Question regarding The Free Software Definition"
date: 2008-12-02
forum: The Cafe
---

### Post by DarKnyht on 2008-12-02
I am asking this because I am trying to better grasp the concepts of copyleft and copyright.  I have been researching on both sides and came across [this]("http://www.gnu.org/philosophy/free-sw.html") today

> One important way to modify a program is by merging in available free subroutines and modules. If the program's license says that you cannot merge in an existing module, such as if it requires you to be the copyright holder of any code you add, then the license is too restrictive to qualify as free. 

My question is this, "How is it that GPL is considered free if it doesn't allow other free licenses to make use of code licensed under it without modifying the license?" 

Another way I've seen this put is, "Why is it that GPL gets everything without returning to others (BSD, free to use, non-protected)?"

---

### Post by ssam on 2008-12-02
it depends if you think its an important freedom to give up your freedom.

someone can take a piece of BSD code, and use it to make proprietary software. so you are free to remove the freeness.

GPL code cannot be redistributed with out the original freedoms.

You can argue that either of these is freer than the other.

I prefer GPL style, because it means the original project can always use new features added to a fork. I think this helps linux. Many companies are using linux, and they have to give their changes back so that everyone benefits from them.

(you should also note that if you are not going to redistribute the result you can merge GPL code with anything you have permission to. eg you can make your own Linux/BSD/solaris hybrid and run it your computer)

---

### Post by az on 2008-12-02
> **DarKnyht said:**
> I am asking this because I am trying to better grasp the concepts of copyleft and copyright.  I have been researching on both sides and came across [this]("http://www.gnu.org/philosophy/free-sw.html") today



My question is this, "How is it that GPL is considered free if it doesn't allow other free licenses to make use of code licensed under it without modifying the license?" 

Another way I've seen this put is, "Why is it that GPL gets everything without returning to others (BSD, free to use, non-protected)?"

The GPL has to impose restrictions to protect freedoms.  There's no other way to do it.  For example, a BSD license doesn't protect against someone else taking away your freedoms.  Someone can take a piece of BSD-licensed code and turn it into a non-free software project.  

If you are the author of a software project and want the software to be free forever and ever, you can't guarantee that by licensing it under a BSD license.  That's why the GPL is paradoxically more free.

---

### Post by saulgoode on 2008-12-02
> **DarKnyht said:**
> My question is this, "How is it that GPL is considered free if it doesn't allow other free licenses to make use of code licensed under it without modifying the license?"
Firstly, you are indeed allowed to make use of GPL code with code under other licenses; however, you may not distribute the result except under the GPL. If you are not *distributing* the result, you may do whatever you like with the GPL code. That is the point of the GPL, to protect the freedom of the user to use the software.

To the Free Software Foundation, "users" come first; not developers, not distributors, not corporations. The GPL is designed so that the users' freedom to use the software will not be abrogated. Therefore it is important that those freedoms pass from one user to the next whenever the software is passed from one user to the next. To ensure that the freedom is passed on with the software, it is necessary to make that a condition of the transfer.

---

### Post by linuxguymarshall on 2008-12-02
I think the ability to take open source code and using it in proprietary software is what makes FOSS so great. That is why I usually release my code under the MIT License.

---

### Post by DarKnyht on 2008-12-02
But to me, the GPL doesn't seem to really protect the four freedoms of everyone.  It forces the original programmer's view of the four freedoms onto everyone that follows.  It's sort of like saying here is something free (as in freedom), BUT you cannot do what you want with it.

This just seems almost as wrong as the other extreme.

Now granted, I don't think the current protection structure of patents and copyright properly cover software in the first place.  A code copyright to me seems as absurd as trying to copyright 2+2=4.  I think the presentation (design and style) of the solution should be protected as there is an art-form to that, but the raw logic of programming shouldn't be.

---

### Post by Luke has no name on 2008-12-03
GPL doesn't protect the users' freedom, it protects the software's freedom. The user isn't free to do whatever they want, they have to keep any modifications open source.

As opposed to BSD, where people are free to do what they wish with it. 

It is a matter of opinion as to which is better. While I think the goals of the GPL are lofty, I believe allowing code to be used for proprietary applications is not an evil thing. 

LGPL is a nice medium. If I recall correctly, LGPL allows devs to make "dynamically linked" additions to the software that are proprietary.

---

### Post by earthpigg on 2008-12-03
> **ssam said:**
> 
(you should also note that if you are not going to redistribute the result you can merge GPL code with anything you have permission to. eg you can make your own Linux/BSD/solaris hybrid and run it your computer)

can i distribute it **internally **to my organization?

edit: and what if my organization is huge? and can i give my employees a copy to put on their home computers so they can work from home?

---

### Post by Ripfox on 2008-12-03
> **earthpigg said:**
> can i distribute it **internally **to my organization?

edit: and what if my organization is huge? and can i give my employees a copy to put on their home computers so they can work from home?

That is one hell of a good question. I have pondered this myself.

---

### Post by saulgoode on 2008-12-03
> **DarKnyht said:**
> But to me, the GPL doesn't seem to really protect the four freedoms of everyone.
Which of [the four]("http://www.gnu.org/philosophy/free-sw.html") does it fail to protect? (Here I suspect your intent is to comment on the GPL not offering certain *other* freedoms.)


> **DarKnyht said:**
> It forces the original programmer's view of the four freedoms onto everyone that follows.
The Free Software viewpoint is only "forced" upon those who choose to distribute GPLed software either commercially or as a modified version. You can choose not distribute it at all; give it away unmodified for no commercial benefit, or distribute it along with access to source the code. 
Nonetheless, the choice is yours -- and even should you choose not to distribute the software, you are still free to use the software however you wish.

> **DarKnyht said:**
> It's sort of like saying here is something free (as in freedom), BUT you cannot do what you want with it.
To quote Charles Hodgson's Humpty Dumpty, "*When I use a word, it means exactly what I want it to mean. Nothing more. Nothing less.*" 

The definition of Free Software as given by the Free Software Foundation focuses on the users' freedoms. This is little different than "free elections" only being concerned with citizens of majority age; or the "free press" still being restricted from publishing state's secrets; or a "free iLife" being contingent upon a purchase of OSX. 

The GPL is Free Software because, despite conditions being placed upon distribution, there are no conditions or arrogations of the Four Freedoms (or even the 10 criteria of the Open Source Definition).

> **DarKnyht said:**
> This just seems almost as wrong as the other extreme.
You don't think that a user having the freedom to use the software however he wishes -- in addition to being permitted to give away as many unmodified versions as he wishes -- is a significant benefit?

---

### Post by phrostbyte on 2008-12-03
Think of freedom of speech and the first amendment. 

1) Congress shall make no law ..

The first amendment actually sets restrictions.

In a way, the GPL is the Bill of Rights but for software. It sets certain restrictions designed to protect certain freedoms.

---

### Post by saulgoode on 2008-12-03
> **earthpigg said:**
> can i distribute it **internally **to my organization?
[Here is what the FSF says about it.]("http://www.fsf.org/licensing/licenses/gpl-faq.html#GPLRequireSourcePostedPublic")

> **earthpigg said:**
> edit: and what if my organization is huge? and can i give my employees a copy to put on their home computers so they can work from home?
A couple years ago, it was estimated that Google had over 600,000 servers running a customized version of GNU/Linux. That number is quite possibly over a million today -- yet Google has not released (and is not required to) any source for the GPLed code they have (presumably) modified.

---

### Post by earthpigg on 2008-12-03
> **saulgoode said:**
> [Yes.]("http://www.fsf.org/licensing/licenses/gpl-faq.html#GPLRequireSourcePostedPublic")


A couple years ago, it was estimated that Google had over 600,000 servers running a customized version of GNU/Linux. That number is quite possibly over a million today -- yet Google has not released (and is not required to) any source for the GPLed code they have (presumably) modified.

thanks, saul... but my question was not about GPL'd stuff.

if i take code from GPL, solaris, something with the Microsoft Open Source license, mozilla, openBSD code, some code i wrote myself and decided to make proprietary, and maybe even some Darwin code... and mash all that together into something just for my organization with all sorts of incompatible lisences (but all of them let **me **use the code):

without violating the GPL v2

can i distribute internally to my organization with 30,000 employees?

can i distribute CDs to my employees to work from home, with or without releasing the source code to them?

---

### Post by saulgoode on 2008-12-03
Sorry, Earthpigg. We aren't permitted to [talk about such things]("http://ubuntuforums.org/showpost.php?p=5942298&postcount=46") here.

---

### Post by Sef on 2008-12-03
> The GPL has to impose restrictions to protect freedoms. There's no other way to do it. For example, a BSD license doesn't protect against someone else taking away your freedoms. Someone can take a piece of BSD-licensed code and turn it into a non-free software project. 


An example of this is Apple OSX.

---

### Post by az on 2008-12-03
> **DarKnyht said:**
> But to me, the GPL doesn't seem to really protect the four freedoms of everyone.  It forces the original programmer's view of the four freedoms onto everyone that follows.  It's sort of like saying here is something free (as in freedom), BUT you cannot do what you want with it.

This just seems almost as wrong as the other extreme.


I think another way of expressing what others have already said about the GPL is to say that the GPL is not as ideological as you would assume.  It's a practical license.  As the author of code, you are granted rights though copyright.  The GPL enables you to clearly define your rights.  The GPL enables you to share your code without giving up your rights.

It's your code and you are choosing to share it with others.  If you choose to distribute it under the GPL, it's because you want the users of the code to all enjoy equal use of it.  It should be your right to decide, right?

It's not as though the GPL prevents you from choosing to release your code under a BSD or Public Domain style license, either.  Unless you are reusing someone else's code who has already chosen to use the GPL.

---

### Post by DarKnyht on 2008-12-03
> **az said:**
> It's your code and you are choosing to share it with others.  If you choose to distribute it under the GPL, it's because you want the users of the code to all enjoy equal use of it.  It should be your right to decide, right?

It's not as though the GPL prevents you from choosing to release your code under a BSD or Public Domain style license, either.  Unless you are reusing someone else's code who has already chosen to use the GPL.

First of all, again thanks for the rationale discussion.  Second, I know I am walking into murky waters, so I hope that this discussion can stay this way.

At least how I am understanding the GPL working, this philosophy does not work in reverse and I think that is the issue I have with it.  If you take code from a non-restricted license (such as BSD, because that is really the only other license I more or less understand right now) and make changes and GPL them.   Do you not do what break the intent of the GPL by not returning the code in a way that a BSD user can use without being forced to accept your view of freedoms?

If you truly believed in freedom of the software, wouldn't you return the work back so the original creators can benefit?  I mean how is that any different than Apple taking the BSD code and turning it into OS X?  The only difference I see can is that they don't claim to want to make software free for all, while seemingly doing otherwise.

---

### Post by az on 2008-12-03
> **DarKnyht said:**
> At least how I am understanding the GPL working, this philosophy does not work in reverse and I think that is the issue I have with it.  

You believe that taking code that is licensed under a less restrictive license and re-releasing it under a more restrictive license is unethical.

From an ideological view, it may or may not be ethical.  From a more pragmatic point of view, there is no other way around it, because other people will take your code, your development community and your userbase and give back far less than if you used the GPL.

> **DarKnyht said:**
> 
If you take code from a non-restricted license (such as BSD, because that is really the only other license I more or less understand right now) and make changes and GPL them.

First off, no one is forcing you to GPL the code you wrote.  But you have the right to GPL it because the BSD license let's you do whatever you want.  If the BSD license prevented you from doing whatever you want, then it would be more or less the same as the GPL.

> **DarKnyht said:**
> 
Do you not do what break the intent of the GPL by not returning the code in a way that a BSD user can use without being forced to accept your view of freedoms?

The GPL does not try to please everyone - that would be too ideological.  The GPL defines software freedom (the four freedoms) and tries to protect them.  You have to define freedom before you try to protect it.  Just granting "total freedom" as does a BSD license does not prevent the software from becoming non-free.

If the upstream author wanted the software to always be free in the BSD sense, they have to live with the consequence that every single user who gets that software has to freedom to make it non-free and not share any code they contribute.

When a developer releases code under a BSD license, they don't care what happens to it.  At least, they didn't chose a license that can do anything about it (which in the real world is the same thing).

> **DarKnyht said:**
> 
If you truly believed in freedom of the software, wouldn't you return the work back so the original creators can benefit?  I mean how is that any different than Apple taking the BSD code and turning it into OS X?  

Because you cannot obtain OSX for free.  You cannot study and modify the code, nor can you pass along any changes you make to it.  Isn't that a huge difference?

---

### Post by DarKnyht on 2008-12-03
Perhaps my issue really should be described as a moral/philosophical one.  And I apologize for somewhat puzzling my thoughts as I go.  I will try one more time to find the correct way to put this into words.

As I see it, I am using BSD as the example of absolute freedom in code anyone can do whatever they want with it.  I guess I would be using GPL as the example of Copyleft because it seems as close to that as I can find that relates with BSD.  And because of Apple's work with BSD, they are the example of Copyright. 

In the case of Apple user BSD code:  They take the code, add to it, and close it up offering nothing back to the BSD user.  They sell their finalized product to all, including the original coder, but no one gets access to the code unless they become part of Apple.

In the case of someone using GPL License user (unfortunately, I don't know of a specific example):  They take the code, add to it, GPL their portion.  Then they proclaim that the software is free to all, including the original coder, but no one can make use of the code unless they become part of the GPL.

Now within my understanding of these three, it seems like both sides (copyleft and copyright) are really only looking out to protect and gain the benefit for themselves.  If you are not on their side, then you get left out.

Now don't get me wrong, I love the open drivers, formats, and everything else that has been provided.  I personally have no desire to switch back, it is just this seems like a contradiction to the philosophy most copyleft coders profess.

---

### Post by saulgoode on 2008-12-03
> **DarKnyht said:**
> In the case of Apple user BSD code:  They take the code, add to it, and close it up offering nothing back to the BSD user.  They sell their finalized product to all, including the original coder, but no one gets access to the code unless they become part of Apple.
From the standpoint of the software recipient (i.e., the "user"), there is no distinction between this "Free Software" and proprietary software. The user has no rights to examine, to modify, make personal copies, or distribute copies or derivations. In other words, what they have received is not Free Software.

> **DarKnyht said:**
> In the case of someone using GPL License user (unfortunately, I don't know of a specific example):  They take the code, add to it, GPL their portion.  Then they proclaim that the software is free to all, including the original coder, but no one can make use of the code unless they become part of the GPL.
In this scenario, the software recipient indeed has the freedom to examine, modify, and make personal copies -- even to distribute copies and derivations so long as they pass those freedoms on to *their* recipients. 

The "amount of freedom" the software inheres under the two approaches is dependent upon how you measure that freedom. While a user *directly* receiving BSD-licensed software has a bit more freedom than one receiving GPLed software, one receiving that BSD-licensed software after it has been appropriated is receiving significantly less.

---

### Post by DarKnyht on 2008-12-03
> **saulgoode said:**
> From the standpoint of the software recipient (i.e., the "user"), there is no distinction between this "Free Software" and proprietary software. The user has no rights to examine, to modify, make personal copies, or distribute copies or derivations. In other words, what they have received is not Free Software.

In this scenario, the software recipient indeed has the freedom to examine, modify, and make personal copies -- even to distribute copies and derivations so long as they pass those freedoms on to *their* recipients. 

The "amount of freedom" the software inheres under the two approaches is dependent upon how you measure that freedom. While a user *directly* receiving BSD-licensed software has a bit more freedom than one receiving GPLed software, one receiving that BSD-licensed software after it has been appropriated is receiving significantly less.

I am not arguing that fact but merely noticing this: 

Copyright coders use copyright to protect the interests of the group they belong to, in most cases a corporation or organization.  Only the members of their group fully get the true freedom from the work they do.  Which means to get true freedom you must join the group (even if you created the originating source).

Likewise, copyleft coders when put together are much like a corporation (or organization if you prefer), they exist to protect their own interests.  Only the people that have aligned themselves with the group get true freedom.  Which means to get those true freedom you must be willing to copyleft your work (even if it is the originating source)

In both cases if you don't belong to the group or won't align yourself with the group, you cannot have true freedom.  So in the end, copyleft and copyright seem to me to be the same thing just applied differently.

---

### Post by az on 2008-12-03
> **DarKnyht said:**
> Perhaps my issue really should be described as a moral/philosophical one.  And I apologize for somewhat puzzling my thoughts as I go.  I will try one more time to find the correct way to put this into words.
...

In the case of someone using GPL License user They take the code, add to it, GPL their portion.  Then they proclaim that the software is free to all, including the original coder, but no one can make use of the code unless they become part of the GPL.

What does "they become part of the GPL" mean?  If "they" want to use the added code in their project, they must comply with the license by which it was given to them.  If they don't want to do that, then they don't have to incorporate the code.  It's their choice.

You would think that there would be a heck of a lot of forking of projects because of this, but it's remarkable how rarely this happens.  To me, that's proof that this is not an issue that a lot of people have a problem with.

> **DarKnyht said:**
> 
Now within my understanding of these three, it seems like both sides (copyleft and copyright) are really only looking out to protect and gain the benefit for themselves.  If you are not on their side, then you get left out.


You're not comparing the same things.  You can't compare the proprietary developer's interest in closing the code with the F/Loss developer's interest in using the GPL.

---

### Post by DarKnyht on 2008-12-03
> **az said:**
> What does "they become part of the GPL" mean?  If "they" want to use the added code in their project, they must comply with the license by which it was given to them.  If they don't want to do that, then they don't have to incorporate the code.  It's their choice.

You would think that there would be a heck of a lot of forking of projects because of this, but it's remarkable how rarely this happens.  To me, that's proof that this is not an issue that a lot of people have a problem with.

But how many comply with the license simply because they see no other choice?  Look at what most musicians are willing to put up with just for the opportunity to make music.

> **az said:**
> You're not comparing the same things.  You can't compare the proprietary developer's interest in closing the code with the F/Loss developer's interest in using the GPL.

I think they are very comparable.  They are both the implementation of someone's philosophical beliefs in terms of software coding.  Group A believes in Copyright approach, Group B believes in Copyleft approach.  Each has built a wall using the law around their kingdoms to protect their interests.

---

### Post by saulgoode on 2008-12-03
> **DarKnyht said:**
> I am not arguing that fact but merely noticing this: [snip]
I would hope that my commentary is not perceived as overly argumentative. You have pointed out the parodoxical situation that copyleft/reciprocal licenses do not remove as many restrictions as permissive licenses (note that the GPL does not place ANY restrictions on software, any restrictions present are actuated by default in the terms of copyright law, and to varying degrees removed by reciprocal and university licensing). 

There is little to dispute about the existence of this paradox (and it was recognized 20 years ago in the GNU Manifesto). The main comment I would make is "so what?"; it is the nature of the beast. Reciprocal licensing advocates want their contributions to remain "free" to the end user and permissive licensing advocates want end users to be allowed to remove the "freeness" for their end users. These are not reconcilable alternatives. Pick the license you want for code you create.

Regarding your concern that reciprocal license advocates are taking permissively-licensed software and releasing it only under the GPL, I would ask whether this practice is commonplace. To my knowledge, the only instances have been merely temporary "mistakes", typically only occurring in a developer's personal "private" branch and never being merged back into the main trunk. 

As Az stated, it is somewhat unethical to place new restrictions upon permissively-licensed software, even if those restrictions only relate to the restriction not to restrict (:)). But in my opinion this rarely, if ever, occurs (perhaps you could provide some examples).

The source code of GPLed software MUST be provided and the license terms of BSD-licensed software MUST be included with the source code. Therefore it seems inconceivable to me that BSD-licensed code could ever be "re-licensed" as GPL-only (that is not to say that the GPL programmer has contributed back his improvements, but the BSD author never demanded that, and the GPL is not about programmers' rights).

> **DarKnyht said:**
> Likewise, copyleft coders when put together are much like a corporation (or organization if you prefer), they exist to protect their own interests. 
The distinction is that the "interest" of the copyleft coders is the freedom of the recipient of the software.

> **DarKnyht said:**
> In both cases if you don't belong to the group or won't align yourself with the group, you cannot have true freedom.  So in the end, copyleft and copyright seem to me to be the same thing just applied differently.
Maybe to the developer there is a similarity, but there is a significant distinction to the *end user*. A distinction of which every Ubuntu user should be aware.

---

### Post by az on 2008-12-03
> **DarKnyht said:**
> But how many comply with the license simply because they see no other choice?  

I don't know who you are describing.  If you are a hacker submitting a patch to a large project and you want your code to be GPLed, you can't expect the whole project to switch from a BSD license to the GPL just so that they can use your patch.  And likewise, a large GPLed project won't switch license nor accept a patch if it's under a GPL-incompatible license. 

Nobody is held hostage.  Everybody has a choice.  And if the license is not compatible, the code doesn't make it's way into the project.

> **DarKnyht said:**
> 
Look at what most musicians are willing to put up with just for the opportunity to make music.


Actually, I know many musicians that make plenty of music without having to put up with anything.  Some of them even distribute their music under CC licenses.  Like anything, it's when you want to make money from something that the headaches begin.


> **DarKnyht said:**
> 
I think they are very comparable.  They are both the implementation of someone's philosophical beliefs in terms of software coding.  

No.  It has nothing to do with coding.  It has nothing to do with programming.  It has to do with distributing the code.  In either case, you can code what you want.


> **DarKnyht said:**
> 
Each has built a wall using the law around their kingdoms to protect their interests.

That sounds like an argument made for the sake of making an argument and not for the sake of describing any actual problem.  Instead of phrases like that, can you give some real-world examples that illustrate the problem?

---

### Post by DarKnyht on 2008-12-03
> **az said:**
> That sounds like an argument made for the sake of making an argument and not for the sake of describing any actual problem.  Instead of phrases like that, can you give some real-world examples that illustrate the problem?

Well, one real world example that comes to mind (mainly because I remember the stink raise on the tech sites I read) is the Atheros wireless device drivers created mostly by OpenBSD.  In that particular situation, GPLv2 coders were wanting to relicense the driver as GPLv2, effectively cutting the creators access to what they added to it.  Now, that situation was clarified and corrected but that is a great example of what I am talking about.

To quote the OpenBSD project creator, Theo de Raadt:

> "GPL fans said the great problem we would face is that companies would take our BSD code, modify it, and not give back. Nope -- the great problem we face is that people would wrap the GPL around our code, and lock us out in the same way that these supposed companies would lock us out. Just like the Linux community, we have many companies giving us code back, all the time. But once the code is GPL'd, we cannot get it back.

"Ironic."

I am not saying that every GPL fan would do something like this, it is just that when this is an option eventually it will be abused by the extreme fringe.

Another way I would describe it is that the GPL is like roman citizenship: great for full citizens of the GPL (programmers that use/support the GPL), ok for those with access to Latin Right (users that use/support GPL software but will never code anything), but it sure can suck for everyone else.

---

### Post by phrostbyte on 2008-12-03
What I think you doing is using the word freedom too lightly and too subjectively. Freedom is a very abstract concept, and certain "freedoms" aren't always ideal. 

For one, I am not free to drive up to Nashville, TN and steal your computer. If I do so I am committing a crime and I can be punished for it. But look I lost a freedom, the freedom to steal your computer.

The same reason we have laws that make murder illegal. You are taking away people's freedom to murder other people. But we as a society think the right to murder is not a right at all, but the right to life should be protected.

Basically what I am trying to get at is the GPL is a set of restrictions who purpose is to protect certain freedoms, like the right to modify or distribute software. BSD is less effective at protecting this rights, just like if you have a government who makes murder legal, it will be less effective at protecting certain freedoms like the freedom to exist.

---

### Post by cardinals_fan on 2008-12-03
My 2 cents:

The ideal license, to me, is the licensing used by Trolltech for Qt ([http://trolltech.com/products/appdev/licensing](http://trolltech.com/products/appdev/licensing)).  If you want to use the code for free, you have to make your changes open source as well (GPL).  If you want to code a proprietary app, you have to pay.

EDIT: My primary issue with the GPL is not its lack of true freedom.  I just think it's too long.  They've added pages and pages of legalese to prevent the tiniest little transgressions.  I don't think any license should be too long to print on one 8.5 x 11 inch piece of paper in size 12 Courier font.

---

### Post by DarKnyht on 2008-12-03
> **saulgoode said:**
> I would hope that my commentary is not perceived as overly argumentative. You have pointed out the parodoxical situation that copyleft/reciprocal licenses do not remove as many restrictions as permissive licenses (note that the GPL does not place ANY restrictions on software, any restrictions present are actuated by default in the terms of copyright law, and to varying degrees removed by reciprocal and university licensing). 

There is little to dispute about the existence of this paradox (and it was recognized 20 years ago in the GNU Manifesto). The main comment I would make is "so what?"; it is the nature of the beast. Reciprocal licensing advocates want their contributions to remain "free" to the end user and permissive licensing advocates want end users to be allowed to remove the "freeness" for their end users. These are not reconcilable alternatives. Pick the license you want for code you create.

Regarding your concern that reciprocal license advocates are taking permissively-licensed software and releasing it only under the GPL, I would ask whether this practice is commonplace. To my knowledge, the only instances have been merely temporary "mistakes", typically only occurring in a developer's personal "private" branch and never being merged back into the main trunk. 

As Az stated, it is somewhat unethical to place new restrictions upon permissively-licensed software, even if those restrictions only relate to the restriction not to restrict (:)). But in my opinion this rarely, if ever, occurs (perhaps you could provide some examples).

The source code of GPLed software MUST be provided and the license terms of BSD-licensed software MUST be included with the source code. Therefore it seems inconceivable to me that BSD-licensed code could ever be "re-licensed" as GPL-only (that is not to say that the GPL programmer has contributed back his improvements, but the BSD author never demanded that, and the GPL is not about programmers' rights).

The distinction is that the "interest" of the copyleft coders is the freedom of the recipient of the software.

Maybe to the developer there is a similarity, but there is a significant distinction to the *end user*. A distinction of which every Ubuntu user should be aware.

No it is not argumentative, it is just I think we are getting two different discussions in the same thread.  But that is because my thoughts are progressing as I read more on the issue here and elsewhere.  Everything that has been said this far has been insightful/thought provoking and not at all offensive to me.  I have gained a much better understanding of GPL (and even BSD license) from this, not to mention the laws surrounding it.

Besides, it would be silly of me to get mad when I get a reply with a difference of opinion when that is what I more or less asked for.

Lets just say that this is something of my own eyes being opened up to the paradox that you point out everyone has been aware of for 20 years.  I see the potential for this paradox to be abused in an unethical way.  I also worry when something moves too far to one particular extreme.  I am see the potential of using things such as the mess with the Atheros driver and Tivoization as testings of what the fringe can force upon the masses.

---

### Post by DarKnyht on 2008-12-03
> **phrostbyte said:**
> What I think you doing is using the word freedom too lightly and too subjectively. Freedom is a very abstract concept, and certain "freedoms" aren't always ideal. 

For one, I am not free to drive up to Nashville, TN and steal your computer. If I do so I am committing a crime and I can be punished for it. But look I lost a freedom, the freedom to steal your computer.

The same reason we have laws that make murder illegal. You are taking away people's freedom to murder other people. But we as a society think the right to murder is not a right at all, but the right to life should be protected.

Basically what I am trying to get at is the GPL is a set of restrictions who purpose is to protect certain freedoms, like the right to modify or distribute software. BSD is less effective at protecting this rights, just like if you have a government who makes murder legal, it will be less effective at protecting certain freedoms like the freedom to exist.

I think I am holding the same definition of freedom throughout.  As in complete freedom equally provided for all.  I apologize if I haven't.

---

### Post by saulgoode on 2008-12-04
> **DarKnyht said:**
> Well, one real world example that comes to mind (mainly because I remember the stink raise on the tech sites I read) is the Atheros wireless device drivers created mostly by OpenBSD.  In that particular situation, GPLv2 coders were wanting to relicense the driver as GPLv2, effectively cutting the creators access to what they added to it.  Now, that situation was clarified and corrected but that is a great example of what I am talking about. 
Yes, the drivers were created mostly by OpenBSD developers, but it was offered under *both* the BSD and the GPL licenses. The Linux coder was not "relicensing"; he was using the version that was GPLed by the original developers. There were mistakes made in the patch submitted to the Linux devs -- but the patch was rejected. If I recall correctly, the changes eventually made in the Linux drivers were made available under both the GPL and BSD licenses. 

> **DarKnyht said:**
> To quote the OpenBSD project creator, Theo de Raadt:
> "GPL fans said the great problem we would face is that companies would take our BSD code, modify it, and not give back. Nope -- the great problem we face is that people would wrap the GPL around our code, and lock us out in the same way that these supposed companies would lock us out. Just like the Linux community, we have many companies giving us code back, all the time. But once the code is GPL'd, we cannot get it back.

"Ironic."
Aside from the fact that what Mr de Raadt describes as "our BSD code" was already available under GPL terms (i.e., there was no "wrapping" of the GPL around it), even were his accusations accurate there would be an equal irony in his criticism saying in effect "our license is better because you aren't obligated to contribute back -- of course if you don't contribute back then we will call you hypocrites". 

> **DarKnyht said:**
> I am not saying that every GPL fan would do something like this, ...
I remain unconvinced that this has *ever* happened, which is a testament to the level of respect that developers in both camps have for contributions being made to Free Software. 

> **DarKnyht said:**
> ... it is just that when this is an option eventually it will be abused by the extreme fringe.
Why do you consider it an "abuse"? Isn't the intent of BSD licensing that recipients can use the code in a manner by which they make a profit? Why would it be considered so evil that a GPL coder make his "profit" (i.e., further improvements to the code by others as opposed to monetary gain)?

Such "relicensing" should only be considered an "abuse" by the GPL camp. It seems to me hypocritical that fans of BSD licensing would consider behavior "abusive" when that behavior is specifically permitted (and is the most significant distinction with the GPL). If you consider relicensing to be abusive, shouldn't you be using a license which expresses that (and removes that opprobrious option)?

> **DarKnyht said:**
> I think I am holding the same definition of freedom throughout.  As in complete freedom equally provided for all.
This is impossible. "Complete freedom" obtains the freedom to deny another's freedom, ergo it is not equally provided.

---

### Post by Buffalo Soldier on 2008-12-04
DarKnyht,

I'm sorry, I don't mean to put words into your mouth... but I just want to clarify this. It seems to me (my personal opinion) that in your mind:

[list=1]
[*] freedom == "all access/free to do anything/no rules".
[*] any rules or laws that safeguard freedom is in itself against the spirit of freedom
[/list]

I think if that is the case, than what you're referring to as "Freedom" is actually "Anarchy".

---

### Post by az on 2008-12-04
> **DarKnyht said:**
> effectively cutting the creators access to what they added to it.  

Yes, because the additions were added by people who want to guarantee that their code remains free.  That's hardly claiming something for their Kingdom.  That's being fair.  

If the authors of BSD-licensed don't have a problem with people taking their code and not giving anything back at all, why do they have a problem with people taking, but giving back code under a different license?

Again, nobody is forcing them to use the GPLed patches.  They chose to use a BSD license.  The consequence of that is that your users will take your code and use it in any way they please.  If you don't want your users to do that with your code, pick a different license.  I don't get what the issue is here.

---

