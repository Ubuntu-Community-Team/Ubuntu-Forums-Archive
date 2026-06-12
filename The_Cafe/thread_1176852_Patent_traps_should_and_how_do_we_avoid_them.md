---
title: "Patent traps should and how do we avoid them?"
date: 2009-06-02
forum: The Cafe
---

### Post by satipera on 2009-06-02
I have been reading about mono and how it could be a patent trap should I be avoiding tomboy like redhat are?

---

### Post by Tibuda on 2009-06-02
Mono is based on [ECMA standards]("http://www.mono-project.com/ECMA"). If you are really worried about patents, you should not even use the Linux kernel, which has the support for Microsoft file systems (FAT/NTFS), or OpenOffice, which supports Microsoft Office file formats (doc/xls). There are thousands of small things also.

Would you drop great applications like Tomboy, Banshee or Gnome-Do because of it?

---

### Post by benj1 on 2009-06-02
there are hundreds of threads on this forum about it, and one or two blogs too. 
personally i don't see a problem patent wise, im more worried about people that rely on it to be cross platform. you know the old ms trick embrace, extend, extinguish.
but ignore me everybody seems to have their own opinion on this

---

### Post by satipera on 2009-06-02
I am totally signed up to linux but I am aware that certain software looking for inclusion is more of a risk than others. I am for the moment more worried by mono, do I need to be worried about using mono in 10 years time?

---

### Post by directhex on 2009-06-02
The oft-overlooked issue:

*Free software is immune to "patent traps"*

Let's look at a real-world example: Freetype. Freetype is a font library. It implemented a bunch of code, and the developers were contacted by Apple to say "you're infringing a patent, stop or we sue". What they did was work *around* the supposed patent, to keep the library usable without harming users.

In the case of Mono, people act as if a single *active* threat from an aggressor (if it ever happens) will kill dead apps like Tomboy. This is completely false, in the same way that a single threat against Linux would not kill the kernel dead, and a single threat against Freetype didn't kill it.

Firstly, there's an option of removing infringing code. If it has no adverse effects on the archive (e.g. only used for Windows compatibility) then chunks of source can be deleted from packages, leaving the remainder "safe". Next is the Freetype option of working around code non-destructively. Next is the option of making breaking changes to the framework - we have the source to all the apps, so we can simply patch the apps to cope with a new incompatible API. Worst case: the framework is removed completely. All existing apps wouldn't simply be deleted - their developers would work to port them to things like C++ or Java or Vala.

The apps cannot be killed in a single stroke. And the framework is only there to facilitate the apps. It's non-sensical to assume that an attack against Mono means the end of anything - it means only annoyance, of varying degrees, for packagers and developers.

---

### Post by satipera on 2009-06-02
Ty Directhex for the thoughtful reply. I realise that the framework is there for the app and that if it is attacked there will be a workaround. What I am asking is if there will be less bother if mono is avoided now rather than having to deal with mono patent problems from an interested 3rd party,no names mentioned.

---

### Post by wh0rd on 2009-06-02
> **satipera said:**
> I am totally signed up to linux but I am aware that certain software looking for inclusion is more of a risk than others. I am for the moment more worried by mono, do I need to be worried about using mono in 10 years time?

> **satipera said:**
> I am totally signed up to linux but I am aware that certain software looking for inclusion is more of a risk than others. I am for the moment more worried by mono, do I need to be worried about using mono in 10 years time?

You should be worried about Mono. There are definite gray areas even the Mono developers don't understand. The default claim of ECMA standard as a safety net from future patent issues is false. The ECMA is not protection from future lawsuits. There is a reason why companies like Redhat are relacing Mono based applications like Tomboy with Gnote (Mono-free) applications. 

Why you should worry is related to your question of 10 year span. This is a very valid question, where long term dependency of Mono will make it  breeding grounds for patent traps. As of right now these small projects like Banshee, Blam, Fspot, Gnome-Do, Synapse, and Tomboy easily have better alternatives and can be removed from default installation of Ubuntu. If you are concerned and want to remove Mono completely from your system use this command:

```
sudo apt-get remove --purge mono-common libmono0 mono libmono1.0-cil libmono2.0-cil
```


A list of alternatives for Mono based apps on Linux:

