---
title: "Has anything come out of Automatix/EasyUbuntu?"
date: 2007-12-30
forum: The Cafe
---

### Post by altonbr on 2007-12-30
I remember using Automatix when I didn't know what I was doing in 5.10 and 6.06 but I've quickly learned and actually have my own, similar script that installs all the programs I need on my own, my family's and my neighbour's computers.

I decided to look back at EasyUbuntu (which I never used) and Automatix and saw that Automatix was still kicking strong while EasyUbuntu said their project was defunct because Ubuntu now has no use for such a project.

I also found it interesting that Automatix was a fork of an early EasyUbuntu script ([http://easyubuntu.freecontrib.org/HtmlDocs/ch07.html](http://easyubuntu.freecontrib.org/HtmlDocs/ch07.html)), especially to see where they both forked to in the end. I really would like to see the original Automatix however, when it was still bash and zenity and not bash and PyGTK, especially after reading this review because by the time I saw Automatix and EasyUbuntu, I saw it quite the opposite: [http://citfab.blogspot.com/2006/08/easyubuntu-vs-automatix.html](http://citfab.blogspot.com/2006/08/easyubuntu-vs-automatix.html)

Anyway, I was wondering if anything has come from Automatix or EasyUbuntu as in Brother MFC printer fixes, firewire permission fixes, getting Compiz to run on blacklisted GPUs when really it works, the merging of Add/Remove and Automatix, negating the need for Automatix, backup services, performance optimizations, using a official wine repository instead of a official ubuntu wine repository (faster response to product updates) etc.

It just seems like a lot of apps out there do one thing and one thing only until their need is negated. Example: Till Kamppeter writing a Ubuntu port for printerdrake (system-config-printer). 

It seems to me, programs like Automatix, are temporary solutions until the real developers handle the problems. Why doesn't Automatix include GConf editing like mintDesktop. Why is there even a mintDesktop program? It should get included into a preference optionin System > Preferences > Appearance > Desktop Icons. Or what about enabling 'sysinfo' by default so people can see the specs on their computer? Or what about right-clicking on the trash can and running "Secure Empty Trash" instead of just "Empty Trash".

I just hope we're not all wasting our energy writing our own little scripts and software instead of collaborating these ideas into a conglomerated package.

I guess that's what Ubuntu is trying to do and the reason why there are forks: aka Linux Mint.

---

### Post by erfahren on 2007-12-31
I used EasyUbuntu when I first started out and liked it better that Automatix. I was a newbie at that time but just trusted it more because it seemed more basic, easier to understand, and therefore potentionally less problematic for my inexperienced hands.

I don't have an install script but just made a list of the package names of the apps that I install. I can just select, copy and paste the ones I want into the command line. 

What I think would be a good idea is have more "friendly" return errors for newbies when installing from the command line (or through Synaptic) - instead of just "package is uninstallable" type thing it could also return with "please check your software sources" and/or "see online documentation on enabling repositories".

I know that the developers of Automatix put a lot of work into it and filled a need at the time (and meant well), but I'm not sorry to see it go. I think some new users still hear of it and feel they need it and in turn consider installing apps without it is more difficult than it really is.

I remember that Synaptic Package Manager was really daunting to me at first. There's so many esoteric packages in it. Being used to using FOSS and freeware on Windows I quickly realized that most Linux apps I came across on the internet might be available through it. I see the occasional new person ask about compiling a program that's already in the repos. 

I think Synaptic could use a better filter on it to filter out the compiling tools, utilities, etc. so that when someone selects the "games" section (for example) then only the games will show without the developing tools, etc. showing. (The filter might already be able to be set to do that, maybe I just haven't looked at it enough.)

I think having something like EasyUbuntu is still viable though. a script that would automatically test the sources.list and add the Medibuntu repository (and key) to get the non-free packages would save newbies some time and confusion (and also the experienced users the time it takes to explain it to them).

I'm kind of surprised the developers of Automatix kept it up as long as they have. Maybe they feel the way you were alluding to though, they don't want all their work be for naught.

---

### Post by gn2 on 2007-12-31
I believe that Automatix highlighted a genuine need.

Would the ubuntu-restricted-extras metapackage have come into being if it wasn't for Automatix, or would we still have to add what I like to call the "useful missing bits" the hard way?

All the anti-Automatix stuff I read always saddens me, because without the work of it's developers I would have permanently abandoned Ubuntu a while ago.

So it's a big thankyou to the Automatix developers from me.

---

### Post by altonbr on 2007-12-31
> **erfahren said:**
> I think Synaptic could use a better filter on it to filter out the compiling tools, utilities, etc. so that when someone selects the "games" section (for example) then only the games will show without the developing tools, etc. showing. (The filter might already be able to be set to do that, maybe I just haven't looked at it enough.)

That's what Applications > Add/Remove... is for. What bothers me is the redundancy of the whole thing. Let Add/Remove be what it is while an Advanced tab be Synaptic...

I've found Ubuntu needs to merge a lot of its apps (and there is a corresponding Hardy blueprint for this), but in the meantime, this is a very good summary:
[URL="http://architectfantasy.com/?p=1"]
Ubuntu 7.10 Pragmatic Visual Presentation Critique I[/URL]
> Your average computer user might never say that they find the flicker at the start of the Operating System a bit daunting or cheap looking, but when they switch between an OSX desktop and a Linux desktop subconsciously the fluid interface does register in their mind. The result of that is all the praise we hear about the gorgeous OSX interface.

[Ubuntu 7.10 Pragmatic Visual and Behavioral Critique II]("http://architectfantasy.com/?p=25")
>    1. System->Preferences->Screen Resolution
   2. System->Administration->Screens and Graphics
...
   1. Applications->Accessories->Manage Print Jobs
   2. System->Administration->Printing
   3. System->Preferences-> Default Printer
...
   1. System->Preferences->Appearance-> “Customize Button”->Pointer Tab
   2. System->Preferences->Mouse
   3. System->Preferences->Universal Access->Keyboard Accessibility Preferences->Mouse “Keys”
...
   1. System->Preferences->Keyboard
   2. System->Preferences->Keyboard Shortcuts
   3. System->Preferences->Universal Access->Keyboard and Accessibility Preferences

...
   1. System->Preferences->Network Proxy
   2. System->Administration->Network
   3. System->Administration->Network Tools
...
   1. System->Administration->Update Manager
   2. System->Administration->Synaptic Package Manager
   3. System->Administration->Software Sources
   4. Applications->Add/Remove
...

> **gn2 said:**
> I believe that Automatix highlighted a genuine need.

Would the ubuntu-restricted-extras metapackage have come into being if it wasn't for Automatix, or would we still have to add what I like to call the "useful missing bits" the hard way?

All the anti-Automatix stuff I read always saddens me, because without the work of it's developers I would have permanently abandoned Ubuntu a while ago.

So it's a big thankyou to the Automatix developers from me.

Yeah, that's true and I agree. In my script, one of the first packages installed is ubuntu-restricted-extras.

At least we're pushing for the user with these kinds of programs eh? This allows us to see what the needs are of the user and then how we can implement them (safely and legally).

Two good articles to read on this are:

[Eric S. Raymond's "World Domination 201"]("http://www.catb.org/~esr/writings/world-domination/world-domination-201.html")
> The previous approaches had one thing in common: they attempt to avoid the conventional proprietary software approach of paying per-copy royalties for software binaries. We've gone to great lengths to avoid facing a simple unfortunate truth: Some IP holders insist on per-copy royalties. If they don't get them, they're quite prepared to sue. The current legal environment makes it likely they will win if they do.

This reality makes open-source hackers angry and nauseated. But no amount of anger, nausea, or denial will make it go away.

[Richard Stallman's rebuttal to "World Domination 201"]("http://www.libervis.com/static/richard_stallman_on_world_domination_201.html")
> Richard M. Stallman wrote:

To "argue" in favor of adding non-free software in GNU/Linux distros
is almost superfluous, since that's what nearly all of them have
already done. This reflects the general spinelessness of our
community. Most of its members have never heard the philosophy of
freedom and community which motivated the GNU Project to build the
community, and most care more about convenience than freedom.

As a result, we are in danger of heading for a big "success" in which
a non-free operating system that includes parts of GNU and Linux is as
popular as Microsoft Windows, and ethically no better.

People such as Raymond and Torvalds, who reject freedom as a goal,
might rejoice in that "success"--but as regards freedom, it would be a
failure. So count me out. I will keep on campaigning for freedom. 

---

