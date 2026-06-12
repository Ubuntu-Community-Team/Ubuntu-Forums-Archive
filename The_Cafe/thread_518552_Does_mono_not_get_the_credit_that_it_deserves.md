---
title: "Does mono not get the credit that it deserves?"
date: 2007-08-06
forum: The Cafe
---

### Post by triptoe on 2007-08-06
> ure, the Mono Project isn’t anything you would actually consider to be a “Linux version” of the .NET Framework thanks to the rather-conspicuous yet well-hidden fact that it doesn’t have a compatible UI Library (well, not yet anyway) and that, in reality, it’s a port of the CLR and C#, not of the .NET Framework itself; but nevertheless, Mono is pretty amazing.

> Silverlight (and now, Moonlight as well) uses XAML to create the UI and make all those pretty little ponies dance around that computer screen. Silverlight and Moonlight’s jobs are to take that XAML code and render it on the screen. Unlike the .NET Framework on Windows where you use certain APIs to design the form, in Silverlight/Moonlight, everything is WPF and now, fully portable to Linux.

Well, to be fair, Moonlight isn’t ready yet. It’s really close, but not yet there. But what matters is, it does have a working C++ XAML parser, and the main UI interface/library will be truly cross-platform compatible with Windows. 

It occurred to me that what if .Net is actually useful.. if it is useful and is in some cases the best tool for the job.. is it not unwise to simply not use it because of some uncertainty? It seems to me there has been a lot of fud spread about the Mono and whether it is like a microsoft trojan horse. But in reality.. isn't the kernel itself.. isn't any piece of open source software vulnerable to patents somewhere? If you trust that the kernel itself is safe then I think mono can be trusted as well... since after all the CLR is an open standard... an open specification.

Here is a good article though that got me to thinking about it and silverlight. The reason why I am interested in silverlight is because it could be an improvement over flash for 3 reasons... One is that with moonlight, we could get an open source implementation server side and client side. Another is that some benchmarks show silverlight with the CLR is superior to flash and javafx.. the only other alternatives. And lastly, you can pretty much choose the programming language of your choice... And python is one of the languages that is supported.