[SIZE="3"]**Media players** [/SIZE]
[INDENT][COLOR="Silver"]Mono: Banshee[/COLOR] [/INDENT]
[INDENT]**Mono-free:** Exaile, Listen, Rhythmbox, Totem.[/INDENT]


[SIZE="3"]**RSS Reader **[/SIZE]
[INDENT][COLOR="Silver"]Mono: Blam[/COLOR][/INDENT]
[INDENT]**Mono-free:** Liferea, Sage (Firefox Extension), Thunderbird's build in RSS.[/INDENT]


[SIZE="3"]**Image Viewer/Organizer**[/SIZE]
[INDENT][COLOR="Silver"]Mono: Fspot[/COLOR][/INDENT]
[INDENT]**Mono-free:** gThumb, Google Picasa.[/INDENT]


[SIZE="3"]**Application launching utilities**[/SIZE]
[INDENT][COLOR="Silver"]Mono: Gnome-Do[/COLOR][/INDENT]
[INDENT]**Mono-free:** Launchy, Katapult (KDE)[/INDENT]


[SIZE="3"]**Notes/Sticky Desktop application **[/SIZE]
[INDENT][COLOR="Silver"]Mono: Tomboy[/COLOR][/INDENT]
[INDENT]**Mono-free:** Gnote.[/INDENT]


[SIZE="3"]**IMing software **[/SIZE]
[INDENT][COLOR="Silver"]Mono: Synapse[/COLOR][/INDENT]
[INDENT]**Mono-free:** Pidgin, Emesene, Empathy.[/INDENT]

---

### Post by directhex on 2009-06-03
> **wh0rd said:**
> If you are concerned and want to remove Mono completely from your system use this command:

```
sudo apt-get remove --purge mono-common libmono0 mono libmono1.0-cil libmono2.0-cil
```

Wrong.

You got that list from "mononono" didn't you. It's wrong there and it's wrong here. "mono" hasn't been in a package since 2007. And libmono{1,2}.0-cil is there to provide translation support - it's anything but a core library.

