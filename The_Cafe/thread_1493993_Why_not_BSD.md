---
title: "Why not BSD?"
date: 2010-05-26
forum: The Cafe
---

### Post by kaldor on 2010-05-26
*BSD is more secure and superior to Linux in many ways, and also has a more commercial-friendly license than Linux does. On top of that, KDE/GNOME are both usable on BSD. Same with things like Firefox.

What's keeping BSD away from the community? I installed FreeBSD 8 and it's not nearly as complicated as people make it out to be! 

Not only on desktops, but what about on servers and embedded devices?

It's not too different from Linux, but it has some things that are just better. Use google to get an idea of what I mean if you aren't sure. It just surprises me that BSD doesn't have a bigger market share than it does when it has so much potential.

---

### Post by RiceMonster on 2010-05-26
I like FreeBSD a lot, but I prefer Linux on the desktop. Linux has better hardware support and it gets features faster. I also prefer Linux package managers like yum/rpm and pacman over FreeBSD's pkg_add and ports.

That said, FreeBSD is likely my first choice for a server OS. I also have yet to try NetBSD and OpenBSD.

---

### Post by del_diablo on 2010-05-26
> and also has a more commercial-friendly license than Linux does.

The same license which is completely horrible to build a comunity around....

> What's keeping BSD away from the community?

License?

> It's not too different from Linux, but it has some things that are just better. Use google to get an idea of what I mean if you aren't sure. It just surprises me that BSD doesn't have a bigger market share than it does when it has so much potential.

Using a real world argument: Why the hell did Windows even aquire markedshare when it sucks compared to its competitors.
In a world where actual justice and marked existed it would have a decent markedshare I guess.

---

### Post by Sporkman on 2010-05-26
> **RiceMonster said:**
> That said, FreeBSD is likely my first choice for a server OS. I also have yet to try NetBSD and OpenBSD.

Linux also makes a fine server OS.

---

### Post by RiceMonster on 2010-05-26
> **Sporkman said:**
> Linux also makes a fine server OS.

Indeed it does. CentOS/RHEL is also a top choice for me. Debian would be good too, but I prefer Red Hat (just a personal preference).

---

### Post by Sporkman on 2010-05-26
> **RiceMonster said:**
> Indeed it does. CentOS/RHEL is also a top choice for me. Debian would be good too, but I prefer Red Hat (just a personal preference).

I also recommend Ubuntu Server - fast & rock solid.

---

### Post by RiceMonster on 2010-05-26
> **Sporkman said:**
> I also recommend Ubuntu Server - fast & rock solid.

I never would have guessed.

---

### Post by cascade9 on 2010-05-26
del_diablo got me in one. Its that BSD licence that keeps me away. I've use FreeBSD, PC-BSD and OpenBSD, they are good systems. But I dont want to add to BSDs userbase, because of the licence.

---

### Post by RiceMonster on 2010-05-26
> **cascade9 said:**
> del_diablo got me in one. Its that BSD licence that keeps me away. I've use FreeBSD, PC-BSD and OpenBSD, they are good systems. But I dont want to add to BSDs userbase, because of the licence.

Xorg uses a license very similar to the BSD license. Better stop using a GUI on Linux. Openssh, which is the ssh implementation on every Linux distro is BSD license as well. Hopefully you never use ssh either.

Sorry, but I think being that picky about a license, when it's viewed as free by even the FSF is silly.

---

### Post by Sporkman on 2010-05-26
The BSD license disincentivizes (?) contributing improvements to the code back to the community, whereas the GPL legally requires it.

Makes for more tightly controlled distribution (i.e. less forks, etc), however it puts all the work on the core developers.

---

### Post by hoagie on 2010-05-26
Well firstly even though freeBSD is not that more complicated than say ArchLinux, it is more complicated than Ubuntu, Fedora etc. Moreover, freeBSD does not aim at taking over Windows as Ubuntu does thus, the developers don't bother with making the operating system user friendly.
About the server market now. Yes freeBSD and any BSD is as good and maybe even better than linux. The reason that linux is more widely used is that back in the early 90's BSDi faced legal trouble against AT&T which at that date held the Unix trademark. This slowed the developement of BSD based operating systems for nearly two years. Linux based operating systems on the other which did not have such leagal issues received greater support and beacame more popular than any other Unix like OS. This popularity is what seperated linux from 386BSD back in the day and still does.
Linus Torvalds himself stated that that if 386BSD had been available at the time, he probably would not have created Linux.

