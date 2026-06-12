---
title: "Is this possible under GPL?"
date: 2012-08-30
forum: The Cafe
---

### Post by expelledboy on 2012-08-30
Hey,

I thought I understood the GNU General Public License (GPL), without actually having read it.

From my understanding if I designed a server that ran nothing but configured open-source pacakages I would not have the right to keep those configurations private and pre-package it as a distro for sale. Not to mention doing so and then not acknowledging the projects I have made use of through out the solution.  

How then do [_these guys_]("http://www.2x.com/thinclientserver/") get away with it? Originally located on [_sourceforge_]("https://sourceforge.net/projects/pxes/") they now make a bundle selling on pxe servers that serve linux systems with pre-loaded remote desktop applications.

For that matter how does apple get away with it?

Why isnt any of their profit, founded on the work of open source developers, spilling back into the community?

---

### Post by Primefalcon on 2012-08-30
Apple is based on FreeBSD Unix which is under the BSD license... not the GPL

[http://en.wikipedia.org/wiki/BSD_licenses](http://en.wikipedia.org/wiki/BSD_licenses)

And your also allowed to have your own proprietary software running on top of Linux.... otherwise how would companies release things like valve to Linux? or the numerous closed source wireless drivers that are in Ubuntu or most other big distro's

---

### Post by Bachstelze on 2012-08-30
> **expelledboy said:**
> 
I thought I understood the GNU General Public License (GPL), without actually having read it.

Eh eh....

> From my understanding if I designed a server that ran nothing but configured open-source pacakages I would not have the right to keep those configurations private and pre-package it as a distro for sale. Not to mention doing so and then not acknowledging the projects I have made use of through out the solution.

You would have to elaborate on that, because it's not very clear... The bottom-line is that it is perfectly OK to sell GPL software, but when someone buys it then 1) you are required to provide them the source code, and 2) they are allowed to redistribute it for free (as long as they comply with the GPL as well).

> For that matter how does apple get away with it?

Apple provides the source code of all the free software they distribute (even when they are not required to do so). See [http://www.apple.com/opensource/](http://www.apple.com/opensource/)

> Why isnt any of their profit, founded on the work of open source developers, spilling back into the community?

Because free sotware is about freedom, not money.

> **Primefalcon said:**
> **Mac OS X** is based on FreeBSD [s]Unix[/s], which is under the BSD license... not the GPL

Fixed that for you. Also, OS X includes a lot of GPL software as well. (And so does FreeBSD, for that matter.)

---

### Post by evilsoup on 2012-08-30
The GPL is about free-as-in-speech, not free-as-in-beer. As I understand it, you're allowed to sell any GPL software, you just have to make sure whoever you're selling it to has access to the source code, and the ability to alter it if they really want to.

---

### Post by expelledboy on 2012-08-30
I never said you werent allowed to have your own proprietary software running on top of Linux, I said I dont get how some develop solutions using open source tools, and then making it proprietary.

I was not aware that FreeBSD had a different licence. Regarless, haven't there been numerous GPL'ed projects ported to BSD?

---

### Post by expelledboy on 2012-08-30
@evilsoup I see. Beautiful way of saying it. I understand now.

So, with regards to the particular project I pointed out?

---

### Post by Bachstelze on 2012-08-30
> **expelledboy said:**
> I never said you werent allowed to have your own proprietary software running on top of Linux, I said I dont get how some develop solutions using open source tools, and then making it proprietary.

1) You can't take GPL code and make it proprietary.
2) Selling a software and making it proprietary are not the same thing.

> I was not aware that FreeBSD had a different licence. Regarless, haven't there been numerous GPL'ed projects ported to BSD?

What do you mean by "ported"? Also, what do you mean by "BSD", for that matter?

---

### Post by evilsoup on 2012-08-30
I don't know, I'm really not an expert. As far as I know, so long as they give the source code of the GPL'd bits to their customers & make clear any changes they've made from publicly-available versions, they're fine.

But I'm really not an expert, I could be wrong. If you want to know more, try looking [here]("http://www.gnu.org/copyleft/gpl.html")

