---
title: "&quot;Intel Will Not Support Ubuntu's XMir&quot; What will be the consequences?"
date: 2013-09-08
forum: Ubuntu, Linux and OS Chat
---

### Post by carterclan2 on 2013-09-08
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ1NjY](http://www.phoronix.com/scan.php?page=news_item&px=MTQ1NjY)

What will this mean for the Mir project?

---

### Post by grahammechanical on 2013-09-08
This is what it will mean

> Canonical will now need to carry the XMir support out-of-tree from the  xf86-video-intel driver. Canonical is also carrying patched versions of  Mesa, xf86-video-ati, and xf86-video-nouveau for being able to support  Mir/XMir in Ubuntu 13.10. The binary AMD and NVIDIA graphics drivers  also remain incompatible with Mir.

Well, we already knew that the proprietary video drivers were incompatible. Personally speaking, I stopped using proprietary video drivers more than a year ago. Too buggy for my liking. Nouveau does fine on my machine with Xserver or Xmir. But then again I am not about to buy the latest hardware, am I. So, it does not matter with me.

Regards.

---

### Post by prodigy_ on 2013-09-08
The best possible consequence for the Linux community would be Canonical finally admitting Mir and Unity fiasco and discontinuing both. Sadly it's not going to happen.

---

### Post by codingman on 2013-09-08
Sorry for being a fool, but what %exactly% is Mir?

---

### Post by santosh83 on 2013-09-08
Sad decision by Intel to first [release]("http://www.phoronix.com/scan.php?page=news_item&px=MTQ1MzU") their driver with inbuilt support for XMir and then to [revoke]("http://www.phoronix.com/scan.php?page=news_item&px=MTQ1NjY") it, apparently a management decision. I hope the issues behind this get ironed out and we get the support of the major graphics manufacturers.

---

### Post by codingman on 2013-09-08
Psst... An Mir thread about this has already been made...

---

### Post by coffeecat on 2013-09-08
Threads merged.

---

### Post by codingman on 2013-09-08
Thanks, please delete my post above you. :D

---

### Post by Gyokuro on 2013-09-08
> **santosh83 said:**
> Sad decision by Intel to first [release]("http://www.phoronix.com/scan.php?page=news_item&px=MTQ1MzU") their driver with inbuilt support for XMir and then to [revoke]("http://www.phoronix.com/scan.php?page=news_item&px=MTQ1NjY") it, apparently a management decision. I hope the issues behind this get ironed out and we get the support of the major graphics manufacturers.

That is Canonicals part to support said hardware with a working driver as it is not a general linux graphic driver problem only a single distribution problem.

---

### Post by santosh83 on 2013-09-08
> **Gyokuro said:**
> That is Canonicals part to support said hardware with a working driver as it is not a general linux graphic driver problem only a single distribution problem.

Strictly speaking yes, but Intel is a giant compared to Canonical, and if they cared about the overall Linux ecosystem, surely maintaining a small patch would be a good altruistic intention right? After all, they know their driver the best. It's not that Intel isn't capable, but that ideologically they want community efforts to consolidate behind Wayland I suppose, since they've already invested time and effort in it, and this is one way to get the message across to the other hardware makers and distributions to get behind them in line, and begin to shun Mir. Who knows what the future will bring... I still hope we can have both Mir and Wayland both doing well, with the least possible fragmentation of both the underlying drivers as well as the overlying toolkits, GUIs etc, as cooperative diversity is the best thing for Linux. Neither having all the eggs in one basket, nor bitter and divisive fragmentation would help in the long run.

---

### Post by Gyokuro on 2013-09-08
Yes - Intel could but why should they take care about something which get only used in a single distribution - for the said ecosystem where Canonical played a game and lost it?? Canonical have done already great work of fragmentation of said ecosystem and it seems they do not care as they live in their Ubuntu universe but the rest have not forgotten how this Mir debacle started - X11 have layed the foundation for Wayland years before - in their hard work in X11/Mesa and carefully engineering and the road was and is: X11=>wayland. Intel made a statement and I think the decission of NVidia/AMD will not be different as Intels one.

---

### Post by etna2 on 2013-09-08
I can't believe I registered just to post this, but what the hey.

> **santosh83 said:**
> Strictly speaking yes, but Intel is a giant compared to Canonical, **and if they cared about the overall Linux ecosystem**, surely maintaining a small patch would be a good altruistic intention right?

It's because they care about Linux that they are doing this. No  operating system can, and neither should it have to support more than 1 fundamental stack such as the graphics stack. Remember the madness that resulted when Microsoft updated the display stack from what it was in Windows XP and earlier to the new one that is being used in Vista and later? Most of the manufacturers were slow in delivering updated drivers that conform to the new model even though Microsoft already notified the hardware manufacturers well in advance about the need for updated drivers to properly support new graphics stack. The transition to Wayland is definitely not going to be all smooth and plain sailing, and now you want to suddenly introduce another source of uncertainty to the migration with Mir?   


 > After all, they know their driver the best. It's not that Intel isn't capable, but that ideologically they want community efforts to consolidate behind Wayland I suppose, since they've already invested time and effort in it, and this is one way to get the message across to the other hardware makers and distributions to get behind them in line, and begin to shun Mir. 

Which is the way things should be done. As i said earlier, an operating system should not have to support more than 1 of any of the fundamental components that drives it. How many graphics stacks do most of the operating systems have today? Windows has only 1, OS X has only 1, the BSDs have only 1, Android has only 1, etc etc. You get the point. It's just silly to have more than 1 display server for Linux **especially when they are binary incompatible with each other where drivers are concerned**. It's already so difficult to get manufacturers to support Linux with drivers, either closed or open, and leave it to Canonical to complicate things up a notch with their announcement of Mir. Especially when **they** were the original proponents of Wayland that started this massive development effort on it, only for them to never contribute anything to Wayland and now turn their back and mooch off all the existing hard work that was put into it. 

If Ubuntu still wants to be called a Linux distribution that it has to expect to play by the established rules and practices in use. Ubuntu can have its own init daemon (Upstart), its own DE (Unity) and anything else that they fancy but when it comes to aspects that concern drivers, it's 'upstream or die', because no major hardware vendor is going to support single distro-only solutions and write special drivers to support that 'special' distribution. 

And Intel has just demonstrated that to Canonical in the bluntest of ways.

And for the record, if the planned X11 migration path was to move to Mir i'd be saying the same thing about Wayland in this post. But it's not; the official migration path as agreed upon by almost all non-Ubuntu distributions is X11 ---> Wayland, as was decided at least 2 - 3 ago.

---

### Post by leo-ms on 2013-09-08
Why did Intel so suddenly decide to stop support? Was there some little squabble or spit that happened?

---

### Post by etna2 on 2013-09-08
> **Gyokuro said:**
> Yes - Intel could but why should they take care about something which get only used in a single distribution - for the said ecosystem where Canonical played a game and lost it?? Canonical have done already great work of fragmentation of said ecosystem and it seems they do not care as they live in their Ubuntu universe but the rest have not forgotten how this Mir debacle started - X11 have layed the foundation for Wayland years before - in their hard work in X11/Mesa and carefully engineering and the road was and is: X11=>wayland. Intel made a statement and I think the decission of NVidia/AMD will not be different as Intels one.

Unfortunately most Ubuntu users do not know about this bit of history...and about the sorry state of Linux graphics driver support as it already is today even with only 1 display server.

Otherwise they would not be supporting Mir or Xmir in any way.

---

### Post by Gyokuro on 2013-09-08
Yes you are correct as long it works for them it is ok but outside of this tiny universe it is different and a lot of people(developers) take care of this ecosystem and they have not forgotten. As long there are enough Linux users in the enterprise market which are demanding closed source X11 drivers for their CAD/CUDA work binary drivers get released which should make Linux home users happy -  that's the only reason why binary graphics drivers for Linux are available. They earn money with enterprise clients not home users and said enterprise are interested in a sane migration from X11 to a sucessor and Intel have to take care of this clients which are developing for Xeon Phi another area is Tizen.

---

### Post by kaldor on 2013-09-08
I think this is a justifiable move by Intel. Wayland has been in the works for years and is well-established, so why should everyone cater to Ubuntu's separate and unique product? If Canonical wishes to create their own ecosystem (I am by no means against that), then they should expect to do the work on their own. It isn't Intel's responsibility to provide support for a project that is not only against the rest of the community, but also not certain to succeed.

---

### Post by buzzingrobot on 2013-09-08
These ideological and grudge-driven decisions among the developer community damage Linux.  It's disheartening to see a corporation like Intel announce a decision like this via a nastygram post on GitHub.  (So much so I wonder if it is valid.)  Is that how Intel deals with other businesses?

Canonical has done nothing wrong by deciding to develop software that is best for them and their purposes. That's what the "free" in FOSS is all about. You are free to do what you wish, and you get to deal with all the implications of your choices.  I'm pretty sure Canonical knows the implications of their Mir decisions.

Many in the developer community are arguing, essentially, that Mir is unhealthy for the developer community.  Perhaps it is.  But, the interests of the broader Linux community -- the users -- and the interests of the narrow community -- the developers -- aren't necessarily identical.

When the dust settles, I'll use Mir or Wayland or X, which ever I think is best for my purposes.  I'm a user, and I don't have a reason to commit to one side or the other.

---

### Post by BigSilly on 2013-09-08
> **buzzingrobot said:**
> These ideological and grudge-driven decisions among the developer community damage Linux.  It's disheartening to see a corporation like Intel announce a decision like this via a nastygram post on GitHub.  (So much so I wonder if it is valid.)  Is that how Intel deals with other businesses?

Canonical has done nothing wrong by deciding to develop software that is best for them and their purposes. That's what the "free" in FOSS is all about. You are free to do what you wish, and you get to deal with all the implications of your choices.  I'm pretty sure Canonical knows the implications of their Mir decisions.

Many in the developer community are arguing, essentially, that Mir is unhealthy for the developer community.  Perhaps it is.  But, the interests of the broader Linux community -- the users -- and the interests of the narrow community -- the developers -- aren't necessarily identical.

When the dust settles, I'll use Mir or Wayland or X, which ever I think is best for my purposes.  I'm a user, and I don't have a reason to commit to one side or the other.

Got to say, I'm no expert on everything that's happening with Mir, Wayland, X etc, but I do agree with your post. I think it comes across as very unprofessional how this has been done, and I imagine there's nothing altruistic in their decision. I don't think Intel was rushing in to save the world at all. Rather, it seems to me that they simply aren't going to do the Mir work for Canonical, and this makes sense and you don't have to be a developer to understand that. Like you say, I am pretty confident that when Canonical made these decisions to go their own route, they knew things like this would happen. They knew they'd have to do their own work to make Mir viable.

But the whole poisoning of Ubuntu thing going on is very sad indeed, and sad to see it going on outside of forums, spilling into professional companies doing and saying silly things.

---

### Post by JDShu on 2013-09-08
> **buzzingrobot said:**
> These ideological and grudge-driven decisions among the developer community damage Linux.  It's disheartening to see a corporation like Intel announce a decision like this via a nastygram post on GitHub.  (So much so I wonder if it is valid.)  Is that how Intel deals with other businesses?   Intel does many things that are not nice - if you follow GKH on G+ there are plenty of complaints about the way they do business. They are a huge corporation, what do you expect? It is expressly against their interests to support a competing solution. At the same time they are well within their rights to accept whichever patches they want in their own upstream. The same way that Canonical is well within their right to roll their own solution over the current standard.  >  Canonical has done nothing wrong by deciding to develop software that is best for them and their purposes. That's what the "free" in FOSS is all about. You are free to do what you wish, and you get to deal with all the implications of your choices.  I'm pretty sure Canonical knows the implications of their Mir decisions.   "Wrong" is really in the eye of the beholder. The history behind the introduction of Mir certainly makes Canonical look bad to some people - FUD/Incompetence regarding Wayland, secret development of an "Open" project etc. If you can't understand the criticism, then you are refusing to look. Again, at the same time, Canonical has the right to do whatever they want. They are a private company. But they have to realize that certain things they do can and will have an effect on how other companies respond to them. Making enemies of other corporations in the eco system is not an intelligent course of action.  >  Many in the developer community are arguing, essentially, that Mir is unhealthy for the developer community.  Perhaps it is.  But, the interests of the broader Linux community -- the users -- and the interests of the narrow community -- the developers -- aren't necessarily identical.   Mir may benefit the Ubuntu community (not the rest of the Linux community) if it is done well. We don't know if that will be the case at all. There are many ways in which it could end badly for users - we just don't know at this point. On the other hand the harm to the developer community is very predictable and real.  >  When the dust settles, I'll use Mir or Wayland or X, which ever I think is best for my purposes.  I'm a user, and I don't have a reason to commit to one side or the other.  You do that. For me on the other hand, I call what I see, and from what I can see, Canonical is making more enemies for a solution of dubious value.   EDIT: I forgot to mention the main point which is that this particular commit sounds more like an Intel developer passing the blame to his boss.

---

### Post by monkeybrain20122 on 2013-09-08
> **Gyokuro said:**
> Yes - Intel could but why should they take care about something which get only used in a single distribution - for the said ecosystem where Canonical played a game and lost it??.

It will be used by a single distribution if Intel etc make sure that other distribution cannot use it by not supporting Mir upstream (the patch is written by Canonical employee so it is not even that Intel has to do the supporting). So this is a bit of circular reasoning. Note that the developer who reversed the decision to support Mir is the same one who accepted the patch in the first place, citing "management" to remove the patch. So the developer doesn't have an issue, it is a political decision by the company.

BTW I am no Mir fan, I would much rather they stick with the broader ecosystem, but just saying. I don't think Canonical would go back on Mir at this point, with so much work and money invested in  mobile and touch already. On the other hand, so far no one other than Intel says it will support Wayland either.

---

### Post by buzzingrobot on 2013-09-08
@JDShu:  I understand your counter-arguments, but I just don't see that I have any skin in that game.  I am not a developer, so I have no need to commit to X or Mir or Wayland.  Kibbitzing in corporate politics goes on all the time but I'm out here in the peanut gallery, so it's a bit pointless.  (Like football fans pretending to coach.) When a product is offered, I'll see if I like it.  That's no different than the normal state of affairs. If I don't like Mir, I won't use Ubuntu.  Nothing difficult there.

I do, though, agree that there's reason not to take this github post at face value.  I've always assumed Canonical would get proprietary support for Mir only by paying for it.  Maybe that's in the mix here.

---

### Post by etna2 on 2013-09-08
> **BigSilly said:**
> Got to say, I'm no expert on everything that's happening with Mir, Wayland, X etc

Then here's a quick history lesson.

_2010 - 2011_ 
- **Ubuntu and Canonical announce a shift to Wayland as a replacement for X**. 
- Every major distribution agree to back Wayland as the successor to X as a display server
- **Wayland is established as the de facto migration path from X for Linux**
- Work commences on Wayland and XWayland development
- **Not a peep or single commit was made to Wayland by Canonical employees / Ubuntu developers**

_2012_
- GTK3 achieves partial Wayland support, Wayland support targeted for Qt in future releases
- First ever Wayland-only distro (Rebecca Black) released as a testbed for Wayland / Weston + XWayland
- **Not a peep or single commit was made to Wayland by Canonical employees / Ubuntu developers** 

_2013_
- GTK3 and QT slowly gains additional Wayland support
- **Canonical does an about turn, claims that Wayland is unsuitable for their use, announces 'open' project Mir that was conceived in secret over the years.**
- Wayland and Weston hit v1 release
- GTK3 and Qt gain support for Wayland at much quicker paces than previously observed
- Updated version of Rebecca Black released

[quote=monkeybrain20122]It will be used by a single distribution if Intel etc make sure  that other distribution cannot use it by not supporting Mir upstream. So  this is a bit of circular reasoning. Note that the developer who  reversed the decision to support Mir is the same one who accepted the  patch in the first place, citing "management" to remove the patch. So  the developer doesn't have an issue, it is a political decision by the  company.[/quote]

No other distro intends to use Mir, period. Arch and Gentoo are preparing for Wayland, and so are most of the major RPM-based distributions like OpenSUSE and Fedora. Conservative distributions like Debian will stay on X for the forseeable future until the migration is well and fully tested, and even then, the fact that Debian does not have any Mir packages in unstable, testing or experimental says a lot when there are Wayland packages in those repositories. 

Even official Ubuntu derivatives such as Xubuntu, Lubuntu and Kubuntu refuse to use Mir, preferring instead to stick with X for the forseeable future and eventually migrate over to Wayland once the dust settles. So Mir is every bit a single-distro-only solution. And single-distro-only software = do your own patches yourself.

---

### Post by santosh83 on 2013-09-08
> **Gyokuro said:**
> Yes - Intel could but why should they take care about something which get only used in a single distribution - for the said ecosystem where Canonical played a game and lost it?? Canonical have done already great work of fragmentation of said ecosystem and it seems they do not care as they live in their Ubuntu universe but the rest have not forgotten how this Mir debacle started - X11 have layed the foundation for Wayland years before - in their hard work in X11/Mesa and carefully engineering and the road was and is: X11=>wayland. Intel made a statement and I think the decission of NVidia/AMD will not be different as Intels one.

Okay, as an ordinary user I didn't know the history behind this, nor can I understand well the technical merits and demerits of Wayland vs. Mir.

From what I've read in various places it seems the Wayland effort has been going on for a few years now, and was generally supported by the major distribution vendors and now I read that even Intel supports it and has a paid developer working on it. Also read though that until recently development on Wayland had been frustratingly slow and that was a part of the reason why Canonical dropped Wayland to start developing their own Mir. People have said that instead Canonical could've contributed to Wayland development and speeded it up, to both their's and the community benefit. Some have responded saying Canonical and Wayland developers couldn't agree on crucial technical features, and it seems they could not get to cooperate, hence Canonical splitting off on their own, especially since they have a tight self-imposed deadline for rolling out mobile/tablet versions, and Wayland dev had either been too slow or not to their wishes, they could've been forced to abandon their mobile/tablet plans. Whew... lots of opinions flung back and forth!

In the end, although the beauty of open source is that anyone is free to fork/modify, Canonical being a (the?) leading player in the Linux world could perhaps have made more efforts to get behind Wayland and adapt it for their purposes too, rather than splitting off a major portion of the OS. On the other hand though, we now have two competing solutions to the same problem, and ignoring political decisions, each could be an incentive for faster development of the other, and finally one could emerge a clearly better solution. But it seems that the politics is in fact ruining relationships and cooperation, and that's detrimental.

> **etna2 said:**
> 
If Ubuntu still wants to be called a Linux distribution that it has to expect to play by the established rules and practices in use. Ubuntu can have its own init daemon (Upstart), its own DE (Unity) and anything else that they fancy but when it comes to aspects that concern drivers, it's 'upstream or die', because no major hardware vendor is going to support single distro-only solutions and write special drivers to support that 'special' distribution. 

And Intel has just demonstrated that to Canonical in the bluntest of ways.

And for the record, if the planned X11 migration path was to move to Mir i'd be saying the same thing about Wayland in this post. But it's not; the official migration path as agreed upon by almost all non-Ubuntu distributions is X11 ---> Wayland, as was decided at least 2 - 3 ago.

On principle I'd say that any subsystem, no matter how major, could feasibly have alternatives and competition, and this wouldn't necessarily be bad in an ideal situation. But as you say above, we aren't in an ideal situation and are dealing with already cranky upstream manufacturers in no mood to pamper the Linux community. So in this case everyone could've got behind one effort (either Wayland or Mir) just to present a unified face to the driver writers.

Now we'll probably have most vendors getting behind Wayland, which means Canonical will have to spend extra manpower to keep their version of the drivers competitive and current with upstream. Let's see how it goes.

Also read elsewhere that this not only affects the bottom rung of the hierarchy (i.e., the drivers) but also the top level, i.e., desktop environments and applications. Many desktop maintainers seem to have the same sentiments as Intel, that they cannot be expected to make their systems work on Mir unless significant help and cooperation is forthcoming from Canonical. Again only time will tell how this is going to play out. In any case, trying times ahead for Canonical.

---

### Post by prodigy_ on 2013-09-08
> **santosh83 said:**
> Canonical being a (the?) leading player in the Linux world
What? Canonical isn't even on the list of kernel contributors: [http://go.linuxfoundation.org/who-writes-linux-2012](http://go.linuxfoundation.org/who-writes-linux-2012). (Unlike Intel which is indeed one of the top contributors.)

Canonical amounts pretty much to zero in the Linux world. They do not contribute anything upstream, they develop their own solutions that are unnecessary and incompatible with everything else (NIH syndrome) and they completely ignore the community.

---

### Post by codingman on 2013-09-08
What the hell was wrong with X anyways? 
What the hell was (is) wrong with *Wayland* anyways?
Why don't the devs spend their sweet time fixing suspend from command-line instead?

---

### Post by Gyokuro on 2013-09-08
> **monkeybrain20122 said:**
> It will be used by a single distribution if Intel etc make sure that other distribution cannot use it by not supporting Mir upstream (the patch is written by Canonical employee so it is not even that Intel has to do the supporting). So this is a bit of circular reasoning. Note that the developer who reversed the decision to support Mir is the same one who accepted the patch in the first place, citing "management" to remove the patch. So the developer doesn't have an issue, it is a political decision by the company.

Intel is responsible for their Intel graphic drivers and not for all other parts where MIR support patches have to go in - that's part of various upstream maintainers, Intel is only one of them. As a maintainer they have the right to NAK patches and therefore can influence a project - in this case done via their management (commit) and they show their commitment to Wayland and Canonicals attitude concerning said ecosystem. Nobody can deny that Canonical had a good hand of how different aspects got handled in the past and up till now. MIR is also a political decision of a company and not only a technical decision (if it is which I deny) to get control of it's platform and future direction.

---

### Post by monkeybrain20122 on 2013-09-08
> **etna2 said:**
> 


No other distro intends to use Mir, period. Arch and Gentoo are preparing for Wayland, and so are most of the major RPM-based distributions like OpenSUSE and Fedora. Conservative distributions like Debian will stay on X for the forseeable future until the migration is well and fully tested, and even then, the fact that Debian does not have any Mir packages in unstable, testing or experimental says a lot when there are Wayland packages in those repositories. 

Even official Ubuntu derivatives such as Xubuntu, Lubuntu and Kubuntu refuse to use Mir, preferring instead to stick with X for the forseeable future and eventually migrate over to Wayland once the dust settles. So Mir is every bit a single-distro-only solution. And single-distro-only software = do your own patches yourself.

This can change, especially with debian based disros (RedHat also has vested interest in Wayland) but with Intel being uncooperative in this high handed way surly it will discourage other distros to try out MIr. And btw why is it that there is no complaint about deb vs rpm being fragmenting?

Other than Kubuntu I am not aware that the other Ubuntu derivatives are committed to Wayland. For example, Xubuntu devs say that they are not using xmir in 13.10 after extensive testing, this is not to say that they never will and the fact that they actually went through the testing suggests that they consider it an option.

The main reason for Mir, I think, is that Canonical cannot wait for Wayland to mature as it has a tight deadline a bunch of specifications to meet, so it would be hard to rely on upstream developers who have different priorities, time frames and goals, it is really nobody's fault and it doesn't have to turn into a war. Intel's latest decision is not helping especially this is not a technical decision and its own developer appears to have no problem with accepting Canonical's patch  (Intel has  declared neutrality in the Wayland vs Mir thing earlier if I remember correctly)

---

### Post by ikt on 2013-09-08
> **codingman said:**
> What the hell was wrong with X anyways? 
What the hell was (is) wrong with *Wayland* anyways?
Why don't the devs spend their sweet time fixing suspend from command-line instead?

[video=youtube;RIctzAQOe44]http://www.youtube.com/watch?v=RIctzAQOe44[/video]

I try and get as many people to watch this as possible :)

