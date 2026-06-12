---
title: "Wine: do we need to know what's thinking Microsoft about it?"
date: 2010-11-19
forum: The Cafe
---

### Post by alexan on 2010-11-19
Here's my Brainstorm:
[http://brainstorm.ubuntu.com/idea/26503](http://brainstorm.ubuntu.com/idea/26503)


IMHO: this is very important. One very key word of FUD is "uncertainty": this is the main reason we hadn't official position of Microsoft towards Wine.

If you think I am right, debate.. if you don't: debate it as well. We need to put this under Canonical's eyes. And, in democracy, problems are seen only if citizen of every side start to realize there's something to debate about. :popcorn:

---

### Post by Paqman on 2010-11-19
Even if Microsoft gave a hoot about Wine, which I doubt they do, there's nothing they could do. There's nothing illegal about writing new code that's designed to be compatible with an existing system. The folks behind Wine have been careful to make sure they aren't exposing themselves to any risk.

> **alexan said:**
> We need to put this under Canonical's eyes. 

This isn't really the right place to do that directly, Canonical don't really monitor this forum. But if you want to try and build a consensus among community members go for it, then approach someone from Canonical directly (Jono Bacon maybe?)

---

### Post by zekopeko on 2010-11-19
> **alexan said:**
> Here's my Brainstorm:
[http://brainstorm.ubuntu.com/idea/26503](http://brainstorm.ubuntu.com/idea/26503)


IMHO: this is very important. One very key word of FUD is "uncertainty": this is the main reason we hadn't official position of Microsoft towards Wine.

If you think I am right, debate.. if you don't: debate it as well. We need to put this under Canonical's eyes. And, in democracy, problems are seen only if citizen of every side start to realize there's something to debate about. :popcorn:

Microsoft is pretty clear I think. You can't use the Windows dlls on a non-Windows OS. Plus I don't know about Microsoft ever saying anything about Wine. Heck Google used and distributed Wine as part of Picasa for Linux before.

---

### Post by matthew.ball on 2010-11-19
WINE (and ReactOS) are both clean room reverse engineered projects I believe.

While that doesn't entirely free them from legal issues (I'm pretty sure patents are still applicable, as they are a process more than an implementation) it does get around potential copyright infringements.

I could be totally wrong though.

---

### Post by nerdopolis on 2010-11-19
A while back, Wine was able to pass the Windows Genuine Advantage test, and I think a Microsoft person did bring up Wine a while back calling it the most popular win32 something....

And a Microsoft site mentions it here. (near the end)
[http://www.microsoft.com/genuine/downloads/faq.aspx](http://www.microsoft.com/genuine/downloads/faq.aspx)

---

### Post by Iksf on 2010-11-19
Doubt theres a problem, Wine devs have been notoriously conservative about using other peoples code

---

### Post by NCLI on 2010-11-19
> **nerdopolis said:**
> A while back, Wine was able to pass the Windows Genuine Advantage test, and I think a Microsoft person did bring up Wine a while back calling it the most popular win32 something....

And a Microsoft site mentions it here. (near the end)
[http://www.microsoft.com/genuine/downloads/faq.aspx](http://www.microsoft.com/genuine/downloads/faq.aspx)
> Q:
Will systems running Wine pass WGA validation?
A:
Wine is an implementation of the Windows 3.x and Win32 APIs on top of X and Unix. When WGA validation detects Wine running on the system, it will notify users that they are running non-genuine Windows, and it will not allow genuine Windows downloads for that system. Users of Wine should consult the Wine community for Wine updates. It is important to note that Wine users, and other users of non-genuine Windows, can continue to download updates for most Microsoft applications from Microsoft application-specific sites, such as Office Update.

To me, it sounds like they don't care.

---

### Post by slackthumbz on 2010-11-19
Was the original post (on brainstorm) put through a hungover version of google translate or something? 'cos it doesn't make a great deal of sense.

---

### Post by Paqman on 2010-11-19
> **slackthumbz said:**
> Was the original post (on brainstorm) put through a hungover version of google translate or something? 'cos it doesn't make a great deal of sense.

For many Ubuntu users, English is not their first language.

---

### Post by grahammechanical on 2010-11-19
I use Wine to run one program that is compiled to run under a Microsoft operating system. I do not have a copy of any of Microsoft's operating systems. I am not using parts of Microsoft's operating systems illegally because I am not using anything from any of their Operating Systems. I comply with the licensing conditions of the publisher of the program that I am using.

If I had a legal copy of a Microsoft operating system then I would not be breaking the law if I used parts of it under Wine. Do we break the terms and conditions of the Microsoft license when we run one of its operating systems in a virtual machine? Only if the copy of the operating system is illegal.

The purpose of Wine is not to allow MS Windows operating systems to run on Linux but to allow programs compiled for MS Windows to run under Linux and to do this legally. Wine is not a replacement for Windows. Linux is. I repeat that I have only one program that I want to use that does not have a Linux equivalent or superior program. That program is a reader for the catalogue of a book and magazine publisher. I get everything I need for my computer from the Linux community. That is the direction that Microsoft looks to when it looks over it's shoulder.

Don't fix what ain't broke. 

Regards.

---

### Post by 3Miro on 2010-11-19
> **grahammechanical said:**
> 
If I had a legal copy of a Microsoft operating system then I would not be breaking the law if I used parts of it under Wine. Do we break the terms and conditions of the Microsoft license when we run one of its operating systems in a virtual machine? Only if the copy of the operating system is illegal.


This may or may not be true. For Mac OSX, I am sure that it is illegal to use it under Virtual Box or any non-Mac hardware. Thechnically, MS can prohibit you from using parts of their system under Linux, even if you own a legitimate copy of windows.

Wine is a reverse engineering on the API not code. The first is somewhat legal the second one is not. Wine is walking a thin line and I think MS is waiting for a missed a step and then attack it. MS will not have an official position until they can profit from an official position.

Canonical is not wine and wine is not part of Ubuntu. Wine an additional piece of software that people can install on Ubuntu using community repositories. There is no real reason for Canonical to care about wine.

---

### Post by MasterNetra on 2010-11-19
> **NCLI said:**
> To me, it sounds like they don't care.

Of course not wine is still very buggy with a good number of apps, and is unable to run many. Plus many have to be configured or rig up to work. Windows > Wine still. If wine got to the point where you could install and run the vast majority of apps including all if not just about all the popular ones and do so just as well if not better then on windows, then you would most likely see MS start attacking. As it stands wine really isn't a threat yet.

---

### Post by forrestcupp on 2010-11-19
> **zekopeko said:**
> Microsoft is pretty clear I think. You can't use the Windows dlls on a non-Windows OS.

Wine doesn't use Windows dlls.  They reverse engineered all of those dlls.  Not one of them is taken from Windows.  They allow you to choose to override their dlls and use Windows ones if you want, but they don't include them, and they're not used by default.  Wine isn't doing anything illegal at all.

---

### Post by zekopeko on 2010-11-19
> **forrestcupp said:**
> Wine doesn't use Windows dlls.  They reverse engineered all of those dlls.  Not one of them is taken from Windows.  They allow you to choose to override their dlls and use Windows ones if you want, but they don't include them, and they're not used by default.  Wine isn't doing anything illegal at all.

And where was I saying that Wine is doing something wrong? I was simply saying that, IIRC, you can't use Windows dlls in a non-Windows OS. I believe it is in the Windows EULA but I could be wrong since it was some time ago I read up on that particular scenario.

---

### Post by unknownPoster on 2010-11-19
> **grahammechanical said:**
>  Wine is not a replacement for Windows. Linux is.

That's not true at all. Each have their distinct uses, advantages, and disadvantages. To expect one operating system to replace another seamlessly is disingenuous at best.

---

### Post by forrestcupp on 2010-11-19
> **zekopeko said:**
> And where was I saying that Wine is doing something wrong? I was simply saying that, IIRC, you can't use Windows dlls in a non-Windows OS. I believe it is in the Windows EULA but I could be wrong since it was some time ago I read up on that particular scenario.

Sorry, I misunderstood.  Some people really believe that Wine is illegal because of what you were talking about.  They don't realize that everything about it is reverse engineered.

---

### Post by kako13 on 2010-11-19
I don't think Microsoft care as long as you used their software.  And we already know what Bill Gate said about piracy...

[SIZE=4]*“It’s easier for our software to compete with Linux when there’s piracy than when there’s not.” - Bill Gate*[/SIZE]

---

### Post by unknownPoster on 2010-11-19
> **kako13 said:**
> I don't think Microsoft care as long as you used their software.  And we already know what Bill Gate said about piracy...

[SIZE=4]*“It’s easier for our software to compete with Linux when there’s piracy than when there’s not.” - Bill Gate*[/SIZE]

Source?

---

### Post by alexfish on 2010-11-19
> **unknownPoster said:**
> Source?

Don't think it's got much to do with wine

[http://schestowitz.com/UseNet/2008/September_2008_1/msg00460.html](http://schestowitz.com/UseNet/2008/September_2008_1/msg00460.html)

Old as the hills

---

### Post by endotherm on 2010-11-19
> **Paqman said:**
> Even if Microsoft gave a hoot about Wine, which I doubt they do, there's nothing they could do. There's nothing illegal about writing new code that's designed to be compatible with an existing system. The folks behind Wine have been careful to make sure they aren't exposing themselves to any risk.

this is definitely true of copyrighted system integration, but in countries where software patents are legal however, it is very unlikely that they could avoid all of MS's claims in all of their pertinent patents, without licensing them officially. this is exactly why software patents are essentially censorship. 

"no you can't write that code; I already wrote and patented something completely different that does the same thing."

---

### Post by kako13 on 2010-11-19
> **unknownPoster said:**
> Source?

Very interesting article: [http://money.cnn.com/magazines/fortune/fortune_archive/2007/07/23/100134488/](http://money.cnn.com/magazines/fortune/fortune_archive/2007/07/23/100134488/).

---

### Post by 3Miro on 2010-11-19
MS is benefiting from piracy. Right now, people have the choice of Legal Windows, Illegal Windows (respectively Mac OSX) or Free Legal Linux. Many people cannot or will not pay for legal windows, so MS is better off with them using illegal windows than Linux.

Reverse engineering windows is illegal. Wine reverse engineers the API, not the code (basically how third party apps interact with windows). The API may or may not violate software patents, which makes it borderline illegal.

---

### Post by howefield on 2010-11-19
2 posts removed.

Play nice now.

Read the strapline description for this forum... mainly the bit about "fun and community building". :)

---

### Post by unknownPoster on 2010-11-19
> **howefield said:**
> 2 posts removed.

Play nice now.

Read the strapline description for this forum... mainly the bit about "fun and community building". :)

Thank you. :)

---

### Post by Quadunit404 on 2010-11-19
I think we established on the first page that Microsoft doesn't really care that much about Wine, based on what was quoted from the WGA FAQ.

If they did care about Wine, they would have done something about it a loooooong time ago. However, beyond locking Wine users out of WU (but not application-specific update sites e.g. Microsoft Office Update) they have basically ignored the existence of Wine throughout its development. They know it exists, but don't really seem to mind its existence.

---

### Post by Mr. Picklesworth on 2010-11-20
Codeweavers (a major contributor to Wine) ships a commercial product called [Crossover]("http://www.codeweavers.com/products/"), which is basically Wine + a nice UI and a stable release cycle. It costs a reasonable bit of money on both MacOS and Linux and sells in regular retail stores (including London Drugs here in Canada).

We have nothing to worry about shipping Wine in this humble little distro :)

---

### Post by endotherm on 2010-11-20
> **Quadunit404 said:**
> 
If they did care about Wine, they would have done something about it a loooooong time ago. 

I agree with your analysis, save for this statement. it was actually only some weeks ago, that the terms of EULAs were[ declared by the courts to be legally binding in the u]("http://arstechnica.com/tech-policy/news/2010/09/the-end-of-used-major-ruling-upholds-tough-software-licenses.ars")s, and software patent law in particular has many untested facets that are still gray areas. important precedent forming decisions are being made regularly, as to the role of imaginary property within our society. after each one, you see a new block of lawsuits, long prepared, targeting the specific precedents set.

the industry has spent decades getting us to the point where socially, we accept the concept of licenses in a way we would not 20 years ago, changing our entire notion of ownership. the idea that we can resell things we have previously bought are being attacked, as is the idea that we actually own, and can thus modify whatever we do purchase. these changes take a long time to sink into a populations general consciousness, so the industries that rely on IP have been patiently leading us down the trail with both sticks and carrots, waiting for the courts to catch up with their vision. 

in 1994, the idea that a software vendor could use software to perform "Self Help" remedies to automatically shutdown unlicensed software, was largely considered by the legal community to be repugnant, so much so, that both MS and Intel were forced to withdraw certain privacy-sensitive features from their products. by 1998 however, big content had won over enough legislators to pass the DMCA. the software companies hopped on board, and by 2002, the MS legal team was confident enough of the environment to approve Activation, something that forces the user to prove their legitimacy, and regularly monitors the state of their PC hardware (reporting any change to MS) and determining their right to use the software on their terms. by 2005, activation began to include WGA checking, to ramp up the monitoring, and to apply even more aggressive self help remedies. in 2006, vista introduced activation requirements involving phoning home every 90 days for re-verification. 

[I]Please note, i am not attempting to bash MS specifically. Many other software vendors went through this same kind of evolution, but I speak of MS because many of us can remember and relate to the windows-based time line.  Many oldtimers might better relate to the SCO v. Everyone fiasco. luckily, that one ended better.
 
[/I]so I guess my point is, positions on IP from a interoperability perspective are increasingly vulnerable every year, at least in my neck of the woods. a few months ago for instance, the MPEGLA started rattling sabers, claiming that they could attack ogg/theora and the new VP8 codec[I], based on patents in h.264.
[/I]
eternal digital freedom requires eternal vigilance, I suppose.

---

### Post by alexan on 2010-11-20
> **Mr. Picklesworth said:**
> Codeweavers (a major contributor to Wine) ships a commercial product called [Crossover]("http://www.codeweavers.com/products/"), which is basically Wine + a nice UI and a stable release cycle. It costs a reasonable bit of money on both MacOS and Linux and sells in regular retail stores (including London Drugs here in Canada).

We have nothing to worry about shipping Wine in this humble little distro :)
Google's Android too hadn't nothing to worry from SUN before it start to sell *too many devices*



