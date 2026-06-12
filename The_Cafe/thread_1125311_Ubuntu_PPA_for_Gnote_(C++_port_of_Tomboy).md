---
title: "Ubuntu PPA for Gnote (C++ port of Tomboy)"
date: 2009-04-14
forum: The Cafe
---

### Post by Vadi on 2009-04-14
Gnote is my experimental port of Tomboy to C++

It is the same note taking application, minus things not done yet, boatload of addins and synchronization. Be patient they'll come. 

The old PPA has been cancelled; instead there is another one here: **[https://launchpad.net/~gnote/+archive/ppa](https://launchpad.net/~gnote/+archive/ppa)**. Please remove the [SIZE="1"]https://launchpad.net/~vperetokin/+archive/gnote[/SIZE] one and replace with this one:

[SIZE="4"]New PPA: [https://launchpad.net/~gnote/+archive/ppa](https://launchpad.net/~gnote/+archive/ppa)[/SIZE]

[SIZE="1"]**Changelog:**
**May 13th, '09:**: PPA cancelled, use [https://launchpad.net/~gnote/+archive/ppa](https://launchpad.net/~gnote/+archive/ppa) instead.
**May 2nd, '09:** Gnote 0.3.0 is up, see [changelog]("http://www.figuiere.net/hub/blog/?2009/04/29/663-gnote-030").
**April 24th, '09:** Gnote 0.2.0 is up, see [changelog]("http://www.figuiere.net/hub/blog/?2009/04/22/661-gnote-020").
**April 16th, '09:** Gnote 0.1.2 is up, see [changelog]("http://www.figuiere.net/hub/blog/?2009/04/15/660-gnote-012").
**April 15th, '09:** Just a small fix to the package - make it so it appears in *Applications* and *Alt+F2* right after installation.
**April 14th, '09:** Gnote 0.1.1, fixes compiling issues for older distros.[/SIZE]

---

### Post by cl333r on 2009-04-14
Thanks!
Less Microsoft "intellectual property" in our OS less worries for us!

---

### Post by Methuselah on 2009-04-14
> **cl333r said:**
> Thanks!
Less Microsoft "intellectual property" in our OS less worries for us!

Heh..like FLOSS needs to tap into the intellect that took 5 years to give up and release ... Vista.
Look at how major open source projects have improved in the past 5 years and you'll see no comparison.

---

### Post by Simian Man on 2009-04-14
Wow just the other day I was thinking "Tomboy's great but I wish they had used crappy, painful tools to write it in".  Now with gnote, the developers will be able to really focus on the nitty-gritty programming details of it rather than adding annoying features and stability.  Awesome!!

---

### Post by zekopeko on 2009-04-14
i always laugh when people do such counter-productive things because they are afraid. Looks like FUD is in full swing. Way to go Vadi!

@Simian Man: nice /s :D

---

### Post by Methuselah on 2009-04-14
> **Simian Man said:**
> Wow just the other day I was thinking "Tomboy's great but I wish they had used crappy, painful tools to write it in".  Now with gnote, the developers will be able to really focus on the nitty-gritty programming details of it rather than adding annoying features and stability.  Awesome!!

Wow. Since when are gcc, C, and C++ crappy, painful tools?
Since linux is implemented in C and it's pretty damn likely Mono is too, it might be a bad idea to curse the hand that feeds you. ;)

---

### Post by directhex on 2009-04-14
Still missing most of Tomboy's features, and involving wholesale license & copyright violation

But remember, kids - stealing code is fine as long as it's "one in the eye" for Free Software developers like the Tomboy authors!

---

### Post by zekopeko on 2009-04-14
> **cl333r said:**
> Thanks!
Less Microsoft "intellectual property" in our OS less worries for us!

C# is an ECMA and ISO standard. And i always find it funny how nobody mentions that the GNU Project (the one which Richard Stallman founded) has a C# implementation called  DotGNU.

---

### Post by Simian Man on 2009-04-14
> **Methuselah said:**
> Wow. Since when are gcc, C, and C++ crappy, painful tools?
Since linux is implemented in C and it's pretty damn likely Mono is too, it might be a bad idea to curse the hand that feeds you. ;)

They are crappy, painful tools for desktop application development.  For the kernel and lower-level tools like Mono, they are fantastic.  I primarily program in C, but I would never choose it for something like Tomboy.

They say that when the only tool you have is a hammer, all of your problems start to look like nails.  C and C++ are hammers are desktop apps aren't nails.

Look at Banshee and Rhythmbox.  Banshee (C#) already has surpassed Rhythmbox (C) in terms of features despite Rhythmbox having a four year head start!

---

### Post by Methuselah on 2009-04-14
> **directhex said:**
> Still missing most of Tomboy's features, and involving wholesale license & copyright violation

But remember, kids - stealing code is fine as long as it's "one in the eye" for Free Software developers like the Tomboy authors!

Stealing code? 
Are you suggesting that Tomboy isn't released under and open source license?
If so, there may be an even stronger case for re-implementation since Gnome is 'free software'.

---

### Post by zekopeko on 2009-04-14
> **Methuselah said:**
> Wow. Since when are gcc, C, and C++ crappy, painful tools?
Since linux is implemented in C and it's pretty damn likely Mono is too, it might be a bad idea to curse the hand that feeds you. ;)

Mono is implemented in mono ;) . Their compiler/VM is written in mono and it compiles itself in mono :lolflag:

---

### Post by directhex on 2009-04-14
> **Methuselah said:**
> Stealing code? 
Are you suggesting that Tomboy isn't released under and open source license?
If so, there may be an even stronger case for re-implementation since Gnome is 'free software'.

I'm suggesting that

1) you can't change an app's license. Tomboy is LGPL2.1-only, GNote is GPL3. You can't simply say "I am declaring this code to be GPL3 because I want it to be", despite the provisions in the license permitting accepting of TERMS from a later license (assuming that clause is permitted, which it is NOT in this case)

2) You can't say "copyright me and only me" on code by other people

Unless you think it'd be cool for someone to, say, look at the Linux source, translate it line-by-line into C++, and cover it under a proprietary license, claiming 100% of copyright ownership

---

### Post by directhex on 2009-04-14
> **zekopeko said:**
> Mono is implemented in mono ;) . Their compiler/VM is written in mono and it compiles itself in mono :lolflag:

The runtime is C. The compiler & libs are C#.

---

### Post by zekopeko on 2009-04-14
> **directhex said:**
> The runtime is C. The compiler & libs are C#.

didn't know that. thanks

---

### Post by Methuselah on 2009-04-14
> **Simian Man said:**
> They are crappy, painful tools for desktop application development.  For the kernel and lower-level tools like Mono, they are fantastic.  I primarily program in C, but I would never choose it for something like Tomboy.

They say that when the only tool you have is a hammer, all of your problems start to look like nails.  C and C++ are hammers are desktop apps aren't nails.

Look at Banshee and Rhythmbox.  Banshee (C#) already has surpassed Rhythmbox (C) in terms of features despite Rhythmbox having a four year head start!

Yes, I thought your comment was rather heavy handed and did not think you meant it...but couldn't resist calling you out...
I agree that C is a rather low level language with few ways to hide low level considerations.
I learned C++ first and I still find C difficult because you find yourself always dealing with the boilerplate stuff.
C++ on the other hand, has quite powerful abstraction techniques and with the right libraries it is truly high-level and efficient.
It still might be more heavy duty tool than C# but a crocodile can carry its newly hatched young in the same mouth than can rend apart a wildebeest.

Despite over a decade of Java and years of .NET, the most successful proprietary and open source desktop applications are still mostly C/C++ programs.
I am not even considering the fact that the former frameworks have moneyed companies/marketing machines behind them whereas the latter have been quiet, standardised workhorses chosen for their genuine virtues.
So if wanted, I'd argue Gnote is using tried and true tools (which Mono certainly isn't) rather than 'crappy tools'.

---

### Post by Methuselah on 2009-04-14
> **directhex said:**
> I'm suggesting that

1) you can't change an app's license. Tomboy is LGPL2.1-only, GNote is GPL3. You can't simply say "I am declaring this code to be GPL3 because I want it to be", despite the provisions in the license permitting accepting of TERMS from a later license (assuming that clause is permitted, which it is NOT in this case)

2) You can't say "copyright me and only me" on code by other people

Unless you think it'd be cool for someone to, say, look at the Linux source, translate it line-by-line into C++, and cover it under a proprietary license, claiming 100% of copyright ownership


Sorry, I don't know the full details.
But 'stealing' and 'copyright infringement' seem like overly strong accusations given the open source context.

---

### Post by directhex on 2009-04-14
> **Methuselah said:**
> Sorry, I don't know the full details.
But 'stealing' and 'copyright infringement' seem like overly strong accusations given the open source context.

"open source" is not the same thing as "public domain" - Free Software can only live as a result of strong licensing and copyright law.

If you use something in violation of its license - whether said license is the GPL, LGPL, Windows EULA, or whatever, then you are still in violation - take a peek at [http://gpl-violations.org/](http://gpl-violations.org/) for some companies who thought it was fine to rip off GPL'd things wholesale. You can't change a source's license without explicit permission to do so (e.g. as offered in WTFPL), and you can't claim copyright over someone else's work.

---

### Post by Simian Man on 2009-04-14
> **Methuselah said:**
> I agree that C is a rather low level language with few ways to hide low level considerations.
I learned C++ first and I still find C difficult because you find yourself always dealing with the boilerplate stuff.
C++ on the other hand, has quite powerful abstraction techniques and with the right libraries it is truly high-level and efficient.
It still might be more heavy duty tool than C# but a crocodile can carry its newly hatched young in the same mouth than can rend apart a wildebeest.
C++ still requires manual memory-management which is an order of magnitude bigger pain in the *** than any of the C problems that C++ actually solves.  In fact I find C++ more painful than straight C because it allows you to abstract much of the details away, but the portion that you cannot abstract will always bite you when you don't expect it.  A real high-level language is still a better option than C++.

> **Methuselah said:**
> Despite over a decade of Java and years of .NET, the most successful proprietary and open source desktop applications are still mostly C/C++ programs.
I am not even considering the fact that the former frameworks have moneyed companies/marketing machines behind them whereas the latter have been quiet, standardised workhorses chosen for their genuine virtues.
So if wanted, I'd argue Gnote is using tried and true tools (which Mono certainly isn't) rather than 'crappy tools'.

That is mostly due to legacy and inertia.  What applications that have been started since, say 2000, are the "most successful proprietary and open source desktop applications" that you are speaking of.  Most of these apps like OpenOffice, Firefox, and most Gnome and KDE apps have significant base codes and/or library frameworks that date back to when C/C++ was still the only viable option.  That isn't the case any more, but things tend to take a while to change.

---

### Post by zekopeko on 2009-04-14
> **Methuselah said:**
> Sorry, I don't know the full details.
But 'stealing' and 'copyright infringement' seem like overly strong accusations given the open source context.

if this is true then i'm guessing Gnote doesn't have much time since probably some tomboy contributor with copyright will threaten legal action.

like directhex said, you can't take the code from a project and slap your license on it without adhering to the license of the original project. 

so in future reference, if this does happen (legal action) don't think for a second that it's because the "author" of Gnote is getting slammed for porting tomboy to c++. he is going to get slammed because he's using the code from the project against the wishes of it's creators as defined in the tomoboy's code license.

btw: something similar happened a few years ago with Linux wireless driver code being used in a BSD project against it's license. guess what happened. the subversion for the BSD project was shutdown after the pressure from the copyright holder.

---

### Post by SKLP on 2009-04-14
> **simian man said:**
> wow just the other day i was thinking "tomboy's great but i wish they had used crappy, painful tools to write it in".  Now with gnote, the developers will be able to really focus on the nitty-gritty programming details of it rather than adding annoying features and stability.  Awesome!!

+1
;-)

---

### Post by Methuselah on 2009-04-14
You guys may be right on the license issues.
I'm no lawyer.

> **Simian Man said:**
> C++ still requires manual memory-management which is an order of magnitude bigger pain in the *** than any of the C problems that C++ actually solves.  In fact I find C++ more painful than straight C because it allows you to abstract much of the details away, but the portion that you cannot abstract will always bite you when you don't expect it.  A real high-level language is still a better option than C++.


Resource management will always be an issue.
If not memory, then something else.
I remember finding it funny that Java went on and on about garbage collection but for any other kind of resource management I might as well have been using C.
I personally like the patterns that exist in C++ for resource management and often miss them when I go to these 'higher level languages' that look suspicously like it syntactically.


> That is mostly due to legacy and inertia.  What applications that have been started since, say 2000, are the "most successful proprietary and open source desktop applications" that you are speaking of.  Most of these apps like OpenOffice, Firefox, and most Gnome and KDE apps have significant base codes and/or library frameworks that date back to when C/C++ was still the only viable option.  That isn't the case any more, but things tend to take a while to change.

Legacy and inertia definitely play a role but it doesn't really negate the point that C++ is mature application programming language and certainly not a 'crappy' choice unless one is selling something else.
This reminds me of the 'why use linux where you might have to type command codes when you can use the windows?' angle.
Well, we use it because it is efficient, powerful, mature, and open/free even if sometimes a bit less convenient.

---

### Post by Mr. Picklesworth on 2009-04-14
Great, this could be the proof we need that Mono does not actually have a big memory footprint.

Anyway, try not to create too much noise about the license. I'm sure it's just a misunderstanding on the author's part.

---

### Post by directhex on 2009-04-14
> **zekopeko said:**
> if this is true then i'm guessing Gnote doesn't have much time since probably some tomboy contributor with copyright will threaten legal action.

like directhex said, you can't take the code from a project and slap your license on it without adhering to the license of the original project. 

so in future reference, if this does happen (legal action) don't think for a second that it's because the "author" of Gnote is getting slammed for porting tomboy to c++. he is going to get slammed because he's using the code from the project against the wishes of it's creators as defined in the tomoboy's code license.

