---
title: "Canonical needs to devote more developers, time and resources to Kubuntu"
date: 2010-04-26
forum: The Cafe
---

### Post by autumnraine on 2010-04-26
First of all I want to thank the Kubuntu developers for all the hard work they do. I like their general approach to keeping it simple and giving the user a mostly vanilla KDE implementation. That said, there are serious deficiencies with Kubuntu compared to some other KDE-focused distros, and the Kubuntu development team does not have sufficient resources ('manpower' for lack of a more appropriate term) to address all of these problems. 

Even if you personally don't like or use KDE, I think this should concern anyone who cares about Ubuntu, for several reasons. At least until Gnome 3 reaches an equivalent state of maturity as KDE 4.4, I think most people looking at it objectively would agree that KDE is presently more advanced in terms of overall desktop suite integration, and customization and system configuration capabilities - see [here]("http://itmanagement.earthweb.com/osrc/article.php/12068_3860396_3/KDE-vs-GNOME-Configuration-and-Admin-Tools.htm") for details. (while Gnome has many programs one can install to achieve similar ends these aren't integrated or as easy to use as those in KDE). This means that KDE is often the DE of choice for desktop users (of which there are still and probably always will be MANY) and professionals of various stripes. So Canonical is compromising it's own success by neglecting KDE. It's clear that BDFL Mark Shuttleworth [gets this]("http://dot.kde.org/2006/10/15/mark-shuttleworth-becomes-first-patron-kde"), so why is Canonical allowing Kubuntu to lag behind? 

To get more specific, here are some of the major PITA bugs still affecting my clean install of the Lucid Kubuntu RC (just the ones that come to mind at the moment), and which I'm pretty sure are NOT upstream problems: 

1) The keyboard shortcuts for several items - such as the desktop pager  and quick access menu, both on the panel by default - simply don't work,  even with the supposed workarounds listed elsewhere in these forums or on Launchpad.  

2) When I rotate the screen (using Krandr with the default Nouveau packages) the  screen is not properly refit to the changed orientation - the mouse will  continue going beyond the limits of the visible area, and menus at the  far right of the screen will be unreadable because they pop up mostly  off screen. 

3) As many people have mentioned, the panel icons, menus, pictures are frequently  scrambled, or however you'd describe it, especially but not exclusively for non-native KDE applications like OpenOffice and Skype. (May happen in Ubuntu too, I don't know; apparently specific to x64).

4) Pulseaudio does not integrate properly with Phonon, even though it  DOES in the recent betas of Mandriva and Fedora and is generally  supposed to integrate well in KDE 4.4.2. This is due to some packaging  mix ups which cause audio to be routed through Phonon's ALSA connection THEN to pulseaudio (and THEN to jack if you use it), which obviously caused several latency issues and is a regression from Karmic that [won't be fixed for the Lucid release]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/557514"). 

Some might say the first 3 are merely cosmetic annoyances, but they're not, they seriously hamper work flow and general usability. The 4th bug is obviously very serious, and a major show-stopper for me or anyone else with advanced audio needs - yet it seems it won't be fixed any time soon for lack of time and resources on the Kubuntu team's part. 

What I'm suggesting is that Canonical needs to devote more resources - specifically developers - to work on Kubuntu, even if it means a few less working on Gnome. We can all agree Gnome gets the lion's share of Canonical developers' attention, and that's NOT because Kubuntu is simply a 'community flavor' or spin-off - it's long been acknowledged as an essential alternative to Ubuntu's Gnome; or as Shuttleworth said regarding why he became the first 'Patron of KDE' in 2006 (see link above), "*With the growing importance of Kubuntu within the Ubuntu family *[...]"). I also don't think this is just a selfish request on my part, since it affects K/Ubuntu's competitiveness and hence Canonical's viability, not to mention the thousands of Kubuntu users either affected or chased away by it's deficiencies. 

So what do others think? Please vote and leave a comment.

---

### Post by carl4926 on 2010-04-26
I take it you are coming at this purely from a user perspective and not as a active developer?
Though you know users can participate in development, if only by testing and bug reporting.
You should check upstream for bugs on your issues too and report accordingly.

---

### Post by splicerr on 2010-04-26
> **autumnraine said:**
> I think most people looking at it objectively would agree that KDE is presently more advanced in terms of overall desktop suite integration, and customization and system configuration capabilities 

Only a KDE fanboy would come to that conclusion.  The general consensus is that KDE 4 is a buggy pos and a memory hog. Also I don't see the relevance to this forum.

---

### Post by autumnraine on 2010-04-26
> **splicerr said:**
> Only a KDE fanboy would come to that conclusion.  The general consensus is that KDE 4 is a buggy pos and a memory hog. Also I don't see the relevance to this forum.

I'm guessing you're not expecting me to take that seriously, but if you are, something more than vague 'general consensus' statements would be useful. 

And the relevance to this forum is that these bugs are all specific to Kubuntu 10.04, the DEVELOPMENT version of Ubuntu for the time being, hence the place where most future DEVELOPMENT will take place - and this is in the DEVELOPMENT forum!

---

### Post by Bachstelze on 2010-04-26
Other. It's not up to you or me to tell Canonical what they should do. Also, I'm perfectly satisfied with KDE in Ubuntu right now.

---

### Post by aceracer24 on 2010-04-26
Ubuntu was the main running distro with Kubuntu coming later as an after thought...at least as far as I know. If that is true, and I believe it is, Canonical should be devoting their main effort to Ubuntu, not Kubuntu. Kubuntu is a spin off of Ubuntu and is and always will be the red headed step child. That is not to say that I wouldn't mind "someone" putting more time into Kubuntu. I personally like the styling of Kubuntu better but Kubuntu was not first in the food chain.

---

### Post by autumnraine on 2010-04-26
> **carl4926 said:**
> I take it you are coming at this purely from a user perspective and not as a active developer?
Though you know users can participate in development, if only by testing and bug reporting.
You should check upstream for bugs on your issues too and report accordingly.
 
Definitely, I am primarily a user, but I don't quite understand the meaning of your distinction: other developers in several other distributions have either ironed out these issues or had the time to carefully configure their systems correctly so that these don't arise. My point is the Kubuntu development team is, by most people's accounts, understaffed and so unable to match the excellence achieved by the KDE implementations in other KDE-focused distributions. 

As a user I do my best to contribute by reporting bugs and commenting in Launchpad, as do many other volunteers, but I also work and study, and am not as yet an expert in Linux packaging and development. Inevitably the core of the development for most distributions will be done by developers paid by the distribution or a corporation, supplemented by some brilliant work by dedicated volunteers.

---