---

### Post by expelledboy on 2012-08-30
> 1) You can't take GPL code and make it proprietary.
2) Selling a software and making it proprietary are not the same thing.

1 - My limited understanding of the GPL licence before evilsoup's response.
2 - What I have learned since.


> What do you mean by "ported"? Also, what do you mean by "BSD", for that matter?
s/BSD/FreeBSD/

Again I dont know much about FreeBSD, or apple and its practices, for that matter. I was just curious.

Ported in its general sense means adapting software to run in a different environment from which it was originally designed. Although I was not aware FreeBSD used a licence other than GPL, I assume that if you develop a solution on top of FreeBSD any project within its repos are otherwise made available under the BSD license?

---

### Post by Primefalcon on 2012-08-30
> **expelledboy said:**
> I assume that if you develop a solution on top of FreeBSD any project within its repos are otherwise made available under the BSD license?
you don't have to no... freeBSD is a lot more commercial friendly than the GPL, companies can take it and close source what they do with it.. without any issues, they don't even have to give credit I don't think

---

### Post by Bachstelze on 2012-08-30
> **expelledboy said:**
> 
Ported in its general sense means adapting software to run in a different environment from which it was originally designed.

I know that. ;) Your mistake is that you seem to think the software that you use on Linux has been designed for Linux. In the vast majority of cases, this is not true, the software has been designed to run on any POSIX-compliant OS. Linux is one such OS, FreeBSD is another. In most cases, no porting is necessary, you just download the source and compile it on FreeBSD and it will run, just in the same way it does on Linux.

> Although I was not aware FreeBSD used a licence other than GPL, I assume that if you develop a solution on top of FreeBSD any project within its repos are otherwise made available under the BSD license?

I'm not following you here. What do you mean by "its repos"?

---

### Post by vexorian on 2012-08-30
You can actually take GPL and "make" it proprietary. You just can't redistribute it.

It is actually a requirement of a license to be called a free software or open source licensed. It should allow commercial use.

However, if you try to, say, sell the GIMP, you would have to include GIMP's source code when you sell it. And also, there is nothing stopping the people that bought your GIMP copies to start giving it away for free. or from people taking the additions you put in GIMP and also giving them away for free. So it is not a big business opportunity. 

What it allows in practice, is for the GIMP to be bundled with commercial packages of software without much issue. If the package of software needs it for some reason. And also, you could offer paid support for GIMP users. With Linux, this is how Red Hat's whole business work, selling support.

The BSD license is not friendlier to commercial software than the GPL. It is friendlier to proprietary forks. So-called "Permissive" licenses are the reason, Cedega happened for example. It seems that the only thing "permissive" licenses permit that copyleft licenses don't are things that are detrimental to us users . That's why I prefer copyleft on core projects.

But FreeBSD comes with a lot of GPLed software and Linux comes with a lot of software with BSD license. No free software license restricts you on the kind of software you can bundle something with. The GPL can restrict you on the sort of code you inject into a GPLed project though.

---

### Post by expelledboy on 2012-08-30
@Bachstelze I guess ported is the wrong word. My point is exactly that doesnt take much to migrate a GPL'ed project onto a FreeBSD system. Does this give companies like apple the right to use such projects, and otherwise circumvent the licence?

---

### Post by Bachstelze on 2012-08-30
> **expelledboy said:**
> @Bachstelze I guess ported is the wrong word. My point is exactly that doesnt take much to migrate a GPL'ed project onto a FreeBSD system. Does this give companies like apple the right to use such projects, and otherwise circumvent the licence?

They do not circumvent the licence. What makes you think they do?

---

### Post by snip3r8 on 2012-08-30
The GPL is a funny thing, it stands for freedom but **forces** you to contribute by submitting changes back to the community. To me ,anything that forces you to do something is not freedom. Its almost like a "this statement is false" scenario. The MIT Licence is true freedom , and I commit changes without being forced.

---

### Post by expelledboy on 2012-08-30
So my question now, a step toward my understanding...