btw: something similar happened a few years ago with Linux wireless driver code being used in a BSD project against it's license. guess what happened. the subversion for the BSD project was shutdown after the pressure from the copyright holder.

> **Mr. Picklesworth said:**
> Anyway, try not to create too much noise about the license. I'm sure it's just a misunderstanding on the author's part.

Tomboy's authors are actually pretty keen to resolve the matter amicably - however, Gnote is about as aggressive a fork as an aggressive fork can be - and whilst the author might not properly understand what he's done wrong (pretty obvious from reading his contributions to mailing lists plus his Git commit logs), that doesn't mean there'll be legal action. Nobody wants legal action, and the Tomboy authors feel (as do many of us) that whilst it's seemingly redundant, it's impressive work. There's no reason for things to hit the proverbial fan just because the "ZOMG NO MONOZ!!" crowd overlap the "ONLY GPLv3 SI TEH FREE!!!" crowd.

As I've said elsewhere: even if you DO have the freedom to do something, there's a difference between exercising Freedom and being a dick. Co-opting a large codebase and claiming it as your own would best-case be a dick move. Even if relicensing were permitted, changing license on someone else's code is considered (let's hear it now) a dick move.

If Hub was after anything other than exposure and brownie points from the mental subnormals on FUD blogs like BN, then he wouldn't have done the things he did. If he wanted to work *positively* with others, then he could easily do so.

---

### Post by Vadi on 2009-04-14
*directhex*, stop bickering, contact the author and let him know - it is most likely a misunderstanding. As the author is an ex-Novell employee and an Abiword contributor, I doubt his intentions were to deframe anyone. Are you even part of the Tomboy team to complain?

---

### Post by directhex on 2009-04-14
> **Vadi said:**
> *directhex*, stop bickering, contact the author and let him know - it is most likely a misunderstanding.

He DOES know. He's framing it as a "minor issue", which he supposedly "fixed" with a 6-line commit to Git. He has no interest in actually resolving the problems.

> As the author is an ex-Novell employee and an Abiword contributor, I doubt his intentions were to deframe anyone.

His intentions are "one in the eye" for his former employee. Claiming ownership & unilateral relicensing are probably a good way to do this.

> Are you even part of the Tomboy team to complain?

No. I'm not a member of the kernel team either, but I resolved a GPL violation there too.

---

### Post by bsharp on 2009-04-14
I don't use Tomboy, but why in the world does it matter what language a functional program is done in? As long as it works, does it really matter if it is C/C++ or C#?

---

### Post by zekopeko on 2009-04-14
> **directhex said:**
> Tomboy's authors are actually pretty keen to resolve the matter amicably - however, Gnote is about as aggressive a fork as an aggressive fork can be - and whilst the author might not properly understand what he's done wrong (pretty obvious from reading his contributions to mailing lists plus his Git commit logs), that doesn't mean there'll be legal action. Nobody wants legal action, and the Tomboy authors feel (as do many of us) that whilst it's seemingly redundant, it's impressive work. There's no reason for things to hit the proverbial fan just because the "ZOMG NO MONOZ!!" crowd overlap the "ONLY GPLv3 SI TEH FREE!!!" crowd.

As I've said elsewhere: even if you DO have the freedom to do something, there's a difference between exercising Freedom and being a dick. Co-opting a large codebase and claiming it as your own would best-case be a dick move. Even if relicensing were permitted, changing license on someone else's code is considered (let's hear it now) a dick move.

If Hub was after anything other than exposure and brownie points from the mental subnormals on FUD blogs like BN, then he wouldn't have done the things he did. If he wanted to work *positively* with others, then he could easily do so.

i just wanted to say that this isn't a situation without legal ramification. he took the app and ported it in a fashion that goes against the wished of the author's of tomboy. and he should understand that it's with in their right so sue him.

i would also like to say that i hope this situation get's resolved amicably. but considering the whole point of the port (as you nicely put it: ZOMG NO MONOZ!!!!) i'm doubtful.

---

### Post by directhex on 2009-04-14
> **bsharp said:**
> I don't use Tomboy, but why in the world does it matter what language a functional program is done in? As long as it works, does it really matter if it is C/C++ or C#?

For some people, it's the only thing that matters.

```
directhex@desire:~$ du -hs /usr/lib/tomboy/
520K	/usr/lib/tomboy/
directhex@desire:~$ du -hs /usr/bin/gnote 
1.2M	/usr/bin/gnote
```

C++ IS SO MUCH LESS RESOURCE HUNGRY, SEE!

---

### Post by zekopeko on 2009-04-14
> **Vadi said:**
> *directhex*, stop bickering, contact the author and let him know - it is most likely a misunderstanding. As the author is an ex-Novell employee and an Abiword contributor, I doubt his intentions were to deframe anyone. Are you even part of the Tomboy team to complain?

directhex isn't bickering. he is merely pointing the legal problems that should be addressed as soon as possible.

i personally think that this port is a waste of time but if it makes the author happy... go for it while adhering to the tomboy license.

---

### Post by Simian Man on 2009-04-14
> **bsharp said:**
> I don't use Tomboy, but why in the world does it matter what language a functional program is done in? As long as it works, does it really matter if it is C/C++ or C#?

Some people have some kind of agenda to push against C# even though it is an international standard and the implementation (Mono) and libraries used (Gtk#) are all free software.  You're not missing something, it doesn't matter, and is retarded.

> **directhex said:**
> 
```
directhex@desire:~$ du -hs /usr/lib/tomboy/
520K	/usr/lib/tomboy/
directhex@desire:~$ du -hs /usr/bin/gnote 
1.2M	/usr/bin/gnote
```

C++ IS SO MUCH LESS RESOURCE HUNGRY, SEE!

LOL I imagine this will only continue to grow as more features are added and bugs are fixed.

---

### Post by directhex on 2009-04-14
> **Simian Man said:**
> LOL I imagine this will only continue to grow as more features are added and bugs are fixed.

The Tomboy number is for the ENTIRE app, including every single space-hungry addon, versus bare Gnote. Tomboy's disk consumption comes from its documentation

---

### Post by Vadi on 2009-04-14
Gnote starts faster, and looking at the ram it uses (5.1mb vs 22mb), it is more memory-efficient (do note though that it's not fully implemented, so that might change!).

That is the difference - it's a user vs. developer tradeoff. Either developer can code the thing faster, but user gets it slower and more ram-heavy, or the developer spends lots of time, and the user gets it faster and more memory efficient.

Which is why Vala is looking wonderful - C#-like syntax, C speed, and no additional runtime components for the user.

edit: directhex, yes, not everyone is as anal about licensing as you. I agree with the author. Not like the FSF, Tomboy authors, or anyone important is coming after him with mad rage.

---

### Post by directhex on 2009-04-14
> **Vadi said:**
> edit: directhex, yes, not everyone is as anal about licensing as you. I agree with the author. Not like the FSF, Tomboy authors, or anyone important is coming after him with mad rage.

I know you do. I find it frankly hilarious how much the anti-Mono crowd don't give a crap about Free Software or licensing.

---

### Post by zekopeko on 2009-04-14
> **Vadi said:**
> edit: directhex, yes, not everyone is as anal about licensing as you. I agree with the author. Not like the FSF, Tomboy authors, or anyone important is coming after him with mad rage.

so it's ok to steal other people's work and claim it as yours?
the FLOSS world works because people value other people's work and respect their wishes about usage rights on the code.

---

### Post by Vadi on 2009-04-14
No, it's not ok. It is OK though to publicly say that it is a port of tomboy, including in the application, and fix up the licensing in the 3rd or later releases.

Seriously - if the Tomboy developers had an issue, they'd say something. You two are just raising hell on an issue which is understood by everyone else, including the affected parties.

---

### Post by saulgoode on 2009-04-14
> **directhex said:**
> I'm suggesting that

1) you can't change an app's license. Tomboy is LGPL2.1-only, GNote is GPL3.
You should perhaps read the terms of version 2.1 of the Lesser General Public License sometime, in particular the first sentence of Section 3.

---

### Post by Vadi on 2009-04-14
Looks like saulgoode just won.

> You may opt to apply the terms of the ordinary GNU General Public License instead of this License to a given copy of the Library. To do this, you must alter all the notices that refer to this License, so that they refer to the ordinary GNU General Public License, version 2, instead of to this License. (If a newer version than version 2 of the ordinary GNU General Public License has appeared, then you can specify that version instead if you wish.)

---

### Post by days_of_ruin on 2009-04-14
pwnt!

---

### Post by zekopeko on 2009-04-14
> **Vadi said:**
> Looks like saulgoode just won.

i wasn't aware this was a competition.

i skimmed through the 3rd section and i'm not so sure that section 3 applies but i could be wrong. who can change the the license to GPL2+? anybody who takes the code or only the copyright holder?

if it's the later then gnote author is still going against the LGPL 2.1 since the had no authority to change the license.

---

