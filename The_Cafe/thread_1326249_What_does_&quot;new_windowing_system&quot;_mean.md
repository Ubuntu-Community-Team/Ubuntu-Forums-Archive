---
title: "What does &quot;new windowing system&quot; mean?"
date: 2009-11-14
forum: The Cafe
---

### Post by froggyswamp on 2009-11-14
Folks there are rants that Google Chrome OS (beta) will launch next week and they say it will have a "new windowing system" - what exactly is that?
Is it like a "new Gnome" or is it something low level like a new X server stack like Mac's Quartz graphics layer?

---

### Post by NoaHall on 2009-11-14
Yep, it's for them to use instead of X.

---

### Post by vagrantrooper on 2009-11-14
X windowing renders GUI amongst other things and has always been a sluggish point for Linux imo up until a couple of years ago.

---

### Post by Paqman on 2009-11-14
No-one knows really, because Google aren't telling. It's a pretty vague term. Best guess is that they aren't using X, but it really is just a guess.

---

### Post by Xbehave on 2009-11-14
> **vagrantrooper said:**
> X windowing renders GUI amongst other things and has always been a sluggish point for Linux imo up until a couple of years ago.
If by a couple you mean >5 then possibly. What is with all the X hate? The UNIX-HATERS Handbook is **old**.

Yes "new windowing system" does mean no x11 (or a simple mistake on googles part), it will probably be replaced by
1) Android like java stuff
2) PalmOS like, html stuff

My money is on 2 and the entire front end being html based.

> **Paqman said:**
> No-one knows really, because Google aren't telling. It's a pretty vague term. Best guess is that they aren't using X, but it really is just a guess.
[windowing system]("http://en.wikipedia.org/wiki/Windowing_system") is a well defined term, there is a chance that google made a mistake in the announcement, but it seams if that were the case they would have corrected it by now.

---

### Post by Tibuda on 2009-11-14
I have not seen official evidence that it is a X replacement. I would guess it is a new window manager.

---

### Post by NoaHall on 2009-11-14
> **Xbehave said:**
> If by a couple you mean >5 then possibly. What is with all the X hate? The UNIX-HATERS Handbook is **old**.

Yes "new windowing system" does mean no x11 (or a simple mistake on googles part), it will probably be replaced by
1) Android like java stuff
2) PalmOS like, html stuff

My money is on 2 and the entire front end being html based.

Really? I don't think they'd use something you couldn't install GDE/KDE/xfce on. Their hand-held interfaces might be pretty, but they are no gnome.


Oh, and btw everyone Windowing System != windows manager.
You seem to be mixing them up.

Windowing System = X11
windows manager = gnome, kde, xfce, lxde, compiz(to some extent) etc

---

### Post by Tibuda on 2009-11-14
> **NoaHall said:**
> Oh, and btw everyone Windowing System != windows manager.
You seem to be mixing them up.

Windowing System = X11
windows manager = [s]gnome, kde,[/s] **metacity, kwin**, xfce, [s]lxde[/s] **openbox**, compiz[s](to some extent)[/s] etc

In popular language, the word "system" can be used to almost anything. There's no evidence that it was used to refer to what you are calling "windowing system", which is the technical term.

---

### Post by froggyswamp on 2009-11-14
> **Xbehave said:**
> 
My money is on 2 and the entire front end being html based.
The HTML rendered directly to video card? huh To render HTML one still needs a graphics server like X. And yes, the unix haters book is old, but the X Server is even older and nobody has rewritten its core and design, during all this time it has been kept up to work "good enough" or (as many people call it) "not too shabby".

