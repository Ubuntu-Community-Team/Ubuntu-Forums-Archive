---
title: "2011 course of the Ubuntu Studio?"
date: 2011-06-05
forum: Ubuntu Studio
---

### Post by sgx on 2011-06-05
I suggest that US focus on a live barebones distro, with synaptic, complete online/network/modem collection, jack2, RT kernel, solid 3D support, a few instrument and recording apps to verify working i/o, and let the user choose the rest. Offer a variety of meta-packages, for audio, video, print media, animation, and environment/window-manager.
Along with repositories and PPAs,
this would present many options, and once it was rock-sold, various
isos could be released, should there be a demand.

The constant migration to phantom greener pastures, seeking some holy grail, insures only disappointment for new users, and forums full of help requests.  8.04 was a fine release. It worked, without endless
configuration mysteries.

Thanks mainly to what I have learned here, I can put together a basic audio setup, using a barebones linux, one such setup uses Bodhi,
an E17 lightweight distro based on ubuntu/debian.

I added this kernel, linux-image-2.6.31-11-rt_2.6.31-11.154_i386.deb

and the desired audio apps and dependencies, from ubuntu repos, Falk and Autostatic PPAs, and debian ubstable repos.

It works well, many of the installs are done with dpkg -i xxx.deb

For dependencies, I just added the odd ducks, ones I knew from experience, were not standard system files. dpkg tells you if there are more needed files.

A solid, easily constructed Ubuntu Studio, would be very popular.
Cheers

---

### Post by dawiba on 2011-06-05
> **sgx said:**
> i suggest that us focus on a live barebones distro, with synaptic, complete online/network/modem collection, jack2, rt kernel, solid 3d support, a few instrument and recording apps to verify working i/o, and let the user choose the rest. Offer a variety of meta-packages, for audio, video, print media, animation, and environment/window-manager.
Along with repositories and ppas,
this would present many options, and once it was rock-sold, various
isos could be released, should there be a demand.

The constant migration to phantom greener pastures, seeking some holy grail, insures only disappointment for new users, and forums full of help requests. 8.04 was a fine release. It worked, without endless
configuration mysteries.

Thanks mainly to what i have learned here, i can put together a basic audio setup, using a barebones linux, one such setup uses bodhi,
an e17 lightweight distro based on ubuntu/debian.

I added this kernel, linux-image-2.6.31-11-rt_2.6.31-11.154_i386.deb

and the desired audio apps and dependencies, from ubuntu repos, falk and autostatic ppas, and debian ubstable repos.

It works well, many of the installs are done with dpkg -i xxx.deb

for dependencies, i just added the odd ducks, ones i knew from experience, were not standard system files. Dpkg tells you if there are more needed files.

A solid, easily constructed ubuntu studio, would be very popular.
Cheers

+1

Only differences for me are that I use regular Ubuntu with the programs I need installed from the repos and no RT kernel.

Everything works just fine.

---

### Post by cchhrriiss121212 on 2011-06-05
sgx, have you tried bringing this up on the [studio developers mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-devel")?

---

### Post by jejeman on 2011-06-05
If someone wants to "build" it's "own" ubuntu studio, one can always start with ubuntu mini.iso. And install what he/she needs.

+1 for more different meta packages.

I like US as it is now. It does not need to be live. You have puppy studio for that, or kxstudio.

---

### Post by sgx on 2011-06-05
> **cchhrriiss121212 said:**
> sgx, have you tried bringing this up on the [studio developers mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-devel")?
Hi, from what I read, they are implementing a good plan, if they keep it simple, and perfect one RT kernel, and one implementation of jackd,
with permissions defaulted properly, the rest should be easy. The more choices left for users, the more the
Studio developers can focus on a solid foundation. :)
Cheers

---

### Post by sgx on 2011-06-05
> **jejeman said:**
> If someone wants to "build" it's "own" ubuntu studio, one can always start with ubuntu mini.iso. And install what he/she needs.

+1 for more different meta packages.

I like US as it is now. It does not need to be live. You have puppy studio for that, or kxstudio.
I don't think making a bootable iso has any effect on the functionality
of an installed Studio, it's fairly standard for linux releases, I don't see any upside to reducing a potential new users ability to test, especially considering the limited choices of hardware that linux users deal with. To the extent that there is real competition among specialty studio distributions, the live option may be crucial for success.
(success not holding a traditional marketplace definition, in this case.)
Cheers

---

### Post by cchhrriiss121212 on 2011-06-06
That sounds promising, I can't say I've tried out the last 2 versions of Studio so I don't know what exactly has been changed. 

What do you think about Studio being built only from LTS releases? That sounds like it might be a good idea to me, as from what I have seen on the mailing lists, the devs have trouble making and testing a new distro every 6 months. All the chopping and changing going on with GUIs and kernels can't help either.

---

### Post by sgx on 2011-06-07
I would toss out both the cat and the dog, to end the fighting.
Just use a few components that are well tested to work together, add some unique themes/artwork, and press record :)
Release numbers are meaningless.

I think all the bad apple apps are now well known, if we can just resist promising world domination to frustrated windows refugees,
and present a clear set of expectations, we be :guitar:

---

### Post by cchhrriiss121212 on 2011-06-07
Studio being based on LTS (that means Long Term Support) versions would mean there was a release every 2 years, and not the current 6 month cycle. Then PPAs could be used for more up to date software.

---

### Post by sgx on 2011-06-07
> **cchhrriiss121212 said:**
> Studio being based on LTS (that means Long Term Support) versions would mean there was a release every 2 years, and not the current 6 month cycle. Then PPAs could be used for more up to date software.
Tying a recording studio to anything based on just a label is foolish.
A real recording studio uses gear that works, and keeps it until a known and tested quantity comes along that is significantly better.

