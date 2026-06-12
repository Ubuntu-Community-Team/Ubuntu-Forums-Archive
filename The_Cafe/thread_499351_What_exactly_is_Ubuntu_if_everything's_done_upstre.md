---
title: "What exactly is Ubuntu if everything's done upstream?"
date: 2007-07-12
forum: The Cafe
---

### Post by Game_boy on 2007-07-12
I understand what Ubuntu is, as a Linux distribution: it includes a desktop environment, useful software, update facilities, the kernel, et cetera.

However, with all features I can think of for an OS itself, most of these are the domain of one of these upstream projects e.g. everything I can see on the screen is GNOME, and will always be GNOME even if I switch to a different distribution with GNOME enabled.

So, apart from an installer and an update capability, what is Ubuntu in the context of what features are those which are implementable by the developers?

---

### Post by PriceChild on 2007-07-12
[LIST=1]
[*]The way it all fits together - ie debs
[*]The defaults
[*]small, important bits like easy codec instillation & restricted manager
[*]the community[/LIST]and probably loads more that i've over looked.

---

### Post by @trophy on 2007-07-12
> **Game_boy said:**
> I understand what Ubuntu is, as a Linux distribution: it includes a desktop environment, useful software, update facilities, the kernel, et cetera.

However, with all features I can think of for an OS itself, most of these are the domain of one of these upstream projects e.g. everything I can see on the screen is GNOME, and will always be GNOME even if I switch to a different distribution with GNOME enabled.

So, apart from an installer and an update capability, what is Ubuntu in the context of what features are those which are implementable by the developers?

I don't know, but the installer and the update capability are why I use Ubuntu.  Yum sucks.  Period.  It forgets what it's doing halfway through updates and I've had it brick a couple of machines before.  Ubuntu's updater, on the other hand, has never once failed me.  :hugs the updater:

---

### Post by Engnome on 2007-07-12
umm painting everything brown? :) The restricted drivers managers maybe? patching the kernel with non free drivers?

---

### Post by ThinkBuntu on 2007-07-12
> **@trophy said:**
> I don't know, but the installer and the update capability are why I use Ubuntu.  Yum sucks.  Period.  It forgets what it's doing halfway through updates and I've had it brick a couple of machines before.  Ubuntu's updater, on the other hand, has never once failed me.  :hugs the updater:
Debian has an identical updater.

---

### Post by @trophy on 2007-07-12
> **ThinkBuntu said:**
> Debian has an identical updater.

Yes, but does it come in brown? :wink:

---

### Post by az on 2007-07-12
> **Game_boy said:**
> I understand what Ubuntu is, as a Linux distribution: it includes a desktop environment, useful software, update facilities, the kernel, et cetera.

However, with all features I can think of for an OS itself, most of these are the domain of one of these upstream projects e.g. everything I can see on the screen is GNOME, and will always be GNOME even if I switch to a different distribution with GNOME enabled.

So, apart from an installer and an update capability, what is Ubuntu in the context of what features are those which are implementable by the developers?

Good question.

Upstream is a moving target and often, the individual pieces don't fit well together without help.  A distro is a community of people who maintain a bunch of packages.  The software itself is in source form.  To run it, you need to compile it.  The distro takes care of that and provides the end-user with a binary version of the software.

They take one version of each piece of software, fix it up, release it and support it.

To make all the apps work together, they often need tweaking.  Along with tweaking, there needs to be a clear line of responsibility to keep an eye out for upstream bug fixes and security issues.  Can you think of what a nightmare it would be to have to keep track of all the bugs and security issues for all the packages by yourself?

So that's what maintaining and supporting the software is.  The distro team also can contribute to upstream development.  Ubuntu's installer was headed by Colin Watson, who was also the person who wrote (mostly) the current installer for Debian.  Improvements made to the installer were brought to both distros at the same time.

Lot's of fun things are happening with Apt, too.  Those improvements will be brought back to Debian as well.

---

### Post by ThinkBuntu on 2007-07-12
Ubuntu is Debian's PR department :^)