For Jaunty and below, the "root" packages to remove are libmono0 and mono-common (everything Depends: on those). For Karmic and later, mono-runtime (and libmono0 too, but only on upgrade installs, not fresh installs which won't include that package)

---

### Post by directhex on 2009-06-03
> **satipera said:**
> Ty Directhex for the thoughtful reply. I realise that the framework is there for the app and that if it is attacked there will be a workaround. What I am asking is if there will be less bother if mono is avoided now rather than having to deal with mono patent problems from an interested 3rd party,no names mentioned.

It's your prerogative whether or not to use apps built on a given framework - whether it's C++/Qt, Java, Vala, or whatever. But you need to consider that it's also the choice of other people to pick differently - and that especially counts for people writing apps. Try telling the guy behind Docky (for GNOME Do) to stop using C#, and he'd tell you... well, it'd be impolite, and involve being told to choke on a bucket of something.

Programmers use the tools they want to use. Free Software is a meritocracy - people who are actually *doing things* should be free to use whatever tools they want. Telling programmers what you permit them to use is..... well, the antithesis of Freedom.

Fr'example, I package the Visual Basic.NET compiler. VB.NET, as with VB before it, is a crap language. Absolutely terrible. Never written any, and don't intend to. However, consider the situation of a guy doing a Computer Science degree at a Microsoft-slanted University. The guy's spent 2 years of his course learning VB.NET, has discovered the joys of Free Software and Ubuntu, and wants to contribute - using the skills he has already built up. By offering a VB.NET compiler, they can get straight to work, writing apps for Ubuntu, and leveraging technologies such as GTK# (rather than possibly-patented WinForms) to develop the apps they want using the tools they want.

Now, the list given by wh0rd gives special insight into the anti-Mono "side", because you'll notice that included amongst his list of apps is proprietary, Wine-based software. Apparently, using Wine-based proprietary apps is better than using Free apps, as long as the end goal of removing users' and developers' Freedom is achieved. No, really:
```
jms@osc-franzibald:~$ dpkg -L picasa | grep libwine.so
/opt/google/picasa/3.0/wine/lib/libwine.so.1.0
```

Is that REALLY a better option? Personally, as someone who believes in Freedom, I don't think so - whilst people should be free to use whichever apps they want, even proprietary ones, I'd find the act of *recommending* a non-Free course of action to be distasteful at best

---

### Post by sehe on 2009-06-03
i'd refer to many blogs and slash-dot

this area is well-vetted and the idea that you would get a clear and canned avdise from asking on any forum seems erm..... a bit optimistic[1]


[1] read: naive

---

### Post by ready4thebreak on 2009-06-03
Am I the only one reading this that is completely lost? I looked at the Wiki Page of Mono it from what it looks like this was all settled between Novell and Microsoft in 2006? 

What the hell revelance does this have in anything Ubuntu Beginner forums? Although I am interested in this discussion I'm going to have to request they move this to another forum.

---

### Post by Sef on 2009-06-03
Moved to communtiy cafe.

---

### Post by monsterstack on 2009-06-03
inb4 Moved to Recurring Discussions.

---

### Post by The Toxic Mite on 2009-06-03
> **satipera said:**
> I have been reading about mono and how it could be a patent trap should I be avoiding tomboy like redhat are?

God's sake! Not another mono rant :|

---

### Post by directhex on 2009-06-03
> **The Toxic Mite said:**
> God's sake! Not another mono rant :|

[img]http://www2.apebox.org/wordpress/wp-content/gallery/00-single/ibtlzs8.gif[/img] ?

---

### Post by ssam on 2009-06-03
read about [http://www.openinventionnetwork.com/](http://www.openinventionnetwork.com/) then stop worrying.

then read [http://www.gnu.org/philosophy/fighting-software-patents.html](http://www.gnu.org/philosophy/fighting-software-patents.html) and worry about all software.

---

### Post by wh0rd on 2009-06-03
First of all stop your Mono rant. The OP asked a question about patent traps. So stop trying to derail the thread conversation with ad hominem attacks. 

Your repeated searches on UbuntuForums with the term &#8220;mono&#8221; so you can troll the threads is getting annoying. I'm going to address you once and for all:

> **directhex said:**
> 
Now, the list given by wh0rd gives special insight into the anti-Mono "side", because you'll notice that included amongst his list of apps is proprietary, Wine-based software. Apparently, using Wine-based proprietary apps is better than using Free apps, as long as the end goal of removing users' and developers' Freedom is achieved. 


> **directhex said:**
> 
Is that REALLY a better option? Personally, as someone who believes in Freedom, I don't think so - whilst people should be free to use whichever apps they want, even proprietary ones, I'd find the act of recommending a non-Free course of action to be distasteful at best


There is nothing wrong with using Google Picasa, Google isn't preventing Linux from moving forward. Google embraced Linux unlike Microsoft who still is threatened by the progression of Linux. I bet you use non-free flash and proprietary graphics drivers.

Here's a known list of non-free things that you do use:
 
[LIST=1]
[*]The font, Verdana, you are using on your [blog]("http://www2.apebox.org/wordpress/"), along with 
[*]Lauchpad
[*]Ubuntu kernel has non free blobs
[*]This forum, vBulletin, you are posting on is also not free.
[/LIST] 

Its hilarious considering you actively sought out to prevent Gnote from being included in Debian by [trolling some bogus license issue]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=523093"). Then there is you bad mouthing Gnote on your Blog, [ApeBox]("http://www2.apebox.org/wordpress/rants/93/#comment-768"). Now you want to cry out &#8220;Freedom&#8221; and be a white knight on this thread, while still making comments like this about the Gnote port from Tomboy:

> 
The problem is that it&#8217;s grounded in douchebaggery. Taking somebody&#8217;s code, and making a 1-way change in the license, is a dick move. End of story. Telling a BSD kernel developer &#8220;oh, well you can have all the changes we made to our GPL-only fork of your code, you just need to convert to GPL&#8221; isn&#8217;t a solution in that case, nor in this identical case. It&#8217;s pure and simple douchebaggery.


Now go ahead and change the comments in your blog when no is looking...

---

### Post by directhex on 2009-06-03
> **wh0rd said:**
> First of all stop your Mono rant. The OP asked a question about patent traps. So stop trying to derail the thread conversation with ad hominem attacks.

I was under the impression I had replied to the OP. Posts 5 and 9 to the thread, for those at the back.

> Your repeated searches on UbuntuForums with the term “mono” so you can troll the threads is getting annoying. I'm going to address you once and for all:

UbuntuForums has an INCREDIBLY high post rate compared to other forums I frequent. Hence I filter out topics to post in based on interests. I hadn't noticed that talking about what you know was banned. Can you cite a specific section of forum policy that this contravenes?

> There is nothing wrong with using Google Picasa, Google isn't preventing Linux from moving forward. Google embraced Linux unlike Microsoft who still is threatened by the progression of Linux. I bet you use non-free flash and proprietary graphics drivers.

That's right, I use Flash and NVIDIA drivers. And as an AMD64 user, I have years of experience in just how badly Flash sucks, as a direct result of its proprietary nature.

However, whilst there is nothing "wrong" with using proprietary apps with Wine (like Picasa), it doesn't strike you as even *slightly* disingenuous to recommend Wine as a way to avoid infringing on phantom Microsoft patents?

> Here's a known list of non-free things that you do use:
 
[LIST=1]
[*]The font, Verdana, you are using on your [blog]("http://www2.apebox.org/wordpress/"), along with 
[*]Lauchpad
[*]Ubuntu kernel has non free blobs
[*]This forum, vBulletin, you are posting on is also not free.
[/LIST]

Nice list. You should probably add to that list my games consoles, those are pretty non-Free. Actually, mentioning vBulletin raises a beautiful point - AJAX is Microsoft technology, and is used for things like the forum's Edit Post button.

> Its hilarious considering you actively sought out to prevent Gnote from being included in Debian by [trolling some bogus license issue]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=523093"). Then there is you bad mouthing Gnote on your Blog, [ApeBox]("http://www2.apebox.org/wordpress/rants/93/#comment-768"). Now you want to cry out “Freedom” and be a white knight on this thread, while still making comments like this about the Gnote port from Tomboy:

Ah, yes, *bogus*. Those of us who occasionally find ourselves writing or contributing to Free software take licensing pretty seriously (seriously enough that I personally resolved a wholesale theft of the Linux kernel by a Taiwanese TV card manufacturer) - and just because something is a cause celebre, it does not make it immune from criticism. Gnote's licensing/copyright situation certainly WAS suspect at the time - and was still dreadfully handled by upstream and packager alike. Pretending otherwise is madness. Actually, here's an example. **every word of this forum post, including parts in quote tags, is (c) directhex, because it doesn't say any differently**. Can you understand why this is an incorrect statement? Good.

It should be noted that 1) I performed a package review of Gnote when it was uploaded to REVU, pointing out specific packaging issues that would cause problems, and 2) that independently of me, the Ubuntu archive admins rejected Gnote MULTIPLE times from being uploaded to the archive for having poorly documented copyright (a point which I raised on the original ITP and also in my blog comments, and was criticized for raising).

> Now go ahead and change the comments in your blog when no is looking...

Why would I do that? I stand by my comments. I've made a non-corrective change once to one of my own blog comments, at someone's direct request. On the whole, it's not something I do.

---

### Post by monsterstack on 2009-06-03
Sorry to interrupt the argument, gentlemen, but I have some questions and advice for optimum Ubuntu Forums productivity!

> **directhex said:**
> UbuntuForums has an INCREDIBLY high post rate compared to other forums I frequent. Hence I filter out topics to post in based on interests. I hadn't noticed that talking about what you know was banned. Can you cite a specific section of forum policy that this contravenes?

How do you go about doing that, by the way? One of the things I do is set the "Subscribe to every thread" option in the control panel, and load the forum rss into Thunderbird. Then I just use Thunderbird's folder filters to split the relevant topics into categories of things I've commented on, things I might be interested in, and so on. Make sure you use IMAP to avoid seeing ten billion UF messages in your main inbox when checking it from the web. Works a treat. I used to lose track of all my posts before that. Now I'm mega up-to-date. *All the time*.

---

### Post by directhex on 2009-06-03
> **monsterstack said:**
> Sorry to interrupt the argument, gentlemen, but I have some questions and advice for optimum Ubuntu Forums productivity!



How do you go about doing that, by the way? One of the things I do is set the "Subscribe to every thread" option in the control panel, and load the forum rss into Thunderbird. Then I just use Thunderbird's folder filters to split the relevant topics into categories of things I've commented on, things I might be interested in, and so on. Make sure you use IMAP to avoid seeing ten billion UF messages in your main inbox when checking it from the web. Works a treat. I used to lose track of all my posts before that. Now I'm mega up-to-date. *All the time*.

I just use the forum search, as was implied. The search indexes are cached for 2 hours, so every 2.5 hours or so are when it's appropriate to search for topics of interest

---

### Post by alternatealias on 2009-06-03
> **directhex said:**
> Now, the list given by wh0rd gives special insight into the anti-Mono "side", because you'll notice that included amongst his list of apps is proprietary, Wine-based software. Apparently, using Wine-based proprietary apps is better than using Free apps, as long as the end goal of removing users' and developers' Freedom is achieved. No, really:
```
jms@osc-franzibald:~$ dpkg -L picasa | grep libwine.so
/opt/google/picasa/3.0/wine/lib/libwine.so.1.0
```

Is that REALLY a better option? Personally, as someone who believes in Freedom, I don't think so - whilst people should be free to use whichever apps they want, even proprietary ones, I'd find the act of *recommending* a non-Free course of action to be distasteful at best

It's also rather ironic since the arguments against Mono due to "omgz ze patents!" are generally referring to Mono's Windows.Forms implementation.

Microsoft's Windows.Forms implementation is just a .NET binding to their native Windows API, which is EXACTLY what Wine implements (the native Windows C/C++ API among other things).

This is why Windows.Forms itself is not a danger, as it is just a binding. Bindings are just API wrappers to some other library and APIs cannot be patented.

In other words, if the FUD about Mono's Windows.Forms being dangerous is true, then so is Wine - and in fact, it's an even /bigger/ danger since it's far more widely depended on than Mono's Windows.Forms.

However, IMHO, it's just FUD and I do not advocate badmouthing Wine either and I think that since Wine is so heavily depended on and has been around for so long, I seriously doubt Microsoft will ever sue over Wine patents (or Mono Windows.Forms) because they haven't so far and Wine has been around for over 10 years (and Mono has been around for ~8 or so).


As a further note, no Linux apps based on Mono use Windows.Forms.

---

### Post by alternatealias on 2009-06-03
> **satipera said:**
> I have been reading about mono and how it could be a patent trap should I be avoiding tomboy like redhat are?

There's no evidence at all that Red Hat are shipping GNote over Tomboy due to fear of Mono patents (Fedora still ships Mono & Tomboy, but fresh installs get GNote while upgrades get Tomboy if the user already has Tomboy installed). This "theory" is only being propagated by anti-Mono propagandists.

It is far more likely that they chose GNote because it allows them to use the same app on the LiveCD.

---

### Post by monsterstack on 2009-06-03
> **alternatealias said:**
> It's also rather ironic since the arguments against Mono due to "omgz ze patents!" are generally referring to Mono's Windows.Forms implementation.

Microsoft's Windows.Forms implementation is just a .NET binding to their native Windows API, which is EXACTLY what Wine implements (the native Windows C/C++ API among other things).

This is why Windows.Forms itself is not a danger, as it is just a binding. Bindings are just API wrappers to some other library and APIs cannot be patented.

In other words, if the FUD about Mono's Windows.Forms being dangerous is true, then so is Wine - and in fact, it's an even /bigger/ danger since it's far more widely depended on than Mono's Windows.Forms.

However, IMHO, it's just FUD and I do not advocate badmouthing Wine either and I think that since Wine is so heavily depended on and has been around for so long, I seriously doubt Microsoft will ever sue over Wine patents (or Mono Windows.Forms) because they haven't so far and Wine has been around for over 10 years (and Mono has been around for ~8 or so).

Ah, but don't forget, the Wine devs are extremely particular about who gets to edit the source code. If you've ever seen a single line of the win32 API, forget it, they won't let you touch it. They are extremely careful of avoiding patent issues. Still I think that Microsoft might have loved the idea of crushing Wine years ago, but now it's rather useful for Microsoft to have something like Wine around. After all, if people insist on using Linux, at least they can still use apps made for Windows, which means more sales of software licences in the long run. I think the same goes for Mono; Microsoft are probably unlikely to sue because Mono (in Microsoft's eyes, at least) represents a chance for them to edge into the Linux business by making Windows apps run there. It's more profitable to rely on the sales of software licences they might get from that than lose a butt-ton of money going up against IBM, Red Hat, Google, the Open Invention Network and chums. Microsoft would collapse like a house of cards if they even dared. Microsoft have always had shrewd lawyers and executives and it looks to me as if they're finally adopting the embrace approach rather than all out war. Still it remains to be seen if they advance to the extend and extinguish stages; but considering the software world is *ever so slowly* moving towards open standards, it gets ever more difficult for that to happen.

---

### Post by directhex on 2009-06-03
> **monsterstack said:**
> Ah, but don't forget, the Wine devs are extremely particular about who gets to edit the source code. If you've ever seen a single line of the win32 API, forget it, they won't let you touch it. They are extremely careful of avoiding patent issues.

You've confused patents and copyrights here. Mono has an identical policy regarding people who have seen the source either for Microsoft's Shared Source .NET framework ("Rotor") or have access somehow to the "full" thing. Copyright is unrelated to patent concerns, as a patent may be accidentally infringed by ANY app implementing ANYTHING, regardless of whose source code you've seen.

---

### Post by directhex on 2009-06-03
> **alternatealias said:**
> As a further note, no Linux apps based on Mono use Windows.Forms.

Strictly speaking, that's not true. There are a few examples - for example, ikvm pulls in Winforms (as IKVM's experimental Swing implementation is a wrapper around WinForms). And a couple of development tools such as nunit-gui and gendarme use it.

Nothing that couldn't be patched out with some developer effort, of course.

---

### Post by monsterstack on 2009-06-03
> **directhex said:**
> You've confused patents and copyrights here. Mono has an identical policy regarding people who have seen the source either for Microsoft's Shared Source .NET framework ("Rotor") or have access somehow to the "full" thing. Copyright is unrelated to patent concerns, as a patent may be accidentally infringed by ANY app implementing ANYTHING, regardless of whose source code you've seen.

Thanks for the clarification. There should have been an "as well" at the end of that sentence I suppose. Again with patents, though, the point is patents can be worked around. The Samba folks aren't that interested in patent licensing deals, for instance. Submarine patents are a legitimate threat as you say, but look how long it took somebody to patch VFAT after the TomTom events. Microsoft used to go around claiming the Linux kernel itself infringes on all sorts of patents. But if they *were* to launch a patent attack, their leverage would be very short-lived.

---

### Post by alternatealias on 2009-06-03
> **monsterstack said:**
> but look how long it took somebody to patch VFAT after the TomTom events.

According to what I can find on Google, TomTom settled with Microsoft and is now using a licensed VFAT implementation in their product. The Linux kernel has not, afaict, worked around the patent nor dropped vfat support.

If you have evidence to the contrary, I'd really like a link so that I may become better informed :-)

---

### Post by alternatealias on 2009-06-03
> **directhex said:**
> Strictly speaking, that's not true. There are a few examples - for example, ikvm pulls in Winforms (as IKVM's experimental Swing implementation is a wrapper around WinForms). And a couple of development tools such as nunit-gui and gendarme use it.

