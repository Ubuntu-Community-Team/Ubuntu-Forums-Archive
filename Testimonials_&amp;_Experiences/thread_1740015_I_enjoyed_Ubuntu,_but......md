---
title: "I enjoyed Ubuntu, but....."
date: 2011-04-26
forum: Testimonials &amp; Experiences
---

### Post by Gandalf_the_Grey on 2011-04-26
I have really enjoyed using Ubuntu, which was the second distribution of Linux I ever tried (the first being Fedora).  

However, I have decided to cease using Ubuntu as my primary distribution.

The reason I have switched back to using Fedora as my primary distribution is the fact that Ubuntu includes Mono by default on any new install of Ubuntu.  I have researched Mono, and I have come to the conclusion that it has too many potential licensing issues for me to take the chance of using it.  In addition, with Microsoft now looking at acquiring Novell, and with it Mono, I cannot use Mono without an enormous amount of unease.  Fortunately, at the moment I can remove Mono without removing any key programs, but it appears Canonical is working to change that, integrating Mono more and more into Ubuntu.

However, I do still think Ubuntu is a very good distribution, particularly for those who are new to Linux.  It was Ubuntu that really helped me learn how to use Linux well, back when I had just switched from Windows.  Ubuntu is still the easiest  distribution to use, as far as I can tell.  

Please, remove Mono from Ubuntu.  It is a huge risk, not to mention a waste of disk space.  There are programs that can replace those installed by default in Ubuntu that require Mono (for instance, Gnote can replace Tomboy).

Most sincerely,
                         Gandalf_the_Grey

---

### Post by directhex on 2011-04-26
> **Gandalf_the_Grey said:**
> (for instance, Gnote can replace Tomboy)

When an anti-Mono activist gets off their lazy behind and writes a C++ version of Tomboy's online note synchronization, then it can replace Tomboy. Until then, it's a featureless clone.

I've been waiting a few years for someone to do it.

---

### Post by pricetech on 2011-04-26
As always, use what works for you and be happy.

---

### Post by tgm4883 on 2011-04-26
> **pricetech said:**
> as always, use what works for you and be happy.

+1

---

### Post by Gandalf_the_Grey on 2011-04-26
> **directhex said:**
> When an anti-Mono activist gets off their lazy behind and writes a C++ version of Tomboy's online note synchronization, then it can replace Tomboy. Until then, it's a featureless clone.

I've been waiting a few years for someone to do it.

As of last month, that was one of the features being worked on.  Gnote is still a work in progress.  Its end goal is to be a complete C++-based replacement for Tomboy, including online note synchronization.

---

### Post by el_koraco on 2011-04-26
Mono rocks!

---

