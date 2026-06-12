---
title: "Why does it take so long to get updated .debs for WINE?"
date: 2006-11-25
forum: The Cafe
---

### Post by AndrewG on 2006-11-25
I reckon WINE is a great project, and get extremely excited when a new version is released. Yesterday morning I woke up to find out that 0.9.26 just came out. I find it really annoying that it takes 2-3 days for a .deb to be released for each new version. Is there any reason for this? Does anyone maintain an unofficial mirror that could be used instead of wine.budgetdedicated.com that gets updated sooner?


Thanks,

AG

---

### Post by qamelian on 2006-11-25
> **AndrewG said:**
> I reckon WINE is a great project, and get extremely excited when a new version is released. Yesterday morning I woke up to find out that 0.9.26 just came out. I find it really annoying that it takes 2-3 days for a .deb to be released for each new version. Is there any reason for this? Does anyone maintain an unofficial mirror that could be used instead of wine.budgetdedicated.com that gets updated sooner?


Thanks,

AG
Highly unlikely, since I believe that is the official Wine repository for Ubuntu/Debian. Pretty hard to get it any faster than the original provider unless you want to download the source and build it yourself.

---

### Post by meng on 2006-11-25
Sure, accuse me of being in the "near-enough-is-good-enough" crowd, but 2-3 days lag for .deb behind source is really not much of a lag now is it?

---

### Post by InsomniacUK on 2006-11-25
> **AndrewG said:**
> I reckon WINE is a great project, and get extremely excited when a new version is released. Yesterday morning I woke up to find out that 0.9.26 just came out. I find it really annoying that it takes 2-3 days for a .deb to be released for each new version. Is there any reason for this? Does anyone maintain an unofficial mirror that could be used instead of wine.budgetdedicated.com that gets updated sooner?


Thanks,

AG

Well, someone has to take the time to compile it and package it, so maybe they have other things on?

You can always download the source and compile it yourself. Otherwise, you'll just have to wait until someone else does.

---

### Post by givré on 2006-11-25
winehq provide deb package but it's courtesy to them, They don't have to do it, so your reaction is quite disrespectful.
Just wait a bit, usually it doesn't take more than one week.

---

### Post by AndrewG on 2006-11-25
Would an automatic deb building thing work?

I was thinking that someone else would make the unofficial debs themselves from source...

---

### Post by gschoper on 2006-11-25
> **AndrewG said:**
> I reckon WINE is a great project, and get extremely excited when a new version is released. Yesterday morning I woke up to find out that 0.9.26 just came out. I find it really annoying that it takes 2-3 days for a .deb to be released for each new version. Is there any reason for this? Does anyone maintain an unofficial mirror that could be used instead of wine.budgetdedicated.com that gets updated sooner?


Thanks,

AG

Waiting 2-3 days for a new package to be released is nothing considering the amount of work that people put into developing software for you for free. If you require it faster than that I would suggest you download the sources and build your own packages.

My $0.02

gschoper

---

### Post by givré on 2006-11-25
> **AndrewG said:**
> Would an automatic deb building thing work?

And having it to fail one time on two ?
wine is not a small project. Packaging it can be painful.
Can't you really wait few days ?

---

### Post by loell on 2006-11-25
pls remember that debian packaging is a voluntary work, we should be thankful to the packager for voluteering on such a painful task.

---

### Post by AndrewG on 2006-11-25
I can wait, but it's just a bit surprising that it takes so long, that's all.

---

