---
title: "Microsoft open sources .NET, but will it make a difference?"
date: 2014-11-12
forum: The Cafe
---

### Post by Dragonbite on 2014-11-12
Microsoft open sources .NET : [http://tirania.org/blog/archive/2014/Nov-12.html]("http://tirania.org/blog/archive/2014/Nov-12.html")

> 

The code is available today from [http://github.com/Microsoft/referencesource](http://github.com/Microsoft/referencesource). Mono will be able to use as much a it wants from this project.

We have a project underway that already does this. We are replacing chunks of Mono code that was either incomplete, buggy, or not as fully featured as it should be with Microsoft's code.


I wonder, though, how big of an impact this will have on Linux users as Mono-based applications like F-spot have been replaced with Shotwell and other projects (Tomboy, Banshee, etc.) have not had the same prominence lately as a few years ago.

---

### Post by theo-friberg on 2014-11-12
Microsoft makes actual FOSS?
What else have I missed? :shock:

---

### Post by user1397 on 2014-11-13
I wonder how much this helps WINE or even ReactOS people :)

---

### Post by Lars Noodén on 2014-11-13
> **theo-friberg said:**
> 
What else have I missed? :shock:

Usually, in the past, when their outsourced PR teams make a lot of noise it is to distract from something bad happening elsewhere.  Since there is not a lot going on in the courts lately my guess would be something like this:

[http://www.pcworld.com/article/2846004/microsoft-fixes-severe-19-year-old-windows-bug-found-in-everything-since-windows-95.html](http://www.pcworld.com/article/2846004/microsoft-fixes-severe-19-year-old-windows-bug-found-in-everything-since-windows-95.html)

all that bug needs now is its own logo and web site.  There were many, many articles starting to pop up but they have all vanished from the top of their repsective publications and mostly even from Google.  It took a few minutes searching for known phrases from that article to find even that one again.  

About the allegations of promoting Free and Open Source Software.  It would be cool if it were true, the products would have a fighting chance at improving their quality to something acceptable, but it is not likely.  Going FOSS would be too much of a sea change for the company management and against the entire multi-decade history of the company.  Gates, via Nadella, does not have in place yet the 'services' business model which could build upon FOSS.  It is more likely that they are promoting either an open-core model or freemium, neither are OSS let alone FOSS.  Unfortunately, to find that out, it will take more than glancing at the misguided headlines that most repeat articles are based on.  

The devil is in which license is used and to what it is applied.

Their own official press release is hard to parse but it looks like they are talking only about changes to various versions of VisualStudio, which is neither FOSS nor runs on Ubuntu.  My other guess is that you have to have Windows to even download the terms and conditions.  Between that and not being a lawyer, it will be hard to impossible to look into.

---

### Post by ukripper on 2014-11-13
> **Lars Noodén said:**
> Usually, in the past, when their outsourced PR teams make a lot of noise it is to distract from something bad happening elsewhere.  Since there is not a lot going on in the courts lately my guess would be something like this:

[http://www.pcworld.com/article/2846004/microsoft-fixes-severe-19-year-old-windows-bug-found-in-everything-since-windows-95.html](http://www.pcworld.com/article/2846004/microsoft-fixes-severe-19-year-old-windows-bug-found-in-everything-since-windows-95.html)

all that bug needs now is its own logo and web site.  There were many, many articles starting to pop up but they have all vanished from the top of their repsective publications and mostly even from Google.  It took a few minutes searching for known phrases from that article to find even that one again.  

About the allegations of promoting Free and Open Source Software.  It would be cool if it were true, the products would have a fighting chance at improving their quality to something acceptable, but it is not likely.  Going FOSS would be too much of a sea change for the company management and against the entire multi-decade history of the company.  Gates, via Nadella, does not have in place yet the 'services' business model which could build upon FOSS.  It is more likely that they are promoting either an open-core model or freemium, neither are OSS let alone FOSS.  Unfortunately, to find that out, it will take more than glancing at the misguided headlines that most repeat articles are based on.  

The devil is in which license is used and to what it is applied.

Their own official press release is hard to parse but it looks like they are talking only about changes to various versions of VisualStudio, which is neither FOSS nor runs on Ubuntu.  My other guess is that you have to have Windows to even download the terms and conditions.  Between that and not being a lawyer, it will be hard to impossible to look into.

But on the plus side source code for .net surely ensure there will be forks which could be truly FOSS..

---

### Post by mips on 2014-11-13
> **lars noodén said:**
> 
the devil is in which license is used and to what it is applied.

MIT [http://blogs.msdn.com/b/dotnet/archive/2014/11/12/announcing-net-2015-preview-a-new-era-for-net.aspx](http://blogs.msdn.com/b/dotnet/archive/2014/11/12/announcing-net-2015-preview-a-new-era-for-net.aspx)

---

### Post by Lars Noodén on 2014-11-13
> **mips said:**
> MIT [http://blogs.msdn.com/b/dotnet/archive/2014/11/12/announcing-net-2015-preview-a-new-era-for-net.aspx](http://blogs.msdn.com/b/dotnet/archive/2014/11/12/announcing-net-2015-preview-a-new-era-for-net.aspx)

Ok.  An MIT license is legit.  But otherwise it looks like it might be the 'open-core' dodge mentioned earlier, depending on what all the components left out actually do.  I guess we'll have to wait for an analysis of what if anything  their Core .5 does on its own.

---

### Post by Dragonbite on 2014-11-13
Microsoft is a strange beast... when Management was saying that "Linux is the devil" (cancer, whatever) there were numerous blogs and mention where the engineers and technical people were much more open and collaborative with FOSS and Linux.

At the same time, the (technical) world in which Gates raised the company is way, waaaaay different than the technical world today!  That's also a good reason why top level management had to change.  

I know Xamarin has been working with Microsoft a lot lately and there were rumors about Microsoft purchasing Xamarin but they didn't.  This seems to be very counter to "embrace, extend, extinguish" methodology.

For Microsoft, this may bring more non-Windows computers to using .NET when Windows is slowly loosing ground.  It also allows Microsoft to push .NET as a (real) cross-platform language for even iOS and Android!  For FOSS it means greater support and less work trying to get it 100% compatible (in time, I know..).

And > This patent promise addresses the historical concerns that the open source, Unix and free software communities have raised over the years. doesn't hurt either ;)

I may not trust them 100% (but hey, I don't trust Canonical 100% either ;) ) but am hopeful and optimistic about this.

---

### Post by vasa1 on 2014-11-13
> **Dragonbite said:**
> Microsoft is a strange beast... when Management was saying that "Linux is the devil" (cancer, whatever) ...
Yikes, I got an infraction a couple of years ago for quoting that.

---

### Post by vasa1 on 2014-11-13
> **Dragonbite said:**
> ...
I wonder, though, how big of an impact this will have on Linux users as Mono-based applications like ...Doesn't Docky also have something mono about it?

---

### Post by Dragonbite on 2014-11-13
> **vasa1 said:**
> Doesn't Docky also have something mono about it?

I'm also not sure about Pinta, which is a Paint.NET "inspired" graphics program.

---

### Post by uRock on 2014-11-13
This mean I might be able to get Swannview to work in Linux, which is good.

---

### Post by irv on 2014-11-13
[Microsoft takes .NET open source and makes it available for Linux and Mac]("http://www.theinquirer.net/inquirer/news/2381172/microsoft-takes-net-open-source-and-makes-it-available-for-linux-and-mac#")
I found this article interesting. it was in the Inquirer.
I ran across this today.

---

### Post by overdrank on 2014-11-13
Threads merged :)

---

### Post by QIII on 2014-11-13
Beware of Greeks bearing gifts?

---

### Post by pqwoerituytrueiwoq on 2014-11-13
> **QIII said:**
> Beware of Greeks bearing gifts?yea lets not use this till we have been over every single line of code

---

### Post by irv on 2014-11-14
We know that most software is built collaboratively. Does this really mean MS is finely seeing this? I always feel they have something up their sleeve.

---

### Post by Dragonbite on 2014-11-14
> **irv said:**
> We know that most software is built collaboratively. Does this really mean MS is finely seeing this? I always feel they have something up their sleeve.

I understand that, but I think times have changed significantly and am (hopeful? optimistic?) that this may be different (but taking it with a grain of salt).

I outlined it before the threads got merged at (instead of repeating myself) [http://ubuntuforums.org/showthread.php?t=2252504&p=13166435#post13166435]("http://ubuntuforums.org/showthread.php?t=2252504&p=13166435#post13166435").

---

### Post by Lars Noodén on 2014-11-15
> **Dragonbite said:**
>  (but taking it with a grain of salt)

That's probably wisest, very old parables about farmers and vipers notwithstanding.  Now that people are starting to look into the details, it looks like the patent license could use more than a little work to make it safe as far as paperwork goes (holding quiet about the technical stuff):

[http://www.plingzine.com/?p=686](http://www.plingzine.com/?p=686)

Of interest is that how patents are dealt with is one of the differences between the Apache and MIT licenses.  
[list]
[*] [http://opensource.org/licenses/Apache-2.0](http://opensource.org/licenses/Apache-2.0)
[*] [http://opensource.org/licenses/MIT](http://opensource.org/licenses/MIT)
[/list]

---

### Post by rrnbtter on 2014-11-15
Greetings,
This looks to me like
"hiding a bad motive under a good one".
Someone over at Microsoft has been robbing the wine cabinet. Burp! ....net
Gee! Just when I thought it was safe to go back in the water.

---

### Post by The Cog on 2014-11-15
Microsoft decided a long time ago that its battle for world domination would be fought with patents. They published the specs for FAT, remember. Then years later they began suing everyone who used it. Open sourcing .net is just inviting people to paint a target on their backs.

---

### Post by irv on 2014-11-15
> **Dragonbite said:**
> I understand that, but I think times have changed significantly and am (hopeful? optimistic?) that this may be different (but taking it with a grain of salt).

I outlined it before the threads got merged at (instead of repeating myself) [http://ubuntuforums.org/showthread.php?t=2252504&p=13166435#post13166435]("http://ubuntuforums.org/showthread.php?t=2252504&p=13166435#post13166435").

Thanks Dragonbit for posting the link. Just so happens I read your post. (I went back when my thread got merged). I agree with what you had to say about top level management having to change. Open Source has set the bar high and if MS doesn't  jump on the open source wagon they are going to get left behind. The quality of open source software has come of age and I believe that you can find some real nice software in the open source market.

---

### Post by CantankRus on 2014-11-17
Yeah right... put part of .net under a mit licence and headline MS goes "open source".
PR fluff as MS tries to gain some sort of control and relevance in the new OS markets and cloud.
I prefer to believe Roy....
[**_[COLOR="#B22222"]lies-about-microsoft-dotnet[/COLOR]_**]("http://techrights.org/2014/11/15/lies-about-microsoft-dotnet/")

---

### Post by Dragonbite on 2014-11-17
> **CantankRus said:**
> Yeah right... put part of .net under a mit licence and headline MS goes "open source".
PR fluff as MS tries to gain some sort of control and relevance in the new OS markets and cloud.
I prefer to believe Roy....
[**_[COLOR="#B22222"]lies-about-microsoft-dotnet[/COLOR]_**]("http://techrights.org/2014/11/15/lies-about-microsoft-dotnet/")

I take his site with a grain of salt.  Isn't he the one that also started BoycottNovell.com?

Just as Paul Thurrott is pro-MS, Dr. Roy is equally anti-MS. So neither of them gives a neutral view.

I'm looking at it as somebody who uses ASP.NET at work (alongside PHP and Drupal on FreeBSD) and Linux (Ubuntu, openSUSE, Fedora and more) at home.  To me, having greater .NET support on Linux is a good thing even though I don't use it much on my home systems currently.

But I am taking this news with a grain of salt, and curious to see how it pans out.  

This could end up being something that benefits Enterprises invested in .NET applications who are looking for running on a non-Microsoft platform (or cloud) or for an application developer company wanting to utilize the same code across multiple platforms and HTML5 & JS isn't there for them yet.  Heck, if it works out enough we may be able to move our current .NET application off of a Windows Server to something more stable, safe and manageable!

---

### Post by CantankRus on 2014-11-17
> **Dragonbite said:**
>  Dr. Roy is equally anti-MS.


With good reason and documented proof.

---

### Post by Dragonbite on 2014-11-17
> **irv said:**
> Thanks Dragonbit for posting the link. Just so happens I read your post. (I went back when my thread got merged). I agree with what you had to say about top level management having to change. Open Source has set the bar high and if MS doesn't  jump on the open source wagon they are going to get left behind. The quality of open source software has come of age and I believe that you can find some real nice software in the open source market.

Also, MS is changing their focus to "web" and "mobile".  The web has been a strong suit of Linux so it seems natural they will need to change their tactics in that arena and Google and Apple are big enough to call most of the shots in the mobile market.

> **CantankRus said:**
> With good reason and documented proof.

I would hardly call his writing as "proof".  In Journalism, Law and Advertising anything can be "spun" to support one's opinion.

Some of the quotes have good points (such as Simon Phipps and Carlo Piana and maddog) but a lot of the post are links to what other people say.

"*but will it make a difference?*"

---

### Post by Linuxratty on 2014-11-17
> **The Cog said:**
> Microsoft decided a long time ago that its battle for world domination would be fought with patents. They published the specs for FAT, remember. Then years later they began suing everyone who used it. Open sourcing .net is just inviting people to paint a target on their backs.

 So is FAT what they used to milk Linspire, Android,Red Hat,etc? or is this just the tip of the ice berg?
Also,do you think people who use .net will be sued? What would be the ramifications of this?

---

### Post by Dragonbite on 2014-11-18
> **Linuxratty said:**
> So is FAT what they used to milk Linspire, Android,Red Hat,etc? or is this just the tip of the ice berg?
Also,do you think people who use .net will be sued? What would be the ramifications of this?

That's tricky, because how is open sourcing the .NET libraries going to change what you can and cannot do with .NET now?  Even on Windows?

I think they are releasing it because without Mono they are finding that .NET is severely limited in this web & mobile world.  Yes, there is ASP.NET for web but the web runs mostly on Linux, and the Windows Phone is the only one to run anything like .NET and it's market share is dismal. 

When you add in Xamarin and Mono. Now you have .NET that works on Linux servers and Xamarin makes .NET work on Android and iOS!

So instead of letting .NET continue to become irrelevant where they have no control (and no revenue from Visual Studio and MSDN subscriptions) by open sourcing it they can try to capture these platforms that was primarily the property of Java.

Understandably for the Open Source and Linux crowd this is probably not going to make that much of a difference, other than the few Mono-based applications becoming more compatible.  For enterprises that already have investment in .NET but are looking at switching to Linux-based servers or cloud solutions it keeps them "in the fold" by allowing them to possibly use their existing program on Linux/Cloud rather than them leaving wholesale.

Plus, if they can get developers to use .NET for programming their mobile apps, then porting popular apps to the Windows Phone because that much easier which increases the number of apps for Microsoft's phones & tablets which is one of their biggest counter-arguments.

---

### Post by vasa1 on 2014-11-18
> **Dragonbite said:**
> I take his site with a grain of salt. ...
I'm happy that the Techrights site exists though it doesn't make up for Groklaw going away.

---

### Post by /ADM on 2014-11-21
> **The Cog said:**
> Microsoft decided a long time ago that its battle for world domination would be fought with patents. They published the specs for FAT, remember. Then years later they began suing everyone who used it. Open sourcing .net is just inviting people to paint a target on their backs.

That would be like the FSF suing everyone who used Emacs (if they wanted to).  Open Sourcing via the MIT is basically saying "Hey take the source and do what the <snip> you want, just don't remove this license header".  Patents or not.

Don't forget, patents don't apply to software in the EU and largely most of Asia (except Japan and South-Korea).  So it wouldn't stand in these territories anyway.

---

### Post by Dragonbite on 2014-11-21
Isn't the MIT license what some open source software applications use if they are going into the enterprise market?  I thought MySQL had the open license for users, and a version with the MIT license for anybody wishing to use it in a non-open source program?

I think FreeBSD is under the MIT license as well. Then there is the Apache license too... (too many licenses to keep track of).

---

### Post by Lars Noodén on 2014-11-21
> **Dragonbite said:**
> Isn't the MIT license what some open source software applications use if they are going into the enterprise market?  I thought MySQL had the open license for users, and a version with the MIT license for anybody wishing to use it in a non-open source program?

I think FreeBSD is under the MIT license as well. Then there is the Apache license too... (too many licenses to keep track of).

MySQL used to be dual licensed.  It was under the GPL but for those that wanted to make a closed source product there was the option of buying a closed source license.  It was a good money maker.  Those that *redistributed* MySQL contributed either code or money.

FreeBSD is under one of the [BSD license](http://www.freebsd.org/copyright/freebsd-license.html)s which is a bit different than the MIT license.  Neither cover patents.  

There are not that many OSS licenses, 

[http://opensource.org/licenses](http://opensource.org/licenses)

especially compared to the number of closed source licenses.  I knew someone that once forced their MS-oriented IT department to print out the relevant licenses for their workstation basic set up to see what the licences really were.  The resulting paper stack was about an inch thick, if I recall correctly.  Every version of every package had a separate long license.

---

### Post by /ADM on 2014-11-21
> **Lars Noodén said:**
> MySQL used to be dual licensed.  It was under the GPL but for those that wanted to make a closed source product there was the option of buying a closed source license.  It was a good money maker.  Those that *redistributed* MySQL contributed either code or money.

FreeBSD is under one of the [BSD license](http://www.freebsd.org/copyright/freebsd-license.html)s which is a bit different than the MIT license.  Neither cover patents.  

There are not that many OSS licenses, 

[http://opensource.org/licenses](http://opensource.org/licenses)

especially compared to the number of closed source licenses.  I knew someone that once forced their MS-oriented IT department to print out the relevant licenses for their workstation basic set up to see what the licences really were.  The resulting paper stack was about an inch thick, if I recall correctly.  Every version of every package had a separate long license.

FreeBSD is (obviously) under the 2-Clause BSD License ([https://en.wikipedia.org/wiki/BSD_licenses#2-clause](https://en.wikipedia.org/wiki/BSD_licenses#2-clause)).

Neither cover patents because the laws differ depending on countries.

UPDATE:  Seems MS will be clarifying patents:
[http://www.net-security.org/secworld.php?id=17633](http://www.net-security.org/secworld.php?id=17633)
"We are releasing the source under the MIT open source license and are also issuing an explicit patent promise to clarify users patent rights to .NET."

Doesn't appear so evil as some are saying.

---

### Post by Dragonbite on 2014-11-21
> **Lars Noodén said:**
> FreeBSD is under one of the [BSD license](http://www.freebsd.org/copyright/freebsd-license.html)s which is a bit different than the MIT license.  

doh! :redface:  I should have known that....

> **Lars Noodén said:**
> I knew someone that once forced their MS-oriented IT department to print out the relevant licenses for their workstation basic set up to see what the licences really were.  The resulting paper stack was about an inch thick, if I recall correctly.  Every version of every package had a separate long license.

Our company has somebody hired to just for looking over the licenses and making sure everything is covered.  No surprise, when able to inject open source, we try to (web server running FreeBSD, PHP, PostgreSQL and Drupal)

---