### Post by Khakilang on 2010-04-26
Canonical could very well concentrate on Ubuntu like most of the Distro they only had 1 flavour for their OS. Like Mandriva, OpenSuse, Debian and among others as compare to Canonical. What if Canonical concentrate all their resource to just Ubuntu alone? It could be one of the best Linux.

---

### Post by psyke83 on 2010-04-26
Before anybody dismisses the OP as trolling or becomes overly-defensive, keep in mind  that the Kubuntu developers are in consensus with autumnraine (more or less*). Within the Ubuntu community, KDE is not receiving enough attention and development manpower to reach its potential, and I find it hard to believe that anybody can consider Kubuntu as one of the best KDE distributions - unless they have never tried another KDE-focused distribution (such as openSUSE) in which to make a comparison.

Don't believe me? See [Project Timelord]("http://www.kubuntu.org/news/timelord").

*I'm speaking about KDE integration in general terms, not about the specific issues that autumraine has listed.

---

### Post by psyke83 on 2010-04-26
> **splicerr said:**
> Only a KDE fanboy would come to that conclusion.  The general consensus is that KDE 4 is a buggy pos and a memory hog. Also I don't see the relevance to this forum.

KDE 4.4.2 is a lot different to KDE 4.0 (which wasn't ready for mass consumption, and shouldn't have been released in distributions). Also, to call KDE a memory hog suggests that you're parroting complaints that you heard from others; I can run a KDE desktop on an ancient PII 350Mhz system with 196MB ram just as comfortably as GNOME.

---

### Post by psyke83 on 2010-04-26
> **Koh Kook Loon said:**
> Canonical could very well concentrate on Ubuntu like most of the Distro they only had 1 flavour for their OS. Like Mandriva, OpenSuse, Debian and among others as compare to Canonical. What if Canonical concentrate all their resource to just Ubuntu alone? It could be one of the best Linux.

Are you serious? What you're describing is the current status quo. Kubuntu is a second-class citizen, and the KDE packages are maintained by a very small group of developers.

---

### Post by Reiger on 2010-04-26
Hmm. I just wish that Kubuntu would offer the kde-minimal style package of Debian. That be the KDE base for me.

As far as things go the only problem I have with Kubuntu is that a lot of [s]Gnome[/s] Ubuntu specific stuff finds its way into Kubuntu without providing tangible improvements over the KDE equivalents. Regressions more like, because the KDE equivalents have been built with the needs of a KDE desktop in mind. And heaven only knows why installing a single gtk application (Meld or Wicd-gtk) can pull in half of gnome if you're not careful.

---

### Post by autumnraine on 2010-04-26
Thank you psyke83, I was a bit disconcerted by splicerr's in my opinion rude comment. I didn't intend this thread to be controversial, and I'm certainly not a troll - I post here regularly and more than anywhere else. But I do think this issue needs to be discussed.

---

### Post by cariboo on 2010-04-26
This really isn't a support question, or a discussion about Lucid. Moved to the Cafe.

---

### Post by Bachstelze on 2010-04-26
> **Reiger said:**
> Hmm. I just wish that Kubuntu would offer the kde-minimal style package of Debian. That be the KDE base for me.

Er, what? The [font=monospace]kde-minimal[/font] package is in Ubuntu too.

---

### Post by Reiger on 2010-04-26
> **Bachstelze said:**
> Er, what? The [font=monospace]kde-minimal[/font] package is in Ubuntu too.

Hey? Thanks for pointing that out, I'll use it when I install RC from the alternate CD then. (The live environment most definitely does not install kde-minimal.)

---

### Post by Bachstelze on 2010-04-26
> **Reiger said:**
> Hey? Thanks for pointing that out, I'll use it when I install RC from the alternate CD then. (The live environment most definitely does not install kde-minimal.)

It would defeat the point of having Kubuntu at all if all it did were install a barebone KDE. ;)

---

### Post by autumnraine on 2010-04-26
> **Bachstelze said:**
> It would defeat the point of having Kubuntu at all if all it did were install a barebone KDE. ;)

