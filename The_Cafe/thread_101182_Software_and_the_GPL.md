---
title: "Software and the GPL"
date: 2005-12-09
forum: The Cafe
---

### Post by lerrup on 2005-12-09
This is not a very detailed introduction into the question of copyrights and licences. I could go on as licences were the reason I became interested in Linux in the first place. I do not claim to be an expert in this and so clarifications and corrections are welcome. 

When you create something it is normal to wish to control your creation in some way. For books, pictures and similar matters the idea of copyright was invented to enable creators a way of controlling their creations. These grew up in various jurisdictions and became an established area of law. When computer programs began to be written there was a perceived need for creators again to be able to control their creations. Written source code was covered by copyright as a literary work and so copyright became that way. 

Therefore, if you are the initial developer of a program you will own the copyright in it unless there are other factors that affect the ownership of the work.   This may be that you have assigned them or that you created it for an employer and so the rights have been assigned to the employer by law there is an agreement to assign rights or some other analogous position. 

As most users will be aware as users you do not, as a rule, have any rights assigned to you apart from those contained in the licence used by the copyright holder and what minimal rights that may be granted by statute. For most proprietary software these are very restricted and amount to installing and running the application; they usually expressly forbid distribution or amending. 

The Gnu Public Licence (GPL) is different. It is a licence that grants those rights to users of the application provided that they observe the conditions of the GPL. These are straightforward and in particular apply should the code be redistributed in any form. They include the obligation that the distributor must acknowledge the work of all copyright holders in the work, distribute the source code along with the binaries, the lack of any warranty must be acknowledged and most importantly that the new work shall be covered by the GPL. 

These conditions apply whenever GPL covered code is distributed, adapted or used as part of another application or program. This would be considered to be a derivative application; this does not necessarily mean that there is any moral judgement on the status of the application. Rather, it means that it just uses the code of the previous application, it is built on it or the old code is integrated into the new application. 

The GPL goes into more detail about this and should be read when there is a question of whether an application is or isn't a derivative work from a GPL covered app. 

If you wish to keep control of your work and not have anyone else change it without your express permission you can not do so if it is a derivative of a GPLed application within the terms of the GPL. You need to either negotiate a separate licence to use the code for that application or you need to write an application from scratch. You can, however, use the idea or concept of another application; if you couldn't there wouldn't be more than one word processor in the world. The protection of inventions in this way are covered by patents, which I don't think are a good idea for software and are beyond the scope of this piece. 

In relation to the development of free software, the GPL is in my opinion a key paradigm shift that has enabled this to happen. It is the licence that has allowed GNU applications and the Linux kernel to develop to where they are now. Without it, or a similar licence there would be much less reuse of code and work.  This work and code would therefore end up in numerous bunkers with thousands of hours of duplicate work and no Linux.

Therefore to sum up the licence position of a piece of code that you might write: 

1 If it is a derivative work, check the licence that the original was based on and ensure you meet its conditions. 

2 It is a new work then you should ensure you distribute under a licence that meets your requirements. 

If it is a work for Ubuntu I would urge you to consider the GPL as without it you wouldn't have been able to write an app for Ubuntu in the first place. It wouldn't exist.

---

### Post by LordHunter317 on 2005-12-09
> **lerrup]When computer programs began to be written there was a perceived need for creators again to be able to control their creations.[/quote]There was never a need.  Source code is text, so it was protected under copyright from the beginning.

> Therefore, if you are the initial developer of a program you will own the copyright in it unless you assign them said:**
> In most jursidictions on Earth, a "works for hire" clause exists which essentially means that merely being hired by someone is enough for you to forefit your copyright, unless you specifically preserve it via contract or some other mechanism.


[quote] They include the obligation that the distributor must acknowledge the work of all copyright holders in the work, freely distribute the source code must be,Nope.  The person doing the distribution only has to provide source code to whoever he gives binaries too.  If he doesn't feel like giving someone the code, he doesn't have to at all.

This is an important thing to note as many people really the GPL gives everyone access to the source code.  It doesn't.  However, it does have a "cat out of the bag" phenonema in that if I refuse person B the code but give it to person C, I cannot prevent person C from giving it to person B. 

[quote]If you wish to keep control of your work and not have anyone else change it without your express permission you can not do so if it is based on a GPLed application.Not true, see the existing works clause.

> Ideas are covered by patents,Nope, you can't patent an idea, just an invention.  However, the patent office seems to belive that ideas are inventions as of late, which is disappointing.

> In relation to the development of free software, the GPL is in my opinion a key paradigm shift that has enabled this to happen.  It is the licence that has allowed GNU applications and the Linux kernel to develop to where they are now.Hardly: the license really can be attributed anything and in the kernel, it's been a setback in several ways several times.