### Post by cgroza on 2011-04-26
I have nothing against Mono. I thank the developers of mono for bringing support for such a wonderful language to Linux (talking about C#).

---

### Post by jdrodrig on 2011-04-26
> **Gandalf_the_Grey said:**
>  I have researched Mono, and I have come to the conclusion that it has too many potential licensing issues for me to take the chance of using it.  

This is interesting; not the Mono-ignorant as myself, building on your research efforts, could you elaborate about this licensing issues?

---

### Post by Gandalf_the_Grey on 2011-04-26
Mono, released by Novell in 2004, is essentially a project that created a set of .NET and C# tools for Linux, including a C# compiler and a CLR (Common Language Runtime).  In essence, Mono allows .NET and C# programs to be compiled and run on Linux.  Now, there wouldn't be any problems with this normally.  Who wouldn't want .NET and C# programs to run on Linux, since that would increase compatibility?

However, parts of Mono are covered under patents owned by Microsoft relating to their .NET Framework.  In 2001, while Mono was still in development, Microsoft released a letter in which it promised that use of the patents would be available royalty-free, on a reasonable and non-discriminatory basis.  First question (still unanswered): What does "reasonable" mean?  Second question: Is this letter of Microsoft's legally binding, or could Microsoft still use these patents to sue all Linux distributions that include Mono?

Later, in 2009, Microsoft released their "Community Promise", promising again to never take legal action against people using Mono.  However, this "Community Promise" is not recognized by GNU as being compatible with the General Public License, under which most of Linux and Ubuntu are licensed.  Also, there is a potential loophole in the Community Promise: it makes no mention of whether *partial* implementations of .NET and C# are protected from legal action.  

Richard Stallman, founder of GNU and the Free Software Foundation, said "Even assuming Microsoft follows through on this announcement and covers ECMA 334 and 335 [the ECMA standards pertaining to Mono] under the Community Promise, this will not be sufficient to protect us against the dangers . . . . That's because Mono implements, and Tomboy depends upon, a number of libraries which are 'standard' in the sense that they're under C#'s "System" namespace (indicating that they're part of the standard library) and provided in Microsoft's implementation, but somewhat pointedly excluded from the ECMA specifications."

Finally, there are signs that Novell may soon be bought by Microsoft.  If this comes to pass, Microsoft will then directly own Mono.  I believe that Microsoft would not hesitate to sue producers of Linux distributions that include Mono.

Those are just some of the licensing risks involved when using Mono.  In addition to the risks, I and other Linux users have also noticed that Mono causes GNOME to be more sluggish.  I notices a significant increase in the speed of GNOME when I purged Mono and the programs that depend on it (F-Spot and Tomboy being the biggest).

That is why I will never use Mono again, and why I wish no distribution would even have it in their repositories, much less have it preinstalled.  One example of a distribution that has stripped Mono completely out of it is Netrunner.  According to Netrunner's developer, "it serves as a testcase for a functional Ubuntu without Mono."

---

### Post by benweston on 2011-04-26
> **pricetech said:**
> As always, use what works for you and be happy.

The paradox being, of course, that real progress will never be made if everyone took that approach to points they don't like.

---

### Post by jdrodrig on 2011-04-26
Gandalf, many thanks for this useful background information.

But wouldnt an increase in the number of people using distros with mono, decrease the probability of such legal action from Microsoft?. After all, more voices would yell faul if such event happened and Microsoft already tainted reputation be damaged.

If so, the implication is for the desirability of more people using distros like Ubuntu.

Also, is the claim that there is no legal instrument that would make this thread vanish? or there is something like a Community Promise 2.0 that would make even Stallman happy?

---

### Post by directhex on 2011-04-26
> **Gandalf_the_Grey said:**
> Mono, released by Novell in 2004

2001

> , is essentially a project that created a set of .NET and C# tools for Linux, including a C# compiler and a CLR (Common Language Runtime).  In essence, Mono allows .NET and C# programs to be compiled and run on Linux.  Now, there wouldn't be any problems with this normally.  Who wouldn't want .NET and C# programs to run on Linux, since that would increase compatibility?

However, parts of Mono are covered under patents owned by Microsoft relating to their .NET Framework.

Name them.

> In 2001, while Mono was still in development, Microsoft released a letter in which it promised that use of the patents would be available royalty-free, on a reasonable and non-discriminatory basis.  First question (still unanswered): What does "reasonable" mean?  Second question: Is this letter of Microsoft's legally binding, or could Microsoft still use these patents to sue all Linux distributions that include Mono?

Later, in 2009, Microsoft released their "Community Promise", promising again to never take legal action against people using Mono.  However, this "Community Promise" is not recognized by GNU as being compatible with the General Public License, under which most of Linux and Ubuntu are licensed.

Irrelevant. Why does it matter, if the apps and framework in question are not under a GPL license?

> Also, there is a potential loophole in the Community Promise: it makes no mention of whether *partial* implementations of .NET and C# are protected from legal action.  

It's clear: they're not. The Community Promise requires full implementations. The Open Specification Promise does not.

> Richard Stallman, founder of GNU and the Free Software Foundation, said "Even assuming Microsoft follows through on this announcement and covers ECMA 334 and 335 [the ECMA standards pertaining to Mono] under the Community Promise, this will not be sufficient to protect us against the dangers . . . . That's because Mono implements, and Tomboy depends upon, a number of libraries which are 'standard' in the sense that they're under C#'s "System" namespace (indicating that they're part of the standard library) and provided in Microsoft's implementation, but somewhat pointedly excluded from the ECMA specifications."

Stallman's analysis is wrong, but he explicitly does not accept criticism on the basis that anyone who disagrees with him is an evil liar.

> Finally, there are signs that Novell may soon be bought by Microsoft.

Attachmate.

> If this comes to pass, Microsoft will then directly own Mono.  I believe that Microsoft would not hesitate to sue producers of Linux distributions that include Mono.

On what basis? The source was already released under a selection of Free Software licenses - importantly, that includes libraries released by Microsoft themselves under GPLv3-compatible FOSS licenses with full patent grants. If they were to own Mono (an utterly moronic purchase for them - only an idiot would have written the sites filling your head with this kind of nonsense), then they could not make any copyright claims regarding previously-released code. Patent claims? Well, if they owned relevant patents already, they could have sued already - and if not, then that means Mono does NOT infringe on existing patents, surely?

> Those are just some of the licensing risks involved when using Mono.

Licensing is not patents. See [http://apebox.org/wordpress/rants/352/](http://apebox.org/wordpress/rants/352/)

> In addition to the risks, I and other Linux users have also noticed that Mono causes GNOME to be more sluggish.

This is a fantasy, and is literally impossible. See [http://en.wikipedia.org/wiki/Confirmation_bias](http://en.wikipedia.org/wiki/Confirmation_bias)

> I notices a significant increase in the speed of GNOME when I purged Mono and the programs that depend on it (F-Spot and Tomboy being the biggest).

That is why I will never use Mono again, and why I wish no distribution would even have it in their repositories, much less have it preinstalled.

You believe the best way to encourage Freedom is to remove Freedom from people to write the apps they want, with the languages they want, and for distributions to include the apps they want? What kind of goose-stepping vision of Freedom do you have?

> One example of a distribution that has stripped Mono completely out of it is Netrunner.  According to Netrunner's developer, "it serves as a testcase for a functional Ubuntu without Mono."

I wrote "a testcase for a functional Ubuntu without Mono" myself. Apps are just apps, swapping a few inferior apps into an ISO isn't a big deal. It took about an hour, plus time looking at photos of chickens on Flickr. I managed less than a dozen downloads, and it was a thoroughly pointless exercise. See [http://apebox.org/wordpress/linux/210/](http://apebox.org/wordpress/linux/210/)

---

### Post by directhex on 2011-04-26
> **jdrodrig said:**
> But wouldnt an increase in the number of people using distros with mono, decrease the probability of such legal action from Microsoft?.

Ask yourself the questions "What, ***EXACTLY*** can Microsoft do?", "What would be the outcome for Free Software distros", and "What would be the outcome for Microsoft?"

> After all, more voices would yell faul if such event happened and Microsoft already tainted reputation be damaged.

Clever. What would benefit Microsoft more, in an area where they are suffering a SERIOUS haemmorage of mindshare - stamping out a "competing" implementation of a spec they co-authored, and alienating every FOSS developer on the planet - or leaving it be, and potentially allowing Windows devs to move to Linux? Which is the bigger risk to their investors' profits?

> If so, the implication is for the desirability of more people using distros like Ubuntu.

I don't really think they care. Users shouldn't need to care about the programming languages making up their distro, they just want to run apps. And Microsoft don't care since the existence of Mono helps them gain positive mindshare from FOSS Windows developers.

> Also, is the claim that there is no legal instrument that would make this thread vanish? or there is something like a Community Promise 2.0 that would make even Stallman happy?

It's Microsoft. They could release Microsoft.NET 5.0 under AGPLv3, and still people would call it poison.

---

### Post by jdrodrig on 2011-04-26
Thanks for the extra information.

"Well, if they owned relevant patents already, they could have sued already - and if not, then that means Mono does NOT infringe on existing patents, surely?"

Dangerous logic, why Nokia seems to have waited for the iPhone to take off, for it to claim patent violations? the issue is whether these infringements have statute of limitations?

The issue is simple:

1) Microsoft buying or not Novell, do they have legal basis to claim violations from distros using Mono despite the Community Promise or other documents signed up to this moment?

2) Does Microsoft buying Novell change anything?

---

### Post by directhex on 2011-04-26
> **jdrodrig said:**
> 1) Microsoft buying or not Novell, do they have legal basis to claim violations from distros using Mono despite the Community Promise or other documents signed up to this moment?

