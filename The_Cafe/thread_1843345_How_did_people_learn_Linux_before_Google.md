---
title: "How did people learn Linux before Google?"
date: 2011-09-13
forum: The Cafe
---

### Post by ninjaaron on 2011-09-13
So, when I want to know how to do something with my computer, I google it, check on the forums, or check the ArchWiki (best wiki EVAR!).

I can't imaging trying to do get Linux to do stuff without Google, let alone with out WWW.

Maybe the "old-timers" can tell us how they learned back in the day.

---

### Post by haqking on 2011-09-13
> **ninjaaron said:**
> So, when I want to know how to do something with my computer, I google it, check on the forums, or check the ArchWiki (best wiki EVAR!).

I can't imaging trying to do get Linux to do stuff without Google, let alone with out WWW.

Maybe the "old-timers" can tell us how they learned back in the day.

Usenet

---

### Post by sffvba[e0rt on 2011-09-13
Man pages... and patience...


404

PS - Title seems to be missing a letter ;)

---

### Post by haqking on 2011-09-13
> **not found said:**
> Man pages... and patience...


404

PS - Title seems to be missing a letter ;)


+1

yeah that too and Usenet for problem sharing.

shame man and patience is not utilised still ;-)

---

### Post by SeijiSensei on 2011-09-13
Linux and the Internet grew up more or less together.  I started using Linux in 1994 when I was starting a business to help organizations connect to the Internet.  We started building gateway servers to provide connectivity, web, and mail services, and Linux was really the only option.  Our first distro was Slackware with kernel 1.1.59.

Many of the applications we used then, and largely still use today, were well-established in the UNIX world by then.  So I read books targeting BSD and SVR4 users on subjects like BIND and sendmail.  Craig Hunt's [TCP/IP Network Administration](http://shop.oreilly.com/product/9780596002978.do) was an invaluable resource.  

Our other major source of information was the now-defunct server-linux mailing list.  We were a small community in those days, and the list had many illustrious members of the Linux development team, [Alan Cox]("http://en.wikipedia.org/wiki/Alan_Cox") in particular.  Cox pretty much wrote the entire TCP/IP stack for early Linux kernels and played a major role in its development for years.  Another frequent contributor was [Donald Becker]("http://en.wikipedia.org/wiki/Donald_Becker") who was responsible for many of the network drivers in the kernel.

---

### Post by Erik1984 on 2011-09-13
No idea... would be a lot harde I guess. Started using Linux when Google was already popular.

---

### Post by ninjaaron on 2011-09-13
> **haqking said:**
> +1

yeah that too and Usenet for problem sharing.

shame man and patience is not utilised still ;-)

I only recenlty figured out that man read through less, and how less actually works.

