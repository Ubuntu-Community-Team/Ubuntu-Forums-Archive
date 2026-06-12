---
title: "Is Google's Chrome OS Good for Linux?"
date: 2010-01-26
forum: The Cafe
---

### Post by jonathank89 on 2010-01-26
I wrote [this piece]("http://friendlytechninja.com/2010/01/24/is-googles-chrome-os-good-for-linux/") after listening to a tuxradar podcast were they talked about Chrome OS (they even read my answer to there "Chrome OS: hero or zero?" question on air, which was cool :)).

Anyway...I'm an Ubuntu user and have been for a couple of years now, but I've come to release that while linux on the desktop has grown a decent amount I just wish it was more, because I'm sure like most of you, I can really see the potential there and want the world to see it! With Google entering the OS space and with it being built on linux and being open source I'm really hoping that going to help vendors get there act together and support linux properly! Anyway, I'm interested in what other people think about this:

My post: [http://friendlytechninja.com/2010/01/24/is-googles-chrome-os-good-for-linux/](http://friendlytechninja.com/2010/01/24/is-googles-chrome-os-good-for-linux/)

Oh if you see typo's or something leave a comment on the post to let me know...I usually just write howto's...Thanks :)

---

### Post by AllRadioisDead on 2010-01-26
it's*

---