### Post by Simian Man on 2009-04-14
Even if the license thing is a non-issue (I don't really know), gnote is still a spiteful, useless failure.

---

### Post by directhex on 2009-04-14
> **saulgoode said:**
> You should perhaps read the terms of version 2.1 of the Lesser General Public License sometime, in particular the first sentence of Section 3.

Point well made.

And the claiming other peoples' copyright?

---

### Post by ghindo on 2009-04-14
[img]http://img524.imageshack.us/img524/8899/1236735067144.gif[/img]

---

### Post by zekopeko on 2009-04-14
> **Simian Man said:**
> Even if the license thing is a non-issue (I don't really know), gnote is still a spiteful, useless failure.

i have 0 problem with that as long everything is in legal order. if people want to be petty they should have that option. i just have a problem with them disregarding other people's wishes.

---

### Post by Vadi on 2009-04-14
edit: thanks *ghindo*.

---

### Post by Methuselah on 2009-04-14
> 
Even if the license thing is a non-issue (I don't really know), gnote is still a spiteful, useless failure.



Hmm...I see it more like: "Hey, I like Tomboy's design but it would probably be faster and have less dependencies if it were written in C++".
Let me give it a shot!

---

### Post by Vadi on 2009-04-14
**[http://www.figuiere.net/hub/blog/?q=gnote](http://www.figuiere.net/hub/blog/?q=gnote)**

Thanks.

---

### Post by SKLP on 2009-04-14
> **Methuselah said:**
> Hmm...I see it more like: "Hey, I like Tomboy's design but it would probably be faster and have less dependencies if it were written in C++".
Let me give it a shot!Well that's just incorrect...
a small application that's mostly GUI "glue" and a little note database is very unlikely to get any *FASTER* or slower by being written in a lower-level language. It would probably not be noticable performance-wise even if it was written in Python. Development will slow though, when it's written in C++(probably).
Regarding "less dependencies", well I don't know
* the gtkmm stack is probably equivalent to the GTK# stack
* the boost libraries are probably smaller than the mono BCL, but on the other hand a minimal mono install is pretty damn small

---

### Post by directhex on 2009-04-14
> **Methuselah said:**
> Hmm...I see it more like: "Hey, I like Tomboy's design but it would probably be faster and have less dependencies if it were written in C++".
Let me give it a shot!

Which is fair enough. Gnote's a very impressive achievement, especially in such a short stretch of time. The "less dependencies" thing will shrink over time though - e.g. fifty percent of the space difference between tomboy & gnote (including all their uniquely held dependencies) is documentation (Gnote is undocumented). Deps to fill in missing functionality (e.g. the lack of syncing support) will likely increase things further

---

### Post by zekopeko on 2009-04-14
> **directhex said:**
> Point well made.

And the claiming other peoples' copyright?

isn't this fixed in git?

it looks like section 3 applies after all since the "you" part is the licensee. but,again, i could be wrong.

i give up at this point. no point to beat a dead cow. if there is a problem with copyright tomboy developers can sort it out since it's their app. the boycott novel crowd is still going to be paranoid and anti-productive as ever so no point to continue a futile "battle".

@Vadi: you should re-read the Miguel de Icaza's comment on Hub's site and rethink your position. that man and others like him did an amazing job bringing an excellent  development framework to linux. and i'm guessing that there isn't a problem with mono since many companies are using it in their commercial products.

---

### Post by Methuselah on 2009-04-14
> **SKLP said:**
> Well that's just incorrect...
a small application that's mostly GUI "glue" and a little note database is very unlikely to get any *FASTER* or slower by being written in a lower-level language. It would probably not be noticable performance-wise even if it was written in Python. Development will slow though, when it's written in C++(probably).
Regarding "less dependencies", well I don't know
* the gtkmm stack is probably equivalent to the GTK# stack
* the boost libraries are probably smaller than the mono BCL, but on the other hand a minimal mono install is pretty damn small

You use terms like 'very unlikely' and 'probably' etc.
What is the harm in doing it and finding out for sure?
Someone has the time and desire and others are willing to test.
Is this a personal insult to someone?

---

### Post by Methuselah on 2009-04-14
> **directhex said:**
> Which is fair enough. Gnote's a very impressive achievement, especially in such a short stretch of time. The "less dependencies" thing will shrink over time though - e.g. fifty percent of the space difference between tomboy & gnote (including all their uniquely held dependencies) is documentation (Gnote is undocumented). Deps to fill in missing functionality (e.g. the lack of syncing support) will likely increase things further

Then there's the potential of removing Mono where it might be needed for Tomboy only; this is a concern for some people.

---

### Post by directhex on 2009-04-14
> **Methuselah said:**
> You use terms like 'very unlikely' and 'probably' etc.
What is the harm in doing it and finding out for sure?
Someone has the time and desire and others are willing to test.
Is this a personal insult to someone?

I ran the numbers. The difference in disk space between Ubuntu with Tomboy and Ubuntu with Gnote is just under 10 meg. That's a nice saving. But, as stated, there are some hidden caveats in that, such as the 5 meg of docs in Tomboy, and all of Tomboy's add-ins.

> **Methuselah said:**
> Then there's the potential of removing Mono where it might be needed for Tomboy only; this is a concern for some people.

If it reaches feature parity, and if it has full support for importing settings from Tomboy, and if it shows itself to be stable and reliable, and if the desktop team determine a clone as being a wise choice for app to track (i.e. an app without its own development roadmap), then it'd make sense to swap it out.

F-Spot however remains on the default install and would need a replacement too, with the same provisos. Plus i hear Shuttleworth likes Gnome-Do. And there's the issue over Rhythmbox's development being pretty much dead, and the most obvious option to move on to with active development being Banshee.

---

### Post by Methuselah on 2009-04-14
> **directhex said:**
> 

If it reaches feature parity, and if it has full support for importing settings from Tomboy, and if it shows itself to be stable and reliable, and if the desktop team determine a clone as being a wise choice for app to track (i.e. an app without its own development roadmap), then it'd make sense to swap it out.

F-Spot however remains on the default install and would need a replacement too, with the same provisos. Plus i hear Shuttleworth likes Gnome-Do. And there's the issue over Rhythmbox's development being pretty much dead, and the most obvious option to move on to with active development being Banshee.

I feel Mono is unlikely to be removed from Gnome any time soon for various reasons; some technical, some not.
However, Gnote might make Mono removal practicable for some users who desire to do so.

---

### Post by Vadi on 2009-04-14
I did read Miguel's comment. I do think that as a general note, having a framework and an IDE for it on Linux is *awesome*. C#'s syntactic sugar is great too.

But, I didn't state my position in this thread on Mono. I just made the PPA, and follow Gnotes development - because I like the performance improvements it brings to me as a user.

---

### Post by saulgoode on 2009-04-14
> **directhex said:**
> I know you do. I find it frankly hilarious how much the anti-Mono crowd don't give a crap about Free Software or licensing.
Perhaps you can provide some substantiation for the concept that *Mono developers* actually "give a crap about Free Software or licensing" by addressing some of the following:

Why does the Mono Project release its runtime under the 1991 version of the LGPL? Specifically this version is called the Library General Public License version 2.**0**. Why use a Free Software license which predates Linux, is considered deprecated by its authors, and has not even been accepted by the Open Source Initiative as an Open Source license? The LGPLv2.1 was available about two years before the Mono Project was even initiated and and over five years before the decision was made to switch from the GPL licensing under which Mono was originally developed to the LGPL.

Of course, the preceding is based upon the supposed accuracy of the Mono Project's [Licensing FAQ](http://www.mono-project.com/Licensing), which states, "The runtime libraries are under the GNU Library GPL 2.0 (LGPL 2.0)." 

But what *are* the runtime libraries? Do the runtime libraries include the same files as the "runtime" referenced later in the FAQ where the discussion turns to why users might be required to purchase a license from Novell?

What files in the source code fall under the category of "runtime library" (and thus released under the LGPLv2.0)? A quick examination of the source tree reveals a directory called ["runtime"]("http://anonsvn.mono-project.com/viewvc/trunk/mono/runtime/"), but the only thing in it is a couple of shell scripts, neither of which contain any licensing information.

In fact, a search of the entire Mono source code repository reveals that there are NO source files containing licensing information indicating that they are released under the Library General Public License Version 2.0 except files for [the code adopted]("http://anonsvn.mono-project.com/viewvc/trunk/gluezilla/") from the [Gluezilla project]("http://www.ohloh.net/p/10777"). I will assume that the Mono Project has been diligent in obtaining permission from the gluezilla authors to re-license that project's LGPLv2.**1** code under the LGPLv2.**0** license (something not permitted by the LGPLv2.1).

In addition to the gluezilla sources, I would note that the Mono source trees also indicate that something called [libgdiplus]("http://anonsvn.mono-project.com/viewvc/trunk/libgdiplus/") "is licensed under the terms of the GNU Library GPL or the Mozilla Public License 1.1". Is this part of the runtime libraries covered by the LGPLv2.0? It is a bit disconcerting that the LICENSE file does not specify which version of the LGPL is applied (EDIT: my mistake on this point; since it says "Library" the license is clearly v2.**0**), but being as the Mozilla Public License permits releases under other than MPL terms (i.e., re-licensing, see MPLv1.1 Section 3.6), this should not be overly problematic (though potential developers who "give a crap" would probably wish to know for sure whether the code is being relicensed under LGPLv2.0 or MIT/X11 licensing).

I look at the licensing of other Free Software projects and it is very clear what code falls under what license. Even with projects run by "amateurs" (such as the GIMP), either every source file contains a mention of what it's license is, or at least there's a top level directory which asserts that all files under that level carry a certain license. With the Mono Project, the licensing seems to be some unfathomable mish-mosh whereby there's no clue about what files are part of the "runtime libraries" and the source files contain hardly any information other than who the copyright holder is.  

I have not in the past considered myself to be "anti-Mono", though I admit to having become so of late. Not a single concern I've raised about patent grants, Mono components, or licensing terms has been addressed and worse, people associated with the Mono Project resort to merely labeling anybody with such concerns as "liars", "fudsters", "trolls", "douchebags", and "pricks". Such might be understandable if Mono was some Donkey Kong clone written in Python by a kid in his grandma's basement, but Novell has some thirty-odd full-time employees working on it and it is not just a game to be played a few times until you lose interest; you are asking people to adopt it as a programming development platform to which programmers are expected to commit themselves for years to come.

---

### Post by directhex on 2009-04-14
> **saulgoode said:**
> Perhaps you can provide some substantiation for the concept that *Mono developers* actually "give a crap about Free Software or licensing" by addressing some of the following:

Why does the Mono Project release its runtime under the 1991 version of the LGPL? Specifically this version is called the Library General Public License version 2.**0**. Why use a Free Software license which predates Linux, is considered deprecated by its authors, and has not even been accepted by the Open Source Initiative as an Open Source license? The LGPLv2.1 was available about two years before the Mono Project was even initiated and and over five years before the decision was made to switch from the GPL licensing under which Mono was originally developed to the LGPL.

Of course, the preceding is based upon the supposed accuracy of the Mono Project's [Licensing FAQ](http://www.mono-project.com/Licensing), which states, "The runtime libraries are under the GNU Library GPL 2.0 (LGPL 2.0)." 

But what *are* the runtime libraries? Do the runtime libraries include the same files as the "runtime" referenced later in the FAQ where the discussion turns to why users might be required to purchase a license from Novell?

What files in the source code fall under the category of "runtime library" (and thus released under the LGPLv2.0)? A quick examination of the source tree reveals a directory called ["runtime"]("http://anonsvn.mono-project.com/viewvc/trunk/mono/runtime/"), but the only thing in it is a couple of shell scripts, neither of which contain any licensing information.

In fact, a search of the entire Mono source code repository reveals that there are NO source files containing licensing information indicating that they are released under the Library General Public License Version 2.0 except files for [the code adopted]("http://anonsvn.mono-project.com/viewvc/trunk/gluezilla/") from the [Gluezilla project]("http://www.ohloh.net/p/10777"). I will assume that the Mono Project has been diligent in obtaining permission from the gluezilla authors to re-license that project's LGPLv2.**1** code under the LGPLv2.**0** license (something not permitted by the LGPLv2.1).

In addition to the gluezilla sources, I would note that the Mono source trees also indicate that something called [libgdiplus]("http://anonsvn.mono-project.com/viewvc/trunk/libgdiplus/") "is licensed under the terms of the GNU Library GPL or the Mozilla Public License 1.1". Is this part of the runtime libraries covered by the LGPLv2.0? It is a bit disconcerting that the LICENSE file does not specify which version of the LGPL is applied, but being as the Mozilla Public License permits releases under other than MPL terms (i.e., re-licensing, see MPLv1.1 Section 3.6), this should not be overly problematic (though potential developers who "give a crap" would probably wish to know for sure whether the code is being relicensed under LGPLv2.0 or MIT/X11 licensing).

I look at the licensing of other Free Software projects and it is very clear what code falls under what license. Even with projects run by "amateurs" (such as the GIMP), either every source file contains a mention of what it's license is, or at least there's a top level directory which asserts that all files under that level carry a certain license. With the Mono Project, the licensing seems to be some unfathomable mish-mosh whereby there's no clue about what files are part of the "runtime libraries" and the source files contain hardly any information other than who the copyright holder is.  

I have not in the past considered myself to be "anti-Mono", though I admit to having become so of late. Not a single concern I've raised about patent grants, Mono components, or licensing terms has been addressed and worse, people associated with the Mono Project resort to merely labeling anybody with such concerns as "liars", "fudsters", "trolls", "douchebags", and "pricks". Such might be understandable if Mono was some Donkey Kong clone written in Python by a kid in his grandma's basement, but Novell has some thirty-odd full-time employees working on it and it is not just a game to be played a few times until you lose interest; you are asking people to adopt it as a programming development platform to which programmers are expected to commit themselves for years to come.

The runtime is stuff in the "mono/" folder, i.e. the bits written in C which form part of the "mono" source tarball (excluding tools). For files which are missing adequate headers, I'd generally suggest filing a bug - it SHOULD be corrected, but many apps miss these details out.

As for several licenses, try taking a peek at the license for OpenJDK. Licenses in use last time I audited it were GPLv2 (with classpath exception), GPLv2 (without classpath exception), Apache 2.0, Apache 1.1, BSD, custom BSD-like. Firefox is a mix of GPLv2, LGPLv2.1, MPL1.1, several (about 10) BSD-likes, a special 5-clause JPNIC license, a haiku of some kind, 4-clause BSD, the libpng license, zlib license, and probably more besides (debian/copyright is woefully inadequate here). Mishmashes of licenses are not uncommon for big projects. That said, if you spot a specific issue, FILE A BUG. The Debian Mono team has on several occasions registered licensing issues with Mono upstream (e.g. use of CC-SA) which are usually resolved one way or another (usually by removal from package source until a clarified version is released). If you spot a file you want to use in your own project, but are not sure about the licensing terms, then just ask - it's not hard.

---

### Post by bruce89 on 2009-04-14
> **directhex said:**
> F-Spot however remains on the default install and would need a replacement too, with the same provisos. Plus i hear Shuttleworth likes Gnome-Do. And there's the issue over Rhythmbox's development being pretty much dead, and the most obvious option to move on to with active development being Banshee.

The Rhythmbox thing was completely unfounded, and not at all true.

> **Methuselah said:**
> I feel Mono is unlikely to be removed from Gnome any time soon for various reasons; some technical, some not.

Actually, GObject-Introspection and Vala might mean GNOME moves in another direction (Vala and JavaScript (perhaps)).

---

### Post by directhex on 2009-04-14
> **bruce89 said:**
> The Rhythmbox thing was completely unfounded, and not at all true.

How has RB improved since, say, Dapper?

---

### Post by bruce89 on 2009-04-14
> **directhex said:**
> How has RB improved since, say, Dapper?

Perhaps you should read the [NEWS]("http://svn.gnome.org/viewvc/rhythmbox/trunk/NEWS?r1=6226&r2=3804") file?

Anyway, here's the post - [http://cfergeau.blogspot.com/2009/03/why-is-so-hard-to-find-blog-post-title.html](http://cfergeau.blogspot.com/2009/03/why-is-so-hard-to-find-blog-post-title.html)

---

### Post by saulgoode on 2009-04-14
> **directhex said:**
> The runtime is stuff in the "mono/" folder, i.e. the bits written in C which form part of the "mono" source tarball (excluding tools). For files which are missing adequate headers, I'd generally suggest filing a bug - it SHOULD be corrected, but many apps miss these details out.
I appreciate you providing that information. In the interests of the project, shouldn't such knowledge be readily discernible? The "mono/" directory contains no LICENSE file, and a quick scan of that directory would indicate only about five files which specify any licensing information at all (and none of those suggesting LGPLv2.0).

> **directhex said:**
> As for several licenses, try taking a peek at the license for OpenJDK.
I admit to not having examined the source tree for Java, however, I would invite you to examine the Open Java [licensing FAQ]("http://www.sun.com/software/opensource/java/faq.jsp#g") and contrast that with what the Mono Project provides. Or perhaps the [QT licensing FAQ]("http://www.qtsoftware.com/about/licensing/frequently-asked-questions"); both of these serve as fine examples of due diligence in presenting licensing information to prospective developers.

Indeed, most Free Software projects employ a number of licensing schemes, but none that I've seen are so lacking in specifying the licensing of its code as would appear the Mono Project. Most of the projects that leverage multiple licenses require each source file to include a licensing header (as an example, see the [KDE licensing policy]("http://techbase.kde.org/Policies/Licensing_Policy")). This would seem to be especially incumbent upon a project which aspires to be *development platform* for Open Source programmers (but I will leave it to others to present the issue as I'm not interested in contributing to the Mono Project).

---

### Post by directhex on 2009-04-14
> **saulgoode said:**
> I appreciate you providing that information. In the interests of the project, shouldn't such knowledge be readily discernible? The "mono/" directory contains no LICENSE file, and a quick scan of that directory would indicate only about five files which specify any licensing information at all (and none of those suggesting LGPLv2.0).

A couple of them do. Obviously not enough of them, but there are some.


> I admit to not having examined the source tree for Java, however, I would invite you to examine the Open Java [licensing FAQ]("http://www.sun.com/software/opensource/java/faq.jsp#g") and contrast that with what the Mono Project provides. Or perhaps the [QT licensing FAQ]("http://www.qtsoftware.com/about/licensing/frequently-asked-questions"); both of these serve as fine examples of due diligence in presenting licensing information to prospective developers.

Indeed, most Free Software projects employ a number of licensing schemes, but none that I've seen are so lacking in specifying the licensing of its code as would appear the Mono Project. Most of the projects that leverage multiple licenses require each source file to include a licensing header (as an example, see the [KDE licensing policy]("http://techbase.kde.org/Policies/Licensing_Policy")). This would seem to be especially incumbent upon a project which aspires to be *development platform* for Open Source programmers (but I will leave it to others to present the issue as I'm not interested in contributing to the Mono Project).

Hanlon's razor.

---

### Post by gnomeuser on 2009-04-14
> **bruce89 said:**
> Perhaps you should read the [NEWS]("http://svn.gnome.org/viewvc/rhythmbox/trunk/NEWS?r1=6226&r2=3804") file?

Anyway, here's the post - [http://cfergeau.blogspot.com/2009/03/why-is-so-hard-to-find-blog-post-title.html](http://cfergeau.blogspot.com/2009/03/why-is-so-hard-to-find-blog-post-title.html)

8 Months of development gives us:

last.fm stream improvements, iPod and MTP improvements. changes to update rb from outdated libaries but no new features outside of making cd importing possible and they still in close to 5 years have no managed to make device syncronization work. That was what happened in 8 months. Also don't fail to notice that the blog posting you linked does not mention even a single new feature, it's just stated that they have them.

This is what 3 months of Banshee development gets you:

Plenty of new features such as Indexer support, new track editor, support for having files automatically moved as metadata changes (personally I love this one it makes a world of difference with wrongly tagged files), offline mode, new device support and OS X support (as a preview currently not fully functional as of yet admittedly). Bugfixes and the community around Banshee continues to produce interesting plugins to go along with it such as Mirage.

[http://banshee-project.org/download/archives/1.4.1/](http://banshee-project.org/download/archives/1.4.1/)

The list of changes from 1.4.3 to the upcoming 1.5.0 release is already impressive with several performance enhancements and additional features.

Most importantly though to me, Banshee has responsive and kind developers. When a bug is filed it is generally handled well. We can count on the Banshee community to continue to feed us exciting stuff in a stable fashion, as well as handling bugs and performance issues.

---

### Post by Vadi on 2009-04-14
RB and Banshee are the one most laughable examples ever to come about - because any kid knows that it's about the master, not the tools.

---

### Post by rushmobius on 2009-04-14
I would argue it is both...

Give Mozart a tin can and ask him to perform a concerto...
Now give him a modern synth rig.

Tools are just that, the better the tools the easier it is to accomplish a task.

I can communicate with Morse code, but I find telephones, IM's and email a lot more convenient.

---

### Post by Simian Man on 2009-04-14
> **Vadi said:**
> RB and Banshee are the one most laughable examples ever to come about - because any kid knows that it's about the master, not the tools.

Yeah and a master will choose the right tools for the job :).  Choosing to write a music player in C is *not* choosing the right tool for the job.  Even if development is continuing on, one of the lead developers basically said the source was nearly unmaintainable.  I personally think the example is fairly apt.


[quote=Methuselah]You use terms like 'very unlikely' and 'probably' etc.
What is the harm in doing it and finding out for sure?
Someone has the time and desire and others are willing to test.
Is this a personal insult to someone?[/quote]
There's a little thing called [Amdahl's Law]("http://en.wikipedia.org/wiki/Amdahl%27s_law") that relates performance to the ratio that a speedup affects.  You can get better performance out of C and C++ than C#, but an application like Tomboy is going to be performance-bound by disc-access, the database library and the underlying widget library.  None of these things are being changed in the port so even if C++ were twice as fast as C#, the performance improvement would be negligible.

Sure no harm will come from anybody trying, but it's not like performance is something where you never know until you try - we do have tools to measure it.

---

### Post by gnomeuser on 2009-04-14
> **Simian Man said:**
> 
There's a little thing called [Amdahl's Law]("http://en.wikipedia.org/wiki/Amdahl%27s_law") that relates performance to the ratio that a speedup affects.  You can get better performance out of C and C++ than C#, but an application like Tomboy is going to be performance-bound by disc-access, the database library and the underlying widget library.  None of these things are being changed in the port so even if C++ were twice as fast as C#, the performance improvement would be negligible.