IMHO: Microsoft is actually in mode "Make Them Happy"; if you check the FAQs on their site (thanks to those who provide the link) they "officially" state that even some Microsoft's product _**may**_ update even if the WGA detect that you're using Wine.
At this time Microsoft is in a game where it win nearly all battles; so they don't need to *make new kind of battles with linux*.

Simply:
Microsoft do not need *engage* some fight with Linux.

The bad news is that these are indeed the kind of battles Linux's need.

---

### Post by Sean Moran on 2010-11-20
I'm no expert, but it would seem to me a little bit like trying to sue someone for looking at a computer screen with Windows on the desktop through a shop-window.

Microsoft is not necessarily the owner of that shop-window, and they certainly don't own the street outside, and they don't own my eyes either.

---

### Post by ellis rowell on 2010-11-20
It's an interesting discussion about Wine.

I have a Windows application which was written by an English company in the 1990's. It has worked on all versions of Windows from 95 to XP (I ditched Windows when Vista came out). It also works the same under Wine. I can only assume that it contains it's own lib files so is independent of the Windows libs.

---

### Post by Sean Moran on 2010-11-20
Put it this way: If Windows had been open-source then there'd never have been any need for Wine in the first place.  One or the other, admit the errors of Redmond or else the most it comes down to is felony-copyright infringement or whatever.

