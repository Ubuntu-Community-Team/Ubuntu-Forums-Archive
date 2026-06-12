---
title: "Gnash.  Are We Too Embarrassed To Talk About It?"
date: 2009-08-09
forum: The Cafe
---

### Post by Mark76 on 2009-08-09
It's funny how whenever I try to start a serious thread about open source's answer to Flash and its idiosyncrasies (try playing anything on the BBC's IPlayer using it) I always end up getting zero replies.

Are you all just ignoring it in the hope that it'll go away (Gnash, that is). Or just waiting for every video site to switch to using html5 tags?

---

### Post by Skripka on 2009-08-09
No, most folks just don't care about it-because most folks don't use it.  Why use something that doesn't work?

---

### Post by JDShu on 2009-08-09
lol I use Gnash

---

### Post by gnomeuser on 2009-08-09
It's a feature incomplete implementation of a proprietary platform with no access to conformance tests. Aside that Flash is poorly implemented, the difference in downloading a flv video from youtube then play it back in totem as opposed to using the flash plugin are profound. It eats CPU cycles for breakfast.

Personally I can't wait for the world to embrace Silverlight and rid ourselves of this plague, gnash or not, flash is a problem.

---

### Post by joey-elijah on 2009-08-09
I've not tried it, and probably won't purely because Flash 10 x64 works flawlessly (for a linux version, anyway!).

That said, i cannot wait for Youtube to (inevitably) start using HTML5 video tags as DailyMotion now does. once Youtube makes the switch/option then the rest of the web will follow.

---

### Post by Mark76 on 2009-08-09
> **gnomeuser said:**
> It's a feature incomplete implementation of a proprietary platform with no access to conformance tests. Aside that Flash is poorly implemented, the difference in downloading a flv video from youtube then play it back in totem as opposed to using the flash plugin are profound. It eats CPU cycles for breakfast.

Personally I can't wait for the world to embrace Silverlight and rid ourselves of this plague, gnash or not, flash is a problem.
You want the open-source world to swap one proprietory format for another? :eek:

---

### Post by swoll1980 on 2009-08-09
> **Mark76 said:**
> You want the open-source world to swap one proprietory format for another? :eek:

The Silverlight player is open source.

---

### Post by gnomeuser on 2009-08-09
> **Mark76 said:**
> You want the open-source world to swap one proprietory format for another? :eek:

No, I would love to see everyone switch to a platform for which a 100% verifiable conformance to the specification. A platform based on an open specification (the XAML dictionary is under the OSP). With Silverlight 3 (and Moonlight 2) you get the option to use additional formats so long as the implementation is managed (we already have Dirac and Vorbis support, I believe someone is working on a Theora port).

damn right, I would love to see us embrace a genuinely better alternative.

---

### Post by Mark76 on 2009-08-09
> **swoll1980 said:**
> The Silverlight player is open source.
Are you sure?

You're not getting Moonlight and Silverlight mixed up, by any chance?

---

### Post by swoll1980 on 2009-08-09
> **Mark76 said:**
> Are you sure?

You're not getting Moonlight and Silverlight mixed up, by any chance?

aren't they the same thing?

---

### Post by Mark76 on 2009-08-09
Not quite

Check the Wikipedia articles. Silverlight has a completely different licence

---

### Post by dlmarti on 2009-08-09
> **swoll1980 said:**
> The Silverlight player is open source.

In your dreams maybe, but not in the real world it isn't.

There was a rumor at one time, that Mickeysoft would opensource SOME of the code.  They have since denied they have any plans to do so.

Moonlight is getting some help from MS, through a third party, but I would hardly call this open source.

---

### Post by gnomeuser on 2009-08-09
> **dlmarti said:**
> In your dreams maybe, but not in the real world it isn't.

There was a rumor at one time, that Mickeysoft would opensource SOME of the code.  They have since denied they have any plans to do so.

Moonlight is getting some help from MS, through a third party, but I would hardly call this open source.

You are wrong on all counts, Microsoft has released code relating to Silverlight (as well as related to ASP.NET and other .NET components) as open source. They tend to prefer the Microsoft Permissive License which is similar to the X11 MIT license with a patent grant. This license is confirmed by OSI as conforming to the Open Source standards.

Moonlight is directly using the very same test suite Microsoft uses for Silverlight as part of the Novell-Microsoft interoperatibility agreement. Microsoft work directly with several members of the Mono community and are ready to resolve issues (as was seen most recently with the community promise for the ECMA standards covering .NET).

Moonlight will thus be 100% compatible with Silverlight, verifiable so. Microsoft is being very helpful in bringing this about, so much so that when you visit a Silverlight site on a Linux machine without the plugin installed, they will automatically redirect you to the Moonlight download.

---

### Post by ssam on 2009-08-09
there has been a big effort over the summer to fix up flash 9/10 support in gnash. [http://wiki.gnashdev.org/Gnash_2009_Summer_Project](http://wiki.gnashdev.org/Gnash_2009_Summer_Project)

the next release will probably be a big step forwards.

personally i am happy most of the time with no flash player installed in my browser.

---

### Post by dlmarti on 2009-08-09
> **gnomeuser said:**
> You are wrong on all counts, Microsoft has released code relating to Silverlight (as well as related to ASP.NET and other .NET components) as open source. They tend to prefer the Microsoft Permissive License which is similar to the X11 MIT license with a patent grant. This license is confirmed by OSI as conforming to the Open Source standards.

Moonlight is directly using the very same test suite Microsoft uses for Silverlight as part of the Novell-Microsoft interoperatibility agreement. Microsoft work directly with several members of the Mono community and are ready to resolve issues (as was seen most recently with the community promise for the ECMA standards covering .NET).

Moonlight will thus be 100% compatible with Silverlight, verifiable so. Microsoft is being very helpful in bringing this about, so much so that when you visit a Silverlight site on a Linux machine without the plugin installed, they will automatically redirect you to the Moonlight download.

They have released SOME of the code, the API spec, and test cases.  They have released SOME of the codec's in binary form.

While I agree that this is WAY better than the Adobe situation, until the all the code (but not the codec's) are released to the general public I would not call Silverlight open source.

I also agree that Moonlight has a much better chance of becoming 100% compatible than a free version of Flash.

I'm not trying to argue which is better, I am simply pointing out that Silverlight is NOT open source by any normal definition.  If it were the API and source would be generally available to the public.  As well as a method for reproducing the Silverlight binary.

If you disagree, I welcome you to obtain the source and compile it yourself.

---

### Post by orlox on 2009-08-09
I wonder if this support for moonlight is nothing more than the typical “embrace, extend, and extinguish” strategy from microsoft. i.e. support moonlight until silverlight becomes an industry standard, extend silverlight discretely in a way that developers start writing exclusively silverlight compatible apps without noticing it, and then, cutting support from moonlight completely.

They've done it a thousand times already, but I think that in the current times, they risk this whole thing severely blowing rright into their faces...

---

### Post by mouchero08 on 2009-08-09
when i open up my fantasy football site with Gnash i find my CPU leaks out to 100% most of the time.
this stops my enjoyment of surfing to this site on Ubuntu

---

### Post by thunk77 on 2009-08-09
When the darn thing starts working i'll use it

---

### Post by windows-killer on 2009-08-09
gnash is nothing compared to adobe flash.

---

### Post by DeadSuperHero on 2009-08-09
Honestly, I don't think Gnash is a good solution to the "Proprietary Web" problem.

Instead of coming up with a completely open framework to rival Flash and Silverlight, we merely have incomplete implementations of both. 

I really would like to see a third alternative that could be used, at least until HTML5's capabilities are fully realized and unleashed.

---

### Post by CJ Master on 2009-08-09
> **Mr. Psychopath said:**
> Honestly, I don't think Gnash is a good solution to the "Proprietary Web" problem.

Instead of coming up with a completely open framework to rival Flash and Silverlight, we merely have incomplete implementations of both. 

I really would like to see a third alternative that could be used, at least until HTML5's capabilities are fully realized and unleashed.

I was thinking that, but then I'd realize how much it'd fail. Consider that Microsoft of all things pushes an alternative, and how well is it doing? Not good. And they got WAY too much funding as well. No way a F/OSS alternative would catch on.

---

### Post by DeadSuperHero on 2009-08-09
Either way, one can dream. 
But the fact of the matter is, the best we're doing right now is treating a symptom, as opposed to curing a disease.

---

### Post by doorknob60 on 2009-08-09
Here's an open source alternative for Youtube, and yes it works, and uses a lot less CPU. Only works on Youtube, but that's what I use Flash for most of the time. [http://userscripts.org/scripts/show/38074](http://userscripts.org/scripts/show/38074) Edit some of the default options as they can be slightly annoying, but when configured right it uses the mplayer plugin (if you have it installed, should work with totem or vlc or whatever too) instead of Flash to play Youtube, as well as adding a download button and some nice extras (like automatically using the highest quality available). It works well most of the time, and when it doesn't there's a button to switch to the Flash version. You need the Greasemonkey Firefox addon: [https://addons.mozilla.org/en-US/firefox/addon/748](https://addons.mozilla.org/en-US/firefox/addon/748)

---

### Post by gnomeuser on 2009-08-09
> **Mr. Psychopath said:**
> Honestly, I don't think Gnash is a good solution to the "Proprietary Web" problem.

Instead of coming up with a completely open framework to rival Flash and Silverlight, we merely have incomplete implementations of both. 

I really would like to see a third alternative that could be used, at least until HTML5's capabilities are fully realized and unleashed.

In this wonderful new world you advocate, what choice of language do I have.. essentially JavaScript no? with all it's wonderfully odd syntax, marvelous lack of proper standardization, poor performance and fantastic security flaws by design. It seems like an awful foundation to build anything on, not at all designed to support these big critical deployments we are looking at in the future. Aside that HTML5 isn't done yet, with comments coming in all the time from major vendors trying to shape it who knows when we will see a final platform released both Silverlight and Flash are here today.

Also you are mistaken in thinking Moonlight won't ever be feature complete or will be incompatible. There are plenty of people working hard to close the gap from SL1 to SL2, the SL2 to SL3 development will be a much smaller effort. Aside that we have access to the conformance tests to ensure it will be fully compatible. 

Moonlight also isn't just about the web, it's a good choice for developing next generation desktop applications.

---

### Post by SunnyRabbiera on 2009-08-09
> **gnomeuser said:**
> It's a feature incomplete implementation of a proprietary platform with no access to conformance tests. Aside that Flash is poorly implemented, the difference in downloading a flv video from youtube then play it back in totem as opposed to using the flash plugin are profound. It eats CPU cycles for breakfast.

Personally I can't wait for the world to embrace Silverlight and rid ourselves of this plague, gnash or not, flash is a problem.

But silverlight is worse, look at moonlight its supposed to be Microsofts collab with Novell to make silverlight for linux and its way behind silverlight.
We are better off with flash

---

### Post by Mateo on 2009-08-09
It's ignored because so many open source -only advocates don't want to talk about it.  There is no open source alternative to flash that's usable and telling people not to use websites that use flash is untenable.  So the issue is simply ignored.

I disagree that Moonlight is a good alternative.  Silverlight 2.0 was released last october.... waiting 1 year to go back to a website that no longer works for you is not an acceptable work around.

---

### Post by SunnyRabbiera on 2009-08-09
> **Mateo said:**
> It's ignored because so many open source -only advocates don't want to talk about it.  There is no open source alternative to flash that's usable and telling people not to use websites that use flash is untenable.  So the issue is simply ignored.

I disagree that Moonlight is a good alternative.  Silverlight 2.0 was released last october.... waiting 1 year to go back to a website that no longer works for you is not an acceptable work around.

I know, at least with flash we get regular updates...
Moonlight is a year behind almost, even if flash isnt that great itself at lest it works for most.
Moonlight/silverlight dont cut it

---

### Post by racerraul on 2009-08-09
> **doorknob60 said:**
> Here's an open source alternative for Youtube, and yes it works, and uses a lot less CPU. Only works on Youtube, but that's what I use Flash for most of the time. [http://userscripts.org/scripts/show/38074](http://userscripts.org/scripts/show/38074) Edit some of the default options as they can be slightly annoying, but when configured right it uses the mplayer plugin (if you have it installed, should work with totem or vlc or whatever too) instead of Flash to play Youtube, as well as adding a download button and some nice extras (like automatically using the highest quality available). It works well most of the time, and when it doesn't there's a button to switch to the Flash version. You need the Greasemonkey Firefox addon: [https://addons.mozilla.org/en-US/firefox/addon/748](https://addons.mozilla.org/en-US/firefox/addon/748)

Very nice alternative... thank you for sharing.

---

### Post by BuffaloX on 2009-08-09
> **gnomeuser said:**
> You are wrong on all counts, Microsoft has released code relating to Silverlight (as well as related to ASP.NET and other .NET components) as open source. They tend to prefer the Microsoft Permissive License which is similar to the X11 MIT license **with a patent grant**. This license is confirmed by OSI as conforming to the Open Source standards.


If Microsoft have patents on Silverlight, they can pull the plug for Moonlight anytime they want.
I'd rather stay with Flash then, at least Adobe give Linux support by developing a reasonably decent player.
Also Adobe have no conflict of interest supporting Linux, which Microsoft most definitely have, and we all know how that usually turns out.

---

### Post by directhex on 2009-08-09
Anyone with positive words for Adobe here obviously didn't spend 5 years waiting for a 64-bit plugin

---

### Post by BoyOfDestiny on 2009-08-09
Abandoning flash at this point is like leaving QWERTY. Sadly. 

It would be like abandoning .doc for a better format. This is actually gaining traction thankfully, but, without Free programs that could read/write .doc these past years, how effective would a proposition like that have been? What could be done to convert the document to a usable format without an interpreter?

As for moonlight, if the past ( [http://www.groklaw.net/articlebasic.php?story=20071023002351958](http://www.groklaw.net/articlebasic.php?story=20071023002351958) ) is an indicator of future behavior, Microsoft will ensure that it is one step behind (at least) of silverlight on Windows.

P.S. I should mention I do use gnash.

---

### Post by starcannon on 2009-08-09
> **Mark76 said:**
> It's funny how whenever I try to start a serious thread about open source's answer to Flash and its idiosyncrasies (try playing anything on the BBC's IPlayer using it) I always end up getting zero replies.

Are you all just ignoring it in the hope that it'll go away (Gnash, that is). Or just waiting for every video site to switch to using html5 tags?

I prefer Adobe Flash Player myself; so I really have nothing to say about Gnash. I'm guessing that must be true for a lot of us. Same goes for Sun Java, I don't see a need to try to work the FOSS alternative. Both companies have released native linux software, I'd prefer they keep working on it, and allow manpower to be freed up for other projects. But those working on Gnash probably find it interesting, so if they are happy, I'm happy for them.

GL and HF

---

### Post by Methuselah on 2009-08-09
When I was using FreeBSD a year ago, Gnash was the absolute best option I had.
Given that youtube was my main use for flash, it worked well enough with a few idiosyncrasies.
There was a time when I used it in Ubuntu rather than the proprietary flash plugin. 
I can only imagine that it's better today than the last time I used it.

---

### Post by MikeTheC on 2009-08-10
> **Mark76 said:**
> **Gnash.  Are We Too Embarrassed To Talk About It?**
Yes, actually.

---

### Post by running_rabbit07 on 2009-08-10
> **mouchero08 said:**
> when i open up my fantasy football site with Gnash i find my CPU leaks out to 100% most of the time.
this stops my enjoyment of surfing to this site on Ubuntu

It is only because you went to a football site that it didn't work.

---

### Post by running_rabbit07 on 2009-08-10
> **Mateo said:**
> It's ignored because so many open source -only advocates don't want to talk about it.  There is no open source alternative to flash that's usable and telling people not to use websites that use flash is untenable.  So the issue is simply ignored.

I disagree that Moonlight is a good alternative.  Silverlight 2.0 was released last october.... waiting 1 year to go back to a website that no longer works for you is not an acceptable work around.

Agreed, my college uses Flash for all of it's online lectures, if I try not to use flash, I just fail. Some get to use their systems for pleasure but I find myself having to use the streamlined proprietary stuff for college. I can do the flash lectures no problem with the Adobe add-ons in Ubuntu and Fedora. I only need MS for all the programs that some with my textbooks.

I also like that the Adobe sit offers  packages for deb, rpm, and yum.

---

### Post by joebodo on 2009-08-10
Expecting MS to provide a free open standard is very naive. There are too many examples to even begin.

Here's a new patent battle with MS:

[http://arstechnica.com/microsoft/news/2009/08/microsoft-granted-patent-on-xml-word-processing-files.ars]("http://arstechnica.com/microsoft/news/2009/08/microsoft-granted-patent-on-xml-word-processing-files.ars")

---

### Post by calrogman on 2009-08-10
> **CJ Master said:**
> I was thinking that, but then I'd realize how much it'd fail. Consider that Microsoft of all things pushes an alternative, and how well is it doing? Not good. And they got WAY too much funding as well. No way a F/OSS alternative would catch on.


LINUX is obsolete  --  Andrew S. Tanenbaum, 1992

[http://groups.google.com/group/comp.os.minix/msg/f447530d082cd95d](http://groups.google.com/group/comp.os.minix/msg/f447530d082cd95d)

---

### Post by running_rabbit07 on 2009-08-10
> **joebodo said:**
> Expecting MS to provide a free open standard is very naive. There are too many examples to even begin.

Here's a new patent battle with MS:

[http://arstechnica.com/microsoft/news/2009/08/microsoft-granted-patent-on-xml-word-processing-files.ars](http://arstechnica.com/microsoft/news/2009/08/microsoft-granted-patent-on-xml-word-processing-files.ars)

I bet Bill Gates secretly has Ubuntu installed on his desk machine. (of course he had someone else set it up though.)

---

### Post by MythAaron on 2009-08-10
I am very much a Torvalds-like pragmatist (I used up all my zealotry on the Amiga).  That said, I think the Linux world should stay as far away from Microsoft as possible.  On the last Osnews podcast, the gang talked about the maturing process that is slowing going on at Microsoft.  However, the company is still run by the embrace, extend, extinguish crowd.

I think on the whole Adobe has been good to Linux.  They came late, but who hasn't?  I think Gnash deserves much credit for bring Adobe around.  Gnash had its day, though.

In the end, I hope things will come together for HTML 5.  Seriously, why can't the WHATWG specification include BOTH Theora and whatever codec Apple wants?

---

### Post by BuffaloX on 2009-08-10
> **directhex said:**
> Anyone with positive words for Adobe here obviously didn't spend 5 years waiting for a 64-bit plugin

I'm not sure if this was partly directed at me?
But I'm not saying Adobe is any better than Microsoft, I'm just saying Adobe don't have any reason to hinder the rise of Linux, Microsoft most definitely have.

---

### Post by directhex on 2009-08-10
> **BuffaloX said:**
> I'm not sure if this was partly directed at me?
But I'm not saying Adobe is any better than Microsoft, I'm just saying Adobe don't have any reason to hinder the rise of Linux, Microsoft most definitely have.

[http://www2.apebox.org/wordpress/rants/156/](http://www2.apebox.org/wordpress/rants/156/)

More seriously though, Microsoft need Moonlight.

Consider that you're an artsy web designer type. If it helps, wear a beret, a black turtleneck, and wear hipster shades. Now, you're looking to design a flashy new site for some reason or another, and you're firmly a believer that HTML's for girls. Before you say "but I wouldn't", I think the evidence (i.e. the internet) says such people are common.

Now, you look at two competing products: Microsoft Expression Studio, and Adobe Creative Suite. The Adobe product is a LOT more well known, but... well, it costs three times as much. What are the pros? What are the cons?

"Oh", you say "the Microsoft one only works with Windows and Mac. And in these crazy cross-platform days, I can't afford not to support Linux"

Bam, lost sale for Microsoft.

Moonlight allows them to sell Expression, it allows them to sell Windows Server 2008 (for hosting the sites, especially if you use Windows Media Services 2008 for video content), it allows them to sell Windows on the desktop, it allows them to sell Visual Studio for heavyweight coding... the "cost" is encouraging someone *else* to develop the *free* plugin for them, for *free*. Oh, and paying the MPEG-LA license fees for their codec pack.

Microsoft need Moonlight. Certainly for now, anyway. Perhaps by the time they start acting like bastards over it, HTML5 will be relevant enough for plugins not to matter anymore.

---

### Post by dmizer on 2009-08-10
Closed for review.

---

