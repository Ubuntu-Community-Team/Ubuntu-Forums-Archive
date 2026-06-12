---
title: "Ubuntu Technical Board Mono Position Statement"
date: 2009-06-30
forum: The Cafe
---

### Post by Technoviking on 2009-06-30
[From [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000584.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000584.html) ]

The Ubuntu Technical Board has been asked for a position statement on the use of C#, specifically the Mono implementation, by applications in Ubuntu.

These applications, as well as the Mono stack, were proposed for inclusion like any other application and underwent the same review process that all new applications and platforms undergo before being accepted into the archive.

With specific regard to the default installed application set, applications have been reviewed and compared against each other on merit and features.  These often take place during the Ubuntu Developer Summits, most recently over the default media player.


A common concern cited about Mono is the patent position, largely it seems due to the originator of the C# language and associated ECMA standards.

The Ubuntu Project takes patent issues seriously, and the Ubuntu Technical Board is the governance body that handles allegations of patent infringement.  The Ubuntu Technical Board strives to engage with rights holder openly in terms of the code that we ship.  If a rights holder claims a patent infringement applies to said code, the Technical Board will commit to a review of the claim.

The Ubuntu Technical Board has received no claims of infringement against the Mono stack, and is not aware of any such claims having been received by other similar projects.

It is common practice in the software industry to register patents as protection against litigation, rather than as an intent to litigate. Thus mere existence of a patent, without a claim of infringement, is not sufficient reason to warrant exclusion from the Ubuntu Project.

(While the Ubuntu project wishes to be responsive to patent infringement claims, we cannot commit to the assessment and review of claims made by anyone other than the registered rights holder.)


Given the above, the Ubuntu Technical Board sees no reason to exclude Mono or applications based upon it from the archive, or from the default installation set.

Since the Mono stack is already a dependency of the default installation set for many remixes of Ubuntu, including the Desktop Edition, there is no reason to consider a dependency on Mono as an issue when suggesting applications for the default set.

(Other remixes may obviously consider the CD Size implications if an application would introduce the Mono platform to the set.)


Scott
on behalf of the [Ubuntu Technical Board]("http://www.ubuntu.com/community/processes/techboard")

---

### Post by .Maleficus. on 2009-06-30
Sticky!  Please oh please sticky this so the Mono threads can stop!


Edit:  Nevermind :) and thank you.

---

### Post by ghindo on 2009-07-01
Thank you for posting this.  I suspect anti-Mono true believers won't be swayed much by this statement, but nevertheless, an official, clarifying statement is helpful.

---

### Post by Dragonbite on 2009-07-01
I think this is a great move by the Technical Board, to put down for everybody to see their position. This should help reduce fanning the flames.

I can go either way regarding Mono being pre-installed really, so long as it is all available from the default repositories (not a 3rd party repository somebody has to manually add).

Thank you UTB for your statement.

---

### Post by aesis05401 on 2009-07-01
> **Technoviking said:**
> [From [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000584.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000584.html) ]

A common concern cited about Mono is the patent position, largely it seems due to the originator of the C# language and associated ECMA standards.



The statement seems pretty balanced, but the portion quoted above was a little befuddling.  All the patent talk I have seen is related to the fact that the Novell says Mono infringes MS patents, and then paid for a license from MS. 

That is all pretty straightforward,  and both companies have public statements posted that the patent protection agreement explicitly includes Mono.