History lesson is over.:KS

---

### Post by DeadSuperHero on 2010-05-26
I wonder about this myself from time to time. FreeBSD would be a fantastic system to base a desktop operating system on, provided you have the resources to properly put it together. In fact, an Ubuntu-styled FreeBSD distro would be really, really interesting. Especially if you could get the Ayatana notifications and indicator applets working.

However, like Ricemonster pointed out, FreeBSD has less hardware support than Linux does currently.

---

### Post by cascade9 on 2010-05-26
> **RiceMonster said:**
> Xorg uses a license very similar to the BSD license. Better stop using a GUI on Linux. Openssh, which is the ssh implementation on every Linux distro is BSD license as well. Hopefully you never use ssh either.

Sorry, but I think being that picky about a license, when it's viewed as free by even the FSF is silly.

LMAO. I'm free to use/not use whatever I want, for whatever reasons I want. ;) 
 
I'm one of the few people I know who actually reads the licences, and when I was using windows I used to (not in a nasty way) 'push' people to programs that had sane licences (like flac, not ape with its licence written by a monkey). 

I'd just rather be adding to GPL/copyleft. 

> **Sporkman said:**
> The BSD license disincentivizes (?) contributing improvements to the code back to the community, whereas the GPL legally requires it.


+1

---

### Post by RiceMonster on 2010-05-26
> **cascade9 said:**
> LMAO. I'm free to use/not use whatever I want, for whatever reasons I want. ;) 

LMAO. I'm free to agree/disagree with whatever I want, for whatever reasons I want. ;) 

> **cascade9 said:**
> I'm one of the few people I know who actually reads the licences, and when I was using windows I used to (not in a nasty way) 'push' people to programs that had sane licences (like flac, not ape with its licence written by a monkey). 

I'd just rather be adding to GPL/copyleft. 

But you will be getting all the same rights from the BSD license that you will be from the GPL, so what difference does it make if you're not forking the code or submitting patches to the project (in which case you may want to consider what people might do with your code)? Feel free to prefer the GPL, by all means. I'm just questioning your logic.

> **Sporkman said:**
> The BSD license disincentivizes (?) contributing improvements to the code back to the community, whereas the GPL legally requires it.

Makes for more tightly controlled distribution (i.e. less forks, etc), however it puts all the work on the core developers.

Irrelevant if you're not part of the development of the project.

---

### Post by Sporkman on 2010-05-26
> **RiceMonster said:**
> Irrelevant if you're not part of the development of the project.

How so? This gets GPL projects lots of "free labor" in implementing features & fixing bugs, which then benefits users.

---

### Post by RiceMonster on 2010-05-26
> **Sporkman said:**
> How so? This gets GPL projects lots of "free labor" in implementing features & fixing bugs, which then benefits users.

You're talking stickly in theory. Again, that's something to consider when you are developing something yourself. When we have highly reliable and secure projects like OpenSSH and FreeBSD under the BSD license, that DO get the benefits you speak of, why does it matter to the end user whether it's GPL or BSD? The end use will get all the rights from the BSD license that they could get from the GPL, so shouldn't they only be concerned with the quality of the software at this point?

---

### Post by cascade9 on 2010-05-26
> **RiceMonster said:**
> But you will be getting all the same rights from the BSD license that you will be from the GPL, so what difference does it make if you're not forking the code or submitting patches to the project (in which case you may want to consider what people might do with your code)? Feel free to prefer the GPL, by all means. I'm just questioning your logic.

I might get 'the same rights' as an end-user, but its not just about what I get. The more BSD licence projects, or BSD users, the bigger the project gest, the more users come, etc.. So I just try to avoid BSD-style licences as much as possible. 

> **RiceMonster said:**
> Irrelevant if you're not part of the development of the project.