As taken from the GPL licence;
> For example, if you distribute copies of such a program, whether gratis or for a fee, you must pass on to the recipients the same freedoms that you received. You must make sure that they, too, receive or can get the source code. And you must show them these terms so they know their rights.

Do [_these guys_]("http://www.2x.com/thinclientserver/") meet the requirements?

---

### Post by Bachstelze on 2012-08-30
> **snip3r8 said:**
> The GPL is a funny thing, it stands for freedom but **forces** you to contribute by submitting changes back to the community. To me ,anything that forces you to do something is not freedom. Its almost like a "this statement is false" scenario. The MIT Licence is true freedom , and I commit changes without being forced.

The MIT license also forces you to do something (namely, copy the text of the license in your documentation). ;) You want the WTFPL.

---

### Post by expelledboy on 2012-08-30
> **Bachstelze said:**
> They do not circumvent the licence. What makes you think they do?

If apple havent circumvented the licence then how is it that there isnt an OpenOSX? Like there is a chromium to chrome.

---

### Post by mips on 2012-08-30
> **Primefalcon said:**
> ...they don't even have to give credit I don't think

That's actually one of the few things they have to do. They have to display the copyright notice, year & holders name.
[http://en.wikipedia.org/wiki/BSD_licenses](http://en.wikipedia.org/wiki/BSD_licenses)

---

### Post by Bachstelze on 2012-08-30
> **expelledboy said:**
> If apple havent circumvented the licence then how is it that there isnt an OpenOSX? Like there is a chromium to chrome.

Because OS X contains a lot of proprietary code. The crucial difference is that the proprietary parts are entirely Apple's work, and thus they are not covered by the GPL.

---

### Post by expelledboy on 2012-08-30
Okay I think I'm starting to get this.

So, if I design a server that uses an open-source pxe service, that serves an open-source linux distro, that has an open-source remote desktop application, given that I have done nothing but configure these various elements to work together, customizing and optimizing where appropriate, and garnishing it with my logos, I can sell the solution.

But, I would have to publish is under the same licence, and provide all GPLed source code, including that which I have modified, making anyone who would purchase this solution aware of their rights granted by such a licencing model.

If I have missed anything please amend.

Given that idea I still dont like the whole [www.2x.com](www.2x.com) thing.

---

### Post by snip3r8 on 2012-08-30
The proprietary parts Apple keeps to themselves , the open source parts of the OS are available [here]("http://opensource.apple.com/"). Remember an OS is not just one program , it is a system. You can still sell it even though it has Open Source parts because it has proprietary parts too.

---

### Post by Bachstelze on 2012-08-30
> **snip3r8 said:**
> You can still sell it even though it has Open Source parts because it has proprietary parts too.

You can sell it even if it has only open source parts... Canonical sells Ubuntu CDs for example.

---

### Post by Primefalcon on 2012-08-30
As I stated before FreeBSD is not under nor subject to the GPL, its under the BSD license and which means pretty much they can do whatever they want

---

### Post by Bachstelze on 2012-08-30
> **Primefalcon said:**
> As I stated before FreeBSD is not under nor subject to the GPL, its under the BSD license and which means pretty much they can do whatever they want

As I stated before, you are wrong. FreeBSD is a large collection of software, not all of which is under the BSD license. There is GPL software in FreeBSD (and in OS X as well).

---

### Post by Primefalcon on 2012-08-30
> **Bachstelze said:**
> As I stated before, you are wrong. FreeBSD is a large collection of software, not all of which is under the BSD license. There is GPL software in FreeBSD (and in OS X as well).
I am sure there is, but FreeBSD itself is under the BSD licence 

> License: 	FreeBSD License, FreeBSD Documentation License
wich dictates that

> Proprietary software licenses compatibility

The BSD License allows proprietary use, and for the software released under the license to be incorporated into proprietary products. Works based on the material may be released under a proprietary license or as closed source software.

It is possible for something to be distributed with the BSD License and some other license to apply as well.

Yes the software that is GPL'ed would have to apply but freebsd itself and all other BSD'ed software is not subject to the GPL

---

### Post by Bachstelze on 2012-08-30
> **Primefalcon said:**
> I am sure there is, but FreeBSD itself is under the BSD licence

Oh, and what do you mean by "FreeBSD itself"?

---

### Post by Primefalcon on 2012-08-30
> **Bachstelze said:**
> Oh, and what do you mean by "FreeBSD itself"?
From their own wiki page.....

> This covers both the works of the FreeBSD development team and the (original) works of The Regents of the University of California.

---

### Post by Bachstelze on 2012-08-30
But FreeBSD contains a lot of software which **is not the work of the FreeBSD development team**. Absolutely no project of that size contains the work of only one team, not even Windows.

---

### Post by KiwiNZ on 2012-08-30
> **Primefalcon said:**
> Apple is based on FreeBSD Unix which is under the BSD license... not the GPL

[http://en.wikipedia.org/wiki/BSD_licenses](http://en.wikipedia.org/wiki/BSD_licenses)

And your also allowed to have your own proprietary software running on top of Linux.... otherwise how would companies release things like valve to Linux? or the numerous closed source wireless drivers that are in Ubuntu or most other big distro's

OSX is based on the March Kernel, bits and pieces of FreeBSD,NetBSD/Unix and of course Nextstep.

---

### Post by Primefalcon on 2012-08-30
> **Bachstelze said:**
> But FreeBSD contains a lot of software which **is not the work of the FreeBSD development team**. Absolutely no project of that size contains the work of only one team, not even Windows.
I am not arguing that all of it is, for example I realize parts of it such as X11 are under the MIT license (if I remember right)... but the core project is under the BSD licence.. which means all the work the FreeBSD team themselves do is under the bsd licence.... remember that original AT&T Unix was a proprietary license...

And BSD Unix (which stated using the BSD license at this stage), was based on that, and freeBSD which also uses the BSD license was based on that..

So yes while there is a lot of non-bsd'ed code in there I would argue that the majority is going to be under the BSD licence..

My point being apple are not doing anything they're not supposed to be doing here, trust me, I'd love to shoot angry shouts about apple.... I hate their stuff.... but in this case.... they're not doing anything wrong

---

### Post by Bachstelze on 2012-08-30
> **Primefalcon said:**
> 
So yes while there is a lot of non-bsd'ed code in there I would argue that the majority is going to be under the BSD licence..

Yes, but "the majority" does not mean "all of it". ;) The original point was that both FreeBSD and OS X contain code under a variety of licenses, including the GPL, and that it is OK because it's just different software shipped together, not GPL code injected in a non-GPL program.

---

### Post by Primefalcon on 2012-08-30
> **Bachstelze said:**
> Yes, but "the majority" does not mean "all of it". ;) The original point was that both FreeBSD and OS X contain code under a variety of licenses, including the GPL, and that it is OK because it's just different software shipped together, not GPL code injected in a non-GPL program.
Either way our points are the same.... Apple is doing nothing wrong in this case........ unfortunately.........