This is somewhat offtopic but since you mentioned Amdahl's Law, I figured you might enjoy this:

[Amdahl's Law in the multicore Era](http://www.youtube.com/watch?v=KfgWmQpzD74)

Aside that Fredrico Mena-Quintero had an interesting talk on this subject at the 2007 FOSDEM:

[Profiling Desktop Applications](http://ftp.belnet.be/mirrors/FOSDEM/2007/FOSDEM2007-ProfilingDesktopApplication.ogg).

Both should provide an understanding as to where optimization matters, on the hardware level and in software.

---

### Post by Vadi on 2009-04-15
Added a changelog to the OP. I'll be updating the PPA to new releases.

---

### Post by Methuselah on 2009-04-15
> 
There's a little thing called Amdahl's Law that relates performance to the ratio that a speedup affects. You can get better performance out of C and C++ than C#, but an application like Tomboy is going to be performance-bound by disc-access, the database library and the underlying widget library. None of these things are being changed in the port so even if C++ were twice as fast as C#, the performance improvement would be negligible.


Rght, the C++ version has the same underlying user interface and database libraries (which are themselves mostly written in C/C++).
So Mono is a largely extraneous additional layer of software that buys you ... garbage collection?

> 
Sure no harm will come from anybody trying, but it's not like performance is something where you never know until you try - we do have tools to measure it.


How does one measure performance without having anything to measure?
Sure, we can make reasonable estimates beforehand but none of the above argues against a C++ implementation.

---

### Post by Methuselah on 2009-04-15
> **bruce89 said:**
> 
Actually, GObject-Introspection and Vala might mean GNOME moves in another direction (Vala and JavaScript (perhaps)).

Interesting. This seems like a more natural evolution of the platform.

---

### Post by Mr. Picklesworth on 2009-04-15
GNOME has never used Mono. Popular applications that fit in the GNOME application have.
Big difference :)

---

### Post by gnomeuser on 2009-04-15
> **Mr. Picklesworth said:**
> GNOME has never used Mono. Popular applications that fit in the GNOME application have.
Big difference :)

Tomboy is part of GNOME, and several of the dependencies are listed as blessed dependencies for the platform. It is a legitimate part of the official platform.

---

### Post by Methuselah on 2009-04-15
> **Mr. Picklesworth said:**
> GNOME has never used Mono. Popular applications that fit in the GNOME application have.
Big difference :)

Not that big.
If applications that use Mono are included as standard components of the Gnome desktop then we have a Gnome dependency on Mono.
I certainly can't think of any one component of the Gnome Desktop that is 'the Gnome'.
Gnome is one and Gnome is all.

---

### Post by Methuselah on 2009-04-15
By the way:

[http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03096.pdf](http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03096.pdf)

Microsoft confidential

> 
**Evangelism is War**

Our mission is to establish Microsoft's platforms as the *de facto* standards throughout the computer industry. Our enemies are the vendors of platforms that compete with ours: Netscape, Sun, IBM, Oracle, Lotus, etc. The field of battle is the software industry. Success is measured in shipping applications. Every line of code that is written to our standards is a small victory; every line of code that is written to any other standard, is a small defeat. Total victory, for DRG, is a universal adoption of our standards by developers, as this is an important step towards total victory for Microsoft itself: "A computer on every desk and in every home, running Microsoft software."

Our weapons are psychological, economic, and political - not military. No one is forced to adopt our standards at the barrel of a gun. We only convince, not compel. Those who adopt our standards do so as a rational decision to serve their own ends, whatever those may be. It is our job to ensure that those choosing an operating system are presented with an overwhelming abundance of evidence and reasoned argument in favor or our standards - so overwhelming that the choice of our standards seems obvious, or (ideally) that the developer is not even aware that a decision was faced, and a choice made.


Seems this goal has largely been accomplished, except for a few enclaves of resistance.

Would I want open source software based on a platform engineered and 'intellectually owned' by a company with such a monstrous mission statement to proliferate on gnu-linux?

I'd have to be crazy to want that and once again question would have to question the motives of those who push the opposite.

So I'll readily admit that I cannot separate any (questionable) technical advantages of Mono from the strategic reasons for its existence and the potential dangers associated with its inextricable entanglement in the gnu-linux Desktop stack.

So yeah, I support efforts like Gnote that provide alternative implementations of useful applications.

---

### Post by Simian Man on 2009-04-15
> **Methuselah said:**
> *noise*

OK it's quite clear that you are a reactionary Mono-hater and are either unwilling or incapable of evaluating and discussing technology in a logical, productive manner.  So go ahead and refuse to use Mono apps, you're only hurting yourself and nobody's impressed with your dedication.

---

### Post by directhex on 2009-04-15
> **Simian Man said:**
> OK it's quite clear that you are a reactionary Mono-hater and are either unwilling or incapable of evaluating and discussing technology in a logical, productive manner.  So go ahead and refuse to use Mono apps, you're only hurting yourself and nobody's impressed with your dedication.

[http://www2.apebox.org/wordpress/rants/70/](http://www2.apebox.org/wordpress/rants/70/)

---

### Post by Methuselah on 2009-04-15
> **Simian Man said:**
> OK it's quite clear that you are a reactionary Mono-hater and are either unwilling or incapable of evaluating and discussing technology in a logical, productive manner.  So go ahead and refuse to use Mono apps, you're only hurting yourself and nobody's impressed with your dedication.

Sorry baby, you can call me names if you want but I'll not sweep real issues under the rug when they cannot be escaped.
And I'd hardly call my conclusions reactionary; I'd rather claim that your apt (self-chosen mind-you) nick-name might explain your willingness to be blind, deaf and dumb to obvious risks.

It's funny that the same people who will nitpick about which open source licenses are being violated by other *open source* projects seem to be much less cautious about dealing with 'intellectual property', created by the bastion of proprietary software.
Once again, I question your motives.

---

### Post by CraigPaleo on 2009-04-15
> **directhex said:**
> [http://www2.apebox.org/wordpress/rants/70/](http://www2.apebox.org/wordpress/rants/70/)

Great link! 

>  GNU is a vastly superior Free clone of UNIX. Re-using all the time effort and energy that went into the concepts behind UNIX is a good thing. To do it better and Freer is not a bad thing. Linux is a vastly superior Free replacement for the MINIX kernel. Anyone who suggests that there is nothing to be learnt from making superior Free versions of proprietary systems, yet uses GNU/Linux, is simply thick.What a beautiful comparison.

---

### Post by Methuselah on 2009-04-15
> 
To do it better and Freer is not a bad thing. Linux is a vastly superior Free replacement for the MINIX kernel. Anyone who suggests that there is nothing to be learnt from making superior Free versions of proprietary systems, yet uses GNU/Linux, is simply thick. 


This might have been a beautiful comparison in the context it was made but here it's arguing a strawman.
I don't remember anyone in this thread saying that Mono should not exist.
However, there are dangers associated with dependence on it and I'll argue unceasingly against that.

---

### Post by gnomeuser on 2009-04-15
> **Methuselah said:**
> By the way:

[http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03096.pdf](http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03096.pdf)


I see dates ranging from 1995 to 2000, you do realise those statements are 9 years old or more by now and that Microsoft like the rest of the world can adapt and change right?

Then I see an internal Microsoft elevator presentation, I would expect any company to use the wording they did. Microsoft is there to help Microsoft, big deal. 

Followed by pages and pages of black stuff.

Let's assume all of this is genuine, so what, Microsoft telling their employees to get excited about Microsoft technology. They are wise words in part, if we aren't excited about our platform how do we expect other people do be. Don't recommend alternatives, you work for Microsoft - totally understandable, I wouldn't expect to get a recommendation from anyone to go buy the competitions product. They even say that they can't force anyone to use their products, that doesn't mean they can't do their best to produce good stuff and market it well, which is what they are proposing - this is called PR and every company does it. 

So really, reading this (admittingly I have only glanced at this briefly so far read maybe the first 50 pages or so):

A) What is the problem with these statements, are you somehow not expecting Microsoft to promote Microsoft products?

B) Considering the age of these documents, and Microsofts recent invests and deals to promote openness, do you assume their business strategy hasn't changed the slightest since the late 90's despite their actions and public statements?

---

### Post by Vadi on 2009-04-15
> **Simian Man said:**
> OK it's quite clear that you are a reactionary Mono-hater and are either unwilling or incapable of evaluating and discussing technology in a logical, productive manner.  So go ahead and refuse to use Mono apps, you're only hurting yourself and nobody's impressed with your dedication.

Actually, it's quite clear that you didn't bother to read the persons argument and didn't even bother to refute any of his points - just called his point "noise" and applied characteristics to the person.

Your post didn't make a great impression or statement. Was it meant to do anything?

---

### Post by Methuselah on 2009-04-15
> **gnomeuser said:**
> I see dates ranging from 1995 to 2000, you do realise those statements are 9 years old or more by now and that Microsoft like the rest of the world can adapt and change right?

Then I see an internal Microsoft elevator presentation, I would expect any company to use the wording they did. Microsoft is there to help Microsoft, big deal. 

Followed by pages and pages of black stuff.

Let's assume all of this is genuine, so what, Microsoft telling their employees to get excited about Microsoft technology. They are wise words in part, if we aren't excited about our platform how do we expect other people do be. Don't recommend alternatives, you work for Microsoft - totally understandable, I wouldn't expect to get a recommendation from anyone to go buy the competitions product. They even say that they can't force anyone to use their products, that doesn't mean they can't do their best to produce good stuff and market it well, which is what they are proposing - this is called PR and every company does it. 

So really, reading this (admittingly I have only glanced at this briefly so far read maybe the first 50 pages or so):

A) What is the problem with these statements, are you somehow not expecting Microsoft to promote Microsoft products?

B) Considering the age of these documents, and Microsofts recent invests and deals to promote openness, do you assume their business strategy hasn't changed the slightest since the late 90's despite their actions and public statements?

The documents are genuine and are from the antitrust cases at the close of the 20th. The time frame is expected and I thought that this would be obvious from the URL.