Not IMO. Would you say that the windows style EULA (or any other the other proprietary licences) are irrelevant if the people involved arent devs?

---

### Post by quinnten83 on 2010-05-26
> **DeadSuperHero said:**
> I wonder about this myself from time to time. FreeBSD would be a fantastic system to base a desktop operating system on, provided you have the resources to properly put it together. In fact, an Ubuntu-styled FreeBSD distro would be really, really interesting. Especially if you could get the Ayatana notifications and indicator applets working.

However, like Ricemonster pointed out, FreeBSD has less hardware support than Linux does currently.

FreeBuntu anyone?

---

### Post by Sporkman on 2010-05-26
> **RiceMonster said:**
> You're talking stickly in theory. Again, that's something to consider when you are developing something yourself. When we have highly reliable and secure projects like OpenSSH and FreeBSD under the BSD license, that DO get the benefits you speak of, why does it matter to the end user whether it's GPL or BSD? The end use will get all the rights from the BSD license that they could get from the GPL, so shouldn't they only be concerned with the quality of the software at this point?

Two points: First, OpenSSH for example is what it is, and people want to use it, but it may have arrived slower than it would have had more parties been required to contribute to it. Second, it may have privately been redistributed with many good improvements, which the general public doesn't get access to.

---

### Post by kk0sse54 on 2010-05-26
> **Sporkman said:**
> The BSD license disincentivizes (?) contributing improvements to the code back to the community, whereas the GPL legally requires it.

I don't see how this is the case,anybody is free to submit a patch or code to any of the *BSD projects and there are numerous proprietary companies which release code back to the *BSD community unlike the GPL community despite their focus on supposed freedom.

> Makes for more tightly controlled distribution (i.e. less forks, etc), however it puts all the work on the core developers.

The reason there's less forks is 1) nobody hears about the smaller *BSD OSs and 2) the *BSDs are **not** distrobutions like linux distros are. They are completely separate operating systems as such how many forks could you possibly have of one OS?

---

### Post by Sporkman on 2010-05-26
> **C!oud said:**
> ...and there are numerous proprietary companies which release code back to the *BSD community