I hope Google comes with a _good_ X alternative which will be picked up by the industry, if Google doesn't manage it, we're bound to keep improving (X's) old code that can't change substantially because of it's old design. Even at Red Hat there's (been) an effort to replace X with "Wayland" but for about a year I haven't heard anything of it, there's been many attempts but no one had the power to develop a qualitative stack till the end. Good luck Google, I hope you succeed.

---

### Post by Paqman on 2009-11-14
> **Xbehave said:**
> 
[windowing system]("http://en.wikipedia.org/wiki/Windowing_system") is a well defined term, there is a chance that google made a mistake in the announcement, but it seams if that were the case they would have corrected it by now.

I'm inclined to agree, but the tone of the blog post was chatty and informal. I wouldn't put to much faith in the technical precision of the terms. They were deliberately vague on a lot of details.

---

### Post by Tibuda on 2009-11-14
> **Paqman said:**
> I'm inclined to agree, but the tone of the blog post was chatty and informal. I wouldn't put to much faith in the technical precision of the terms. They were deliberately vague on a lot of details.

That's exactlt what I think.


For people saying that X is the reason why Firefox is so slow on Linux:
I have seen [that Chrome/ium is fastest under Linux (X Windowing System) than under Windows]("http://groups.google.com/group/chromium-dev/browse_thread/thread/d86faf0eff41b998?pli=1"), which is the opposite result of Firefox benchmarks.

---

### Post by Xbehave on 2009-11-14
> **froggyswamp said:**
> The HTML rendered directly to video card? huh To render HTML one still needs a graphics server like X.
Have a look at the [webOS]("http://en.wikipedia.org/wiki/WebOS"), it's a linux based phone, that has all it's front end is done in ajax.

> And yes, the unix haters book is old, but the X Server is even older and nobody has rewritten its core and design,
Apart from all the stuff that **has** been rewritten and the change to a very modular design (An xorg release is just the packaging of several independently developed components). We are on the verge of a rootless-xorg

> during all this time it has been kept up to work "good enough" or (as many people call it) "not too shabby".
Any examples of why it's "good enough" instead of just "good", I mean I've seen a lot of people badmouth it but nothing ever really sticks. Arguably it could do more stuff in kernel for a speed boost, there is an embedded proprietary program X11 compatible system that does this.

> Even at Red Hat there's (been) an effort to replace X with "Wayland" but for about a year I haven't heard anything of it, there's been many attempts but no one had the power to develop a qualitative stack till the end. Good luck Google, I hope you succeed.
Wayland is still being developed but i don't think it's a priority at RH. But something will have to be a lot better than X11 for it to be worth distros switching and loosing backwards compatibility, I'm not sure this will be a problem for google who will want a web based os anyway.

edit:
> **danielrmt said:**
> For people saying that X is the reason why Firefox is so slow on Linux:
I have seen [that Chrome/ium is fastest under Linux (X Windowing System) than under Windows]("http://groups.google.com/group/chromium-dev/browse_thread/thread/d86faf0eff41b998?pli=1"), which is the opposite result of Firefox benchmarks.I think the reason firefox is faster on windows is that the binaries are compiled with PGO, there is a bug preventing this being the default on linux

---

### Post by froggyswamp on 2009-11-14
> **danielrmt said:**
> That's exactlt what I think.
For people saying that X is the reason why Firefox is so slow on Linux:
I have seen [that Chrome/ium is fastest under Linux (X Windowing System) than under Windows]("http://groups.google.com/group/chromium-dev/browse_thread/thread/d86faf0eff41b998?pli=1"), which is the opposite result of Firefox benchmarks.
He later acknowledges that the computer with Linux was more powerful then the windows one.

---

### Post by froggyswamp on 2009-11-14
> **Xbehave said:**
> Have a look at the [webOS]("http://en.wikipedia.org/wiki/WebOS"), it's a linux based phone, that has all it's front end is done in ajax.
Haha omg are you implying it doesn't have a graphics server and that "ajax" is doing the rendering directly to it's video card? If so that's the craziest thing I've heard lately.

---

### Post by froggyswamp on 2009-11-14
I see, you probably read these lines on wikipedia
> 
webOS's [graphical user interface]("http://en.wikipedia.org/wiki/Graphical_user_interface") is designed for use on devices with [touchscreens]("http://en.wikipedia.org/wiki/Touchscreen"). It includes a suite of applications for personal information management and makes use of a number of web technologies such as [HTML 5]("http://en.wikipedia.org/wiki/HTML_5"), [JavaScript]("http://en.wikipedia.org/wiki/JavaScript"), and [CSS]("http://en.wikipedia.org/wiki/CSS").[[4]]("http://en.wikipedia.org/wiki/WebOS#cite_note-3")[[5]]("http://en.wikipedia.org/wiki/WebOS#cite_note-4") Palm claims that the design around these existing technologies was intended to spare developers from learning a new programming language
and decided that it means there's no graphical server underneath, no my friend, there is one, wikipedia just didn't specify which one, since WebOS has proprietary components - the graphics stack might be one of them so the author of the article might just not know which one WebOS uses.

---

### Post by Xbehave on 2009-11-14
> **froggyswamp said:**
> I see, you probably read these lines on wikipedia
and decided that it means there's no graphical server underneath, no my friend, there is one, wikipedia just didn't specify which one, since WebOS has proprietary components - the graphics stack might be one of them so the author of the article might just not know which one WebOS uses.
I didn't say there is no graphical server underneath, just that programs are presented with a different windowing system.

---

### Post by froggyswamp on 2009-11-14
Why X sucks:
A big bunch of crappy code under another licence than the one of Linux kernel.

Old code from the 80's that contains solutions for other days problems.

Very few developers.

Code that is very difficult to understand and produce patchs for it.

The X don't use today's graphic cards options and facilities that make
developers life easy.

Very amount of code executing with Root privileges (going to be fixed...)

Architecture that has became crappy and not optimized.

Release cycle dates are never like they said.

Big parts of X aren't being used today for security or because there
is no need for it. (networking through ports are replaced with ssh
secured session)

Writing drivers for X is very difficult.

Do you need more ?

[http://groups.google.com/group/wayland-display-server/browse_thread/thread/632afcd92cb7950d](http://groups.google.com/group/wayland-display-server/browse_thread/thread/632afcd92cb7950d)

---

### Post by Xbehave on 2009-11-14
> **froggyswamp said:**
> Why X sucks:
A big bunch of crappy code under another licence than the one of Linux kernel.
One of the strengths of X11 is the MIT license as it allows it to be used on closed systems such as AIX, solaris (pre openness), etc

> Old code from the 80's that contains solutions for other days problems.
I doubt it, the code has undergone several reworking, just because they haven't done a rewrite doesn't mean it's the same code.

> Very few developers.
That's not a problem with xorg, that's just that people prefer to whine about it than "fix" it.

> Code that is very difficult to understand and produce patchs for it.
[citation]

> The X don't use today's graphic cards options and facilities that make developers life easy.

[citation], i follow xorg-radeon development and i've never seen this criticism

> Architecture that has became crappy and not optimized.
[citation]

> Release cycle dates are never like they said.
Yeah, and Debian sucks too! Having a release when it's ready approach is just as good as a time based releases that can go horribly wrong (see kde4.0). Not only that but they have moved to a 6 month cycle now too.

> Big parts of X aren't being used today for security or because there is no need for it. (networking through ports are replaced with ssh
secured session) 
1) networking is still done though ports, it's done inside shh now if you need security
2) there are many situations where you don't need security
3) It is hardly a huge part of X, network transparency between as server-client is shouldn't take much work if you have sane IPC.