### Post by qamelian on 2006-11-25
> **AndrewG said:**
> I can wait, but it's just a bit surprising that it takes so long, that's all.
I don't think it really that long. They are being courteous by building these packages at all and they are building them for a number of different distros, not just Ubuntu and Debian. If they didn't do this, in most cases you options would be to build it yourself, hope that someone else would do an unofficial build, or wait several months for the next release of your distro of choice and hope that they include a more recent version (which doesn't always happen).

All things considered, I think a 2 or 3 day wait for complementary official packages, that the Wine team are not under any obligation to provide, is almost a ridiculously short time!

---

### Post by gschoper on 2006-11-26
> **AndrewG said:**
> I can wait, but it's just a bit surprising that it takes so long, that's all.

Why is a few days too long? As I stated above, why aren't you downloading the source and building the packages for all us. If your not willing to do it, what gives you the right to complain about how long it takes.

The packages that are built and put in the repositories are built by people just like you and me in their free time. If your not willing to do it yourself, then stop complaining about it!

Again, my $0.02,

gschoper

---

### Post by argie on 2006-11-26
Dude, I don't see why anyone would want a new version unless it gives them some particular feature that they want. As for me, for months I had my wine version pinned because I didn't need the update.

Besides, it's just 2-3 *days*. That is hardly slow. I can't see why it should be any faster.

---

### Post by AndrewG on 2006-11-26
If I was told how to make the deb packages, I would do it. If someone tells me how, I'll also provide the mirrors.

The only thing that could be a problem is that my computer isn't quite the vanilla installation.

---

### Post by shining on 2006-11-26
> **AndrewG said:**
> If I was told how to make the deb packages, I would do it. If someone tells me how, I'll also provide the mirrors.

The only thing that could be a problem is that my computer isn't quite the vanilla installation.

You should read [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/) , and then maybe propose your help to wine?
The problem you're talking about (non vanilla install) is mentioned in the guide, and solved with pbuilder:
[http://www.debian.org/doc/maint-guide/ch-checkit.fr.html#s-pbuilder](http://www.debian.org/doc/maint-guide/ch-checkit.fr.html#s-pbuilder)

---

### Post by maagimies on 2006-11-26
> **argie said:**
> Dude, I don't see why anyone would want a new version unless it gives them some particular feature that they want. As for me, for months I had my wine version pinned because I didn't need the update.What's new in this release:
>   - Better support for Unix locale settings.
  - Improved X11 keyboard support.
  - Various MSI fixes.
  - Winecfg improvements.
  **- Lots of bug fixes.**Yeah, WHY ON EARTH would anyone want bugfixes? I like my segfaults.

**And to the OP:**
Few days isn't that big time, make a deb on your own if you can't wait, don't complain for something people do voluntarily.

---

### Post by shining on 2006-11-26
> **maagimies said:**
> What's new in this release:
Yeah, WHY ON EARTH would anyone want bugfixes? I like my segfaults.

The regressions are not listed there for obvious reasons (regressions are not known yet)..
Wine is a very complex project, so version+1 is not necessarily better than version. Wine is very active though, and it's true that it has greatly improved overall.

But it's right the first thing to do when you have a problem, before asking support or reporting bugs, is to check you have the latest release. So it's very nice that wine provides deb packages itself. If the delay is only of a few days, it's great.

Otherwise, if you're not having too many problems, and the windows application you badly need is usable, there is no need to upgrade.

---

### Post by maagimies on 2006-11-26
> **shining said:**
> The regressions are not listed there for obvious reasons (regressions are not known yet)..
Wine is a very complex project, so version+1 is not necessarily better than version. Wine is very active though, and it's true that it has greatly improved overall.

But it's right the first thing to do when you have a problem, before asking support or reporting bugs, is to check you have the latest release. So it's very nice that wine provides deb packages itself. If the delay is only of a few days, it's great.I do understand that, I just have had more success with later Wine versions, and it is still beta software, and thus I like to have recent versions, I'm assuming they are more mature as a project.
> Otherwise, if you're not having too many problems, and the windows application you badly need is usable, there is no need to upgrade.I agree.

---

### Post by BoyOfDestiny on 2006-11-26
Well to compile it, download the tar.bz, extract it.
Go to that directory in a terminal.

type 

*./configure*

Watch for any messages about any file missing (go to synaptic, get package build-essential, and some other dev packages...)

try again, type 

*./configure*

Repeat until it looks good (no error messages, don't worry too much, this is pretty much a one time thing, once you have the -dev [development libraries] you'll be set)

then type

*make && make depend*

If you want the "easy way" to make a deb, but not really good for distributing (doesn't contain dependencies) but makes installing/removing a breeze...

*sudo apt-get install checkinstall*

then type

*checkinstall -D*

when done you'll have a .deb. Install it via gdebi or sudo dpkg -i nameofdeb.

Good luck.

Anyway, if all goes well, next version it should be as simple as
[I]./configure
make depend && make
checkinstall -D[/I]

painless :)

or if you'd rather not use checkinstall, and just install
type this instead of checkinstall -D
*sudo make install*

---

### Post by argie on 2006-11-26
> **maagimies said:**
> What's new in this release:
Yeah, WHY ON EARTH would anyone want bugfixes? I like my segfaults.
...
Heheh, that sounds all very nice but see, if wine works fine for you in its current version, then you aren't experiencing the bug that it fixes, and so you won't need to upgrade.

Also, as shining pointed out, there are regressions sometimes. I remember around Jan last year Ragnarok Online worked perfectly, then when I upgraded wine a couple of months later it wouldn't work, so then I had to get an older version.

Simply put, if it works, don't "fix" it.

---

### Post by AndrewG on 2006-11-26
> **BoyOfDestiny said:**
> Well to compile it, download the tar.bz, extract it.
Go to that directory in a terminal.

type 

*./configure*

Watch for any messages about any file missing (go to synaptic, get package build-essential, and some other dev packages...)

try again, type 

*./configure*

Repeat until it looks good (no error messages, don't worry too much, this is pretty much a one time thing, once you have the -dev [development libraries] you'll be set)

then type

*make && make depend*

If you want the "easy way" to make a deb, but not really good for distributing (doesn't contain dependencies) but makes installing/removing a breeze...

*sudo apt-get install checkinstall*

then type

*checkinstall -D*

when done you'll have a .deb. Install it via gdebi or sudo dpkg -i nameofdeb.

Good luck.

Anyway, if all goes well, next version it should be as simple as
[I]./configure
make && make depend
checkinstall -D[/I]

painless :)

or if you'd rather not use checkinstall, and just install
type this instead of checkinstall -D
*sudo make install*

Thanks for that method, it worked great. **make** and **make depend** did however go the other way around.

I've uploaded the deb to [http://www.thewebdruid.com/files/wine/wine_0.9.26-1_i386.deb](http://www.thewebdruid.com/files/wine/wine_0.9.26-1_i386.deb) for anyone who wants it.

Now, how to create an apt repository?

---

### Post by Shay Stephens on 2006-11-26
> **AndrewG said:**
> I can wait, but it's just a bit surprising that it takes so long, that's all.

Faster than I could do it myself.  My advice is to stop checking for new versions from their website.  I now just wait for them to show up in their repository.  Then there is no wait ;-)

The other option I suppose is to write a letter demanding your money back hehehe

---

### Post by loell on 2006-11-26
> **AndrewG said:**
> Thanks for that method, it worked great. **make** and **make depend** did however go the other way around.

I've uploaded the deb to [http://www.thewebdruid.com/files/wine/wine_0.9.26-1_i386.deb](http://www.thewebdruid.com/files/wine/wine_0.9.26-1_i386.deb) for anyone who wants it.

Now, how to create an apt repository?

like the above post said, its not good for distributing ;) , as it does not resolve dependencies