> Without it there would be no reuse of code and work and so it would end up in numerous bunkers with thousands of hours of duplicate work and no Linux.False.  There are other projects under other licenses that are as old or older than the GNU project that have had just as much contribution.

---

### Post by endersshadow on 2005-12-09
Yeah, under US, and to the best extent of my knowledge, international law, once you write code, it is automatically copyrighted.  It is intellectual material, and therefore cannot be patented, as patents are for inventions, copyrights are for ideas, as Lord stated.  If you released software without filing in the copyright office, you would still have a copyright on that material.  The GPL actually lessens the original author's copyright on his/her software by allowing anybody to edit it and redistribute it either under the same name or under a different name.  The GPL is much less restrictive than an unregistered copyright.

[http://creativecommons.org/licenses/GPL/2.0/](http://creativecommons.org/licenses/GPL/2.0/)

That's a good summary of what the GPL allows you to do and what you must do in order to comply with it.

---

### Post by LordHunter317 on 2005-12-09
[QUOTE=endersshadow] copyrights are for ideas, as Lord stated.[/quote]Nope.  Copyrights are for (artistic) works.  I can't take copyright on the idea of a book about a young boy wizard in England who's the savior of all man, just merely the words I used to describe it...

---

### Post by matthewstory on 2005-12-09
IDK the GPL is actually a pretty restrictive liscence, in that it is a viral liscence.  Everything it touches must also be GPL.  I prefer the LGPL:

[http://www.gnu.org/copyleft/lesser.html](http://www.gnu.org/copyleft/lesser.html)

though richard stallman does not:

[http://www.gnu.org/philosophy/why-not-lgpl.html](http://www.gnu.org/philosophy/why-not-lgpl.html)

For pretty much the exact same reasons i prefer it, he hates it.

regards,
matt

---

### Post by endersshadow on 2005-12-09
[QUOTE=LordHunter317]Nope.  Copyrights are for (artistic) works.  I can't take copyright on the idea of a book about a young boy wizard in England who's the savior of all man, just merely the words I used to describe it...[/QUOTE]

Yeah, I realize that, sorry for the semantics.

---

### Post by LordHunter317 on 2005-12-09
It's ok, but unfortunately with these things, the distinction between idea, copyrightable works, and patenable works (works in the most generic sense) must be made clear, as there's already plenty of confusion and misunderstanding, especially when the GPL is involved.

---

### Post by gil-galad on 2005-12-09
[QUOTE=matthewstory]
For pretty much the exact same reasons i prefer it, he hates it.

regards,
matt[/QUOTE]

Richard Stallman does not *hate* the lgpl, he created it and uses it himself .  It is very usefull for things like the C library and GTK.  Libraries that closed-source programs can, and should be able to, use without giving away source.

---

### Post by lerrup on 2005-12-16
A tip for you, don't start writing things like this when you should be doing something else like moving house...

Thanks for the clarification of my text - I hope that I have managed to make what I meant more easily understood.

I do disagree with some of Lordhunter's statements about the effect of the GPL.  That it is the licence of choice for both the Kernel and for most free software projects show that it is something special.  I believe that in a recent survey that 8 out of 10 coders said that their cats prefer it so that must show something...

---

### Post by asimon on 2005-12-16
[QUOTE=gil-galad]Richard Stallman does not *hate* the lgpl, he created it and uses it himself .[/QUOTE]
Mr. Stallman released something under LGPL? Didn't he even wrote an article "Why you shouldn't use the Library GPL for your next library"? I always thought he is pretty hardcore GPL when it comes to his own code.

---

### Post by LordHunter317 on 2005-12-16
[QUOTE=lerrup]AI do disagree with some of Lordhunter's statements about the effect of the GPL.[/quote]How so?  It's been a clear holdback in the adoption of binary modules and in letting more code into the kernel.

> That it is the licence of choice for both the Kernel and for most free software projects show that it is something special.Or that people pick licenses without thinking about the ramifications of them.

[quote=gil-galad]Richard Stallman does not hate the lgpl, he created it and uses it himself [/quote]No, he does.  The FSF created it out of mere realistic necessity, there's even a paper on their FAQ page saying why you shouldn't use the LGPL for your next library.

---

### Post by asimon on 2005-12-16
[QUOTE=LordHunter317]How so?  It's been a clear holdback in the adoption of binary modules and in letting more code into the kernel.[/QUOTE]
Well, there are people who think that binary only modules are a bad idea and don't want them at all. Thus for some people that is and advantage. ;-)

---