If any violated patents in Mono which fall outside the protected sections (CP-covered code, and code with Microsoft copyright & patent grants) were pointed out, the first for the ten years Mono has existed I might add, then you know what would happen? That code would be rewritten. The same way code was rewritten in the Linux kernel after attacks on it with patents (e.g. FAT32 long filename behaviour).

Areas up for debate are generally uninteresting for FOSS systems anyway - stuff like the System.Windows.Forms UI code for Windows apps (and patents on that are likely violated in Wine too), where Mono has its own superior UI code. Microsoft have a lot of very uninteresting libraries, and nobody would care if they were even removed entirely from Mono.

> 2) Does Microsoft buying Novell change anything?

Microsoft are not buying Novell. I have no idea where this fantasy story came from, but I have a strong hunch.

---

### Post by jdrodrig on 2011-04-26
Thanks, useful point of view.

---

### Post by Simian Man on 2011-04-26
Thanks for being a voice of reason directhex.  You are exactly right, but I don't know how you have the energy to argue with trolls all the time :).

---

### Post by wolfen69 on 2011-04-26
All of this mono stuff aside, you know what I find really kind of funny? All of these Stallman-esque freedom lovers use proprietary non-free blobs every day, and don't even think twice about it. If you live in a modern society and take advantage of modern conveniences, you are using non-free stuff all the time. How come no uproar about *that*? Your car, your TV, your microwave, ATM, phone service are all controlled by companies that live by proprietary, non-free ways. Yet these so-called freedom lovers decided to single out the PC as a source of evil because it *can* contain "non-free" parts.