What were their actions and public statements around the time these documents were circulated internally?
Were they saying these things publicly?
You yourself suggest that what they say internally is unlikely to harmonize with the external PR.

They should have changed much more than they have.
Microsoft was convicted of anti-competitive practices and really got away with a slap on the wrist.
The bones they have been throwing in the name of openness seems at least partially related to lawsuits that the EU has been slapping them with for the same reason they were sued in the USA a decade ago.

Listen, Microsoft clearly has done a fine job of promoting its products since we are stuck with them almost everywhere.
The question is why we would want free open source software intended for gnu-linux to have gratuitous dependencies on Microsoft IP?
I say gratuitous because in the case of Tomboy it seems the .NET implementation buys us garbage collection and additional layers of bindings to underlying C/C++ toolkits.
<facetious>
There are any number of frameworks that could introduce such overhead if one desires it. 
</facetious>

---

### Post by Simian Man on 2009-04-15
> **Vadi said:**
> Actually, it's quite clear that you didn't bother to read the persons argument and didn't even bother to refute any of his points - just called his point "noise" and applied characteristics to the person.

His "argument" is nothing more than unreasoned FUD.  C# is an ECMA standard and Mono and GTK# are free software.  When the argument was about actual technology, it was interesting, but I'm not going to lower myself to trying to refute arguments that are completely impervious to logic - it is a waste of time.

It's also obvious from Methuseleh's last post that he hasn't even ever seriously used C# if he thinks it just buys us garbage collection :).

---

### Post by Methuselah on 2009-04-15
> **Simian Man said:**
> His "argument" is nothing more than unreasoned FUD.  C# is an ECMA standard and Mono and GTK# are free software.  When the argument was about actual technology, it was interesting, but I'm not going to lower myself to trying to refute arguments that are completely impervious to logic - it is a waste of time.

It's also obvious from Methuseleh's last post that he hasn't even ever seriously used C# if he thinks it just buys us garbage collection :).

AFAIK, being an ECMA standard does not guarantee patent indemnity. 
You can correct me, with proof, if I'm wrong.

And note, that I didn't say C# buys you garbage collection I said .NET did.
C# buys you a little different syntax, but you get can C# syntax without .NET.

I'd laugh when I'm right about this stuff ... if it mightn't affect me too.

---

### Post by Vadi on 2009-04-15
> **Simian Man said:**
> His "argument" is nothing more than unreasoned FUD.  C# is an ECMA standard and Mono and GTK# are free software.  When the argument was about actual technology, it was interesting, but I'm not going to lower myself to trying to refute arguments that are completely impervious to logic - it is a waste of time.

It's also obvious from Methuseleh's last post that he hasn't even ever seriously used C# if he thinks it just buys us garbage collection :).

That's understandable. But do realize that unlike C, C++ - only two groups are leading this development, with the linux version lagging behind and as I understand, having no say in the platforms direction.

But yes, C# itself is open-source, ecma'd, and nice. Hopefully it also doesn't have it's isNot operator patented though ;) (joking, but it is a reason for worrying.)

---

### Post by Methuselah on 2009-04-15
> **Vadi said:**
> That's understandable. But do realize that unlike C, C++ - only two groups are leading this development, with the linux version lagging behind and as I understand, having no say in the platforms direction.

But yes, C# itself is open-source, ecma'd, and nice. Hopefully it also doesn't have it's isNot operator patented though ;) (joking, but it is a reason for worrying.)

Well said.

But I'm not joking and I don't care what I'm accused of for having a contrary view.
My thoughts are based on both technical need and strategic implications.
The two cannot be divorced as I can guarantee they were wed on the day MS decided to 'open' .NET.

I would be only a bit more annoyed if several Gnome applications started needing Wine + Samba + Microsoft.NET to run.
While the above are useful in themselves, that dependence is unecessary for a gnu-linux desktop.

Gnote/Tomboy is a good test of one possible migration path away from Mono.
But there are other options that are also more mature than Mono is.

---

### Post by zekopeko on 2009-04-15
> **Vadi said:**
> That's understandable. But do realize that unlike C, C++ - only two groups are leading this development, with the linux version lagging behind and as I understand, having no say in the platforms direction.

But yes, C# itself is open-source, ecma'd, and nice. Hopefully it also doesn't have it's isNot operator patented though ;) (joking, but it is a reason for worrying.)

yet again you didn't read Miguel de Icaza's comment on Hubs site.
He gave the names for half a dozen different companies that contributed to the Mono stack.

Since Mono is open source it can be taken and forked so your repeated statements that only 2 entities are controlling the mono stack is flawed. it's like saying that firefox is controlled by only Mozilla while ignoring the fact that there are many products out there that use Mozilla's code since it's open source. just because one company is in the spotlight for backing the project doesn't mean that the project is controlled.

And as far as i understand saying that c/c++ are not controlled fly in the way of logic. what guaranties do you have that there isn't a patent on some part of c/c++? just because somebody didn't sue doesn't mean that there isn't a patent out there that could kill c/c++. 
c# is just a language. mono is the implementation of that language.
c/c++ are also ISO and ECMA standards as far as i know just like c#. using mono is the same as using the linux kernel. there is always a risk for patent infringement since it's the whole patent system is so broken in america.

---

### Post by zekopeko on 2009-04-15
> **Methuselah said:**
> 
I would be only a bit more annoyed if several Gnome applications started needing Wine + Samba + Microsoft.NET to run.
While the above are useful in themselves, that dependence is unecessary for a gnu-linux desktop.

Gnote/Tomboy is a good test of one possible migration path away from Mono.
But there are other options that are also more mature than Mono is.

isn't samba a GNU project implementing microsoft's network protocols for file/printer/user-managment sharing?

You are missing one big strategic advantage of mono. lower entry barrier for windows developers. i would love if somebody could port Paint.Net to linux. the only legal considered is the winforms part of the program that might be infringing on microsoft's patents. but that could be fixed by working with microsoft to release those part with an opensource license.

---

### Post by Methuselah on 2009-04-15
> **zekopeko said:**
> isn't samba a GNU project implementing microsoft's network protocols for file/printer/user-managment sharing?


Yes...just saying that I wouldn't want the overhead of replicating a windows desktop just to get a gnu-linux desktop to work properly.

> 
You are missing one big strategic advantage of mono. lower entry barrier for windows developers. i would love if somebody could port Paint.Net to linux. the only legal considered is the winforms part of the program that might be infringing on microsoft's patents. but that could be fixed by working with microsoft to release those part with an opensource license.

There is some merit there, but as you said, it's use for porting is limited because if it's to be somewhat safe it has to be missing frequently used components anyway.
As a compatibility layer a la Wine I'm all for it, those things are convenient and optional niceties.

If you want to develop with Mono, your effort. There's even winelib for gnu-linux apps too if you're inclned to also use the Win32 API everywhere.
But reading people bash a C++ port of a Gnome application had me looking backwards at the grooves on my cerebrum.

---

### Post by Vadi on 2009-04-15
I did read Miguels comment.

The companies listed aren't exactly spearheading development. From what I see, they just contributed misc. items. Nothing that defines the direction of Mono. Same with Microsoft and C# - from what I see, it goes where Microsoft says it will. But yes, the Mono stack did receive contributions from other non-Novell sources.

Miguel is also known to be way more attracted to his C# and all this nice development stuff than caring about it working on the Linux platform.

**Edit**: I totally agree with the lowered barried for Windows developers for Mono. That one thing which, even lagging behind Microsofts implementation, it does better than other solutions. For anything else - hm, Vala would rock it once mature. C# syntax, C speed - heaven match!

---

### Post by zekopeko on 2009-04-15
> **Methuselah said:**
> Yes...just saying that I wouldn't want the overhead of replicating a windows desktop just to get a gnu-linux desktop to work properly.



There is some merit there, but as you said, it's use for porting is limited because if it's to be somewhat safe it has to be missing frequently used components anyway.
As a compatibility layer a la Wine I'm all for it, those things are convenient and optional niceties.

If you want to develop with Mono, your effort. There's even winelib for gnu-linux apps too if you're inclned to also use the Win32 API everywhere.
But reading people bash a C++ port of a Gnome application had me looking backwards at the grooves on my cerebrum.

wouldn't using wine be more of a threat then using mono? wine is recreating the whole windows system on linux. .NET is only a development framework that sits on top of win32api. but i don't hear any rants against using wine.

vala is nice from the description but mono is cross-platform. consider how easy it was for banshee to port to mac (and i hope windows soon). i get the feeling that mono is something like java done right.

---

### Post by Vadi on 2009-04-15
*cough* C, Vala, C++ are cross-platform too.

Only cross-platform enviroment done right, surprisingly enough, is Flash. But that is too offtopic ;)

---

### Post by zekopeko on 2009-04-15
> **Vadi said:**
> *cough* C, Vala, C++ are cross-platform too.

Only cross-platform enviroment done right, surprisingly enough, is Flash. But that is too offtopic ;)

i was talking about the framework not a specific language. i'm guessing that a c app has much more problems when being ported to different platform then say c# or python.

---

### Post by Vadi on 2009-04-15
Debatable - because it would be one binary, all ready to go. python and c# would require runtime stuff, and that means tinkering with the installers, bloating up the size, messing with shell scripts or embedment and etc.

---

### Post by directhex on 2009-04-15
> **Vadi said:**
> Debatable - because it would be one binary, all ready to go. python and c# would require runtime stuff, and that means tinkering with the installers, bloating up the size, messing with shell scripts or embedment and etc.

The "size bloat" argument is bunk. The numbers prove the reverse.

---

### Post by Vadi on 2009-04-15
Okay, so lets remove that. The extra fuss associated still stands.

---

### Post by directhex on 2009-04-15
> **Vadi said:**
> Okay, so lets remove that. The extra fuss associated still stands.

To a degree, sure..... Assuming you're fine with the GTK+ runtime requirement (or lots of static compilation), or that your installer is incompetent (plenty of apps, e.g. commercial games, bundle things like Python, and soon will be bundling Mono). If C is so cross-platform, why no RHythmBox (or Gnote, even) for Windows?

You can play these hypotheticals all day, but when all's said & done, all that matters is quality Linux desktops. The rest is noise.

---

### Post by Vadi on 2009-04-15
> why no RHythmBox (or Gnote, even) for Windows?

...

all that matters is quality Linux desktops. The rest is noise.

You answered the question and I agree on the second point. Which is why I'm favourable to Gnote too - normally, a reimplementation of an existing thing would sound stupid. But Gnote starts in under a second while the mono thing takes 3 to initialize (number might be different for you, but others have reported faster startup too), and that makes me a happier linux user.

---

### Post by zekopeko on 2009-04-15
> **Vadi said:**
> Debatable - because it would be one binary, all ready to go. python and c# would require runtime stuff, and that means tinkering with the installers, bloating up the size, messing with shell scripts or embedment and etc.

the .NET framework is installed on Vista and up. so that point is mostly moot. most game that use 3D bundle directx and the microsoft c++ redistributable.

and yet again. second life and unity use mono as the scripting engine  in their games. 
i don't see microsoft coming at their door. if companies use opensource commercially the you really have to ask yourself is there really a problem with mono or am i just being a prick against other peoples work just out of spite.

again, i don't see any thread about wine being evil. and wine's code base is used in commercial products.

worst case scenario is that microsoft comes after mono and they have to work around some things. and then the OIN network slam microsoft with various patent infringement law suites and legal Armageddon ensues. which costs microsoft billions of dollars and ends them as a company. and after a few years nobody can open their word documents since the support for them went it MS.
the end.

---

### Post by zekopeko on 2009-04-15
> **Vadi said:**
> You answered the question and I agree on the second point. Which is why I'm favourable to Gnote too - normally, a reimplementation of an existing thing would sound stupid. But Gnote starts in under a second while the mono thing takes 3 to initialize (number might be different for you, but others have reported faster startup too), and that makes me a happier linux user.

mono is getting some awesome improvements as of late. and really 3 seconds? imagine when one day every computer get's and SSD. initialization is going to be a thing of the past for such small apps. and the only thing developers are going to care is how to write a quality app in as little time as possible. enter mono.

---

### Post by directhex on 2009-04-15
There's always AOT if you want to speed up app startup (at the expense of performance)

---

### Post by SKLP on 2009-04-15
> **Vadi said:**
> Only cross-platform enviroment done right, surprisingly enough, is Flash. But that is too offtopic ;)
Done _RIGHT_, you say?!
It is so bad its not even funny... the Windows version is decent, mac and linux versions eat cpu compared to it and the linux version is somewhat unstable

Flash is not cross platform done right, and there is nothing about flash that I would consider done right...


(everything IMO, of course )

---

### Post by directhex on 2009-04-15
> **SKLP said:**
> Done _RIGHT_, you say?!
It is so bad its not even funny... the Windows version is decent, mac and linux versions eat cpu compared to it and the linux version is somewhat unstable

Flash is not cross platform done right, and there is nothing about flash that I would consider done right...


(everything IMO, of course )

I didn't have the energy to dispute the "yay for proprietary Adobe crap" bit, but yeah, all of the above

---

### Post by bruce89 on 2009-04-15
> **gnomeuser said:**
> 8 Months of development gives us:

[...]

This is what 3 months of Banshee development gets you:

[blah]



Use Banshee then, but no need to preach it.

---

### Post by zekopeko on 2009-04-15
> **bruce89 said:**
> Use Banshee then, but no need to preach it.

he isn't preaching. he's stating the facts.

---

### Post by Vadi on 2009-04-15
Unity is Windows-only (horray.), and the majority of the worlds home computer users are still on Windows XP.

---

### Post by zekopeko on 2009-04-15
> **Vadi said:**
> Unity is Windows-only (horray.), and the majority of the worlds home computer users are still on Windows XP.

yes,hooray for not having an integrated solution for developing games on linux!!!! oh wait...

---

### Post by ghindo on 2009-04-15
I wonder if these sort of discussions ensue if you rewrite other software in different languages.

---