---

### Post by bapoumba on 2013-09-08
Closed for Staff review.

---

### Post by Elfy on 2013-09-09
Re-opened.

Let's see if we can have a discussion without the trolling.

---

### Post by Bucky Ball on 2013-09-09
@ikt: The MC or presenter you, ikt? I notice the Australian accents. ;)

---

### Post by whatthefunk on 2013-09-09
Canonical wants to go out on their own.  These are the consequences.

---

### Post by mastablasta on 2013-09-09
well to me it's strange they go against everything and against warnings form others. i understand you need ot stand for yourself, but sometimes some self reflection is necessary. 
the Ubuntu Edge campain was ran in a ridiculous way (the incentives, the choice of campaign place...) only to have it failed miserably despite so many pledges by companies and individuals...
they went on their own with GTK based Unity interface (which still doesn't work with all apps) totally abandoning KDE (Qt) based Kubuntu (apparently because businesses were more interested in Gnome) only to later finding out that they should use Qt for mobile version... And this despite the fact that when they were still planning mobile OS the KDE already had a working Qt based plasma touch interface. and the fact that they in the end dropped Gnome interface anyway.

inventing the wheel is what they do lately it seems... but then again it is their choice and they have to deal with consequences. it seems to me they really do have plenty of resources. or at least so they think.

---

### Post by mikewhatever on 2013-09-09
> **mastablasta said:**
> well to me it's strange they go against everything and against warnings form others. i understand you need ot stand for yourself, but sometimes some self reflection is necessary. 
the Ubuntu Edge campain was ran in a ridiculous way (the incentives, the choice of campaign place...) only to have it failed miserably despite so many pledges by companies and individuals...
they went on their own with GTK based Unity interface (which still doesn't work with all apps) totally abandoning KDE (Qt) based Kubuntu (apparently because businesses were more interested in Gnome) only to later finding out that they should use Qt for mobile version... And this despite the fact that when they were still planning mobile OS the KDE already had a working Qt based plasma touch interface. and the fact that they in the end dropped Gnome interface anyway.

inventing the wheel is what they do lately it seems... but then again it is their choice and they have to deal with consequences. it seems to me they really do have plenty of resources. or at least so they think.

Where does all the "if you aren't with us, you are against us" attidude come from?
Ubuntu decided to go its own way, so what? Why is that a bad thing?
Why are people (many of whom, apparently don't use Ubuntu) so peeved up about Canonical tying to invent something?

---

### Post by ZoiaGuyver on 2013-09-09
I still don't understand why Wayland just has to be accepted by a "one fits all" solution. Mir just gives Canonical a better way to make use of Unity 8. 

The whole argument though is invalid to begin with.. "The management" is not a technical refusal for any commit, the project is open source it only means that as has been done every other time, Downstream will be responsible for the patches, more work for Ubuntu and the maintainers but meh.

We are 5 years on and still waiting to see the Wayland protocol to be used as a default in any distribution. You can say "Oh well the community agreed" the community didn't agree to anything in Wayland.. It was the ONLY choice. Also look at past experience with the "community" we have been happily chugging away with a 26 year old X server because there was nothing else. 

From my point of view all this backing of Wayland is great, but to say the GNU/Linux community supports it is kinda meh, Wayland is not GPL'd, Other projects wont accept XMir/Mir as it is GPLv3 and it isn't "upstream", yet the patches to make it available upstream are then reverted by the management. How does this management talk for everyone in the community? I've been a Linux user for the last 20+ years of my life and to see such underhanded tactics as "the management" used in a so called "open source" project is sickening. The whole argument around this is not that the commit was refused, it is the reason it was reverted, "The Management". No technical reason, not even a "well its a single distro solution so we don't feel the patch is needed upstream" (although that goes back to the original point of Mir not being accepted upstream, so other projects wont use it).

We can all criticise Canonical for the way they have done things (hell most of us do it daily including me!, when something doesn't work just the way I want), but they are only human.. Intel is just a company after their own goals, I guess even after all the years battling for Wintel to disappear people are just happy to see someone else as the bad guy, in this case Canonical/Ubuntu. People can say about Canonical not giving back upstream, yet this isn't the first time that Canonical has pushed for acceptance upstream only to be told "No".

Wayland is not working in any distro as a default, it does not even have a fully commited distro as of yet (Rebeccablack is a tech preview), it can talk all it wants about how it is the accepted solution but as for the distros using it as a default protocol (to use a Linus Torvalds comment) "Talk is cheap, Show us the code". Wayland does not have full support from the "Desktop linux" market (one of the influential distros is kinda missing), Yet already has commits to support it upstream, one of the main devs for Wayland works at Intel, a few of the others at Collabora. 

Most say they use linux because it's "open source" I guess that fits for aslong as you want, then you can change on a penny. I'm not a "Free software" advocate, I'm an "Open Source" advocate.

I'll stop the rant though, Its probably a wasted excercise as most seem to want Wayland and no competition.. I guess having competition is bad, I mean Linux isn't the only kernel, it is the best (in a lot of peoples opinion, including mine). But there are a lot of others like Mach, but I guess having a choice on the only part of the system that the "Community" has decided on is fine, X is the only thing that between most systems is the only solution.

---

### Post by etna2 on 2013-09-09
> **mikewhatever said:**
> Where does all the "if you aren't with us, you are against us" attidude come from?
Ubuntu decided to go its own way, so what? Why is that a bad thing?
Why are people (many of whom, apparently don't use Ubuntu) so peeved up about Canonical tying to invent something?

Canonical are free to do what they want, and they better be prepared for the consequences of their actions.

Any distro is free to fork and invent what they think is needed for themselves **as long as they leave the core base system stack alone. **Especially when X --> Wayland was already determined 3 years ago as the de facto migration path **when Canonical themselves first proposed it**. This X-to-Wayland migration was also backed by all the major distributions.

This is tantamount to backstabbing, especially when Canonical never bothered to contribute **anything** to the Wayland project over those 3 years, and suddenly released their own 'open' project that was developed in secret, and essentially split the graphics stack into 2; Mir vs Wayland with all the crap such as incompatible drivers that they single-handedly created.

And they got the gall to request that upstream accept their single-distro-only Mir compatibility patches, and subsequently complain that upstream is making their life harder by refusing to accept them?

And for the record, this is not the first time Canonical has been hostile to the larger Linux software stack. At a much higher level, ever wonder why not a single distribution is actively packaging Unity as a DE even though Canonical claims that they are free to do so? Here's the answer; it requires so many Ubuntu-specific bits and patches that it places an unnecessary maintenance burden for any non Ubuntu-based distribution. 

Canonical has never planned to share their projects with the larger Linux user base, period. Just throwing code out there as open source does not mean a thing at all. You can see from how every single patch request made to the various toolkits, Mesa and the individual X drivers have been either rejected outright or just plain ignored. 

Since Canonical loves to do things their own way there's nothing stopping them from tracking every single X driver, Xserver and Mesa release and performing downstream patches themselves. Since is it claimed in the various mailing lists that the patchset is reasonably small (<1500 lines), it should be a walk in the park to perform those downstream patches.

> Wayland does not have full support from the "Desktop linux" market (one  of the influential distros is kinda missing), Yet already has commits  to support it upstream, one of the main devs for Wayland works at Intel,  a few of the others at Collabora.

GTK3 and Qt5 are almost fully Wayland capable. Gnome is also close to full Wayland support, while KDE is expected to see core Wayland support with Frameworks 5. I consider that very significant support considerig almost every single desktop Linux configuration is built over GTK or Qt. And neither of them even want to consider Mir support as an upstream goal. at all.

---

### Post by ZoiaGuyver on 2013-09-09
Who decided it was the "de facto migration"? it definatly wasn't the community as the community already has a choice in every other part of the system bar X, so it being the communitys decision would mean around 30 display servers/Protocols. 

Look at it this way..

Kernel: Linux, Mach, BSD (plus many others)

DE/UX: Unity, Gnome, KDE, LXDE (many others)

Toolchain: GNU, Cygwin, MiniWG, PS3 (others)

Display Server: X.org

I kinda see a problem there as far as wanting a monopoly on one part of the system goes.. Also Drivers are written for the Architecture be it x86, ARM, PPC, there is even a choice there on what to use. Yet display server, no we can't have competition there, it has to be X > Wayland and nothing else..

---

### Post by prodigy_ on 2013-09-09
> **etna2 said:**
> Since Canonical loves to do things their own way there's nothing stopping them from tracking every single X driver, Xserver and Mesa release and performing downstream patches themselves.
And eventually making their own kernel.

Seriously, the sooner - the better.

---

### Post by etna2 on 2013-09-09
> **ZoiaGuyver said:**
> Who decided it was the "de facto migration"? i

Canonical (at that time)
Red Hat
Fedora
OpenSUSE
Arch
GTK
Qt
Intel
KDE
Gnome
**X.org** (at least, the Linux developers)

and recently, Mate.

---

### Post by ZoiaGuyver on 2013-09-09
The kernel has nothing to do with this at all. Linux is a "universal" kernel. Plus in a sense people do "make" their own kernels through guess what "patches" CK patch sets and many others. 

But i agree I wish Canonical would say "Fu" to the community as a whole and just close off all the stuff they do, like Google does. Then we wouldn't have the problem of a so called "Community" thinking they have any decision on the course of a project.

---

### Post by mikewhatever on 2013-09-09
> **etna2 said:**
> 

...trolling


See what I am talking about? Another one, just signed up to slander.

---

### Post by ZoiaGuyver on 2013-09-09
Well i see the distros there, none of which who have it working in any of their distros as of yet due to it having nothing but a reference compositor also most of the distros follow upstream which Mir can't be part of because of the "Management".. 

Why Canonical is there kinda makes it weird, Ubuntu is based on Debian. Debian will be for atleast a long while yet stuck with X.org, Red Hat and Fedora are one in the same, so your left with OpenSuse and Arch.. Both of which have no choice but to follow what the "management" says as they have only one choice from Upstream X > Wayland.

---

### Post by etna2 on 2013-09-09
> **ZoiaGuyver said:**
> The kernel has nothing to do with this at all. Linux is a "universal" kernel. Plus in a sense people do "make" their own kernels through guess what "patches" CK patch sets and many others. 

Yes they do, and do any of those kernels break compatibility with the main kernel? No, it doesn't. It's still the Linux kernel and everything that was created to work with the standard Linux kernel will work in the patched kernel.

This is not what is going on with Mir. It is incompatible with Wayland, It needs its own rewritten drivers. Rewrites and recodes which upstream has no intention of accommodating,.

---

### Post by ZoiaGuyver on 2013-09-09
It is not incompatible with Wayland (Wayland is only a Protocol), if someone writes the code Mir can act as the compositor for Wayland same as Weston does now..

---

### Post by ZoiaGuyver on 2013-09-09
No,  "You are what you are, because its what you decided you must be."

lol lets blame "Mr Shuttleworth" for everything thats wrong with the IT World. Makes life easier to blame someone rather than take it on your own shoulders.

---

### Post by nenadlatinovic on 2013-09-09
Can anyone answer how's this going to work out for the end user, who does not know even what this issue is all about?

---

### Post by ZoiaGuyver on 2013-09-09
It wont affect the end user at all, What it means in laymens terms is rather than everything being done at the factory, it needs some of it done DIY (not by the end user) and then the end user gets it. (hope that makes it easier to understand).

Which is basically what happens for every release anyways as a lot of stuff is patched then tested. Its also why we have Alpha > Beta > Release.

---

### Post by JDShu on 2013-09-09
> **ZoiaGuyver said:**
> I still don't understand why Wayland just has to be accepted by a "one fits all" solution. Mir just gives Canonical a better way to make use of Unity 8.    In what way does Mir help Canonical make use of Unity? By the way, Wayland is a standard with some helper libraries to implement that standard. There are very good reasons to want everybody to accept a standard (as opposed to an implementation).  >  The whole argument though is invalid to begin with.. "The management" is not a technical refusal for any commit, the project is open source it only means that as has been done every other time, Downstream will be responsible for the patches, more work for Ubuntu and the maintainers but meh.   Sometimes, there are no technical reasons to do some things. Mir itself is one example.  >  We are 5 years on and still waiting to see the Wayland protocol to be used as a default in any distribution.   You may want to do some research on why this is. Much of what Mir did is built on the groundwork that was required to get Wayland working. Saying "it's been 5 years and nothing has happened" is a gross oversimplification.  >   You can say "Oh well the community agreed" the community didn't agree to anything in Wayland.. It was the ONLY choice. Also look at past experience with the "community" we have been happily chugging away with a 26 year old X server because there was nothing else.    Well, now the community minus Canonical has agreed. And anyway, Canonical in particular agreed early on, and then suddenly revealed that they had been developing Mir in secret instead. This is generally looked down on in the open source community.  >  From my point of view all this backing of Wayland is great, but to say the GNU/Linux community supports it is kinda meh, Wayland is not GPL'd, Other projects wont accept XMir/Mir as it is GPLv3 and it isn't "upstream", yet the patches to make it available upstream are then reverted by the management. How does this management talk for everyone in the community? I've been a Linux user for the last 20+ years of my life and to see such underhanded tactics as "the management" used in a so called "open source" project is sickening. The whole argument around this is not that the commit was refused, it is the reason it was reverted, "The Management". No technical reason, not even a "well its a single distro solution so we don't feel the patch is needed upstream" (although that goes back to the original point of Mir not being accepted upstream, so other projects wont use it).   Intel Management is not talking for everybody in the community. Intel Management is talking for Intel and it just so happens that many people in the community agree for various reasons. Again, there are not always technical reasons as Ubuntu defenders are always willing to support when it comes to Mir. Perhaps ethically Intel is in the wrong here, but so is Canonical. It's called business. Remember when Canonical changed the terms with Banshee? And the time they decided to refuse support for the Raspberry Pi? To many people including me, those were unethical things to do. It was also their right.  >  We can all criticise Canonical for the way they have done things (hell most of us do it daily including me!, when something doesn't work just the way I want), but they are only human.. Intel is just a company after their own goals, I guess even after all the years battling for Wintel to disappear people are just happy to see someone else as the bad guy, in this case Canonical/Ubuntu.   Why is Canonical "only human" and Intel "just a company"?  >  People can say about Canonical not giving back upstream, yet this isn't the first time that Canonical has pushed for acceptance upstream only to be told "No".   You don't just throw code to upstream. It is a back on forth process that requires mutual respect and understanding. The maintainer wants code that can be of use to them - they don't just accept things willy nilly. There are many reasons for why they won't accept your code, although it can be done eventually through effort.  >  Wayland is not working in any distro as a default, it does not even have a fully commited distro as of yet (Rebeccablack is a tech preview), it can talk all it wants about how it is the accepted solution but as for the distros using it as a default protocol (to use a Linus Torvalds comment) "Talk is cheap, Show us the code". Wayland does not have full support from the "Desktop linux" market (one of the influential distros is kinda missing), Yet already has commits to support it upstream, one of the main devs for Wayland works at Intel, a few of the others at Collabora.    There is code. More code than there is for Mir in fact. As I stated earlier, much of what Mir did that looks like rapid progress is actually due to groundwork done to allow Wayland to start working. Indeed something like xMir is something that has been working for wayland for years (xWayland) but it doesn't actually make sense to use it in a real distribution, besides in the way that Canonical is - trying to get testers and have a smooth transition.  >  Most say they use linux because it's "open source" I guess that fits for aslong as you want, then you can change on a penny. I'm not a "Free software" advocate, I'm an "Open Source" advocate.  I'll stop the rant though, Its probably a wasted excercise as most seem to want Wayland and no competition.. I guess having competition is bad, I mean Linux isn't the only kernel, it is the best (in a lot of peoples opinion, including mine). But there are a lot of others like Mach, but I guess having a choice on the only part of the system that the "Community" has decided on is fine, X is the only thing that between most systems is the only solution.  You yourself seem to understand that Wayland is a protocol, not an implementation. Surely then, you understand why it's better to support a protocol for a solution over an implementation?

---

### Post by vasa1 on 2013-09-09
> **mikewhatever said:**
> ...
Why are people (many of whom, apparently don't use Ubuntu) so peeved up about Canonical tying to invent something?
That's the consequence of allowing "Discussions" here instead of being just a pure support forum.
For a start, these posts addressed to Canonical or about Canonical should be diverted to [http://ubuntu-discourse.org/](http://ubuntu-discourse.org/).

---

### Post by Elfy on 2013-09-09
> **vasa1 said:**
> That's the consequence of allowing "Discussions" here instead of being just a pure support forum.
For a start, these posts addressed to Canonical or about Canonical should be diverted to [http://ubuntu-discourse.org/](http://ubuntu-discourse.org/).

There were discussions going on here a long time before you joined.

There'll be discussions here as long as our users want them.

---

### Post by ZoiaGuyver on 2013-09-09
Mir is not forked or based on Wayland, it makes use of the same interfaces OpenGL/ES, DRI2, KMS. Its actually closer code wise to Surfaceflinger on android or even iOS. 

The code wasn't just thrown upstream.. it was debated (but looking at your response I guess you didn't read that). The patch was accepted and merged upstream only to be reverted by the "management". There was actually a "release" of the branch 2.99.901 that had the patch included.

Mir is a Protocol, Compositor, Session Manager basically it does what with Wayland is in 3 parts Wayland, Compositor (Gnome/KDE) GDM/KDM. This for Ubuntu is right direction as it means a it can be integrated better with Unity.

I hope and know Wayland Project will be a success in its own right, what I don't agree with is Mir not even being given a chance. No technical reasons as to why Mir can't stand a chance other than the management.

Gnome and KDE are the "implementation" of the Wayland Protocols Compositor, so already you have two differing designs and toolkits that need to support Wayland. QT and GTK for the most part do already, but neither of them supply a compositor (Clutter/Mutter/Gnome-Shell are still in progress as is Kwin). 

I guess it should be just an agree to disagree.

---

### Post by vasa1 on 2013-09-09
> **nenadlatinovic said:**
> Can anyone answer how's this going to work out for the end user, who does not know even what this issue is all about?
The end user need not panic: [http://www.youtube.com/watch?v=ZR6wok7g7do](http://www.youtube.com/watch?v=ZR6wok7g7do)
(Mods: I promise that's the last time I'll post that link)

---

### Post by mbohets on 2013-09-09
I guess this is the downside of having many options, manufactureres will not support all of them, they will choose only the most used one.
There is X, wayland, Mir, and suppors 10 other guys also start writing their own graphics SW, it will be a nightmare to support all of them.

---

### Post by Elfy on 2013-09-09
We are quite happy for people to discuss this issue - and in fact like to see it.

We won't though sit back and let trolls ruin the discussion for others.

If you can't make your point without doing so then take it elsewhere.

Thanks

---

### Post by ZoiaGuyver on 2013-09-09
Sorry Elfy.

Will try to keep the discussion on track.

---

### Post by philinux on 2013-09-09
> **nenadlatinovic said:**
> Can anyone answer how's this going to work out for the end user, who does not know even what this issue is all about?

> What This Means For You

Canonical are set to enable XMir in 13.10 for supported hardware. Though the removal of XMir support from the Intel drivers is a step backwards in some respects, Canonical plan on including the patches in their downstream packages nonetheless.


If you will be using Intel graphics on Ubuntu 13.10, the drivers will continue to support XMir as they did up until yesterday – through patches.

Canonical’s Alan Pope explained the impact to us in a tweet earlier: “[This decision] just means more work for us (Canonical) to keep integrating xmir patches into x with each release/update.”

From [http://www.omgubuntu.co.uk/2013/09/intel-remove-xmir-support-in-xorg-video-driver?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2013/09/intel-remove-xmir-support-in-xorg-video-driver?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by JDShu on 2013-09-09
> **ZoiaGuyver said:**
> Mir is not forked or based on Wayland, it makes use of the same interfaces OpenGL/ES, DRI2, KMS. Its actually closer code wise to Surfaceflinger on android or even iOS.    I don't think I ever claimed it was forked or based on Wayland? In fact the problem I see is that it isn't.  >  The code wasn't just thrown upstream.. it was debated (but looking at your response I guess you didn't read that). The patch was accepted and merged upstream only to be reverted by the "management". There was actually a "release" of the branch 2.99.901 that had the patch included.   I know that, but you specifically said "This isn't the first time" and the last time Canonical had code rejected was just such a situation. This time it's because Canonical is going their own way and made enemies with Intel. Canonical will just have to bear the consequences.  >  Mir is a Protocol, Compositor, Session Manager basically it does what with Wayland is in 3 parts Wayland, Compositor (Gnome/KDE) GDM/KDM. This for Ubuntu is right direction as it means a it can be integrated better with Unity.   The Mir developers specifically state that they will not try to have a stable protocol - I mean they call it "protocol agnostic" whatever that means. You're right, it basically does what Wayland does, so why don't they just implement Wayland? The reason I suspect is control, which is fair enough, but that means that upstream shouldn't be expected to handle their code.  >  I hope and know Wayland Project will be a success in its own right, what I don't agree with is Mir not even being given a chance. No technical reasons as to why Mir can't stand a chance other than the management. [/quote  There are also no technical reasons for why Mir needs to exist. That is really the problem for the developer community.  [quote] Gnome and KDE are the "implementation" of the Wayland Protocols Compositor, so already you have two differing designs and toolkits that need to support Wayland. QT and GTK for the most part do already, but neither of them supply a compositor (Clutter/Mutter/Gnome-Shell are still in progress as is Kwin).   I guess it should be just an agree to disagree.  What exactly are you trying to argue?

---

### Post by Yougo on 2013-09-09
i've been trying to find anything intelligent on the Internet about this, and found some discussions making a good start, only to be derailed by what seem to be a bunch of uninformed attention starved twelve year olds. (i'm not sure if it's a positive thing if these people actually aren't twelve year olds :-k )

finally i found something; Christopher Halse Rogers posted some things that at least make sense:
[http://blog.cooperteam.net/2013/03/for-posterity.html](http://blog.cooperteam.net/2013/03/for-posterity.html)
[http://blog.cooperteam.net/2013/03/mir-and-you.html](http://blog.cooperteam.net/2013/03/mir-and-you.html)
[http://blog.cooperteam.net/2013/03/server-allocated-buffers-in-mir.html](http://blog.cooperteam.net/2013/03/server-allocated-buffers-in-mir.html)
[http://blog.cooperteam.net/2013/03/artistic-differences.html](http://blog.cooperteam.net/2013/03/artistic-differences.html)
read in this order.

from linked point of view, it makes quite a lot of sense to go for Mir, and with that attitude in mind, i can see how, while Intel accepting the patch would have made life easier, Canonical didn't count on much, or even 'demanded' support from upstream anyway.

From what i read, Mir isn't even meant as a direct across the board competitor to Wayland. Apparently Mir happened because of mobile architectural demands.

i do agree that if Canonical were more open about their motivation, and said exactly what Chris said, much of the bad seeds wouldn't have been planted.
conversely if intel were a bit less cryptic bout their rejection, many of those seeking drama wouldn't have found it there.

---

### Post by buzzingrobot on 2013-09-09
1. Canonical has determined it needs Mir to support its effort to build an essentially platform-independent OS.

2. One individual has posted one comment asserting that Intel won't support Mir. Let's assume that's accurate.

3. Therefore, if Mir is to have Intel support, Canonical must furnish it.

4. Or, pay Intel to do it.

I've always been a bit surprised that Intel, Nvidia and AMD provide any gratis driver support.  I assume they do it to create good will, and, to a degree, foster hardware sales. Are Nvidia/AMD personnel actually paid to do this?

---

### Post by ZoiaGuyver on 2013-09-09
Wayland is only the Protocol. They can't "implement" Wayland, at the moment Wayland does not have any Compositor other than Weston, Gnome Wayland support and prob KDE will not be around till spring 2014 meaning that it will also be to late for 14.04, basically to get Wayland on Ubuntu, Canonical and Ubuntu have to wait again after already waiting 3 years to be able to use it. Saying Canonical should have just gone all in on Wayland is kinda weird, why does Wayland need Canonical when they have Redhat/Suse/Intel devs all working on it (also brings up why it hasn't gotten further than it has). Mir is all of it, the compositor the library the server. 

And again someone doesn't see the problem of actually including the patch, releasing a branch with that patch included, then reverting the change due to "management". They had already accepted the code..

Anyways all this is just going in circles. People want to suport Wintel v2.0 thats fine, I'll stick to Ubuntu as that is my choice and the choice of many others.

---

### Post by JDShu on 2013-09-09
> **buzzingrobot said:**
>  I've always been a bit surprised that Intel, Nvidia and AMD provide any gratis driver support.  I assume they do it to create good will, and, to a degree, foster hardware sales. Are Nvidia/AMD personnel actually paid to do this?  The reason according to AMD developers is that the workstation market needs Linux drivers that work, and that is where the money comes from. Large companies probably pay nVidia/AMD for support contracts.

---

### Post by JDShu on 2013-09-09
> **ZoiaGuyver said:**
> Wayland is only the Protocol. They can't "implement" Wayland, at the moment Wayland does not have any Compositor other than Weston, Gnome Wayland support and prob KDE will not be around till spring 2014 meaning that it will also be to late for 14.04, basically to get Wayland on Ubuntu, Canonical and Ubuntu have to wait again after already waiting 3 years to be able to use it. Saying Canonical should have just gone all in on Wayland is kinda weird, why does Wayland need Canonical when they have Redhat/Suse/Intel devs all working on it (also brings up why it hasn't gotten further than it has). Mir is all of it, the compositor the library the server.    Wait, what? Wayland is "only" a protocol, that is (mostly) correct, and protocols are made to be implemented. Maybe you're getting choosy about the words used? I'm saying that Canonical could have written a compositor or extended Unity/Compiz such that it used the Wayland protocol, which would have been simpler than designing everything from the ground up and caused less friction. The reason it hasn't gotten further is because the groundwork - for example EGL support - had to be done first. So no actually, even if Ubuntu had wanted to use Mir from the start, they would still have had to wait 3 years. Mir support isn't even expected until 14.04 anyway - and even that is optimistic.  >  And again someone doesn't see the problem of actually including the patch, releasing a branch with that patch included, then reverting the change due to "management". They had already accepted the code..   And again, sometimes the reasons are not technical. Intel gets to choose what goes into their own drivers, regardless of ethics. Like I said earlier, Canonical is not a shining beacon of ethics either, particularly regarding this issue.  >  Anyways all this is just going in circles. People want to suport Wintel v2.0 thats fine, I'll stick to Ubuntu as that is my choice and the choice of many others.  Of course we can all do what we want, I just don't want people reading this thread to be misinformed. Also, discussing this issue in detail is a great way for me and (hopefully for you) to verify my comprehension of the situation

---

### Post by ZoiaGuyver on 2013-09-09
Mir is actually in 13.10 if your running the opensource drivers. Its actually XMir on top of Mir, the only time this changes in 13.10 is when you install NV or ATI blob drivers then it falls back to X.org

Wayland is just the protocol and I think they actually use the Wayland name for the C library (which is Wayland aswell ofc), Weston is it's compositor at the moment but only a "tech preview" as it were. I don't think I have misled anyone in what I posted. I have been researching Wayland and tracking its progress since it was announced 5 years ago on and off, the whole concept of basically a "serverless" display manager is rather intriguing. Leveraging the kernel and hardware to do the work is how it should be, allowing the clients to control their own output as it were is also in a weird way genius. Its a lot less problematic.

If the patch was openly refused or with even a weak excuse like "maintainance" I could have accepted that and it would have been a totally understandable position. But to include the patch, release it and then revert it with only "the management does not support Canonical chosen path" as a reason is totally politics and competition related. Thats the problem I have with it as they also stated they were "neutral", how is it neutral to refuse a patch from one display manager but include ones from the other?

I didn't mean to seem picky about the words but most are reffering to Wayland as a "Display Server" which it is not, Weston is a (for want of a better term)display server, Mir is a (same as before)display server, Wayland is a protocol.

Wayland and Mir are not really competing projects as if the code was written Mir could act as the compositor for Wayland much like Gnome and KDE. This has been discussed but people only see what they want. The problem with the "protocol agnostic" solutions is it does invite a lot of bickering. If Mir had been announced as the Compositor for Wayland using Unity it probably wouldn't have even heard a whisper. But because it was also chose that Mir should be a display manager aswell is when the sparks flew, plus the fact that Canonical posted a lot of FUD on the issue (which i give credit to them for apologising for, but it should have been researched before it was posted).

---

### Post by philinux on 2013-09-09
Interesting to see what's installed in 13.10 to do with wayland.
```

aptitude search wayland
i A libwayland-client0                        - wayland compositor infrastructure - client library  
p   libwayland-client0:i386                   - wayland compositor infrastructure - client library  
p   libwayland-client0-dbg                    - wayland compositor infrastructure - client library (
p   libwayland-client0-dbg:i386               - wayland compositor infrastructure - client library (
i A libwayland-cursor0                        - wayland compositor infrastructure - cursor library  
p   libwayland-cursor0:i386                   - wayland compositor infrastructure - cursor library  
p   libwayland-cursor0-dbg                    - wayland compositor infrastructure - cursor library (
p   libwayland-cursor0-dbg:i386               - wayland compositor infrastructure - cursor library (
p   libwayland-dev                            - wayland compositor infrastructure - development file
p   libwayland-dev:i386                       - wayland compositor infrastructure - development file
i A libwayland-server0                        - wayland compositor infrastructure - server library  
p   libwayland-server0:i386                   - wayland compositor infrastructure - server library  
p   libwayland-server0-dbg                    - wayland compositor infrastructure - server library (
p   libwayland-server0-dbg:i386               - wayland compositor infrastructure - server library (
c   libwayland0                             
```  - wayland compositor infrastructure - shared libraries

---

### Post by ZoiaGuyver on 2013-09-09
Also weird to see it in 13.04

aptitude search wayland
p   libwayland-dev                  - wayland compositor infrastructure - develo
p   libwayland-dev:i386             - wayland compositor infrastructure - develo
i   libwayland0                     - wayland compositor infrastructure - shared
p   libwayland0:i386                - wayland compositor infrastructure - shared
p   libwayland0-dbg                 - wayland compositor infrastructure - shared
p   libwayland0-dbg:i386            - wayland compositor infrastructure - shared

I'm guessing that the libwayland-server/client/cursor are new in 13.10. best guess would be that the librarys are for IPC maybe?

Plus don't see any Xwayland, they were meant to be using evdev for input and KMS. So I guess I was wrong in thinking that Wayland was only the protocol, it seems to have been made into a full display server (or atleast library wise). Sorry for the misinterpretation.

So much for

"In wayland the compositor is the display server. We transfer the control of KMS and evdev to the compositor. The wayland protocol lets the compositor send the input events directly to the clients and lets the client send the damage event directly to the compositor"

And Mir by comparison

mir
unity-greeter-session-broadcast
unity-system-compositor

---

### Post by Gyokuro on 2013-09-09
> **ZoiaGuyver said:**
> I still don't understand why Wayland just has to be accepted by a "one fits all" solution. Mir just gives Canonical a better way to make use of Unity 8. 

The whole argument though is invalid to begin with.. "The management" is not a technical refusal for any commit, the project is open source it only means that as has been done every other time, Downstream will be responsible for the patches, more work for Ubuntu and the maintainers but meh.

We are 5 years on and still waiting to see the Wayland protocol to be used as a default in any distribution. You can say "Oh well the community agreed" the community didn't agree to anything in Wayland.. It was the ONLY choice. Also look at past experience with the "community" we have been happily chugging away with a 26 year old X server because there was nothing else. 

From my point of view all this backing of Wayland is great, but to say the GNU/Linux community supports it is kinda meh, Wayland is not GPL'd, Other projects wont accept XMir/Mir as it is GPLv3 and it isn't "upstream", yet the patches to make it available upstream are then reverted by the management. How does this management talk for everyone in the community? I've been a Linux user for the last 20+ years of my life and to see such underhanded tactics as "the management" used in a so called "open source" project is sickening. The whole argument around this is not that the commit was refused, it is the reason it was reverted, "The Management". No technical reason, not even a "well its a single distro solution so we don't feel the patch is needed upstream" (although that goes back to the original point of Mir not being accepted upstream, so other projects wont use it).

We can all criticise Canonical for the way they have done things (hell most of us do it daily including me!, when something doesn't work just the way I want), but they are only human.. Intel is just a company after their own goals, I guess even after all the years battling for Wintel to disappear people are just happy to see someone else as the bad guy, in this case Canonical/Ubuntu. People can say about Canonical not giving back upstream, yet this isn't the first time that Canonical has pushed for acceptance upstream only to be told "No".

Wayland is not working in any distro as a default, it does not even have a fully commited distro as of yet (Rebeccablack is a tech preview), it can talk all it wants about how it is the accepted solution but as for the distros using it as a default protocol (to use a Linus Torvalds comment) "Talk is cheap, Show us the code". Wayland does not have full support from the "Desktop linux" market (one of the influential distros is kinda missing), Yet already has commits to support it upstream, one of the main devs for Wayland works at Intel, a few of the others at Collabora. 

Most say they use linux because it's "open source" I guess that fits for aslong as you want, then you can change on a penny. I'm not a "Free software" advocate, I'm an "Open Source" advocate.

I'll stop the rant though, Its probably a wasted excercise as most seem to want Wayland and no competition.. I guess having competition is bad, I mean Linux isn't the only kernel, it is the best (in a lot of peoples opinion, including mine). But there are a lot of others like Mach, but I guess having a choice on the only part of the system that the "Community" has decided on is fine, X is the only thing that between most systems is the only solution.

What I never get is the argument: Wayland has been in development for 5 years and up till now we have nothing: take only a look in your ubuntu system and tell me something about KMS, modularising of X, MesaEGL and you have your five years of development - that argument is not fair against the developers which have done an enormous job and everybody of us have all this little parts in our systems and enjoy them with our daily work with said systems and their engineering work and for X developers the last step is wayland. Without previous mentioned project tasks even MIR were not possible as the major work were done by the X.org/Mesa developers.

---

### Post by buzzingrobot on 2013-09-09
> **ZoiaGuyver said:**
> ...most seem to want Wayland and no competition.. I guess having competition is bad...

As a user. my interests are served by better Linux products.  Competition works to deliver better products elsewhere.  There's nothing special about Linux that exempts it.

I realize egos have been bruised and toes stepped on in this game.  It is, though, a game developers are playing, not users.

Developer communities share many characteristics with cartels, in that they tend to prefer widespread agreement on how to do something.  That reduces risk, reduces the learning curve, and eliminates the hassle and cost of making your code work in different contexts.Competition is the antithesis of that.

 Trouble is, that leaves users out of the loop.  We're stuck with choices made by developers for reasons that don't advantage users.

---

### Post by monkeybrain20122 on 2013-09-09
> **buzzingrobot said:**
> 

I realize egos have been bruised and toes stepped on in this game.  It is, though, a game developers are playing, not users.



Probably not even so much developers, but company politics Redhat vs Canonical etc

---

### Post by ZoiaGuyver on 2013-09-09
See this is the thing, you say all the work is in KMS, Modularising X (which has zero effect on wayland as its a re-write from the ground up, so was a pointless task in the context of Wayland) MesaGL. None of this was done by the "Wayland". team, they may have contributed to it as individuals but not as "Wayland". There is also the problem that some of the tech like KMS was implemented before wayland was even planned or thought of. 

I give credit where its due, but in 5 years we have seen no "working" distro with Wayland, Fedora has said now they are aiming for a tech preview in Fedora 20 but it is just that a Tech Preview. The Wayland devs have done amazing things and I never meant for people to feel I was taking away from that. But the work they have done has also been slow without any real reason. Intel and Redhat have been said to be collaborating on Wayland, yet only now were seeing the actual tech demos in working systems (by working I mean actual distros with it as a usable thing)?. Wayland may have layed some of the ground work for Mir, but also remember that Wayland has been accepted upstream, has the backing and help of atleast three big companies (Redhat/Intel/Novell) with that much manpower on the project does it not seem to be slow in making us a replacement?

buzzingbot, that comment you quote, was more that Wayland seems to not want any competition at all. There has been a lot of debate back and forth, with crap in both directions. As an end user your right it has no affect at all, or atleast the end-user should not notice any change. Thats the only consistent thing between both projects.

You're also correct about us being stuck with what devs decide. Redhat, Intel, Canonical, Novell have all in their time been total muppets and done a lot of things that have had adverse affects on the community. 

But the decision by Canonical to go with their own display server for thier own release is a decision that helps not only Canonical but the whole of opensource (if it wasn't for the devs upstream..) the Mir code is GPLv3 meaning we can study it (which I've already been looking at it and that of Wayland). Both projects have a right to survive and on level grounds, anyone remember Xfree86? and how X.org was actually a fork of that at the start? anyone remember Xouvert?

See this is where people like myself get all misty eyed and nostalgic. X.org for better or worse, killed off the other projects. X.org at the start of it was pretty much dead, but it picked up momentum and with the backing of the large distros (who didn't have much choice due to Xfree86s licence change) moved to X.org. So the little "fork" of Xfree86 made good.

Now flash forward to today, we have had X.org since around 2003/2004 they have done great things, making the X display server modular, advancing things like Direct Rendering support. Noone can ever deny the work they have done is amazing. Now that X.org has basically reached its end, it's been showing its age for a long time but due to the efforts of Free Software has been kept alive. But now we also have Mir that is made by a company who actually came about during the transition from Xfree86 to X.org (if memory serves). Now though the landscape is different, Linux is actually accepted as a "desktop" OS, its not just the geeky kids play toy on his 486/586/Pentium or heaven forbid at the time AMD K6.

But now the same competition (without the licencing crap) that made X.org a success is deemed "evil", "copying", "duplicating". So yeah when people refer to Mir as being a clone or copy of Wayland, plus that Mir has no place, I think back and I get a little pissed that people forgot exactly what X.org is, It's a "Fork" of Xfree86 at its base. Those deeming a new project as wasting time because they should have "just" went with Wayland. If X.org went the same way at the start we wouldn't be where we are, I doubt we would even be having this discussion. People tend to forget that new projects and even forks can have a massively good effect on the overall outcome.

Sorry for the rant and the history lesson >.>. I hope people remember when they look at Wayland that it is a strategy born from a fork, give Mir a chance and see if it is as capable as the old X.org was, Mir is not a fork, but it deserves the same right that we gave X.org way back when. It deserves the chance to prove itself without the roadblocks and back and forth arguing.

Anyways enough of me going on (sorry again for the essay).

TLDR: Give Mir a chance to change things, like we did with X.org in the past even if the only affected landscape is that of Ubuntu. It means a win for all of us in the end.

---

### Post by Kevin_Arnold on 2013-09-09
> **ZoiaGuyver said:**
> 
TLDR: Give Mir a chance to change things, like we did with X.org in the past even if the only affected landscape is that of Ubuntu. It means a win for all of us in the end.

Agreed. The Canonical bashing is as boring as the Microsoft bashing. People need to be more open to change, if Mir sucks it will fail all on it's own. I honestly don't understand the dogpiling that happens in tech circles.

---

### Post by codingman on 2013-09-09
Have you ever heard of something called too much change? Maybe Mir falls into this range.

Hey! That rhymed!

---

### Post by Yougo on 2013-09-10
From what I understand, the way Mir works is actually closer to X11/X.org than what Wayland does. If only a teensy bit.

both are closer to each other than either are to X11/X.org.

---

### Post by ZoiaGuyver on 2013-09-10
**Warning this is definatly an essay, bad spelling, grammar and all sorts, I haven't written like this in years**

There is no such thing as "too much change". Our lives change every day. Our decisions and path changes every day, Our uses of technology changes every day, the list goes on..

Plus the "too much change" doesn't really hold any water, every upstream project changes daily, it gains or loses something every day. If it didn't then the project would be stagnant and probably dead. 

Basically everything changes every day, no matter what, you can't stop it, you can only help to influence the way it goes for yourself by your decisions and acts. Also if you look at some things having a majority, leads to tyrants. A good quote is "Power corrupts; absolute power corrupts absolutely". The "power" some companies have over the open source scene is shown in the current argument "The Management" decided the course of action. 

You could say the same for Mr Shuttleworth and Ubuntu, at some points but there is a difference, Mr Shuttleworth has a vision of what he wants Ubuntu to do as a whole. He is willing to take the burden for that vision, be it good or bad. He is a single point in the community to blame, and takes most of the blame even for things that are not in his control. If we have the same "vision" then great we all get along in our happy little worlds. If however we dont get along, cannot agree or are a risk to the overall vision then Mr Shuttleworth makes the last call. This to my knowledge has happened very few times in Ubuntu (the main ones that get brought up are the decision on Unity and Upstart, both of which I actually agree with).

The thing is all of us whether we be on Ubuntu, Arch, Fedora, OpenSuse, Gentoo or any number of the other distros out there have always given eachother choices, We have the choice to use RPM/Deb, binary/source. We have a pick in every choice we make for the systems we run even down to the "kernel" we choose, the very heart of the OS. Yet X.org and Wayland has to be the only choice in the display server. It's the one place where there is no choice at the moment, would be no choice in the future (if Intel/Redhat and the rest had their way). The Proprietary driver issue is actually a good, valid and technical argument as to why one soloution would be good, but then theres also another problem.. They write drivers for Windows, Mac OS-X, BSD, Linux and Unix and thats only the OS list thats not talking about the architectures. They reuse segments of code on each of those platforms and have been for many years. So why wouldn't they just enable support for the most used Linux Desktop?

So if you want to look at "fragmentation" like Mir has been accused of, the whole Operating System world.. actually the whole IT industry is nothing but fragmentation, they are less viewable to the people who buy the "phone" or "PC" but the fragmentation is still there. The reason there is less viewable to the outside is all those are pretty much proprietary solutions that battle it out with patents and copyrights. For decades Apple and Microsoft have battled it out over differing concepts, now Apple Macs run Windows on Intel hardware. The outside is different but the internals of the system are like any other x86/x86_64 architecture.  

I agree in the sense that linux needs to have a set standard for doing things, in a sense it already has, LSB and SDL. But that standard cannot and should not ever come at the cost of competition and openness, the standards should be agreed on by all involved. It should have neither a protocol or an implementation, the standard should be agnostic in every sense (this is looking at it from an ABI perspective). LSB/SDL are both agnostic as far as what they run on or use (although the specification does suggest RPM as the "standard" (hello again Redhat) and has been fought by Debian and others over the years). Both of them though can give a rough "guideline", its down to the distrobutions to decide outside of that, be they community or commercial distros.

Tbh what RPM says it is about is another great goal. 

" After a long development break rpm.org was relaunched 2007 with the goal to reclaim the position as upstream home of RPM. As a first step patches that had piled up in the different distributions have been integrated into the code base as far as possible. **We want RPM not be the province of one company, or a small set of developers. It needs to be developed in an open community, consumed and contributed to by many companies, users, distributions, and developers. We therefore welcome any and all contributors.**

We are currently trying to catch up the lack of maintenance of the last years and start addressing the new problems and needs that have developed over time. "

The intention of RPM was to make a totally open standard, yet now imo it is locked down and is slowly becoming irrelavant, or maybe irrelavant is the wrong word for what its becoming. It's becoming less and less of a focus, with Pacman, Dpkg, Portage and others or varients of them.

I know I have gone off a bit on a tangent here, but what I'm trying to make the point of, is even at the very core of "Open Source" software there is still choice, fragmentation, politics, bs, fud and whatever else you want to add. But none of those are about a "single" project. They are about the differences between them, the whole point of the open source community the very heart that drives it are the users, but sometimes the users can be a little blind, short sighted or whatever else. This is where as users we need companies and people to make a decision and burden the blame, but the decision has to be made. 

Being Impartial is something I don't believe Redhat/Intel or others have proven in the past, Redhat were implementing and using Upstart from Fedora 9 > 14, like Ubuntu. Yet systemd was created by two Redhat devs, guess what gets chosen as the "must" have default. Even though the projects were a long way apart, Upstart in 2006 and systemd in 2010. 

Upstart was created by Canonical and Google devs, its still being used in Ubuntu, Chrome and Chrome OS plus a few others. The choice even at that level is there, systemd, Upstart, OpenRC plus others. 

Now the argument will probably be "but Canonical is evil like Google, Apple and MS, they give nothing back to the community!". Now everyone in their right mind knows that FUD... Canonical and Google do a hell of a lot for the "Open Source" community outside of their software. Look at the events that are sponsored, the code that is GPL licenced. 

Now I know there is argument for how Canonical have acted, Admitted the whole Amazon thing rubbed a lot the wrong way, which was right, people were offended, but then again we put up with adverts in almost every other part of out daily life. Weve got good at ignoring them, why is this any different? Oh right, because a company (Canonical) agreed with another company (Amazon)to use their system for a bit of advertising. Now admitted in my personal opinion that was a really bad move.. there are plenty around better than Amazon, but having said that there are also plenty worse. They also gave us a way to totally disable it and remove the components, I agree with some that it shouldn't of been there at the start. But then Canonical doesn't have an "Enterprise" branch of the OS to make money off of while advertising what they want. Ubuntu is in both areas, the home desktop and the workplace, Its not seperated like RHEL/Fedora or SLED/OpenSuse. 

Look at whats happened in the past, for years most hadn't even heard of linux (unless they were in the IT trade), they didn't know anything bar Windows and Mac existed. It even led to the term "PC" being coined as a Microsoft Windows only thing!, (we allowed that to happen) Ubuntu was released with a lot of hype and fanfare, marketing and charisma, something the Linux Desktop hadn't had before (and hasn't since since from any company outside of Canonical). 

We all came to ubuntu with a passion to drive it to be the best it could be, we weren't thinking of Redhat, Suse or any other distro.. we were totally passionate about Ubuntu. Over time that wore off, people went their own ways, made new choices, headed to greener pastures, yet Ubuntu was still thriving. Then Unity hit, a lot were appauled they left Ubuntu while cussing and cursing all at Canonical for their huge "Betrayal to Ubuntus ideas". Unity began to mature while still being bashed over the head by some. Unity becomes actually usable (wtf!) its actually really smooth!, this isn't to bad after all, people start to come back, slowly admittedly but still. Then comes Mir.. this crap really hits the fan now, people begin blaming Canonical for everything that has gone wrong, will go wrong with the "Open Source" community, while having never actually tried it or even given it a chance. 

OMG CANONICAL STABBED WAYLAND IN THE BACK!!. yet the wayland devs said canonical didn't put anything in anyways so by that admission how can Canonical be stabbing them in the back for going out on their own? Canonical doesn't put patches upstream! (although when they do they are "reverted" due to management which is the latest example, or if they actually are the upstream Upstart they get dropped for no real reason). Canonical don't give to the community!! yet they gave us Upstart which for four years looked to be replacing sysv only to be dropped for a Redhat alternative (atleast in some distros). 

I think i'll leave it there this is getting rather long.. I hope it is an enjoyable read for someone. 

P.S Im not a Canonical/Ubuntu fanboy, I do use Ubuntu aswell as Gentoo, Funtoo and Pentoo.

TLDR: Blurb and lots of it.. Don't bash things just to be a lemming, Study them, come to your own conclusions, have a reason and convey your thoughts, don't use FUD, use facts in a discussion and work for change, strong arguments can change peoples minds if they have facts to back them up. Openness and Competition are GOOD!

---

### Post by mikewhatever on 2013-09-10
> **codingman said:**
> Have you ever heard of something called too much change? Maybe Mir falls into this range.

Hey! That rhymed!

I like the way Carl Richel, the CEO if System76 put it:
[http://www.tuicool.com/articles/fEfqIf](http://www.tuicool.com/articles/fEfqIf)
> It's hard for me to criticise anyone for creating something to fit their needs. System76 does it all the time. I expect any smart company to do the same.

---

### Post by santosh83 on 2013-09-10
> **ZoiaGuyver said:**
> 
buzzingbot, that comment you quote, was more that Wayland seems to not want any competition at all. There has been a lot of debate back and forth, with crap in both directions. As an end user your right it has no affect at all, or atleast the end-user should not notice any change. Thats the only consistent thing between both projects.

There's the case where hardware manufacturers develop drivers for Wayland but don't develop for Mir...
There's the case where projects like KDE, GNOME, XFCE, LXDE etc. port to Wayland but don't port to Mir...

Both could possibly be overcome by Canonical doing all the work themselves, but it will become increasingly difficult. At the end of the day if Canonical decide to stop maintaining patches for GNOME, KDE, LXDE, XFCE etc., then they will become a Unity-only distro, affecting massive amounts of end-users.

If Canonical also fail to maintain patches for graphics and kernel drivers then the performance of Mir will be seriously affected, again impacting all end-users.


> But now the same competition (without the licencing crap) that made X.org a success is deemed "evil", "copying", "duplicating". So yeah when people refer to Mir as being a clone or copy of Wayland, plus that Mir has no place, I think back and I get a little pissed that people forgot exactly what X.org is, It's a "Fork" of Xfree86 at its base. Those deeming a new project as wasting time because they should have "just" went with Wayland. If X.org went the same way at the start we wouldn't be where we are, I doubt we would even be having this discussion. People tend to forget that new projects and even forks can have a massively good effect on the overall outcome.

I think the issue here is how the rest of the FOSS world see the decisions behind Canonical to fork away (even if not literally forking Wayland's code, then moving away so to speak.)

The Xfree86 fork was seen to be in the larger interests of the community and hence the community supported. Mir is seen (rightly or wrongly) as being a fork solely benefiting Canonical and harming the larger interests of the community, and this I believe is the main reason for the antagonism. Strong factors also are how Canonical were very secretive about Mir all these years, and those incorrect technical statements about Wayland given, which were later retracted, but the damage to community goodwill was done.

However in essense you're right. Canonical have the right to develop Mir and the right to be uncooperative with the community if they want, and the community should spend its efforts focusing more on Wayland and less on bashing Canonical. This way we'll have two good products being developed. And ultimately they'll stand or fall in time based on how much support they get from hardware and software developers.

---

### Post by ZoiaGuyver on 2013-09-10
First let me get one point out of the way, Xfree86 wasn't forked because it was seen to be in the larger interest for the community, X.org sat dormant for a good while before anything started to appear on it. It was almost 4 years before Xfree86 died out (although I think some of the older Xquartz stuff is still based on it). It died because of the developers leaving to form X.org, or well actually I should rephrase that, It committed suicide by first changing the licensing to something that was incompatible with GPL and then the people overseeing it leaving to join X.org. 

Nvidia has already stated they have no plans to support Wayland. AMD are more quiet, they don't say anything. But I did post a bit on G+ about that when someone said about it.

Now the next bit you can call FUD, optimistic or whatever you want but spend a little time thinking about it.

Valve's Steam have chosen Ubuntu as the distro they support for gaming (though it does work on other distros), Valve has a lot more sway with any of the hardware manufacturers that actually make performance cards than anyone else in the community. Now look at this from a business perspective like Valve has done, Ubuntu release Mir, Mir is okish at the start (not the disaster unity was) but it does progress nicely for a few months in 13.10 on the desktop/laptop and phone. But it has no support for binary drivers, the ABI is created and stable but NVidia and AMD have not released anything, also on the horizon is Wayland the "community" choice. Now here's a problem, do you go to AMD and Nvidia and ask to support one display manager thats used in one distro with their proprietary drivers with the intent of Gaming, also explaining that the community choice wont be impacted as Wayland has full support from open source drivers. 

Or do you go to them and try to make the argument that Wayland has a larger following, but is split across 100s of distros with Upstream support of Redhat and Intel developers, also pointing out that Wayland is the display manager for Tizen and various other projects. It also has a stable ABI and API was created by the same people who created and then forked Xfree86 and has been working on Wayland. It is also supported by the open source toolkits.

If it were to happen as a business you would choose the one with the backing of your potential market. AMD are going into ARM and x86, Nvidia has Tegra.. Plus my guess would be there are not massive differences between Mir and Surfaceflinger being as Mir can use Android drivers (afaik)

Now that is a bit of a weird argument I know and I have already stated that as BS, I hope it wont happen, everybody else should hope that as well.

---

### Post by santosh83 on 2013-09-10
> **ZoiaGuyver said:**
> 
Nvidia has already stated they have no plans to support Wayland. AMD are more quiet, they don't say anything. But I did post a bit on G+ about that when someone said about it.

Did NVidia categorically state they have no plans to support Wayland? I didn't come across any such news. That's surprising and disappointing to say the least!

> 
Now that is a bit of a weird argument I know and I have already stated that as BS, I hope it wont happen, everybody else should hope that as well.
[/QUOTE]

I agree that interesting times lie ahead for graphics on Linux. One hopes both Wayland and Mir can thrive side by side, both with full support and backing of the hardware guys, but it may be bit too optimistic. Time will tell in any case. There's no point in blaming anyone anymore as each side have staked their positions, and we simply have to wait and see.

---

### Post by Yougo on 2013-09-10
^ when a company says "we have no plans for that", they mean just that.  it doesn't mean "we have plans to not do that". it doesn't mean there weren't plans, it doesn't mean there won't be plans in the future.

they just don't want to commit to any statement one way or the other.

---

### Post by ZoiaGuyver on 2013-09-10
Well tbh the comment was made a long time ago, 2010 I think. As we all know plans change, no one can see what the future holds. 

I agree with you santosh83, I really hope for proprietary support for both display managers, from both the vendors. This will make things better for everyone.

The last post made by anyone at NV was this [Wayland with NVidia Drivers]("https://devtalk.nvidia.com/default/topic/539833/linux/wayland-with-nvidia-drivers/2/"). Being that NVidia are known for their NDAs and planning well in advance, plus the fact that they don't actually contribute anything to linux bar the binary blob (atleast in public), could be good for both projects.

---

### Post by John_McCourt on 2013-09-10
The fundamental problem with Linux. Too many cooks, too many egos. Intel have better things to be doing with their time than supporting desktop Linux. They should be supporting severs, but not desktops.

---

### Post by Yougo on 2013-09-10
^how big is the graphics card market for servers?
what runs on servers?

---

### Post by buzzingrobot on 2013-09-10
> **santosh83 said:**
> ... Canonical have the right to develop Mir and the right to be uncooperative with the community if they want, and the community should spend its efforts focusing more on Wayland and less on bashing Canonical. This way we'll have two good products being developed. And ultimately they'll stand or fall in time based on how much support they get from hardware and software developers.

Who decides all these things? No one asked me.

What, exactly, is "the community"?  We talk about it all the time.  Who's in and who's out?  Who decides who's in and who's out?  

Seems to me that the "community" stick is what's waved around every time someone does something that offends some number of developers. Many times, offense is taken for reasons that have little or nothing to do with making software for users, but simply because someone has violated the assumed but unwritten and unspecified cultural norms of some people. 

I've used Linux for almost 20 years and this kind of infighting has always existed.  It's as useless today as ever.

---

### Post by Yougo on 2013-09-10
^in this case, I suspect 'community' means 'anyone not on Canonical payroll'. it doesn't specify if these people are devs, users, or random people who care.

/edit:
At least, I suppose some emotional involvement should be present, right?

---

### Post by buzzingrobot on 2013-09-10
> **Yougo said:**
> ^in this case, I suspect 'community' means 'anyone not on Canonical payroll'. it doesn't specify if these people are devs, users, or random people who care.

/edit:
At least, I suppose some emotional involvement should be present, right?

Actually, I'd amend that to 'anyone I don't agree with'. ;)

---

### Post by ZoiaGuyver on 2013-09-10
buzzingrobot I totally agree there, the infighting has and I think always will be part of the linux ecosystem, the same infighting and differences though are also what can drive huge changes, so at times it does have it's advantages. 

The part of the argument I don't really get, if people hate Canonical and Ubuntu so much for betraying, backstabbing and whatever else they accuse them of, why do they still show any interest in the "walled garden" they suggest Ubuntu is becoming?

 I guess human nature speaks for itself, society has to have a "bad guy" for everything that goes wrong, it means then the blame isn't on them.

---

### Post by buzzingrobot on 2013-09-10
> **ZoiaGuyver said:**
> buzzingrobot I totally agree there, the infighting has and I think always will be part of the linux ecosystem, the same infighting and differences though are also what can drive huge changes, so at times it does have it's advantages. 

The part of the argument I don't really get, if people hate Canonical and Ubuntu so much for betraying, backstabbing and whatever else they accuse them of, why do they still show any interest in the "walled garden" they suggest Ubuntu is becoming?

 I guess human nature speaks for itself, society has to have a "bad guy" for everything that goes wrong, it means then the blame isn't on them.

In part, at least, I think it is fueled by the Linux media and bloggers, who like to frame things as contests, combats, and winner-take-all scenarios. I can't count how many times I've seen headlines like this: 5 Ways Debian Is the Best Linux, or, Ubuntu versus Mint:  Who Wins?, or  8 Ways KDE/Gnome/Unity/XFCE Is All You Need.  The content is almost entirely subjective, and often revolves around trivial things like theming and default configurations.  Linux media people speculate about Canonical plans without a shred of evidence. On and on.

There's lots of room here. Success for A does not mean failure for B.

---

### Post by santosh83 on 2013-09-10
On this thread's topic, recently read on slashdot about Intel and Redhat intensifying efforts to bring full Wayland support to GNOME, with a view to bringing a "tech preview" in Fedora 20 and full inclusion in later releases. Read the details here:

[http://www.muktware.com/5872/intel-red-hat-working-enabling-wayland-support-gnome](http://www.muktware.com/5872/intel-red-hat-working-enabling-wayland-support-gnome)
[http://blogs.gnome.org/uraeus/2013/09/09/fedora-wayland-update/](http://blogs.gnome.org/uraeus/2013/09/09/fedora-wayland-update/)

---

### Post by montag dp on 2013-09-10
Just curious, but considering that the reasons Canonical initially provided for developing their own display server were not sound, have they since then given a good reason for it?  Seems like it is just not-invented-here syndrome.  As long as it doesn't make video hardware support worse in Linux, I'm fine with it, but I'm not sure that's a given.

---

### Post by buzzingrobot on 2013-09-10
> **montag dp said:**
> Just curious, but considering that the reasons Canonical initially provided for developing their own display server were not sound, have they since then given a good reason for it?  Seems like it is just not-invented-here syndrome.  As long as it doesn't make video hardware support worse in Linux, I'm fine with it, but I'm not sure that's a given.

You'll need to substantiate that "reasons... were not sound" assertion.

But, would you make your company's future dependent on a product you cannot control?  Sure, Mir is in-house, and there are very good reasons it.

Among other things, Canonical needs to be able to sign contracts that say X will be delivered on Y.  They cannot do that if X depends on code written and mainiained by some amorphous mass of FOSS developers who work to their own schedule and interests. And, that includes some who would screw Canonical just for jollies.

Mir doesn't stand a chance of making video support "worse in Linux".  If it doesn't work, Canonical will be stuck with it; no one else will use it.  if it is demonstrably better than  X or Wayland, people who care about performance more than NIH syndrome will use it.

---

### Post by codingman on 2013-09-10
Just because things change doesn't mean that it is necessarily good.

---

### Post by ZoiaGuyver on 2013-09-10
Well there are a few technical differences between the two. Mir from the start was built with "convergence" in mind, Wayland wasn't (although it can support it), Wayland after all is the protocol, not the the implementation (that is left to Gnome or KDE, user choice..). The problem is that both of them technical parts aside, do the same thing in different ways as a default. They both use the OpenGL/ES, DRI and KMS (Which Wayland is being credited for even though most was long before Wayland, Some is even the work of Xfree86, some argue as Wayland is by the same people it should have the same credits, but that's a whole different argument). 

A lot of this brings back memories of the current init situation in a lot of ways, but the rolls are reversed. Canonical/Google made a great replacement for sysvinit, it was worked on continuously (even now it is still going, but people will tell you its dead or failed as it is only used in Ubuntu, Chrome and Chrome OS) it is called Upstart and started in 2006. It ties to a lot of other components like Plymouth and X (soon to be mir) but its aim is more "desktop" orientated than server (pretty boot screens, non-switching) This continued until 2010 when two Redhat devs announced systemd, which was immediately accepted as the "de facto" standard for the sysvinit replacement even though the remedy only supports Linux whereas Upstart supports Linux and BSD, dropping Upstart and Canonical/Googles work. They also included another problem systemd is packaged with files to increase its performance as standard (some rsyslog stuff), but Upstart not being an "upstream" blessed project any more does not have the files it needs packaged as standard in anything but Ubuntu and Googles Chrome OS. So in conclusion systemd on the face of it seemed faster and cleaner, although it is not "event driven". There was an amazing explanation about this at this link [eli5_the_systemd_vs_initupstart_controversy]("http://www.reddit.com/r/linux/comments/132gle/eli5_the_systemd_vs_initupstart_controversy/")

I know this is not current, but I do feel it is actually quite pertinent to the discussion, this shows that forcing people into only one supported project is not a new thing with linux, it also shows that Redhat and others are willing to turn what was accepted as the "community" solution for more than 4 years on its head and go off to duplicate the effort when it benefits them and their hold on Linux. 

Both parties are not justified in this argument, but it has became another battle for Ubuntu against the two "big dogs" as it were in Linux, Intel/Redhat. The more they control the less likely it will become for linux to ever take a hold on the "desktop" market, hell they been at it for as long as X has been, they have had over 26 years to give the desktop an open source OS, up to now they have either failed or are not interested in the desktop linux market. Intel is definitely not interested in the desktop market they have Microsoft Windows (You know the thing that was such a big failure, but still holds the majority of desktops).

Now look at what happened after Ubuntu came about, a project that actually cares about Linux on a desktop as well as the other platforms and areas. It had and still has massive support from users (yes us guys here discussing this from Ubuntu machines) and companies inside and outside of the Linux/Open Source market. Canonical its investor which includes the "NIH SABDFL" everyone seems to love to hate Mr Shuttleworth, who has a direction he wants to take with Ubuntu. 

Whether we all agree or disagree with the crap going around at the moment, Ubuntu even with all the changes, the mud flinging exercises and the FUD (The comments on the first announce of Mir) from both Canonical and outside projects. I do still feel that at the base of it is a leadership and community that still wants the best "Linux based Desktop distribution" around. That it wants to improve things for everyone not just Ubuntu, but it is a rather large goal..

Since 2004 when Ubuntu was released in a lot of the "end-users" cases Ubuntu has became synonymous with Linux (this is not the right thing, but neither is games or hardware manufactures calling a Windows PC just PC.. especially considering the actual PC runs a lot more than Windows). For tech savvy yeah we know the difference, for them well they need a little education on the subject.

Some of the younger users probably had the first taste of linux on Ubuntu. Then maybe they went on to bigger and better things, maybe they went to where the grass was greener, maybe they stuck around with Ubuntu and now are classed as OAPs (Like me >.> or at least that's how it feels lol). Whichever choice they made it was theirs and I hope them all the best.

And I'm doing it again.. on a reminiscing trip to who knows where. Sorry.

---

### Post by JDShu on 2013-09-10
I'm going to stop quoting and commenting on every point that people make because... well it's too much work :)

> **ZoiaGuyver said:**
> Well there are a few technical differences between the two. Mir from the start was built with "convergence" in mind, Wayland wasn't (although it can support it), Wayland after all is the protocol, not the the implementation (that is left to Gnome or KDE, user choice..). The problem is that both of them technical parts aside, do the same thing in different ways as a default. They both use the OpenGL/ES, DRI and KMS (Which Wayland is being credited for even though most was long before Wayland, Some is even the work of Xfree86, some argue as Wayland is by the same people it should have the same credits, but that's a whole different argument). 

A lot of this brings back memories of the current init situation in a lot of ways, but the rolls are reversed. Canonical/Google made a great replacement for sysvinit, it was worked on continuously (even now it is still going, but people will tell you its dead or failed as it is only used in Ubuntu, Chrome and Chrome OS) it is called Upstart and started in 2006. It ties to a lot of other components like Plymouth and X (soon to be mir) but its aim is more "desktop" orientated than server (pretty boot screens, non-switching) This continued until 2010 when two Redhat devs announced systemd, which was immediately accepted as the "de facto" standard for the sysvinit replacement even though the remedy only supports Linux whereas Upstart supports Linux and BSD, dropping Upstart and Canonical/Googles work. They also included another problem systemd is packaged with files to increase its performance as standard (some rsyslog stuff), but Upstart not being an "upstream" blessed project any more does not have the files it needs packaged as standard in anything but Ubuntu and Googles Chrome OS. So in conclusion systemd on the face of it seemed faster and cleaner, although it is not "event driven". There was an amazing explanation about this at this link [eli5_the_systemd_vs_initupstart_controversy]("http://www.reddit.com/r/linux/comments/132gle/eli5_the_systemd_vs_initupstart_controversy/")

I know this is not current, but I do feel it is actually quite pertinent to the discussion, this shows that forcing people into only one supported project is not a new thing with linux, it also shows that Redhat and others are willing to turn what was accepted as the "community" solution for more than 4 years on its head and go off to duplicate the effort when it benefits them and their hold on Linux. 


So the obvious problem with this comparison is that systemd and upstart have fundamentally different architectures, and there are technical reasons for why distribution developer prefer systemd. Note that fedora actually used upstart for a while before systemd existed. Contrast to Mir and Wayland where the only reason for Mir to exist is so that Canonical will have a modern display server under it's control without needing to work together with the Wayland community.

> 
Now look at what happened after Ubuntu came about, a project that actually cares about Linux on a desktop as well as the other platforms and areas. It had and still has massive support from users (yes us guys here discussing this from Ubuntu machines) and companies inside and outside of the Linux/Open Source market. Canonical its investor which includes the "NIH SABDFL" everyone seems to love to hate Mr Shuttleworth, who has a direction he wants to take with Ubuntu. 


This seems plain disrespectful of almost every other Linux distribution. You think they don't care about Linux on the desktop? And perhaps Shuttleworth earned the hatred - when such a large communityof people have decided that they don't like a person, maybe there is a reason?

---

### Post by buzzingrobot on 2013-09-10
> **JDShu said:**
> 


...perhaps Shuttleworth earned the hatred - when such a large communityof people have decided that they don't like a person, maybe there is a reason?


That, frankly, is an outlandish statement.  How many people in this so-called community have even met the man? What right do they, or any of us, have to cast judgement?

Working up that depth of emotion, any emotion, over software -- software they receive as a gift -- is a sign of a life out of whack.

---

### Post by montag dp on 2013-09-10
> **buzzingrobot said:**
> You'll need to substantiate that "reasons... were not sound" assertion.

I was referring to the false claims they made about Wayland.

> **buzzingrobot said:**
> But, would you make your company's future dependent on a product you cannot control?  Sure, Mir is in-house, and there are very good reasons it.

Among other things, Canonical needs to be able to sign contracts that say X will be delivered on Y.  They cannot do that if X depends on code written and mainiained by some amorphous mass of FOSS developers who work to their own schedule and interests. And, that includes some who would screw Canonical just for jollies.I get that developing things in-house, even if an alternative already exists, can be beneficial sometimes.  My question is, why do they need to develop their own display server?  They're not developing their own kernel, right?  So why is it so important to have their own display server, specifically?  I think this is a valid question and I haven't seen it addressed by Canonical.  If the concern is that Wayland development is too slow, why did they decide to start from scratch with their own instead of contributing to the project they originally agreed to support?

> **buzzingrobot said:**
> Mir doesn't stand a chance of making video support "worse in Linux".  If it doesn't work, Canonical will be stuck with it; no one else will use it.  if it is demonstrably better than  X or Wayland, people who care about performance more than NIH syndrome will use it.I don't agree with this.  What if company A decides to develop drivers for Wayland only, and company B decides to develop drivers for Mir only (which is quite possible if both Mir and Wayland end up performing on par and there is no clear "winner")?  Suddenly those who own hardware from those companies have had their ability to choose a distro severely limited.

---

### Post by buzzingrobot on 2013-09-10
> **montag dp said:**
> I was referring to the false claims they made about Wayland.

I get that developing things in-house, even if an alternative already exists, can be beneficial sometimes.  My question is, why do they need to develop their own display server?  They're not developing their own kernel, right?  So why is it so important to have their own display server, specifically?  I think this is a valid question and I haven't seen it addressed by Canonical.  If the concern is that Wayland development is too slow, why did they decide to start from scratch with their own instead of contributing more to the project they originally agreed to support?

I don't agree with this.  What if company A decides to develop drivers for Wayland only, and company B decides to develop drivers for Mir only?  Suddenly those who own hardware from those companies have had their ability to choose a distro severely limited.

They maintain their own kernels.  

It isn't that in-house development is "beneficial".  It's that you can't do business if you can't meet schedule commitments made to customers.  That's tough enough with your own developers, almost impossible if you are dependent on "community" developers who are indifferent, if not hostile, to your business needs.

Company A and Company B cannot go back in time to eliminate the drivers already in use. So, no one loses any choice.  Besides, they give the stuff away.  We don't pay for it.  They have no obligation to us at all.

---

### Post by JDShu on 2013-09-10
> **buzzingrobot said:**
> That, frankly, is an outlandish statement.  How many people in this so-called community have even met the man? What right do they, or any of us, have to cast judgement?


So are we not allowed to cast judgement on anybody? I (even more frankly) disagree.  Everybody is allowed to have an opinion. And to clarify, I am assuming  you mean casting judgement as in deciding to dislike him.

> 
Working up that depth of emotion, any emotion, over software -- software they receive as a gift -- is a sign of a life out of whack.

I also do not see the software as a gift. I don't think Mark Shuttleworth does either. Telling me to be grateful for it is demeaning to me. And why can't I have emotions over it anyway? There are people' who's lives are heavily impacted, in both good and bad ways, by various software.

---

### Post by ZoiaGuyver on 2013-09-10
Perhaps he did, perhaps he didn't

The argument for systemd may be fair it does on the face of it looks better. But what do actual distros think?

Fuduntu devs didnt like it [systemd-new-pulseaudio]("http://www.linuxadvocates.com/2013/04/systemd-new-pulseaudio.html")

"Systemd, whether by design, or circumstance, is largely becoming non-optional. Inclusion of core technologies such as dbus and udev are reducing choice for linux users and developers, rather than expanding them--which is the very antithesis of the idea of Free/Open Source software." -Shawn W Dunn 

"ConsoleKit + UDev + Syslog + DBus + Polkit + Sysinit + this + that. RedHat Enterprise Systemd is the best product we've ever been force fed.  We are facing being forced to integrate it at Fuduntu because it's replacing so many core tools now that it's impossible to continue the project without it. Those "idiots" that don't like binary logs aren't "idiots", some of us actually have some idea of what we are talking about, but what do I know..&#65279;" -Andrew Wyatt Founder of Fuduntu

Ofcourse this is the "communities" choice these things aren't being forced on anyone by making it a core component that is depended on by other important parts.. The same is happening now with Wayland.. people are being force fed it they don't have a choice but to use it as everything is reliant on it. It's basically a "You will use this, or nothing at all" scenario. If I wanted to stay in that environment why would I move away from Windows/Mac OS-X?

Now Ubuntu could be seen the same way, people could say we were force fed Unity, Upstart but there is a difference, even outside of the fact that we can choose to replace those parts freely if we want to. There was one man at the beginning of this that funded the whole thing, there still is one man with the help of a business still funding all this. Every distro has a community that because of Redhat and others have no choice in what they use.

Can you name any other distribution that aims at the desktop market through ease of use, compatibility, software? OpenSuse is maybe the only other contender for it, and while OpenSuse is a great linux distro it also has a lot of issues to contend with within the general community.

I dont see how Shuttleworth has earned any more hatred than the likes of Intel or Redhat over the years. [Red+Hat,Ubuntu Trends]("http://www.google.com/trends/explore#q=Red+Hat,Ubuntu")

But hey when such a large community like the person or the distribution, maybe there is a reason.

---

### Post by montag dp on 2013-09-10
> **buzzingrobot said:**
> They maintain their own kernels.  

It isn't that in-house development is "beneficial".  It's that you can't do business if you can't meet schedule commitments made to customers.  That's tough enough with your own developers, almost impossible if you are dependent on "community" developers who are indifferent, if not hostile, to your business needs.Canonical has themselves to thank for any hostility of the Wayland developers towards them.  That would have been different if Canonical hadn't gone back on their word and developed Mir secretly, so I don't see it as a good reason to develop Mir in-house.

> **buzzingrobot said:**
> Company A and Company B cannot go back in time to eliminate the drivers already in use. So, no one loses any choice.  If they want to use a modern display server they do.  Particularly if X eventually stops being supported by the distro maintainers.

 > **buzzingrobot said:**
> Besides, they give the stuff away.  We don't pay for it.  They have no obligation to us at all.

I don't see how that is relevant to this discussion.

---

### Post by cariboo on 2013-09-11
I personally think that Intel is shooting themselves in the foot. I've seen figures stating that there are about 70 million users of Linux based distributions, and Canonical claims there are about 20 million Ubuntu users, to me that looks like close to 1/3 of all Linux distribution users, use Ubuntu. I'm planning on building a new system in the new year, and this unsubstantiated silliness just pushed me away from even considering Intel products for my next build. 

I'll put up with a cpu that is a few percentage points slower than the current Intel offerings, I"ve never had any really good experience with Intel products so for me it really isn't that hard a decision to make.

I'm not going to argue the merits of either graphics rendering system, as there aren't any released versions of any distribution that use wayland or mir at this time. I've played with both, and neither seems to be better or worse than the other.

Maybe it's time to create a poll with the pre-requisite that if you vote, you have to provide proof that you are actually using one or the other.

---

### Post by santosh83 on 2013-09-11
> **ZoiaGuyver said:**
> 
A lot of this brings back memories of the current init situation in a lot of ways, but the rolls are reversed. Canonical/Google made a great replacement for sysvinit, it was worked on continuously (even now it is still going, but people will tell you its dead or failed as it is only used in Ubuntu, Chrome and Chrome OS) it is called Upstart and started in 2006. It ties to a lot of other components like Plymouth and X (soon to be mir) but its aim is more "desktop" orientated than server (pretty boot screens, non-switching) This continued until 2010 when two Redhat devs announced systemd, which was immediately accepted as the "de facto" standard for the sysvinit replacement even though the remedy only supports Linux whereas Upstart supports Linux and BSD, dropping Upstart and Canonical/Googles work.

I'm just speculating here, but could this (i.e., the larger community dropping Upstart to favour systemd) have anything at all to do with licensing. I know Upstart is also GPL just like systemd, but does contributing to it have any requirement for signing copyright assignment agreements or something like that? I understand that's the case for contributing to Mir.

> 
Both parties are not justified in this argument, but it has became another battle for Ubuntu against the two "big dogs" as it were in Linux, Intel/Redhat. The more they control the less likely it will become for linux to ever take a hold on the "desktop" market, [...]

Now look at what happened after Ubuntu came about, a project that actually cares about Linux on a desktop as well as the other platforms and areas.

The thing though is Canonical seems to be increasingly preoccupied with mobile systems, as they seem to be convinced that's where they can find any commercial success if at all. Desktops are being treated as second class citizens everywhere these days. :-(

As always hardware innovations and consumer reception will always drive the software by and large, as seen by the big shift from Workstations to PC form factors, then now the shift towards mobile. Redhat and Canonical both are profit driven (even if nominally) companies so they need to sell something somewhere. For Redhat it has long been enterprise support, and Canonical is now foraying into both mobile as well as enterprise support. The desktop code base will only be maintained by both as a sort of common launching point for their tailored solutions, and we have to live with that.

---

### Post by santosh83 on 2013-09-11
> **buzzingrobot said:**
> They maintain their own kernels.  
It isn't that in-house development is "beneficial".  It's that you can't do business if you can't meet schedule commitments made to customers.  That's tough enough with your own developers, almost impossible if you are dependent on "community" developers who are indifferent, if not hostile, to your business needs.


Just wondering how Redhat meet these commitments then. Everyone seems to uphold Redhat as a model for contributing to upstream and working with the community, so how so they manage to do both that, and meeting commercial schedules?

---

### Post by buzzingrobot on 2013-09-11
> **JDShu said:**
> So are we not allowed to cast judgement on anybody? I (even more frankly) disagree.  Everybody is allowed to have an opinion. And to clarify, I am assuming  you mean casting judgement as in deciding to dislike him.



I also do not see the software as a gift. I don't think Mark Shuttleworth does either. Telling me to be grateful for it is demeaning to me. And why can't I have emotions over it anyway? There are people' who's lives are heavily impacted, in both good and bad ways, by various software.



There's a real and important difference between not liking a policy Canonical has decided to follow versus declaring your hatred for someone just because he has a lead role in shaping tha policy.

If you receive something at no charge from someone, that's commonly called a "gift". 

You can be as emotional as you wish.  Publicly declaring your hatred for Shuttleworth because you don't agree with all his business decisions seems over the top and rather difficult to justify.

The world is afflicted with any number of unfortunate things that merit your hatred.  People running software companies aren't on that list.

---

### Post by buzzingrobot on 2013-09-11
> **santosh83 said:**
> Just wondering how Redhat meet these commitments then. Everyone seems to uphold Redhat as a model for contributing to upstream and working with the community, so how so they manage to do both that, and meeting commercial schedules?

Red Hat is in a fundamentally different business. They sell support. They don't contract to deliver support for code that hasn't been released.  Once they make a release, they come very close to freezing their code base for years, restricting the addition of new code to bug and security patches as much as possible. (And RH does have a  staff of developers.) 

Red Hat is also not trying to create a universal OS that works on multiple devices.  If Red Hat was, in fact, trying to do that, they'd face the same issues.  E.g., if they did a deal with a tablet maker, they'd need to agree on a set of schedules for delivery of working software, testing, etc.  When the vendor asked for a change, they'd need to be able to fix a date for delivery that was not enitrely fictional.  If they were dependent on people who don't work for them, who work part time on code that RH needs to meet a schedule commitment, then they'd lose control.  

Or, suppose RH needs XYZ library patched, by next Friday.  If the library's maintainer doesn't work for them, and decides he can't or won't do it, where does that leave RH? 

More simple example:  If you run a restaurant that needs to buy 200 loaves a bread a day, you won't sign a contract with a bakery than depends on part-time volunteer bakers who work out of their own kitchens, on no certain schedule.

---

### Post by erasmusp on 2013-09-11
> [I]Where does all the "if you aren't with us, you are against us" attidude come from?
Ubuntu decided to go its own way, so what? Why is that a bad thing?
Why are people (many of whom, apparently don't use Ubuntu) so peeved up about Canonical tying to invent something? [/I]

100%. Everybody is making a fuss about this but why? So what? We heard the same noise when Ubuntu took the Unity route. Now that noise has subsided and Unity is being accepted and like by many.... So please, let's all not be arm chair coaches here and see how this plays out.

---

### Post by ZoiaGuyver on 2013-09-11
> **santosh83 said:**
> I'm just speculating here, but could this (i.e., the larger community dropping Upstart to favour systemd) have anything at all to do with licensing. I know Upstart is also GPL just like systemd, but does contributing to it have any requirement for signing copyright assignment agreements or something like that? I understand that's the case for contributing to Mir.



The thing though is Canonical seems to be increasingly preoccupied with mobile systems, as they seem to be convinced that's where they can find any commercial success if at all. Desktops are being treated as second class citizens everywhere these days. :-(

As always hardware innovations and consumer reception will always drive the software by and large, as seen by the big shift from Workstations to PC form factors, then now the shift towards mobile. Redhat and Canonical both are profit driven (even if nominally) companies so they need to sell something somewhere. For Redhat it has long been enterprise support, and Canonical is now foraying into both mobile as well as enterprise support. The desktop code base will only be maintained by both as a sort of common launching point for their tailored solutions, and we have to live with that.

To cover the licensing part Canonical in the first CLA imo were wrong, they basically forced people to give Canonical the copyright to the material that person had contributed. With the changes in 2011 Canonical sorta reversed that, instead of giving Canonical the Copyright, the contributor gave Canonical a licence that allowed them to change the licence if needed, the contributor keeps the copyright. Its a much better solution, but at the moment the argument is there is no clause like that with FSF.

> "FSFE shall only exercise the granted rights and licences in accordance with the principles of Free Software as defined by the Free Software Foundations. FSFE guarantees to use the rights and licences transferred in strict accordance with the regulations imposed by Free Software licences, including, but not limited to, the GNU General Public Licence (GPL) or the GNU Lesser General Public Licence (LGPL) respectively. In the event FSFE violates the principles of Free Software, all granted rights and licences shall automatically return to the Beneficiary and the licences granted hereunder shall be terminated and expire.[18]"

Which seems to get a lot of peoples backs up, It's more a legal technicality and possibly a loophole. I'm not a lawyer, but having read and studied a lot of agreements from an OEMs perspective, I kinda see what Canonical are trying to do, but it also is a bit of contention. I think if any clause had been made in the CLA it wouldn't kick up as much fuss. Canonical isn't the only company in the free/open source market to use a CLA. Apache, FSF, Digia/QT Foundation and many others use them aswell. Although I personally have not studied them for the differences between them and Canonicals (outside of the before mentioned clause). All the projects at Canonical actually require this which is another point for argument, its not voluntary like the FSF one.

Now myself I kind of agree santosh83, at the moment Canonical seems to be focused on the mobile market. I don't agree that the desktop is a second class citizen (even though outside of the current issues it does certainly seem that way) I think a lot of people are seeing it as a separation which isn't the target. The target at least from Canonical is a convergence of the devices, I guess that at the start it does lead to a separation in the sense things have to be changed to accept the mobile infrastructure, So at some point mobile has to be the focus. Personally I feel this is the point at which we are at, 12.04LTS and 13.04 are well rounded and stable (for the most part). There hasn't been a lot of big changes as far as the end-user is concerned, but there has been a lot of change under the hood.

I think Canonical decided as the base 12.04 and 13.04 have proven themselves, that now was the time they could focus on the mobile side and start bringing things into line with each other. Time will tell if they are right, but the interest in Ubuntu Touch and Ubuntu Edge (although that failed for many reasons) shows that at least the direction is correct. 

Over the years the desktop computer (or personal computer) as a whole has seen huge changes in both it's usage and in it's tech. From being a system that was separated and thought of as a work tool not targeted at the home space, to something that consolidates our devices and is the main hub of our media intake as a consumer. This will definitely be an interesting time, the whole market has shifted and is still shifting towards more convergence of the devices we use. Canonical I think are chasing that goal with Ubuntu, but its receiving as much opposition as any product trying it before has. Whether Ubuntu wins out to be really frank is down to us.

---

### Post by codingman on 2013-09-11
> **cariboo907 said:**
> I personally think that Intel is shooting themselves in the foot. I've seen figures stating that there are about 70 million users of Linux based distributions, and Canonical claims there are about 20 million Ubuntu users, to me that looks like close to 1/3 of all Linux distribution users, use Ubuntu. I'm planning on building a new system in the new year, and this unsubstantiated silliness just pushed me away from even considering Intel products for my next build. 

I'll put up with a cpu that is a few percentage points slower than the current Intel offerings, I"ve never had any really good experience with Intel products so for me it really isn't that hard a decision to make.

I'm not going to argue the merits of either graphics rendering system, as there aren't any released versions of any distribution that use wayland or mir at this time. I've played with both, and neither seems to be better or worse than the other.

Maybe it's time to create a poll with the pre-requisite that if you vote, you have to provide proof that you are actually using one or the other.

+1

By the way, what do you plan on using? AMD FX Series or what? Phenom II? 

I only went for Intel because at the time of building, the FX Series was awful, and I needed something with low consumption, but before that I loved AMD all the way, and I was really sad about their decision to not compete with Intel any more...

---

### Post by cariboo on 2013-09-11
> **codingman said:**
> +1

By the way, what do you plan on using? AMD FX Series or what? Phenom II? 

I only went for Intel because at the time of building, the FX Series was awful, and I needed something with low consumption, but before that I loved AMD all the way, and I was really sad about their decision to not compete with Intel any more...

I'm planning on going with the AMD-FX series, especially now that they have a cpu that runs at 5Ghz (FX-9590).

---

### Post by Mephisto Pheles on 2013-09-12
Interesting and very educational thread indeed.

I found the EDGE concept interesting enough to realise that there's no way they will ever get there without having to leave behind some of the bagage of the past.
You can't define a new pardigm by desperately hanging on to the previous one.
I can understand some people are afraid, worried about where this might be leading to.
Some of the arguments are philosphical in nature, but even philosophy is subject to evolution.
Or it will become dogmatic.
 FOSS and whatever it is we understand under "linux community" will probably have to develop as well, unless it should become stale, and ultimately irrelevant.
That some people find that unsettling was to be expected. But honestly... does that justify your hatered?
I don't know Marc Shuttleworth, and although there have been some blunders and misunderstandings, it's not like there's a manual lying around somewhere to guide anybody through changes as fundamental as what Canonical has set out to do. 
Their journey to the future might not go over trodden paths of the past any longer.
Words, terms, definitions, concepts that once were important might have to be adjusted, some even abandoned, to change the paradigm this radical.
Are "desktop users" really being left behind, or are we in the middle of a development where the term "desktop user" is being redefined.
From what i've seen from the EDGE it looks a lot like that is the case. We may very well get a lot more instead of less in the end.
I don't have a smartphone or a tablet, I never was interested, my old "dumb" nokia still works and serves me well, but this EDGE idea really struck a chord.
Now that would be something I might be willing to go for.

Nobody can guarantee that it will work out as planned, but nobody can tell where or what it will lead us to either.
Did anybody know what Steve Jobs was gonna pull off when he came back to Apple?.
Did anybody even expect Jobs to return to Apple at all?
Did anybody expect NExTStep to become OS-X?
 
Shuttleworth might not exactly be a Steve Jobs but he's got a vision that I would not want to dismiss just like that.
Even if intel, nvidia and others are reluctant, for whatever reason, that doesn't have to mean they won't jump on board once the train starts rolling.
 Maybe Ubuntu will have to become a Linux based OS, like Android to some extent, instead of a Linux Distro as is now the case.
And those that want pure linux, there's enough choices. No?
I'm willing to wait and see.

I appreciate the guts that Ubuntu is displaying. And I'm sure that intel's coup will only make a lot of Canonical people even more determined.
And I wish them the best of luck.

- mephisto

---

### Post by ZoiaGuyver on 2013-09-12
JkbrrLJ That was a very interesting read and I agree with much of what you say.

Steve Jobs for good or bad made a very successful company, some would argue a "technology leading" company. Even though Apple is seen as the epitome of the "Walled/Shuttered/Closed garden" No one can really refute their success. 

Steve Jobs was also a visionary and unlike much of the Linux community on a whole was a very outspoken and critical person, even to the detriment of how people saw him. I think Mr Shuttleworth has a tendency to be head strong and outspoken, but he also gives a lot in the sense of supporting projects and ideas. The whole issue with Wayland and Mir is one that is based on semantics, corporate politics, differing opinion, misunderstanding, misinterpretation and FUD. These are not of any value to anyone, but with technology is often part of the driving factors. 

Like you say a lot of the times change is met with full brute force denial to it. The mindset for most people is that complete change is bad, incremental change is somewhat accepted. The whole Wayland/Mir story in a year or maybe less/more will be just another pin in the very spotty map of linux. Much like the arguments before them they will subside into obscurity.

As a whole people should embrace the projects as open source attempts to advance the current status quo. There will always be people who want to pick a fight just on the basis of their own view, the same as there will always be lemmings to follow those people. 

Mistakes were made (hopefully they will be learnt from) now is the time to move on to bigger and better things.

On that note some may be interested to have a read through articles like this, they are not really pertinent to the topic now but they do make interesting reading. [intel_fud_versus_amd_fact]("http://www.arnnet.com.au/article/183272/intel_fud_versus_amd_fact/")

---

### Post by buzzingrobot on 2013-09-12
The success of Apple is the best example that people care what's in the garden, not if it's closed or open.

If Jobs' developers brought him an idea or a prototype he didn't like, he would direct them to stop working on it.  And, they would. In LinuxLand, they'd fork their ideas and publicly accuse Jobs of being hostile to the welfare of "the community" (dev speak for disgreeing with them).

---

### Post by ZoiaGuyver on 2013-09-12
> **buzzingrobot said:**
> The success of Apple is the best example that people care what's in the garden, not if it's closed or open.

If Jobs' developers brought him an idea or a prototype he didn't like, he would direct them to stop working on it.  And, they would. In LinuxLand, they'd fork their ideas and publicly accuse Jobs of being hostile to the welfare of "the community" (dev speak for disgreeing with them).

That is by far the best analogy of it. It's also pretty much how open source works.

---

### Post by montag dp on 2013-09-12
> **ZoiaGuyver said:**
> That is by far the best analogy of it. It's also pretty much how open source works.That's true, but it applies to Canonical too.  Like how Wayland didn't work for them, so they decided to create their own display server and made false public claims about Wayland.

---

### Post by codingman on 2013-09-12
> **cariboo907 said:**
> I'm planning on going with the AMD-FX series, especially now that they have a cpu that runs at 5Ghz (FX-9590).

Meh. $700! I'd rather get an X79 system.

Guys, give Canonical a break, and let them do what they want, it's not like we're going to change their minds anytime soon.

---

### Post by monkeybrain20122 on 2013-09-12
> The success of Apple is the best example that people care what's in the garden, not if it's closed or open.

I understand the point being made, but Ubuntu is not a walled garden, everything is open source. If Mir ends up being a "Ubuntu only" solution it is because other distros prefer Wayland,--rightly or wrongly,-- it is not because Canonical doesn't allow it (I think it woud want the opposite) Also one is not restricted on Ubuntu in any way like on a Mac, Ubuntu offers as much freedom as other Linux distros. Steve Jobs went beyond being a "visionary", he took other people's ideas and closed them and then sued everyone for patent violation, I don't see that happening with Shuttleworth. Let's not fuel the misinformation and FUD even unintentionally. :)

---

### Post by Mephisto Pheles on 2013-09-13
> **ZoiaGuyver said:**
> JkbrrLJ That was a very interesting read and I agree with much of what you say.

Steve Jobs for good or bad made a very successful company, some would argue a "technology leading" company. Even though Apple is seen as the epitome of the "Walled/Shuttered/Closed garden" No one can really refute their success. 

Steve Jobs was also a visionary and unlike much of the Linux community on a whole was a very outspoken and critical person, even to the detriment of how people saw him. I think Mr Shuttleworth has a tendency to be head strong and outspoken, but he also gives a lot in the sense of supporting projects and ideas. The whole issue with Wayland and Mir is one that is based on semantics, corporate politics, differing opinion, misunderstanding, misinterpretation and FUD. These are not of any value to anyone, but with technology is often part of the driving factors. 

Like you say a lot of the times change is met with full brute force denial to it. The mindset for most people is that complete change is bad, incremental change is somewhat accepted. The whole Wayland/Mir story in a year or maybe less/more will be just another pin in the very spotty map of linux. Much like the arguments before them they will subside into obscurity.

As a whole people should embrace the projects as open source attempts to advance the current status quo. There will always be people who want to pick a fight just on the basis of their own view, the same as there will always be lemmings to follow those people. 

Mistakes were made (hopefully they will be learnt from) now is the time to move on to bigger and better things.

On that note some may be interested to have a read through articles like this, they are not really pertinent to the topic now but they do make interesting reading. [intel_fud_versus_amd_fact]("http://www.arnnet.com.au/article/183272/intel_fud_versus_amd_fact/")

   Not that I am an Apple fan, or even have any Apple devices myself, ipod was a fundamental change of concept, not just a player but including the entire iTunes eco-system that came with it. Just like the iphone, for a company that had never ever even made a phone was a bloody huge risk to take. Again it was not just a phone, but the entire apps eco-system that came with it. Those have been immense departures for Apple/Jobs. Look what it has done to the Nokias in the phone business. Not to mention what it has done to Microsoft.

The EDGE concept to me is just as interesting. If Ubuntu does succeed and manages to actually get it done, it'll be a major next step in the IT revolution. We'll look back on these discussions with a smile, and some with a certain degree of embarrassment I bet.

  Even if the EDGE concept - and even if Canonical as a company as a consequence - would fail miserably,  the Linux eco system will survive. Whether with Wayland or MIR or whatever else somebody else might come up with is something none of us can tell for sure. Linux was there long before Canonical and Ubuntu and it will survive without it, should that ever happen. The push forward in technology, or as they like to call it "device agnostic technology" to me is as important and liberating as the philisophy behind FOSS in all its variations. As the old saying goes: "you can't make an omelet without breaking eggs". The current environment as such is so rusted in old approaches and traditional procedures, that moving forward will always have to be at the expense of some of it having to give way to allow for new and different approaches.

I don't see any reason for an "either or" in this transition, it doesn't have to be either Wayland or MIR. Regardless of what corporations like Intel, NVIDIA and other hardware companies want.
In the end it will all be about what WE want!
 If Jobs would have announced itunes or asked for "permission", do you think any of the record companies would have wanted to know about it at the time? 
 He didn't leave them any choice, and now, finally, they are willing to admit that he probably saved their ass to a large extent.

Sometimes "visionaries" have no other option but to just to do it. And if it works out, all the rest will fall in place. 
Intel and the others will only be too happy to jump on the bandwagon. 
TIZEN isn't exactly going all that smooth either. Even with the backing of a giant like Samsung.
Let's not forget that even companies like intel - add the rest of the pack - have had numerous blunders and flops in their corporate history as well.
Was it Intel that came up with the idea of Android? Was it Samsung? Any of the other major vendors?

  If the EDGE concept will make it or rather ends up being made, it will be a revolution. And to those that have always wanted to see more adaption of linux, it might actually be a dream come true.

And let's not forget where Linux itself comes from. Anybody remember how outraged some of the old UNIX folks were at the time?
Canonical/Ubuntu can not accept that they're being held hostage by the likes of Red Hat, Intel.. you name them, the list is long.. and they should not accept it if they really want to make some landmark improvements and new products. That is inevitable. And that does not justify some of the questionable things they have done or said recently. The big mistake is that they're trying to justfiy their decisions. They don't have to. They should just do it, get on with it, show us that it can be done... and introduce the product.. and then it's our time to vote. With our wallets.

 I have the feeling too many people are overestimating the power of intel, no matter how huge they may be. They don't make the final calls. Not even on XMIR.

---

### Post by Mephisto Pheles on 2013-09-13
Here's a good read

One day we'll look back and say this was the end of the software platform
[http://www.theregister.co.uk/2013/09/13/microsoft_has_just_killed_the_software_era/](http://www.theregister.co.uk/2013/09/13/microsoft_has_just_killed_the_software_era/)

---

### Post by J._R._Menzie on 2013-10-02
Unity is great now. I was one of the hater before but they have done a lot of work on it.

---

### Post by Eggnog on 2013-10-07
My goodness.  All this sound and fury, signifying nothing.  Okay, I so stole that but still ...

---