> Writing drivers for X is very difficult.
writing drivers is supposed to be easy?

Your link is just one guys uncited,uninformed rant and is rebutted right there.

---

### Post by froggyswamp on 2009-11-14
> **Xbehave said:**
> 
Your link is just one guys uncited, uninformed rant and is rebutted right there.
Oh man, I stopped using your tactics when I was a kid: oversimplifying, misinterpreting and downplaying and when I say that - your move will be that it's actully _me_ using those tactics.
So it's impossible to prove something to you unless I wanna spend like a month proving and I certainly don't.
Let me take your tactics just for you to have a taste what it feels like: I'm saying the earth is not round and challenge you to prove me wrong (but not in this thread for it would be too much offtopic).

---

### Post by Mr. Picklesworth on 2009-11-14
> **froggyswamp said:**
> I see, you probably read these lines on wikipedia
and decided that it means there's no graphical server underneath, no my friend, there is one, wikipedia just didn't specify which one, since WebOS has proprietary components - the graphics stack might be one of them so the author of the article might just not know which one WebOS uses.

It uses GStreamer, dbus and Pulseaudio so I would *guess* that it's running X, since that's the underlying window system that those work well for.

These people should know: [http://www.webos-internals.org/wiki/Main_Page](http://www.webos-internals.org/wiki/Main_Page)

Edit: Here you go! [http://www.webos-internals.org/wiki/Running_Processes](http://www.webos-internals.org/wiki/Running_Processes)
(And as a reminder, WebOS is regarded as an incredibly awesome OS, so maybe it's time to stop blaming the low-level tools and start working with them better).



And for the "X is obsolete" whining... if there are so few developers working on X, then there must be lots of people out there in the remaining universe who can work on a new window system. When they make something functionally superior to X, I'm sure all the hardware manufacturers and distros will happily move over. It isn't really constructive to say that it's junk without ANY citation or solutions.

(As for solutions, there is [Wayland]("http://en.wikipedia.org/wiki/Wayland_(display_server)"), always making progress. It's a display server, however, so a tad off topic).

---

### Post by Xbehave on 2009-11-14
> **froggyswamp said:**
> 
So it's impossible to prove something to you unless I wanna spend like a month proving and I certainly don't.
Right only all i wanted was a citation of somebody describing in details something that is wrong with xorg, but like most xorg trolls (I'm sure you don't consider yourself one but you are badmouthing it without actually backing up your claims) you are unable to produce the goods. If i claim ubuntu sucks, it is **ME** who is expected to say why, however just to humour you, [here]("http://www.phoronix.com/scan.php?page=article&item=nvidia_qa_linux&num=8") is what somebody that knows a thing or to about graphics has to say on xorg:
> In terms of future growth: I believe the largest opportunities are in the X Window System. This isn't because X is bad (many of the core architectural decisions are quite sound: e.g., separation of policy into window managers and composite managers), but the further evolution of the Linux composited desktop will necessarily occur in the primary desktop components: the X server, the X drivers, the window managers and composite managers.

Thankfully, in my view, the X Window System as implemented using the XFree86/X.Org Loadable Driver Framework, has the flexibility and extensibility to be used to solve the modern Linux desktop challenges.
hmmm, nvidia graphics driver developer vs some dude on some message board, who knows more about graphics?

---

### Post by froggyswamp on 2009-11-14
> **Mr. Picklesworth said:**
> 
And for the "X is obsolete" whining... if there are so few developers working on X, then there must be lots of people out there in the remaining universe who can work on a new window system. When they make something functionally superior to X, I'm sure all the hardware manufacturers and distros will happily move over. It isn't really constructive to say that it's junk without ANY citation or solutions.
I love this logic, I really do. It's an unbelievable oversimplification. You probably know that if one creates a better implementation it doesn't nearly mean the industry (the people around the world) will just jump in and start using it.
Firefox is better and "more modern" than IE yet, after 5 years the majority uses IE, because there are much more factors to get the industry using something besides plain quality. One of these factors is power, and Google has such power (influence & money) hence I hope/believe Google will succeed, but the change won't happen overnight.

---

### Post by froggyswamp on 2009-11-14
Xbehave, please PM me and try proving me the earth is round, I bet 1000$ you won't prove - just to show you how easy I can play with you using your own "skilled" (duh) tactics.
Again, I won't argue with you not because of implying the truth is on your side, but because of your tactics which only lead to long discussions and in the end when the other person is fed up arguing you'll say: you quit cause you can't prove me wrong duh.
I can myself issue like 10 reasons why X is "very good" by issuing skilled half-truths based on different tactics like cherry picking only the info I like better, oversimplification, challenging what's objective and what's not, downplaying, defining authorities as sources of truth etc etc ad nauseam.
Accept my challenge and we'll decide where to argue, if you're not afraid.

---

### Post by Mr. Picklesworth on 2009-11-14
> **froggyswamp said:**
> I love this logic, I really do. It's an unbelievable oversimplification. You probably know that if one creates a better implementation it doesn't nearly mean the industry (the people around the world) will just jump in and start using it.
Firefox is better and "more modern" than IE yet, after 5 years the majority uses IE, because there are much more factors to get the industry using something besides plain quality. One of these factors is power, and Google has such power (influence & money) hence I hope/believe Google will succeed, but the change won't happen overnight.

Yes, I am simplifying, but so are you. (For example, you are doing even less than cherrypicking; you don't have anything tangible at all).

The difference between Firefox and Xorg is that Firefox is competing on Microsoft's ecosystem. Xorg doesn't have power; it's simply there. (Although it is true that the turmoil from needing to port all the drivers would really suck, so it has some staying power from that).

Froggy, we are derailing this thread. I have seen your rant, I disagree. You could be right, and I wrong. We're done.

---

### Post by Xbehave on 2009-11-14
> **Mr. Picklesworth said:**
> It uses GStreamer, dbus and Pulseaudio so I would *guess* that it's running X, since that's the underlying window system that those work well for.

These people should know: [http://www.webos-internals.org/wiki/Main_Page](http://www.webos-internals.org/wiki/Main_Page)
dbus and pulseaduio are unrelated to X and gstreamer can output in many formats.

> Edit: Here you go! [http://www.webos-internals.org/wiki/Running_Processes](http://www.webos-internals.org/wiki/Running_Processes)
(And as a reminder, WebOS is regarded as an incredibly awesome OS, so maybe it's time to stop blaming the low-level tools and start working with them better).
I can't see X anywhere in there, meaning that webOS has some other windowing system running. I do agree that there is nothing wrong with the tools, however different tools suit different needs, if you want a full blown desktop then ATM you need xorg, if you want a web based OS you don't.

---

### Post by Mr. Picklesworth on 2009-11-14
> **Xbehave said:**
> dbus and pulseaduio are unrelated to X and gstreamer can output in many formats.


I can't see X anywhere in there, meaning that webOS has some other windowing system running. I do agree that there is nothing wrong with the tools, however different tools suit different needs, if you want a full blown desktop then ATM you need xorg, if you want a web based OS you don't.

Yep, I poked around and that does seem the case. Weirdly, though, someone claims to have used ssh -x. He's probably just delusional. I wish I knew what they were using! :)

Edit:
dbus-daemon isn't in that list either, but that one is definitely there. Funny...

---

### Post by froggyswamp on 2009-11-14
> **Mr. Picklesworth said:**
> 
The difference between Firefox and Xorg is that Firefox is competing on Microsoft's ecosystem. Xorg doesn't have power; it's simply there. (Although it is true that the turmoil from needing to port all the drivers would really suck, so it has some staying power from that).

Froggy, we are derailing this thread. I have seen your rant, I disagree. We're done.
We're done - alright, thanks.
Yes, my example doesn't fit in 100% because there can't be an example that would fit 100%. It was meant to ease comprehension not for giving a perfect and exact copy of some phenomenon.

---

### Post by phrostbyte on 2009-11-14
Are there even any benchmarks showing that X is actually slow in comparison to Quartz and/or Windows? It gets thrown around a lot, but no one actually have any factual evidence of the assertion. I think people naturally assume because X has a client/server architecture it's going to be slow, but that's a silly assertion.

---

### Post by phrostbyte on 2009-11-14
> I think the reason firefox is faster on windows is that the binaries are compiled with PGO, there is a bug preventing this being the default on linux

Actually it's because the 64-bit version of Firefox lacks a JavaScript compiler. That's why when you test the (64-bit Firefox) against a Wine (32-bit) version, it is significantly faster. There is no official 64-bit version of Firefox for Windows.

If you compare Chromium, which does have a 64-bit compiler, you will find that it's JavaScript performance tends to be (slightly) faster then on Windows.

Here is a chart:
[http://1.bp.blogspot.com/_A8yyx3PMRLo/SvM1tOAz3oI/AAAAAAAAAXM/LNqm2CLOY54/s1600-h/chart.png](http://1.bp.blogspot.com/_A8yyx3PMRLo/SvM1tOAz3oI/AAAAAAAAAXM/LNqm2CLOY54/s1600-h/chart.png)

---

### Post by Xbehave on 2009-11-14
> **froggyswamp said:**
> Xbehave, please PM me and try proving me the earth is round, I bet 1000$ you won't prove - just to show you how easy I can play with you using your own "skilled" (duh) tactics.
**You** are the one making the claim that xorg sucks, **you** need to provide some sort of evidence. I'm not looking for 100%, mearly a good point from somebody who knows about xorg development in the last 5 years. Despite the fact that I consider anybody who mindlessly posts
"pulseaudio/xorg/netowrkmanager/ubuntu/etc SUXORS" without any justification a tool, I am happy to consider the validity of your points, if you can show they have **anything** to them. 

The reason you refuse to argue, is because your just repeating **FUD** that you heard elsewhere and now confronted by this fact all you can do is dodge the question.

---

### Post by froggyswamp on 2009-11-14
There are lies, damn lies and statistics (benchmarks).
Unfortunately an "objective" benchmark is somewhat an oxymoron.. one can't issue a benchmark with which anyone would agree and there's plenty of issues based on which one can declare the benchmark(s) doubtful and/or void.

---

### Post by froggyswamp on 2009-11-14
> **Xbehave said:**
>  (lots of stuff said)  haha which is what I said you'll say. Please read what I said again, maybe you'll understand.

---

### Post by phrostbyte on 2009-11-14
> **froggyswamp said:**
> There are lies, damn lies and statistics (benchmarks).
Unfortunately an "objective" benchmark is somewhat an oxymoron.. one can't issue a benchmark with which anyone would agree and there's plenty of issues based on which one can declare the benchmark(s) doubtful and/or void.

It would be nice to at least HAVE a benchmark. You are right that benchmarks don't always tell the whole story. But they are far far better then making up stuff from thin air. Seriously.

Detailed benchmarks (one that do dozens of tests), can potentially find performance bottlenecks that can be fixed.

---

### Post by froggyswamp on 2009-11-14
I agree. I remember when I was reading (couple months ago) somewhere about DirectFB people were talking about a benchmark between X and DirectFB and saying that the benchmark showed X was about 30% slower, but
1) I (of course) don't remember where I read it
2) It might already not be up to date, "time passes, things change".

---

### Post by Xbehave on 2009-11-14
> **froggyswamp said:**
> haha which is what I said you'll say. Please read what I said again, maybe you'll understand.
I don't want to debate unrelated crap with you, I just want to make it clear to anybody who is reading this thread that you are full of it and your claims regarding xorg are unfounded, your posts are no better than [this]("http://www.microsoft.com/uk/getthefacts/default.mspx").

I'll type this extra slow so you can follow:
**[SIZE="4"]If   you   are   going   to   claim   something   needs improving,   it   is   up   to   you   to    show    that    is    the case[/SIZE]**

---

### Post by froggyswamp on 2009-11-14
> **Xbehave said:**
> 
Thank you very much for your kind words, linking to Microsoft was very genuine too :))

---

### Post by Frak on 2009-11-14
I won't say X is slow, but I will say that due to its Client/Server nature, it scares off some companies from heavily investing into Linux. It's weird, it can be buggy at times, and a lot of features that can be got from Client/Server don't apply to a home user. Remotely rendering a display is nice, but it isn't necessarily something that a home user might use.

From whom I've talked to at Google, there is some distaste for X, but from that I cannot assume whether they're creating their own DM, WM, or X Replacement altogether. The way they use the term is vague.

---

### Post by earthpigg on 2009-11-14
my novice and uneducated understanding of the terms being thrown around:

Windowing System: Quartz, X11.
Window Manager: openbox, metacity, compiz
Desktop Environment: gnome, lxde, kde


windowing system (note the lack of capital letters): take the word 'windowing' in the context of software, and 'system' in the context of software. a very ambiguous term, can mean anything.

---

### Post by Chame_Wizard on 2009-11-14
> **Frak said:**
> I won't say X is slow, but I will say that due to its Client/Server nature, it scares off some companies from heavily investing into Linux. It's weird, it can be buggy at times, and a lot of features that can be got from Client/Server don't apply to a home user. Remotely rendering a display is nice, but it isn't necessarily something that a home user might use.


So what?screw those companies,at least X11 can be fixed if something is broken.:P

---

### Post by Frak on 2009-11-14
> **Chame_Wizard said:**
> So what?screw those companies,at least X11 can be fixed if something is broken.:P
From what I've worked with X, if something is broken, it's best to let everybody work around it.

Also, until Linux gets commercial support, it won't go anywhere. Google is trying to solve this dilemma.

---

### Post by Regenweald on 2009-11-14
I honestly think it will be a new window manager 'concept' above same old xorg ;)
The original announcement wreaks of inuendo

"And as we did for the Google Chrome browser, we are going back to the basics and completely redesigning the underlying security architecture of the OS so that users don't have to deal with viruses, malware and security updates. It should just work."

Now call me a synic, but to me this says: 
"yes, every FOSS user already knows that if our OS is based on Linux, then potential users don't have to worry about every windows virus out there, and to another extent, viruses in general, but if we state it this way, non-savy users will think - Wow! if i use google's OS I won't get viruses! - So yeah, we didn't say that the google brand is solely responsible for this new amazing virus free experience, but we didn't *not*say it either ;)"

I like their style, all a matter of interpretation. Any how you take it, I too look forward to its release.

---

### Post by toupeiro on 2009-11-14
Wow... This thread is a FUD fest..

First off, Modern day xorg uses more GPU for local rendering than Aero, taking the load off the CPU and releasing cycles back for things they should be used for.  Quartz you won't here me quote a lot because I don't know anything about it.   Windows Vista / 7 do not leverage the GPU very well for their window system rendering, and yes, I have been able to trend the performance first hand using very graphic intensive applications that are cross platform where I work. I wish I had more to share out than that, but I don't so I'm only talking from first hand experience and testing. 

Whether or not there are any realistic benchmarks readily available between X, Quartz, and Aero, why would there be?  You're not going to run Areo on Linux, or Quartz on windows!  This would be the only situation where a benchmark like this would even mean anything at all.  In fact, if Google means an xorg replacement by windowing system (which hasn't been confirmed or denied, but argued in this thread none the less as written in stone fact), this will be the first time that a windowing system will have space to compete on the same OS.  (Correct me if I am wrong, but quartz cannot be replaced in Mac/OSX)

Xorg has its shortcomings in places, but these arguments that it makes firefox slower on the same hardware is just ridiculous.  xorg is a strong windowing system, and while I welcome competition, I also worry about what this will make chrome's compatibility look like.  Surely I don't want to run their windowing system and have to run X as well to maintain compatibility.  Thats a waste of resources.

---

### Post by toupeiro on 2009-11-14
> **Regenweald said:**
> I honestly think it will be a new window manager 'concept' above same old xorg ;)


I'm inclined to agree, but we'll see.

---

### Post by Xbehave on 2009-11-14
> **Frak said:**
> I will say that due to its Client/Server nature, it scares off some companies from heavily investing into Linux. It's weird, it can be buggy at times
Why? (I'm not disagreeing, but why does that scare them off?)

> a lot of features that can be got from Client/Server don't apply to a home user. Remotely rendering a display is nice, but it isn't necessarily something that a home user might use.
I think you need stuff to be pretty much client/server for multi login desktops to make sense. OFC most desktop users could drop network transparency, but you need something similar to unix sockets for X11 to work right anyway.

---

### Post by tjwoosta on 2009-11-14
For everyone who thinks the new windowing system is a rumor, or just a new window manager, check this link. They are clearly talking about a whole new windowing system, not just a new window manager.

[http://en.wikipedia.org/wiki/Google_Chrome_OS](http://en.wikipedia.org/wiki/Google_Chrome_OS)

> Google has stated that the Google Chrome OS project will be open source[4] by the end of 2009, and that it will use "a new windowing system".[5]

If you follow the "windowing system" link on the wiki page, it is clearly talking about the X windowing system, which suggests they are infact going to be replacing X with their own new windowing system.

> A windowing system (or window system) is a component of a graphical user interface (GUI), and more specifically of a desktop environment, which supports the implementation of window managers, and provides basic support for graphics hardware, pointing devices such as mice, and keyboards.

---

### Post by Xbehave on 2009-11-14
> **toupeiro said:**
> In fact, if Google means an xorg replacement by windowing system, this will be the first time that a windowing system will have space to compete on the same OS.
It might of got lost in the FUD but there are already examples of linux without X, such as webOS and android (it's on netbooks so comparisons vs same netbook with Xorg are possible)

---

### Post by tjwoosta on 2009-11-14
> **Xbehave said:**
> It might of got lost in the FUD but there are already examples of linux without X, such as webOS and android (it's on netbooks so comparisons vs same netbook with Xorg are possible)

check this out  (taken from the windowing system wiki page)

Windowing systems for Unix-like operating systems

    * 8½ and rio for Plan 9
    * Fresco/Berlin
    * FBUI
    * HP Windows
    * ManaGeR (MGR)
    * Metisse
    * MicroXwin (provide faster GUI and small disk/memory usage but still compatible with X Window)
    * NeWS / Xnews
    * NeXT DPS
    * Qtopia
    * Quartz Compositor integrated into Mac OS X
    * SunView
    * Twin (Text WINdows)
    * Wayland (extremely simple display server using cutting edge Linux kernel technology and DRI/DRI2 to make a fast GUI in which every frame is perfect)
    * X Window System (free-software, de-facto standard on Linux and other Unix-like operating systems)
    * Xynth
    * XFast
    * Y Window System

And this is just unix

---

### Post by gnomeuser on 2009-11-14
> **toupeiro said:**
> I'm inclined to agree, but we'll see.

The first reports out are claiming that hardware support in the version we will get next week will be limited. As the kernel and X.org would be roughly the same that would be untrue. The only way to make it true provided the other information is true is if they did replace X.

---

### Post by vagrantrooper on 2009-11-14
To my knowledge Macintosh still uses xorg at least in some of its releases but I am sure it 

will be highly customised from the original entwined with propriety code.

---

### Post by Xbehave on 2009-11-14
> **vagrantrooper said:**
> To my knowledge Macintosh still uses xorg at least in some of its releases but I am sure it 

will be highly customised from the original entwined with propriety code.
Nah os X uses quartz, it has support for running X11 apps through [XQuartz]("http://en.wikipedia.org/wiki/XQuartz") but your average mac os X install will never use it.

---

### Post by ZankerH on 2009-11-14
My guess is google's GUI stack will probably be composed of AJAX, javascript, CSS, (x)html and the rest of the web 2.0 buzzwords, rendered by webkit or a derivative thereof. At this point, whether it all runs on xorg or google's windowing system is pretty irrelevant, because it's going to be bloated beyond measure in any case.

---

### Post by hessiess on 2009-11-14
For everyone wining about X11, the extreme level of customisability in Linux comes directly from the modularity of X, Without this it would not even be passable to run different desktop environments like GNOME or KDE, or even different window managers. It would just be a monolithic, imposable to customise lump like Windows and OSX.

Sure you *can* run different shells on Windows, but they integrate very poorly with the OS.

---

### Post by Chronon on 2009-11-14
> **Frak said:**
> I won't say X is slow, but I will say that due to its Client/Server nature, it scares off some companies from heavily investing into Linux. It's weird, it can be buggy at times, and a lot of features that can be got from Client/Server don't apply to a home user. Remotely rendering a display is nice, but it isn't necessarily something that a home user might use.

Interesting.  I find that very useful, actually.  I SSH to my tower from my netbook via the wireless LAN and let it do the heavy lifting and/or run software, like Mathematica, that I only have a single-machine, single-user license  for.

---

### Post by toupeiro on 2009-11-14
> **Xbehave said:**
> It might of got lost in the FUD but there are already examples of linux without X, such as webOS and android (it's on netbooks so comparisons vs same netbook with Xorg are possible)

True, but I don't consider these drop-in replacements to X.  For example, they don't have the same extensions which X has. e.g MESA 6.x GLX, and multi-output supportability (Can't cite this last part as fact, but from what I've seen from the little I've played with them, its true).  It may be possible to extend WebOS and Android to support things like this, but the point is that these are intentionally stripped down, lightweight Windowing systems optimized for a specific architecture.  They have their place, but they cannot provide all the functionality X extends to a Linux OS on i686 or x86_64 architecture.  What we are talking about with Chrome is something that will hopefully match, component for component, Xorgs functionality at minimum on traditional commodity PC architecture.  And again, I worry greatly about cross-compatibility with X.  You're cutting your own throat before you ever took a breath if you don't make that pretty failsafe.

---

### Post by toupeiro on 2009-11-14
> **hessiess said:**
> for everyone wining about x11, the extreme level of customisability in linux comes directly from the modularity of x, without this it would not even be passable to run different desktop environments like gnome or kde, or even different window managers. It would just be a monolithic, imposable to customise lump like windows and osx.

Sure you *can* run different shells on windows, but they integrate very poorly with the os.

+1

---

### Post by Frak on 2009-11-14
> **Chronon said:**
> Interesting.  I find that very useful, actually.  I SSH to my tower from my netbook via the wireless LAN and let it do the heavy lifting and/or run software, like Mathematica, that I only have a single-machine, single-user license  for.
Good for you.

---

### Post by Chronon on 2009-11-14
> **Frak said:**
> Good for you.

My point being, I would have assumed this to be pretty standard practice on home networks.

---

### Post by Frak on 2009-11-14
> **Chronon said:**
> My point being, I would have assumed this to be pretty standard practice on home networks.
I can see times when this could be beneficial. Other than that, home users will rarely take advantage of it. Businesses would love it.

---

### Post by Tibuda on 2009-11-19
Here's the new window manager source code:
[http://src.chromium.org/cgi-bin/gitweb.cgi?p=chromiumos.git;a=tree;f=src/platform/window_manager;hb=HEAD](http://src.chromium.org/cgi-bin/gitweb.cgi?p=chromiumos.git;a=tree;f=src/platform/window_manager;hb=HEAD)

it runs under X server

---

### Post by Regenweald on 2009-11-19
> **toupeiro said:**
> I'm inclined to agree, but we'll see.

Guess I was right ;)

---

