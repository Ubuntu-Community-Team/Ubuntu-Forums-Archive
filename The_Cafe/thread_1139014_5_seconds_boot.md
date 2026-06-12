---
title: "5 seconds boot"
date: 2009-04-26
forum: The Cafe
---

### Post by Framp on 2009-04-26
yesterday i found a boot replacement for arch linux and i was amazed.. O_o

check this out:
[http://translate.google.it/translate?prev=hp&hl=en&js=n&u=http%3A%2F%2Fadrinux.wordpress.com%2Fquick-init%2F&sl=it&tl=en](http://translate.google.it/translate?prev=hp&hl=en&js=n&u=http%3A%2F%2Fadrinux.wordpress.com%2Fquick-init%2F&sl=it&tl=en)
5 seconds from grub to x, on a common pc!

i think it's quite interesting and it would be cool if something similar got implemented in ubuntu

actually i was wondering why nobody have thought of it before..
i don't know a lot about boot implementations, but it looks like this guy have parallelized boot daemons in order to achieve speed.. and it's working!

just wanna to share this piece of information.. (hoping that ubuntu follows this direction :) )

bye :)

EDIT: that's better :P
[http://translate.google.it/translate?prev=hp&hl=en&js=n&u=http%3A%2F%2Fadrinux.wordpress.com%2F2009%2F04%2F25%2Ffinit-arc-fast-init-for-archlinux-01-beta-version%2F&sl=it&tl=en](http://translate.google.it/translate?prev=hp&hl=en&js=n&u=http%3A%2F%2Fadrinux.wordpress.com%2F2009%2F04%2F25%2Ffinit-arc-fast-init-for-archlinux-01-beta-version%2F&sl=it&tl=en)

---

### Post by Framp on 2009-05-03
yawn, nobody cares :p

just wanna make somebody know

---

### Post by gn2 on 2009-05-03
Boot times are pretty irrelevant unless you are someone who is *extremely* impatient.

---

### Post by Pasdar on 2009-05-03
> **gn2 said:**
> Boot times are pretty irrelevant unless you are someone who is *extremely* impatient.
When I heard Shuttleworth say that they are again going to waste lots of their time on making Ubuntu Karmic boot faster than Jaunty, I thought OMG... these people have no idea what the correct priorities are.

Having a fast DE is a thousand times more important than a faster boot time. Many ATI users have a lag of 1-2 secs with everything when Compiz is enabled, it annoys the hell out of them. This is what makes/kills an OS, not how fast it can boot to the DE.

---

### Post by DMcA on 2009-05-03
actually, I believe quick boot times should be a priority, although not the only one of course. I don't see why modern computers should take so long to do relatively basic tasks. People don't write as efficient code as they used to

---

### Post by Pasdar on 2009-05-03
Boot up time should always be on their priority list, but whether it was a 1 sec boot up time or 20 seconds, will neither make or break Ubuntu. What will really make it is if Ubuntu cooperates with either GNOME or KDE and make their DEs better faster, less bugs, etc.

When normal users compare their experience of Ubuntu against, lets say VISTA. They rarely even mention the boot up time. They mention how fast programs opened and how easily they found/installed something, how well it worked out of the box, etc. That is, unless there is a dramatic difference in boot up time.

Jaunty boot up time is good as it is for now. They need to focus on the DE so when I run the packagae manager in GNOME, it doesn't take me 2+ secs to load, 3-4 seconds to check for updates, 4+ seconds to shut down the updater again. This is total B/S for any modern OS. If Windows ever released something like this for the price they're selling it, they would have lost a significant portion of their market.

---

### Post by Hakimio on 2009-05-03
Here some more articles for those interested in fast boot:
[LPC: Booting Linux in five seconds](http://lwn.net/Articles/299483/)
[Linux boot in 3 seconds](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fwww.lineo.co.jp%2Fproducts-services%2Fservices%2Fwarp.html&sl=ja&tl=en&history_state0=)

---

### Post by RATM_Owns on 2009-05-03
[http://aur.archlinux.org/packages.php?ID=25159](http://aur.archlinux.org/packages.php?ID=25159)

---

### Post by xnef1025 on 2009-05-03
I'd have to respectully disagree with boot times not being an important priority.  More and more people are using their computers more like appliances, particularly their laptops/netbooks.  They turn them off when they aren't using them and turn them on just to check if an email has come, print a document, or get one file.  These users are quickly becoming the majority.  Shaving boot time off of systems also would help businesses in general.  Real world example:  I work in a customer service call center.  We have to be alotted 10 minutes of our day, everyday, for starting up our computers.  That's probably around 3 calls going unanswered per rep.  Multiply by a thousand employees, and you are talking a lot of calls kept holding everyday because the reps are busy waiting on the computers.

---

### Post by Dr Small on 2009-05-03
I have a very fast boot time (around 15 seconds), but I only ever reboot if there is a problem with the system (very rare, but it happens around every 100 days) or there is a loss of power.

Fast boot times are nice, but I don't reboot my system enough to worry about it. I would much rather have a slick system and a slow boot time that a fast boot time and a bloated/slow system.

Just my 2 cents.
Dr Small

---

### Post by sertse on 2009-05-03
Gosh, stop this either one or the other nonsense.

Boot times are important for only to a certain extent, then its only nice to have, but not essential. Personally my systems (Ubuntu and Debian etc) will boot between 15-30 secs and I'm happy with that - it no longer "frustrating" me. Sure a 5 sec boot is great, but that'll only be a bonus. 

Like others, I care more whether it is slow during use. How long an app take to open up, whether switching apps is jerky, do I get an quick response from pressing a button etc.

---

### Post by Phreaker on 2009-05-03
How does this work ?

---

### Post by Pasdar on 2009-05-03
> **xnef1025 said:**
> I'd have to respectully disagree with boot times not being an important priority.  More and more people are using their computers more like appliances, particularly their laptops/netbooks.  They turn them off when they aren't using them and turn them on just to check if an email has come, print a document, or get one file.  These users are quickly becoming the majority.  Shaving boot time off of systems also would help businesses in general.  Real world example:  I work in a customer service call center.  We have to be alotted 10 minutes of our day, everyday, for starting up our computers.  That's probably around 3 calls going unanswered per rep.  Multiply by a thousand employees, and you are talking a lot of calls kept holding everyday because the reps are busy waiting on the computers.
So the 19 seconds boot up time of Jaunty is still not enough to fit your 10 minutes allotted time to boot up your system and you want Canonical to keep putting boot up time on priority one? Owwwkay.... Even if theoretically the boot up time was 10 minutes in your business it would still fit your boot up allotted time. You could even ask the first person that gets in to walk past all computers and turn them on before everyone else arrives.

What is more important is that once that PC is on and the OS is running, that everything goes fast. People get more annoyed when they have to wait on the phone talking to the helpdesk because it takes him a long time opening closing programs/searching things, rather than they that they can only call you from 8:10 AM and not from 8:00AM, lol. In fact, they couldn't care less.

---

### Post by Pasdar on 2009-05-03
Also check this topic: [http://ubuntuforums.org/showthread.php?t=1147070](http://ubuntuforums.org/showthread.php?t=1147070)

KDE 4.X is definitely much faster than GNOME.

---

### Post by mips on 2009-05-03
> **Pasdar said:**
> Also check this topic: [http://ubuntuforums.org/showthread.php?t=1147070](http://ubuntuforums.org/showthread.php?t=1147070)

KDE 4.X is definitely much faster than GNOME.

It's even faster with QT 4.5.

---

### Post by LightB on 2009-05-03
> **Pasdar said:**
> They need to focus on the DE so when I run the packagae manager in GNOME, it doesn't take me 2+ secs to load, 3-4 seconds to check for updates, 4+ seconds to shut down the updater again.

If you're talking about synaptic, this is ridiculous.

---

### Post by Kareeser on 2009-05-03
> **Pasdar said:**
> They need to focus on the DE so when I run the packagae manager in GNOME, it doesn't take me 2+ secs to load, 3-4 seconds to check for updates, 4+ seconds to shut down the updater again. If Windows ever released something like this for the price they're selling it, they would have lost a significant portion of their market.

Hm. I figured it would be par for the course.

Ever checked out how long it takes for the list of programs in "Add/Remove Programs" to render?

Ironically, it's a very similar example. :)

---

### Post by MikeTheC on 2009-05-03
Au contraire, folks, boot time is important and significant, even if it's mostly for psychological reasons. Besides, this is the modern age, and there are strategies (heck, Fedora is using some of them) to drop the boot time from Grub to log-in to 20 seconds.

For that matter, on an Intel-based Mac, Mac OS X only take about 25-30 to get to the desktop. It's just a matter of optimizations, people. It's nothing to turn your nose up at.

Likewise, I agree that Gnome, KDE and probably even XFCE all could use some optimizations. They can drag a** and it's within reason and our technological capabilities to do that as well.

---

### Post by LightB on 2009-05-03
The new ubuntu seems to boot for me pretty close to 5 seconds already, so what are people talking about? If ubuntu would boot that fast from now on without regressions, I would say it's good enough. Any further hacking just to speed that up is going to burn out other areas. For instance, it doesn't impress me much that the framebuffer terminals often just don't work right and sometimes even cause the display to blow up (this happens on the new ati driver). It's clearly due to heavy ubuntu hacks that aren't related to debian at all or any other distro. So I say hack away but do it overall not just the showy stuff zealots vote for.

---

### Post by toupeiro on 2009-05-03
There are some people who never reboot their machines (or, only in the rare circumstance that they receive an update which requires them to reboot ..eventually)  To those people, boot times are less important.  Some people turn their computers off every night for power savings and overall system longivity (point of debate aside).   To those people, boot times are a bit more important.  I've historically kept my machine on all the time, but with a 10 second POST, and a 4 second boot, I really don't care at all anymore. I move anything I ran that required 24/7 off of my desktop. I don't hybernate because it takes longer to resume from hybernation than it does to boot.. (THIS they should have sped up)

Its important, and people do care, contrary to what post #2 in this thread thinks.  Any improvements in boot time or hybernation time should be considered priority improvement.

---

### Post by mips on 2009-05-03
> **LightB said:**
> For instance, it doesn't impress me much that the framebuffer terminals often just don't work right and sometimes even cause the display to blow up (this happens on the new ati driver). It's clearly due to heavy ubuntu hacks that aren't related to debian at all or any other distro.

That might be a ATI problem and not a Ubuntu one.

---

### Post by Saint Angeles on 2009-05-03
> **Kareeser said:**
> Hm. I figured it would be par for the course.

Ever checked out how long it takes for the list of programs in "Add/Remove Programs" to render?

Ironically, it's a very similar example. :)
4 seconds (i just timed mine);) and most of it was "dependency generation" which is extremely important. this is far more advanced than the "add/remove programs" crap in windows (which I can say often takes forever to load and sometimes, deleted programs will still show up in it even after they are "uninstalled" from the system)

but my perspective is that they've already focused a LOT of their time getting Jaunty's boot time to a ridiculously low number of seconds... whats the point of spending more time (and resources) shaving off an additional 5 seconds when there is so much more important stuff that needs to be added to Karmic (a new theme anyone?)

and shouldn't they be working on that horrible intel graphics problem thats plaguing many users?

---

### Post by skymera on 2009-05-03
5 second boot seems nice.

But with a peak read of 3MB/s? Wow. So at most it could read 9MB.

Hardly a usable desktop.

---

### Post by SomeGuyDude on 2009-05-03
> **gn2 said:**
> Boot times are pretty irrelevant unless you are someone who is *extremely* impatient.

Most things we focus on with our systems are pretty irrelevant. How many times do we see people bragging that their OS can run off a 256mb flash drive when it's on a computer with a 200gb HD with 3gb of RAM in it?

Part of the Linux endeavor is seeing what is POSSIBLE with an OS.

---

### Post by Jordanwb on 2009-05-03
> **DMcA said:**
> actually, I believe quick boot times should be a priority, although not the only one of course. I don't see why modern computers should take so long to do relatively basic tasks. People don't write as efficient code as they used to

+10^100000000

The main thing that slows down my boot sequence is the motherboard. It takes so long to get to Grub. Grrrr. Never getting an Asus mobo again.

---

### Post by LightB on 2009-05-03
> **mips said:**
> That might be a ATI problem and not a Ubuntu one.

I've seen fb issues on several PCs over the years from the first time I tried Ubuntu. They didn't all have ATI video. It's clear the fb is hacked somehow, probably related to the splash screen, but I was never able to put my finger on it. No other distros I've tried behave in this way.

---

### Post by Kareeser on 2009-05-03
> **Saint Angeles said:**
>  whats the point of spending more time (and resources) shaving off an additional 5 seconds when there is so much more important stuff that needs to be added to Karmic (a new theme anyone?)

and shouldn't they be working on that horrible intel graphics problem thats plaguing many users?

There are some that would say a new theme for Karmic is a waste of developer talent ;)

I'm not one of then, but I'm just sayin'.

The only excuse I've heard to explain the regressions is that "cutting edge Ubuntu releases are designed for top-notch computers with an eye towards backwards compatability. If you are experiencing regressions, your technology is too old".

Except, my 3 year old laptop is not too old, I'd think. *sigh*

---

### Post by mikechant on 2009-05-14
People saying 'I get 5 seconds boot time, who cares' should realize that other people have different equipment and different needs.

For example, I'm quite happy with the Jaunty boot times on my Dell desktop, and if I want a faster startup I can use suspend to RAM. 

But my eeePC netbook is a different matter. I don't want to use suspend on it because (acording to the hardware manual, presumably due to the small heat generation) I shouldn't put it in the soft case supplied while suspended, only while off.
The boot time in the supplied Xandros is 14s to login and then less than 5s to desktop.

I want to switch to Jaunty - it gives better wifi performance among other advantages - but the boot time is about 25s to login and then nearly another 25s from login to desktop. This is significant when you just want to check email or do a quick web search.

I only installed Jaunty yesterday so I'm hoping to optimize it a bit by turning off unnecessary services etc. but previous experience suggests this will only shave a few seconds.
I would hope that Ubuntu could at least approach Xandros's boot+ login time e.g. total in the range 20-30 secs rather than 50 secs.

---

### Post by Orlsend on 2009-05-14
> **Framp said:**
> yesterday i found a boot replacement for arch linux and i was amazed.. O_o

check this out:
[http://translate.google.it/translate?prev=hp&hl=en&js=n&u=http%3A%2F%2Fadrinux.wordpress.com%2Fquick-init%2F&sl=it&tl=en](http://translate.google.it/translate?prev=hp&hl=en&js=n&u=http%3A%2F%2Fadrinux.wordpress.com%2Fquick-init%2F&sl=it&tl=en)
5 seconds from grub to x, on a common pc!

i think it's quite interesting and it would be cool if something similar got implemented in ubuntu

actually i was wondering why nobody have thought of it before..
i don't know a lot about boot implementations, but it looks like this guy have parallelized boot daemons in order to achieve speed.. and it's working!

just wanna to share this piece of information.. (hoping that ubuntu follows this direction :) )

bye :)

EDIT: that's better :P
[http://translate.google.it/translate?prev=hp&hl=en&js=n&u=http%3A%2F%2Fadrinux.wordpress.com%2F2009%2F04%2F25%2Ffinit-arc-fast-init-for-archlinux-01-beta-version%2F&sl=it&tl=en](http://translate.google.it/translate?prev=hp&hl=en&js=n&u=http%3A%2F%2Fadrinux.wordpress.com%2F2009%2F04%2F25%2Ffinit-arc-fast-init-for-archlinux-01-beta-version%2F&sl=it&tl=en)

How long from the bios to X?

---