Relying on LTS or any other jargon, is akin to letting the janitor come in and 'improving' the studio with gear gleaned from the flea market, and exchanging it at will.

We already have the things that work, so just give the place a paint job, a cozy couch, plug the cables in, and

LOCK THE FREAKIN DOORS :guitar:  :)

---

### Post by cchhrriiss121212 on 2011-06-08
I'm not talking about labels or jargon, I'm talking about changing the release cycle from 6 months to 2 years, don't you think that would make a difference?
But what you or I would like to see from the distro does not look likely to be implemented. From the[ wiki]("https://wiki.ubuntu.com/UbuntuStudio"):
> Our aim is to make it more accessible for new users to get into the  tools that GNU/Linux has to offer for multimedia creation and  production. We also want to spotlight what's out there, and show users  tools they might not know to exist. 
The whole focus of Ubuntu is to attract new users, and they do that by stuffing the ISO with software and releasing something often.

Stability or a minimal base to build up from might actually be more useful for people, but it won't attract new users.

---

### Post by fedexnman on 2011-06-08
interesting thread !! i had alot of success and xrun free  recording with ubuntu studio 9.10  and its rt kernel , it was really a solid ubuntu studio release . i wish i would of not deleted that partition , i use a firewire device and havent had the best luck with the newer releases , i  do use windows for audio too, its hard to ween off of windows , i know shame on me . i really love ardour and hydrogen though.  ****** i would rather see ubuntu studio only release solid releases  with good rt kernels and it does'nt have to keep up with ubuntu LTS release cycle , they can do there own 
LTS releases  *****

---

### Post by sgx on 2011-06-08
> **cchhrriiss121212 said:**
> I'm not talking about labels or jargon, I'm talking about changing the release cycle from 6 months to 2 years, don't you think that would make a difference?
But what you or I would like to see from the distro does not look likely to be implemented. From the[ wiki]("https://wiki.ubuntu.com/UbuntuStudio"):

The whole focus of Ubuntu is to attract new users, and they do that by stuffing the ISO with software and releasing something often.

Stability or a minimal base to build up from might actually be more useful for people, but it won't attract new users.

LTS = label
'release cycle' = jargon
or do I have it backwards? :wink:

even the Queen could jam with a stable minimalist distro :guitar: Distro builders as a whole, bewilder most of the new users, with meaningless or fluctuating naming schemes. Perhaps a moderator could compile a list of forum users with fewer than 20 posts, and no posts after the first month of joining the forum. 
( I do wish the Queen would quit shaving her goatee :) )

---

### Post by cchhrriiss121212 on 2011-06-09
> **sgx said:**
> LTS = label
'release cycle' = jargon
or do I have it backwards? :wink:

You don't have it backwards, you are just missing the point. I used these labels as a part of a larger talking point, I would like to discuss this point and not the language used to describe it. I will re-iterate that point minus any of these labels:

[I]Ubuntu Studio could release a new version every 2 years. This would reduce the number of bugs any new users will experience, and make troubleshooting easier on these forums. It would also users to get to grips with the software, and not the last minute changes found in regular Ubuntu. 

It would also mean develpoers had more time to sort out things like a working rt/low latency kernel, and eliminate more bugs. Currently, if something is broken, developers will often wait until the next release to fix it, then when the next release comes out something else breaks etc. [/I](Case in point, fedexnman's post below regarding firewire on newer releases)

> Distro builders as a whole, bewilder most of the new users, with  meaningless or fluctuating naming schemes. Perhaps a moderator could  compile a list of forum users with fewer than 20 posts, and no posts  after the first month of joining the forum. 
I really doubt that anyone stops using Ubuntu because of the naming schemes, the OS has far more obvious problems than that.

---

### Post by sgx on 2011-06-09
Perhaps the 'rolling release' model would work? This replaces an
arbitrary timeframe as upgrade decision maker, and allows a
critical mass of improvements, new apps, and bugfixes, to decide
when a new release should happen. In the interim, repositories are
updated, to the point where new users begin having issues with the first big update after the first install, as can be the case when a major revision of xorg, and C libraries, occurs in the same timeframe. This has worked well for pclinuxos, for 5 years or so.
Cheers

---

### Post by fedexnman on 2011-06-12
debian thats on a rolling release right ? i know  " av linux " is based on debian using remastersys and seems to becoming pretty popular , one of the forum members here " trulan "  uses it alongside ubuntu , and is helping out with the kernel for the next version .  like i said before i use firewire , so hopefully one day soon  we wont need a rt kernel and things will work ok with the generic or stock kernel so these 6 month releases wont be so dissapointing .

---

### Post by bluesscream on 2011-06-12
what does a us newbie really need?
A standard system easily to install, a set of standard audio/video/graphics production software,  a standard audio/midi basis implemented including codecs and flash properly interacting smoothly with jack and ffado ootb, actualized  3d-videodrivers for the top dog cards, a kernel with adjustable irq priorisation and lowlatency or realtime features. That's all. 
If one will be seduced and debauched, next step on the pathway of evil might be compiling bleeding edge apps alpha dev versions from git and svn, activating obscure ppa's, fiddling with git kernel-next customized  for preeempt... and the black hole will gobble them up completely...

---

### Post by sgx on 2011-06-13
integrating the best hardware detection is also crucial. I recently
tried remix_os distro, and it shot black screen blanks at an nvidia 9400 video card, with all the boot arguments and combos of them, tried on a monsoon day.

But it worked on an old P4 with just old motherboard video, so linux
hardware support as a whole, needs to improve, as the 9400 is also pretty old, and the video card makers are on a fast release cycle, with ever more complicated designs.
Cheers

---