I'll get a ton of flack from the Debian people for that one.

---

### Post by starcraft.man on 2007-07-12
> **ThinkBuntu said:**
> Ubuntu is Debian's PR department :^)

I'll get a ton of flack from the Debian people for that one.

ROFL!!! There's more to it than that think :p

As for the OP, if your degenerating things like the way you seem to think (i.e. how the majority of important packages/parts are developed upstream) you'll find lots of distributions that are just a repackaging of things (there are even distros that are solely repackaged Ubuntu with extra apps). In the end, every distro has it's own unique way of combining it all into one great package.

Think of it like soup, you have a whole pantry full of ingredients that came from farms and other growing plantations. Then you mix em up any way you like in your pot and make something that tastes great, and there isn't just one way of mixing just more and less popular ways. That should do it :).

---

### Post by FoolsGold_MKII on 2007-07-12
Ubuntu is the whole experience, which isn't just about the software itself, but also includes this community and forum.

---

### Post by Sporkman on 2007-07-13
> **FoolsGold_MKII said:**
> Ubuntu is the whole experience, which isn't just about the software itself, but also includes this community and forum.

I also like the "software for the people of the world" theme.

---

### Post by Erunno on 2007-07-13
Ubuntu is mostly a marketing machine which doesn't really contribute awfully much to upstream or Linux in general. At least RedHat and Novell pay a lot of upstream developers (Kernel, GNOME, KDE, X, etc) while Ubuntu mostly develops for itself and leeches other distributions effort.

---

### Post by rajeev1204 on 2007-07-13
> **az said:**
> Good question.

Upstream is a moving target and often, the individual pieces don't fit well together without help.  A distro is a community of people who maintain a bunch of packages.  The software itself is in source form.  To run it, you need to compile it.  The distro takes care of that and provides the end-user with a binary version of the software.

They take one version of each piece of software, fix it up, release it and support it.

To make all the apps work together, they often need tweaking.  Along with tweaking, there needs to be a clear line of responsibility to keep an eye out for upstream bug fixes and security issues.  Can you think of what a nightmare it would be to have to keep track of all the bugs and security issues for all the packages by yourself?

So that's what maintaining and supporting the software is.  The distro team also can contribute to upstream development.  Ubuntu's installer was headed by Colin Watson, who was also the person who wrote (mostly) the current installer for Debian.  Improvements made to the installer were brought to both distros at the same time.

Lot's of fun things are happening with Apt, too.  Those improvements will be brought back to Debian as well.


Very nicely explained sir , Iam also grateful to the OP for asking this question.

Once again thank you AZ

---

### Post by sonny on 2007-07-13
AZ answer is correct, but he missed one tiny part which is choice. Every distro has what the developers think is the right way to go, I mean, in Linux world it's not strange that you have 2 or 3 projects (sometime even more, way more) to do the same thing and the developers choose what they think is the propper technology to go; for example, sme of the older guys remember that 3 years ago was a debacle about X system management, and some distros had Xfree system and other would load with the X.org technology, and it didn't matter they were Debian based. Packaging is the difference that everyone notice, but under the hood there's ton's of little changes, for example, not so long ago most of the Distros came with OpenOffice 1.X and very few with OpenOffice 2.X or they had Koffice, little diferences like that makes a big diference, from using the stable release of the kernel or having the unstable, using xorg or xfree, having propietary drivers or not, using the 2.6.22 kernel with a Xfree system or the 2.6.20 with xorg. The combinations are practically endless, that's why every distro performs different, plus the tweaks that the devs have to make to put it all together.

---

### Post by mdsmedia on 2007-07-13
> **Erunno said:**
> Ubuntu is mostly a marketing machine which doesn't really contribute awfully much to upstream or Linux in general. At least RedHat and Novell pay a lot of upstream developers (Kernel, GNOME, KDE, X, etc) while Ubuntu mostly develops for itself and leeches other distributions effort.ummm....BS

---