Nothing that couldn't be patched out with some developer effort, of course.

Ah, thanks for the info. Normally I would consider those to be "tools" more than "applications", but my definitions may differ from other peoples' ;-)

In either case, they are meant for developers and not end-users.

---

### Post by zekopeko on 2009-06-03
i'm amazed how entrenched people are about microsoft. yes they didn't play fairly a decade ago but know they are finally starting to see the light at the end of a tunnel.
please read before your start trolling (again):
[http://arstechnica.com/tech-policy/news/2009/05/making-microsoft-nicer-through-patents.ars](http://arstechnica.com/tech-policy/news/2009/05/making-microsoft-nicer-through-patents.ars)

---

### Post by zekopeko on 2009-06-03
> **satipera said:**
> I have been reading about mono and how it could be a patent trap should I be avoiding tomboy like redhat are?

no you shouldn't. if you like an app please use it on it's merit not because somebody shouted "that thing is evil". the programming language shouldn't be something you should think about as a user.

people who scream about mono being "patent encumbered" always forget to mention that any software application can infringe a patent since patent's aren't tied to a particular language.
that means that an app is just as likely to infringe a patent if it's written in C#/Mono or C++/Qt or any other language.
Mono as a framework is far more protected since it's an ECMA standard (just like javascript that is powering your broswer/gmail/facebook).

directhex explained it really nicely in his first post. and it's sad that he has to spend a part of his time here defending mono when he could be out there fixing/packaging free software (go go power banshee!).
i for one am grateful to directhex/every-other-mono-contributor for providing truly slick software.

---

### Post by monsterstack on 2009-06-03
> **alternatealias said:**
> According to what I can find on Google, TomTom settled with Microsoft and is now using a licensed VFAT implementation in their product. The Linux kernel has not, afaict, worked around the patent nor dropped vfat support.

If you have evidence to the contrary, I'd really like a link so that I may become better informed :-)

Licensed users there may well be, but that didn't stop a few people writing possible patches to avoid the patents anyway. Andrew Tridgell submitted [this one]("http://lkml.org/lkml/2009/5/1/280") [lkml.org], for instance. There may be others, but I don't know. Whether or not these patches eventually make it into mainline of course is ultimately up to Linus, but anyone is free to use the patch if they're scared of future issues. But the main point is that if there are patent issues people know about, then developers will try to deal with them accordingly. In this case, the patent was trivially easy to overcome. They might not always be, but hey.

---

### Post by alternatealias on 2009-06-03
> **monsterstack said:**
> Licensed users there may well be, but that didn't stop a few people writing possible patches to avoid the patents anyway. Andrew Tridgell submitted [this one]("http://lkml.org/lkml/2009/5/1/280") [lkml.org], for instance.

Thanks for the link.

> **monsterstack said:**
> There may be others, but I don't know. Whether or not these patches eventually make it into mainline of course is ultimately up to Linus, but anyone is free to use the patch if they're scared of future issues. But the main point is that if there are patent issues people know about, then developers will try to deal with them accordingly. In this case, the patent was trivially easy to overcome. They might not always be, but hey.

On that point I definitely agree ;-)