### Post by Vadi on 2009-04-15
> **zekopeko said:**
> yes,hooray for not having an integrated solution for developing games on linux!!!! oh wait...

Yeah, that's what Mono is all about, no? :)

---

### Post by Vadi on 2009-04-16
Apparently Mono isn't about an easy integrated solution for developing games on linux but windows-only. Okay, that helps.

Anyway, Gnote 0.1.2 is up - see [changelog]("http://www.figuiere.net/hub/blog/?2009/04/15/660-gnote-012").

---

### Post by directhex on 2009-04-16
> **Vadi said:**
> Apparently Mono isn't about an easy integrated solution for developing games on linux but windows-only. Okay, that helps.

Your claimed position would be helped if you didn't make up things that are a load of crap, y'know.

---

### Post by Vadi on 2009-04-16
What? Nobody refuted the point, so it stands. You didn't either.

---

### Post by directhex on 2009-04-16
> **Vadi said:**
> What? Nobody refuted the point, so it stands. You didn't either.

If I don't take time out to refute flat-earthers on an individual basis, it doesn't make them right either. And there's a lovely concept that the anti-Mono crowd (which you've demonstrated you form part of) don't comprehend, called "burden of proof"

Unity3D is a commercial development product for Mac (and now Windows) based on Mono. That doesn't mean it cannot be ported to Linux, it means it hasn't - any more than the absence of ANY app on a given OS based on Free Software is proof of any insidiousness. Let's re-apply your twisted logic to a similar case:

$product_using_free_software (Civilization 4) is not available on $os (Linux) which proves that $free_software (Python) is useless for games.

You're simply talking crap, it's painful to try and refute. Argue based on reality, or not at all.

Now, is Mono "an easy integrated solution for developing games on linux"? Not in isolation any more than, I dunno, GTKmm. With the required libraries alongside it, then it can be, yes. A sprite library, or OpenGL binding, or full 3D engine like Ogre? Yes.

---

### Post by Vadi on 2009-04-16
Okay, lets look at reality. Unity3D does not run on Linux. It is made on a supposedly cross-platform Mono framework.

Miguel de Icaza couldn't care less either; all he is happy about is that it's made on Mono. 

Does this help the Linux desktop? Not a single bit.

Now look at flash - 99% of flash-based games are compatible with Linux. Does that help the Linux desktop? Yes, because $unhappy_user can install Linux, flash, and play their games just as they were.

---

### Post by Methuselah on 2009-04-16
All evidence points to Mono being a rather redundant framework for LINUX development.
And I'm beginning to think that some of the most vociferous supporters [Microsoft Directx and Mono Man (Mono = Monkey)] might be evangelical shills here and elsewhere

Thanks maintaining the Gnote PPA Vadi!

---

### Post by directhex on 2009-04-16
> **Vadi said:**
> Okay, lets look at reality. Unity3D does not run on Linux. It is made on a supposedly cross-platform Mono framework.

Made WITH. It's an important distinction. Mono forms PART of Unity, along with deep-down changes to the JIT. If Unity were purely on TOP of Mono, then it'd be cross-platform.

> Miguel de Icaza couldn't care less either; all he is happy about is that it's made on Mono.

People have different feelings about their software being used in commercial projects. BSD-like licenses are a sign that the author is fine with it.

> Does this help the Linux desktop? Not a single bit.

Unity? Correct - excluding improvements to the core Mono framework submitted by Unity devs.

> Now look at flash - 99% of flash-based games are compatible with Linux. Does that help the Linux desktop? Yes, because $unhappy_user can install Linux, flash, and play their games just as they were.

How many years did it take for an AMD64 release? Hint, there's still no stable release, just a beta. That's the problem with relying on commercial vendors - you're at their mercy when it comes to doing anything "odd" like running a CPU architecture from 2003. How long did Flash 9 take? How long did Flash 8 take (hint, it didn't)

> **Methuselah said:**
> All evidence points to Mono being a rather redundant framework for LINUX development.
And I'm beginning to think that some of the most vociferous supporters [Microsoft Directx and Mono Man (Mono = Monkey)] might be evangelical shills here and elsewhere

Thanks maintaining the Gnote PPA Vadi!

Shilling for whom, specifically?

---

### Post by zekopeko on 2009-04-16
> **Vadi said:**
> Okay, lets look at reality. Unity3D does not run on Linux. It is made on a supposedly cross-platform Mono framework.

Miguel de Icaza couldn't care less either; all he is happy about is that it's made on Mono. 

Does this help the Linux desktop? Not a single bit.

Now look at flash - 99% of flash-based games are compatible with Linux. Does that help the Linux desktop? Yes, because $unhappy_user can install Linux, flash, and play their games just as they were.

I have to agree with directhex that you really ignore reality as you see fit. "Supposedly cross-platform Mono"... i guess you missed various installers/tarballs for mono on their page.

now unity3D isn't available for linux now but i wonder would it be harder or easier to port it to linux using c/c++ or mono? consider that they built the mac version first and then the windows version.
i'm guessing that it's easier to port something from mac to linux then from windows to linux.

Miguel de Icaza is a programmer with only one agenda: empower open source development with new tools. he's happy that people use mono because it means that if you have more people invested in a project with commercial interests you are more likely to get help maintaining the code base. and it goes against your whole "mono is evil" argument since commercial invested entities are going to protect their product and by extension mono.

on the flash issue. flash is a horrible citizen on the linux desktop. far worst then say moonlight. what does flash bring to the linux desktop? well by my experience: crashes, slowdown, 100% CPU usage etc.
and btw what does Gnote bring to the desktop? flash is closed source so there are project to implement it in open source. that a valid reason for that. but what's Gnote's? faster startup time? 3 seconds boost is worth it? higher barrier for ex-windows developers to contribute code to an already existing project written in c#? i don't get it.

---

### Post by Methuselah on 2009-04-16
> 
Shilling for whom, specifically?


That's not a question I'm really concerned with.
It's just that it's quite unnatural for an immature development framework to have such staunch defenders unless they have some connection to it.
I'm pretty sure I'm right about this but as I do not want to risk derailing this thread, I'll not say anything more.

---

### Post by zekopeko on 2009-04-16
> **Methuselah said:**
> That's not a question I'm really concerned with.
It's just that it's quite unnatural for an immature development framework to have such staunch defenders unless they have some connection to it.
I'm pretty sure I'm right about this but as I do not want to risk derailing this thread, I'll not say anything more.

so lets apply reverse logic. directhex is invested in mono so he's going to protect. you are not invested in mono yet your are attacking it? /me confused. your are not using it yet you are attacking it.

And please don't call mono an immature dev framework. it's been present from like 2003/2004 (have to look up the exact year). and judging from Gnome Do i would have to say that mono is the most advanced framework on the KDE/Gnome platform except KDE/Qt.

---

### Post by Simian Man on 2009-04-16
> **Methuselah said:**
> All evidence points to Mono being a rather redundant framework for LINUX development.
And I'm beginning to think that some of the most vociferous supporters [Microsoft Directx and Mono Man (Mono = Monkey)] might be evangelical shills here and elsewhere


OK now I get then name insult from earlier.  I can assure you that Simian has been a handle of mine since before Mono (or .NET) even existed :).  If you think I am a Microsoft employee who pretends to be a Linux user and argues in favor of Mono on various Linux user forums in order to bring about MS-superiority, then you are even more on the outskirts of sanity than I though.

---

### Post by Methuselah on 2009-04-16
> **Simian Man said:**
> OK now I get then name insult from earlier.  I can assure you that Simian has been a handle of mine since before Mono (or .NET) even existed :).  If you think I am a Microsoft employee who pretends to be a Linux user and argues in favor of Mono on various Linux user forums in order to bring about MS-superiority, then you are even more on the outskirts of sanity than I though.