If these people truly wanted to live "free" in the truest sense of the word, they would all find a place to live in the middle of nowhere, build their own house with there bare hands from fallen trees, grow their own food, make there own clothing, and never touch anything fabricated in a factory. 

Big companies that use non-free, proprietary technology produce almost everything you touch and use. Why is that OK, but something as trivial as TomBoy notes is not? Seems kind of hypocritical to me.

---

### Post by jdrodrig on 2011-04-26
> **Simian Man said:**
> Thanks for being a voice of reason directhex.  You are exactly right, but I don't know how you have the energy to argue with trolls all the time :).

"troll"? (I am almost sure you did not mean me..but...) I think this name calling is totally uncalled for.

if you want to go in life calling trolls anyone with a different point of view than yours, it is your own preference; but it does a disservice to these forums to take such an aggressive attitude with OPs that, like in this case, seem to have a genuine concern and take the time to write here...

---

### Post by Gandalf_the_Grey on 2011-04-26
Wolfen69: as to your comment about not being a "Stallman-esque freedom-lover", I can assure you that I am not one of them.  I have no problem with using proprietary hardware, software, devices, etc.  What I do have a problem with, however, is when software that may have issues that could spell the end for an entire Linux distribution is bundled as though there were no risk at all.

Directhex: I am only human, so if I do get my facts wrong due to incorrect sources or other errors, do not chalk it up to me being some kind of extraordinarily over-zealous all-software-must-be-perfectly-free person.