---

### Post by expelledboy on 2012-09-01
> **Primefalcon said:**
> Either way our points are the same.... Apple is doing nothing wrong in this case........ unfortunately.........

Perhaps I shouldnt have implicated apple. I knew they would have a tight ship, and supporters thereof. What is unfortunate is that everyone is missing the other half of my communication, with regards in particular to the company I fingered out.

---

### Post by Bachstelze on 2012-09-01
> **expelledboy said:**
> What is unfortunate is that everyone is missing the other half of my communication, with regards in particular to the company I fingered out.

That's hardly unexpected, though. No one really cares about an obscure company like that. Apple, on the other hand...

---

### Post by expelledboy on 2012-09-02
Sure apple has a big red target on their backs, but I am sure they jump the loops.

These guys however are breaking the rules.

---

### Post by Bachstelze on 2012-09-02
> **expelledboy said:**
> These guys however are breaking the rules.

How do you know?

---

### Post by expelledboy on 2012-09-02
> **Bachstelze said:**
> How do you know?

I knew you would say that.

Again, I was asking. It appears to me that is the case.

---

### Post by Bachstelze on 2012-09-02
> **expelledboy said:**
> I knew you would say that.

Again, I was asking. It appears to me that is the case.

And nobody heres cares enough to check (not to mention that in order to verify that they do provide the source code to their customers, one would have to either know someone who is a customer, or become one). A good principle states that you do't throw baseless accusations like that.