No, the 'previous insult' was a reference to the 'Three wise moneys' and a retort to your previous rude response:
[http://en.wikipedia.org/wiki/Three_wise_monkeys](http://en.wikipedia.org/wiki/Three_wise_monkeys)
I thought it was pretty good too :D

This one was in reference to the Mono monkey logo.
(sorry your handle is too rich in applications)

Anyway, we have veterinarians, I guess you guys have 'humanitarians'.
I accept the diagnosis as insane.

---

### Post by Vadi on 2009-04-16
Great to know that empowering open-source development means leaving Linux out as it is fit.

For the record, I have nothing against commercialization or closed-source - but obviously using a closed-source product would be much less secure than using one which is a re-implementation.

So where are we at? Oh yes, Unity3D not running on Linux, Gnote being faster, GPLing of an LGPL program being perfectly legal and Mono lagging behind .NET framework.

I too was estatic when first realizing what Mono is - a united framework with an IDE for Linux, great C# syntax, easy tool to help Windows and CS students get started on Linux. Their whole addin idea is great, and looking at its success, I'd assume easy to add to the program.

Then dissapointments like Unity3D, microsoft-linux related patent issues, the lack of a clear future - 80% of mono's work is re-implementing what microsoft is doing, and they are still lagging behind with no sign of anyone but microsoft spearheading the development. The mono vm having [less-than-impressive]("http://code.google.com/p/vala-benchmarks/wiki/BenchResults") benchmarks and the fact that Mono is unusable on most of the worlds computers (read: winxp, and it was a pita to install that no common user would go gladly) made the light fade away. Everyone has different values though, and I guess that not everybody values these deficiencies as much.


So that's why I personally support alternative programs if they're of equal functionality. The fact that Miguels goal is to create an open development framework for all developers doesn't help me a single bit - I'm a user, and look at the results of it. Faster and smaller programs definitely make me happier.

---

### Post by directhex on 2009-04-16
There's no point itemising the layers of hypocrisy is there?

---

### Post by Vadi on 2009-04-16
There's no point in posting without a purpose either, or failing to read the original notice that all mono-related and off-topic discussions are welcome at the authors blog.

Thanks!

---

### Post by bapoumba on 2009-04-16
Please everyone, keep the discussion constructive, thanks.

---

### Post by zekopeko on 2009-04-16
> **Vadi said:**
> There's no point in posting without a purpose either, or failing to read the original notice that all mono-related and off-topic discussions are welcome at the authors blog.

Thanks!

you must be kidding. why would i want to post at the authors blog where he has all the control of looking and/or deleting comments?
the comments section of a blog isn't a really compelling forum for expressing one's opinion.

---

### Post by Vadi on 2009-04-16
Looking at the fuss raised there, I don't see any comments having been deleted. Feel free to try it and let us know!

---

### Post by zekopeko on 2009-04-16
> **Vadi said:**
> Great to know that empowering open-source development means leaving Linux out as it is fit.

For the record, I have nothing against commercialization or closed-source - but obviously using a closed-source product would be much less secure than using one which is a re-implementation.

So where are we at? Oh yes, Unity3D not running on Linux, Gnote being faster, GPLing of an LGPL program being perfectly legal and Mono lagging behind .NET framework.

I too was estatic when first realizing what Mono is - a united framework with an IDE for Linux, great C# syntax, easy tool to help Windows and CS students get started on Linux. Their whole addin idea is great, and looking at its success, I'd assume easy to add to the program.

Then dissapointments like Unity3D, microsoft-linux related patent issues, the lack of a clear future - 80% of mono's work is re-implementing what microsoft is doing, and they are still lagging behind with no sign of anyone but microsoft spearheading the development. The mono vm having [less-than-impressive]("http://code.google.com/p/vala-benchmarks/wiki/BenchResults") benchmarks and the fact that Mono is unusable on most of the worlds computers (read: winxp, and it was a pita to install that no common user would go gladly) made the light fade away. Everyone has different values though, and I guess that not everybody values these deficiencies as much.


So that's why I personally support alternative programs if they're of equal functionality. The fact that Miguels goal is to create an open development framework for all developers doesn't help me a single bit - I'm a user, and look at the results of it. Faster and smaller programs definitely make me happier.

i'm confused. you say that mono is a great tool, point out all of the nice things it brings and then going on a rant that is hypocritical. Unity3D was just my example of commercial usage of mono that i know of that's not coming from novell. and yet again i'will point out that a company that wants to make money is using this "patent hellhole".

and about the whole MS-Linux patent situation. How can you be so blind? Mono isn't the only part of linux that can be targeted for lawsuits. Almost every part of the linux ecosystem could be targeted. even Gnote and by proxy Tomboy. not because of the language used but simply by implementing some idea from a patent about note keeping programs. 

Mono is lagging behind microsoft only in some parts. part that are of interest are being worked on. and don't forget mono specific bits that have nothing to do with .net. 

On the benchmark thingy. that's so old it's not even funny. mono is now at 2.4 and there it's 1.9.1 . Mono isn't for every application out there. it has it's uses depending under what constraints are you working (time,money,features). I don't see people implementing the linux kernel in c# because c  is better suited for that. but creating a note taking app in c# makes sense since you are not building speed-critial application.

And why does mono make you happy in the 4th paragraph as a developer (i doubt a user cares what and IDE is) and then in the last paragraph you say that you are simply a user?
DirectHex has you nailed spot on. you are are hypocrite.

---

### Post by zekopeko on 2009-04-16
> **Vadi said:**
> Looking at the fuss raised there, I don't see any comments having been deleted. Feel free to try it and let us know!

doesn't maatter. comment areas are for short snippet of thought on the article. forums are for discussion. btw hub closed comments on one of the blog posts.

---

### Post by Vadi on 2009-04-16
Wow, accusations of hypocrism now? I understand you're a fan of Mono, but come on - be civil.

I am a notes user. When doing other programs, I am a developer. Guess what - these two can coexist. Should I explain how? (hint: I don't code on tomboy.)

I don't consider your arguments to be worthy, so they, for me, still stand. Save for the benchmarks one - only one where you had a valid argument. But looking at tomboy vs gnote start speed, that point is refuted.

---

### Post by CraigPaleo on 2009-04-16
> **bapoumba said:**
> Please everyone, keep the discussion constructive, thanks.

Eh hem *clearing throat*

---

### Post by gnomeuser on 2009-04-16
> **zekopeko said:**
> 
Mono is lagging behind microsoft only in some parts. part that are of interest are being worked on. and don't forget mono specific bits that have nothing to do with .net. 


This generally line of argument also totally omits the places Mono is innovating in .NET such as Mono.SIMD and the support for 64 bit arrays. These are bits that aren't in the Microsoft reference implementation of .NET and bits that the Mono community once it's polished can take to ECMA and have put into the standard.

Yes there are places Mono lacks behind currently, for lack of manpower and community interest. These areas will be filled in once there is a business reason for Novell to do so. Remembering that MOMA output from their clients generally determine which APIs are high priority to get done for them outside of their person usage. 

There is also community interest, or other corporate interests like Mainsoft (and others) has done with large parts of Mono for a while. They needed something, so they implemented it and supported it. 

Mono is a community project, it is Open Source so everyone has the chance to come and help instead of whining that it's an arms race. We are implementing a standard, if something you need isn't there yet and nobody is doing it for you (for free might you), you can do it yourself.

We can get there faster if people stop whining and start helping, or at the very least understand that every minute someone like Miguel or directhex spends answering the same baseless FUD is a minute that person is not spending working on Mono (or any software project for that matter). It is a minute regardless of how you look at it that does nothing but hurt Open Source.

---

### Post by zekopeko on 2009-04-16
> **Vadi said:**
> Wow, accusations of hypocrism now? I understand you're a fan of Mono, but come on - be civil.

I am a notes user. When doing other programs, I am a developer. Guess what - these two can coexist. Should I explain how? (hint: I don't code on tomboy.)

I don't consider your arguments to be worthy, so they, for me, still stand. Save for the benchmarks one - only one where you had a valid argument. But looking at tomboy vs gnote start speed, that point is refuted.

since when is hypocrisy an insult? i'm simply stating the obvious.
from a users perspective mono brings nothing if it's not implemented in an application. tomboy being one.
And sure dev/user duality has to coexist. so what's your problem with tomboy then from a user perspective? once it start it's still as fast as any other implementation for a notes app.
see why i call you dishonest and a hypocrite?
the only reason you have something against tomboy is because it's written in c#/mono. gnote is a copy&paste job done in c++ for some (to me) unknown reason. at least say that you don't like mono because you are a follower of a vocal minority who exists in a perpetual  state of denial and hypocrisy basing that state on nothing but pure ignorance.

btw you haven't responded to any of my conclusions that if mono is a patent minefield then so is , wine, the linux kernel, samba or any other of the 1000's FLOSS app out there. if you want to have any arguments left standing then please explain why is mono more dangerous than any other FLOSS app patent wise?

---

### Post by saulgoode on 2009-04-16
> **gnomeuser said:**
> Mono is a community project, ...
No, it is not. Novell owns the trademarks for Mono and has ultimate say in decisions made by the project. Community projects permit the community to make decisions and the trademarks are not held by a for-profit company. Ubuntu is not a community project, Slackware is not a community project, and Qt, BitTorrent, and MySQL are not community projects. That is not to say that these projects are "evil" in any way, or that people shouldn't use or contribute to them; but claiming that Mono is a community project demeans the nature of true community projects such as Debian, GIMP, Perl, and GNOME where governance is in actuality controlled by the community.

> **gnomeuser said:**
> ... it is Open Source so everyone has the chance to come and help instead of whining that it's an arms race.
But aren't you "whining" about the Open Source Gnotes project? How do you justify that?

> **zekopeko said:**
> btw you haven't responded to any of my conclusions that if mono is a patent minefield then so is , wine, the linux kernel, samba or any other of the 1000's FLOSS app out there. if you want to have any arguments left standing then please explain why is mono more dangerous than any other FLOSS app patent wise?
If you care to address the question I posed in [this post]("http://ubuntuforums.org/showpost.php?p=7037311&postcount=23"), I shall be glad to share my thoughts on your conclusions.

---

### Post by gnomeuser on 2009-04-17
> **saulgoode said:**
> No, it is not. Novell owns the trademarks for Mono and has ultimate say in decisions made by the project. Community projects permit the community to make decisions and the trademarks are not held by a for-profit company. Ubuntu is not a community project, Slackware is not a community project, and Qt, BitTorrent, and MySQL are not community projects. That is not to say that these projects are "evil" in any way, or that people shouldn't use or contribute to them; but claiming that Mono is a community project demeans the nature of true community projects such as Debian, GIMP, Perl, and GNOME where governance is in actuality controlled by the community.


No that is just plain falsehoods. Mono is a true community project. Novell doesn't even require copyright assignment for the code you contribute, the only rules that exist for contributing involve having looked at the source code for Microsoft' .NET implementation. Novell nor anyone will stop you from developing any part of Mono you like. There are in fact companies like Mainsoft doing just that and they have done that for years.

> 
But aren't you "whining" about the Open Source Gnotes project? How do you justify that?


Name me one place in which I said anything about GNotes in this debate. There simply isn't one, I have only been commenting after this turned into the typical Mono is evil fest of lies and character assassination. 

> 
If you care to address the question I posed in [this post]("http://ubuntuforums.org/showpost.php?p=7037311&postcount=23"), I shall be glad to share my thoughts on your conclusions.

I don't see the point, you know how ECMA standardization works or can research it, you can also go read the list of specifications under the OSP. 

Considering your dishonesty in the reply above I predict that you will find something in this reply to hang on to regardless, thus retaining your opinion that the slightest hole in my knowledge or anyones makes your entire theory truthful. You may like to look into the tactics used by creationists arguing against evolution - it is the same approach.

---

### Post by Vadi on 2009-04-17
Look at this list: [http://www.ecma-international.org/publications/standards/Standardwithdrawn.htm](http://www.ecma-international.org/publications/standards/Standardwithdrawn.htm)

That's a list of standards that were withdrawn by ECMA.

Now, read this: [http://www.ecma-international.org/publications/files/ECMA-ST/Ecma%20PATENT/ECMA-334%20&%20335/2001ga-123%20&%202002ga-003.pdf](http://www.ecma-international.org/publications/files/ECMA-ST/Ecma%20PATENT/ECMA-334%20&%20335/2001ga-123%20&%202002ga-003.pdf) ['This declaration remains valid only as long as the corresponding ECMA Standard remains valid.']

Same letter is done below by HP.

Huh? C# is patented, and should ECMA drop the standard like it already did with that huge list above, Microsoft and HP are going to withdraw their "licenses on reasonable terms and conditions, for its patent(s) that are necessary or the implementation of the ECMA standard."

The patent side of mono wasn't really too interesting to me until now... what are their plans to do once ecma withdraws (as it has with the huge list already)?

Need to find out the terms of the license that MS & HP gave to Novell for implementing C#. A license for implementing a standard. hehe.

---

### Post by alternatealias on 2009-04-17
> **saulgoode said:**
> You should perhaps read the terms of version 2.1 of the Lesser General Public License sometime, in particular the first sentence of Section 3.

Earlier in this thread it was mentioned that Tomboy is under the LGPLv2.1-only license.

This means that you cannot change the license to GPLv2-or-later, thus cannot get to GPLv3.

The only GPL license that the GNote guy could legally choose to use is GPLv2.


You'd be correct if Tomboy was licensed under LGPLv2.1-or-later, however.

---

### Post by zekopeko on 2009-04-17
> **alternatealias said:**
> Earlier in this thread it was mentioned that Tomboy is under the LGPLv2.1-only license.

This means that you cannot change the license to GPLv2-or-later, thus cannot get to GPLv3.

The only GPL license that the GNote guy could legally choose to use is GPLv2.


You'd be correct if Tomboy was licensed under LGPLv2.1-or-later, however.

well that part i a little vague. on tomboys page it says that the project is under LGPL and links to LGPL 3. but in svn it's LGPL2.1. and i don't see any reference to the only part.

---

### Post by zekopeko on 2009-04-17
> **Vadi said:**
> Look at this list: [http://www.ecma-international.org/publications/standards/Standardwithdrawn.htm](http://www.ecma-international.org/publications/standards/Standardwithdrawn.htm)

That's a list of standards that were withdrawn by ECMA.

Now, read this: [http://www.ecma-international.org/publications/files/ECMA-ST/Ecma%20PATENT/ECMA-334%20&%20335/2001ga-123%20&%202002ga-003.pdf](http://www.ecma-international.org/publications/files/ECMA-ST/Ecma%20PATENT/ECMA-334%20&%20335/2001ga-123%20&%202002ga-003.pdf) ['This declaration remains valid only as long as the corresponding ECMA Standard remains valid.']

Same letter is done below by HP.

Huh? C# is patented, and should ECMA drop the standard like it already did with that huge list above, Microsoft and HP are going to withdraw their "licenses on reasonable terms and conditions, for its patent(s) that are necessary or the implementation of the ECMA standard."

The patent side of mono wasn't really too interesting to me until now... what are their plans to do once ecma withdraws (as it has with the huge list already)?

Need to find out the terms of the license that MS & HP gave to Novell for implementing C#. A license for implementing a standard. hehe.

i'll just laugh. did you even glance at the dropped standards you are referring to? they are so old it's unbelievable. actually they are so old that patents on those EMCA standards don't exist anymore. As i understand it you can implement any ECMA standards any way you like (as long as you're following the standard) because implementation automatically grants you a license.

---

### Post by saulgoode on 2009-04-17
> **alternatealias said:**
> Earlier in this thread it was mentioned that Tomboy is under the LGPLv2.1-only license.

This means that you cannot change the license to GPLv2-or-later, thus cannot get to GPLv3.

The only GPL license that the GNote guy could legally choose to use is GPLv2.

Wrong.

> [**LGPLv2.1**]("http://www.gnu.org/licenses/old-licenses/lgpl-2.1.html") <-- click on link to read it for yourself 

*3. You may opt to apply the terms of the ordinary GNU General Public License instead of this License to a given copy of the Library. To do this, you must alter all the notices that refer to this License, so that they refer to the ordinary GNU General Public License, version 2, instead of to this License. (**If a newer version than version 2 of the ordinary GNU General Public License has appeared, then you can specify that version instead if you wish.** Do not make any other change in these notices.)*

---

### Post by saulgoode on 2009-04-17
> **gnomeuser said:**
> No that is just plain falsehoods. Mono is a true community project. Novell doesn't even require copyright assignment for the code you contribute, the only rules that exist for contributing involve having looked at the source code for Microsoft' .NET implementation. Novell nor anyone will stop you from developing any part of Mono you like. There are in fact companies like Mainsoft doing just that and they have done that for years.
What does any of that have to do with whether Mono is a "community project"? A community project has its control ultimately vested in the community, not a corporation.
> **gnomeuser said:**
> Name me one place in which I said anything about GNotes in this debate. There simply isn't one...

**[http://ubuntuforums.org/showpost.php?p=7065536&postcount=78](http://ubuntuforums.org/showpost.php?p=7065536&postcount=78)** 

That link is to a post by you in another thread, should you wish to not consider that part of "this debate"; however, I would point out that **I** did not equivocate my assertion in such a manner.

> **gnomeuser said:**
> I don't see the point, you know how ECMA standardization works or can research it, you can also go read the list of specifications under the OSP. 
Of course. Don't actually respond to questions put to you with facts or even opinions. Far better to toss out accusations of "falsehood", "dishonesty", "evil fest of lies", and "character assassination".

> **gnomeuser said:**
> Considering your dishonesty in the reply above I predict that you will find something in this reply to hang on to regardless, ...
I will hang on to the fact that I am honest person, none of my statements on the Internet have ever been shown to be lies (because they are not), and your post offers not one wit of support of your accusation that I am dishonest.

> **gnomeuser said:**
> ...thus retaining your opinion that the slightest hole in my knowledge or anyones makes your entire theory truthful. You may like to look into the tactics used by creationists arguing against evolution - it is the same approach.
If there is "hole in my knowledge", I have no objection to somebody trying to fill that hole. In fact, I welcome and appreciate such efforts. I do NOT appreciate unwarranted accusations of dishonesty by any party, directed toward any other.

I would suggest that you contrast your own behavior with that which you ascribe to others.

---

### Post by wsonar on 2009-04-17
retarted questions never mind

---

### Post by saulgoode on 2009-04-17
> **zekopeko said:**
> As i understand it you can implement any ECMA standards any way you like (as long as you're following the standard) because implementation automatically grants you a license.
My understanding of ECMA  differs from yours. The only absolute requirement that ECMA demands of contributors to its standards is that any necessary patents [will be made available on a reasonable, non-discriminatory basis]("http://www.ecma-international.org/memento/codeofconduct.htm") (RAND).

The contributors to the ECMA 335 (MS and HP) have [met this requirement]("http://www.ecma-international.org/publications/files/ECMA-ST/Ecma%20PATENT/ECMA-334%20&%20335/2001ga-123%20&%202002ga-003.pdf") (PDF) and have even gone further by offering upon request RAND licensing terms for their necessary patents. There has even been some indication that the RAND terms for any Microsoft-held patents are offered free of any royalty demands (often called RAND-Z for RAND at Zero cost).

However, there is a distinction between something being "offered" and something being "provided". There appears to be no evidence put forth that the RAND-Z licensing is provided and indeed the RAND-Z licensing would appear to only be available by the licensee actually requesting it of the patent holders.

---

### Post by zekopeko on 2009-04-17
> **saulgoode said:**
> My understanding of ECMA  differs from yours. The only absolute requirement that ECMA demands of contributors to its standards is that any necessary patents [will be made available on a reasonable, non-discriminatory basis]("http://www.ecma-international.org/memento/codeofconduct.htm") (RAND).

The contributors to the ECMA 335 (MS and HP) have [met this requirement]("http://www.ecma-international.org/publications/files/ECMA-ST/Ecma%20PATENT/ECMA-334%20&%20335/2001ga-123%20&%202002ga-003.pdf") (PDF) and have even gone further by offering upon request RAND licensing terms for their necessary patents. There has even been some indication that the RAND terms for any Microsoft-held patents are offered free of any royalty demands (often called RAND-Z for RAND at Zero cost).

However, there is a distinction between something being "offered" and something being "provided". There appears to be no evidence put forth that the RAND-Z licensing is provided and indeed the RAND-Z licensing would appear to only be available by the licensee actually requesting it of the patent holders.

mono can be sued just like any other program out there if there is a legal basis for the lawsuite. software patents are a mess in the US and poorly organized. so every time you write code you could be breaking a patent. this leads to fear and this fear is part of FUD.

so stop singling mono out. if there is a problem microsoft can point the finger and say what exactly is being infringed upon and mono devs can work around that if there is a legal basis for the complaint. just like linux , java, openoffice and 1000s more. so why worry?

---

### Post by Vadi on 2009-04-17
#-o maybe because it definitely has issues, while other components don't have it as such.

You didn't really answer the point either, a "the whole linux ecosystem is suable! why worry?" answer raises more worries than anything else.

---

### Post by zekopeko on 2009-04-17
> **Vadi said:**
> #-o maybe because it definitely has issues, while other components don't have it as such.

You didn't really answer the point either, a "the whole linux ecosystem is suable! why worry?" answer raises more worries than anything else.

well considering the part with ECMA and ISO standards i would say that mono is less likely to be sued then the rest of the linux ecosystem.
the thing is  that you are being paranoid. unhealthy paranoid that is.

and other components do have it as such. samba and wine are the two most prominent examples. i don't see people bashing them.
microsoft created a good development framework and language. why can't you just accept that and stop with the juvenile "i have to port this because it's tainted with sweat of 100's of MS programmers"?

---

### Post by Vadi on 2009-04-17
Doesn't look like you're saying anything helpful, sorry. No need to devolve to "mono is good, why can't you just leave it alone?!".

---

### Post by migueldeicaza on 2009-04-25
Someone pointed me to this thread, and I figured I could chime in on a few posts.

> **Vadi said:**
> Okay, lets look at reality. Unity3D does not run on Linux. It is made on a supposedly cross-platform Mono framework.


Unity3d started as a game engine for MacOS written in C++ and using a large collection of gaming technologies.   They originally used Python to drive scripting in the game and later switched to Mono for the performance benefits that Mono brought to their platform.

For many years Unity3D was a MacOS only application.   As you can guess the majority of the code was deeply tied to MacOS X and it took many years and a lot of work on their part to port this OSX codebase to Windows.

You portray Unity as a Mono application.   It was actually a C++ app with very little Mono.   It was only recently that a lot of the Objective-C code and MacOS X-isms was replaced with C# and Mono code when they rewrote their game editor to run on Windows.

We have talked to Unity about doing a Linux port but Linux on the desktop remains a small market today.   Despite the fact that the Linux desktop market is not something that their customers require, they were kidn enough to give me access to their source code to do a port.

With the help of Chris Toshok (the Moonlight project lead) we made some progress on the port, but I can tell you that none of the porting challenges had anything to do with Mono, it is all about getting all of the dependencies that Unity depends on to build with g++ on Linux and writing an X11 backend.

The engine works, but the physics engine is not working properly.  Sadly both my experience on this matter and my time are limited and I have not been able to fix this last problem.

> 
Miguel de Icaza couldn't care less either; all he is happy about is that it's made on Mono. 


Well, I cared enough that I negotiated with Unity the access to the source, worked on a port on my weekends and spare time and contributed the work back to Unity.   

But you are right that I love Unity as a user of Mono.  After all, I do spend all of my time working on Mono and I like to help people that use my software.

Just as I am happy to see when a company, a government or an organization adopts Gnome, Linux or free software in general.   

Even if these companies use it in proprietary products.  For example, I do love what Amazon and Google have done with Linux, even if not all of the software that they have built is open source.

The way I see things, the more users we get using Mono will transate into more contributors, more contributors, more software written for it, better documentation, better tests, a warmer community and so on.

So I do like to nurture Mono users and I try to help my users be successful with their uses of Mono.   

We have seen this phenomenon with Amazon, Google and every other company that develops proprietary software but uses free software: contributions start to trickle back to the originating projects and these projects become better over time.

Miguel.

---

### Post by migueldeicaza on 2009-04-25
> **saulgoode said:**
> No, it is not. Novell owns the trademarks for Mono and has ultimate say in decisions made by the project. Community projects permit the community to make decisions and the trademarks are not held by a for-profit company. 


The problem with arguing over what is a "community project" is that lacking a definition set in stone everyone will argue based on what they feel is a "community project" as the comment above illustrates. 

You have set the bar at "trademarks are not held by a for-profit company" which is a rule that you just made up.   And it would lead into an endless discussion about Fedora(tm), Ubuntu(tm).

Mono is an open source project, and even if Novell contributes most of the work there are dozens of companies that contribute regularly to Mono.   

Being free software allows anyone to fork Mono if they feel that we are not making the right decisions or that we are blocking significant or important progress.

Luckily this is not something that has happened.   But the day that we screw over the community it is the day that someone will fork the project.   It has happened in the past with other projects, and there is no reason to think this could not happen to Mono.

---

### Post by Vadi on 2009-04-26
PPA updated to 0.2.0

@migueldeicaza: thanks for the replies, I didn't know a lot of the info.

---

### Post by pingjocky on 2009-04-26
> **Vadi said:**
> PPA updated to 0.2.0


Thanks for keeping it up to date!!

---

### Post by hanzomon4 on 2009-04-26
What does this provide over tomboy?

---

### Post by bapoumba on 2009-04-26
> **migueldeicaza said:**
> 
Miguel.
Welcome to the ubuntuforums :)

---

### Post by Tibuda on 2009-04-26
> **hanzomon4 said:**
> What does this provide over tomboy?

Nothing. It has to "catch up". (Hey, that's what FUD people tell Mono has to do with .NET)

---

### Post by pingjocky on 2009-04-26
> **hanzomon4 said:**
> What does this provide over tomboy?

Choices... The freedom to choose which one you want to use.  Some people don't care for apps written in mono, some don't care either way but this is a great example of the flexibility Open Source.

---

### Post by hanzomon4 on 2009-04-26
Seems redundant for no good reason to me. I mean is performance better with c++? People can do whatever they want but this appears to be one of those frivolous things that adds nothing to foss and is driven by fud... sorry

---

### Post by directhex on 2009-04-26
> **hanzomon4 said:**
> Seems redundant for no good reason to me. I mean is performance better with c++?

It's a bit faster to start up, & more lightweight, but is harder to develop & lacks features.

---

### Post by gnomeuser on 2009-04-26
> **directhex said:**
> It's a bit faster to start up, & more lightweight, but is harder to develop & lacks features.

I noticed that tomboy got some massive startup improvements after some profiling was done. I wonder if the startup performance difference will continue to be measurable in the real world as general Mono performance increases and awareness of profiling becomes more widespread.

The GNOME community seem to go in bouts of performance testing, a couple of years ago Fredrico was really hammering on about the subject (with an excellent FOSDEM 2007 talk btw. people should go see it). Now again performance seems to be taking the rounds again.

I even noticed that Banshee started adding performance regression tests in an effort to follow the webkit motto of keeping the program fast by never allowing it to become slow.

In general I think we could do more work here on the platform itself, we really don't do regression testing for performance and it's only really taken up to revision in this short bursts every few years.

Is it time I wonder to file bugs against all projects that do not have a performance regression test suite, in the hope that they might consider adding one. That way at least we would know when we are becoming slower with real metrics instead of users complaining that suddenly their systems feel awful.

---

### Post by zekopeko on 2009-04-26
> **gnomeuser said:**
> I noticed that tomboy got some massive startup improvements after some profiling was done. I wonder if the startup performance difference will continue to be measurable in the real world as general Mono performance increases and awareness of profiling becomes more widespread.

The GNOME community seem to go in bouts of performance testing, a couple of years ago Fredrico was really hammering on about the subject (with an excellent FOSDEM 2007 talk btw. people should go see it). Now again performance seems to be taking the rounds again.

I even noticed that Banshee started adding performance regression tests in an effort to follow the webkit motto of keeping the program fast by never allowing it to become slow.

In general I think we could do more work here on the platform itself, we really don't do regression testing for performance and it's only really taken up to revision in this short bursts every few years.

Is it time I wonder to file bugs against all projects that do not have a performance regression test suite, in the hope that they might consider adding one. That way at least we would know when we are becoming slower with real metrics instead of users complaining that suddenly their systems feel awful.

this is a great idea. i remember when banshee-1 was released they had a splash screen. after 1.2 (?) it was gone since the only point of a splash screen is to make you look at something pretty while it loads (a broken design since it only mask the problem).
i'm all for it.

---

### Post by Vadi on 2009-04-26
> **hanzomon4 said:**
> What does this provide over tomboy?

From the users POV, it's just faster to start and lighter on memory while running. It's an experiment mainly, and as it's turning out, a rather successful one in the technical side (it starts, works the same. No addins yet though.)

---

### Post by Vadi on 2009-05-02
0.3.0 is now available.

> New features:

    * Applet support (Closes #578979).
    * Print addon.
    * Insert Time Stamp addon.
    * Bugzilla addon.
    * Implement addin preferences.

Fixes:

    * Should now build if Gtk+ 2.16 is present but not Gtkmm 2.16.
    * Should build with Gtk+ 2.12 and Gtkmm 2.12 (Closes #580250) (Robert Millan)
    * Fix a typo in gnote.1 (Closes #580211) (Robert Millan)
    * Desktop file reflect XFCE and bugzilla component. (Closes #580481) (Ritesh Khadgaray)
    * Missing accelerators in link context menu (Closes #580443) (Mário Machado)
    * Reference bugzilla component in server file (Closes #579198)

Translations:

    * Short descriptions in shema must not end with a '.' (Closes #579337)
    * Added translations: - British English (en_GB) - Czech (cs) - Portugese (pt) - Spanish (es) - Thai (th)
    * Updated translations: - Arabic (ar) - German (de)


---

### Post by directhex on 2009-05-02
I can't seem to disable addins. Is this a bug?

---

### Post by Vadi on 2009-05-02
No idea and the author doesn't look at this thread, better luck posting on his blog or bugtracker.

---

### Post by Vadi on 2009-05-13
PPA cancelled, use [https://launchpad.net/~gnote/+archive/ppa](https://launchpad.net/~gnote/+archive/ppa) instead.

---

### Post by neighborlee on 2009-05-28
> **hanzomon4 said:**
> What does this provide over tomboy?

HOw about not being written in patented languages, for which it seems  from here:

[http://www.itwire.com/content/view/25215/1090/](http://www.itwire.com/content/view/25215/1090/)

, would indicate that there is a  huge question now over ecma ...for which I still  have not received a answer on ubuntu forum, so I guess I should just take it to the MOTU ML ?

Is gnote the start of something big ? ;)))< something good, this way comes>

cheers
nl

---

### Post by monsterstack on 2009-05-28
Uh, why revive this thread if there is no news on the latest developments in Gnote?

---

### Post by neighborlee on 2009-05-28
> **monsterstack said:**
> Uh, why revive this thread if there is no news on the latest developments in Gnote?

So your questioning my right to comment on ubuntu thread with which I find relevance, thereby denying my constitutional rights ?

I"ve been busy, and if I find a thread where misinformation has been posted, you can be assured I will respond, no matter what the age of the threads, but if you find somewhere in ubuntu forum policy that I can not do that and that the date range is stipulated, then fine l(

cheers
nl

---

### Post by monsterstack on 2009-05-28
> **neighborlee said:**
> So your questioning my right to comment on ubuntu thread with which I find relevance, thereby denying my constitutional rights ?

I"ve been busy, and if I find a thread where misinformation has been posted, you can be assured I will respond, no matter what the age of the threads, but if you find somewhere in ubuntu forum policy that I can not do that and that the date range is stipulated, then fine l(

cheers
nl

Yeah, I know. But this thread has already come so far off-topic it's a joke. There's nothing stopping you from creating a new mono-debate thread, seeing as the last one in "Recurring Discussions" has been closed. Things like that ITWire article are worth discussing, no arguments there, but perhaps better served in its own dedicated thread. I don't like the way any thread remotely connected to mono is inevitably derailed, that's all.

---

### Post by aanderse on 2009-05-28
slightly off topic, but this seemed like a good place to post...

for people who were involved in the pro/anti mono debate: have any of you ever tried using vala yet? if so, did you like it? if not, why not? for those who have or have not tried it - do you have anything against it?

i'm not going to say i'm against mono for legal/"fud" reasons some people would claim... but i will say that for gnome development vala just seems to make much more sense to me.



i want to note that i'm not completely ignorant to the topic- i've played with vala extensively, and my day job requires me to code in dot net almost all day every day.

just curious!

ps. imho a vala port of tomboy (instead of c++) would have been good :)

---

### Post by ghindo on 2009-05-28
> **neighborlee said:**
> So your questioning my right to comment on ubuntu thread with which I find relevance, thereby denying my constitutional rights ?No, we're quesitioning why you're rehashing what has been said time and time again not only in this thread, but numerous other places.  Did you read the rest of this thread, or just jump right on in?

---

### Post by neighborlee on 2009-05-28
> **ghindo said:**
> No, we're quesitioning why you're rehashing what has been said time and time again not only in this thread, but numerous other places.  Did you read the rest of this thread, or just jump right on in?

Of course I did, what would make you think otherwise , and where is it written, that when I see threads not discussing something very relevant, that I dont have the right to chime in ?

Where is that written into the ubuntu forum policy ?

cheers
nl

---

### Post by cariboo on 2009-05-28
The membership has spoken, this is not a democracy, this thread is closed. Please quit trying to push forward your own agenda.

---