---

### Post by zekopeko on 2009-06-03
> **wh0rd said:**
> First of all stop your Mono rant. The OP asked a question about patent traps. So stop trying to derail the thread conversation with ad hominem attacks.

OP was talking about mono and directhex responed in a constructive structured manner 

Your repeated searches on UbuntuForums with the term “mono” so you can troll the threads is getting annoying. I'm going to address you once and for all:


directhex doesn't troll. he provides thought out replies, facts and contributes code to various FOSS project and is a valued member of this forums and ubuntu community at large. it is you who is using ad hominem attacks.

> 
There is nothing wrong with using Google Picasa, Google isn't preventing Linux from moving forward. Google embraced Linux unlike Microsoft who still is threatened by the progression of Linux. I bet you use non-free flash and proprietary graphics drivers.

Utter hypocrisy. At least if something is wrong with a FOSS app it can be fixed. not so with picasa or other closed source.
and if you read the arstechnica article that i provided a couple of post up you will see that microsoft is turning the boat around. they are starting to actively support FOSS apps. 

> 
Here's a known list of non-free things that you do use:
 
[LIST=1]
[*]The font, Verdana, you are using on your [blog]("http://www2.apebox.org/wordpress/"), along with 
[*]Lauchpad
[*]Ubuntu kernel has non free blobs
[*]This forum, vBulletin, you are posting on is also not free.
[/LIST] 


you also use the kernel and this forums. that's 2 less then directhex. gee that must make a better person. i guess you contribute to opensource projects all day long like directhex. heck you probably do twice as directhex ever did for FOSS.

> 
Its hilarious considering you actively sought out to prevent Gnote from being included in Debian by [trolling some bogus license issue]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=523093"). Then there is you bad mouthing Gnote on your Blog, [ApeBox]("http://www2.apebox.org/wordpress/rants/93/#comment-768"). Now you want to cry out “Freedom” and be a white knight on this thread, while still making comments like this about the Gnote port from Tomboy:
Now go ahead and change the comments in your blog when no is looking...

he was merely trying clear gnote's legal status so that there is no doubt about it. in essence he was helping gnote's dev by fixing potential problems in the start. and just because something is FOSS doesn't mean that you can use it anyway you like.

---