---

### Post by expelledboy on 2012-09-02
So now you attack my principles?

Surely a good principle to have, being part of the open source community, would be to whistle blow on companies suspected of abusing the work done in the public domain?

And, as we have established, my understanding of the terms of licensing is scratchy at best. So I ask, to both gain understanding and potentially show up a company conducting itself in a way that might interest this community.

Based on your reaction my only resolution is to follow suit and stop caring.

---

### Post by Bachstelze on 2012-09-02
And what have they done to be "suspected" by you? They are selling software? You mistakenly believed that selling software and making it proprietary were the same thing, and we corrected you on that, so now, absent other clues, they are considered perfectly legitimate.

---

### Post by Primefalcon on 2012-09-02
> **Bachstelze said:**
> And what have they done to be "suspected" by you? They are selling software? You mistakenly believed that selling software and making it proprietary were the same thing, and we corrected you on that, so now, absent other clues, they are considered perfectly legitimate.
+1 I don't see much different to red hat here tbh or even untangle, your allowed to put your own custom layers on top, and there'd be something wrong if you couldn't tbh..... not really a lot to discuss about that.

If you really care as much as you say you do? why not contact them yourself and ask about their policy on making source code available? making accusations without facts is......... bad

---

### Post by t0p on 2012-09-02
It is pretty good [what they did on their website]("http://www.2x.com/thinclientserver/") though.  They're selling the 2X ThinClientServer, and they show a pic of a *thin* person.  Get that?  Eh?  Ha ha ha ha ha!!!

Only works if the model is thin though.  Those short shorts wouldn't look so good on me.

---

### Post by vexorian on 2012-09-02
> **snip3r8 said:**
> The GPL is a funny thing, it stands for freedom but **forces** you to contribute by submitting changes back to the community. To me ,anything that forces you to do something is not freedom. Its almost like a "this statement is false" scenario. The MIT Licence is true freedom , and I commit changes without being forced.
This is a common misunderstanding.

You can use GPL code and do anything with it. However, you can't redistribute it without making the source available and letting changes stay with the GPL license.

Nobody is really forcing you to contribute anything to the GPL project. You can make the choice not to do any changes to it. And if you do make changes to it, you can make the choice not to release those changes and thus avoid all those conditions required to make you able to redistribute it.

I think the GPL gives true freedom precisely because of these conditions. I believe that your own freedom ends where other people's freedoms begin. In real life, we are all considered free people, but for that to be possible, it is illegal to kidnap people and lock them inside rooms or to enslave them. We are truly free, because it is not allowed to remove freedom from others. 

In the case of free software, the stakes are not nearly as seriously as in kidnapping and slavery, but I think it works the say. And it has given us great results in the past. Think about Oracle. Our freedom is guaranteed because Oracle has no freedom to take it away from us.

Another misunderstanding is that the GPL stops corporations from benefiting from open source. There is really nothing in the GPL that bans corporations from getting a benefit. What the GPL prevents is a case where *a single* corporation getting the benefit. CUPS for example has made Apple's life a lot easier. But thanks to it, corporations like Canonical and Red Hat also grab a benefit from it.

---

### Post by Bachstelze on 2012-09-02
> **vexorian said:**
> 
I think the GPL gives true freedom precisely because of these conditions. I believe that your own freedom ends where other people's freedoms begin. In real life, we are all considered free people, but for that to be possible, it is illegal to kidnap people and lock them inside rooms or to enslave them. We are truly free, because it is not allowed to remove freedom from others. 