Not entirely, the KDE-minimal package still installs many Kubuntu customizations, and is still a Kubuntu system. It would be nice to have an option to install either the full or minimal Kubuntu version (maybe also the netbook version, if that's significantly different).

---

### Post by Bachstelze on 2010-04-26
> **autumnraine said:**
> Not entirely, the KDE-minimal package still installs many Kubuntu customizations

Namely?

---

### Post by 23meg on 2010-04-26
> **autumnraine said:**
> So what do others think?

I think telling privately funded companies what they should do is an exercise in futility, especially when there are far more viable and realistic alternatives for accomplishing what you want, such as strengthening the community of contributors to Kubuntu (that they are merely sponsoring, and they haven't committed to anything beyond that) by becoming part of it, and encouraging others to do so.

On a more general note (read: don't take this personally), I'm saddened by the widespread trend of people resorting to "Canonical should do more" at the sign of every shortcoming of Ubuntu, instead of thinking of what they can do themselves to fix or amend the issues they're encountering through community participation. If we're going to end up asking a specific company to "do more", or do the specific things that we think they should do every time we're dissatisfied with some aspect of free software, as if we were at their mercy, instead of seeing how we can fix it ourselves, we might as well be using proprietary software.

[QUOTE=psyke83]Before anybody dismisses the OP as trolling or becomes overly-defensive, keep in mind that the Kubuntu developers are in consensus with autumnraine (more or less*).

...

*I'm speaking about KDE integration in general terms, not about the specific issues that autumraine has listed[/QUOTE]

Here are two long-time Kubuntu developers who aren't, about the "Canonical should..." thing:

[http://apachelog.wordpress.com/2010/03/17/kubuntu-is-not-ubuntu/](http://apachelog.wordpress.com/2010/03/17/kubuntu-is-not-ubuntu/)
[http://blog.nixternal.com/2009.09.26/myth-of-the-blue-headed-step-children/](http://blog.nixternal.com/2009.09.26/myth-of-the-blue-headed-step-children/)

---

### Post by umberstark on 2010-04-26
Canonicals efforts to spruce up Gnome is akin to putting lipstick on a pig.

Ditch Gnome and make KDE the primary desktop enviroment, imo.

---

### Post by phrostbyte on 2010-04-26
From when I [rarely] deal with the Ubuntu developers, they generally seem swamped. There is definitely some kind of extreme shortage of them. So no I do not think Gnome should lose developers - it needs all it can get. There is no real easy solution to this problem, unfortunately. :(

---

### Post by Penguin Guy on 2010-04-26
> **splicerr said:**
> [QUOTE=autumnraine;9174991]I think most people looking at it objectively would agree that KDE is presently more advanced in terms of overall desktop suite integration, and customization and system configuration capabilities

Only a KDE fanboy would come to that conclusion.  The general consensus is that KDE 4 is a buggy pos and a memory hog. Also I don't see the relevance to this forum.[/QUOTE]
Actually I hate KDE, but I completely agree. There's no doubt that KDE's better than GNOME, but I also find KDE more complicated.

---

### Post by Khakilang on 2010-04-26
> **psyke83 said:**
> Are you serious? What you're describing is the current status quo. Kubuntu is a second-class citizen, and the KDE packages are maintained by a very small group of developers.

If there is shortage of manpower and only if. Which would they choose? KDE or Gnome?:confused::confused::confused:

---

### Post by autumnraine on 2010-04-26
> **23meg said:**
> I think telling privately funded companies what  they should do is an exercise in futility, especially when there are far  more viable and realistic alternatives for accomplishing what you want,  such as strengthening the community of contributors to Kubuntu (that  they are merely sponsoring, and they haven't committed to anything  beyond that) by becoming part of it, and encouraging others to do so.

On a more general note (read: don't take this personally), I'm saddened  by the widespread trend of people resorting to "Canonical should do  more" at the sign of every shortcoming of Ubuntu, instead of thinking of  what they can do themselves to fix or amend the issues they're  encountering through community participation. If we're going to end up  asking a specific company to "do more", or do the specific things that  we think they should do every time we're dissatisfied with some aspect  of free software, as if we were at their mercy, instead of seeing how we  can fix it ourselves, we might as well be using proprietary software.

Here are two long-time Kubuntu developers who aren't, about the  "Canonical should..." thing:

[http://apachelog.wordpress.com/2010/03/17/kubuntu-is-not-ubuntu/](http://apachelog.wordpress.com/2010/03/17/kubuntu-is-not-ubuntu/)
[http://blog.nixternal.com/2009.09.26/myth-of-the-blue-headed-step-children/](http://blog.nixternal.com/2009.09.26/myth-of-the-blue-headed-step-children/)

Interesting links, thanks :). However when I said "Canonical should" I meant, as I explained in the original post, that it would be in Canonical's own best interest to do so. It is a company whose product is selling commercial support for its own distributions, and so it makes sound business sense to not just concede a large percentage of your potential clientèle (KDE users) to your rival competitors. Hence my suggestions are no less legitimate than what you'd read in the op-eds of a financial magazine, for instance. 

I too appreciate that the heart of Linux is the DIY spirit and community participation of its users, but the facts remain that a) most users do not have the time or acquired knowledge to contribute heavily to the development of a distribution, and so b) the fundamental development work for any distribution sponsored by a company will be mostly done by paid developers. 

Ubuntu also prides itself on being a beginner-friendly distro that welcomes people with no Linux experience and little interest in knowing about the subsurface workings of a Linux desktop - that's one of its main target markets for paid support. Since it offers commercial support for Kubuntu, it makes no sense to then produce a less-than-stellar distro that it will have to struggle to support. 

> **Bachstelze said:**
>       [SIZE=1]Quote:[/SIZE]
                                                                      [SIZE=1]Originally Posted by **autumnraine**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9175305#post9175305")[/SIZE]                 
                 *[SIZE=1]Not entirely, the KDE-minimal  package still installs many Kubuntu customizations[/SIZE]*
                                 
Namely?

The packages are compiled and configured by the Kubuntu team, and if you install KDE-minimal in Ubuntu and then log in to the KDE, you'll see a desktop that is little different than what you end up with installing from the main Kubuntu Live CD - same theme, panel configuration, etc. 

> **aceracer24 said:**
>                                                    Ubuntu was the  main running distro with Kubuntu coming later as an after thought...Kubuntu was not first in the food chain.

This may have been how it started, but that's immaterial to the Ubuntu family's present priorities. One of its main 'selling points' is that it comes with such a diverse variety of pre-configured desktop environments, several of which - Kubuntu, Xubuntu, UNR, probably Lubuntu in the near future - Canonical wishes to sell support for (it explicitly says so on their websites). Hence it doesn't make sense even from a business perspective to produce less-than-stellar distributions if your bread and butter is to offer commercial support for them.

---

### Post by bigbrovar on 2010-04-26
You are very right in every aspect kubuntu can not be compared to ubuntu in term of features and attention ubuntu gets from canonical. The way i see it this has its pros and cons. On one hand, it means kubuntu misses out on most of the coolness and general awesomeness that canonical have developed for ubuntu. things like ubuntuone integration,music store, app center, guest session, new artwork etc. on the other hand it means less attention from canonical also means less imposition of ideas on the kubuntu community. When you look at the recent buttongate issue where canonical simply used its veto against users wishes to move the window buttons to the left. and how more and more the ubuntu distro is been shaped as an open source OSX implementation a move which many user aren't comfortable with. you will see that canonical's neglect of kubuntu is actually one of kubuntu's strength IMHO.

when i look at the two scenarios I think I would like the status quo to remain as is. if we can learn anything from canonical's ubuntu relationship.. he who plays the piper dictate the tunes. we may not have all the man power ubuntu gets. But we have something better. Kubuntu is a community distro independent of canonical and as a community we should look less and less to canonical for help and support but ask yourself what can i do to help? How can I help make kubuntu better. Things like artwork, filing bugs, code contribution etc would go along way. Even raising awareness, documentations blogging, helping out new users They are tons of ways every kubuntu user can help out make kubuntu a better product. Kubuntu choose to stick with kde vanilla hence any improvement to kubuntu is more likely to be accepted by kde upstream which means your improvements reaches out to more then just the *buntu crowd.

In conclusion I would defo appreciate more hands working on kubuntu. But if that would result in the project being hijacked from the community the way canonical hijacked ubuntu. then I think I would pass. we are much more better off to DIY as a community. IMHO

---

### Post by NightwishFan on 2010-04-26
I have always found Kubuntu satisfactory. It just does not really focus on branding in kde4 as much as it did on kde3 is all.

---

### Post by autumnraine on 2010-04-26
> **bigbrovar said:**
> You are very right in every aspect kubuntu can not be compared to ubuntu in term of features and attention ubuntu gets from canonical. The way i see it this has its pros and cons. On one hand, it means kubuntu misses out on most of the coolness and general awesomeness that canonical have developed for ubuntu. things like ubuntuone integration,music store, app center, guest session, new artwork etc. on the other hand it means less attention from canonical also means less imposition of ideas on the kubuntu community. When you look at the recent buttongate issue where canonical simply used its veto against users wishes to move the window buttons to the left. and how more and more the ubuntu distro is been shaped as an open source OSX implementation a move which many user aren't comfortable with. you will see that canonical's neglect of kubuntu is actually one of kubuntu's strength IMHO.

when i look at the two scenarios I think I would like the status quo to remain as is. if we can learn anything from canonical's ubuntu relationship.. he who plays the piper dictate the tunes. we may not have all the man power ubuntu gets. But we have something better. Kubuntu is a community distro independent of canonical and as a community we should look less and less to canonical for help and support but ask yourself what can i do to help? How can I help make kubuntu better. Things like artwork, filing bugs, code contribution etc would go along way. Even raising awareness, documentations blogging, helping out new users They are tons of ways every kubuntu user can help out make kubuntu a better product. Kubuntu choose to stick with kde vanilla hence any improvement to kubuntu is more likely to be accepted by kde upstream which means your improvements reaches out to more then just the *buntu crowd.

In conclusion I would defo appreciate more hands working on kubuntu. But if that would result in the project being hijacked from the community the way canonical hijacked ubuntu. then I think I would pass. we are much more better off to DIY as a community. IMHO

For the most part I definitely agree. However there are some things none but the most advanced users can do, such as compile a working implementation of Phonon's integration with Pulseaudio (as Mandriva and Fedora now do). For this we mostly rely on the ability of our development team to write good code (read: have the time to write good code), or are at the mercy of wise Jedi-superusers' benevolence, which is severely limited by the fact that most such people have other demanding day jobs. Users should contribute in every way possible and shoulder most of the load for artwork, helping people in the forums, etc. But for the really big stuff we need professional developers. IMO anyway FWIW.

---

### Post by bigbrovar on 2010-04-26
> **autumnraine said:**
> For the most part I definitely agree. However there are some things none but the most advanced users can do, such as compile a working implementation of Phonon's integration with Pulseaudio (as Mandriva and Fedora now do). For this we mostly rely on the ability of our development team to write good code (read: have the time to write good code), or are at the mercy of wise Jedi-superusers' benevolence, which is severely limited by the fact that most such people have other demanding day jobs. Users should contribute in every way possible and shoulder most of the load for artwork, helping people in the forums, etc. But for the really big stuff we need professional developers. IMO anyway FWIW.

You seem to under estimate the power of the community. Again I am not against cooperate sponsorship. what I am against is cooperate control against the spirit and wishes of the community. From the look of things the more people from canonical we have working on kubuntu. The less the influence the community would have on Kubuntu. The community is very powerful and some of the biggest contributors to kubuntu are not even employed by canonical. Take [http://identi.ca/nixternal](http://identi.ca/nixternal)  he is one of the biggest contributors to kubuntu he helped out with kubuntu plymouth theme and many other things with kubuntu yet he is not a canonical employee. we have distros like debian, archlinux etc which are completely community sponsored distros and yet Debian is one of the most stable linux distros out there. Community doesn't not mean unprofessional. Again it would be nice to have people paid to work on kubuntu. But if it would be at the cost of community control then i think we are better off as we are believe me. You dont even have to be a uber geek to help out. There are lots of little areas (artwork, documentations) which kubuntu can benefit from. Things like pulse integration with kde is being worked on upstream and the kubuntu developers i spoke too said it was decided by the community that Lucid should be left as is (being LTS and all) the move to pulse audio can be worked on with Lucid +

---

### Post by praveesh on 2010-04-26
Please see the web page :  [http://apachelog.wordpress.com/2010/03/17/kubuntu-is-not-ubuntu/](http://apachelog.wordpress.com/2010/03/17/kubuntu-is-not-ubuntu/)   . It says why kUbuntu is not  recieving much love from canonical .

---

### Post by uljanow on 2010-04-26
Why isn't KDE in the main repository? Such an important software shouldn't be in the community section.


Canonical should consider switching to KDE as the default DE. It's hard to image that the next Ubuntu release will be shipping with Gnome Shell which requires 3D support, doesn't support Desktop effects (compiz) and has a  completely new UX.

---

### Post by Grenage on 2010-04-26
Indeed, God help them for wanting to try something different.  Who wants to try new things, when we could just update the same old programs for the next 20 years.

---

### Post by Zlatan on 2010-04-26
> **uljanow said:**
> ...


Canonical should consider switching to KDE as the default DE. It's hard to image that the next Ubuntu release will be shipping with Gnome Shell which requires 3D support, doesn't support Desktop effects (compiz) and has a  completely new UX.

1. Canonical should? What if I tell you what YOU should do?:)
2. Please check before spreading FUD on Gnome Shell, you will sound more reasonable:
[http://live.gnome.org/GNOME3Myths]("http://live.gnome.org/GNOME3Myths")

---

### Post by uljanow on 2010-04-26
> **Zlatan said:**
> 1. Canonical should? What if I tell you what YOU should do?:)
2. Please check before spreading FUD on Gnome Shell, you will sound more reasonable:
[http://live.gnome.org/GNOME3Myths]("http://live.gnome.org/GNOME3Myths")

That's factually accurate. You SHOULD check it out yourself.

---

### Post by XubuRoxMySox on 2010-04-26
I checked "Other" out of ignorance. It's a really a vote for "I dunno."

But it seems to me that [SIZE="6"]X[/SIZE]ubuntu is the more likely "blue-headed step child" of Canonical. I find it curiously odd that Canonical's ShipIt service offers Ubuntu and Kubuntu CDs, but not Xubuntu CDs. They had to make their own separate arrangements with another vendor (On-Disk.com). 

My question is motivated only curiosity about the relationship between the 'buntus and Canonical, not in any sense of "what canonical should do."

Just wondering,
Robin

---

### Post by swoll1980 on 2010-04-26
Canonical doesn't **need** to do anything. They don't even have to develop Ubuntu if they don't want to.

---

### Post by BrokenKingpin on 2010-04-26
I think they should focus mainly on Gnome. I feel supporting multiple spin-offs makes the Gnome version suffer. I have no problem with spin-offs of Ubuntu, I just do not think Canonical should manage and support them. They should only manage/support Desktop/Netbook, and Server editions.

---

### Post by MCVenom on 2010-04-26
> **splicerr said:**
> Only a KDE fanboy would come to that conclusion.  The general consensus is that KDE 4 is a buggy pos and a memory hog. Also I don't see the relevance to this forum.
Gnome fanboy here -- just so you can't call me a KDE fanboy :P

I believe OP was comparing KDE to Gnome 3. Now considering that Gnome 3 hasn't even had a BETA yet, I'm pretty sure that its not as mature as Gnome (current) or KDE. Don't get your panties in a bunch. :rolleyes:

I've used the version of Gnome Shell in the Karmic repos (PPA was always broken for me, I even got a few nasty memory leaks from it :(), judging just from it, I'd say that Gnome 3 has a long way to being a mature DE.

---

### Post by EarthMind on 2010-04-26
I voted yes because despite using it myself I hate Gnome for its slowness and ugliness.

---

### Post by tommcd on 2010-04-26
Personally, I have never liked KDE. There is just too much "stuff" in the KDE menu. I prefer a simple and uncluttered and uncomplicated user interface. I also use the terminal for all sys admin and software installation tasks. I also even use MPlayer from the terminal to play all my music and video files. So I do not care if "*KDE is presently more advanced in terms of overall desktop suite integration, and customization and system configuration capabilities *" as the OP said. 
However...
If Ubuntu (i.e., Canonical) claims to support and develop Kubuntu as well as the obvious flagship (and Mark Shuttleworth favorite) Ubuntu with Gnome, then I would think that they ought to devote as much resources to developing Kubuntu as they do Ubuntu.
Many first time linux users are just as likely to try Kubuntu instead of Ubuntu. If they have a poor experience with Kubuntu, they may just decide that *buntu in particular (and therefore linux in general) sucks. And they will no doubt tell *all* of their friends about it.
So .... the *buntu devs should devote equal resources to Kubuntu as they do Ubuntu. If they claim to support KDE, then they should support it just as well as Gnome.

---

### Post by koenn on 2010-04-26
> **autumnraine said:**
> Interesting links, thanks :). However when I said "Canonical should" I meant, as I explained in the original post, that it would be in Canonical's own best interest to do so. It is a company whose product is selling commercial support for its own distributions, and so it makes sound business sense to not just concede a large percentage of your potential clientèle (KDE users) to your rival competitors. 

I'd say it's up to canonical to take its own business decisions, but if it's just about sharing opinions, gere's mine:

It would probably *also*be in Canonical's own best interest not to spread it's resources too thin. Or to compete with it's own flagship. Or assume responsibility for something they don't control (or have a conflict with the Kubuntu community over that control). etc.  
it's all in here, really: [http://apachelog.wordpress.com/2010/03/17/kubuntu-is-not-ubuntu/](http://apachelog.wordpress.com/2010/03/17/kubuntu-is-not-ubuntu/)

It's up to Canonical, of course, but to me that outweighs "more users, more potential support contracts - good for business". So your post still reads as a "I have some problems with Kubuntu, Canonical should bail me out" thing.


Other than that, I think the decision to have Gnome as a desktop makes perfect sense, from an Ubuntu/Canonical point of view. Ubuntu was "for human beings", and their strategy was : make things simple, reduce overwhelming choice, deliver a system that works without any additional configuration ... (see a.o. the live cd installer, the 1 task = 1 program approach, ...). Gnome takes a similar approach to DE - it's a natural match.

---

### Post by Frogs Hair on 2010-04-26
> **Bachstelze said:**
> Other. It's not up to you or me to tell Canonical what they should do. Also, I'm perfectly satisfied with KDE in Ubuntu right now.

I agree , because I don't know the big picture or Canonical's plans for its operating systems in the future.

---

### Post by Zlatan on 2010-04-26
> **uljanow said:**
> That's factually accurate. You SHOULD check it out yourself.

The only component that requires 3D or graphics acceleration is GNOME Shell and to be fair can perform very well in any computer from the last 4 years.

In the worst case, you can opt to not use GNOME Shell and instead use the Panel and Metacity from GNOME 2.x.

cited from my link

---

### Post by cgroza on 2010-04-26
KDE always left me down so I believe that id does not worth it.

---

### Post by beetleman64 on 2010-04-26
To be perfectly honest, if I was high up at Canonical then I would dump every additional project and just keep Ubuntu and the Server Edition. That would ensure that these two core projects receive the development they need and deserve with no excess baggage.

---

### Post by thatguruguy on 2010-04-26
I've never been a fan of the KDE desktop, really.  I find it kind of confusing, placing eye candy above simplicity.  Although I realize and appreciate that others may disagree.  That being said, I think that if Canonical is going to devote more developers, time and resources to ANYTHING it should be fixing some of the extant bugs in the system, particularly the bugs in its flagship product, Ubuntu.  After those issues are resolved, it can worry about the spin-offs.

---

### Post by WinterMadness on 2010-04-26
Gnome is simply out dated.

Many Ubuntu users havent really given KDE its fair shot. You guys took the time to learn Ubuntu with Gnome, why wouldnt you give it its fair shot?


Gnome is only really good if you dont have a ton of applications installed. If you do, the kick off menu is superior.

I am typically a Mandriva user. I would prefer if Ubuntu had a really good KDE implementation because I prefer the way Ubuntu works under the hood.

---

### Post by WinterMadness on 2010-04-26
> **thatguruguy said:**
> I've never been a fan of the KDE desktop, really.  I find it kind of confusing, placing eye candy above simplicity.  Although I realize and appreciate that others may disagree.  That being said, I think that if Canonical is going to devote more developers, time and resources to ANYTHING it should be fixing some of the extant bugs in the system, particularly the bugs in its flagship product, Ubuntu.  After those issues are resolved, it can worry about the spin-offs.

what did you find was confusing?

finding applications in KDE is probably twice as fast.

I never look through menus or anything like that

if im looking for netbeans I usually put it on my favorites list or I just type "net" and hit enter. Its usually the first result in the search box

---

### Post by MCVenom on 2010-04-26
> **WinterMadness said:**
> Gnome is simply out dated.

Many Ubuntu users havent really given KDE its fair shot. You guys took the time to learn Ubuntu with Gnome, why wouldnt you give it its fair shot?


Gnome is only really good if you dont have a ton of applications installed. If you do, the kick off menu is superior.

I am typically a Mandriva user. I would prefer if Ubuntu had a really good KDE implementation because I prefer the way Ubuntu works under the hood.
No off-topic! :p

This is not a discussion of **Gnome's out-dated-ness**, or **KDE's inherent superiority** and uber-simplicity! Back on subject! :p

---

### Post by autumnraine on 2010-04-26
> **koenn said:**
> your post still reads as a "I have some problems with Kubuntu, Canonical should bail me out" thing.

I don't see how you can draw that conclusion from my posts - from the amount of information I've provided it should be evident that *I* am perfectly capable of using a diifferent distribution; nonetheless I do like the *buntus for the most part and want to see them succeed, and because the *buntus are many times over the most used distribution, especially by people new to Linux, I'm also concerned that their negative experiences with any *buntu will soil the reputation of Linux in the broader mainstream media and popular consciousness. As tommcd put it: 

> **tommcd said:**
> Many first time linux users are just as likely to try Kubuntu instead of Ubuntu. If they have a poor experience with Kubuntu, they may just decide that *buntu in particular (and therefore linux in general) sucks. And they will no doubt tell all of their friends about it.

If other people don't care whether that happens that's fine and their perogative. But personally I do.

---

### Post by autumnraine on 2010-04-26
> **cgroza said:**
> KDE always left me down so I believe that id does not worth it.

Have you tried any other distribution that is KDE-centric (like the ones mentioned in the poll)? If not then you haven't really experienced how good KDE can be, hence the topic of this thread.

---

### Post by seenthelite on 2010-04-27
[QUOTE=autumnraine;9174991] That said, there are serious deficiencies with Kubuntu compared to some other KDE-focused distros, and the Kubuntu development team does not have sufficient resources ('manpower' for lack of a more appropriate term) to address all of these problems. 

 I have been using (testing) Kubuntu 10.04 and like KDE and would like to check out the other KDE-focused distros, could you recommend one or more, please.

---

### Post by NightwishFan on 2010-04-27
I think Kubuntu is fine, and I have used Mandriva and OpenSUSE. (I recommend OpenSUSE but Mandriva was fun). Kubuntu is more sternly KDE, but I agree it could use some themes and branding to make it a fun KDE desktop.

---

### Post by koenn on 2010-04-27
> **autumnraine said:**
> I don't see how you can draw that conclusion from my posts - from the amount of information I've provided it should be evident that *I* am perfectly capable of using a diifferent distribution; nonetheless I do like the *buntus for the most part and want to see them succeed, and because the *buntus are many times over the most used distribution, especially by people new to Linux, I'm also concerned that their negative experiences with any *buntu will soil the reputation of Linux in the broader mainstream media and popular consciousness. As tommcd put it: ...

Let me rephrase that. I get the impression that you're annoyed with some shortcomings in Kubuntu, and that your plea for Canonical to do something about it is more generated by self-interest, although you're trying to pass it of as "in the interest of Canonical". Seeing similar threads over the years probably has something to do with it, but yes, in the end it's just a subjective opinion, impression, interpretation, ... so if you say I'm wrong, so be it - let's both not lose sleep over it.


As your reference to tommcd's "Many first time linux users are just as likely to try Kubuntu instead of Ubuntu" - I pretty much doubt that. 

First time users will be googling 'Ubuntu' 'cause that's what all the hype is about. And whether it's from ubuntu.com or canonical.com (where they'll end up after googling), all the "get ubuntu" links lead to an ubuntu download - looks to me that it's going to be pretty hard to find Kubuntu if you don't already knows it exists and go look for it explicitly, and most first timers will know about Ubuntu, not Kubuntu. 
So no, I don't think that first time users are just as likely to try Kubuntu instead of Ubuntu.

---

### Post by NightwishFan on 2010-04-27
I honestly think Ubuntu and Kubuntu should merge identity. However, it has been Kubuntu for so long that would be difficult.

---

### Post by autumnraine on 2010-04-28
> **seenthelite said:**
> I have been using (testing) Kubuntu 10.04 and like KDE and would like to check out the other KDE-focused distros, could you recommend one or more, please.

Absolutely. I would start with PC Linux OS (most user friendly) or Mandriva (which PC Linux OS is based on). If you want to stick with Debian, Mepis uses KDE 4.3.4 and is built upon the stable branch of Debian, unlike Ubuntu which samples from the testing and sid (unstable) branches. openSUSE has the most advanced configuration options. If you need new features like Nouveau or Pulseaudio integration, the testing versions of Fedora and Mandriva include these. Otherwise I would go with the latest stable release.

---

### Post by autumnraine on 2010-04-28
> **koenn said:**
> First time users will be googling 'Ubuntu' 'cause that's what all the hype is about. And whether it's from ubuntu.com or canonical.com (where they'll end up after googling), all the "get ubuntu" links lead to an ubuntu download - looks to me that it's going to be pretty hard to find Kubuntu if you don't already knows it exists and go look for it explicitly, and most first timers will know about Ubuntu, not Kubuntu. 
So no, I don't think that first time users are just as likely to try Kubuntu instead of Ubuntu.

Except that most new users will be coming from Windows, and those who don't much like or care about computers and just use them for basic functions are going to be more comfortable with the layout of KDE. Thus if I were installing Linux for an older relative, for instance, I'd show them what KDE and Gnome each look like and most of the time they'd pick KDE. Yes they could quickly learn how Gnome works but some people don't want to - they want to use their computer as a tool and get on with their lives.

---

### Post by dewclaw82 on 2010-04-29
I'm certainly in the "more resources for Kubuntu" camp.  I find that the basic packages tend to work just about the same as they did in _Dapper._  Just as one example, instead of upgrading the Konquerer or Krusader, the developers came up a new file manager in Dolphin.  Dolphin sure had a cute and spiffy interface but but using it in dual pane view was a horror; even if you got it there once, the minute you narrowed in on something, both of your panes changed back to your "cute little house."  It would have been much more helpful to make substantive improvements to Krusader and then incorporate some new icons if a new look was desired.  I'll take competent over cute any day.

---

### Post by NightwishFan on 2010-04-29
Well Dewclaw, that was an upstream KDE decision to make Dolphin the default. If alternatives exist you can still use them.

---

### Post by ssri on 2010-04-29
> **koenn said:**
> As your reference to tommcd's "Many first time linux users are just as likely to try Kubuntu instead of Ubuntu" - I pretty much doubt that. 

First time users will be googling 'Ubuntu' 'cause that's what all the hype is about. And whether it's from ubuntu.com or canonical.com (where they'll end up after googling), all the "get ubuntu" links lead to an ubuntu download - looks to me that it's going to be pretty hard to find Kubuntu if you don't already knows it exists and go look for it explicitly, and most first timers will know about Ubuntu, not Kubuntu. 
So no, I don't think that first time users are just as likely to try Kubuntu instead of Ubuntu.

Funny, almost two years ago, I decided to use a partition from a new harddrive on my laptop to try out linux.  I never used linux prior to that, but I heard of gnome and kde.  I also used to have a csh shell account at a local ISP, where I first learned how to use the cli, twelve years earlier.  Anyways, after seeing the media coverage for Ubuntu 08.10, I decided to check it out.  Needless to say that I was not too impressed with the earthtones from canonical's screenshots, so I checked out Kubuntu.  I have to admit, KDE 4.1.x was a bit of a rough ride.  However, trying out gnome via ubuntu or fedora has always left me dissatisfied.  Slowly, but surely, KDE became better and was truly usable by 4.2.x.

---

### Post by Sporkman on 2010-04-29
KDE seems foreign & weird.

---

### Post by ttshivers on 2010-04-29
I don't care much about Kubuntu or KDE.  It reminds me too much of windows.  I like Gnome much better.

---

### Post by drreed on 2010-04-29
Well I said no, but now that I think about it, maybe they should. Then, when I take a wrong turn and wind up with K on my desktop, it might not be as unpleasant as it is now. I use a distro with kde3 (Back Track 4) several times a day and in my opinion, it's second rate compared to almost anything else produced in the last 5 years.  Why anyone would want it is beyond me, unless it was the first Linux environment they used, and they don't want to change because of the time invested.

I get my work done, but I'm glad to hit reboot when I'm done.:)

---

### Post by Firestem4 on 2010-04-29
Kubuntu is not developed by Canonical. It is a community-developed derivative of Ubuntu. Canonical isn't lacking in terms of support for Kubuntu because they don't develop it. Its up to the community developer for this. And they're doing a good job as time progresses.

> **splicerr said:**
> Only a KDE fanboy would come to that conclusion.  The general consensus is that KDE 4 is a buggy pos and a memory hog. Also I don't see the relevance to this forum.

Memory hog is subjective. I typically see my full KDE-desktop run at 300mb's in RAM. Todays computer that have upwards of 6 gigs?

---

### Post by NightwishFan on 2010-04-29
I was under the impression Kubuntu was official and had paid developers at Canonical.

---

### Post by OrbJinzo on 2010-04-29
I loved kde back in the 3.5.x and earlier days. I always though gnome was sluggish and crashed alot for me. Then KDE 4.x dropped I tried on each release from 4.0 to 1 to 2 3 and 4 and i still cant stand it. Then I decided to give gnome another try and once i setup it right most of my issues was fixed

---

### Post by bruce89 on 2010-04-29
Count yourselves lucky.

---

### Post by autumnraine on 2010-05-01
> **Firestem4 said:**
> Kubuntu is not developed by Canonical. It is a community-developed derivative of Ubuntu. Canonical isn't lacking in terms of support for Kubuntu because they don't develop it. Its up to the community developer for this. And they're doing a good job as time progresses.

Beg to differ. Canonical offers paid support for Kubuntu, therefore they MUST have some of their own paid developers involved to ensure that they would be able to support it. And as NighwishFan said Kubuntu is an OFFICIAL member of the *buntus and a project of Canonical, even if it may be more community-driven (in the negative sense of being less encumbered by arbitrary commands from on high).

---

### Post by KiwiNZ on 2010-05-01
Kubuntu is officially supported. I do not agree that more resources should be given to Kubuntu at the cost of Ubuntu, Edubuntu or the Server edition.

---

### Post by Ms_Angel_D on 2010-05-01
I have to agree that Since it is advertised that they provide support for both DE's, it only makes since to help develop both. But I'm for adding new developers and not taking away from Ubuntu's Dev team.

---

### Post by Chrysantine on 2010-05-01
Having tried KUbuntu in a VM, I can only say one thing; it's a total mess. If you want a proper KDE desktop, just switch to another distribution and see how 4.4 ploughs GNOME into a pit with features.

As for "memory consumption", well DDR3 is literally free off the shelf nowadays.

---

### Post by praveesh on 2010-05-01
When opensuse introduced firefox integration , it got too much publicity . But at that same time , KUbuntu introduced openoffice integration in kde 4 . But it didn't get any publicity . Now  the KUbuntu people introduced firefox integration in lucid . But nobody is mentioning it anywhere. There is partiality  . I think there is a general belief that the  KUbuntu is bad  . It is not as bad as many people say .

---

### Post by praveesh on 2010-05-01
> **Chrysantine said:**
> Having tried KUbuntu in a VM, I can only say one thing; it's a total mess. If you want a proper KDE desktop, just switch to another distribution and see how 4.4 ploughs GNOME into a pit with features.

As for "memory consumption", well DDR3 is literally free off the shelf nowadays.

Can you say why KUbuntu is a mess ? What in KUbuntu doesn't work for you ?

---

### Post by kaldor on 2010-05-01
KDE3 wasn't for me.

KDE4 was promising, but I fought with it too much to get stuff done. TOO buggy. At least KDE4 got rid of the cartoonish appearance and opted for the nice glassy look it now has...

I think KDE is promising, but my problem is that it *really* resembles Windows way too much. I'd rather see the technology go to something more unique and interesting. There have been times I have mistaken KDE for Vista/7.

Kubuntu 10.04 is a bad example for an LTS. KDE is a mess in its current form. Advanced users won't mind much, but imagine the constant issues/bugs/crashes to the average idiot.

---

### Post by Danny Dubya on 2010-05-01
> But at that same time , KUbuntu introduced openoffice integration in kde 4 . But it didn't get any publicity .
And could that possibly be because OpenOffice's KDE4 integration is a mess of graphical glitches that just looks barely native, compared to the GTK version? I would've been more than happy if OpenOffice just got KDE dialogs, defaults or whatever like Firefox did, but they messed with the look too and it looks way too rough around the edges.

---

### Post by praveenthivari on 2010-05-01
Kubuntu needs more attention, but not so much so tht Canonical would need to devote whole lot of time in improvements. It just requires a few little things which are completely overlooked by canonical, like:
1) Does Kubuntu hav a software cente. It has  package management, but I want Software management equal to USC.
2) ICONS,those reload, stop, home buttons of dolphin, firefox really sucks.  Folders look great though. I want icons to look like those in Ubuntu, not those old looking ones :-(

For tht matter no other OS has changes those icons

---

### Post by jkxx on 2010-05-01
> 1) Does Kubuntu hav a software cente. It has package management, but I want Software management equal to USC.

A manner of theming or skinning. Here I have both GTK and Qt use qtcurve so basically I get Nautilus and Dolphin to look nearly identical and both integrate well with the overall desktop. They could do that by default or do a GTK->Oxygen translator if they want to get really ambitious. There is no reason to not use the existing GTK apps, many of which are of excellent quality.

I'll have to agree there are various issues in Kubuntu though, most notably the Phonon/PulseAudio mess the OP mentioned. I can't have more than one app playing sound without things getting messed up to where sound just stops until I close all offending apps.

I've spotted several bugs in KDE's apps as well but those are for the KDE devs to work on and not necessarily Kubuntu's. 

There's nothing wrong with supporting Gnome as it is one of the 2 "major" desktop suites out, but it makes sense to pay as much attention to KDE, it being the second big desktop suite.

---

### Post by Half-Left on 2010-05-01
> **kaldor said:**
> KDE3 wasn't for me.

KDE4 was promising, but I fought with it too much to get stuff done. TOO buggy. At least KDE4 got rid of the cartoonish appearance and opted for the nice glassy look it now has...

I think KDE is promising, but my problem is that it *really* resembles Windows way too much. I'd rather see the technology go to something more unique and interesting. There have been times I have mistaken KDE for Vista/7.

Kubuntu 10.04 is a bad example for an LTS. KDE is a mess in its current form. Advanced users won't mind much, but imagine the constant issues/bugs/crashes to the average idiot.

Funny, people say exactly the same thing about Lucid, in the fact is an OS X copy.

Who cares about looks anyway? KDE4 is much different in it's design ideas from Windows 

KDE4.4 is much, much more flexible than Windows and it's layout has always been the same from it's conception. I think it's a case of Windows 7 can be mistaken for KDE4 because KDE4 has been out well over 2 years.

---

### Post by ronnoc on 2010-05-01
> **splicerr said:**
> Only a KDE fanboy would come to that conclusion.  The general consensus is that KDE 4 is a buggy pos and a memory hog. Also I don't see the relevance to this forum.

Methinks the vote tallies on this poll would prove your derogatory slam abhorrently false...

---

### Post by ronnoc on 2010-05-01
> **kaldor said:**
> KDE3 wasn't for me.

...but my problem is that it *really* resembles Windows way too much. I'd rather see the technology go to something more unique and interesting. There have been times I have mistaken KDE for Vista/7.

If you follow the development timelines though you could only help but come to the logical conclusion that, in fact, it was Windows that copied KDE ni terms of looks and function. The volume bar, for example, appears identical in Win7 to KDE 4.x. 

I would take it as a compliment. Imitation, after all, is the sincerest form of flattery. :P

---

### Post by claydoh on 2010-05-01
> **23meg said:**
> I think telling privately funded companies what they should do is an exercise in futility, especially when there are far more viable and realistic alternatives for accomplishing what you want, such as strengthening the community of contributors to Kubuntu (that they are merely sponsoring, and they haven't committed to anything beyond that) by becoming part of it, and encouraging others to do so.

On a more general note (read: don't take this personally), I'm saddened by the widespread trend of people resorting to "Canonical should do more" at the sign of every shortcoming of Ubuntu, instead of thinking of what they can do themselves to fix or amend the issues they're encountering through community participation. If we're going to end up asking a specific company to "do more", or do the specific things that we think they should do every time we're dissatisfied with some aspect of free software, as if we were at their mercy, instead of seeing how we can fix it ourselves, we might as well be using proprietary software.



Here are two long-time Kubuntu developers who aren't, about the "Canonical should..." thing:

[http://apachelog.wordpress.com/2010/03/17/kubuntu-is-not-ubuntu/](http://apachelog.wordpress.com/2010/03/17/kubuntu-is-not-ubuntu/)
[http://blog.nixternal.com/2009.09.26/myth-of-the-blue-headed-step-children/](http://blog.nixternal.com/2009.09.26/myth-of-the-blue-headed-step-children/)

I have to agree 100% with the above. Demanding Canonical do something that distracts them from their overall long term goals is bad for everyone. Kubuntu included.

---

### Post by ronnoc on 2010-05-04
> **claydoh said:**
> I have to agree 100% with the above. Demanding Canonical do something that distracts them from their overall long term goals is bad for everyone. Kubuntu included.

I think the OP is making a case that Canonical should align with KDE to batter enhance their chances of achieving their overall goals. To that end, I would have to agree. KDE, IMHO, is the best chance Canonical has to get rid of bug #1.

---

### Post by Yuri sss on 2010-07-05
[x] Yes, Canonical should devote more developers/time and resources to Kubuntu.

> **Ms_Angel_D said:**
> I have to agree that Since it is advertised that they provide support for both DE's, it only makes since to help develop both. But I'm for adding new developers and not taking away from Ubuntu's Dev team.
Yes, since it's advertised, they really ought to put more effort into the development of Kubuntu.

---

### Post by Bachstelze on 2010-07-05
> **Yuri sss said:**
> 
Yes, since it's advertised, they really ought to put more effort into the development of Kubuntu.

Where is it advertised?

---

### Post by mamamia88 on 2010-07-05
don't like kde never have so my vote is no

---

### Post by claydoh on 2010-07-05
> **mamamia88 said:**
> don't like kde never have so my vote is no

**I** have never liked Gnome, and (probably) never will ;), and I still say no - they should stick to what they have put their time and effort into.

---

### Post by NightwishFan on 2010-07-05
If KDE continues to be popular I am quite sure it will continue to be available.

---

### Post by greg batmarx on 2010-07-10
Till now, I was using gnome and I loved it!
Then I tested kde 4.5rc and wow!
This is awesome!

What can I say?
I could not imagine that kde is so much better than gnome.

I will mention just 3 reasons:

1)Tabbed AND tabbing applications!So convenient to tab an app inside another app.Simple marvelous!

2)Different wallpapers AND different widgets in each desktop.
I was dreaming for this to be done in gnome.It is done in KDE!

3)Activities that give another dimension to "different wallpapers and widgets in each desktop" You have to see it to believe it!
I have 4 different desktops in 6 different activities.

Thus, I have 24(!) different wallpapers (and some wallpapers can be the whole earth rotating!) and 40 different widgets at the same time in one computer!
SIMPLY UNBELIEVABLE!
And yes all these don't eat my resources(at least as much as I was expecting)!
I can run 10 different apps without lagging and my computer is a cheap acer notebook dual core with 4 giga RAM.

Yes! kde was buggy and still has its bugs.
Yes! kde demands relatively powerful computers and not old ones to reveal its beauty!
Yes! it can be better!

BUT,it is clearly the future in a manner that gnome is not...
I still love gnome, but I adore kde!

Ubuntu should consider to give more resources to kubuntu!
It deserves it!

PS Till kde 4.3, i could not run this gui in my computer...
It failed...Unbelievable how much thing changed and kde runs so smoothly now!

---

### Post by Redo on 2010-07-10
I've had endless issues with KDE 4.x among many distros. If Canonical puts all of its resources behind KDE, it still wouldn't be enough to get KDE to be as solid and stable as Gnome with a variety of hardware setups.

Ubuntu has the best Gnome setup out of the box of any distro IMO. They should keep developing exactly as they are now.

---

### Post by lcnrj on 2010-07-12
> **psyke83 said:**
> KDE 4.4.2 is a lot different to KDE 4.0 (which wasn't ready for mass consumption, and shouldn't have been released in distributions). Also, to call KDE a memory hog suggests that you're parroting complaints that you heard from others; I can run a KDE desktop on an ancient PII 350Mhz system with 196MB ram just as comfortably as GNOME.

Yes! I agree too.
And doesn't show liberty kill KDE 

Another thing: the prograns for KDE still better then for gnome.

---

