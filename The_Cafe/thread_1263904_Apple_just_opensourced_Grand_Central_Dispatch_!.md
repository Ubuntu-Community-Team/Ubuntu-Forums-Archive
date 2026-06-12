---
title: "Apple just opensourced Grand Central Dispatch !"
date: 2009-09-11
forum: The Cafe
---

### Post by artir on 2009-09-11
GCD is a technology that helps the developers to create multithreaded apps, letting the system do the threading instead of the individual apps.
Now it's licensed under the Apache License, and yes, it can be ported to Linux. 


[http://www.macresearch.org/grand-central-now-open-all](http://www.macresearch.org/grand-central-now-open-all)
[http://www.apple.com/macosx/technology/#grandcentral](http://www.apple.com/macosx/technology/#grandcentral)


Now.. why have they done that?

---

### Post by tubezninja on 2009-09-11
Maybe, just *maybe* they're not the evil closed-model overlords that some people on here have made them out to be?

---

### Post by dsavi on 2009-09-11
^ I am an Apple hater, but evil proprietary overlords they are not. If you say they are you're in denial.

---

### Post by schauerlich on 2009-09-11
> **scaredpoet said:**
> Maybe, just *maybe* they're not the evil closed-model overlords that some people on here have made them out to be?

IMPOSSIBLE! I even have a pamphlet about it!

---

### Post by Joeb454 on 2009-09-11
I've just checked Apple's [OpenSource site]("http://opensource.apple.com"), and I couldn't find it on there

---

### Post by Namtabmai on 2009-09-11
O.k. so rather than coding my applications to be multi-threaded, I should now code them to use GCD so that it can make them multithreaded?

Am I missing something?

---

### Post by schauerlich on 2009-09-11
> **Namtabmai said:**
> O.k. so rather than coding my applications to be multi-threaded, I should now code them to use GCD so that it can make them multithreaded?

Am I missing something?

Manually managing multithreaded-ness is a giant pain. GCD makes it much easier by letting libdispatch manage the creation and release of threads. That way, many more app developers will be much more likely to make their apps multi-threaded. All they have to do it make 2 or 3 calls to libdispatch before a block of code, and GCD does the rest.

---

### Post by RabbitWho on 2009-09-11
*cross your fingers for Final Cut Pro 7*

---

### Post by tubezninja on 2009-09-11
> **Namtabmai said:**
> O.k. so rather than coding my applications to be multi-threaded, I should now code them to use GCD so that it can make them multithreaded?

You can do what you want.  That *_is_* the great thing about FOSS.

---

### Post by tubezninja on 2009-09-11
> **Joeb454 said:**
> I've just checked Apple's [OpenSource site]("http://opensource.apple.com"), and I couldn't find it on there


Not sure exactly why it was done this way, but instead of being on the developer site, they put it in macosforge instead:

[http://libdispatch.macosforge.org/](http://libdispatch.macosforge.org/)

---

### Post by misfitpierce on 2009-09-11
> **EDavidBurg said:**
> IMPOSSIBLE! I even have a pamphlet about it!

Me too!

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-09-11
They are still a corporation which is focused on making profit and brainwashing people.
still evil...

---

### Post by phrostbyte on 2009-09-11
Awesome. Does that mean GNU C will support closures now? :)

This complimentary to OpenMP which is already supported. The open source community now has really good parallel development tools. Now we need to bring out those 4000 core processors the Linux kernel now supports. :D

---

### Post by Tibuda on 2009-09-11
They have contributed with CUPS for some time. I can't see them as evil, even if I don't use any of their products.

---

### Post by schauerlich on 2009-09-11
> **phrostbyte said:**
> Awesome. Does that mean GNU C will support closures now? :)

They'll be releasing their changes to GCC at some point soon (it's GPL'd after all), which means that it will support blocks/closures.

---

### Post by phrostbyte on 2009-09-11
> **danielrmt said:**
> They have contributed with CUPS for some time. I can't see them as evil, even if I don't use any of their products.

Yeah actual Apple technology is in every single Ubuntu CD. (like on the CD)

You can say Mono = Microsoft technology, but that isn't true. Mono is wholly developed outside of Microsoft (mostly by Novell).

My only real beef with Apple is their policy on forcing proprietary transfer protocols that you are forced to use iTunes to communicate with Apple devices. The end result Linux users can't sync to iPhone/new gen iPods (and Apple actively fights things that could result in Linux support, with legal threats). Which I find highly lame. =;

---

### Post by hanzomon4 on 2009-09-11
Apple protects the fruit but don't mind handing out the seeds. I mean a lot of the most important low level bits are open. Cups, Webkit, Objective-C(Gnustep), Xnu...

---

### Post by CoreyB. on 2009-09-11
[http://www.macresearch.org/grand-central-now-open-all]("http://www.macresearch.org/grand-central-now-open-all")

Is this something that will benefit Ubuntu or Linux as a whole?

---

### Post by VMC on 2009-09-11
> **CoreyB. said:**
> [http://www.macresearch.org/grand-central-now-open-all]("http://www.macresearch.org/grand-central-now-open-all")

Is this something that will benefit Ubuntu or Linux as a whole?

I think your in the wrong forum. This is for karmic issues. I don't see where that thread has any relevance.

---

### Post by Frak on 2009-09-11
> **EDavidBurg said:**
> IMPOSSIBLE! I even have a pamphlet about it!
I went to AppleOpenSourceCon and all I got was this crappy pamphlet.

---

### Post by inportb on 2009-09-11
Yeah... I don't think Karmic does GCD.

---

### Post by issih on 2009-09-11
> **hanzomon4 said:**
> Apple protects the fruit but don't mind handing out the seeds. I mean a lot of the most important low level bits are open. Cups, Webkit, Objective-C(Gnustep), Xnu...

Very well put....

Apple are a company, companies are a bit evil (its inevitable...even if you make your slogan pretend its not *stares hard at google*) but they are no where near as bad as some would like to make them seem.

They are no where near being saints, but there are far far worse sinners.

---

### Post by pelle.k on 2009-09-11
> even if you make your slogan pretend its not *stares hard at google*
LOL :D that looked funny in my head
> They are no where near being saints, but there are far far worse sinners. 
Well said!

---

### Post by CJ Master on 2009-09-11
> **&#1057 said:**
> They are still a corporation which is focused on making profit and brainwashing people.
still evil...

A corporation... trying to make PROFIT?! Blasphemy!

---

### Post by RiceMonster on 2009-09-11
This is good news. This technology sounds very good and I hope this gets ported to Linux (seems like it's going to!) and Linux developers make good use of it.

---

### Post by Frak on 2009-09-11
> **RiceMonster said:**
> This is good news. This technology sounds very good and I hope this gets ported to Linux (seems like it's going to!) and Linux developers make good use of it.
Same. This could really do some good for Linux overall.

---

### Post by DeadSuperHero on 2009-09-11
My day got a whole lot better after reading this.

Honestly, GCD was one of the reasons I was thinking of switching to Snow Leopard/Mac in general.
 
Buuut, if it's coming to Linux (and probably FreeBSD), then that's one less reason to switch.

---

### Post by xArv3nx on 2009-09-12
I'm guessing most users don't hate them (Apple) because of the proprietary products, but because of other reasons (company practices, similar to MSFT).

that's like me, i could really care less if they open source something or not. it doesn't really make them any better of a company. and the mac scene is disgusting (which is the REAL reason I left macs).

---

### Post by Regenweald on 2009-09-12
Apple's 64bit implementation is not as mature as Linux's so **IF** GCD is implemented in userspace or in the kernel it would be a great opportunity for apple to have a pretty large testing base and also a large free workforce testing/improving GCD. Flipside, FOSS gets new hotness and all round speed improvements. Win Win to me.

---

### Post by Exodist on 2009-09-12
> **Namtabmai said:**
> O.k. so rather than coding my applications to be multi-threaded, I should now code them to use GCD so that it can make them multithreaded?

Am I missing something?

I "ASSUME" if you also compile the application with GCD as well it will make the algorithm multi threaded. Else I am confused as well.

---

### Post by schauerlich on 2009-09-12
> **Mr. Psychopath said:**
> Honestly, GCD was one of the reasons I was thinking of switching to Snow Leopard/Mac in general.
 
Buuut, if it's coming to Linux (and probably FreeBSD), then that's one less reason to switch.

How did you escape from the facility?!

Now now, just come with me... we'll have you [s]brainwashed[/s] properly medicated in no time...

---

### Post by 3rdalbum on 2009-09-12
This seems like a step or two better than Python's "threading" module, but I can't see how it's "threading nirvana", because I can't understand how it solves race conditions without blocking threads.

---

### Post by Frak on 2009-09-12
> **3rdalbum said:**
> This seems like a step or two better than Python's "threading" module, but I can't see how it's "threading nirvana", because I can't understand how it solves race conditions without blocking threads.
When in doubt: magic.

---

### Post by Sporkman on 2009-09-12
> **EDavidBurg said:**
> IMPOSSIBLE! I even have a pamphlet about it!

:lol:

---

### Post by MikeTheC on 2009-09-12
As far as I am concerned, it's a good thing. I'm glad Apple has done this as it is quite the reverse of going the Software Patent direction.

Hooray for the good guys here, I think.

I may even crack open a can of [Boddington's](http://en.wikipedia.org/wiki/Boddingtons) over this!

---

### Post by chris200x9 on 2009-09-12
this is good but, will linux and gnu really add a non standard extension to c?

---

### Post by Frak on 2009-09-12
> **chris200x9 said:**
> this is good but, will linux and gnu really add a non standard extension to c?
That or face another fork war.

---

### Post by MikeTheC on 2009-09-12
> **chris200x9 said:**
> this is good but, will linux and gnu really add a non standard extension to c?

How is this any more non-standard than, say, SELinux? It's a new technological approach, and (if they have any sense) the F/OSS community will eventually perform their version of "embrace and extend" on it, same as they have with many, many other projects.

---

### Post by 3rdalbum on 2009-09-12
> **Frak said:**
> When in doubt: magic.

Libmagic? I thought that just determined the types of files?

---

### Post by Frak on 2009-09-12
> **3rdalbum said:**
> Libmagic? I thought that just determined the types of files?
That's the magical part (?)

---

### Post by kpholmes on 2009-09-12
> **xArv3nx said:**
> the mac scene is disgusting (which is the REAL reason I left macs).

haha, very true

---

### Post by MikeTheC on 2009-09-12
Geez, I guess there's just no pleasing some folks.

---

### Post by Frak on 2009-09-12
> **MikeTheC said:**
> Geez, I guess there's just no pleasing some folks.
"We give you a great technology that should radically increase speeds on my home systems, and cause greater satisfaction in POSIX technology"

"You guys are disgusting pigs!"

---

### Post by pelle.k on 2009-09-13
> and the mac scene is disgusting (which is the REAL reason I left macs).
> haha, very true 
I am thinking about buying me a mac mini (and snow leopard, obviously), so could you elaborate on that? I mean, digusting is a pretty strong word. I guess i'm trying to figure out if you're "haters" or free software fanbois, because if you aren't, and your arguments are valid, i might just have to think again.

---