### Post by k64 on 2010-01-26
I just replied to the Friendly Tech Ninja article (it's awaiting moderation). Hope you like my feedback.

---

### Post by cascade9 on 2010-01-26
I've said it before, and I'll say it again...chrome is NOT open source.

> These Terms of Service apply to the executable code version of Google Chrome. Source code for Google Chrome is available free of charge under open source software license agreements at [http://code.google.com/chromium/terms.html](http://code.google.com/chromium/terms.html).

[http://www.google.com/chrome/intl/en/eula_text.html](http://www.google.com/chrome/intl/en/eula_text.html)

> The Chromium software and sample code developed by Google is licensed under the BSD license.

[http://code.google.com/chromium/terms.html](http://code.google.com/chromium/terms.html)

Because chromium is a BSD licence they can move over whatever code they want to chrome and don't have to provide any source code...and they are under no obligation to move any code over if they so wish. They can also put in whatever code they want into chrome and no give any indication that the code is different to chromium. 

Brilliant gambit from google. Do some work on chrome, release the code as chromium under the BSD licence, insinuate that chrome is open source, (but keep it closed) and get coders for free. My hat is off to the cunning devils. But I'll never run chrome.

---

### Post by n0dix on 2010-01-26
I think that Google Chrome SO will give more popularity to linux in general. Therefore, the community is benefit.

---

### Post by p_quarles on 2010-01-26
> **cascade9 said:**
> Brilliant gambit from google. Do some work on chrome, release the code as chromium under the BSD licence, insinuate that chrome is open source, (but keep it closed) and get coders for free. My hat is off to the cunning devils. But I'll never run chrome.

And yet, even the purist FSF folks consider that license to be free.

I mean, you CAN access the source code, right? Am I missing something?

---

### Post by cascade9 on 2010-01-26
> **p_quarles said:**
> And yet, even the purist FSF folks consider that license to be free.

I mean, you CAN access the source code, right? Am I missing something?

In some way, the BSD licence is 'freer' than the GPL. GPL locks you into more GPL, BSD licence lets you move the code into proprietary projects. (there has been a few 'libertarians' here arguing that the BSD licence is the only 'free' licence for just that reason). 

You can see the code for chromium, but not chrome.

---

### Post by earthpigg on 2010-01-26
> **p_quarles said:**
> And yet, even the purist FSF folks consider that license to be free.

I mean, you CAN access the source code, right? Am I missing something?

yes, the BSD license is free... and from there, you can create non-free works if you wish. i could modify Chromium, load it with ***my own*** spyware and/or malware, keep the source code private, and release it in binary form as "Krome" if i wished. (eventually, i'd get hung up in court... but over trademark, not violating the BSD license.)

OS X is not FreeBSD. but, let's pretend it is for a moment.

OS X and FreeBSD have significantly different names. consumers will not get confused about which is open source and which is not.

but when one person points out, as the user above did, that the full products known as Chrome OS and Chrome Browser are not open source at all, and that Chromium OS and Chromium are open source... folks will be tempted to say "Same thing" and let the waters be murky and muddy.

this could also mean that Open Source get's blamed for some flaw of Chrome Browser/OS that stems from it being proprietary. i can see it now: some google spyware included in chrome that no one gets to see the source code of will have a security vulnerability that gets exploited... "See, open source stuff is just as insecure as proprietary!"

(yes, i know ***some*** of the spyware is included in chromium's source. it would be silly to assume that ***all*** of it is.)

in b4 people start using words like 'based on' and 'built upon'. doesn't matter. 

0. you probably cannot use chrome for any purpose, but i haven't read the EULA. (you can for chromium, though)
1. you cannot study the source code of chrome (you can for chromium, though)
2. you can probably redistribute copies of chrome.
3. you cannot redistribute modified versions of chrome, because there is no access to source code. (you can do this with chromium, though.)

**_The Four Software Freedoms Do Not Apply To Google Chrome OS or Google Chrome Browser. _**

period.

you can ***assume*** and ***wish to believe*** that Chrome and Chromium are exactly identical aside from branding, but that's it. while you are at it, i have a very nice red bridge here in San Francisco that i have for sale, if you are interested. send some money to my paypal, and it's yours. ill fax you the bill of sale.

eventually, perhaps, someone could get interested enough to look at the nitty-gritty system calls and whatnot of Chrome and compare those to Chromium and do some reverse engineering... but i doubt anyone will bother. many/most of those individuals will simply work on or fork or develop chromium instead.

---

### Post by p_quarles on 2010-01-27
> **earthpigg said:**
> yes, the BSD license is free... and from there, you can create non-free works if you wish. i could modify Chromium, load it with ***my own*** spyware and/or malware, keep the source code private, and release it in binary form as "Krome" if i wished. (eventually, i'd get hung up in court... but over trademark, not violating the BSD license.)
More pertinently, you wouldn't be able to distribute your spyware/malware under the BSD license. 

> this could also mean that Open Source get's blamed for some flaw of Chrome Browser/OS that stems from it being proprietary. i can see it now: some google spyware included in chrome that no one gets to see the source code of will have a security vulnerability that gets exploited... "See, open source stuff is just as insecure as proprietary!"
Well, yes, open source stuff *is* just as insecure as proprietary stuff. Security depends on the quality of auditing, not the quantity. 

> ... but i doubt anyone will bother. many/most of those individuals will simply work on or fork or develop chromium instead.
Which they would not be able to do if not for the fact that Chromium was licensed under the BSD license...

---

### Post by cascade9 on 2010-01-27
> **earthpigg said:**
> but when one person points out, as the user above did, that the full products known as Chrome OS and Chrome Browser are not open source at all, and that Chromium OS and Chromium are open source... folks will be tempted to say "Same thing" and let the waters be murky and muddy.

this could also mean that Open Source get's blamed for some flaw of Chrome Browser/OS that stems from it being proprietary. i can see it now: some google spyware included in chrome that no one gets to see the source code of will have a security vulnerability that gets exploited... "See, open source stuff is just as insecure as proprietary!"

Thanks earthpig, I'm glad I'm not the only one :) 

> **p_quarles said:**
> More pertinently, you wouldn't be able to distribute your spyware/malware under the BSD license. 

Glib answer- why not? Its what google is doing ;)

 Seriously, the BSD licence doesnt magically protect against any form a spyware, malware etc. If your are silly enough to install it, that is your problem. 

> **p_quarles said:**
> 
Well, yes, open source stuff *is* just as insecure as proprietary stuff. Security depends on the quality of auditing, not the quantity. 

Its not just about quality vs quantity. Some times is about avtually getting a patch made- 

> Microsoft today admitted it knew of the Internet Explorer flaw used in the attacks against Google and Adobe since September last year.[http://threatpost.com/en_us/blogs/microsoft-knew-ie-zero-day-flaw-september-012110](http://threatpost.com/en_us/blogs/microsoft-knew-ie-zero-day-flaw-september-012110)

At least with open source, once a security flaw is discovered its more likely to get fixed. People who can actually find flaws are more likely to be able to write a fix....With proprietary /closed source software, you have to wait until someone gets the patch out. 

> **p_quarles said:**
> 
Which they would not be able to do if not for the fact that Chromium was licensed under the BSD license...

I'm a bit confused here. Do you mean fork it or develop for it, both of which are totally possible under other licences. Or reverse engineer it? Which is...well, I wont say illegal, but its specifically referred to in the chrome licence- 

> 9.2 Subject to section 1.2, you may not (and you may not permit anyone else to) copy, modify, create a derivative work of, reverse engineer, decompile or otherwise attempt to extract the source code of the Software or any part thereof, unless this is expressly permitted or required by law, or unless you have been specifically told that you may do so by Google, in writing.[http://www.google.com/chrome/intl/en/eula_text.html](http://www.google.com/chrome/intl/en/eula_text.html)

---

### Post by LightB on 2010-01-27
chrome will be good for google if it's successfull. linux is just going to be flying around in the wind like a leaf, get used to it. but it will not go away.

---

### Post by .•*´ on 2010-01-27
Been better done with Unix.

---

### Post by ZarathustraDK on 2010-01-27
I would say that the BSD-license is freer than the GPL.

But I would also say that the GPL is more benevolent than the BSD-license.

The BSD-license is for people who believe all humans are altruistic angels (insofar they believe that the BSD-license is a Good Thing(tm) of course), or people who don't give a damn about information-freedom (they want the benefits of free coding, but also want to be able to take their stuff and leave).

That's what I like about the GPL. It realizes that humans can be bastards, and builds in a safety against it.

---

### Post by LightB on 2010-01-27
> **.•*´ said:**
> Been better done with Unix.

But not as good as on BeOS.

---

### Post by LightB on 2010-01-27
> **ZarathustraDK said:**
> I would say that the BSD-license is freer than the GPL.

But I would also say that the GPL is more benevolent than the BSD-license.

The BSD-license is for people who believe all humans are altruistic angels (insofar they believe that the BSD-license is a Good Thing(tm) of course), or people who don't give a damn about information-freedom (they want the benefits of free coding, but also want to be able to take their stuff and leave).

That's what I like about the GPL. It realizes that humans can be bastards, and builds in a safety against it.

No, BSD is code for "here you go, corporations, come violate this code and throw it away when you're done". Like FreeBSD, Apple's buttboy.

---

### Post by Simian Man on 2010-01-27
> **LightB said:**
> No, BSD is code for "here you go, corporations, come violate this code and throw it away when you're done". Like FreeBSD, Apple's buttboy.

No, the BSD license is for people who want their work to be useful to as many people as possible.  The GPL has a "if you're not with us you're against us" mentality that goes against the grain of Open Source IMHO.

For example, I write code using the MIT license (basically the same as BSD).  Anybody can use and modify my code be it for a commercial project, or open source project (whether GPL or not).  However I can't incorporate code from GPL projects because I'm apparently not on the same team as them.

BTW large corporations can usually avoid using open source code if they want to; look at Microsoft or Apple prior to OSX.  Granted Apple modified BSD because it was more convenient than starting from scratch again, but they could have if they had to.  Who GPL really hurts most is smaller companies that don't have the resources to replace whatever GPL code they need themselves.

---

### Post by k64 on 2010-01-27
[http://www.pcworld.com/businesscenter/article/182289/the_future_of_linux_is_google.html](http://www.pcworld.com/businesscenter/article/182289/the_future_of_linux_is_google.html)

---

### Post by n0dix on 2010-01-27
> **k64 said:**
> [http://www.pcworld.com/businesscenter/article/182289/the_future_of_linux_is_google.html](http://www.pcworld.com/businesscenter/article/182289/the_future_of_linux_is_google.html)

The best of the link it's this part, in my opinion:
*"Whether a Chrome OS beta rolls out this week, next week, next month, or next year, its success will depend heavily on the vast community of sophisticated users and developers who have helped to create such a staggering array of Linux distributions from the kernel up over the last 18 years. Google's name and industry clout can only take a new OS so far."*

it's fundamental that the Google Chrome SO be tested for the community, and the first to do it, of course, is Linux.

---

### Post by cascade9 on 2010-01-28
> **k64 said:**
> [http://www.pcworld.com/businesscenter/article/182289/the_future_of_linux_is_google.html](http://www.pcworld.com/businesscenter/article/182289/the_future_of_linux_is_google.html)

> Now Google is eyeing somewhat larger devices with [Chrome OS]("http://www.pcworld.com/article/168028/google_announces_chrome_os.html"), an open-source operating system for x86 and ARM-based netbooks

Gah!!!! 

ITS not open source! ](*,)

I'm sick of this, even 'professional' places cant seem to get it. #-o

Idiots. Or willfully blind.

---

### Post by earthpigg on 2010-01-30
> **cascade9 said:**
> Gah!!!! 

ITS not open source! ](*,)

I'm sick of this, even 'professional' places cant seem to get it. #-o

Idiots. Or willfully blind.

its ok, in his announcement of a first-of-kind policy for open source in US City gov't, the san fran mayor made [this]("http://mashable.com/2010/01/22/open-source-san-francisco/") error:

> The underlying source code is not copyrighted and therefore available free of charge to read, modify, and build upon.

---

### Post by jonathank89 on 2010-01-30
Wow, I really didn't expect much of a discussion around this, but wow! I honestly hadn't thought about the licences the code was under and now that I've thought about it, Google seems to have made a clear distinction between Chrome and Chromium. I would like to know how does the licensing work in regards to Chromium being barebones Ubuntu and that having it's own license and then there's the Linux Kernel being GPLv2? How do they co-mingle? And how does that effect the release of source code?

Some of you in this thread really opened my eyes to the fact that Google can make changes to Chromium and then ship it as Chrome, but if you think about it, it doesn't make much sense for them to hold back on the community. I feel that the biggest push behind the product will be the Linux community. Based on this, I think it would be foolish for them not to release source code and if publicly caught doing so that's bad PR.

I'd like to just grab the steering wheel here and turn back to  the original question, "Is Google's Chrome OS Good for Linux?". As I mentioned in my piece, which I'm going to have to update/rewrite, with regards to the open source-ness..or lack thereof, the best way Google can help Linux is if hardware vendors start releasing drivers that actually work! I'm not too pushed about the drivers being open source (it would be great though) and I'm sure a lot of you might feel differently, but that's just not something companies like to do (eg. nVidia & ATI).

As I've said before, ultimately I feel that Google's name will help with drive support and the like which can give Linux what it's been lacking for a long time and really give Linux an opportunity to shine!

---

### Post by k64 on 2010-01-30
Chrome OS may, by itself, not be that feature-rich. However, what if somebody edited the "build_chrome.sh" script to take advantage of JHBuild instead of Make to build code, not to mention building GNOME instead of Chrome? They would end up with a new Linux distro. If I had to do this I would, and I would upload the image file that results onto Launchpad. You'll be surprised.

---

### Post by LightB on 2010-01-30
> **Simian Man said:**
> No, the BSD license is for people who want their work to be useful to as many people as possible.  The GPL has a "if you're not with us you're against us" mentality that goes against the grain of Open Source IMHO.

For example, I write code using the MIT license (basically the same as BSD).  Anybody can use and modify my code be it for a commercial project, or open source project (whether GPL or not).  However I can't incorporate code from GPL projects because I'm apparently not on the same team as them.

BTW large corporations can usually avoid using open source code if they want to; look at Microsoft or Apple prior to OSX.  Granted Apple modified BSD because it was more convenient than starting from scratch again, but they could have if they had to.  Who GPL really hurts most is smaller companies that don't have the resources to replace whatever GPL code they need themselves.

Apple took BSD because it was there. OS9 was a joke and they had to take from open source to produce something good. Seems true for large software like an OS or kernel. And if somebody wants to consider MSWin a technological winner, that's cool but I have no further comment on that.

Your isolated experience doesn't define what's best for the entire landscape, either. I'm sure there's tons of people working in the technology sector of smaller companies who would negate your side of the argument. Not to say that BSD shouldn't exist nor that it's a bad license. It's fine for those who require it, like poor Apple. I just personally don't like it and that is just my opinion. And of course there is at least as much of a demand for the GPL side of things because it can't be destroyed and diminished by corporate interests, which is the whole point of its existence.

---

### Post by Simian Man on 2010-02-01
> **LightB said:**
> Apple took BSD because it was there. OS9 was a joke and they had to take from open source to produce something good. Seems true for large software like an OS or kernel. And if somebody wants to consider MSWin a technological winner, that's cool but I have no further comment on that.
OS 9 was a decent operating system for it's time, and Windows is absolutely a technologically sound OS.  It amazes how much they've been able to refine it while still keeping binary compatibility with ancient software (a requirement Linux sure doesn't have).

But the key is that Apple absolutely could have written a Unix-like kernel themselves.  [IBM]("http://en.wikipedia.org/wiki/IBM_AIX_%28operating_system%29"), [HP]("http://en.wikipedia.org/wiki/HP-UX"), [SGI]("http://en.wikipedia.org/wiki/IRIX"), [Sun]("http://en.wikipedia.org/wiki/Solaris_%28operating_system%29") and [SCO]("http://en.wikipedia.org/wiki/UnixWare") did.  And even if Apple didn't want to, they could have licensed a kernel from one of those companies I mentioned.  Anyway if this is such a problem with BSD style licensing, wouldn't you be able to come up with more than one example?

> **LightB said:**
> Your isolated experience doesn't define what's best for the entire landscape, either. I'm sure there's tons of people working in the technology sector of smaller companies who would negate your side of the argument.
OK, well when those other people you speak of are ready to argue for you, you can point them to this thread mmkay?

> **LightB said:**
> Not to say that BSD shouldn't exist nor that it's a bad license. It's fine for those who require it, like poor Apple. I just personally don't like it and that is just my opinion. And of course there is at least as much of a demand for the GPL side of things because it can't be destroyed and diminished by corporate interests, which is the whole point of its existence.
Right.  The point of it's existence is *to lock out anybody using a different license*, not freedom.  That's fine if that's what you want to do, but if your goal is to create something that is as free as possible, the BSD license is obviously better suited.

---

### Post by boobembe on 2010-02-15
> **Simian Man said:**
> 
OK, well when those other people you speak of are ready to argue for you, you can point them to this thread mmkay?

Simian, you never provided any advocates to support YOUR assertion that the GPL hurts smaller companies. So I find it funny that once LightB questions your claim, you suddenly apply such a  rigorous standard. And frankly I have to side with LightB on that issue. It's common sense that there are literally thousands of smaller companies who benefit from some kind of Linux server running Apache, MySQL and PHP, all of which are published under the GPL. And that's just the most obvious example. The thing with the GPL is, you can use it for commercial purposes and even extend the code without publishing it, just as long as you don't ship the application to any other users. But let's have a look at your argument, that publishing Chrome under the GPL would hurt smaller companies. That maybe true for a company who wants to take Chrome and improve it to the extent, that they would be able to take a significant market share away from Google selling their improved (hidden code) version. Does that sound like a realistic scenario for a smaller company to you? How many companies could make it this way? You might argue that your point is more pertinent with regards to other types of software, and that maybe another discussion, but as for here, I don't see how it applies. But more to the point, even if there were such a business model, I as an end user am not really interested in that, and I will choose what's best for me, and that in my opinion includes the guarantee, that the software I run is and always will be open source and open to inspection in all parts. For that reason I will not run nor support Google's approach.

---

### Post by arnab_das on 2010-02-15
(my understanding of linux and ubuntu has changed overnight after i saw a video of the ubuntu developer summit.

[http://www.youtube.com/watch?v=olDMAYD7t3k](http://www.youtube.com/watch?v=olDMAYD7t3k)

if u can, kindly watch it. its pretty lengthy though, around 56 mins)

anyway, the thing is, if google makes an OS (which it obviously is) it brings much needed attention to linux. thats the ultimate thing. i hope with the arrival of google to the linux arena, there will be more opportunities for developers to come up with better stuff, be it softwares, drivers, codecs, etc.

---

### Post by themarker0 on 2010-02-15
My personal thoughts. Plain and simple.

Google has made such a small distro, it will be hard to use without it being on the internet. Like if you are out of range, or simply don't have wireless card from verzion (Or whoever does it, i don't know i'm not from the USA) You will be bored. It may seem stupid (My point) But it could be a factor.

---

### Post by neu5eeCh on 2010-02-15
> **earthpigg said:**
>  [snip] ...but when one person points out, as the user above did, that the full products known as Chrome OS and Chrome Browser are not open source at all, and that Chromium OS and Chromium are open source... folks will be tempted to say "Same thing" and let the waters be murky and muddy. [...] 

Wow. OK. Now the waters are even murkier.

Here's what I thought: 

1.) Google Chrome is a browser.
2.) Chromium OS and Chrome OS are the same thing.
3.) Chromium Browser refers to Chrome OS and Chromium OS.

Ergo:

Chromium OS = Chrome OS = Chromium Browser 

But does not =  Google Chrome Browser.

Is this right?

---

### Post by p_quarles on 2010-02-16
> **VTPoet said:**
> Wow. OK. Now the waters are even murkier.

Here's what I thought: 

1.) Google Chrome is a browser.
2.) Chromium OS and Chrome OS are the same thing.
3.) Chromium Browser refers to Chrome OS and Chromium OS.

Ergo:

Chromium OS = Chrome OS = Chromium Browser 

But does not =  Google Chrome Browser.

Is this right?
No. Chromium is the unbranded source code for the browser, Chrome is the branded binary that Google distributes on its web site. Same with Chrome OS vs. Chromium OS. 

Chromium, as well, is only the Google-authored portion of the browser's code. There are other components, notably webkit, that are already released under open-source licenses. 

Anyway, my understanding is that currently the only difference between Chrome and Chromium is branding. In addition, the OS is tightly integrated with the hardware designed for it that it may be unrealistic to install a source code build on commodity hardware.

---

### Post by Simian Man on 2010-02-16
> **boobembe said:**
> Simian, you never provided any advocates to support YOUR assertion that the GPL hurts smaller companies. So I find it funny that once LightB questions your claim, you suddenly apply such a  rigorous standard. And frankly I have to side with LightB on that issue. It's common sense that there are literally thousands of smaller companies who benefit from some kind of Linux server running Apache, MySQL and PHP, all of which are published under the GPL.

Umm no, not exactly.  Actually Apache is released under the [Apache License]("http://en.wikipedia.org/wiki/Apache_License") which is a non-copyleft license.  That means it is actually much closer to the BSD license than the GPL.  Also PHP is released under the PHP license which, again, has no copy-left restriction so is closer to BSD than GPL.  Of the examples you gave, only MySQL actually even uses the GPL.

And it's beside the point anyway because, for someone who merely wishes to use the software as is - which is the vast majority of LAMP users - it doesn't make a lick of difference which license the software uses.  It only matters to them that it's free of charge.

Where it actually becomes an issue is when the user wishes to extend the software either by modifying the sources or by using the software as a library for new applications.

And there are *many* examples of the GPL hurting smaller companies, but they are not really noteworthy or memorable because nobody is going to remember that company X chose *not* to use product Y.  If you have worked in the software industry at all, you'll know that most companies avoid the GPL like the PLAGUE.

> **boobembe said:**
> And that's just the most obvious example. The thing with the GPL is, you can use it for commercial purposes and even extend the code without publishing it, just as long as you don't ship the application to any other users.
Well that's only useful in a very small number of situations isn't it?  And if you think it's a good thing that people can modify GPL'd code for profit in some situations, how can it be a bad thing that people can modify BSD'd code for profit in any situation??

> **boobembe said:**
> But let's have a look at your argument, that publishing Chrome under the GPL would hurt smaller companies.
That wasn't actually my argument at all - though I can see how you may think that given what thread this is.  I was just defending the license in general.

Both styles of licensing have their place - just as proprietary licensing has its place.  The GPL is better when you want to restrict people to using the GPL license for their work: either to entice them to buy a commercial like QT used to or because you want to lock out everything but the FSF's narrow view of what software should be.

And BSD style licensing is better when you actually want your work to be free to everyone regardless.

---

### Post by swoll1980 on 2010-02-16
> **cascade9 said:**
> I've said it before, and I'll say it again...chrome is NOT open source.



[http://www.google.com/chrome/intl/en/eula_text.html](http://www.google.com/chrome/intl/en/eula_text.html)



[http://code.google.com/chromium/terms.html](http://code.google.com/chromium/terms.html)

Because chromium is a BSD licence they can move over whatever code they want to chrome and don't have to provide any source code...and they are under no obligation to move any code over if they so wish. They can also put in whatever code they want into chrome and no give any indication that the code is different to chromium. 

Brilliant gambit from google. Do some work on chrome, release the code as chromium under the BSD licence, insinuate that chrome is open source, (but keep it closed) and get coders for free. My hat is off to the cunning devils. But I'll never run chrome.

Google is one of the top 10 corporate contributers to the Linux kernel. Every time you boot Linux you're using Google code.

---

### Post by earthpigg on 2010-02-16
> **VTPoet said:**
> 
[snip]
Chromium OS = Chrome OS = Chromium Browser 

But does not =  Google Chrome Browser.

Is this right?

not quite.

Chromium OS + Branding = Chrome OS ***as far as we know.***

and Chrome/Chromium OS includes Chromium/Chrome.

Chromium Browser + Branding = Chrome Browser ***as far as we know.***

before compiling chromium into chrome, what additional stuff (spyware?) gets slipped in at the last minute? we have absolutely no idea, because we cannot see it.

and what if that additional stuff creates security vulnerabilities? the community won't be able to fix them and send the fixes upstream to google, because they won't be able to see the underlying source code that creates the vulnerability.

so the actual formula is this:

Chromium OS + Branding + *stuff we don't know about* = Chrome OS
Chromium Browser + Branding + *stuff we don't know about* = Chromium Browser

now, maybe there is no *stuff we don't know about*. maybe im being paranoid.

if that is the case, however, ***why not release the source code that the binary is directly based on (branding and all)?*** leave it to the self-compilers to remove the branding prior to redistributing, if they chose to redistribute. i am fairly certain that is how firefox does it.

the only reason to differentiate the two is because there is indeed *stuff we don't know about*.

the formula my proposal would create is:

Chrome - Google Branding = Chromium (or whatever you, the person compiling, feel like naming it)

maybe even include a flag that automatically strips the branding for the self-compiler?

---

### Post by p_quarles on 2010-02-16
> **earthpigg said:**
> not quite.

Chromium OS + Branding = Chrome OS ***as far as we know.***

and Chrome/Chromium OS includes Chromium/Chrome.

Chromium Browser + Branding = Chrome Browser ***as far as we know.***

before compiling chromium into chrome, what additional stuff (spyware?) gets slipped in at the last minute? we have absolutely no idea, because we cannot see it.

and what if that additional stuff creates security vulnerabilities? the community won't be able to fix them and send the fixes upstream to google, because they won't be able to see the underlying source code that creates the vulnerability.

so the actual formula is this:

Chromium OS + Branding + *stuff we don't know about* = Chrome OS
Chromium Browser + Branding + *stuff we don't know about* = Chromium Browser

now, maybe there is no *stuff we don't know about*. maybe im being paranoid.

if that is the case, however, ***why not release the source code that the binary is directly based on (branding and all)?*** leave it to the self-compilers to remove the branding prior to redistributing, if they chose to redistribute. i am fairly certain that is how firefox does it.

the only reason to differentiate the two is because there is indeed *stuff we don't know about*.

the formula my proposal would create is:

Chrome - Google Branding = Chromium (or whatever you, the person compiling, feel like naming it)

maybe even include a flag that automatically strips the branding for the self-compiler?
The problem with this argument is that it is true of every single binary in the history of software. It's really impossible to know that a binary isn't doing something you don't know about. If you know what you're looking for, you may be able to discover these things, but there is really no foolproof way of knowing that a binary was compiled from the source code the developer provides for it. 

So, I think the burden lies on the person making the accusation to provide some reasonable grounds for suspicion. And "they could do it if they wanted to" is not reasonable grounds for suspicion. You could apply that logic to a whole host of situations that range from the very likely ("identity thieves go dumpster diving to get personal info") to the far-fetched ("my neighbor is piping poison gas into my house at night"), and it would be equally true for all scenarios. Thus, "they could do it if they wanted to" does not tell you anything about the actual probability of a thing being done. 

I'm certainly not trying to dismiss your concerns, but trying to point out a basic problem with how you are framing them. If you have reasons to believe that Google would surreptitiously add spyware to an open source project (and it would have to go to great lengths to hide this, given the size of that corporation), an open discussion about those reasons would be a valuable thing, I think.

---

### Post by mickie.kext on 2010-02-16
> **earthpigg said:**
> 
so the actual formula is this:

Chromium OS + Branding + *stuff we don't know about* = Chrome OS


This part is not possible for Linux based OS because of GPL. They have to give source of Chrome OS.

They do not have to give source of Chrome Browser because it is BSD licensed.

---

### Post by earthpigg on 2010-02-16
> The problem with this argument is that it is true of every single binary in the history of software. It's really impossible to know that a binary isn't doing something you don't know about. If you know what you're looking for, you may be able to discover these things, but there is really no foolproof way of knowing that a binary was compiled from the source code the developer provides for it.

compare the md5sums of the binary provided to the one you compile yourself with the same flags and version of the compiler on the same architecture. 

the exact same mathematical mumbo jumbo would be performed both times if the source is indeed the exact source the binary is based on.

i think that would work. can someone confirm? 

this is only possible if the source provided includes the branding and everything else, of course.

in the case of FF (source includes mozilla branding), if you found any differences you could go "WTF mozilla?"

in the case of Chrome/ium, you would expect the md5sums to be different due to the branding difference... if the branding was kept in, it would be easy to verify that the binary is indeed from the exact same source code as provided.

> So, I think the burden lies on the person making the accusation to provide some reasonable grounds for suspicion. And "they could do it if they wanted to" is not reasonable grounds for suspicion.

burden lies on the accusor for a 'conviction' or for certainty of guilt. i am only expressing doubt.

their half-hearted open source ethos and creating murky waters regarding what is and is not open source (chromium is, chrome is not) is enough cause for suspicion. i don't know they are guilty of anything, and i don't know they are innocent either. as i pointed out, it would be incredibly easy for them to prove their innocence beyond any possible shadow of a doubt - include the branding in the source provided.

> [QUOTE]so the actual formula is this:

Chromium OS + Branding + stuff we don't know about = Chrome OS
This part is not possible for Linux based OS because of GPL. They have to give source of Chrome OS.

They do not have to give source of Chrome Browser because it is BSD licensed.[/QUOTE]

soo they include the full source of Chrome OS, and keep the stuff they want to hide in Chrome browser (included with Chrome OS)... the same way Linux Mint can include Flash in their distribution without providing the source code for Flash.

---

### Post by say2sky on 2010-02-18
> **earthpigg said:**
> compare the md5sums of the binary provided to the one you compile yourself with the same flags and version of the compiler on the same architecture. 

the exact same mathematical mumbo jumbo would be performed both times if the source is indeed the exact source the binary is based on.

i think that would work. can someone confirm? 

this is only possible if the source provided includes the branding and everything else, of course.

in the case of FF (source includes mozilla branding), if you found any differences you could go "WTF mozilla?"

in the case of Chrome/ium, you would expect the md5sums to be different due to the branding difference... if the branding was kept in, it would be easy to verify that the binary is indeed from the exact same source code as provided.



burden lies on the accusor for a 'conviction' or for certainty of guilt. i am only expressing doubt.

their half-hearted open source ethos and creating murky waters regarding what is and is not open source (chromium is, chrome is not) is enough cause for suspicion. i don't know they are guilty of anything, and i don't know they are innocent either. as i pointed out, it would be incredibly easy for them to prove their innocence beyond any possible shadow of a doubt - include the branding in the source provided.



soo they include the full source of Chrome OS, and keep the stuff they want to hide in Chrome browser (included with Chrome OS)... the same way Linux Mint can include Flash in their distribution without providing the source code for Flash.

learn a lot, thanks.

I hope to know if chromium and chromium OS source code is available and other user or open source community can compile it and release it under GPL, then this binary OS completed by community can be used to avoid any spyware or other malware possible. right?

another thing I hope to know is
if the 2d/3d driver used in chrome os is open source and can be used in other linux distribution? 

If the answer is yes, I think  Chrome OS Good for Linux.

---