---

### Post by AndrewG on 2006-11-26
> **Shay Stephens said:**
> Faster than I could do it myself.  My advice is to stop checking for new versions from their website.  I now just wait for them to show up in their repository.  Then there is no wait ;-)

It's not quite that simple I'm afraid. I've got Liferea set up with news coming from places including DistroWatch.com: Packages (something that won't be going in the near future) so that I know when a whole lot of other things come out such as the kernel, ImageMagick, snort etc. As soon as I know that a new version has come out, I get extremely excited and rush over to WineHQ.org to see what's changed.

Theres also a whole lot of Windows programs that I want to be able to run such as Photoshop, Windows Live Messenger, Office 2003 etc., but can't do so yet.

> **loell said:**
> like the above post said, its not good for distributing ;) , as it does not resolve dependencies

What do you mean by resolving dependencies? The official ones require certain packages whereas mine don't?

---

### Post by givré on 2006-11-26
> **AndrewG said:**
> 
Now, how to create an apt repository?
Don't provide repository for deb package created with checkinstall. Never.

You should better try to learn how to make REAL package. The best way to start is to read the guide you have with the system documentation. You can also look at the MOTU documentation on [http://wiki.ubuntu.com](http://wiki.ubuntu.com) (just search a bit).

Personally, i find that really stupid, but do what you want.

---

### Post by maniacmusician on 2006-11-26
> **givré said:**
> Don't provide repository for deb package created with checkinstall. Never.

You should better try to learn how to make REAL package. The best way to start is to read the guide you have with the system documentation. You can also look at the MOTU documentation on [http://wiki.ubuntu.com](http://wiki.ubuntu.com) (just search a bit).

Personally, i find that really stupid, but do what you want.
hehe, ease up my friend, it's not as if AndrewG did it with the knowledge that it was a bad thing. He's still learning, so cut him a little slack. at least he cares enough to try :)

AndrewG: checkinstall works well for your own system, but you shouldn't distribute a package made with it, as it's not a real package. To learn how to package programs properly, either look up the MOTU documentation as givré said, or find the Debian documentation on how to build a proper package. It's really a pretty useful skill to have (I don't possess it), so good luck learning it, I hope you get to help some people out.

---

### Post by zachtib on 2006-11-27
slightly offtopic:

why does winehq.org never seem to get updated anymore (or is it just me?)

i can manually go the the ?announce=0.9.26 page or whatever, but it doesn't show up on the front page

---

### Post by Shay Stephens on 2006-11-27
> **zachtib said:**
> why does winehq.org never seem to get updated anymore (or is it just me?)

Vacation?

---

### Post by shining on 2006-11-27
> **zachtib said:**
> slightly offtopic:

why does winehq.org never seem to get updated anymore (or is it just me?)

i can manually go the the ?announce=0.9.26 page or whatever, but it doesn't show up on the front page

Well, it seems there is regularly a lag for the announce on the web page. Wine releases are very frequent these days though, maybe a bit too much sometimes, and apparently the announce page doesn't keep up with the releases :)