Wine is just a way to see the other half.  It is not there to try to replicate closed-source software.  If you don't have Windows, then Wine isn't much use at all, is it?


---o0o---
To put it nicely, one might say that Wine just opens the curtains for Windows.

---

### Post by forrestcupp on 2010-11-20
> **3Miro said:**
> 
Reverse engineering windows is illegal.

That's not true.  Clean room reverse engineering of Windows is not illegal.  That's what the ReactOS team is attempting to do.  The only time they ever ran into trouble was in 2006 when a claim was made that a small part of the code was disassembled from Windows XP and copy/pasted into the project.  From that point on, they have done an internal audit, making all code visible and accountable, and they haven't had any more trouble from Microsoft or anyone else.

Clean room reverse engineering is perfectly legal.  Not only that, but everyone (including MS) is aware that software patents and IPs most likely wouldn't even hold up in a US court.  That's why they all resort to scare tactics and name calling instead of actually going to court and solving anything.  If IPs end up holding up in court, then everyone in the world is in trouble.

---

### Post by alexfish on 2010-11-20
> **forrestcupp said:**
> That's not true.  Clean room reverse engineering of Windows is not illegal.  That's what the ReactOS team is attempting to do.  The only time they ever ran into trouble was in 2006 when a claim was made that a small part of the code was disassembled from Windows XP and copy/pasted into the project.  From that point on, they have done an internal audit, making all code visible and accountable, and they haven't had any more trouble from Microsoft or anyone else.

Clean room reverse engineering is perfectly legal.  Not only that, but everyone (including MS) is aware that software patents and IPs most likely wouldn't even hold up in a US court.  That's why they all resort to scare tactics and name calling instead of actually going to court and solving anything.  If IPs end up holding up in court, then everyone in the world is in trouble.

Well put

the only question to most of what I have read , Is this

Are there any software applications Specific to  Microsoft(Windows) that have anything in nature to

"It is illegal to operate or run this software on a Linux platform"

---