Here is the article that got me thinking: [http://neosmart.net/blog/2007/mono-doesnt-get-enough-credit/](http://neosmart.net/blog/2007/mono-doesnt-get-enough-credit/)

---

### Post by izanbardprince on 2007-08-06
> **triptoe said:**
> It occurred to me that what if .Net is actually useful.. if it is useful and is in some cases the best tool for the job.. is it not unwise to simply not use it because of some uncertainty? It seems to me there has been a lot of fud spread about the Mono and whether it is like a microsoft trojan horse. But in reality.. isn't the kernel itself.. isn't any piece of open source software vulnerable to patents somewhere? If you trust that the kernel itself is safe then I think mono can be trusted as well... since after all the CLR is an open standard... an open specification.

Here is a good article though that got me to thinking about it and silverlight. The reason why I am interested in silverlight is because it could be an improvement over flash for 3 reasons... One is that with moonlight, we could get an open source implementation server side and client side. Another is that some benchmarks show silverlight with the CLR is superior to flash and javafx.. the only other alternatives. And lastly, you can pretty much choose the programming language of your choice... And python is one of the languages that is supported.

Here is the article that got me thinking: [http://neosmart.net/blog/2007/mono-doesnt-get-enough-credit/](http://neosmart.net/blog/2007/mono-doesnt-get-enough-credit/)


I had mono once, it kept me in bed for 3 weeks. :popcorn:


Seriously though, mono and silverlight are simply ways to try and make Java and Flash ripoffs that are Windows-only, it's not the first time Microsoft has tried it, in Windows 98 you might remember the ""Microsoft Java VM" and "DirectAnimation", the Microsoft VM was based on Sun's Java VM, but Microsoft had altered it to essentially be something completely diffferent that only ran on Windows, and DirectAnimation was supposed to have an Internet Explorer COM module to render simple animated content, kind of like earlier versions of flash, neither caught on.


Now with ActionScript in Flash, you can use it to play videos with, this is good and bad, good because it gives us Youtube and Xtube and all that wonderful stuff, but bad because now you can stumble onto advertisements that are bigger than the page you're loading, crank the volume up, and start talking or making noise, thats probably why Microsoft wants back in, cause with silverlight, it could be them selling the toolkit to these advertisers, and MONO/.NET is basically retributory spite against Sun for beating them in court..

---

### Post by Spr0k3t on 2007-08-06
.NET and Silverlight will never be developed on my Linux desktop.  These APIs are nothing more than MS Intellectual Properties and therefore I refuse to support it.  Most companies I've done software development for have had a strict regime of "Do not use MS APIs" of which I was thankful for.  Their reasons, I don't know and couldn't care less.  I sincerely doubt I would even consider installing Moonlight or Mono on my system.

---

### Post by laxmanb on 2007-08-06
I personally won't develop for Mono on any *nix. In the end .NET is best with Windows... The only company using Mono that I know of is Wikipedia to power search, as (working) Java was proprietary when they were developing...

And about Moonlight, they might get some XAML to run, but the codecs for video will remain proprietary... and one of the most important reasons for havinf Silverlight will be to view streaming video - How will you be able to do that on *nix

---

### Post by DoctorMO on 2007-08-06
It's a dangerous technoledgy; I'm a programmer and I won't be fooled into creating anything in .Net/Mono; I don't care how good it is, the risks are far far too high and the number of partners controling the direction of the languages and frameworks too low.

In essence the mono gang don't know what they've gotten themselves in for, a number of projects will need to be ported back from .Net/C# to GCC and C/C++

One of the strongest elements of the entire GNU operating system has always been the GCC compilers. I have this gut feeling that mono devs don't like Richard Stallman too much and just don't like using his gnu tools.

---

### Post by chakkaradeep on 2007-08-06
> **DoctorMO said:**
> 
One of the strongest elements of the entire GNU operating system has always been the GCC compilers. I have this gut feeling that mono devs don't like Richard Stallman too much and just don't like using his gnu tools.

err...GCC is a C/C++ compiler and Mono is entirely different :(

---

### Post by tageiru on 2007-08-06
> **DoctorMO said:**
> One of the strongest elements of the entire GNU operating system has always been the GCC compilers. I have this gut feeling that mono devs don't like Richard Stallman too much and just don't like using his gnu tools.

...and what compiler is used to build mono?

Projects like mono ensures that Linux will remain relevant as a modern operating system and make Linux development more palatable for Windows programmers.

---

### Post by DoctorMO on 2007-08-06
> Projects like mono ensures that Linux will remain relevant as a modern operating system and make Linux development more palatable for Windows programmers.

I don't believe FOSS needs .Net or Mono to stay relevant, nor do I believe in pandering to windows programmers (I know I used to be one for 5 years) 

It's weird to way people can sometimes just rabbit the same garbage coming out of Redmond. yet they still do it *sigh* I notice you didn't comment on my opinion that .Net is a dangerous framework to program in; I'll assume you agree.

Besides have you seen Ruby on rails? pretty much shows foss as being relevant to it's own needs right there. If we (as programmers) need something, it will be created and supported.

---

### Post by Incense on 2007-08-06
> **DoctorMO said:**
> Besides have you seen Ruby on rails? pretty much shows foss as being relevant to it's own needs right there. If we (as programmers) need something, it will be created and supported.

That last line is so true, and embodies the spirit of open source. Cheers! 
:guitar:

---

### Post by Dragonbite on 2007-08-06
I don't feel FOSS *needs* Mono, but it is a good project though.

I think there have been a number of Windows-users who develop in .NET and decided to give Linux a chance or are using Mono because it's familiar with what they do at work, raising Mono's popularity.

(I feel sorry for them when they go to try and use Monodevelop though).

Businesses who have spent time/money/effort in a .NET application isn't going to be too keen to throw it out and start from scratch with something like Java in order to migrate off of Windows. If Mono can handle it (with some tweaking but not rebuilding all over again) then there is one more barrier removed.

I don't know about Silverlight/Moonlight at this point (know nothing about it at all) but Mono is a great project and has come a long way in just a few years.

---

### Post by tageiru on 2007-08-06
> **DoctorMO said:**
> I don't believe FOSS needs .Net or Mono to stay relevant, nor do I believe in pandering to windows programmers (I know I used to be one for 5 years)

I think that is somewhat naive. Linux is a marginal platform at best. Lowering the barriers of entry for developers is important now that Ubuntu is starting to make inroads into mainstream computing.

> **DoctorMO said:**
> It's weird to way people can sometimes just rabbit the same garbage coming out of Redmond. yet they still do it *sigh* I notice you didn't comment on my opinion that .Net is a dangerous framework to program in; I'll assume you agree.

No I don't, actually. I have seen no credible evidence that Mono is a dangerous platform. As most non-trivial software are covered by patents there is no reason to single out .NET just because it is a Microsoft technology, which seems to be the only reason people are against it...

---

### Post by triptoe on 2007-08-06
> **Spr0k3t said:**
> .NET and Silverlight will never be developed on my Linux desktop.  These APIs are nothing more than MS Intellectual Properties and therefore I refuse to support it.  Most companies I've done software development for have had a strict regime of "Do not use MS APIs" of which I was thankful for.  Their reasons, I don't know and couldn't care less.  I sincerely doubt I would even consider installing Moonlight or Mono on my system.

Here is a quote from the article: > Unlike the .NET Framework on Windows where you use certain APIs to design the form, in Silverlight/Moonlight, everything is WPF and now, fully portable to Linux.

To me the attractiveness of mono and especially moonlight is not just attracting Windows developers but it seems like a great tool for linux in and of itself. If it is indeed a good tool, and if it is indeed safe despite what may be FUD spread against it.. then it would be hurting linux to just abandon it out of fear when it could have the potential to improve things.

For example check out these benchmarks: [http://blogs.zdnet.com/Stewart/?p=459](http://blogs.zdnet.com/Stewart/?p=459)

Firefox with silverlight + CLR not only bettered flash.. but it obliterated javafx (even though javafx is still in it's infancy) 

What if silverlight + CLR are completely portable with moonlight... what if they are in fact great tools at our disposal... and don't forget that adobe is no great friend of linux. Sure they gave us a flash player finally but mine is buggy as hell... and they still haven't ported any of their other apps or showed any interest. The only other alternative seems to be javafx but how often has relying on sun disappointed us?

Here is also another article detailing how silverlight may indeed be better than flash.. and will possibly  displace it in the future: [http://weblogs.asp.net/jezell/archive/2007/05/03/silverlight-vs-flash-the-developer-story.aspx](http://weblogs.asp.net/jezell/archive/2007/05/03/silverlight-vs-flash-the-developer-story.aspx)

Just think of this... you can use python with moonlight eventually to create Rich Internet aplications that have the potential to outperform flash... not just in the benchmarks but to be much more fundamentally superior in it's design

---

### Post by triptoe on 2007-08-09
[http://www.osnews.com/comment.php?news_id=18430](http://www.osnews.com/comment.php?news_id=18430)

It seems from a patent standpoint... mono is safe. I think the advantage microsoft has with .NET... is not some lockin.. it is in their best interest to be cross platform... but in their "bet" that their development tools will be the best. I simply think that is the advantage it gives them. The OSS community could make some tools to compete but would they be as good as proprietary ? Doubtfully...

But I am betting on silverlight... I think it looks cool and fun and is a chance for microsoft and linux to mutually benefit by a superior platform for building RIA's

---