### Post by Extreme Coder on 2007-07-13
> **az said:**
> Good question.

Upstream is a moving target and often, the individual pieces don't fit well together without help.  A distro is a community of people who maintain a bunch of packages.  The software itself is in source form.  To run it, you need to compile it.  The distro takes care of that and provides the end-user with a binary version of the software.

They take one version of each piece of software, fix it up, release it and support it.

To make all the apps work together, they often need tweaking.  Along with tweaking, there needs to be a clear line of responsibility to keep an eye out for upstream bug fixes and security issues.  Can you think of what a nightmare it would be to have to keep track of all the bugs and security issues for all the packages by yourself?

So that's what maintaining and supporting the software is.  The distro team also can contribute to upstream development.  Ubuntu's installer was headed by Colin Watson, who was also the person who wrote (mostly) the current installer for Debian.  Improvements made to the installer were brought to both distros at the same time.

Lot's of fun things are happening with Apt, too.  Those improvements will be brought back to Debian as well.
That's nice and all, but there's one thing I want to say ;) :
at the beginning of development of each release, doesn't Ubuntu take all the packages from Debian first? I've read about that a lot, can't remember where though :/

---

### Post by Erunno on 2007-07-13
> **mdsmedia said:**
> ummm....BS

I'm glad you took your time for this well thought out rebuttal. I hope you didn't overstrain yourself.

---

### Post by hanzomon4 on 2007-07-13
> **Erunno said:**
> Ubuntu is mostly a marketing machine which doesn't really contribute awfully much to upstream or Linux in general. At least RedHat and Novell pay a lot of upstream developers (Kernel, GNOME, KDE, X, etc) while Ubuntu mostly develops for itself and leeches other distributions effort.

Utter BS....


Edit:Missed mdsmedia's post, I agree

---

### Post by Epilonsama on 2007-07-13
> **Erunno said:**
> Ubuntu is mostly a marketing machine which doesn't really contribute awfully much to upstream or Linux in general. At least RedHat and Novell pay a lot of upstream developers (Kernel, GNOME, KDE, X, etc) while Ubuntu mostly develops for itself and leeches other distributions effort.