In the case of free software, the stakes are not nearly as seriously as in kidnapping and slavery, but I think it works the say. And it has given us great results in the past. Think about Oracle. Our freedom is guaranteed because Oracle has no freedom to take it away from us.

The GPL is based on intellectual property (in particular, copyright). Some people believe that the entire idea of intellectual property contradicts that of freedom, because you are in effect regulating people's minds. The GPL community uses intellectual property laws to its advantage, but from the standpoint of an intellectual property opponent, there is no significant difference between the GPL and proprietary software. Someone is still dictating that you can't do something with a bunch of bits that sit on a media that that you possess.

---

### Post by KiwiNZ on 2012-09-02
> **bachstelze said:**
> the gpl is based on intellectual property (in particular, copyright). Some people believe that the entire idea of intellectual property contradicts that of freedom, because you are in effect regulating people's minds. The gpl community uses intellectual property laws to its advantage, but from the standpoint of an intellectual property opponent, there is no significant difference between the gpl and proprietary software. Someone is still dictating that you can't do something with a bunch of bits that sit on a media that that you possess.

+1

---

### Post by mips on 2012-09-03
> **expelledboy said:**
> Perhaps I shouldnt have implicated apple. I knew they would have a tight ship, and supporters thereof. What is unfortunate is that everyone is missing the other half of my communication, with regards in particular to the company I fingered out.

Your accusations are baseless and without merit. Apple is playing by the rules and do make open source code they use available.
[http://opensource.apple.com/](http://opensource.apple.com/)
[http://www.macosforge.org/](http://www.macosforge.org/)

If Apple were to do anything wrong in this regard they would have the SFS & SFLC all over them in a blink of an eye.

---

### Post by expelledboy on 2012-09-03
I didnt accuse apple, I was just inquiring. Regardless I learnt from it.

> If Apple were to do anything wrong in this regard they would have the SFS & SFLC all over them in a blink of an eye. 
Who are the SFS?

> And what have they done to be "suspected" by you?
Unfortunately I cant point fingers at what they have done. I base my suspicions on the impression I get having read about them online. For example on their own forums;
[LIST]
[*][http://www.2x.com/forums/viewtopic.php?t=83](http://www.2x.com/forums/viewtopic.php?t=83)
[*][http://www.2x.com/forums/viewtopic.php?f=6&t=2610](http://www.2x.com/forums/viewtopic.php?f=6&t=2610)
[*][http://www.2x.com/forums/viewtopic.php?f=2&t=1862](http://www.2x.com/forums/viewtopic.php?f=2&t=1862)
[*][http://www.2x.com/forums/viewtopic.php?f=2&t=581](http://www.2x.com/forums/viewtopic.php?f=2&t=581)
[/LIST]

The last link is probably the most relevant.

---

### Post by Bachstelze on 2012-09-03
> **expelledboy said:**
> 
Unfortunately I cant point fingers at what they have done. I base my suspicions on the impression I get having read about them online. For example on their own forums;
[LIST]
[*][http://www.2x.com/forums/viewtopic.php?t=83](http://www.2x.com/forums/viewtopic.php?t=83)
[*][http://www.2x.com/forums/viewtopic.php?f=6&t=2610](http://www.2x.com/forums/viewtopic.php?f=6&t=2610)
[*][http://www.2x.com/forums/viewtopic.php?f=2&t=1862](http://www.2x.com/forums/viewtopic.php?f=2&t=1862)
[*][http://www.2x.com/forums/viewtopic.php?f=2&t=581](http://www.2x.com/forums/viewtopic.php?f=2&t=581)
[/LIST]

The last link is probably the most relevant.

It is said in the last link that they use the software unmodified, meaning you can get the source code from other sources. I don't know whether or not it is actually okay for them to not distribute the source if it is already available somewhere else, but even if it's not it's certainly a less serious violation.

---

### Post by mips on 2012-09-03
> **expelledboy said:**
> 
Who are the SFS?

Sorry that should be FSF
FSF - [http://www.fsf.org/](http://www.fsf.org/)
SFLC - [http://www.softwarefreedom.org/](http://www.softwarefreedom.org/)

---

