---
title: "whats that license?"
date: 2009-12-15
forum: The Cafe
---

### Post by rahilm on 2009-12-15
Hi. I am new to the open source world. Just out of curiosity i wonder what is the difference between GPL LGPL and the BSD license. Are there any more licenses worth noting in the same line?

I tried googling and found some difference but I want personal responses. and I am not good at reading long licenses

---

### Post by issih on 2009-12-15
[http://developer.kde.org/documentation/licensing/licenses_summary.html](http://developer.kde.org/documentation/licensing/licenses_summary.html)

Hope that helps :)

---

### Post by Exodist on 2009-12-15
[http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)
[http://www.gnu.org/licenses/lgpl.html](http://www.gnu.org/licenses/lgpl.html)
[http://www.gnu.org/licenses/gfdl.html](http://www.gnu.org/licenses/gfdl.html)
[http://www.gnu.org/licenses/agpl.html](http://www.gnu.org/licenses/agpl.html)
[http://creativecommons.org/about/licenses/](http://creativecommons.org/about/licenses/)

---

### Post by Xbehave on 2009-12-15
Oversimplified summary
BSD = Use this code as you wish
MPL = Changes to files we give you files must be given back
LGPL = Any changes to this project must be given back
GPL = Any code developed from this project must be given back

There are many licenses that are similar to BSD/MPL but have different restrictions, but AFAIK LGPL and GPL are the only licenses that require you give your code, if you distribute an improved version of the project.

---

### Post by earthpigg on 2009-12-15
whatever you do, do not forget the [WTFPL]("http://en.wikipedia.org/wiki/WTFPL")!!!

:D

---

### Post by rahilm on 2009-12-15
So what makes GPL so much better??

---

### Post by alphaniner on 2009-12-15
> **rahilm said:**
> So what makes GPL so much better??

That's largely a matter of personal philosophy.  I favour the BSD license.

---

### Post by aaaantoine on 2009-12-15
> **rahilm said:**
> So what makes GPL so much better??

The point of the GPL is for the source code to not only be open and freely distributable, but also to prevent others from taking the work and using it in a closed source application.  Developing under the GPL license means compulsory source code sharing.

Contrast with the BSD license, which makes the source code open and freely distributable, to the point that anyone can take it and make their own thing with it, without giving back to those who developed it to begin with.  *glares at OS X*

The GPL is arguably why Linux is more popular to develop for than *BSD.

---

### Post by earthpigg on 2009-12-15
> **rahilm said:**
> So what makes GPL so much better??

heh, funny you ask... [this thread]("http://ubuntuforums.org/showthread.php?t=1354778") from yesterday was originally not about licenses at all, then it got off topic and thus closed.

a few of us got into some rather ranting discussions about the gpl, bsd, etc.

since this thread is specifically about different licenses, it should be ok to talk about here.

give that thread as skim :D

one thing we need to be sure about here, however, is that we keep it civil. a lot of folks have some pretty strong opinions on the matter.

so, anyone that wishes to participate: please keep the [ad hominem]("http://en.wikipedia.org/wiki/Ad_hominum") and [straw man]("http://en.wikipedia.org/wiki/Straw_man") out of it.

i certainly wouldn't mind a good discussion about this topic that *didn't* get closed.

---

### Post by cariboo on 2009-12-15
> **aaaantoine said:**
> The point of the GPL is for the source code to not only be open and freely distributable, but also to prevent others from taking the work and using it in a closed source application.  Developing under the GPL license means compulsory source code sharing.

Contrast with the BSD license, which makes the source code open and freely distributable, to the point that anyone can take it and make their own thing with it, without giving back to those who developed it to begin with.  *glares at OS X*

The GPL is arguably why Linux is more popular to develop for than *BSD.

Remember to cast a few glares at Microsoft too, they used the BSD networking stack for the longest time.

---

### Post by RiceMonster on 2009-12-15
> **rahilm said:**
> So what makes GPL so much better??

The difference is the BSD License is more free.








 GO!

---

### Post by alphaniner on 2009-12-15
> **RiceMonster said:**
> The difference is the BSD License is more free.








 GO!

In before post deletion and /thread. :P

---

### Post by Tibuda on 2009-12-15
> **aaaantoine said:**
> *glares at OS X*

The OS X kernel is open source.

---

### Post by nrs on 2009-12-15
It's a matter of perspective. Do you want the code / users to be eternally free? The GPL is superior. Do you want developers to be free? BSD is superior.

---

### Post by earthpigg on 2009-12-15
> **nrs said:**
> It's a matter of perspective. Do you want the code / users to be eternally free? The GPL is superior. Do you want developers to be free? BSD is superior.

well said.

---

### Post by aaaantoine on 2009-12-15
> **danielrmt said:**
> The OS X kernel is open source.

Are you referring to the original Mach kernel, or the Mach kernel as modified by Apple?

I'd like to see the code for the latter.

---

### Post by schauerlich on 2009-12-15
> **aaaantoine said:**
> Contrast with the BSD license, which makes the source code open and freely distributable, to the point that anyone can take it and make their own thing with it, without giving back to those who developed it to begin with.  *glares at OS X*

[http://en.wikipedia.org/wiki/Darwin_(operating_system](http://en.wikipedia.org/wiki/Darwin_(operating_system))
[http://opensource.apple.com/](http://opensource.apple.com/)
[http://ubuntuforums.org/showpost.php?p=7347446&postcount=1](http://ubuntuforums.org/showpost.php?p=7347446&postcount=1)

A little research goes a long way.

---

### Post by Tibuda on 2009-12-15
> **aaaantoine said:**
> Are you referring to the original Mach kernel, or the Mach kernel as modified by Apple?

I'd like to see the code for the latter.

Darwin, which is based on both Mach and FreeBSD: [http://developer.apple.com/Darwin/](http://developer.apple.com/Darwin/)

---

### Post by schauerlich on 2009-12-15
> **aaaantoine said:**
> Are you referring to the original Mach kernel, or the Mach kernel as modified by Apple?

I'd like to see the code for the latter.

[http://www.opensource.apple.com/source/xnu/xnu-1456.1.26/](http://www.opensource.apple.com/source/xnu/xnu-1456.1.26/)

---

### Post by Penguin Guy on 2009-12-15
I would highly advise against the [COLOR="Red"]GPL[/COLOR] - it is very restrictive. The [COLOR="Orange"]LGPL[/COLOR] is a shorter, simpler, less restrictive, and all round better. But I release all my work in the [COLOR="Green"]Public Domain[/COLOR], meaning anybody can use it in any way for any purpose.

Some things to note:
[LIST]
[*]There is no 'right' license - pick whichever one you think is fair
[*]It isn't that important - don't get too worked up about it, it's just a license
[*]Once you've licensed something, you won't (legitimately) be able to change the license
[/LIST]

---

### Post by JDShu on 2009-12-15
> **Penguin Guy said:**
> 
[LIST]
[*]There is no 'right' license - pick whichever one you think is fair
[*]It isn't that important - don't get too worked up about it, it's just a license
[*]Once you've licensed something, you won't (legitimately) be able to change the license
[/LIST]


Point 1 is very true.

Point 2... its not just a license... its law ;)

Point 3 I don't believe is true. Correct me if I'm wrong but code you've written always belongs to you and you can do whatever you want with it at any point in time.

---

### Post by schauerlich on 2009-12-15
> **JDShu said:**
> Point 3 I don't believe is true. Correct me if I'm wrong but code you've written always belongs to you and you can do whatever you want with it at any point in time.

It is very difficult to change the license of a GPL'd project, because you have to 1) track down everyone who's made any contribution to it, however small and 2) get their permission to change the license.

---

### Post by JDShu on 2009-12-15
> **EDavidBurg said:**
> It is very difficult to change the license of a GPL'd project, because you have to 1) track down everyone who's made any contribution to it, however small and 2) get their permission to change the license.

Yes, but you can theoretically change the license of your original code right? Its not useful and you probably get no benefits, but its legally possible.

---

### Post by Xbehave on 2009-12-15
> **EDavidBurg said:**
> It is very difficult to change the license of a GPL'd project, because you have to 1) track down everyone who's made any contribution to it, however small and 2) get their permission to change the license.
You can include a clause in your project saying that you own all code contributed to it (Gnu,mozilla,sun & nmap all do this) to avoid the "problem" you just described.

The only license that fully prevents leaching is the GPL, so the only code i have every put out there is under GPL. MPL/LGPL do have some provisions but if you use my code i want **all** code you derive from it in return, because if it wasn't for me you wouldn't have a project !

---

### Post by koenn on 2009-12-15
> **Xbehave said:**
> 
LGPL = Any changes to this project must be given back
GPL = Any code developed from this project must be given back

this is oversimplified to the point where it becomes inaccurate, or at least very ambiguous.
There is no obligation, under GPL or LGPL, to "give back" to the project/person/copyright holder/ ... the code came from. There's only the obligation that ***if*** you distribute this modified code, it has to be distributed under the same license, and if you distribute it in binary form, you must allow  and arrange for access to the source code **for the person/people you distributed the binaries to**.

---

### Post by koenn on 2009-12-15
> **JDShu said:**
> Yes, but you can theoretically change the license of your original code right?

yes and no.
you can decide to distribute (new copies of) your program or source code under any license you choose, but people who received a copy under your original license X, will still be entitled to all rights you granted them in that license.

---

### Post by koenn on 2009-12-15
> **RiceMonster said:**
> The difference is the BSD License is more free.
... but makes no effort to preserve that freedom.

---

### Post by alphaniner on 2009-12-15
> **koenn said:**
> ... but makes no effort to preserve that freedom.

...at the expense of other freedoms.

---

### Post by nrs on 2009-12-15
> **alphaniner said:**
> ...at the expense of other freedoms.
The only freedom that is a causality of the GPL is the freedom to take away the freedom that was initially granted. :-({|= Rules  like this generally exist in the real world too. 

For all the talk of Stallman being the crazed idealist, I think it's the actually the other way around. For me, the GPL is the pragmatic license because it recognizes the reality of the situation and provides you with protection whereas with the BSD license you're basically staking the code's freedom on the kindness of the strangers. Nothing wrong with that, but it definitely seems more idealistic. 

If you can't think of a scenario where either the BSD or GPL would be useful, you're not using your imagination.

---

### Post by koenn on 2009-12-15
> **nrs said:**
> The only freedom that is a causality of the GPL is the freedom to take away the freedom that was initially granted. :-({|= Rules  like this generally exist in the real world too. 

It's a case of "Your freedom to swing your fist ends where my nose begins"

---

### Post by alphaniner on 2009-12-15
> **nrs said:**
> The only freedom that is a causality of the GPL is the freedom to take away the freedom that was initially granted. :-({|= Rules  like this generally exist in the real world too. 

For all the talk of Stallman being the crazed idealist, I think it's the actually the other way around. For me, the GPL is the pragmatic license because it recognizes the reality of the situation and provides you with protection whereas with the BSD license you're basically staking the code's freedom on the kindness of the strangers. Nothing wrong with that, but it definitely seems more idealistic. 

If you can't think of a scenario where either the BSD or GPL would be useful, you're not using your imagination.

With the BSDL the code's freedom is never at risk.  The only thing risked is that others might claim **their work** as **their own**.  They can't take the work of others out of the 'public domain'.  

And there are other casualties of the GPL, for example the inability to have native support of the ZFS filesystem.  When your freedom limits your freedom, you need to stop and consider if you have gone too far.

---

### Post by Xbehave on 2009-12-15
> **alphaniner said:**
> With the BSDL the code's freedom is never at risk.  The only thing risked is that others might claim **their work** as **their own**.  They can't take the work of others out of the 'public domain'.  

And there are other casualties of the GPL, for example the inability to have native support of the ZFS filesystem.  When your freedom limits your freedom, you need to stop and consider if you have gone too far.
Using linux/BSD/solaris/any free OS limits my freedom to play flash well though, so by your logic i should go back to windows.

Many think that zfs was licensed under CDDL specifically to stop linux being able to import the code as linux is a significant competitor to solaris, but BSD and mac are not (not in the markets where sun make money on solaris anyway), in addition to this even if linux could use the code, it probably wouldn't anyway because it has a very mature VFS that would need a significant rewrite to get ZFS to work and btrfs is an equally good fs (IMO it's better as it's b-tree based which makes more sense than just having slices) and just around the corner (just behind the corner if your experimental)

---

### Post by Chame_Wizard on 2009-12-15
> **Xbehave said:**
> Oversimplified summary
BSD = Use this code as you wish
MPL = Changes to files we give you files must be given back
LGPL = Any changes to this project must be given back
GPL = Any code developed from this project must be given back

There are many licenses that are similar to BSD/MPL but have different restrictions, but AFAIK LGPL and GPL are the only licenses that require you give your code, if you distribute an improved version of the project.

:lolflag:

---

### Post by 3rdalbum on 2009-12-15
> **earthpigg said:**
> whatever you do, do not forget the [WTFPL]("http://en.wikipedia.org/wiki/WTFPL")!!!

If this license ever got tested in court, I'm not sure it would stand up because of the use of profanity. ;-)

---

### Post by alphaniner on 2009-12-15
> **Xbehave said:**
> Using linux/BSD/solaris/any free OS limits my freedom to play flash well though, so by your logic i should go back to windows.

Many think that zfs was licensed under CDDL specifically to stop linux...

If Flash is a priority for you, then yes, I suppose you should.

And frankly I doubt the licensing of ZFS was chosen to limit its use in Linux, but even if it was I my point is still valid.  People ask this about Windows all the time, why choose software with a license that limits your options?  And I think it's a very reasonable question.  But as soon as this logic is applied to Linux, it suddenly becomes bad juju.  I call bullsh*t.

---

### Post by rahilm on 2009-12-17
Given the structure of above mentioned licesnses
Would linux have become more successful if Linux released the kernel under the BSD license or would it have fallen prey to EEE policies of Microsoft?
I personally favour the latter case.

---

### Post by nrs on 2009-12-17
> **alphaniner said:**
> With the BSDL the code's freedom is never at risk.  The only thing risked is that others might claim **their work** as **their own**.  They can't take the work of others out of the 'public domain'.  

_***Their work***_? And what of all the preceding code? How are they entitled to close that?

---

### Post by earthpigg on 2009-12-17
> **nrs said:**
> _***Their work***_? And what of all the preceding code? How are they entitled to close that?

there are ways.

"if you want to contribute code to Project X, you agree to transfer all ownership of the code to Project X Leader. Agree? y/n"

thats how chromium does it.

---

### Post by RiceMonster on 2009-12-17
> **earthpigg said:**
> there are ways.

"if you want to contribute code to Project X, you agree to transfer all ownership of the code to Project X Leader. Agree? y/n"

thats how chromium does it.

Correct me if I'm wrong, but as far as I know, if you contribute to a GNU project, you're required to assign copyright of your code over to the FSF as well.

---

### Post by Xbehave on 2009-12-17
> **RiceMonster said:**
> Correct me if I'm wrong, but as far as I know, if you contribute to a GNU project, you're required to assign copyright of your code over to the FSF as well.
Yes and for software by canonical or sun, but not for the kernel or busy box [[1]]("http://lwn.net/Articles/359013/")

---

### Post by phrostbyte on 2009-12-17
The primary difference between the (L)GPL and BSD is the GPL guarantees that derivative works will also be open source, while BSD does not. There is no proprietary Linux kernel. 

Wine for instance used to be licensed under a BSD-like license, but was re-licensed when proprietary software companies making closed source forks of Wine, and not sharing any of their advancements back. So the Wine developers voted against this practice, and now Wine is LGPL.

---

### Post by phrostbyte on 2009-12-17
> **Xbehave said:**
> Yes and for software by canonical or sun, but not for the kernel or busy box [[1]]("http://lwn.net/Articles/359013/")

Right the Linux kernel is GPLv2 with a glibc linking exception.

---

### Post by Xbehave on 2009-12-17
> **phrostbyte said:**
> Right the Linux kernel is GPLv2 with a glibc linking exception.
What RiceMonster is talking about is copyright assignment that various projects require, it isn't really dependent on the license. The LWN article i link to explains it much better than i can but if you want to give code to an opensource project they often ask you to assign them copyright. 
As Fyodor puts it:
>  By sending these changes to Fyodor or one of the         *
 * Insecure.Org development mailing lists, it is assumed that you are      *
 * offering the Nmap Project (Insecure.Com LLC) the unlimited,             *
 * non-exclusive right to reuse, modify, and relicense the code.  Nmap     *
 * will always be available Open Source, but this is important because the *
 * inability to relicense code has caused devastating problems for other   *
 * Free Software projects (such as KDE and NASM). We also occasionally    *
 * relicense the code to third parties as discussed above.  If you wish to *
 * specify special license conditions of your contributions, just say so   *
 * when you send them.  
However for the linux kernel there is no such assumption and all code is remains yours+GPL instead of yours+project's+GPL (the re-licensing is rarely done so most projects don't even mention it explicitly, but when you hand over copyright assignment you do permit sun/canonical/etc to do that.)

---

### Post by schauerlich on 2009-12-17
I think the LGPL is a good compromise between the GPL and the BSD license.

"I don't really care what you do with the code from my project or what kind of project it's used in, but if you make changes to it, I'd like to see them so that my project gets the benefits too."

---