At first, I didn't know how to search man pages, so they were useless.  When I learned a little more bash, I started using...```
echo "`man grep`" > grep-help
```
... to get the man pages into a normal text editor so I could search and navigate them more comfortably.

Then I started vim (and vifm and the vim plugin for firefox [pentadactyl]), and all my problems with navigating less disappeared.  My vote, for whatever it's worth, is that there should be something in the Ubuntu documentation about navigating man pages.  Most man pages are actually pretty helpful, once you learn how to read them.

---

### Post by haqking on 2011-09-13
> **ninjaaron said:**
> I only recenlty figured out that man read through less, and how less actually works.

At first, I didn't know how to search man pages, so they were useless.  When I learned a little more bash, I started using...```
echo "`man grep`" > grep-help
```... to get the man pages into a normal text editor so I could search and navigate them more comfortably.

Then I started vim (and vifm and the vim plugin for firefox [pentadactyl]), and all my problems with navigating less disappeared.  My vote, for whatever it's worth, is that there should be something in the Ubuntu documentation about navigating man pages.  Most man pages are actually pretty helpful, once you learn how to read them.

 you can do man man to find out how to use man ;-)

They can be read online. 

[http://linuxmanpages.com/](http://linuxmanpages.com/)

[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)

with **man** and **apropos** then using the terminal just takes patience.

---

### Post by Ric_NYC on 2011-09-13
Good question!

---

### Post by Jesus_Valdez on 2011-09-13
Before there was Google there was... Altavista!

---

### Post by PaulW2U on 2011-09-13
> **ninjaaron said:**
> Maybe the "old-timers" can tell us how they learned back in the day.

We bought a book. :D

---

### Post by Dragonbite on 2011-09-13
Yahoo & DogPile for internet search
[[COLOR="Blue"]LinuxQuestions.org Forum[/COLOR]]("http://www.linuxquestions.org/questions/")
A friend of mine (boy, I badgered him!)
and a LOT of trial-and-***error***! 
(notice the emphasis on "error" :guitar:)

---

### Post by decoherence on 2011-09-13
I got my start on IRIX and NetBSD and learned them using the "read the fine manual" method. I should note that the manual pages for both systems were much better than most linux man pages at the time (some would say this is still the case, at least with netbsd)

---

### Post by Dragonbite on 2011-09-13
When I moved from Red Hat (after printing a big-honking manual), I moved to Gentoo because they had some great documentation.  Plus, since it was more command-line and working manually more often, it gave me a great chance to learn.  Now I am using Ubuntu, Fedora and Google because I want the answers NOW!

---

### Post by TeoBigusGeekus on 2011-09-13
I once created a [thread]("http://ubuntuforums.org/showthread.php?t=1186517") about this.

---

### Post by Dangertux on 2011-09-13
Usenet, IRC, and books

---

### Post by DZ* on 2011-09-13
> **ninjaaron said:**
> So, when I want to know how to do something with my computer, I google it, check on the forums, or check the ArchWiki (best wiki EVAR!).

I can't imaging trying to do get Linux to do stuff without Google, let alone with out WWW.

Maybe the "old-timers" can tell us how they learned back in the day.

Old-timers? ;) Linux is not THAT old. You can easily be in your 20s using linux since when first distros appeared. Internet and search engines did exist when linux distros were just starting to appear on floppies. There were also plenty of "forums", or more correctly, newsgroups on usenet. BTW, that is where Linus posted an announcement for his intention to develop a new OS. The linux community is still very active on usenet. Some people prefer Usenet as it provides mechanisms to implement things like score-files, kill-files, and general header searches in the client that you cannot really do on an internet forum. For example, you can order posts or threads by posters or subjects, according to your own scoring system.

All in all, not much has changed: 99.99% of stuff on the internet is still bad advice or worse ;)

---

### Post by DZ* on 2011-09-13
I've been on Linux since 1995. The biggest problem that greatest minds struggled with back then, and cannot solve even to this day is how do you search internet for help in setting up your internet connection?

---

### Post by khelben1979 on 2011-09-13
The man pages still works good today since the documentation pages are linked to the actual software version you got in your Linux system, it's still quite efficient, in my opinion.

---

### Post by MG&amp;TL on 2011-09-13
I agree with OP, but that's only because I always ask 'why?' and want to do really weird stuff the system's not really designed to do. manpages do fine if you're not pushing the boundaries. I guess that's what geek conferences were for.

---

### Post by drawkcab on 2011-09-13
I basically just used windows and learned nothing about computers through most of the 90s.

I had some awareness of Linux but I wasn't inspired to learn more until the malware plague of the early '00s became to overwhelming for my windows 98 system.  Eventually a friend on IRC talked me into installing warty warthog and I've been a convert and evangelist ever since.

---

### Post by oldos2er on 2011-09-13
> **ninjaaron said:**
> So, when I want to know how to do something with my computer, I google it, check on the forums, or check the ArchWiki (best wiki EVAR!).

I can't imaging trying to do get Linux to do stuff without Google, let alone with out WWW.

Maybe the "old-timers" can tell us how they learned back in the day.

comp.os.linux.*

Usenet, in other words.

---

### Post by galacticaboy on 2011-09-13
I am not an oldie but I just wanted to say that is it was not for these forums, I would not be using Linux today. These forums were and still are my crutch for using Linux.

---

### Post by qamelian on 2011-09-13
> **PaulW2U said:**
> We bought a book. :D
Or bought a boxed copy of a distro. SuSE Professional included to manuals offering over 600 pages of educational linux-y goodness! Mandrake was similarly packaged.

---

### Post by docbop on 2011-09-13
> **ninjaaron said:**
> So, when I want to know how to do something with my computer, I google it, check on the forums, or check the ArchWiki (best wiki EVAR!).

I can't imaging trying to do get Linux to do stuff without Google, let alone with out WWW.

Maybe the "old-timers" can tell us how they learned back in the day.

They actually read man pages, they studied code, they posted questions on USENET, and something people avoid today they got together and talked to each other.   It was like the apprenticeship model in some industries.  

Today too many just want answers and don't care why something is the answer, or what caused issue or what concept is.

---

### Post by aura7 on 2011-09-13
I have learned using linux mainly because of Google. I am a late user of Linux, started using it officially from July 2010, before that I was a hobbyist, I dedicate my Linux knowledge to Google Search.

---

### Post by mips on 2011-09-13
Usenet
Telnet based chat rooms
IRC

---

### Post by iponeverything on 2011-09-13
rfc's
newsgroups
the source code

---

### Post by Erik1984 on 2011-09-13
> **Dragonbite said:**
> Yahoo & DogPile for internet search
[[COLOR=Blue]LinuxQuestions.org Forum[/COLOR]]("http://www.linuxquestions.org/questions/")
A friend of mine (boy, I badgered him!)
and a LOT of trial-and-***error***! 
(notice the emphasis on "error" :guitar:)
Internet nostalgia :p Yahoo, AltaVista, AlltheWeb. Dogpile were the places to be for searching. I first hated Google for the childish colors. What's that stupid Google? Who is going to use THAT? AltaVista is so much better... Guess history proved me wrong.

---

### Post by MBybee on 2011-09-13
> **qamelian said:**
> Or bought a boxed copy of a distro. SuSE Professional included to manuals offering over 600 pages of educational linux-y goodness! Mandrake was similarly packaged.

Depends on where you live, I suppose - I had a subscription to FreeBSD from 2.2.1 -> 6x, and bought those huge books at my local store all the time. Linux had no such easy help, but I could always look up problems on my BSD or Solaris box in the early days. Newsgroups were huge, I was on the comp.os groups until about 2007 or so.

I think I only ever bought 4 boxed Linux editions - Corel Linux, Caldera Linux, and two or three of the Redhat 7x - 8x editions. I still have all the books, but the inflatable Tux from Corel Linux died years ago.

---

### Post by ninjaaron on 2011-09-13
> **DZ* said:**
> Old-timers? ;) Linux is not THAT old. You can easily be in your 20s using linux since when first distros appeared.

Yeah, If you started using it when you were ten. :p

But really, there are always a few of those types out there.  Still, I doubt few but the extremely gifted kids were prepared to use linux in the state it was in when Debian, Slackware, and Red Hat came out.  Not as many people grew up with computers even 15 years ago.

---

### Post by Retlol on 2011-09-14
> **ninjaaron said:**
> So, when I want to know how to do something with my computer, I google it, check on the forums, or check the ArchWiki (best wiki EVAR!).

I can't imaging trying to do get Linux to do stuff without Google, let alone with out WWW.

Maybe the "old-timers" can tell us how they learned back in the day.

There was "an internet" before google came along, in case you didn't know.

---

### Post by ibutho on 2011-09-14
Usenet, manpages and a lot of trial and error.

---

### Post by spynappels on 2011-09-14
I still have shelves full of Apress and O'Reilly books, and man pages are great, especially now that you can get them online.

+ forums.

---

### Post by HermanAB on 2011-09-14
Before Google, we used Gopher, Altavista, Archie and WAIS...

---

### Post by Grenage on 2011-09-14
It's not just Linux, it's everything!

Need a product manual or to check a warranty? Use the net.
Want to find out when a restaurant closes? Use the net.
Can't remember your car tyre pressure?....
Yellow Pages, what's that?

When the current generation lose internet access, it's as if they regressed to primates playing in the mud.  That's a generalisation, but still; the same goes for problem solving.

---

### Post by the kernel on 2011-09-14
I used Yahoo :-)
 
and before that I used Webcrawler
 
Usually the website had some instructions for installation. For any tech questions there was always the newsgroups. I never used Linux before I got online in 1996.

---

### Post by PaulW2U on 2011-09-14
> **qamelian said:**
> Or bought a boxed copy of a distro. SuSE Professional included to manuals offering over 600 pages of educational linux-y goodness! Mandrake was similarly packaged.

Yes, I'd forgotten about those. I bought several from a bookshop that was selling them off cheap, in maybe 1999 or 2000? I could never get anything to work properly so although I saw the very early versions of Gnome and KDE I didn't stick around to see how they developed.

So I went back to Windows where I knew what I was doing. ](*,)

---

### Post by Off Shore on 2011-09-14
Linux kernel first appeared circa 1991. Resources for Linux developers and 
some users were well established by then and, as some contributors to this thread have noted, incuded IRC, Usenet and various written materials.
 
Initial documentation for Linux was patchy and best described as poor. This has improved over time but still lags well behind that provided by various authors and organisations for the Windows platform.
A point of interest here, almost every serious Windows programmer would, at one time, have had  a copy of Petzold to hand. I wonder how far Windows programming would have advanced without him. 
What a shame he was never tempted to take on some documentation or reference works for Linux.

---

### Post by haqking on 2011-09-14
> **Off Shore said:**
> Linux kernel first appeared circa 1991. Resources for Linux developers and 
some users were well established by then and, as some contributors to this thread have noted, incuded IRC, Usenet and various written materials.
 
Initial documentation for Linux was patchy and best described as poor. This has improved over time but still lags well behind that provided by various authors and organisations for the Windows platform.
A point of interest here, almost every serious Windows programmer would, at one time, have had  a copy of Petzold to hand. I wonder how far Windows programming would have advanced without him. 
What a shame he was never tempted to take on some documentation or reference works for Linux.


very petzold reminiscent book for linux though here [http://www.nostarch.com/tlpi](http://www.nostarch.com/tlpi)

---

### Post by Off Shore on 2011-09-14
> **haqking said:**
> very petzold reminiscent book for linux though here [http://www.nostarch.com/tlpi](http://www.nostarch.com/tlpi)
 
That looks just the ticket. Its a jolly good find thank you.

---

### Post by haqking on 2011-09-14
> **Off Shore said:**
> That looks just the ticket. Its a jolly good find thank you.

no worries, its a good read.

alot cheaper on[ Amazon]("http://www.amazon.co.uk/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=978-1-59327-220-3+&x=0&y=0")

---

### Post by fatality_uk on 2011-09-14
I remember 9.6k modems the size of a shoe box :) Does that register me for "Old Timer" status. MANPAGES was really all we had back in the day. There was a few Computer Clubs where the serious geeks showed us mere mortals all kinds of neat stuff, including Linux

---

### Post by haqking on 2011-09-14
> **fatality_uk said:**
> I remember 9.6k modems the size of a shoe box :) Does that register me for "Old Timer" status. MANPAGES was really all we had back in the day. There was a few Computer Clubs where the serious geeks showed us mere mortals all kinds of neat stuff, including Linux


I have an acoustic coupler in the attic ;-)

---

### Post by DZ* on 2011-09-14
> **ninjaaron said:**
> Still, I doubt few but the extremely gifted kids were prepared to use linux in the state it was in when Debian, Slackware, and Red Hat came out.  Not as many people grew up with computers even 15 years ago.

Linux had GUI, DE, netscape, emacs and all the other stuff unixes like Sun OS had at the time. You had to enter correct values when setting up the display or fry the monitor, and setting up dial up was also less than straightforward. But if you had a cable connection it "just worked". I remember compiling the kernel with every new version, but I forgot whether that was really necessary or just for fun. Can't remember any other major troubles.

---

### Post by MasterNetra on 2011-09-14
> **DZ* said:**
> I've been on Linux since 1995. The biggest problem that greatest minds struggled with back then, and cannot solve even to this day is how do you search internet for help in setting up your internet connection?

Nah that's solved by using another machine that is setup to search for help or before hand have the documentation you would need stored on a USB drive, or some drive your not installing Linux onto.

---

### Post by MBybee on 2011-09-14
> **MasterNetra said:**
> Nah that's solved by using another machine that is setup to search for help or before hand have the documentation you would need stored on a USB drive, or some drive your not installing Linux onto.

USB? :D
During the timeframe we're referring to here, the floppy was still considered a reasonable transfer medium - and server drives were smaller than your normal thumbdrive now. I installed Debian off a big pile of floppies, and FreeBSD was considered pretty awesome because it came on the (still somewhat new) CD media. The Ports collection on CD was really the biggest advantage it had over the nascent Linux distros. No wasting money and time downloading everything and trying to find the dependencies. It was all right there local.

---

### Post by haqking on 2011-09-14
> **MBybee said:**
> USB? :D
During the timeframe we're referring to here, the floppy was still considered a reasonable transfer medium - and server drives were smaller than your normal thumbdrive now. I installed Debian off a big pile of floppies, and FreeBSD was considered pretty awesome because it came on the (still somewhat new) CD media. The Ports collection on CD was really the biggest advantage it had over the nascent Linux distros. No wasting money and time downloading everything and trying to find the dependencies. It was all right there local.

i think he meant it is now solved by using that, as the post he was quoting mentioned to this day.

---

### Post by MBybee on 2011-09-14
> **haqking said:**
> i think he meant it is now solved by using that, as the post he was quoting mentioned to this day.

Ahh - thanks. That would make a great deal more sense.
Hard to imagine being truly 'disconnected' in this day and age - you have so many connected fallbacks. Phones, libraries, coffee shops, etc. Tons of resources.

---

### Post by ninjaaron on 2011-09-14
> **DZ* said:**
> Linux had GUI, DE, netscape, emacs and all the other stuff unixes like Sun OS had at the time. You had to enter correct values when setting up the display or fry the monitor, and setting up dial up was also less than straightforward. But if you had a cable connection it "just worked". I remember compiling the kernel with every new version, but I forgot whether that was really necessary or just for fun. Can't remember any other major troubles.

I somehow don't see a child getting through an install process like that.  I don't think most kids even today, being more tech-savy, could get through an installation of Gentoo, which is significantly simplified from Linux installation in the early nighties, or so I'm told.  I was just a kid, playing with my Dad's Apple IIe.  We didn't need a hex editor or anything. :p

---

### Post by DZ* on 2011-09-15
> **ninjaaron said:**
> I somehow don't see a child getting through an install process like that.  I don't think most kids even today, being more tech-savy, could get through an installation of Gentoo, which is significantly simplified from Linux installation in the early nighties, or so I'm told.  I was just a kid, playing with my Dad's Apple IIe.  We didn't need a hex editor or anything. :p

How hard was it for you to install Apple DOS on it?

---

### Post by BlacqWolf on 2011-09-15
Well, of course I'm not an old-timer, but I learned mostly from my friend who introduced me to Ubuntu (and therefore Linux), and almost never used Google. After I learned about it, I found most of the stuff about Linux to be very easy.

Thing about Linux is that it's quite easy when you get used to it. I know quite a few Linux commands and know my way around a lot of common Linux-based OSes, such as Ubuntu, when I've known about Ubuntu and Linux for about 3 years. Compared to Windows/MS-DOS which I essentially spent a whole lifetime with, and of course I know my way around Windows easily, which figures because Windows is just a GUI for DOS/NT, but when it comes to MS-DOS alone... I know like 5 or so commands.

---

### Post by slackthumbz on 2011-09-15
I read... whaddaya call 'em... papery things... books! Yeah that's it, books... don't see 'em around so much these days. Probably endangered or somethin'

...

---

### Post by snip3r8 on 2011-09-15
Following command:
```

sudo gotofuture --google | w3m

```

---

### Post by Cope57 on 2011-09-15
IRC, and [Gopher]("http://practical-tech.com/operating-system/gophering-the-internet/") is what I recall.

I still use IRC.

---

### Post by FormatSeize on 2011-09-15
> **not found said:**
> Man pages... and patience...
This is how I learned earlier on in 2009. When I first started, I simply did not understand too much about the stuff that people talked about here, and too fearful of looking stupid to sign up and ask questions. So I read, read, and read the man pages, and practiced very simple things like copying, moving things, and using apt-get. 
 
I did this because I could hardly understand the things that I found on Google, and being so new I didn't know what to cut and paste because I had been scared crap-less by the "DOOMSDAY COMMANDS: BEWARE" thread stickied at the top of one of the first pages that I saw upon visiting here. 
 
Once I was comfortable, I signed up here and asked questions; and if I could look back on them, I would probably still wonder why I couldn't figure that out in light of the types of things that I (try to) do nowadays. 
 
But I use Google quite frequently now.

---