If they do, then they are doing their shareholders a disservice, as it gives their competitors an advantage. Why give code back (code that you've paid to develop) if you're not legally required to do so?

---

### Post by RiceMonster on 2010-05-26
> **cascade9 said:**
> Not IMO. Would you say that the windows style EULA (or any other the other proprietary licences) are irrelevant if the people involved arent devs?

I meant irrelevenat when comparing the BSD and GPL. The Windows EULA is in a completely different cattegory.

> **Sporkman said:**
> Two points: First, OpenSSH for example is what it is, and people want to use it, but it may have arrived slower than it would have had more parties been required to contribute to it. Second, it may have privately been redistributed with many good improvements, which the general public doesn't get access to.

But why does that matter when considering the end result? Should I not use it because there's a possibility that it could be even better than it is?

> **Sporkman said:**
> If they do, then they are doing their shareholders a disservice, as it gives their competitors an advantage. Why give code back (code that you've paid to develop) if you're not legally required to do so?

You would find that most companies developing the Linux kernel don't just do so because they are legally required. Now they do not have to maintain a fork, they can get improvements from other parties, and they get more improvements and testing on their own code. Go tell Red Hat is was a bad idea to contribute all that upstream code. I think they'll disagree with you on far more grounds than whether they're alowed to lock up the code or not. If what you say is true, I think a lot more companies would have just done a proprietary *BSD fork.

---

### Post by Sporkman on 2010-05-26
> **RiceMonster said:**
> 
But why does that matter when considering the end result? Should I not use it because there's a possibility that it could be even better than it is?

You should use it, that's not what I'm arguing. I'm simply saying that the GPL begets more community contributions via its legal requirements.

> **RiceMonster said:**
> 
You would find that most companies developing the Linux kernel don't just do so because they are legally required. Now they do not have to maintain a fork, they can get improvements from other parties, and they get more improvements and testing on their own code.

They won't get as many improvements by other parties, as other parties aren't legally required to give back the improvements they make & distribute.

---

### Post by kk0sse54 on 2010-05-26
> **Sporkman said:**
> If they do, then they are doing their shareholders a disservice, as it gives their competitors an advantage. Why give code back (code that you've paid to develop) if you're not legally required to do so?

Why don't you ask Apple, Yahoo, or Juniper just to name a few? Code that's released back to the *BSD projects helps improve the quality of *BSD for everyone and aids in the development of new features and services by *BSD developers themselves which further benefits companies that use *BSD code. Otherwise please state a BSD licensed project that is actively leeched off of by a proprietary company. The one place that BSD licensed code was stolen for quite some time was by GPL developers who through their supposed "freedom" of the GPL lock out *BSD projects such as OpenBSD or FreeBSD from any improvements or changes.

> You should use it, that's not what I'm arguing. I'm simply saying that the GPL begets more community contributions via its legal requirements.

There is no legal requirement under the GPL that the forces community contributions :roll:

---

### Post by RiceMonster on 2010-05-26
> **Sporkman said:**
> You should use it, that's not what I'm arguing. I'm simply saying that the GPL begets more community contributions via its legal requirements.

Which is completely different from what I have been talking about from the beginning, which makes me wonder why you're refuting my arguments.

---

### Post by Sporkman on 2010-05-26
> **C!oud said:**
> Otherwise please state a BSD licensed project that is actively leeched off of by a proprietary company.

How should I know? Companies are not required to disclose that info publicly, they only need to keep the headers on their source code files.

I'd be very surprised if there weren't "leechers", as why shouldn't a company use freely existing code rather than pay to develop it themselves, or be forced to disclose their mods in GPL'd code.

I wouldn't call them "leechers" though, as they are simply using the code as the original author intended.

---

### Post by Sporkman on 2010-05-26
> **RiceMonster said:**
> Which is completely different from what I have been talking about from the beginning, which makes me wonder why you're refuting my arguments.

I was refuting your implication that there is comparable community contributions to BSD projects as there are to GPL projects, which I'm pointing out that there is no requirement & little incentive to do so.

---

### Post by RiceMonster on 2010-05-26
> **Sporkman said:**
> I was refuting your implication that there is comparable community contributions to BSD projects as there are to GPL projects, which I'm pointing out that there is no requirement & little incentive to do so.

If there was little incentive to do so, we wouldn't have any companies making contributions to any open source project. Because by the same path of logic, companies would just be throwing out money by submitting code to the Linux kernel. "How can I make money if I people can freely use and sell my code?".

The companies that choose to take BSD licensed code and lock it up wouldn't contribute to a GPL project in the first place.

---

### Post by kk0sse54 on 2010-05-26
> **Sporkman said:**
> How should I know? Companies are not required to disclose that info publicly, they only need to keep the headers on their source code files.

I'd be very surprised if there weren't "leechers", as why shouldn't a company use freely existing code rather than pay to develop it themselves, or be forced to disclose their mods in GPL'd code.

I wouldn't call them "leechers" though, as they are simply using the code as the original author intended.

Yes you would know since a company is forced to disclose whether they are using BSD licensed code as such your argument is really just a hypothetical one based upon no evidence. Does this mean that there aren't companies who don't do that? Of course not but it is a myth that *BSD projects have no code contributed back to them by any outside party and in the viewpoint of GPL advocates are taken advantage of by proprietary companies.

> **Sporkman said:**
> I was refuting your implication that there is comparable community contributions to BSD projects as there are to GPL projects, which I'm pointing out that there is no requirement & little incentive to do so.

Based on what objective reasoning?

---

### Post by Sporkman on 2010-05-26
> **RiceMonster said:**
> If there was little incentive to do so, we wouldn't have any companies making contributions to any open source project. Because by the same path of logic, companies would just be throwing out money by submitting code to the Linux kernel. "How can I make money if I people can freely use and sell my code?".

No - those companies see a positive gain by using a kernel that took massive amounts of labor to develop (labor that they didn't have to pay for), for the low low cost of disclosing their own mods publicly. Net gain.

If the linux kernel were BSD'd, then they'd use the kernel, but not disclose their mods.


> **RiceMonster said:**
> The companies that choose to take BSD licensed code and lock it up wouldn't contribute to a GPL project in the first place.

Maybe so.

---

### Post by Sporkman on 2010-05-26
> **C!oud said:**
> [QUOTE=Me]I was refuting your implication that there is comparable community contributions to BSD projects as there are to GPL projects, which I'm pointing out that there is no requirement & little incentive to do so.

Based on what objective reasoning?[/QUOTE]

Ok, what is the requirement or major incentive to contribute?

---

### Post by RiceMonster on 2010-05-26
> **Sporkman said:**
> No - those companies see a positive gain by using a kernel that took massive amounts of labor to develop (labor that they didn't have to pay for), for the low low cost of disclosing their own mods publicly. Net gain.

If the linux kernel were BSD'd, then they'd use the kernel, but not disclose their mods.

So why haven't these companies just taken a BSD varient and just locked it up?

---

### Post by m4tic on 2010-05-26
> **Sporkman said:**
> If they do, then they are doing their shareholders a disservice, as it gives their competitors an advantage. Why give code back (code that you've paid to develop) if you're not legally required to do so?

For technology advances. There is Android, its been open source for years, it hasn't given its competitors an advantage.

---

### Post by Sporkman on 2010-05-26
> **RiceMonster said:**
> So why haven't these companies just taken a BSD varient and just locked it up?

Some probably have - I'll bet you there are plenty of routers, dvrs, etc, that run on a BSD variant, but I don't know for sure.

But a lot of companies use & ship linux, probably because it's benefited by a lot of development & community review & contributions. It's more widely reviewed & widely adopted, is my understanding. And the licensing issue is moot if you're not making modifications that the GPL requires to be disclosed.

---

### Post by RiceMonster on 2010-05-26
> **Sporkman said:**
> Some probably have - I'll bet you there are plenty of routers, dvrs, etc, that run on a BSD variant, but I don't know for sure.

But a lot of companies use & ship linux, probably because it's benefited by a lot of development & community review & contributions. It's more widely reviewed & widely adopted, is my understanding. And the licensing issue is moot if you're not making modifications that the GPL requires to be disclosed.

So you agree with me.

---

### Post by Sporkman on 2010-05-26
> **RiceMonster said:**
> So you agree with me.

I...guess? :)

**This just in:** RiceMonster believes there is no requirement and little incentive for users of BSD licensed code to contribute their mods back to the community. :D

---

### Post by kk0sse54 on 2010-05-26
> **Sporkman said:**
> Ok, what is the requirement or major incentive to contribute?

For *Community Contributions*? I fail to see how a license has anything to do with community contributions as long as it is open source. Seriously how does the GPL provide a major incentive? Legal requirements have nothing to do with community contributions.

---

### Post by juancarlospaco on 2010-05-26
[I]You make an enhacement.
Here comes the Apple, just rename it, close it, sell it...[/I]

---

### Post by Sporkman on 2010-05-26
> **C!oud said:**
> For *Community Contributions*? I fail to see how a license has anything to do with community contributions as long as it is open source. Seriously how does the GPL provide a major incentive? Legal requirements have nothing to do with community contributions.

You are making some sort of special distinction re "community". Let me replace "community" with "those who distribute".

If you distribute code derived from GPL'd code, you are legally required to disclose that code. Not so with BSD code.

---

### Post by Sporkman on 2010-05-26
BTW **RiceMonster** agrees with me completely re this. :D

---

### Post by RiceMonster on 2010-05-26
> **juancarlospaco said:**
> [I]You make an enhacement.
Here comes the Apple, just rename it, close it, sell it...[/I]

O RLY?
[http://opensource.apple.com/](http://opensource.apple.com/)

Feel free to download the code to all the BSD derived parts. Oh, and don't forget to thank Apple for WebKit and CUPS.

> **Sporkman said:**
> You are making some sort of special distinction re "community". Let me replace "community" with "those who distribute".

If you distribute code derived from GPL'd code, you are legally required to disclose that code. Not so with BSD code.

I don't understand your argument. What does it matter if I am simply just redistributing BSD licensed code? Even if I lock it up, people can go download it from whatever project anyway.

> **Sporkman said:**
> BTW **RiceMonster** agrees with me completely re this. :D

No, because you seemed to suggest that people don't just contribute because they have to :).

---

### Post by mickie.kext on 2010-05-26
> **RiceMonster said:**
> O RLY?
[http://opensource.apple.com/](http://opensource.apple.com/)

Feel free to download the code to all the BSD derived parts. Oh, and don't forget to thank Apple for WebKit and CUPS.

Those are not nearly all BSD derived parts of OS X. A lot is closed.

---

### Post by undecim on 2010-05-26
One Word: Support

---

### Post by Le-Froid on 2010-05-26
I'm gonna agree with C!oud here. It's going to help the company more if they give their fixes back to the project. If they send anything back to the project I'm sure the developers would work on it and add new features which will benefit everyone. Even Apple does this with their OS; they are constantly giving FreeBSD new code/fixes.

With the GPL you are forced into contributing your fixes back and that's a big turn-off for several projects. The last thing I worked on went with the BSD license because we didn't want any restrictions on the users.

---

### Post by swoll1980 on 2010-05-26
I don't understand this argument. People can say what ever they want either way, but many developers don't want to contribute code to a project, for it to be profited upon by a company that didn't contribute to it. All the arguments in the world can't change this.

---

### Post by RiceMonster on 2010-05-26
> **swoll1980 said:**
> I don't understand this argument. People can say what ever they want either way, but many developers don't want to contribute code to a project, for it to be profited upon by a company that didn't contribute to it. All the arguments in the world can't change this.

Yes, there are many developers who will not want to contribute to a BSD licensed project, however many developers and companies still do contribute. Nobody was arguing that absolutely everyone wants to contribute to a BSD project. However, many people and companies DO contribute back, despite that ability to make the code proprietary. All the arguments in the world can't change this, either.

There are also developers who do not want to contribute to GPL projects (go talk to the OpenBSD developers) because they find it too restrictive. There's multiple sides to each story.

---

### Post by mickie.kext on 2010-05-26
All the arguments in the world can't change the fact that Linux gets more patches while Linus Torvalds is in the toilet, than all BSDs get for whole week of development.

The fact is that BSD lags a lot behind Linux, and that is only increasing.

---

### Post by Tipo on 2010-05-26
I've always felt that the BSD's have much more polish than... most linux distributions out there. It may take a bit more time for packages to make it into the latest release, but it's rare that I encounter anything that's broken (mostly using OpenBSD).

On top of that, I know OpenBSD has better documentation than almost everything else I've seen. I almost never have to look past the man pages to learn to use or configure something. On top of most of that stuff, everything that gets put into the distribution is audited, and bugs are fixed.

If I want something polished, I go for OpenBSD. I mean, look at Fedora 13 -- so unpolished it's scary!

---

### Post by m4tic on 2010-05-26
C o p y r i g h t < y e a r >
< c o p y r i g h t h o l d e r > . A l l
r i g h t s r e s e r v e d .
R e d i s t r i b u t i o n a n d
u s e i n s o u r c e a n d b i n a r y
f o r ms , w i t h o r w i t h o u t
mo d i f i c a t i o n , a r e
p e r m i t t e d p r o v i d e d
t h a t t h e f o l l o w i n g
c o n d i t i o n s a r e me t :
1 . R e d i s t r i b u t i o n s
o f s o u r c e c o d e mu s t r e t a i n
t h e a b o v e c o p y r i g h t n o t i c e ,
t h i s l i s t o f
c o n d i t i o n s a n d
t h e f o l l o w i n g d i s c l a i me r .
2 . R e d i s t r i b u t i o n s
i n b i n a r y f o r m mu s t
r e p r o d u c e t h e a b o v e
c o p y r i g h t n o t i c e , t h i s l i s t
o f c o n d i t i o n s
a n d t h e f o l l o w i n g
d i s c l a i me r i n t h e
d o c ume n t a t i o n a n d / o r o t h e r
ma t e r i a l s
p r o v i d e d   w i t h
t h e d i s t r i b u t i o n .

How free can you get

---

### Post by swoll1980 on 2010-05-26
> **RiceMonster said:**
> Yes, there are many developers who will not want to contribute to a BSD licensed project, however many developers and companies still do contribute. Nobody was arguing that absolutely everyone wants to contribute to a BSD project. However, many people and companies DO contribute back, despite that ability to make the code proprietary. All the arguments in the world can't change this, either.

The original question was "BSD: why not?". Someone answered "The license" I think that was pretty much /thread. A bunch of people jump in defending the license. While the points may be valid, it doesn't detract from the fact that this is why BSD is so far behind Linux.

---

### Post by mickie.kext on 2010-05-26
> **m4tic said:**
> C o p y r i g h t < y e a r >
< c o p y r i g h t h o l d e r > . A l l
r i g h t s r e s e r v e d .
R e d i s t r i b u t i o n a n d
u s e i n s o u r c e a n d b i n a r y
f o r ms , w i t h o r w i t h o u t
mo d i f i c a t i o n , a r e
p e r m i t t e d p r o v i d e d
t h a t t h e f o l l o w i n g
c o n d i t i o n s a r e me t :
1 . R e d i s t r i b u t i o n s
o f s o u r c e c o d e mu s t r e t a i n
t h e a b o v e c o p y r i g h t n o t i c e ,
t h i s l i s t o f
c o n d i t i o n s a n d
t h e f o l l o w i n g d i s c l a i me r .
2 . R e d i s t r i b u t i o n s
i n b i n a r y f o r m mu s t
r e p r o d u c e t h e a b o v e
c o p y r i g h t n o t i c e , t h i s l i s t
o f c o n d i t i o n s
a n d t h e f o l l o w i n g
d i s c l a i me r i n t h e
d o c ume n t a t i o n a n d / o r o t h e r
ma t e r i a l s
p r o v i d e d   w i t h
t h e d i s t r i b u t i o n .

How free can you get

There is Freedom, and there is anarchy...

---

### Post by jrothwell97 on 2010-05-26
My two cents:

I'm opposed to share-alike licenses. As far as I'm concerned, if you modify something that I did, that's *your* work, and you're under no obligation to share it under the same license. I'd like you to credit me, and I'd *love* it if you wanted to share it back with me - but that's *your* choice. Your work, your choice.

Outright opposition to permissive licenses, in my opinion, will only serve to further the myth held by Windows fanboys/Macintards/Steve Ballmer that all Linux users are loony freetards with a cancerous license. You're welcome to release your own software under the GPL, but don't criticise other people for releasing things under more permissive licenses.

---

### Post by Ibidem on 2010-05-26
> **RiceMonster said:**
> O RLY?
[http://opensource.apple.com/](http://opensource.apple.com/)

Feel free to download the code to all the BSD derived parts. Oh, and don't forget to thank Apple for WebKit and CUPS.



I don't understand your argument. What does it matter if I am simply just redistributing BSD licensed code? Even if I lock it up, people can go download it from whatever project anyway.

Note that webkit is a fork of khtml--Apple was legally obligated to provide source.
CUPS was free, and included in Linux distros, before Apple started using it-- if they closed it, the right to fork would result in a massive loss of development/support to the inevitable fork.
If you expect to use fixes from the community, it's simplest to use the same codebase.

Take a look at Cedega for an idea of whether BSD licensed code ever gets "closed".
It's a fork of the last BSD Wine release.


As far as why not BSD, note that every argument used for Windows over Linux applies to Linux over BSD, plus a few:
Proprietary software--Softmaker Office 2004/2006 was the only proprietary office suite for BSD; MatLab, SPSS, etc. are available for Windows/Mac/Linux 
Flash--no native version
Audio--OSS only, no ALSA; losing many open-source apps over this
Drivers--really missing out (Intel is poorly supported, KMS is missing, every BSD driver has a Linux version, but not the other way around)
Focus on security apparently means that everything else gets neglected.
NDIS support means recompiling the kernel with a Windows driver linked in (versus ndiswrapper)

Yes, it is a little more secure than standard Linux; but add Pax+grsecurity and harden Linux up (hardened Gentoo, for instance), and you're pretty close.  Besides that, you don't have as current a system with BSD.

If you don't mind driver issues and prefer a non-Linux OS, I'd say to use OpenSolaris (or perhaps a Debian/opensolaris system) or otherwise Debian GNU/BSD.

---

### Post by chessnerd on 2010-05-26
It is BSD's low usage that keeps it usage low. The same reason that Linux's usage is low. It is a vicious cycle. Not many people use it, so it doesn't get hardware support, so not many people use it, so it doesn't get as much development, so not many people use it...

> **del_diablo said:**
> Using a real world argument: Why the hell did Windows even aquire markedshare when it sucks compared to its competitors.
In a world where actual justice and marked existed it would have a decent markedshare I guess.

You can argue this, but Microsoft got its place by being better than its competitors. 

Apple had the opportunity to be "the" desktop computing solution, but they blew it with their hardware exclusivity and pricing scheme. IBM had similar issues with OS/2. If these companies had kept prices low, or had opened up their software for use on all PC architectures during the critical mid to late 80s, they could have stomped out Windows before it even became anything. 

Also, if the GNU project had successful produced a working kernel in the late 80s, it might have also taken off by beating Microsoft in price while small "mom and pop" OSs still reigned. (Evidently that wasn't a priority, seeing how Hurd is still not stable.)

It was the open nature of Windows and DOS, which could be run on any PC-based computer regardless of manufacturer, combined with low prices and decent (not great) features, that allowed Microsoft to triumph. The other OSs just didn't offer what Windows did - economical computing solutions. Now, everyone is trying catch up to them.

---

### Post by WinterRain on 2010-05-26
I'm a multimedia junkie, and BSD just does not cut it for me. There's no way I could get my TV tuner card working in BSD.

---

### Post by kk0sse54 on 2010-05-27
> **mickie.kext said:**
> All the arguments in the world can't change the fact that Linux gets more patches while Linus Torvalds is in the toilet, than all BSDs get for whole week of development.
And the result of the extremely fast pace decentralized frantic nature of the linux kernel is Torvalds calling the kernel fat and bloated [http://www.computerworlduk.com/toolbox/open-source/kernel-systems/news/index.cfm?newsId=16686](http://www.computerworlduk.com/toolbox/open-source/kernel-systems/news/index.cfm?newsId=16686) in addition to an amazing sense of stability.

> The fact is that BSD lags a lot behind Linux, and that is only increasing.
If you're referring to the development pace of *BSD I really don't see how that is the case especially in regards to the development of FreeBSD with the porting of such things as ZFS, DTRACE, and GCD and other projects like replacing GCC with llvm/clang by the FreeBSD devs or pcc by the OpenBSD devs among a host of other things. To say that *BSD development is dated and falling by the wayside is simply not true. 

> Note that webkit is a fork of khtml--Apple was legally obligated to provide source.
Apple is legally obligated to release the source to WebKit's HTML and JavaScript code but not WebCore and JavaScriptCore which are BSD licensed.


> As far as why not BSD, note that every argument used for Windows over Linux applies to Linux over BSD, plus a few:
Proprietary software--Softmaker Office 2004/2006 was the only proprietary office suite for BSD; MatLab, SPSS, etc. are available for Windows/Mac/Linux
Flash--no native version
Audio--OSS only, no ALSA; losing many open-source apps over this
Drivers--really missing out (Intel is poorly supported, KMS is missing, every BSD driver has a Linux version, but not the other way around)
Focus on security apparently means that everything else gets neglected.
NDIS support means recompiling the kernel with a Windows driver linked in (versus ndiswrapper)
Porting KMS I believe is under way and as far as I know NDIS doesn't require a full kernel compile. Otherwise thanks for giving an actual comparison that doesn't try to make the argument that one shouldn't use *BSD just because of its license.

> Besides that, you don't have as current a system with BSD.
I don't see how you can say that since FBSD ports has more software and is more up to date than most linux distros. Feel free to look around freshports.org

---

### Post by smellyman on 2010-05-27
This made me laugh a bit
 
[BSD is Dying]("http://www.youtube.com/watch?v=g7tvI6JCXD0")

---