Here is the joint statement which can also be found at Microsoft.com:[http://www.novell.com/linux/microsoft/openletter.html](http://www.novell.com/linux/microsoft/openletter.html).

Am I missing something here?

---

### Post by directhex on 2009-07-01
> **aesis05401 said:**
> Novell says Mono infringes MS patents

They specifically say the opposite

[http://www.novell.com/linux/microsoft/community_open_letter.html](http://www.novell.com/linux/microsoft/community_open_letter.html)

> Importantly, our agreement with Microsoft is in no way an acknowledgment that Linux infringes upon any Microsoft intellectual property. When we entered the patent cooperation agreement with Microsoft, Novell did not agree or admit that Linux or any other Novell offering violates Microsoft patents.

---

### Post by aesis05401 on 2009-07-02
> **directhex said:**
> They specifically say the opposite

[http://www.novell.com/linux/microsoft/community_open_letter.html](http://www.novell.com/linux/microsoft/community_open_letter.html)

You and I have been here before. They then state:
*"Under the patent agreement, customers will receive coverage for Mono, Samba, and OpenOffice as well as .NET and Windows Server."*

What coverage if there is no violation?  I don't believe Novell just decided to fork a ton of cash over to MS.  

Something just doesn't seem right.. but I guess I am done talking about it.

---

### Post by mdsmedia on 2009-07-02
That's not exactly the opposite. All it says is that no patent infringements are acknowledged in making the agreement.

That, to me, doesn't necessarily reflect on the position with Mono.

The Ubuntu team's statement is a bit more comforting.

---

### Post by directhex on 2009-07-02
> **aesis05401 said:**
> What coverage if there is no violation?  I don't believe Novell just decided to fork a ton of cash over to MS.

Do you have insurance on your home?

And Novell didn't pay anything - if anything they got paid courtesy of Microsoft's sales of SLES. Also don't forget how many fundamental patents are owned by Novell and infringed by Microsoft

---

### Post by directhex on 2009-07-02
> **mdsmedia said:**
> That's not exactly the opposite. All it says is that no patent infringements are acknowledged in making the agreement.

That, to me, doesn't necessarily reflect on the position with Mono.

The Ubuntu team's statement is a bit more comforting.

Okay, here's the Mono position, from [http://www.mono-project.com/FAQ:_Licensing](http://www.mono-project.com/FAQ:_Licensing)

>  With the new Novell/Microsoft agreement, will the patent policy change?

Mono is a community project, and as such, we will continue to implement the policy of not integrating knowingly infringing code into Mono.

And we will continue to follow the steps outlined in the previous topic if code that potentially infringes is found: finding prior art, finding different implementation techniques, or if none of those are possible, removing the code from Mono. 

---

### Post by Sef on 2009-07-02
> Okay, here's the Mono position, from [http://www.mono-project.com/FAQ:_Licensing](http://www.mono-project.com/FAQ:_Licensing)

Mono Licenses:

> ** What license or licenses are you using for the Mono Project? ** 
We use three open source licenses: 
 
[LIST]
[*] The C# compiler is dual-licensed under the MIT/X11 license and the [GNU General Public License]("http://www.opensource.org/licenses/gpl-license.html") (*[http://www.opensource.org/licenses/gpl-license.html](http://www.opensource.org/licenses/gpl-license.html)*) (GPL).
[/LIST]
 
[LIST]
[*] The tools are released under the terms of the [GNU General Public License]("http://www.opensource.org/licenses/gpl-license.html") (*[http://www.opensource.org/licenses/gpl-license.html](http://www.opensource.org/licenses/gpl-license.html)*) (GPL).
[/LIST]
 
[LIST]
[*] The runtime libraries are under the [GNU Library GPL 2.0]("http://www.gnu.org/copyleft/library.html#TOC1") (*[http://www.gnu.org/copyleft/library.html#TOC1](http://www.gnu.org/copyleft/library.html#TOC1)*) (LGPL 2.0).
[/LIST]
 
[LIST]
[*] The class libraries are released under the terms of the [MIT X11]("http://www.opensource.org/licenses/mit-license.html") (*[http://www.opensource.org/licenses/mit-license.html](http://www.opensource.org/licenses/mit-license.html)*) license.
[/LIST]
 Both the Mono runtime and the Mono C# Compiler are also available under a proprietary license for those who can not use the LGPL and the GPL in their code. 


---

### Post by wersdaluv on 2009-07-02
Thanks. I love mono-based apps most especially GNOME Do. 

I just don't want patent issues to happen one day. I don't think I know enough about the issue so I'll just trust your decisions.

EDIT: 
How certain are we that there will be no patent problems, btw?

---

### Post by Methuselah on 2009-07-02
> **wersdaluv said:**
> Thanks. I love mono-based apps most especially GNOME Do. 

I just don't want patent issues to happen one day. I don't think I know enough about the issue so I'll just trust your decisions.

EDIT: 
How certain are we that there will be no patent problems, btw?

This is exactly one concern.
Mono is not one application but a framework on which multiple applications are likely to depend.
And if it is included by default in most distributions that will encourage the creation of more open source programs that are dependent on it.
So if we are complacent now and adopt mono widely in the face patent issues we might later have to pay royalties or do quite a bit of rooting out/rewriting in the event of a successful legal challenge.
[All these programs would probably still work unchanged on a certain other .NET implementation, BTW]
If mono were a single/self contained application, I for one, would care a lot less but having a framework pulled from under you could be quite disruptive.

But that is the worst case. 
And since the deed has already been done, I hope it remains just a fantastic worst case.
In the best case, Mono becomes to .NET as linux has become to Unix, being almost the primary example of its kind.

---

### Post by wersdaluv on 2009-07-02
> **Methuselah said:**
> This is exactly one concern.
Mono is not one application but a framework on which multiple applications are likely to depend.
And if it is included by default in most distributions that will encourage the creation of more open source programs that are dependent on it.
So if we are complacent now and adopt mono widely in the face patent issues we might later have to pay royalties or do quite a bit of rooting out/rewriting in the event of a successful legal challenge.
[All these programs would probably still work unchanged on a certain other .NET implementation, BTW]
If mono were a single/self contained application, I for one, would care a lot less but having a framework pulled from under you could be quite disruptive.

But that is the worst case. 
And since the deed has already been done, I hope it remains just a fantastic worst case.
In the best case, Mono becomes to .NET as linux has become to Unix, being almost the primary example of its kind.
That's my point. I am dependent on Tomboy notes and GNOME-Do but in the event of such a crisis you mentioned, my desktop setup as a user will be messed up and developers will have a real pain in the butt too. 

If the technical board is confident enough, there must be a greater certainty that there would be no legal crisis, than not.

---

### Post by mdsmedia on 2009-07-03
> **Sef said:**
> Mono Licenses:

Not going to repost what Sef has quoted above, and not being a developer myself, and not being ofe (that e needs a little "`" above it I think) with licensing, that's the one thing that bothers me in that page.

directhex has provided the most comforting post with that link, though.

As someone said, above, I'm not an expert in these things and I have to trust the Ubuntu team. They have more experience in this sort of thing than I do, and their whole philosophy gives me more comfort than anything.

---

### Post by AICollector on 2009-07-03
Ok, one question.

IF MS decide they don't like Mono, and just so happen to target Ubuntu or one of the distros that include it, would Ubuntu pull it?



Note; The reason I don't run Mono is because it's slow and rather heavy on resources. a SECONDARY reason is that it could harm my favorite distro, hence my and others protectiveness.

---

### Post by jittopjose on 2009-07-04
i still believe that technology is not a barrier, its just a mindset. i dont know what bad will happen to the opensource world if mono is included in ubuntu.

---

### Post by directhex on 2009-07-04
> **AICollector said:**
> IF MS decide they don't like Mono, and just so happen to target Ubuntu or one of the distros that include it, would Ubuntu pull it?

If Microsoft issues a Cease & Desist over somethingorother? Yes - same as with anything else in the distro

---

### Post by pt123 on 2009-07-04
I gave Banshee (1.50) a try, used the new RB importer plugin to import 2000 songs. There is a bug to get around it you need to copy your database to the old RB location in ~/.gnome2/...

It has some nice features like the equaliser. But the GUI is so unresponsive, when you change songs it goes into cardiac arrest for 5-10 seconds.
THe CPU usage is 7% when playing a song when you change songs it goes to 80% then to 100%. 
Even you exit Banshee it goes to 100%. 
It uses 150MB of RAM throughout.

While Rhythmbox uses 3% when playing goes to 15% when changing songs.
Only uses 22MB of RAM

My system is not old either AMD 4850e dual core, 2GB of RAM. 
Using Jaunty.

I really don't how you could make this the default media player esp. with Ubuntu targetting Netbooks.

---

### Post by zekopeko on 2009-07-04
> **pt123 said:**
> I gave Banshee (1.50) a try, used the new RB importer plugin to import 2000 songs. There is a bug to get around it you need to copy your database to the old RB location in ~/.gnome2/...

It has some nice features like the equaliser. But the GUI is so unresponsive, when you change songs it goes into cardiac arrest for 5-10 seconds.
THe CPU usage is 7% when playing a song when you change songs it goes to 80% then to 100%. 
Even you exit Banshee it goes to 100%. 
It uses 150MB of RAM throughout.

While Rhythmbox uses 3% when playing goes to 15% when changing songs.
Only uses 22MB of RAM

My system is not old either AMD 4850e dual core, 2GB of RAM. 
Using Jaunty.

I really don't how you could make this the default media player esp. with Ubuntu targetting Netbooks.

report bugs and help the developers. and you will be glad to know that banshee should be the default player in UNR. i run it on asus 1000hg and it preform admirably. welcome to the 21st century.

---

### Post by DoubleClicker on 2009-07-06
The problem I have with Mono has nothing to do with license issues.  I object to it being in the default installation because it's more unnecessary bloatware.  It's bad enough that we have Java and Python, we don't need yet another tool, for lazy programmers to waste system  resources.  What ever happened to the days when programmers wrote optimized code in C, that ran in fast and required little memory.

---

### Post by ghindo on 2009-07-06
> **DoubleClicker said:**
> The problem I have with Mono has nothing to do with license issues.  I object to it being in the default installation because it's more unnecessary bloatware.  It's bad enough that we have Java and Python, we don't need yet another tool, for lazy programmers to waste system  resources.  What ever happened to the days when programmers wrote optimized code in C, that ran in fast and required little memory.How is Mono bloated?

---

### Post by directhex on 2009-07-06
> **DoubleClicker said:**
> The problem I have with Mono has nothing to do with license issues.  I object to it being in the default installation because it's more unnecessary bloatware.  It's bad enough that we have Java and Python, we don't need yet another tool, for lazy programmers to waste system  resources.  What ever happened to the days when programmers wrote optimized code in C, that ran in fast and required little memory.

Are you paying them to only write programs you approve of?

And you can write bloat in ANY language - take a look at (C-based) Evolution or (C++-based) OpenOffice.org

---

### Post by RiceMonster on 2009-07-06
> **DoubleClicker said:**
> The problem I have with Mono has nothing to do with license issues.  I object to it being in the default installation because it's more unnecessary bloatware.  It's bad enough that we have Java and Python, we don't need yet another tool, for lazy programmers to waste system  resources.  What ever happened to the days when programmers wrote optimized code in C, that ran in fast and required little memory.

You know what? C is so inefficient. What happened to the days when programers wrote optimized code in assembly, that ran fast and required little memory? C programmers are just too lazy to work directly with stacks and registers.

Now, you may think that sounds ridiculous, but I've had someone tell me that C is inefficient because it takes however many more CPU cycles to run through a few C lines versus asm lines. This complaint is no different than what you're making. If you're complaining about Ubuntu having too much in the default install, do a minimal install, or switch to something like Slackware, Arch, Gentoo, etc.

---

### Post by Jimmyfj on 2009-07-06
I've been following many different discussions about Mono in various forums on the Internet. And everywhere people complaint about **possible** patent infringement and an almost unimaginable fear of Microsoft. Sometimes this fear is right out childish, and at other times it's a more reasonable fear based in facts and previous events purely controlled by Microsoft.

The thing is that no case has come forward about Mono yet. I honestly doubt there will ever be one in the future. Microsoft simply can not afford or risk a trial over Mono. They *know* that they could not possibly win a case based on patent or copyright infringement because if they do they'll have to put forward all needed evidence in every case revealing things they are better of not showing in public. You know it and I know it.

So, until proven otherwise you all need to trust UTB and Canonical. They do not put themselves at risk towards Microsoft, nor do they put their users at risk in any way.

---

### Post by Dragonbite on 2009-07-06
If Microsoft were to try and strong-arm patents via Mono then it would cost them a lot, give them a PR nightmare and ultimately would not stop Linux much because while distros begin removing their Mono, Red Hat and other systems will still be plugging along without it.

So it isn't a "magic bullet" for Microsoft against Linux.

---

### Post by FuturePilot on 2009-07-07
Maybe this will clarify things
[http://tirania.org/blog/archive/2009/Jul-06.html]("http://tirania.org/blog/archive/2009/Jul-06.html")

---

### Post by Sand Lee on 2009-07-07
Spread the news! :wink:

[http://digg.com/microsoft/Microsoft_...legal_concerns]("http://digg.com/microsoft/Microsoft_issues_patent_promise_dispels_Mono_legal_concerns")

---

### Post by DoubleClicker on 2009-07-07
> **RiceMonster said:**
> You know what? C is so inefficient. What happened to the days when programers wrote optimized code in assembly, that ran fast and required little memory? C programmers are just too lazy to work directly with stacks and registers.

Now, you may think that sounds ridiculous, but I've had someone tell me that C is inefficient because it takes however many more CPU cycles to run through a few C lines versus asm lines. This complaint is no different than what you're making. If you're complaining about Ubuntu having too much in the default install, do a minimal install, or switch to something like Slackware, Arch, Gentoo, etc.

I don't think that sounds ridiculous at all. My friend Bill wrote most of the original Macintosh desktop environment in 68000 assembly, and it fit into 128K of ROM.

---

### Post by directhex on 2009-07-07
> **DoubleClicker said:**
> I don't think that sounds ridiculous at all. My friend Bill wrote most of the original Macintosh desktop environment in 68000 assembly, and it fit into 128K of ROM.

If only we had processors faster than the 68000 today - if we did, we could write apps which made better use of developers' time by not forcing them to jump through hoops that their damn computer should be jumping through for them

Alas :(

---

### Post by cdekter on 2009-07-12
Deleted.

---

### Post by Dr. C on 2009-07-18
The FSF's take on mono and The Microsoft Community Promise:

[http://www.fsf.org/news/2009-07-mscp-mono]("http://www.fsf.org/news/2009-07-mscp-mono")

When is comes to the legal issues surrounding Free Software and by extension Open Source this is a source to take into consideration.

---

### Post by directhex on 2009-07-18
> **FineE said:**
> The FSF's take on mono and The Microsoft Community Promise:

[http://www.fsf.org/news/2009-07-mscp-mono]("http://www.fsf.org/news/2009-07-mscp-mono")

When is comes to the legal issues surrounding Free Software and by extension Open Source this is a source to take into consideration.

I'd feel better if they'd done some basic research.

Tomboy does categorically not use any of the System namespace beyond the System and System.Xml assemblies, which are under the CP. Their claim otherwise is either gross negligence or intentional lying.

---

### Post by fsando on 2009-07-18
> **FineE said:**
> The FSF's take on mono and The Microsoft Community Promise:

[http://www.fsf.org/news/2009-07-mscp-mono]("http://www.fsf.org/news/2009-07-mscp-mono")

When is comes to the legal issues surrounding Free Software and by extension Open Source this is a source to take into consideration.

I agree this should be taken absolutely seriously.

There is another thing that have me wondering. 
As far as I am aware of there are four Mono applications; banshee, fspot, gnome-do and tomboy. I've used fspot, gnome-do and fspot. Maybe it's just me but the only one I found somewhat useful was fspot. In the end I removed them - nothing to do with mono at all - I wasn't even aware of mono as anything contentious at the time - I just tend to remove things I don't use.

So now there is this question nagging me: Why this intense fight over these four (not particularly important or interesting) programs?

Just to clarify - I don't want to say anything negative about the apps they are probably great - even I didn't find them useful - but they are not, like standing out as THE most important apps of their time or anything like that. And apparently there are only the four of them.

---

### Post by directhex on 2009-07-18
> **fsando said:**
> Just to clarify - I don't want to say anything negative about the apps they are probably great - even I didn't find them useful - but they are not, like standing out as THE most important apps of their time or anything like that. And apparently there are only the four of them.

You missed a 0.

There are about 40 apps in Ubuntu using Mono.

---

### Post by fsando on 2009-07-19
> **directhex said:**
> You missed a 0.

There are about 40 apps in Ubuntu using Mono.

Ups! 

I didn't know that. I've only ever heard of those 4 and I've never encountered any of the other 36. I know because I always just removed Mono as it was the lazy way of removing the those few apps I felt I didn't need.

EDIT:
I looked at the dependencies of mono-runtime (in Synaptic) and there are quite a few apps at least 40+ though I only know beagle (in addition to those already mentioned).

---

### Post by gnomeuser on 2009-07-19
> **fsando said:**
> I agree this should be taken absolutely seriously.

There is another thing that have me wondering. 
As far as I am aware of there are four Mono applications; banshee, fspot, gnome-do and tomboy. I've used fspot, gnome-do and fspot. Maybe it's just me but the only one I found somewhat useful was fspot. In the end I removed them - nothing to do with mono at all - I wasn't even aware of mono as anything contentious at the time - I just tend to remove things I don't use.

So now there is this question nagging me: Why this intense fight over these four (not particularly important or interesting) programs?

Just to clarify - I don't want to say anything negative about the apps they are probably great - even I didn't find them useful - but they are not, like standing out as THE most important apps of their time or anything like that. And apparently there are only the four of them.

It is not a battle over a few applications. It's a battle to let tools have a level playing field within Linux and let the best technology win out.

Mono and it's stack presents a set of tools that allows people to create great applications for Linux (and other platforms), we currently have around 40 appications (this number does not include libraries) included in Ubuntu, with 4 being highly popular (Banshee, gnome-do, tomboy and f-spot). They are highly popular for a reason but let's forget that for a moment. 

These people are in effect saying that we shouldn't let those exist, we shouldn't let people innovate using tools other than what they approve. In the process they refuse to acknowledge fact and evidence contrary to their preconceived notions, they slander developers and their followers outright issue personal attacks again distributions, corporations and volunteers who spend their time and money to improve Linux.

Some of us see something wrong with this, especially since their concerns have been addressed and they remain free to write their own software or live without the comfort of our software. Instead they seek to mandate that we be disallowed to contribute on an even playing field. 

This is about discrimination. We say there should be none, anybody should be free to contribute which ever way they please, and their contribution should have a right to be evaluated for inclusion on the same grounds as anything else.

---

### Post by fsando on 2009-07-19
What are the advantages to having Mono installed by default on every desktop?

To me *personally* there doesn't seem to any immediate advantage - I've always removed it (nothing to do with the current debacle but simply a matter of removing things I don't need the easy way).

But the distros then? What advantages are for them?

I look at it like this: the whole computer market is not about OSs but about applications. Imagine that all the apps are flowers and the OS is the soil in which they grow. People don't care about the soil but about the flowers.

There are essentially two distinct markets, private users (desktop) and corporate users (desktop and server). What all promoters of Linux is in effect proposing is that the private market should cease to exist - i.e. desktop OS should be free, as in "you can't make money selling a desktop OS".

All the Linux vendors have said that much several times (and how Microsoft must love that future, will it affect Apple too?). 

Now, why do these Linux vendors keep pushing a monetary black whole? Well, actually they do so only reluctantly (except for Canonical) and only because Canonical/Ubuntu threatens to steal the limelight. Why is Canonical pushing it then? Because they're are essentially following the path of Microsoft (and before them WordPerfect) - if the general user use *your* system at home they will look favourably at your offerings in the corporate market.

So why is Mono important then? The flowers/apps.
There is a vast installed base of .NET apps out there. When Ubuntu and Suse are pushing into the corporate market they need a reliable platform for the businesses to migrate to. They need to develop a fertile ground for all those apps to grow in. It takes time to evolve such a platform and it needs to be a first class citizen.

Why is Microsoft helping in this?

There are a couple of reasons I can think of. One is that EU is 'on their case'. They need to be seen to cooperate.

Another is that Microsoft may be almost a monoply in the home user/desktop market but they are not nearly as dominant in the server market (it is just one of a set of players and it's not even the biggest, I believe).

They want to see their technology (c#/mono, whatever) furthered at the expense of java (and others?). In this there may be a common interest between Linux and Ms. Linux want strong offerings in the corporate market, Ms wants to see its own tech spread as wide as possible (market share).

This may be just as dangerous to Ms as it, at the moment, might seem to Linux. If Mono is able to outpace Ms's own development efforts Mono will be the de facto standard not Ms's own implementation. In that case legal threats would not be of much consequence, I believe, as Ms would in effect threaten its own customers rather than its competitors.

As an aside: what effect does bilski have on this whole affair?

---

### Post by fsando on 2009-07-19
> **gnomeuser said:**
> It is not a battle over a few applications. It's a battle to let tools have a level playing field within Linux and let the best technology win out.

Thanks, I'm grappling with this whole issue. 

Originally when I first heard that Mono was a .NET clone/implementation my only thought was Oh God! All my experience with .NET apps on a my desktop XP were horrible. Would that be the same on Linux? The first apps I then met was beagle and early beta versions gnome-do which sort of confirmed my XP-impressions. Well, new to Linux and not familiar with release early, release often, I decided that Mono was probably not that important to me (the Joe user type).

Anyway I find this public discussion (as well as many others in the open source community) extremely enlightening and important. We all got our say and there is a pressure on everybody to actually explain themselves. I know it's not always nice or pleasant but it makes what eventually happens so much stronger, and so much more solidly founded.

I'm sure, regardless of how unfairly it feels now, it is having an impact that eventually leads to some form of consensus and (I believe) better programs in the future.

---

### Post by directhex on 2009-07-19
> **fsando said:**
> What are the advantages to having Mono installed by default on every desktop?

To me *personally* there doesn't seem to any immediate advantage - I've always removed it (nothing to do with the current debacle but simply a matter of removing things I don't need the easy way).

But the distros then? What advantages are for them?

I look at it like this: the whole computer market is not about OSs but about applications. Imagine that all the apps are flowers and the OS is the soil in which they grow. People don't care about the soil but about the flowers.

There are essentially two distinct markets, private users (desktop) and corporate users (desktop and server). What all promoters of Linux is in effect proposing is that the private market should cease to exist - i.e. desktop OS should be free, as in "you can't make money selling a desktop OS".

All the Linux vendors have said that much several times (and how Microsoft must love that future, will it affect Apple too?). 

Now, why do these Linux vendors keep pushing a monetary black whole? Well, actually they do so only reluctantly (except for Canonical) and only because Canonical/Ubuntu threatens to steal the limelight. Why is Canonical pushing it then? Because they're are essentially following the path of Microsoft (and before them WordPerfect) - if the general user use *your* system at home they will look favourably at your offerings in the corporate market.

So why is Mono important then? The flowers/apps.
There is a vast installed base of .NET apps out there. When Ubuntu and Suse are pushing into the corporate market they need a reliable platform for the businesses to migrate to. They need to develop a fertile ground for all those apps to grow in. It takes time to evolve such a platform and it needs to be a first class citizen.

Why is Microsoft helping in this?

There are a couple of reasons I can think of. One is that EU is 'on their case'. They need to be seen to cooperate.

Another is that Microsoft may be almost a monoply in the home user/desktop market but they are not nearly as dominant in the server market (it is just one of a set of players and it's not even the biggest, I believe).

They want to see their technology (c#/mono, whatever) furthered at the expense of java (and others?). In this there may be a common interest between Linux and Ms. Linux want strong offerings in the corporate market, Ms wants to see its own tech spread as wide as possible (market share).

This may be just as dangerous to Ms as it, at the moment, might seem to Linux. If Mono is able to outpace Ms's own development efforts Mono will be the de facto standard not Ms's own implementation. In that case legal threats would not be of much consequence, I believe, as Ms would in effect threaten its own customers rather than its competitors.

That's actually a reasonable layperson analysis.

It's not (and has never been) about installing Mono by default. It's about installing the apps that the Desktop Team feel are best by default - which means Tomboy and F-Spot. The libraries needed by those apps are just a side effect (and yes, that includes the Mono runtime).

---

### Post by fsando on 2009-07-19
> **directhex said:**
> That's actually a reasonable layperson analysis.

It's not (and has never been) about installing Mono by default. It's about installing the apps that the Desktop Team feel are best by default - which means Tomboy and F-Spot. The libraries needed by those apps are just a side effect (and yes, that includes the Mono runtime).

That may well be the motivation of the Desktop Team but what are the motivations for Novell's investment in Mono - I guess it's not just to have yet another tool for great apps and 'Hey, we just discovered it's compatible with .NET'.

They set out to specifically make sure that corporate applications dependent on .NET would also run on Suse, that is, they want to broadening their offerings in the corporate market. Why is Microsoft interested in supporting a competitor in this endeavour? I'm not thinking conspiracies here just what business sense does it make to them?

---

### Post by directhex on 2009-07-19
> **fsando said:**
> That may well be the motivation of the Desktop Team but what are the motivations for Novell's investment in Mono - I guess it's not just to have yet another tool for great apps and 'Hey, we just discovered it's compatible with .NET'.

NOVELL's investment has largely been in that - but also in making Mono a viable first-choice platform. Which leads to paid licensing to third parties (see: The Sims 3).

The initial years of Mono's life were always about making a first-class Linux development platform. Bear in mind that there was no usable Free Java at the time, either (sorry GCJ folks, it's true)

---

### Post by fsando on 2009-07-19
> **directhex said:**
> NOVELL's investment has largely been in that - but also in making Mono a viable first-choice platform. Which leads to paid licensing to third parties (see: The Sims 3).

The initial years of Mono's life were always about making a first-class Linux development platform. Bear in mind that there was no usable Free Java at the time, either (sorry GCJ folks, it's true)

I did a search for 'sims 3' (didn't know what you meant) and came upon this quote in a comment by one Dylan McCall on boycotnovell:
> Mono is being widely adopted commercially, (for example used by The Sims 3 over MS .Net) because it is actually cross platform. Mono is a completely superior product to Microsoft’s in many ways, so all it needs to do is be strongly adopted (then we just hope Novell actually stands up to the chair throwing) and Mono can call the shots. Heck, I for one think that has already happened to the point that at least Microsoft can’t attack Mono, because in doing that they would be really pissing off EA Games – another very big company.

Which is basically the same as one of my arguments above.

---

### Post by directhex on 2009-07-19
> **fsando said:**
> I did a search for 'sims 3' (didn't know what you meant) and came upon this quote in a comment by one Dylan McCall on boycotnovell:


Which is basically the same as one of my arguments above.

Oh, it's true. Mono 2.4 includes one major feature which will only be copied into Microsoft.NET 5.0 in 2 or 3 years' time (live C# shell w/ process attachment), and Novell are looking to clean up the Mono.Simd namespace for standardization at the ECMA335 level. ECMA is currently in session regarding 334/335, which basically means C# 3 and assorted new (to ECMA, if not new generally) libraries are on the table for inclusion in the standard. And, of course, Novell are participating in the talks. If you've got too much free time, you could ask the GNOME foundation (who are ECMA members) to get you in, too.

---

### Post by Dragonbite on 2009-07-19
> **gnomeuser said:**
> It is not a battle over a few applications. It's a battle to let tools have a level playing field within Linux and let the best technology win out.

That is a VERY nice summary of the issue!  Mind if I quote you elsewhere?

---

### Post by directhex on 2009-07-20
> **directhex said:**
> Oh, it's true. Mono 2.4 includes one major feature which will only be copied into Microsoft.NET 5.0 in 2 or 3 years' time (live C# shell w/ process attachment), and Novell are looking to clean up the Mono.Simd namespace for standardization at the ECMA335 level. ECMA is currently in session regarding 334/335, which basically means C# 3 and assorted new (to ECMA, if not new generally) libraries are on the table for inclusion in the standard. And, of course, Novell are participating in the talks. If you've got too much free time, you could ask the GNOME foundation (who are ECMA members) to get you in, too.

Oh, and I forgot about other details, like Mono having cross-platform full AOT for "thou shall not use JIT" platforms, and Microsoft.NET not, meaning Mono lets you use C# to develop games for Wii, PS3, iPhone - and Microsoft.NET does not

---

### Post by gnomeuser on 2009-07-21
> **Dragonbite said:**
> That is a VERY nice summary of the issue!  Mind if I quote you elsewhere?

Since you ask so politely I don't see why not.

---

### Post by Methuselah on 2009-07-22
A statement that you won't sue users of alternative .NET implementations for patent infringement will probably make it difficult to sue.
Then, the standard compliant parts of mono are likely safe to use and on that basis I think it's fair that mono be given a chance to prove its utility.
Obviously, Microsoft feels it gets something out of this deal but there are opportunities in it for Linux as well.
At this point, I think most of my personal concerns about mono have been sufficiently addressed.

---