Is that so?
[http://akademy2007.kde.org/sponsors/](http://akademy2007.kde.org/sponsors/)

[http://www.guadec.org/sponsors](http://www.guadec.org/sponsors)

I could continue searching but saying the canonical doesn't fund free software is BS and FUD.

---

### Post by az on 2007-07-13
> **Extreme Coder said:**
> That's nice and all, but there's one thing I want to say ;) :
at the beginning of development of each release, doesn't Ubuntu take all the packages from Debian first? I've read about that a lot, can't remember where though :/

Well, the topic was not really about Ubuntu's relationship with Debian.  Ubuntu is a Debian derivative.  As such, they start off with packages from Debian unstable, pick a subset of them (a very small number in comparison to what is in all of Debian) and support them - which means all the work that you would expect to tweak and fix up the package.

Ubuntu can release a lot faster than Debian because they only support a small number of packages.  Ubuntu gives back the work they do to Debian.  For example, most of the work to transition from Xfree86 to Xorg was done by Ubuntu.  Lots of work on the debian installer was done by Ubuntu.  Gnome is up-and-running in Ubuntu before Debian.  There are plenty of other examples.  It's not a one-way relationship.

---

### Post by Xoldie on 2007-07-13
Hi you all,

Reviewing the posts in this thread I see that most of the approaches are sentiment-oriented  more than reason-oriented. Not that a sentiment-oriented approach is a bad thing. I'm not diminishing such an approach in any way. But the analysis of the subject will remain biased and uncompleted if some reason-based view is not attempted.
An OS is a technical and a business issue. There is no place for sentiment there. 
You will not hesitate to affirm the truthfulness of this assertion if the OS were one on the “dark side”. 
But here with Ubuntu we are on the “light side”, on the side of justice, freedom, equality and brotherhood. A position heavily loaded with sentiment.
So, a counterpoint paradigm of evil versus good, profit seekers versus justice seekers, sinners versus righteous, etc. etc., is established. Sentiment is king here.
But, an OS still is just a technical and business issue. Nothing more than that. Its just a tool, either on the “dark side” or on the “light side”. Just a tool. A productivity enhancement tool. 
In my opinion both sides are driven by profit making in last analysis. And that is good !! Other forms of civilization advancement are still to be found out.
Profit making is not the issue to pinpoint. 
The OS from the “dark side” is the result of monopoly, the only way to successfully market an evidently flawed product achieving market share levels not heard in any other branch of commerce.
It is the monopoly that  we have to fight.
And the fight have to be based on quality. 
Unix has already proven its intrinsic quality and is widely used in enterprise large scale data centre environments. The monopoly is retreating somehow there. At the same time the quality of “dark side” OS components has increased tremendously along the last few years in such a field, under the impulse of competence..
It is in desktop environments that the monopoly is by large still the strongest side.  
And the motives for the Linux desktop, in whatever the many flavors available out there,  to be largely behind its “dark side” counterpart are absolutely NOT related to sentiments. It is just strictly a matter of lack of maturity of the product and of the organization of business and technical substrates, layers and corners around the product. 
Let me take the liberty to use a little of hyperbolic thinking here. Suppose that each Linux desktop distribution is a feudal city, surrounded by a high wall. The wall is built at the external boundaries of the software repositories for said distribution. Within the walls the community flourished around the guidelines set for by the foundation fathers, the creators of the distribution. So, flourishment results biased along the lines of the specialized capabilities that where inextricable part of the act of creation of the distribution.
The limits and unicity of the repositories behaves as a restriction to get in touch with other feudal cities (other distributions). The result is a slow pace of development, of intellect growth, of “civilization” expansion. Great sentiments. Not enough efficiency.
A renaissance is needed, an explosion of advancement, a breaking of the dams presently isolating the communities, that is the true interchangeability of software between and among cities (distributions). That will move the history from feudal ages to modern globalization. 
Believe me, do not be misguided, it is not a matter of sentiments.

Best regards to all

---

### Post by stepan2 on 2007-07-13
one think thats special for ubuntu is that it has an optimised kernel that allows more computers to use the OS. From what i know , it has an acpi patch. On every dsitro except this i had to do pci=nommconf to boot. before this , i did acpi=off and for some reason my usb devices didnt work!

---

### Post by Erunno on 2007-07-14
> **Epilonsama said:**
> Is that so?
[http://akademy2007.kde.org/sponsors/](http://akademy2007.kde.org/sponsors/)

[http://www.guadec.org/sponsors](http://www.guadec.org/sponsors)

I could continue searching but saying the canonical doesn't fund free software is BS and FUD.


Great, so Canonical sponsors conferences which I never disputed in the first place. And now I'm sure you can explain me what this has to do with Canonical not paying any upstream developers on trans-distributional (does the word exist at all?) projects, at least not close to the amount (if at all) RedHat and Novell does? A gut feeling tells me that it's far more expensive to pay a bunch highly skilled software engineers than to sponsor one or two yearly conferences.

---

### Post by az on 2007-07-14
> **Erunno said:**
> And now I'm sure you can explain me what this has to do with Canonical not paying any upstream developers on trans-distributional (does the word exist at all?) projects, at least not close to the amount (if at all) RedHat and Novell does? 

Who cares?  Canonical employs a very small number of people.  They do quite an impressive amount of development and a lot of it finds it's way upstream.

> **Erunno said:**
> 
A gut feeling tells me that it's far more expensive to pay a bunch highly skilled software engineers than to sponsor one or two yearly conferences.

This is not a peeing contest.  How many other distributions are working on integrating distributed revision control so that patches and bug fixes that go into one distro (like Ubuntu) find their way into all other distros?  

I don't think you can hold a conversation about the free software community if you chose to use words like "leech".  You cannot possible argue that Canonical are not good free-software community citizens.  You should check your facts.

---