About the licensing/patents mistake: sorry, that was a mistype, due to typing this on a mobile device while away from my computer (which actually helps to prove that I'm not opposed to all proprietary devices and software, as I used an iPad to type this and my earlier posts.)

I will do more research to see if I can find more facts concerning the patents and licensing of Mono.  This post is just to inform you that I am not a troll, neither am I an ultra-zealot of any sort.

---

### Post by 3rdalbum on 2011-04-26
The Mono issue is/should be dead and buried.

Microsoft says it won't sue over C#/.NET implementations. Microsoft says it's happy for Linux users to have Mono. Problem?

If you don't like Mono, then remove it on your own system. But I hold a dim view of Mono scaremongering, and I disapprove of claiming Ubuntu to be on shaky legal ground because of including Mono. IANAL and YANAL but Canonical has legal advice.

Saying that Ubuntu is on bad legal grounds actually sounds a lot like Microsoft-style FUD.

---

### Post by wolfen69 on 2011-04-26
> **3rdalbum said:**
> The Mono issue is/should be dead and buried.

Microsoft says it won't sue over C#/.NET implementations. Microsoft says it's happy for Linux users to have Mono. Problem?

If you don't like Mono, then remove it on your own system. But I hold a dim view of Mono scaremongering, and I disapprove of claiming Ubuntu to be on shaky legal ground because of including Mono. IANAL and YANAL but Canonical has legal advice.

Saying that Ubuntu is on bad legal grounds actually sounds a lot like Microsoft-style FUD.

I agree. 

Now let's all gather 'round and sing kumbaya.

---

### Post by directhex on 2011-04-27
Can someone explain to me the logic behind "if Microsoft suddenly goes mental on Mono, it means THE END OF EVERY DISTRO EVER"?

If that were to happen, then, oop, the bad evil wrong stuff would be stripped out. No big deal. Ubuntu wasn't binned after previous patent disputes in the kernel or elsewhere, was it? No, of course it wasn't - but there's a long-standing double standard applied where patent disputes are easily challenged and worked around - unless they're in Mono, where they would mean the end of the universe.

---

### Post by el_koraco on 2011-04-27
I don't get it either. The worst that could happen if Microsoft went postal would be the removal of some libraries and programs. It's not as if apt and yum were written in C#.

---

### Post by TBABill on 2011-04-27
And we so often brag about the flexibility Linux has to change or be customized, which would obviously include the ability to react to any down-the-road legality that could impact it. It's ironic that we brag so often of the inherent control and flexibility within our system, then fear a single hypothetical legal change could bring it to its knees.

---

### Post by Ad@m on 2011-04-27
The problem with Mono are the parts that rely on the Microsoft's OPS license. As explained in detail here at:

[http://www.groklaw.net/articlebasic.php?story=20080312151954507](http://www.groklaw.net/articlebasic.php?story=20080312151954507)

If Mono becomes very successful and widespread will Microsoft sit back and watch all that potential revenue go to waste??

:popcorn:

---

### Post by Gandalf_the_Grey on 2011-04-27
> **directhex said:**
> Can someone explain to me the logic behind "if Microsoft suddenly goes mental on Mono, it means THE END OF EVERY DISTRO EVER"?

If that were to happen, then, oop, the bad evil wrong stuff would be stripped out. No big deal. Ubuntu wasn't binned after previous patent disputes in the kernel or elsewhere, was it? No, of course it wasn't - but there's a long-standing double standard applied where patent disputes are easily challenged and worked around - unless they're in Mono, where they would mean the end of the universe.

The reasoning behind that, as far as I am aware, is that if Microsoft sued over this, it would in all likelihood result in Canonical going bankrupt.  If Canonical goes bankrupt, there is a very distinct possibility that Ubuntu would not recover.

In addition, it would give Microsoft an enormous amount of ammunition to use to convince businesses not to use Linux.  "Look, see, just like we told you all along, Linux infringed on our patents!". Massive distrust of Linux would likely follow, because businesses might start believing that they could be sued if they used Linux.

At least, that is my understanding of the issue.  I could be completely wrong about all of this, including the patents and license of Mono.  I am only human.

---

### Post by directhex on 2011-04-27
> **Gandalf_the_Grey said:**
> The reasoning behind that, as far as I am aware, is that if Microsoft sued over this, it would in all likelihood result in Canonical going bankrupt.

Canonical's legal counsel have said they're not worried about this. Are you a lawyer with access to better information?

---

### Post by Sef on 2011-04-29
Locked. Off-Topic.

---

