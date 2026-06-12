---
title: "FOSS Licensing"
date: 2010-06-25
forum: The Cafe
---

### Post by Penguin Guy on 2010-06-25
For all you programmers and artists out there - what license(s) do you use, and why?

Personally I always put my work in the Public Domain.

---

### Post by mickie.kext on 2010-06-25
> 
Public Domain:
Hopefully a big company like Windows or Mac will use your work (meaning a cheaper/better OS for end-customers)
Companies rarely pass savings to their customers. They prefer to keep their prices high and increase profit margin, instead of cutting prices due to smaller development cost.

---

### Post by Dustin2128 on 2010-06-25
GPL, apple and microsoft shall not touch my work[-(

---

### Post by phrostbyte on 2010-06-25
I've used MIT, Apache, and GPL in the past. I prefer GPL but I will contribute to any project worthwhile on the license their original authors have chosen without any issue.

---

### Post by splicerr on 2010-06-25
> **Penguin Guy said:**
> For all you programmers and artists out there - what license(s) do you use, and why? Also, what do you think about the below notes?

[LIST]
[*]**Public Domain:**
[LIST]
[*]Actual freedom
[*]Hopefully a big company like Windows or Mac will use your work (meaning a cheaper/better OS for end-customers)
[/LIST]
 
[*]**GPL:**
[LIST]
[*]Big companies won't profit from your work
[*]Big companies will be forced, by the GPL, to contribute code
[/LIST]
 
[/LIST]
*I plan on adding more to this list a later date. I'll also try to keep it updated with other peoples opinions.*

Wrong. Big companies do profit from GPL code and are not forced to contribute code, so  your notes are bollocks.

---

### Post by earthpigg on 2010-06-25
you know Red Hat is a fortune 500 company, right?

and IBM?

you would be correct in stating that the business model for Free Software isn't exactly the same as Microsoft's model, but it's certainly viable.

Keep in mind also that Linus Torvalds is a multi millionaire.

---

### Post by nrs on 2010-06-25
> **Penguin Guy said:**
> what do you think about the below notes?

BSD trolled.

---

### Post by Penguin Guy on 2010-06-26
> **mickie.kext said:**
> Companies rarely pass savings to their customers. They prefer to keep their prices high and increase profit margin, instead of cutting prices due to smaller development cost.
But Microsoft are forced to cut prices a little due to competition, especially so when their monopoly ends.

> **splicerr said:**
> Wrong. Big companies do profit from GPL code and are not forced to contribute code, so  your notes are bollocks.
Okay, I'll just remove that one then.

---

### Post by Xianath on 2010-06-26
What GPL does differently from other less restrictive FOSS licenses is that it discourages forks. If a company takes a project and spins it off without contributing back (i.e. non-GPL license) then community improvements would have to be merged back at the expense of the company, or not at all. A smart company will find a business model that works under those restrictions and use them to its advantage.

At my previous job we used a fork of Apache 1.3.26 as a basis for one of our products. You don't want to know what a security scanner would do with that... What this meant was a constant backporting effort which would consume a huge amount of resources. It took us five years to migrate to Apache 2, and all we had added was a custom access module!

At my current job, I am managing a product which is basically based off a major FOSS project. This time around, we do contribute back. I will actually be seeking managerial approval to open our resources (build farm, test farm, etc.) to all contributors. It's not FOSS zealotry, but pure business sense. With a proper CI framework in place, commits won't be pushed upstream unless they pass all automation tests. This way, we can focus on the parts that are important to us, and the community can do whatever they feel is important to them, but working on the same trunk and constantly testing it would ensure that we won't be stepping on each other's toes. It's a win-win.

Unfortunately, most companies can't just use GPL FOSS as-is because, with a few notable exceptions, it's not tailored for enterprise needs. If they have to add their own IP to make it work for them but have to share it with everyone else, it can easily be seen as a poor business strategy.

---

### Post by alexan on 2010-06-26
> **Penguin Guy said:**
> [LIST][*]**GPL:**
[LIST]
[*]Big companies will be forced, by the GPL, to contribute code
[/LIST]
...not

GPL offer different layer of usability of the source code. What big companies can't do is hide (compile) other's GPL source code and act (steal) as the code was developed by them.

---

### Post by Tibuda on 2010-06-26
[url=http://sam.zoy.org/wtfpl/][quote=http://sam.zoy.org/wtfpl/]there is a long ongoing battle between gpl zealots and bsd fanatics, about which license type is the most free of the two. In fact, both license types have unacceptable obnoxious clauses (such as reproducing a huge disclaimer that is written in all caps) that severely restrain our freedoms. The wtfpl can solve this problem.

When analysing whether a license is free or not, you usually check that it allows free usage, modification and redistribution. Then you check that the additional restrictions do not impair fundamental freedoms. The wtfpl renders this task trivial: It allows everything and has no additional restrictions. How could life be easier? You just do what the **** you want to. [/quote][/url]
:)

---

### Post by earthpigg on 2010-06-26
> # GPL:

    * Big companies won't profit from your work
    * Big companies will be forced, by the GPL, to contribute code

also note that this only applies if you distribute the compiled program.

if google modified the kernel, for example, to make it more responsive to a zillion google searches a minute... they wouldn't have to share those modifications with anyone.

plenty of ways to make money using free software, as long as you aren't stuck on the obsolete put-it-in-a-shrink-wrapped-box-at-retail-stores paradigm.

---

### Post by Penguin Guy on 2010-07-02
People seem to have been concentrating more on nitpicking my arguments than the original question, so the arguments have been removed.
> **Penguin Guy said:**
> For all you programmers and artists out there - what license(s) do you use, and why?

---

### Post by betrunkenaffe on 2010-07-02
If I was releasing to the world, GPL or BSD, depending on if I wanted to force distribution with code or not.

If I was truly concerned with freedom, should go into public domain.

---

### Post by macogw on 2010-07-02
I use GPL so people can't mooch.

---

### Post by RiceMonster on 2010-07-02
The only true license is the [WTFPL](http://sam.zoy.org/wtfpl/).

---

### Post by chessnerd on 2010-07-02
For things that I am comfortable with releasing to the public, I go MIT because I like its simplicity. For things that I keep to myself, well, it doesn't really matter then...

---

### Post by Simian Man on 2010-07-02
I also like the simplicity and freedom of the MIT license.  Even if I wanted to enforce a compyleft (which I don't), I don't think I could bring myself to use the GPL because of the moralistic BS in the preamble.

---

### Post by Penguin Guy on 2010-07-02
This seems very illogical:
> **macogw said:**
> I use GPL so people can't mooch.
**mooch**: ask for and get free; be a parasite

---

### Post by nrs on 2010-07-02
> **Penguin Guy said:**
> This seems very illogical:

**mooch**: ask for and get free; be a parasite
Is donating blood the same thing as being sucked on by a leech or mosquito?

---

### Post by Penguin Guy on 2010-07-02
> **nrs said:**
> Is donating blood the same thing as being sucked on by a leech or mosquito?
Pretty much.

---

### Post by phrostbyte on 2010-07-02
> **Penguin Guy said:**
> This seems very illogical:

**mooch**: ask for and get free; be a parasite

The main difference between the GPL and PD or BSD-like licenses, is that BSD-type licenses allow people to take your code and give back nothing in return. If that is what you want, that's fine. Personally I'm really not into being some proprietary software company's volunteer software developer.

---

### Post by cgroza on 2010-07-02
> **RiceMonster said:**
> The only true license is the [WTFPL]("http://sam.zoy.org/wtfpl/").
That is a joke, right?

---

### Post by chessnerd on 2010-07-02
> **cgroza said:**
> That is a joke, right?

It is actually a legitimate license with uses in countries that don't allow for people to directly place their work in the public domain and some software used in Ubuntu is licensed by the WTFPL. Version 2 of the license was written by a Debian project leader. It is officially recognized as GPL-compatable.

[http://en.wikipedia.org/wiki/WTFPL](http://en.wikipedia.org/wiki/WTFPL)

---

### Post by Bachstelze on 2010-07-02
Mostly depends on my mood of the day. Generally 2-clause BSD, but sometimes GPL or WTFPL.

---

### Post by nrs on 2010-07-02
> **Penguin Guy said:**
> Pretty much.
I actually find that very disturbing. It appears you don't seem to distinguish between charity and exploitation, between sharing and taking.

---

### Post by Random_Dude on 2010-07-02
> **RiceMonster said:**
> The only true license is the [WTFPL]("http://sam.zoy.org/wtfpl/").

That's hilarious. xD

---

### Post by Bachstelze on 2010-07-02
> **nrs said:**
> I actually find that very disturbing. It appears you don't seem to distinguish between charity and exploitation, between sharing and taking.

Welcome to the GPL world, where it's between "us" and "them".

---

### Post by phrostbyte on 2010-07-02
> **Bachstelze said:**
> Welcome to the GPL world, where it's between "us" and "them".

Sounds like a good sound bite, but do you want to elaborate on that?

---

### Post by earthpigg on 2010-07-02
> **RiceMonster said:**
> The only true license is the [WTFPL](http://sam.zoy.org/wtfpl/).

the great thing about the wtfpl is that it can be used for anything covered by copyright. [i used it here]("http://sites.google.com/site/masonux/home/legal-stuff") because [this page]("http://sites.google.com/site/masonux/home/ease-of-use") is potentially useful for anyone doing an ubuntu command line or minimalist install, and i wanted to make it very clear that anyone is welcome to... well, do wtf they want with that text.

when i was [teaching myself python]("http://ubuntuforums.org/showthread.php?t=1350984") (it didn't take long for me to hit a wall due to my then very limited math knowledge) and posting a few scripts on this forum for feedback, i did public domain.

when/if i ever learn enough to create non-trivial software, i will likely harbor no specific loyalties to any particular license. right license for the right purpose. even the [Microsoft Reciprocal License]("http://www.microsoft.com/opensource/licenses.mspx#Ms-RL") has certain admirable features - it's concise, and it has a patent trolling clause. while i strongly disagree with current US Patent Law, i could see where that clause could be useful in certain situations. (though i would still consult a lawyer. that license only works if one owns a patent or >9000. at that point, a lawyer wouldn't be a horrible investment.)

for an operating system and core components, i like the GPL.

i also like the creative commons [Creator-Endorsed]("http://questioncopyright.org/creator_endorsed") logo.

---

### Post by Bachstelze on 2010-07-02
> **phrostbyte said:**
> Sounds like a good sound bite, but do you want to elaborate on that?

It's the whole purpose of the GPL: a piece of GPL code can only be used in a GPL project.  Essentially, it divides the world between "us", GPL projects who can use the code, and "them", the rest of the world, who can't.  This is contrary to the BSD-style licenses, which permits code to be used in any project, regardless of the license that project chooses for its own code.

The GPL divides, excludes, discriminates, and antagonizes.  The BSD-style licenses view the world as one, irrespective of personal choices.

---

### Post by RJARRRPCGP on 2010-07-02
> **ricemonster said:**
> the only true license is the [wtfpl](http://sam.zoy.org/wtfpl/).

lol

---

### Post by earthpigg on 2010-07-02
> **phrostbyte said:**
> 
> Welcome to the GPL world, where it's between "us" and "them".
Sounds like a good sound bite, but do you want to elaborate on that?

many regard the GPL as less free than others because of the clauses that essentially make the software GPL'd perpetual and forever, and thus limit developer freedom.

GPL lovers, on the other hand, regard user freedom as more vital than developer freedom. inflammatory statement could be something like this: "Why do you use the BSD license? You must see yourself as a potential digital colonizer of non-technically oriented people's hardware, or you would use the GPL."

as the GPL is incompatible with every other Free Software License out there, it creates a culture that makes certain GPL fans ideologically incompatible with all others. hence: > Welcome to the GPL world, where it's between "us" and "them".

anyone recall the Free Software filesystem that is/was being developed for Unix-like systems by a company that intentionally picked a license that made it impossible to implement the filesystem on a GPL'd system (ie: Linux) without clean-room reverse engineering it, making it a completely separate program, or something to that effect? that isn't exactly how it worked out, but it was something silly like that. something that would not have been possible if not for the GPL's "GPL or GTFO" aspects.

this stuff is all interesting to look at and observe, as a non-developer outsider, but i can understand why it would be incredibly frustrating for any involved party if they just wanted to make great software and maybe earn a living. and i understand how/why emotions could potentially get out of hand.

---

### Post by donkyhotay on 2010-07-02
I use GPLv3 on my [ own personal FOSS projects](code.google.com/p/tether). 
</end shameless plug> (c;

---

### Post by nrs on 2010-07-02
> **Bachstelze said:**
> 
The GPL divides, excludes, discriminates, and antagonizes.
That's pretty harsh (absurd) language. The fact that you're freely using GPL'd software when clearly you don't care for it is proof your statement is hogwash. Anyone can use it, even the people that hate it. 

The GPL places one restriction:  You can't take it, claim it as your own, and deny to other people the freedoms that were granted to you. How on earth is that considered offensive to people? It's basic fairness, and if we were talking about anything other than software licenses people would agree, but there's some sort of break down in reality when it comes to licenses. 

Example: People lack the appropriate tools, you decide to share yours around the campsite. Eventually, someone declares it's their hammer, and they're not going to give it back or a let other people use it.

How would you feel? How would you respond? 

Can you come up with a logical response to this question or do you just have inflammatory rhetoric?

---

### Post by earthpigg on 2010-07-02
> **nrs said:**
> The GPL places one restriction:  You can't take it, claim it as your own, and deny to other people the freedoms that were granted to you. How on earth is that considered offensive to people?

not quite. you also can't mix-and-match various pieces of Free Software together in order to create a new (and presumably better) product, if some is GPL'd and some is not GPL'd. the GPL is compatible with relatively few other Free Software licenses. hence, the exclusion. 

BSD, Mozilla, Apache... software released under all of these can (as i understand it) be mixed and matched all day long, and still remain Free Software. not so with GPL'd software.

---

### Post by Dr. C on 2010-07-02
> **Dustin2128 said:**
> GPL, apple and microsoft shall not touch my work[-(

The GPL does not prevent Apple and Microsoft from distributing your work or creating derived works from it. By the way I for one have obtained GPL licensed software from Microsoft.

---

### Post by earthpigg on 2010-07-02
here is a [specific list]("http://www.gnu.org/licenses/license-list.html#GPLIncompatibleLicenses") of excluded licenses. you cannot mix-and-match code from GPL'd Free Software with anything licensed under these.

you can, however, mix-and-match BSD licensed Free Software with any of these.

BSD, and other permissive licenses, grant maximum freedom to ***developers***.

GPL grants maximum protections of freedoms to ***users***.

the debate, imo, eventually boils down to which group is more important to the software author.

I wonder: if the kernel where licensed GPLv_**3**_, which of the current line of Android phones would be allowed to exist? Certainly, any phone carrier that had a desire to have the phone's hardware detect if an unofficial version of the phone's software was being used.... would be SOL if they wanted to use Android. That would likely remove any possibility of there existing Android phones with unlimited data plans. Many Android users are thus very fortunate that the kernel uses GPLv_**2**_.

I don't see any ethical dilemma with cheap smartphones being tied to a particular, and enforcible, set of rules. "We are selling you this cheap Android smartphone and providing a cheap unlimited data plan... on the condition that you don't modify the Android software to make it a wifi hotspot." That doesn't strike me as a violation of the Four Freedoms, nor does it strike me as unethical. I could always go purchase an unlocked Android phone at full price, couldn't I? People locking themselves into a restrictive contract isn't something that software licenses should address. People should have that choice. GPLv3 effectively removes this choice from the user.

---

### Post by mickie.kext on 2010-07-02
> **earthpigg said:**
> not quite. you also can't mix-and-match various pieces of Free Software together in order to create a new (and presumably better) product, if some is GPL'd and some is not GPL'd. the GPL is compatible with relatively few other Free Software licenses. hence, the exclusion. 

BSD, Mozilla, Apache... software released under all of these can (as i understand it) be mixed and matched all day long, and still remain Free Software. not so with GPL'd software.

Not true. That is anti-GPL thinking that various corporation are pushing right now. 

You can't take EPL code and copy it into MPL source file. You can't take Apache code and put it in MPL source file. You can make separate source files which one is MPL and other Apache. In case of EPL, whole binary must be EPL (EPL has LGPL-like linking clause but is vaguer and it is somethimes unclear what's derivative work). But if you want to make that kind of project with lots of different licenses, you'd be doing more consulting with lawyers - about what you can copy/paste and what you have to export to separate binary - than actually programming. It would be a mess. 

GPL is written to remove such a mess. I can understand that there is a reason to release things under non-copyleft license (which is GPL compatible), but I don't understand GPL-like licenses that are GPL incompatible. Those are usually written because of hate for GPL.

I think there is 4 licenses that make sense for new projects: AGPLv3, GPLv3, LGPLv3 and Apache v2. Of course, GPLv2 has to stick around because of Linux kernel.

Interesting read, Bruce Perens agree with me about choice of licenses:
[http://itmanagement.earthweb.com/osrc/article.php/3803101/Bruce-Perens-How-Many-Open-Source-Licenses-Do-You-Need.htm](http://itmanagement.earthweb.com/osrc/article.php/3803101/Bruce-Perens-How-Many-Open-Source-Licenses-Do-You-Need.htm)

---

### Post by Penguin Guy on 2010-07-02
> **nrs said:**
> I actually find that very disturbing. It appears you don't seem to distinguish between charity and exploitation, between sharing and taking.
In the real world I understand that you would give charity only to those who most need it because you can't afford to give away stuff to anyone who asks for it. However, it costs no money to give away software - so there's no need to be bothered about who takes it.

FYI I was speaking about the blood in a purely analogical way - it's not going anywhere.

---

### Post by earthpigg on 2010-07-02
about two paragraphs into that article, mickie. def gonna bookmark it. thanks.

how do you feel about my comments about droid phones, as an argument in favor of keeping GPLv2 around, potentially for uses beyond the kernel?

---

### Post by nrs on 2010-07-02
> **earthpigg said:**
> about two paragraphs into that article, mickie. def gonna bookmark it. thanks.

how do you feel about my comments about droid phones, as an argument in favor of keeping GPLv2 around, potentially for uses beyond the kernel?
do they tivo it? that's the only potential problem I can think of.

---

### Post by Penguin Guy on 2010-07-02
> **nrs said:**
> That's pretty harsh (absurd) language. The fact that you're freely using GPL'd software when clearly you don't care for it is proof your statement is hogwash. Anyone can use it, even the people that hate it.
Agree.

> **nrs said:**
> The GPL places one restriction: You can't take it, claim it as your own, and deny to other people the freedoms that were granted to you.
[LIST]
[*]you can't take any software, only copy it
[*]you could claim PD software as your own, but people would know you're lying
[*]most PD software is probably easily available on the internet so it's practically impossible to 'deny to other people the freedoms that were granted to you'

[/LIST]

> **nrs said:**
> How on earth is that considered offensive to people? It's basic fairness, and if we were talking about anything other than software licenses people would agree, but there's some sort of break down in reality when it comes to licenses.

Example: People lack the appropriate tools, you decide to share yours around the campsite. Eventually, someone declares it's their hammer, and they're not going to give it back or a let other people use it.

How would you feel? How would you respond? 

Can you come up with a logical response to this question or do you just have inflammatory rhetoric?
A virtual hammer is not the same as a hammer. You can make a copy of a virtual hammer at no expense, whereas a real hammer costs money to make. I'd have no problem with a person making a copy of my hammer and doing what they like with it.

---

### Post by earthpigg on 2010-07-02
> The other ambitious thing that GPL3 does is that it insists that the software in an embedded device be modifiable in situ. This is so that Open Source operating systems are still possible in the future. 

You see, we need computers to run them on. Today, we can get cheap motherboards for desktops, upon which we can install Linux and other Free Software. In the future, people won't use desktops as much as they use embedded devices like cell phones and web slates. So, we want to make sure that we can run new Free Software on embedded devices that already come with Free Software out of the box.

ah. so the concern, in the case of Android* phones, is that (because of GPLv2 instead of v3) one day there may be a time that no company sells truly unlockable Android phones. All firmware on all Android phones on the market will detect if the OS has been modified, and refuse to boot.

yup, that would suck.

The alternative, however, with the GPLv3 is that OEMs and other outfits won't be able to sell products using Free Software that trade in user freedom for low prices. This will mean that such options will not be available to the consumer.

I tend to believe in the "where there is a demand, a supply will exist" mantra. If there is a demand for an unrestricted Droid phone, and it can be legally manufactured and sold, it will be done. If there is a demand for a motherboard that doesn't shut down if it detects that the OS being used is not Red Hat Enterprise Linux, I believe such a motherboard will exist. That last one is hypothetical, of course, but RHEL could certainly work with Asus to put a motherboard like this on the market if they wished. And I am both ok with that. It could potentially be worth considering if Company X plans to use RHEL for the next 7 years on the 1,000 workstations they are about to purchase anyways. (The assumption here is that the company gets 1,000 supercheap desktops, but they only work using RHEL.)

If we magically replace GPLv2 with GPLv3 in all cases where it exists, we lose out on "$99 Droid phone with a 2 year contract that includes unlimited data". It isn't a choice I would make, but it's certainly one that I feel should be available.


*im using Android, but i suppose the same applies to any Free Software smartphone OS.

---

### Post by mickie.kext on 2010-07-02
> **earthpigg said:**
> about two paragraphs into that article, mickie. def gonna bookmark it. thanks.

how do you feel about my comments about droid phones, as an argument in favor of keeping GPLv2 around, potentially for uses beyond the kernel?

Well, I don't like tivioisation and I beleive that there is nothing to like about it. But carriers might not be in violation of GPLv3. Under GPLv3, you enable people to run modified code on their devices. As in, device must not shut down if detects changed software. It doesn't say that you have to keep offering free service or warranty to those people who actually hack their devices. Some arrangement could be made, GPLv3 is not as scary as some corporation would like people to think (Apple, IBM, Microsoft... I am looking at you!).

---

### Post by earthpigg on 2010-07-02
> **nrs said:**
> 
> how do you feel about my comments about droid phones, as an argument in favor of keeping GPLv2 around, potentially for uses beyond the kernel?

do they tivo it? that's the only potential problem I can think of.

if it hasn't been done already, im sure it will be soon. did the picture i painted of how doing so would benefit both the cell phone carrier and certain customers make sense?

-customer plans to use AT&T Wireless for the next two years anyways, wants unlimited data, and has no desire to turn his cell phone into a wifi hotspot for use as his primary ISP.

-AT&T likes 2 year contracts, and while willing to provide unlimited data for the cell phone, wants assurances that the cell phone will not become the customers primary ISP (because, guess what else AT&T sells? :P ).

So, AT&T has a Droid phone built that ceases functioning if it detects that the OS has been modified to allow it to become a wifi hotspot. Customer gets a $500 phone for $79.99, and AT&T gets what it wants.

and this doesn't restrict my freedom or your or anyone elses... because we are still able to purchase a Droid phone from someone other than AT&T, if we wish.

If the kernel was GPLv3, the customer above would not be able to purchase that hypothetical Droid phone because it would not be allowed to exist.

---

### Post by Penguin Guy on 2010-07-02
I find the whole GPL 'forced freedom' idea quite paradoxical. Same with BSD people that get angry over re-licensing: the whole point of BSD is complete freedom, if you start demanding that software be re-released under the BSD license rather than the GPL, you may as well use the GPL.

---

### Post by earthpigg on 2010-07-02
> **mickie.kext said:**
> Under GPLv3, you enable people to run modified code on their devices. As in, device must not shut down if detects changed software. It doesn't say that you have to keep offering free service or warranty to those people who actually hack their devices. Some arrangement could be made, GPLv3 is not as scary as some corporation would like people to think (Apple, IBM, Microsoft... I am looking at you!).

(EDIT: I'm using AT&T as an example. Playing devil's advocate with AT&T as the devil. I have no idea that AT&T actually does this.)

Ah. So, tell me if my understanding is correct: the cell phone must keep working -- but AT&T isn't under any obligation to keep providing a service as if the software had not been modified, and they can write a contract that stipulates a $50000000 fee and ceasing service or something if they wish?

How would this argument be addressed:

"The very definition of a cellular phone implies being able to connect to a cellular network. By ceasing to provide cell coverage if the customer modifies the software, AT&T has in effect violated the GPLv3. While the cell phone does not refuse to function as a hand-held computer, AT&T's refusal to allow it to function as a cellular phone is, in effect, causing the cellular phone to cease working."

Or has this already been addressed?

---

### Post by Penguin Guy on 2010-07-02
> **earthpigg said:**
> the cell phone must keep working -- but AT&T isn't under any obligation to keep providing a service as if the software had not been modified
I'm no lawyer, but the GPL authors *are*, I'm sure they will have thought of this already.

---

### Post by phrostbyte on 2010-07-02
> **Penguin Guy said:**
> I find the whole GPL 'forced freedom' idea quite paradoxical. Same with BSD people that get angry over re-licensing: the whole point of BSD is complete freedom, if you start demanding that software be re-released under the BSD license rather than the GPL, you may as well use the GPL.

It's about as paradoxical as the US Bill of Rights actually being a set of restrictions. The GPL is basically the Bill of Rights applied to software.

---

### Post by mickie.kext on 2010-07-02
> **earthpigg said:**
> Ah. So, tell me if my understanding is correct: the cell phone must keep working -- but AT&T isn't under any obligation to keep providing a service as if the software had not been modified, and they can write a contract that stipulates a $50000000 fee and ceasing service or something if they wish?

How would this argument be addressed:

"The very definition of a cellular phone implies being able to connect to a cellular network. By ceasing to provide cell coverage if the customer modifies the software, AT&T has in effect violated the GPLv3. While the cell phone does not refuse to function as a hand-held computer, AT&T's refusal to allow it to function as a cellular phone is, in effect, causing the cellular phone to cease working."

Or has this already been addressed?

I didn't know what AT&T does, but if that is the case, then they would be violating GPLv3. GPL is designed to disallow monopolies and make competition, and it is kinda natural that monopolist like AT&T is at foul with it.

---

### Post by earthpigg on 2010-07-02
> **phrostbyte said:**
> It's about as paradoxical as the US Bill of Rights actually being a set of restrictions.

something few people actually realize. :D

We see this misunderstanding when people accuse a company or private individual of "infringing freedom of speech".

---

### Post by earthpigg on 2010-07-02
> **mickie.kext said:**
> I didn't know what AT&T does, but if that is the case, then they would be violating GPLv3. GPL is designed to disallow monopolies and make competition, and it is kinda natural that monopolist like AT&T is at foul with it.

i don't know that AT&T does this, I'm using them as an example. Edited the post above to clarify that.

Then we agree that, if the kernel was GPLv3, there would very likely be no possibility of $500 Droid phones being sold by a cellular carrier for $79 with a 2 year contract that includes unlimited data?

---

### Post by Penguin Guy on 2010-07-02
> **earthpigg said:**
> Then we agree that, if the kernel was GPLv3, there would very likely be no possibility of $500 Droid phones being sold by a cellular carrier for $79 with a 2 year contract that includes unlimited data?
I agree. Public Domain and BSD licenses save the end user a lot of money, which is the main reason reason I am against the GPL.

---

### Post by mickie.kext on 2010-07-02
> **earthpigg said:**
> i don't know that AT&T does this, I'm using them as an example. Edited the post above to clarify that.

Then we agree that, if the kernel was GPLv3, there would very likely be no possibility of $500 Droid phones being sold by a cellular carrier for $79 with a 2 year contract that includes unlimited data?

Well, I would rather pony up for a truly Free phone, like say Nokia. Nokia never tivoize. And I am not in the US so I don't have to deal wit AT&T. 

That AT&T offer sound to me like a classic Faustian deal, which people sadly accept without thinking. But if it is not a real deal, then you have me confused.

---

### Post by mickie.kext on 2010-07-02
> **Penguin Guy said:**
> I agree. Public Domain and BSD licenses save the end user a lot of money, which is the main reason reason I am against the GPL.

How BSD saved money when Android is GPL? 

And in given example money is not saved because of software license, it is saved because AT&T subsidize costs of hardware. Hardware is not in public domain. They could sell Win Mobile phone at same price.

---

### Post by earthpigg on 2010-07-02
> **Penguin Guy said:**
> I agree. Public Domain and BSD licenses save the end user a lot of money, which is the main reason reason I am against the GPL.

Possible Alternative:

Dual-License the Kernel GPLv3 and Proprietary, with the Linux Foundation (or some similar organization) being the owner. Then, if Company X wanted to implement tivoisation... An agreement would need to be reached with the Linux Foundation: they would need to pay royalty fees to the Linux Foundation, and they would still need to grant ownership of any improvements to the Linux Foundation (who would then release those improvements as GPLv3/Proprietary dual license.

-Linux and Droid both remain Free Software.
-The $79 Droid business model is still an option to consumers.
-Lot's of cash for the Linux Foundation to distribute in a reasonable manner to developers and whatnot.
-Linux users potentially benefit from those improvements.
-All Droid users, including those not using tivo-ised phones, potentially benefit from those improvements.

Just something that popped into my head. Don't know if it's the best idea in the world. Since the kernel fork for Droid has already happened, since Google's Droid-specific modifications will likely never be branched back into the mainline kernel, and since the kernel was GPLv2 at that point, it's already to late. But, for future forks?

---

### Post by earthpigg on 2010-07-02
> **mickie.kext said:**
> Well, I would rather pony up for a truly Free phone, like say Nokia. Nokia never tivoize. And I am not in the US so I don't have to deal wit AT&T. 

That AT&T offer sound to me like a classic Faustian deal, which people sadly accept without thinking. But if it is not a real deal, then you have me confused.

It isn't a real deal (yet! and, as far as i know), but it's what I would do if I placed myself in the shoes of the CEO of AT&T and thought I could get away with it -- and, based on my understanding of the GPLv2, they certainly can get away with it.

I recall that when I was in Finland, all you needed to do to switch carriers is switch SIM cards. It was a very trivial task to purchase pre-paid SIM cards, pop them into whatever phone you happened to have, and call away. If it's similar where you live, that may be the cause of the confusion. This is not the case in the US -- many (most? almost all?) cell phones sold come locked into a specific carrier for at least the duration of the initial contract. After the contract is up, you can theoretically (though it is like pulling teeth) call the cell carrier that sold you the phone and get them to give you a magic code that will allow you to use the phone with another carrier. 

I don't know that the scenario I described is specifically the case with AT&T and Droids -- but it is certainly how it normally works here in the states. You can have all the cheap/free cell phones you want, but you need to sign an X Year contract, and the phone is completely locked down. It may indeed be a Faustian deal, but it is also the norm.

So, as an American, it isn't to far fetched to assume that the exact same thing that happens with every single other cell phone - will happen with Droid phones (since it is not protected by GPLv**_3_**).

---

### Post by earthpigg on 2010-07-02
This post is mostly to clarify why I make certain assumptions about how cellular carriers operate that others, particularly Europeans, may find bizzare.

Maybe the attached image will make certain assumptions of mine easier to fathom for folks from nations that have better consumer protection laws. without even trying, i know just from what i circled that only Sprint SIM cards will work in this phone. if i go to the sprint website, i can get all sorts of cheap phones - but i know ahead of time that they will also only work with sprint, and that certain deals will include a longer contract with Sprint, and that if i start trying to modify the software they will all turn into bricks with voided warranties. 

these are all basic assumptions that i make, if i choose not to go with a $500 smartphone sold by someone ***other than*** my cellular carrier. So, if I saw a cheap Droid phone sold by Verizon/Sprint/AT&T/etc... guess what my basic assumptions would be? especially since Droid is _**not**_ GPLv3... :D

Where you ask "Is this specific scenario true?", an American would think "Right, ***of course*** this is how an American cellular carrier would operate... this is how they ***always*** operate."

Americans have, or will have, two choices:
1) $500 Droid phone, unlocked, usable on any carrier, hackable, etc.
2) Cheap Droid phone, locked down to draconian levels.

Because Droid is not special. Those are the American's choices with *every* Smartphone OS.

As I understand it (the understanding I seek to clarify), the only difference that GPLv3 would make is removing choice two. (Remember that GPL and "us versus them" thing being discussed earlier?)... And that is why I am skeptical of GPLv3 - if my understanding is correct.

Does that clarify things? :D

---

### Post by phrostbyte on 2010-07-02
> **earthpigg said:**
> It isn't a real deal (yet! and, as far as i know), but it's what I would do if I placed myself in the shoes of the CEO of AT&T and thought I could get away with it -- and, based on my understanding of the GPLv2, they certainly can get away with it.

I recall that when I was in Finland, all you needed to do to switch carriers is switch SIM cards. It was a very trivial task to purchase pre-paid SIM cards, pop them into whatever phone you happened to have, and call away. If it's similar where you live, that may be the cause of the confusion. This is not the case in the US -- many (most? almost all?) cell phones sold come locked into a specific carrier for at least the duration of the initial contract. After the contract is up, you can theoretically (though it is like pulling teeth) call the cell carrier that sold you the phone and get them to give you a magic code that will allow you to use the phone with another carrier. 

I don't know that the scenario I described is specifically the case with AT&T and Droids -- but it is certainly how it normally works here in the states. You can have all the cheap/free cell phones you want, but you need to sign an X Year contract, and the phone is completely locked down. It may indeed be a Faustian deal, but it is also the norm.

So, as an American, it isn't to far fetched to assume that the exact same thing that happens with every single other cell phone - will happen with Droid phones (since it is not protected by GPLv**_3_**).

Your idea isn't bad, but it's not really feasible. The Linux Foundation does not actually own the copyright to the entirety of Linux. Actually - no single entity does. Everyone who contributes to Linux retains their copyright to that portion of the kernel. So you are talking about potentially hundreds of entities that would have to all agree to this scheme.

---

### Post by splicerr on 2010-07-02
Either GPL or proprietary. If I release open source code I expect some reciprocity, the GPL is not perfect but comes closest to accomplish that. Sorry, I'm not in the business of charity.

---

### Post by mickie.kext on 2010-07-02
> **earthpigg said:**
> This post is mostly to clarify why I make certain assumptions about how cellular carriers operate that others, particularly Europeans, may find bizzare.

Maybe the attached image will make certain assumptions of mine easier to fathom for folks from nations that have better consumer protection laws. without even trying, i know just from what i circled that only Sprint SIM cards will work in this phone. if i go to the sprint website, i can get all sorts of cheap phones - but i know ahead of time that they will also only work with sprint, and that certain deals will include a longer contract with Sprint, and that if i start trying to modify the software they will all turn into bricks with voided warranties. 

these are all basic assumptions that i make, if i choose not to go with a $500 smartphone sold by someone ***other than*** my cellular carrier. So, if I saw a cheap Droid phone sold by Verizon/Sprint/AT&T/etc... guess what my basic assumptions would be? especially since Droid is _**not**_ GPLv3... :D

Where you ask "Is this specific scenario true?", an American would think "Right, ***of course*** this is how an American cellular carrier would operate... this is how they ***always*** operate."

Americans have, or will have, two choices:
1) $500 Droid phone, unlocked, usable on any carrier, hackable, etc.
2) Cheap Droid phone, locked down to draconian levels.

Because Droid is not special. Those are the American's choices with *every* Smartphone OS.

As I understand it (the understanding I seek to clarify), the only difference that GPLv3 would make is removing choice two. (Remember that GPL and "us versus them" thing being discussed earlier?)... And that is why I am skeptical of GPLv3 - if my understanding is correct.

Does that clarify things? :D

Yes, that was the confusion. In my country cellphones are Libre. 

So to get back at point, GPLv3 wouldn't necessarily remove option 2. Only contract would have to be changed. 

It could be like this:

Cheap phone which is locked down but users are provided with way to unlock it. Upon unlocking, users have to pay full price for the phone to get network connectivity. And by that they effectively reverse it to option one.

Everybody happy. 

As for dual-licensing Linux, that would be nice because it would make tivoisation cost money to those who practice it. ANd that would force them to rethink their practices. But no way that all developer can agree on that.

---

### Post by earthpigg on 2010-07-02
> **mickie.kext said:**
> 
It could be like this:

Cheap phone which is locked down but users are provided with way to unlock it. Upon unlocking, users have to pay full price for the phone to get network connectivity. And by that they effectively reverse it to option one.

Everybody happy.

Would GPLv3 allow that form of DRM? I'm assuming [Pick-ur-Carrier] would feel the need to make it more involved than a "push here to unlock" button...


> As for dual-licensing Linux, that would be nice because it would make tivoisation cost money to those who practice it. ANd that would force them to rethink their practices. But no way that all developer can agree on that.

Yes, it was a pipe dream :P

However, it would be possible for other projects. The skype client is about to be open sourced. Maybe some of the 10-foot-interface projects that aim to convert the PC into a multimedia center -- "TiVo our project all you want, but you must pay us to do so, and give code improvements back to us!"... meanwhile, do-it-yourself types still get to DIY and benefit from the corporate-sponsored improvements.

---

### Post by mickie.kext on 2010-07-02
> **earthpigg said:**
> Would GPLv3 allow that form of DRM? I'm assuming [Pick-ur-Carrier] would feel the need to make it more involved than a "push here to unlock" button...
Well, we are talking about hypothetical situation and I don't know what exact scenario is in question. Some arangement could be made to honour GPLv3, and they are maybe honouring it now so we are typing for nothing :D 

> **earthpigg said:**
> However, it would be possible for other projects. The skype client is about to be open sourced. Maybe some of the 10-foot-interface projects that aim to convert the PC into a multimedia center -- "TiVo our project all you want, but you must pay us to do so, and give code improvements back to us!"... meanwhile, do-it-yourself types still get to DIY and benefit from the corporate-sponsored improvements.

That is bad if not done corectly. If copyright are held by one company, that company can decide to add proprietary value add (or freedom subtract) components in order to make more people buy that non-GPL version. It is thin line between dual-licensing and "Open-Core" (rotten outside). If project becomes financially dependant on selling non-GPL licenses, then what would be done when people start using only open source? They will add propriatary crud to non-GPL version to make it more attractive and then GPL version is crippleware. 

Think MySQL and recently Eucalyptus Systems. One guy, Marten Mickos, screwed both project with proprietary crud. So it is best not to depend on dual licensing and it is best to have copyrights either assigned to FSF (because they can't dual-license) or shared over few companies.

---

### Post by zekopeko on 2010-07-02
> **earthpigg said:**
> (EDIT: I'm using AT&T as an example. Playing devil's advocate with AT&T as the devil. I have no idea that AT&T actually does this.)

Ah. So, tell me if my understanding is correct: the cell phone must keep working -- but AT&T isn't under any obligation to keep providing a service as if the software had not been modified, and they can write a contract that stipulates a $50000000 fee and ceasing service or something if they wish?

How would this argument be addressed:

"The very definition of a cellular phone implies being able to connect to a cellular network. By ceasing to provide cell coverage if the customer modifies the software, AT&T has in effect violated the GPLv3. While the cell phone does not refuse to function as a hand-held computer, AT&T's refusal to allow it to function as a cellular phone is, in effect, causing the cellular phone to cease working."

Or has this already been addressed?

I don't think something like this is running afoul the GPLv3. As long as you can run the software on the hardware there is no tivotization. If the carrier wants to deny you access to their network because you are using an unsupported version of the OS that is fully their legal right.

When talking about the FSF's interpretation of the GPL one has to understand that what the FSF thinks is legal reality and what actually is legal reality are two different things. The only entity that can interpret the GPL are the courts. FSF's opinion is simply just that, an opinion without any legal power. They are mostly right but there are examples where what they think wouldn't pass in any US court.

Another point to mention (that I read somewhere; can't find the source now) is that companies generally are weary of the GPLv3 because it isn't tested in the real world as much as they would like. What if it opens them to law suits or exposes their intellectual property etc. ? Once the GPLv3 gets battle tested I think we will see more uptake by the more conservative companies.

Personally I think that having more licences is better for the ecosystem. Forcing a mono-culture is never a good thing.

---

### Post by Penguin Guy on 2010-07-19
I personally think this anti-tivoization stuff is nonsense. If you don't want a tivoizalized product, don't buy one.

---

### Post by mickie.kext on 2010-07-19
> **Penguin Guy said:**
> I personally think this anti-tivoization stuff is nonsense. If you don't want a tivoizalized product, don't buy one.

And what to do when everything is tivoized? 

Contrary what you might think, free market doesn't always work in interest of consumer. If companies agree that they have common interest in pushing tivoization as a standard, they will all push it and every device will be tivoised because it is more profitable to do so. 

If that happens, you will be kicking yourself but it will be too late. And I will laugh and say: "I told you so". :D

---

### Post by Penguin Guy on 2010-07-19
> **mickie.kext said:**
> And what to do when everything is tivoized? 

Contrary what you might think, free market doesn't always work in interest of consumer. If companies agree that they have common interest in pushing tivoization as a standard, they will all push it and every device will be tivoised because it is more profitable to do so. 

If that happens, you will be kicking yourself but it will be too late. And I will laugh and say: "I told you so". :D

Every product? That's impossible. As long as there is a market for non-tivoized products, there will be non-tivoized products.

---

### Post by zekopeko on 2010-07-19
> **Penguin Guy said:**
> Every product? That's impossible. As long as there is a market for non-tivoized products, there will be non-tivoized products.

Not to mention consumer protection laws.

---

### Post by flukeairwalker on 2010-07-19
All my poetry is licensed under a CC Attribution-ShareAlike license. [http://creativecommons.org/licenses/by-sa/3.0/us/](http://creativecommons.org/licenses/by-sa/3.0/us/) It was the fairest license I could find without ripping me off, but at the same time let others be inspired and create their own works. And if anyone doesn't like it they can always ask for my permission to break the license.

---

### Post by beetleman64 on 2010-07-19
While I should stress that I'm not a programmer, I would probably license my work under a BSD-style license so that it remains fairly free, but gives others better flexibility.

---

### Post by Penguin Guy on 2010-07-20
> **flukeairwalker said:**
> All my poetry is licensed under a CC Attribution-ShareAlike license. [http://creativecommons.org/licenses/by-sa/3.0/us/](http://creativecommons.org/licenses/by-sa/3.0/us/) It was the fairest license I could find without ripping me off, but at the same time let others be inspired and create their own works. And if anyone doesn't like it they can always ask for my permission to break the license.
I'm not bothered about attribution. In fact I found an image of mine (Public Domain) included as the logo of a Linux distribution without any credit. I'm not bothered, I don't need a little tag with my name on, I'm just happy that I've helped in some way.

[http://ubuntuforums.org/showthread.php?t=1521319](http://ubuntuforums.org/showthread.php?t=1521319)

---

### Post by Sakrecoer on 2012-08-06
I use this one:

Open Human License 1.1
[http://sakrecoer.com/set/log/humanity-open-human-licence-v11](http://sakrecoer.com/set/log/humanity-open-human-licence-v11)

---

### Post by KiwiNZ on 2012-08-06
The licence on this thread is expired. Time to close

---