---

### Post by BoyOfDestiny on 2006-11-27
> **AndrewG said:**
> Thanks for that method, it worked great. **make** and **make depend** did however go the other way around.

I've uploaded the deb to [http://www.thewebdruid.com/files/wine/wine_0.9.26-1_i386.deb](http://www.thewebdruid.com/files/wine/wine_0.9.26-1_i386.deb) for anyone who wants it.

Now, how to create an apt repository?

Thanks Andrew fixed the error.

Basically about the dependencies, it let's it know what runtime stuff the package needs. There is a good chance if they had wine 0.9.25, they can install your deb and it will run.

Checkinstall does allow you to add them manually, (requires) but still hackish...

The best way is to follow those guides and build it properly. I have tried, it takes longer (much more than 1 command), and some of my packages didn't run when installed...
But for distributing I guess it's a must... Until things like autodeb work 100%...

---

### Post by givré on 2006-11-27
> **BoyOfDestiny said:**
> 
But for distributing I guess it's a must... Until things like autodeb work 100%...
It's not a must it's a need.

Sorry to be so serious about that, but there were some discussion lately about the increasing of third party repository, and i think people should be more careful about that. People tends to trust to easily third party repository but we should pay more attention about them, because if they are not well maintain, they could have important consequence one your system (when upgrading for example).

Making an apt repository is rather easy. It's literally two lines of code, so  if everybody start to make repository with checkinstall packages this will be a nightmare. Starting to trust only people who really know how to make a deb package is i think a good start.

Checkinstall should only be use for personal use, and for personal use, i recommend to use it.

Thanks.

---

### Post by loell on 2006-11-27
join in [ubunu open week]("https://wiki.ubuntu.com/UbuntuOpenWeek") for those who are serious about about pacakge volunteering and maintenance

---

### Post by lotusleaf on 2006-11-27
I'd suggest anyone interested in building WINE for themselves read this page:

[Recommended Packages (Building Wine on 32bit)](http://wiki.winehq.org/Recommended_Packages)

And remember, there's the WINE IRC channel to get live answers to your questions:

[irc://irc.freenode.net/winehq](irc://irc.freenode.net/winehq)

There are lots of helpful people there!

---

### Post by lotusleaf on 2006-11-27
I brought this up earlier today in [#ubuntu-classroom](irc://irc.freenode.net/ubuntu-classroom). I edited my logs a bit for posting here with clarity:

> <lotusleaf> QUESTION: Are there any plans to keep WINE up-to-date and available as a .deb within the official Ubuntu repos, rather than have it sit at the version it is now within them, leaving people to use a 3rd party repo without a gpg key (unless they compile from source) to get the latest version?
<LaserJock> well, that is always the goal
<gnomefreak> what version is it at now?
<gnomefreak> 22?
<LaserJock> we don't sit around all day thinking how we can give users old, crusty software
<LaserJock> we try to do our best to have as stable and updated of software as we can
<LaserJock> but wine is maintained by the Ubuntu community and it's a tough packages
<LaserJock> so you are more than welcome to help maintain it and we can help you along the way
<cbx33> compiling from source is pretty easy
<cbx33> esp for wine
<LaserJock> Get in contact with the MOTU team
<LaserJock> either #ubuntu-motu or the ubuntu-motu mailing list on lists.ubuntu.com
<LaserJock> MOTU does a lot of work on helping people learn to create and maintain packages
<LaserJock> ok, lets move on a little bit more
<cbx33> it totally does
<cbx33> the pacakging guide is great too

That said, I just built 0.9.26 for myself from source and I'm going to continue to do this in the future so:

(a) I can get the latest version the day it's released, and
(b) So I can verify the gpg signature available at Sourceforge signed by Alexandre Julliard

Of course, I test applications frequently with each version of wine for submitting feedback to the [Wine Application Database](http://appdb.winehq.com/), so my want/need for a new version ASAP is a bit different. Generally, as others have said, if you have an application that works without problems, why update to a newer version? There may be a good reason, maybe not, but if you do update, please provide feedback to Wine's Application Database. :) As others have said, you could update and have a certain application that works fine with the version you were using suddenly stop working, so keep that in mind. On the other hand, it just may continue to work, and who knows, it may work better than before.

You can import Alexandre Julliard's key like so:

```
gpg --keyserver wwwkeys.pgp.net --recv-keys B9461DD7
```

Then when you download [wine source packages](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449) (downloading the bz2 and the sign file) you can verify it before using:

```
gpg --verify wine-0.9.26.tar.bz2.sign wine-0.9.26.tar.bz2
```

Remember now, that's the source package, you'll need to compile it yourself if you want bleeding edge the day a new version is released. :) Once you get it down once it's pretty simple.

---

