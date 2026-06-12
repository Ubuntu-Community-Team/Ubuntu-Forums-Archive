---
title: "GNObuntu ?"
date: 2012-06-08
forum: Ubuntu, Linux and OS Chat
---

### Post by Stinger on 2012-06-08
Hi all
Does anyone know if there is any development going on for a pure Gnome edition of 12.10 ?

[http://www.phoronix.com/scan.php?page=news_item&px=MTEwMTU]("http://www.phoronix.com/scan.php?page=news_item&px=MTEwMTU")

And if there is, where to follow it ?

I know there is the "Gnome Shell Remix" of ubuntu

[http://ubuntu-gs-remix.sourceforge.net/p/home/]("http://ubuntu-gs-remix.sourceforge.net/p/home/")

Does it have anything to do with the above ?

Thanks

---

### Post by VMC on 2012-06-08
Have you tried gnome-panel? That's what I'm using and loving it.

---

### Post by cariboo on 2012-06-08
The idea was approved at UDS-Q, all we need now is for someone to start work on it.

---

### Post by cpatrick08 on 2012-06-09
what would one need to do to start working on it?

---

### Post by Stinger on 2012-06-09
> **cariboo907 said:**
> The idea was approved at UDS-Q, all we need now is for someone to start work on it.

Sorry to hear that no one started working on it yet.

> **VMC said:**
> Have you tried gnome-panel? That's what I'm using and loving it.

Well.. I played around with Gnome on Fedora 17 and what I really liked was:

1. It not using as much memory as Unity when running idle

2. The way it handles the graphical desktop ( Gnome-Shell )
   They are using clutter / mutter instead of compiz and the                    llvmpipe so that Gnome-Shell can be used without 3D acceleration hardware, or the appropriate drivers. 
Maybe Quantal will use the llvmpipe too since there will be no Unity 2D ?

3. Reorganization of the directories (Usrmove) for executable files and libraries that are now all in the root directory / usr.

I know that the ubuntu developers are looking at these issues, but I don't know if it's possible for them to implement such huge changes ( clutter / mutter instead of compiz ) or (Usrmove).

Still I prefer Unity over Gnome-Shell for it's usability, but I admire the Fedora developers for their innovation.

---

### Post by jbicha on 2012-06-10
Hi,

I was doing some work on "GNOMEbuntu". My current blocker is that I've yet to figure out how to generate a Ubuntu-style live/installer ISO from a seed (i.e., the list of packages I want to be included by default). That process is not very well documented.

I'd prefer the process I use to be as close as possible to the way official images are generated. If anyone knows how to do that, I'd be happy to have the help!

---

### Post by Stinger on 2012-06-11
Preseeding ?
I don't know if you can use this, but here there is a guide on:

[Automating the installation using preseeding]("https://help.ubuntu.com/12.04/installation-guide/amd64/appendix-preseed.html")

[Using preseeding]("https://help.ubuntu.com/12.04/installation-guide/amd64/preseed-using.html")

[Preseeding other packages]("https://help.ubuntu.com/12.04/installation-guide/amd64/preseed-contents.html#preseed-other")

[InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization")

[Installing extra packages in your preseed file]("https://help.ubuntu.com/community/InstallCDCustomization#Installing_extra_packages_in_your_preseed_file")

Or you might have a look at Jan Hoffmann's livecd script for the Ubuntu Gnome Shell Remix:

[http://sourceforge.net/projects/ubuntu-gs-remix/files/live-script/20120427.12.04/]("http://sourceforge.net/projects/ubuntu-gs-remix/files/live-script/20120427.12.04/")

But I'm not familiar with building installer iso's
Hope it helps.

---

### Post by cpatrick08 on 2012-06-11
> **jbicha said:**
> Hi,

I was doing some work on "GNOMEbuntu". My current blocker is that I've yet to figure out how to generate a Ubuntu-style live/installer ISO from a seed (i.e., the list of packages I want to be included by default). That process is not very well documented.

I'd prefer the process I use to be as close as possible to the way official images are generated. If anyone knows how to do that, I'd be happy to have the help!
try [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)  and see if it will work for you

---

### Post by Stinger on 2012-06-12
Ok found GNObuntu on launchpad, thanks Jeremy :wink: 

[“Ubuntu GNOME Edition Developers” team]("https://launchpad.net/~ubuntu-gnome-dev")

---

### Post by DingusFett on 2012-06-18
I'm not a developer, but if you need someone to help test this once you have an iso, am happy to help out. Maybe a suggestion would be if someone could create an extension that adds updates to the shutdown/logout/etc menu like in Unity, which I think would be great and help with integration to make it feel less like you've just got standard Ubuntu and added gnome-shell to it.

---

### Post by Stinger on 2012-07-11
Ubuntu 12.10 has now reached alpha2 and still not much news regarding a GNObuntu or Gubuntu.

I have been testing out Fedora17,although It's giving me a very pleasant Gnome3 experience, it comes with a few rough edges and the tools and the software I'm used to from Ubuntu are either not available or not working without a bit of tweaking.

I'm not alone in my [Quest for the best Gnome3 distribution]("http://ploum.net/post/best-gnome3-distribution"):grin:

So now what to do ?
I found this article on:
[Totally remove Unity from Ubuntu 12.04]("http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html?utm_source=twitterfeed&utm_medium=twitter")
I tried it with a vanilla 12.10 Alpha2, I't works but there are just to many trade off's to make it useful yet, the biggest pain is that every time you have to make a partial upgrade you get all the unity packages and dependencies back again.

This brought me back to the [Ubuntu Gnome-shell remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/")
What if I added the [Gnome-Shell Testing PPA]("https://launchpad.net/~ricotz/+archive/testing") and the [GNOME3 Team ppa]("https://launchpad.net/~gnome3-team/+archive/gnome3") ?
It worked and I had a running almost clean Gnome 3.5.3(mostly).
But again there is a trade off, I lose my [Gnome Shell Extensions]("https://extensions.gnome.org/"), and I can't live without those.

So conclusion from here is;
The best working and most flexible (software wise) installation at present is a vanilla install of the [Ubuntu Gnome-shell remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/") without adding any GNOME3 Team or Gnome-Shell Testing ppa's.
My Kudos to [Jan Hoffmann]("https://launchpad.net/~jan-hoffmann") and everyone else (if any ) involved in the project, I love what you are doing.
I can highly recommend it to anyone who would like to work with a Gnome-Shell only desktop. 
But be a bit careful when adding ppa's ;)

[Unlike Linus]("https://plus.google.com/102150693225130002912/posts/UkoAaLDpF4i"), I really love my giant smartphone, point and click just works, IMHO Gnome-shell is a very productive desktop environment.

---

### Post by Stinger on 2012-07-13
If anyone is wondering, here is list and screenshot of the used extensions.

[Media player indicator]("https://extensions.gnome.org/extension/55/media-player-indicator/")

[Places Status Indicator]("https://extensions.gnome.org/extension/8/places-status-indicator/")

[Frippery Shut Down Menu]("https://extensions.gnome.org/extension/14/shut-down-menu/")

[Advanced Settings in UserMenu]("https://extensions.gnome.org/extension/130/advanced-settings-in-usermenu/")

I have two tweak-tools installed also:

[Gnome Tweak Tool]("https://live.gnome.org/GnomeTweakTool/")
and
[Ubuntu Tweak]("http://ubuntu-tweak.com/") 

I use [Asunder]("http://littlesvr.ca/asunder/") as CD-ripper and [Banshee]("http://banshee.fm/") as jukebox :D

---

### Post by Stinger on 2012-07-14
To the moderators:
I hope you'll all accept that until an official [Gnome-Shell]("https://live.gnome.org/GnomeShell/") version, be it alpha, beta or anything else, of QQ 12.10 is available this thread will mostly be about The [Ubuntu Gnome-Shell Remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/").

It's as close as we get to a pure [Gnome3]("http://www.gnome.org/") version of Ubuntu without any official release.

My hope is that [Jeremy Bicha]("https://launchpad.net/~jbicha") of the [Ubumtu Gnome Edition Developers Team]("https://launchpad.net/~ubuntu-gnome-dev") and [Jan Hoffmann]("https://launchpad.net/~jan-hoffmann") who made the [Ubuntu Gnome-Shell Remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/") at some point could join forces and make this happen :)

---

### Post by guimaster on 2012-08-11
What I'm seeing all over the web, is word that Gnome-Shell is dying in popularity. The more sensible idea is for a Gnome-Classic spin of Ubuntu. There would be no shortage of users eager to switch away from Unity, or to return to Ubuntu (people who've left for greener pastures since 11.04 landed).

---

### Post by Stinger on 2012-08-12
> **guimaster said:**
> What I'm seeing all over the web, is word that Gnome-Shell is dying in popularity. The more sensible idea is for a Gnome-Classic spin of Ubuntu. There would be no shortage of users eager to switch away from Unity, or to return to Ubuntu (people who've left for greener pastures since 11.04 landed).

I Have to disagree, I think you're wrong.
What we are seeing is a transformation process of the old menu-driven desktop interface into a newer app-oriented desktop interface.
Unity is a good example, but in my opinion a little to much inspired from the mac desktop.
The Gnome-shell is it's own and blends perfectly with the web, or with web apps.

Have you taken the time to try the Gnome-Shell Remix or Fedora17 before writing ?

---

### Post by BigSilly on 2012-08-12
> **Stinger said:**
> I Have to disagree, I think you're wrong.
What we are seeing is a transformation process of the old menu-driven desktop interface into a newer app-oriented desktop interface.
Unity is a good example, but in my opinion a little to much inspired from the mac desktop.
The Gnome-shell is it's own and blends perfectly with the web, or with web apps.

Have you taken the time to try the Gnome-Shell Remix or Fedora17 before writing ?

I agree with you that Gnome Shell is not failing or "dying in popularity". I spent a lot of time myself with Gnome Shell on openSUSE and it really is pretty amazing. I found it very intuitive and easy to use, and not limiting at all. There's just at the moment a hardcore of vocal detractors who don't like the changes being made to the desktop, but there are plenty of options available for those people if they would calm down.

I disagree that Unity is more Mac like than Gnome Shell though. I think they've both taken elements of various Mac desktops of the past and present and incorporated them into their own DE's. Shell is as guilty as Unity in this regard imho.

I'm still looking forward to Gubuntu, and I hope it happens. I think they should use that name regardless of Google's internal use of it. After all, Ubuntu is Ubuntu, and not Google. Does anyone know if this is still going ahead then? It's been very quiet since the announcement a while ago, and there's been no updates.

---

### Post by GreatDanton on 2012-08-12
At the time I had Fedora 17 I was very happy with it. I have to admit I like Unity especially alt command function, but Gnome shell is much more stable IMO. In Gnome shell I never had problems with screen flickering. In Unity this is very common problem. I also prefer to have more workspaces than 4.

Gnome shell is still alive, since many people prefer Gnome, because it's less buggy than Unity.

---

### Post by Stinger on 2012-08-12
> **BigSilly said:**
> I agree with you that Gnome Shell is not failing or "dying in popularity". I spent a lot of time myself with Gnome Shell on openSUSE and it really is pretty amazing. I found it very intuitive and easy to use, and not limiting at all. There's just at the moment a hardcore of vocal detractors who don't like the changes being made to the desktop, but there are plenty of options available for those people if they would calm down.

I disagree that Unity is more Mac like than Gnome Shell though. I think they've both taken elements of various Mac desktops of the past and present and incorporated them into their own DE's. Shell is as guilty as Unity in this regard imho.

I'm still looking forward to Gubuntu, and I hope it happens. I think they should use that name regardless of Google's internal use of it. After all, Ubuntu is Ubuntu, and not Google. Does anyone know if this is still going ahead then? It's been very quiet since the announcement a while ago, and there's been no updates.

Hear hear ! Gnome-Shell is alive and kicking b.. 
Let's not discuss Who's using bits and pieces from who, we know they all do it, strike my comment about unity and mac.

If you haven't tried the Gnome-Shell remix or Fedora17 for that matter ([Kororaa]("http://distrowatch.com/table.php?distribution=kororaa") if you want it to work right away ) , you should, I think they both give a better experience than Open Suse, Fedora is fast and Gnome is fully implemented, The Remix gives you all the benefits of Ubuntu and Gnome is implemented to a level that is way better than installing Gnome-shell from a Ubuntu desktop.
You are so right with your comment about the vocal detractors, we don't all have to live in the middle ages but those that prefer, fine by me, go for mate, cinnamon, xfce, you name it ther are lot of alternatives.
About the development. Like You I can't see any progress at all, it doesn't have to mean that nothing is going on, maybe all the developers are on summer Holiday ? naah... ;)  

There is another alternative under it's way:
The [Gnome-OS]("https://live.gnome.org/GnomeOS/Design/Whiteboards/") read more [here]("http://www.itwire.com/opinion-and-analysis/open-sauce/56143-gnome-os-a-bid-to-catch-up-with-the-big-boys") and [here]("http://www.h-online.com/open/news/item/GNOME-OS-plans-laid-out-1662865.html") or just google it.

---

### Post by Stinger on 2012-08-12
> **GreatDanton said:**
> At the time I had Fedora 17 I was very happy with it. I have to admit I like Unity especially alt command function, but Gnome shell is much more stable IMO. In Gnome shell I never had problems with screen flickering. In Unity this is very common problem. I also prefer to have more workspaces than 4.

I think your screen flickering is caused by compiz, compiz has a lot of features but IMHO also a lot of flaws.
Unity relies on compiz.
Gnome-Shell don't need compiz, it uses Mutter as compositing window manager.

---

### Post by jbicha on 2012-08-12
> **guimaster said:**
> What I'm seeing all over the web, is word that Gnome-Shell is dying in popularity. The more sensible idea is for a Gnome-Classic spin of Ubuntu. There would be no shortage of users eager to switch away from Unity, or to return to Ubuntu (people who've left for greener pastures since 11.04 landed).

Currently, my pre-alpha build of a GNOME edition includes GNOME Classic, although GNOME Shell is rightly the default.

I have two main things I need to take care of first before I'll make an alpha available for testing. Maybe I can get that done by Feature Freeze in a week and a half.

---

### Post by GreatDanton on 2012-08-12
Yes I also think that screen flickering is cause because of compiz. Everything is fine until some part of the application which is on workspaces 1, is also on the workspace 2. If that happen (often) and whenever I press super+w I got some crazy effects. The solution is to press super+w  2 times. It's not such big problem but it's annoying. However Gnome shell doesn't have this problem that's why I think Gnome shell is better.

@jbicha I will definitely test alpha of gnome shell as it will be released. 

Keep up the good work.

---

### Post by Stinger on 2012-08-13
> **jbicha said:**
> Currently, my pre-alpha build of a GNOME edition includes GNOME Classic, although GNOME Shell is rightly the default.

I have two main things I need to take care of first before I'll make an alpha available for testing. Maybe I can get that done by Feature Freeze in a week and a half.

Hi Jeremy, thanks for taking the time to chime in and explain the  development progress of GNObuntu / Gubuntu.
I see you figured out howto [generate a Ubuntu-style live/installer ISO from a seed]("http://ubuntuforums.org/showpost.php?p=12016160&postcount=6"), great !

I can get my hands down, we are gonna get a official GNObuntu =D> Thank you soo much. Can't wait to test your ISO\\:D/

It seems like a win / win situation here :D Both the users of Gnome-Shell and Gnome-Classic get what they want.

I got one question though, will GNObuntu ship with Nautilus version from Ubuntu or Nautilus from Gnome3 ?
Seems like [Ubuntu is planning some kinda fork of Nautilus]("https://mail.gnome.org/archives/nautilus-list/2012-August/msg00015.html") ?
there is a bugreport about it to on launchpad [Bug #1034080]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1034080")

---

### Post by guimaster on 2012-08-17
> **Stinger said:**
> I Have to disagree, I think you're wrong.
What we are seeing is a transformation process of the old menu-driven desktop interface into a newer app-oriented desktop interface.
Unity is a good example, but in my opinion a little to much inspired from the mac desktop.
The Gnome-shell is it's own and blends perfectly with the web, or with web apps.

Have you taken the time to try the Gnome-Shell Remix or Fedora17 before writing ?

I have used Gnome Shell installed in Ubuntu. I kind of liked it, but I don't like the changes they are planning. I'm just speaking based on what I see written all over the web, and what I see tells me that Gnome is a dying project.

---

### Post by Stinger on 2012-08-17
> **guimaster said:**
> I have used Gnome Shell installed in Ubuntu. I kind of liked it, but I don't like the changes they are planning. I'm just speaking based on what I see written all over the web, and what I see tells me that Gnome is a dying project.
You don't like the changes because they don't fit Unity ?

I hope for you and all other Ubuntu users that Gnome is not dying, because that would mean that Ubuntu and Unity is dying too, Ubuntu and Unity relies on Gnome3.

Don't be a grouch, embrace and love your Gnome, you depend on Gnome to have your desktop working.

Here is a good site to follow the Gnome development and the features of Gnome.
[http://worldofgnome.org/]("http://worldofgnome.org/")

Ps.
The desktop I have become so fond of and really love for it's innovation , vision and persistence in creating, what I think is  one of, if not, the best desktop interfaces today, has become 15 years old.

[**[COLOR="Red"]Happy Birthday Gnome ! [/COLOR]**]("http://www.happybirthdaygnome.org/")

---

### Post by CoreyB. on 2012-08-17
> **jbicha said:**
> I have two main things I need to take care of first before I'll make an alpha available for testing. Maybe I can get that done by Feature Freeze in a week and a half.

What are the two things?

---

### Post by Gyokuro on 2012-08-17
> **jbicha said:**
> Currently, my pre-alpha build of a GNOME edition includes GNOME Classic, although GNOME Shell is rightly the default.

I have two main things I need to take care of first before I'll make an alpha available for testing. Maybe I can get that done by Feature Freeze in a week and a half.

Hi

Thank you for your time and manpower which you invest in this project. Looking at the forthcoming problems with the integration of Unity on top of parts of Gnome I think you will need every support which you can get to bring your project in perfect shape is a huge task and therefore I would like to know what can be done to help you somehow.

---

### Post by jbicha on 2012-08-20
> **Stinger said:**
> I got one question though, will GNObuntu ship with Nautilus version from Ubuntu or Nautilus from Gnome3 ?
Seems like [Ubuntu is planning some kinda fork of Nautilus]("https://mail.gnome.org/archives/nautilus-list/2012-August/msg00015.html") ?
there is a bugreport about it to on launchpad [Bug #1034080]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1034080")

The Nautilus fork for Ubuntu doesn't exist yet. You could even say it's a rumor. On the other hand, the rumor did start from the Canonical Desktop Team Tech Lead. But then again, Feature Freeze is this week so it would need a Feature Freeze Exception.

If a split were to happen, GNOMEbuntu would obviously stick to the upstream Nautilus.

> **CoreyB. said:**
> What are the two things?

1. Figuring out what we're going to name the thing
2. Uploading the metapackage

---

### Post by CoreyB. on 2012-08-21
> **jbicha said:**
> 1. Figuring out what we're going to name the thing
2. Uploading the metapackage

That's fantastic!  Can't wait to see the alpha! Love it when we get more Ubuntu choices, everyone should be able to find something they like. ;)

---

### Post by CoreyB. on 2012-08-21
> **jbicha said:**
> If a split were to happen, GNOMEbuntu would obviously stick to the upstream Nautilus.

Would you then have to make a new package in the repos for this separate version of nautilus?

---

### Post by Stinger on 2012-08-21
> **jbicha said:**
> The Nautilus fork for Ubuntu doesn't exist yet. You could even say it's a rumor. On the other hand, the rumor did start from the Canonical Desktop Team Tech Lead. But then again, Feature Freeze is this week so it would need a Feature Freeze Exception.

If a split were to happen, GNOMEbuntu would obviously stick to the upstream Nautilus.

1. Figuring out what we're going to name the thing

I'm so glad to hear that we are sticking to upstream Nautilus. :D
Thank's a lot for answering my question.

The naming thing is difficult, **Gubuntu** is ruled out I think, because of googles Goobuntu.
**GNObuntu** maybe ? But some say it sound a little like "Gee no buntu" they don't like the negation.
**Gnubuntu** is taken and would indicate that it follows the free Software Foundation guidelines.
**Gnomebuntu** is actually not bad maybe we should stick with that one ?
Cheers

---

### Post by BigSilly on 2012-08-21
> **jbicha said:**
> 
1. Figuring out what we're going to name the thing


With respect, why the need to avoid the name **Gubuntu**? So what if Google uses a similar sounding name? I mean, they don't own the 'buntu name, and to me nothing fits the project better than Gubuntu. It makes sense alongside Kubuntu, Xubuntu and Lubuntu.

I just don't get why the need to avoid the most obvious name. What's Google got to do with things? Gubuntu is the most obvious choice, and to me the alternatives don't really suit.

---

### Post by cmcanulty on 2012-08-21
I agree and suspect some behind the scenes talks are going on between Google and Ubuntu. They are actually quite a talented pair.

---

### Post by hugmenot on 2012-08-22
My question is, will this spin remove the dependencies and all that crapola that is associated with canonical?

Single sign on, ubuntuone, unity, gconf, compiz, music store, software center. All that sub-useful stuff.

In essence, will it be a vanilla spin, or a stracciatella spin with all the things left in that lead to friction?

Also, will we get the gnome-settings-daemon and gnome-control-center of upstream. It’s currently really broken because of a battery of patches.

---

### Post by hugmenot on 2012-08-22
Also, call it Gubuntu. On the internet it doesn’t matter if it is a homophone, only spelling matters. And Goobuntu is a name internal  to Google only anyhow.

---

### Post by jbicha on 2012-08-22
> **hugmenot said:**
> 
Single sign on, ubuntuone, unity, gconf, compiz, music store, software center. All that sub-useful stuff.

In essence, will it be a vanilla spin, or a stracciatella spin with all the things left in that lead to friction?

Also, will we get the gnome-settings-daemon and gnome-control-center of upstream. It’s currently really broken because of a battery of patches.

[LIST]
[*]I don't see a problem with Ubuntu single sign on.
[*]Ubuntu One isn't included at the moment. Its UI is a bit crazy and it depends on QT libraries which takes up extra space.
[*]Unity won't be included
[*]gconf is still used by several GNOME & GTK apps
[*]Compiz is included, because GNOME Classic is currently included (with the indicators by the way because it makes the session far more useful by default)
[*]It's currently using Rhythmbox and I don't see a problem with including various music stores.
[*]I'm not sure whether it'll use Ubuntu's Software Center & Updater (update-manager) or gnome-packagekit (which will be called "Software" in the next release).
[*]As has been stated since May, we're going to try shipping Epiphany & Abiword instead of Firefox & LibreOffice. "Documents" will not be included as it currently depends on LibreOffice.
[*]We're even working to split out several customized Ubuntu settings to allow for a purer GNOME experience for those that want it.
[*]Although splitting gnome-control-center and ubuntu-control-center was a goal for this release, no one has stepped up to do it yet.
[*]As always, anyone can install other apps that they like after installing GNOMEbuntu.
[/LIST]
Although I never used it, I believe the stracciatella session was a vanilla-ish GNOME experience.

I strongly disagree with your assessment of those apps & technologies as sub-useful. They are a big part of why Ubuntu is as popular as it is.

---

### Post by Stinger on 2012-08-22
> **jbicha said:**
> 
I strongly disagree with your assessment of those apps & technologies as sub-useful. They are a big part of why Ubuntu is as popular as it is.

+1 for that 
That's exactly the reason why I choose Ubuntu.

I have another question:
What about the GDM log in manager, will it be used in GNOMEbuntu ?

---

### Post by jbicha on 2012-08-22
> **Stinger said:**
> +1 for that 
That's exactly the reason why I choose Ubuntu.

I have another question:
What about the GDM log in manager, will it be used in GNOMEbuntu ?

Yes, GNOME Shell 3.6 effectively requires GDM (it's used by the fancy new lock screen).

It  might be possible for a LightDM greeter or extension to duplicate this  functionality and be a swap-in, but we need someone to create that.

---

### Post by Stinger on 2012-08-22
@jbicha
Thanks again for answering.
GDM is just fine by me, I prefer GDM for Gnome :)

Gnomebuntu is, from what you are  writing, really making some good progress, hope to be running it soon.

---

### Post by hugmenot on 2012-08-22
> **jbicha said:**
> 
Although I never used it, I believe the stracciatella session was a vanilla-ish GNOME experience.

Thanks for the list. Stracciatella refers to a vanilla experience with some bits of Ubuntu-specific patches left in (i.e., the chocolate bits in the vanilla icecream). Some things make sense, like the indicators and their dependencies. But other things hold the whole stack up, like gnome-settings-daemon stuck at 3.4.2 in this mix of gconf and dconf limbo. It sucks.


> I strongly disagree with your assessment of those apps & technologies as sub-useful. They are a big part of why Ubuntu is as popular as it is.

Well, let&#8217;s say they are useful and necessary in the "monetization strategy" scheme of things, but they are not so popular with users because of intrinsic usefulness. It&#8217;s important that Canonical makes money, but the ways they tack on their stuff leads to lots of friction.

---

### Post by hugmenot on 2012-08-22
> **jbicha said:**
> [LIST]
[*]As always, anyone can install other apps that they like after installing GNOMEbuntu.
[/LIST]


I think my main interest stems from this. Will the GNOMEbuntu spin allow me to run a system closer to upstream by removing the patches and hard dependencies that were introduced?

Of course I can add and remove packages only to the extent that no conflicts arise. And the available PPAs only go so far.

The worst pain for me is the custom keyboard shortcuts and media-keys in g-s-d, which are broken because they still sit in Gconf.

Also I don&#8217;t understand why I need two separate online account thingies. The whole idea and its necessity is over my head.

One more thing, what about all those touch and gesture patches? Will you get rid of those too?

---

### Post by jbicha on 2012-08-22
> **hugmenot said:**
> I think my main interest stems from this. Will the GNOMEbuntu spin allow me to run a system closer to upstream by removing the patches and hard dependencies that were introduced?

Of course I can add and remove packages only to the extent that no conflicts arise. And the available PPAs only go so far.

The worst pain for me is the custom keyboard shortcuts and media-keys in g-s-d, which are broken because they still sit in Gconf.

You're in luck! Please see guitara's [latest call for testing]("http://ubuntuforums.org/showthread.php?t=2045579") as the gsettings keyboard shortcuts work is almost ready to land in Ubuntu.

> **hugmenot said:**
> 
Also I don’t understand why I need two separate online account thingies. The whole idea and its necessity is over my head.
I think part of the issue is that the GNOME Online Accounts (GOA) developers were stingy about what services they'd allow to be added, which means that Evolution & Empathy still need separate accounts preferences windows which means GOA isn't very useful. On the other hand, I'm not happy with Ubuntu Online Accounts as it looks to be just an alternative GUI for Empathy accounts and so we still need GOA for Contacts, Documents, etc.

> **hugmenot said:**
> 
One more thing, what about all those touch and gesture patches? Will you get rid of those too?

No, why would we do that?

---

### Post by hugmenot on 2012-08-23
> **jbicha said:**
> 
No, why would we do that?

Well I asked to see how thorough the push to close the gap to upstream will be. If you will, how much chocolate flakes will remain in your stracciatella flavor.

These gesture patches were crash prone earlier. I remeber that I had to push an eog without those patches to my PPA, because I had had to live without eog for months on my work PC because it would segfault on startup every time.

---

### Post by Stinger on 2012-08-23
And now, ladies and gentlemen, I give you:

[**Gnome 3.6 first impressions | Simply Beautiful!**]("http://worldofgnome.org/gnome-3-6-first-impressions-simply-beautiful/")

> *Note: I tested Gnome 3.5.9 in Mageia 3 (aka Cauldron) ..amazing distro. Probably the best distro out there..

That can't be truth :-#, I guess he haven't heard of Gnomebuntu yet ;-)

---

### Post by mcellius on 2012-08-23
> **Stinger said:**
> And now, ladies and gentlemen, I give you:

[**Gnome 3.6 first impressions | Simply Beautiful!**]("http://worldofgnome.org/gnome-3-6-first-impressions-simply-beautiful/")



That can't be truth :-#, I guess he haven't heard of Gnomebuntu yet ;-)

A telling quote from that article, regarding Nautilus:

> Is Files 3.6 overall better than Files 3.4? I let this to you to judge.  But I can say that is prettier. Much prettier. And for me that counts a  lot. More than functionality.Um, yeah.  That tells me not to trust much of what he says.

---

### Post by Stinger on 2012-08-23
> **mcellius said:**
> 
Um, yeah.  That tells me not to trust much of what he says.

But how can we trust you ? Have you even tried Gnome 3.6 ?

---

### Post by BigSilly on 2012-08-23
I don't think pretty is more important than functionality. I want both!

---

### Post by mcellius on 2012-08-23
> **Stinger said:**
> But how can we trust you ? Have you even tried Gnome 3.6 ?

You don't know.  I'm just saying that I don't think "pretty" is more important than "functionality."  I'm not saying you have to agree with me.

I do like "pretty," though, so I'd like to have both, too.

---

### Post by Stinger on 2012-08-23
> **mcellius said:**
> You don't know.  I'm just saying that I don't think "pretty" is more important than "functionality."  I'm not saying you have to agree with me.

I do like "pretty," though, so I'd like to have both, too.
Exactly, we all are entitled to our own opinion, even a person that makes a review, but that doesn't make him less trustworthy in my book. ;)

Be positive, love your Gnome (3.6) :grin:

---

### Post by guimaster on 2012-08-24
Because they don't fit Unity? No. I just don't like changes that are silly like:

You
Everyone Else
Some Other Dude 

That is downright ridiculous. (Changes to Permissions)

> **Stinger said:**
> You don't like the changes because they don't fit Unity ?

I hope for you and all other Ubuntu users that Gnome is not dying, because that would mean that Ubuntu and Unity is dying too, Ubuntu and Unity relies on Gnome3.

Don't be a grouch, embrace and love your Gnome, you depend on Gnome to have your desktop working.

Here is a good site to follow the Gnome development and the features of Gnome.
[http://worldofgnome.org/](http://worldofgnome.org/)

Ps.
The desktop I have become so fond of and really love for it's innovation , vision and persistence in creating, what I think is  one of, if not, the best desktop interfaces today, has become 15 years old.

[**[COLOR=Red]Happy Birthday Gnome ! [/COLOR]**]("http://www.happybirthdaygnome.org/")

---

### Post by Ichtyandr on 2012-08-24
When can first Gnobuntu image be expected? Will it be also provided through Ubuntu website, like Xubuntu eg? 
It can be serious contender for most Ubuntu family member. Gnome-shell is lighter and more customizable than Unity-3d right now, and Ubuntu already "naturally" integrates Gnome.

---

### Post by Corbelius on 2012-08-25
> **jbicha said:**
> Currently, my pre-alpha build of a GNOME edition includes GNOME Classic, although GNOME Shell is rightly the default.

I have two main things I need to take care of first before I'll make an alpha available for testing. Maybe I can get that done by Feature Freeze in a week and a half.

One question: this Gnobuntu, or whatelse, is a sort of GNOME "vanilla" (ubuntu patches free, like to Debian, Fedora, Arch, etc) or is a "simply" Ubuntu with GNOME Shell by default?

---

### Post by hugmenot on 2012-08-25
> **Corbelius said:**
> One question: this Gnobuntu, or whatelse, is a sort of GNOME "vanilla" (ubuntu patches free, like to Debian, Fedora, Arch, etc) or is a "simply" Ubuntu with GNOME Shell by default?

Did you read the thread?

Personally, I wouldn&#8217;t see the point of a separate spin if it boils down to a meta-package with some dependencies that differ from the default seed. If GNOMEbuntu then go all the way.

One advantage would be that I would again be able to pester the Gnome developers upstream in a timely manner. Right now the delta is too large (see, e.g., nautilus, gnome-control-center, gnome-settings-daemon, gnome-shell)

---

### Post by Stinger on 2012-08-29
> **hugmenot said:**
> Well I asked to see how thorough the push to close the gap to upstream will be. If you will, how much chocolate flakes will remain in your stracciatella flavor.

These gesture patches were crash prone earlier. I remeber that I had to push an eog without those patches to my PPA, because I had had to live without eog for months on my work PC because it would segfault on startup every time.

"I remeber that I had to push an eog without those patches to my PPA"

Are you one of the Ubuntu developers too ? Just curious ;)

---

### Post by Stinger on 2012-08-29
> **jbicha said:**
> [LIST]
[*]Although splitting gnome-control-center and ubuntu-control-center was a goal for this release, no one has stepped up to do it yet.
[/LIST]


Have a look at the Gnome Control Center here:
**[A preview of Gnome 3.6 in Quantal]("http://worldofgnome.org/a-preview-of-gnome-3-6-in-quantal/")**
Seems that [Rico Tzschichholz]("https://launchpad.net/~ricotz") has done several improvements :D

There's also a link to the **[Ubuntu GNOME Edition]("http://gnomebuntu.org/")** homepage.

---

### Post by BigSilly on 2012-08-29
> **Stinger said:**
> Have a look at the Gnome Control Center here:
**[A preview of Gnome 3.6 in Quantal]("http://worldofgnome.org/a-preview-of-gnome-3-6-in-quantal/")**
Seems that [Rico Tzschichholz]("https://launchpad.net/~ricotz") has done several improvements :D

There's also a link to the **[Ubuntu GNOME Edition]("http://gnomebuntu.org/")** homepage.

So ***Gnomebuntu*** it is then. Shame.

---

### Post by kuvanito on 2012-08-29
> From Stinger:
Does anyone know if there is any development going on for a pure Gnome edition of 12.10?

Well,I am running Ubuntu 12.10 Quantal Quetzal Pure 100% Gnome Edition with no traces of Unity and it's not from any developer.You can do this yourself in say less than 20 minutes.It actually runs smoother than Unity graphics ways,could i say more stable,so smooth it looks like a finished product but Gnome still brings new things everyday.
Note:This is not just Gnomeshell over Unity.It is Gnome 3.5.90 Latest stable,the Beta is at 3.6.0

---

### Post by defconoii on 2012-08-29
By adding the ricotz/testing and ricotz/staging ppa to quantal and installing gdm be enough to test this out?  Should I also remove unity and is their any other ppa's I should add?  How's the general stability

---

### Post by stephenmac7 on 2012-08-29
> **kuvanito said:**
> Well,I am running Ubuntu 12.10 Quantal Quetzal Pure 100% Gnome Edition with no traces of Unity and it's not from any developer.You can do this yourself in say less than 20 minutes.It actually runs smoother than Unity graphics ways,could i say more stable,so smooth it looks like a finished product but Gnome still brings new things everyday.
Note:This is not just Gnomeshell over Unity.It is Gnome 3.5.90 Latest stable,the Beta is at 3.6.0

Yes, I like your amibiant theme

---

### Post by kuvanito on 2012-08-29
> **defconoii said:**
> By adding the ricotz/testing and ricotz/staging ppa to quantal and installing gdm be enough to test this out?  Should I also remove unity and is their any other ppa's I should add?  How's the general stability
not enough,you must install gnome from it's ophan state to be real gnome 100% and all traces of unity must be removed,something like this:

1-sudo apt-get install gdm gnome-shell synaptic deborphan  (offcourse select gdm)
2-sudo apt-get remove unity unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread unity-asset-pool unity-common unity-lens-applications unity-lens-files unity-lens-music unity-lens-video unity-scope-musicstores unity-scope-video-remote unity-services indicator-messages indicator-status-provider-mc5 appmenu-qt appmenu-gtk appmenu-gtk3 lightdm unity-greeter overlay-scrollbar zeitgeist zeitgeist-core zeitgeist-datahub activity-log-manager-common activity-log-manager-control-center
3-sudo apt-get autoremove
4-sudo reboot (choose Gnome at login)
5-sudo apt-get purge `deborphan`
6-sudo dpkg --purge `dpkg -l | egrep "^rc" | cut -d' ' -f3`
7-sudo apt-get autoremove
8-sudo apt-get autoclean
9-sudo reboot
We will then have a clean Ubuntu 12.10 and distilled, with only Gnome.

I hope the Mods fellows here don't start getting upset.Thank You. :)

---

### Post by Stinger on 2012-08-29
> **kuvanito said:**
> Well,I am running Ubuntu 12.10 Quantal Quetzal Pure 100% Gnome Edition with no traces of Unity and it's not from any developer.You can do this yourself in say less than 20 minutes.
Yeah I know, have done that earlier, there are several ways to do that. 
But [COLOR="Red"]an official supported version is the purpose of this thread[/COLOR] and  what I aim for.8)
To quote myself from earlier:
> **Stinger said:**
> the biggest pain is that every time you have to make a partial upgrade you get all the unity packages and dependencies back again.

---

### Post by defconoii on 2012-08-29
> **kuvanito said:**
> not enough,you must install gnome from it's ophan state to be real gnome 100% and all traces of unity must be removed,something like this:

1-sudo apt-get install gdm gnome-shell synaptic deborphan  (offcourse select gdm)
2-sudo apt-get remove unity unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread unity-asset-pool unity-common unity-lens-applications unity-lens-files unity-lens-music unity-lens-video unity-scope-musicstores unity-scope-video-remote unity-services indicator-messages indicator-status-provider-mc5 appmenu-qt appmenu-gtk appmenu-gtk3 lightdm unity-greeter overlay-scrollbar zeitgeist zeitgeist-core zeitgeist-datahub activity-log-manager-common activity-log-manager-control-center
3-sudo apt-get autoremove
4-sudo reboot (choose Gnome at login)
5-sudo apt-get purge `deborphan`
6-sudo dpkg --purge `dpkg -l | egrep "^rc" | cut -d' ' -f3`
7-sudo apt-get autoremove
8-sudo apt-get autoclean
9-sudo reboot
We will then have a clean Ubuntu 12.10 and distilled, with only Gnome.

I hope the Mods fellows here don't start getting upset.Thank You. :)
Thanks, worked out just fine, cleaned up allot of clutter and seems to be a speed boost as well!  So far gnome-shell on 12.10 is much smoother than on 12.04.  The only issue I got now is im using the open source radeon driver and not fglrx, no quakelive for me ;\ lol

---

### Post by manliodp on 2012-08-30
I know that the name is not important but i think GNOBUNTU is a lot better than GNOMEBUNTU..i thought GNOBUNTU was the chosen name, I really hope you think again about it :)

Anyway I would really say THANK YOU for your effort, it will be a great release!

---

### Post by cmcanulty on 2012-08-30
Are all the commands listed in post #61 safe if I am using gnome classic 12.04? Sorry for a dumb? question

---

### Post by jerrylamos on 2012-08-30
I haven't been following the gnome effort - just seems to me, ubuntu, kubuntu, lubuntu, xubuntu, gnubuntu, all rhyme.

With quantal by preference I use lxde on my tower, notebook, netbook.  "unity" will function on them.  I have to watch the COC on this topic.

2D precise is also on all of them for recovery on "Alpha oops". 

Jerry

p.s. Even Lucid Grub2 on my dual hard drive tower because quantal gets sda and sdb and hd0 and hd1 screwed up on sata vs. ide and boot drive vs. slave drive.  Development has no interest in the launchpad bug, just something else for the user to deal with.  Grub2 will frantically search for UUID on one hard drive when Ubiquity has put that UUID on the other hard drive and Grub2 refuses to look there....I assume gnubuntu will have the same situation.

---

### Post by Stinger on 2012-08-30
> **cmcanulty said:**
> Are all the commands listed in post #61 safe if I am using gnome classic 12.04? Sorry for a dumb? question
They DON'T come with any kind of guarantee !! You are on your own !! 
This is the tutorial I used with QQ alpha2
[http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html?utm_source=twitterfeed&utm_medium=twitter](http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html?utm_source=twitterfeed&utm_medium=twitter)

[COLOR="Red"][B]Please don't hijack this thread with your customized installations. Make your own threads !
It has already been covered [here]("http://ubuntuforums.org/showpost.php?p=12094376&postcount=11").
I recommend the use of [Ubuntu Gnome-shell remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/") or ubuntu QQ with Gnome-Shell, until we get the first alpha of GNO / GNOMEbuntu.

The purpose of this thread is an official version of GNO / GNOMEbuntu !![/B][/COLOR]

---

### Post by kuvanito on 2012-08-30
> **Stinger said:**
> They DON'T come with any kind of guarantee !! You are on your own !! 
This is the tutorial I used with QQ alpha2
[http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html?utm_source=twitterfeed&utm_medium=twitter](http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html?utm_source=twitterfeed&utm_medium=twitter)

[COLOR="Red"][B]Please don't hijack this thread with your customized installations. Make your own threads !
It has already been covered [here]("http://ubuntuforums.org/showpost.php?p=12094376&postcount=11").
I recommend the use of [Ubuntu Gnome-shell remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/") or ubuntu QQ with Gnome-Shell, until we get the first alpha of GNO / GNOMEbuntu.

The purpose of this thread is an official version of GNO / GNOMEbuntu !![/B][/COLOR]

You are absolutely right!
But then again this open source,free,free for you and me,free for all and free to be modified as you or I please so feel FREE! ):P

---

### Post by checoimg on 2012-08-30
WHat do you guys think about "Gnubuntu" ?

---

### Post by defconoii on 2012-08-30
> **checoimg said:**
> WHat do you guys think about "Gnubuntu" ?

I think that Ubuntu needs to get rid of unity and go with straight gnome like other distro's, if their dev's worked with the gnome project im sure it would also be greatly improved.  So GNObuntu in my opinion is a great start.

---

### Post by jerrylamos on 2012-08-30
> **checoimg said:**
> WHat do you guys think about "Gnubuntu" ?

Sure.  ubuntu, lubuntu, xubuntu, kubuntu, gnubuntu (list order your option)

As I understand from this forum, the ubuntu management mantra is "unity everywhere", pc's, ipads, ipods, smartphones, ...

Well, maybe when Nook has 2 gHz dual processors with 4G memory and a very fast SSD it might handle the then further developed (I presume more features are coming) Unity/Compiz.  My opinion.  I don't intend to cause any problem with the ubuntu development forum COC.

The market will decide.  Meanwhile I'm trying a few different desktops, which works as long as ubuntu is compatible with debian.

---

### Post by julo42 on 2012-08-31
Hi everyone,

what's the plan concerning gnome-online-accounts and ubuntu-signon in gnomebuntu? Here is the situation today:
 - Evolution is supposed to work with gnome-online-accounts but is currently broken (accounts can't be added, neither manually nor via goa)
 - Empathy used to work with goa, but now it's been patched to work with ubuntu-signon instead.
 - Gnome-documents seems to work with goa only.
 - Gnome-contacts doesn't work anymore, neither with goa nor with ubuntu-signon.
 - Shotwell and Gwibber work well with ubuntu-signon.

---

### Post by julo42 on 2012-08-31
I noticed you pushed a new ubuntu-gnome-default-settings package which ovverrides some dconf settings. That's great but I think you need to revert ubuntu changes to the default theme too: use Adwaita instead of Ambiance by default please!

---

### Post by ahood on 2012-08-31
I am interested in using Gnome/Ubuntu. I am not a developer, but can test/troubleshoot.

---

### Post by jerrylamos on 2012-08-31
Question - how do I delete the bottom panel on Gnome Shell?

This is a very typical 1366x768 display, horizontal lines are at a premium.

Gubuntu is using up 2 horizontal lines.

LXDE very neatly uses one horizontal line to do the combination of what takes up two horizontal lines on Gnome Shell.  I don't need the tabs on the bottom panel since Alt-Tab does the job easily and quickly.

On Meerkat, Lucid, ... I used to be able to delete the bottom panel with a right click.

Thanks for hints, 

Jerry

Gnubuntu is on another partition so I can switch back and forth with reboot.  I would like to log back and forth between LXDE and gnome shell so I'm looking carefully at the very nice post by kuvanito to remove just the unity stuff and not, for example, lightdm which I think LXDE uses?

---

### Post by vasa1 on 2012-08-31
> **jerrylamos said:**
> ...
Gubuntu is using ...
Gnubuntu is on another ...
I think they've decided on Gnomebuntu? Would be mods consider renaming the thread if that is correct?

---

### Post by Cypher2 on 2012-08-31
Maybe you guys should go look at a fedora 17 or 18 live session and dig out the gnome-session and gnome shell default dconf settings out of there. It's as vanilla as it gets for that distro. Been using it for a year and a half now since unity came in. I really can't wait to try gnobuntu when it's out.

---

### Post by jbicha on 2012-08-31
> **julo42 said:**
> Hi everyone,

what's the plan concerning gnome-online-accounts and ubuntu-signon in gnomebuntu? Here is the situation today:
 - Evolution is supposed to work with gnome-online-accounts but is currently broken (accounts can't be added, neither manually nor via goa)
 - Empathy used to work with goa, but now it's been patched to work with ubuntu-signon instead.
 - Gnome-documents seems to work with goa only.
 - Gnome-contacts doesn't work anymore, neither with goa nor with ubuntu-signon

Could you open bugs about those issues? Currently in Ubuntu we need both gnome-online-accounts and ubuntu-signon. It would be nice to be able to just include one.

---

### Post by jbicha on 2012-08-31
> **julo42 said:**
> I noticed you pushed a new ubuntu-gnome-default-settings package which ovverrides some dconf settings. That's great but I think you need to revert ubuntu changes to the default theme too: use Adwaita instead of Ambiance by default please!

Try uninstalling ubuntu-artwork.

ubuntu-artwork is not installing its gsettings overrides correctly which means it can't be overriden by different overrides easily.

---

### Post by Cypher2 on 2012-08-31
Um, why don't you guys build up on a server image, which normally has no DE or settings installed, and check the package differential to know what to add and what not to add, and then tweak it as you find missing links or other stuff...

One thing is for sure, you won't have to kill yourself with all the Unity* dependencies unless they're built into a package which requires them, you can verify those on install and avoid them...

---

### Post by julo42 on 2012-08-31
> **jbicha said:**
> Could you open bugs about those issues? Currently in Ubuntu we need both gnome-online-accounts and ubuntu-signon. It would be nice to be able to just include one.

There are opened bugs for Evolution and Gnome-contacts:
[https://bugs.launchpad.net/evolution/+bug/1034331](https://bugs.launchpad.net/evolution/+bug/1034331)
[https://bugs.launchpad.net/ubuntu/+source/gnome-contacts/+bug/1024606](https://bugs.launchpad.net/ubuntu/+source/gnome-contacts/+bug/1024606)

For Empathy, there is no bug to open as this is - I think - the expected behaviour on Ubuntu (but maybe not on GNOMEbuntu?), and for documents, it is the expected behaviour on stock gnome (but maybe not on ubuntu and / or GNOMEbuntu?).

---

### Post by julo42 on 2012-08-31
> **jbicha said:**
> Try uninstalling ubuntu-artwork.

ubuntu-artwork is not installing its gsettings overrides correctly which means it can't be overriden by different overrides easily.

I have just removed ubuntu-artwork and Ambiance is still the default GTK theme. To check this, I have launched dconf-editor, clicked on org.gnome.desktop.interface.gtk-theme, then "set to default". While "Adwaita" is correctly displayed, Ambiance is actually set (this is a known bug where dconf-editor displays the stock default but actually applies the overridden default: [https://bugs.launchpad.net/bugs/884943](https://bugs.launchpad.net/bugs/884943)).

---

### Post by Cypher2 on 2012-08-31
> **julo42 said:**
> I have just removed ubuntu-artwork and Ambiance is still the default GTK theme. To check this, I have launched dconf-editor, clicked on org.gnome.desktop.interface.gtk-theme, then "set to default". While "Adwaita" is correctly displayed, Ambiance is actually set (this is a known bug where dconf-editor displays the stock default but actually applies the overridden default: [https://bugs.launchpad.net/bugs/884943](https://bugs.launchpad.net/bugs/884943)).

So override it for now by manually setting it to 'Adwaita' and save it as default using the root/live UID.

Are you working with chroot env?

---

### Post by jbicha on 2012-08-31
> **julo42 said:**
> I have just removed ubuntu-artwork and Ambiance is still the default GTK theme. To check this, I have launched dconf-editor, clicked on org.gnome.desktop.interface.gtk-theme, then "set to default". While "Adwaita" is correctly displayed, Ambiance is actually set (this is a known bug where dconf-editor displays the stock default but actually applies the overridden default: [https://bugs.launchpad.net/bugs/884943](https://bugs.launchpad.net/bugs/884943)).

I tested removing ubuntu-artwork now and it worked after logging out and logging back in.

Try ```
gsettings get org.gnome.desktop.wm.preferences theme
```

---

### Post by julo42 on 2012-08-31
> **Cypher2 said:**
> So override it for now by manually setting it to 'Adwaita' and save it as default using the root/live UID.

Are you working with chroot env?

You're misunderstanding me: I'm not looking for a solution for me, I'm just asking for the settings to be correctly set back to the stock defaults on future GNOMEbuntu installs, but I guess Jeremy and his team are working on it anyway.

---

### Post by Cypher2 on 2012-08-31
> **julo42 said:**
> You're misunderstanding me: I'm not looking for a solution for me, I'm just asking for the settings to be correctly set back to the stock defaults on future GNOMEbuntu installs, but I guess Jeremy and his team are working on it anyway.

I did understand you. I proposed that until the dconf bugs get sorted out I suppose.

Logically, does dconf revert back to 'stock' when removing the packages that reconfigure those keys?

---

### Post by julo42 on 2012-08-31
> **jbicha said:**
> I tested removing ubuntu-artwork now and it worked after logging out and logging back in.

Try ```
gsettings get org.gnome.desktop.wm.preferences theme
```

OK, I didn't know I needed to log out / log in. Now it works perfectly. Sorry ;)

---

### Post by julo42 on 2012-08-31
> **Cypher2 said:**
> I did understand you. I proposed that until the dconf bugs get sorted out I suppose.

Logically, does dconf revert back to 'stock' when removing the packages that reconfigure those keys?

Actually, removing ubuntu-artwork (which is not a dependancy of ubuntu-gnome-desktop) does revert all the theme-related dconf keys to the stock default. So everything is fine!

---

### Post by Cypher2 on 2012-08-31
> **julo42 said:**
> Actually, removing ubuntu-artwork (which is not a dependancy of ubuntu-gnome-desktop) does revert all the theme-related dconf keys to the stock default. So everything is fine!

Perfect :)

---

### Post by Cypher2 on 2012-08-31
Has anyone given any thought, given the 'vanilla' flavor this distro variant will be having to give it a more unified look when transitioning from grub, to plymouth, to gdm to desktop?

what I mean is that given the guidelines, we can have the same exact background (Ubuntu logo on aubergine solid backdrop [HEX #2C001E]) for all three stages, using the logo provided in the Plymouth sub-directory, thus unifying the whole lot of transitions...

---

### Post by julo42 on 2012-08-31
> **Cypher2 said:**
> Has anyone given any thought, given the 'vanilla' flavor this distro variant will be having to give it a more unified look when transitioning from grub, to plymouth, to gdm to desktop?

what I mean is that given the guidelines, we can have the same exact background (Ubuntu logo on aubergine solid backdrop [HEX #2C001E]) for all three stages, using the logo provided in the Plymouth sub-directory, thus unifying the whole lot of transitions...

From my tests, on ubuntu-gnome-desktop, we have the same desktop background in GDM and gnome-shell. Not sure about GRUB and plymouth though...

---

### Post by Cypher2 on 2012-08-31
That I am aware of, since they are by default served by a specified background file on the system (can't remember under which directory though).

Starting from an ubuntu base, plymouth should already be set, it's then just a matter of changing gdm, shell and grub.

you can modify gdm by enabling the "xhost +" parameter and then launching dconf editor as "gdm" user.

would you mind trying to see? I assure you, the result is quite appealing.

Here is a sample of the config i use on fedora which can give you an idea as to where to look and what to change...grub shouldnt be too bad to change (just the color):

```


# User #
gsettings set org.gnome.desktop.background picture-options "centered"
gsettings set org.gnome.desktop.background picture-uri "file:///usr/share/plymouth/themes/charge/throbber-15.png"
gsettings set org.gnome.desktop.background primary-color "#202020"
gsettings set org.gnome.desktop.background secondary-color "#202020"

# GDM #

xhost +

sudo -u gdm gsettings set org.gnome.desktop.background picture-options "centered"
sudo -u gdm gsettings set org.gnome.desktop.background picture-uri "file:///usr/share/plymouth/themes/charge/throbber-15.png"
sudo -u gdm gsettings set org.gnome.desktop.background primary-color "#202020"
sudo -u gdm gsettings set org.gnome.desktop.background secondary-color "#202020"

```

---

### Post by Stinger on 2012-08-31
Hey all Ubuntu guys and girls ( really like the last ones ;) )

I've been spreading the word, hope the dev's don't mind. I think all Gnome fans need to know about GNObuntu. 
This has resulted in a few nice articles :D
Look here:

**[GNOMEbuntu is set to arrive in October, 18!]("http://worldofgnome.org/gnomebuntu-is-set-to-arrive-in-october-18/")**

**[GNOMEbuntu Will Be Available This October]("http://www.muktware.com/4247/gnomebuntu-will-be-available-october")**

**[GNOME-flavoured Ubuntu Spin Coming October 18th]("http://www.omgubuntu.co.uk/2012/08/gnome-flavoured-ubuntu-spin-coming-october-18th")**

Especially like the one from [Muktware]("http://www.muktware.com/"), very informative !

More good news, another developer has joined the team,  [Robert Ancell]("https://launchpad.net/~robert-ancell"), thanks for joining the team.
And [Satyajit Sahoo]("https://launchpad.net/~satyajit-happy") is on hold, this could mean some serious artwork :D

And we are starting to get some code, look here:
[https://code.launchpad.net/~ubuntu-gnome-dev]("https://code.launchpad.net/~ubuntu-gnome-dev")

A new suggestion for a name could be **uGuntu** ?
Suggested by frank_O from the [Gnome board]("https://mail.gnome.org/archives/marketing-list/2012-August/msg00029.html")

Cheers !

---

### Post by Cypher2 on 2012-08-31
Been working on a clean server slate of gnobuntu using 12.04 as a base to test package behavior.

Maybe  using the core desktop Ubuntu image for 12.10 and then adding the required packages by priority and config order would end up with a much cleaner result.

The base config for a functional but very bare desktop is core+gdm+gnome-shell+gnome-terminal.

---

### Post by mc4man on 2012-09-01
> **Stinger said:**
> 
This has resulted in a few nice articles :D
Look here:

What's interesting there is 2 say it will go with the 3.6 nautilus, one says it will stick with the 3.4 one currently in use.
I guess we'll see...

If going with the 3.6 then would be interesting to see how far else with 3.6. Nautilus has added some symbolic icons that would require a new glib or the current .10 glib patched. A new glib may then lead to some other packages needing updates ect. 

(- here I've tried both ways, _for the moment_ prefer a patched glib which works ok with the current naut git master & 3.4.3 totem/grilo-0.1/gstreamer0.10 ect.
A new glib also worked fine with naut but not totem, needed a 3.5.90 totem/gstreamer1.0 which wants grilo-0.2 which doesn't work out so well atm (the plugins
The newer sources are much better though I've no idea if there is an issue using them in 12.10. And as far as grilo-plugins, well Ubuntu doesn't seem to want to supply them anyway..

---

### Post by jbicha on 2012-09-01
> **Cypher2 said:**
> 
you can modify gdm by enabling the "xhost +" parameter and then launching dconf editor as "gdm" user.


Instead of doing that, why don't you try editing /etc/gdm/greeter.gsettings and restarting gdm? Although slightly out of date, that's mentioned in /usr/share/doc/gdm/README.Debian

> **mc4man said:**
> What's interesting there is 2 say it will go with  the 3.6 nautilus, one says it will stick with the 3.4 one currently in  use.


The Ubuntu GNOME remix will be using Nautilus 3.4 since that's what will be in the Ubuntu archives. For those that want the 3.6 stuff that doesn't make it into 12.10, there's always the GNOME3 PPA. Since our goal is to be an official recognized flavor, we can't use PPAs.

Totem 3.6 will not be in Ubuntu 12.10 because it uses gstreamer1.0 and the Ubuntu CD will only include the older not-quite-compatible gstremaer0.10.

---

### Post by Stinger on 2012-09-02
> **jbicha said:**
> 
The Ubuntu GNOME remix will be using Nautilus 3.4 since that's what will be in the Ubuntu archives. For those that want the 3.6 stuff that doesn't make it into 12.10, there's always the GNOME3 PPA. Since our goal is to be an official recognized flavor, we can't use PPAs.

Totem 3.6 will not be in Ubuntu 12.10 because it uses gstreamer1.0 and the Ubuntu CD will only include the older not-quite-compatible gstremaer0.10.

I'm sorry to hear that we are now using Nautilus 3.4 and  not will be using Totem 3.6, but I guess it comes down to If you want to be true to Ubuntu or you want to be true to Gnome.

Although "Ubuntu Gnome Remix" will give a cleaner Gnome experience it will not be a clean Gnome 3.6 and I thought the whole idea of GNObuntu was to follow the Gnome releases upstream ?
Why should GNObuntu have to stick to the Ubuntu Gnome package versions ? As a separate spin, I think,  it should use it's own packages on top of the Ubuntu base

Personally I would rather have an unofficial GNObuntu that follows the Gnome releases than have an official release thats gonna be a mix of Gnome 3.4 and 3.6

---

### Post by smartboyhw on 2012-09-02
Hey, can I help dev too? Or at least I can help testing. I'm good at testing you know:) Documentation is also my tea:) I actually want a GNOME ubuntu.

---

### Post by xebian on 2012-09-02
Totem 3.6 is no longer maintained anyway.  It is now called Videos.:p

---

### Post by jbicha on 2012-09-02
OK, have fun!

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes)

---

### Post by mc4man on 2012-09-02
> **jbicha said:**
> OK, have fun!

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes)

403 here, guess I don't get the idea ?

---

### Post by Stinger on 2012-09-02
> **mc4man said:**
> 403 here, guess I don't get the idea ?
Same here, "403 Forbidden" But thanks anyway, guess it'll soon be fixed ;)

---

### Post by cariboo on 2012-09-02
That's strange, as it works fine from here.

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes)

---

### Post by jbicha on 2012-09-02
Thanks, I have to figure out how to configure Apache to handle torrents correctly but for now I just uploaded the torrents to the wiki directly.

---

### Post by Gyokuro on 2012-09-02
**Forbidden**

 You don't have permission to access /~jbicha/gnomebuntu/quantal-ubuntu-gnome-amd64-20120902.iso.torrent on this server.

---

### Post by mc4man on 2012-09-02
> **Gyokuro said:**
> **Forbidden**

 You don't have permission to access /~jbicha/gnomebuntu/quantal-ubuntu-gnome-amd64-20120902.iso.torrent on this server.

click on 'Attachments' at top of wiki page

---

### Post by Stinger on 2012-09-02
@jbicha
Thanks, downloading right now

---

### Post by Gyokuro on 2012-09-02
> **mc4man said:**
> click on 'Attachments' at top of wiki page

Thank you - need more seeders - I will keep it seeding for the next days.

---

### Post by kuvanito on 2012-09-02
this is awful
give it to distrowatch
180kb/s that suxs!!!!!

---

### Post by GreatDanton on 2012-09-02
kuvanito: Still better than my problem :D

Regards.

Edit: wow now there is one peer. Download speed 30kb/s

---

### Post by kansasnoob on 2012-09-02
> **jbicha said:**
> OK, have fun!

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes)

Awesome :)

I'm downloading now. My boxes will soon be tied up with iso/upgrade testing for a few days but after Quantal Beta 1 is released I'll keep my Intel box cooking 24/7 seeding this torrent :D

---

### Post by kansasnoob on 2012-09-02
One super dumb question. I know we should be OK using a torrent but is there an MD5SUM?

---

### Post by jbicha on 2012-09-02
Yes, [http://people.ubuntu.com/~jbicha/gnomebuntu/MD5SUMS](http://people.ubuntu.com/~jbicha/gnomebuntu/MD5SUMS)

e81aecc7925e5f53f37edb0ce1bc0e50  quantal-ubuntu-gnome-amd64-20120902.iso

77e33e789701ef695bafb6f38c51649e  quantal-ubuntu-gnome-i386-20120902.iso

---

### Post by Cypher2 on 2012-09-02
> **Stinger said:**
> I'm sorry to hear that we are now using Nautilus 3.4 and  not will be using Totem 3.6, but I guess it comes down to If you want to be true to Ubuntu or you want to be true to Gnome.

Although "Ubuntu Gnome Remix" will give a cleaner Gnome experience it will not be a clean Gnome 3.6 and I thought the whole idea of GNObuntu was to follow the Gnome releases upstream ?
Why should GNObuntu have to stick to the Ubuntu Gnome package versions ? As a separate spin, I think,  it should use it's own packages on top of the Ubuntu base

Personally I would rather have an unofficial GNObuntu that follows the Gnome releases than have an official release thats gonna be a mix of Gnome 3.4 and 3.6

I do agree with you, but as Jibicha mentioned, they would like to obtain the 'official' status for this distro as a canonical approved Ubuntu spinoff...

nothing stops us from branching it into a true gnome ubuntu...

i know i can get mine running off a server core image within 30 minutes - pure gnome.

---

### Post by smartboyhw on 2012-09-03
Well, at least I got 2.6 MB/s. That's great!

Anyway, I will also provide the SHA256 checksum of 64-bit if you do want it.

2bd3e1ca34d173031f84f0f683702834716d67042ff0e2c17a25b8289013eb3a (64-bit)
20c7237a7aa3e070bd4db6fc2d00752b9db37adb078e4f685bb96033897bbd94 (32-bit)

EDIT: Found three bugs. One causes me impossible to even USE it. Anyway let's try it out:)

---

### Post by floydsp on 2012-09-03
Well nogo for me get white & Black screen just like ubuntu 12.10. when I use nomodeset it will load (HP Touchsmart 600 with nvida 230 drivers) but then installed will not finish get to format partitions then hangs up.

floydsp

---

### Post by kuvanito on 2012-09-03
man i gave it a shot but no thanks
i like better the way i did it
good try thou,thank you for your efforts
too bad Remastersys doesn't work in 12.10 yet
i'll stick around thou ):P

---

### Post by mc4man on 2012-09-03
> **floydsp said:**
> Well nogo for me get white & Black screen just like ubuntu 12.10. when I use nomodeset it will load (HP Touchsmart 600 with nvida 230 drivers) but then installed will not finish get to format partitions then hangs up.

floydsp
If you are getting the corrupted or b&w screen that plagues some nvisdia chipsets instead of using nomodeset you could try just going to the options screen but don't set any
(shift > enter, then pick either try me or install (if the garbage screen doesn't reappear

---

### Post by Stinger on 2012-09-03
> **Cypher2 said:**
> I do agree with you, but as Jibicha mentioned, they would like to obtain the 'official' status for this distro as a canonical approved Ubuntu spinoff...

nothing stops us from branching it into a true gnome ubuntu...

i know i can get mine running off a server core image within 30 minutes - pure gnome.
Yeah I guess i'm not very good at hiding my disappointment. 
But with gnome-shell 3.5.4, Nautilus 3.4.2, Totem and Gstreamer  stuck at older version too, I really can't see the mission of "Ubuntu Gnome Remix" other than being exactly that! A mix of various Gnome components locked in version and technology because of the needs from (almighty) Unity.
( It'll certainly prove that Unity is better if that's the hidden agenda. )

Why can Kubuntu, Lubuntu and Xubuntu have their own upstream versions of their desktop environments and GNObuntu cannot ??
**It's not fair to Gnome !**
You won't be able to compare Gnome/Gnome-shell to Fedora, Mageia or Suse.

I'm marking this thread as solved, as I don't think the developers will allow a clean 3.6 version of GNObuntu.

I wish you all good luck with the "Ubuntu Gnome Remix" but it's not the clean upstream version of Gnome I was expecting it to be.
I'll try a different approach. 
Cheers !

---

### Post by kuvanito on 2012-09-03
> **Stinger said:**
> Yeah I guess i'm not very good at hiding my disappointment. 
But with gnome-shell 3.5.4, Nautilus 3.4.2, Totem and Gstreamer  stuck at older version too, I really can't see the mission of "Ubuntu Gnome Remix" other than being exactly that! A mix of various Gnome components locked in version an technology because of the needs from (almighty) Unity.
( It'll certainly prove that Unity is better if that's the hidden agenda. )

Why can Kubuntu, Lubuntu and Xubuntu have their own upstream versions of their desktop environments and GNObuntu cannot ??
**It's not fair to Gnome !**
You won't be able to compare Gnome/Gnome-shell to Fedora, Mageia or Suse.

I'm marking this thread as solved, as I don't think the developers will allow a clean 3.6 version of GNObuntu.

I wish you all good luck with the "Ubuntu Gnome Remix" but it's not the clean upstream version of Gnome I was expecting it to be.
I'll try a different approach. 
Cheers !

i so agree with you on this
this got to sux,leaving gnome behind like that
epiphany,iceweasel,abiword,what the hell is that? FF and TB or nothing
that's why i said i like it the way i did it
simply install latest ubuntu daily build and wipe out unity for good after you install Gnome Orphan and it looks as good as Gold..... :guitar:

---

### Post by floydsp on 2012-09-03
lets us know Stinger if you come up with something..best of luck

floydsp

---

### Post by smartboyhw on 2012-09-03
Stinger: You mean you don't like the current version of GNOMEbuntu that jbicha is developing? Also can anyone tell me who is the developer of the ORIGINAL Ubuntu Gnome-shell Remix???

---

### Post by kuvanito on 2012-09-03
it doesn't get any better than this and by the way i get no unity updates coming in because I AM UNITY FREE! althou I test both desktops Unity in a separated HD and Gnome in another HD.They both work good it just a matter of taste...

---

### Post by Stinger on 2012-09-03
> **smartboyhw said:**
> Stinger: You mean you don't like the current version of GNOMEbuntu that jbicha is developing? Also can anyone tell me who is the developer of the ORIGINAL Ubuntu Gnome-shell Remix???
I like the effort Jeremy is putting into the project, but I don't like the fact that "Ubuntu Gnome Remix" is using the Gnome package versions from Ubuntu and not it's own.

As said earlier on this thread, the [Ubuntu GNOME Shell Remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/") is an unofficial spin by [Jan Hoffmann]("https://launchpad.net/~jan-hoffmann")
BTW. The "Ubuntu Gnome Remix" seems to use his [livecd-script]("http://sourceforge.net/projects/ubuntu-gs-remix/files/live-script/20120427.12.04/") as base for [their own creation]("https://code.launchpad.net/~ubuntu-gnome-dev/+junk/iso-build-script").

---

### Post by smartboyhw on 2012-09-03
> **Stinger said:**
> I like the effort Jeremy is putting into the project, but I don't like the fact that "Ubuntu Gnome Remix" is using the Gnome package versions from Ubuntu and not it's own.

As said earlier on this thread, the [Ubuntu GNOME Shell Remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/") is an unofficial spin by [Jan Hoffmann]("https://launchpad.net/~jan-hoffmann")
BTW. The "Ubuntu Gnome Remix" seems to use his [livecd-script]("http://sourceforge.net/projects/ubuntu-gs-remix/files/live-script/20120427.12.04/") as base for [their own creation]("https://code.launchpad.net/~ubuntu-gnome-dev/+junk/iso-build-script").
Stinger: Do you know Jeremy's nick on IRC? Also, thanks for telling me who is the dev:)

---

### Post by Stinger on 2012-09-03
> **floydsp said:**
> lets us know Stinger if you come up with something..best of luck

floydsp
Will do so soon ;)
Maybe I have lost this fight, but I'm NOT gonna lose the entire battle 8)
Stay tuned all you faithful fans of Gnome and Ubuntu :guitar:

---

### Post by Mr.JJ on 2012-09-03
Even I am disappointed now that Jeremy replied that Gnome ubuntu will have an amalgamation of 3.4/3.6.  I was so excited initially. Now this just feels like gnome shell/applications installed on top of ubuntu. But we know that thats no where close to the vanilla gnome.  I am thinking about following the server iso and gnome install method, instead.

---

### Post by smartboyhw on 2012-09-03
Anyway if you're interested in Jeremy's project please join [https://launchpad.net/~ubuntu-gnome](https://launchpad.net/~ubuntu-gnome) :)

---

### Post by Mr.JJ on 2012-09-03
> **Stinger said:**
>  
Why can Kubuntu, Lubuntu and Xubuntu have their own upstream versions of their desktop environments and GNObuntu cannot ??


I'll try a different approach. 
Maybe I have lost this fight, but I'm NOT gonna lose the entire battle

> **Cypher2 said:**
>  nothing stops us from branching it into a true gnome ubuntu... i know i can get mine running off a server core image within 30 minutes - pure gnome.   Well, why can't we get the server install method by Cypher2 into a vanilla gnome version? That will be far better than the current version ubuntu or the ubuntu-gnome one. May be we can get help from the person behind gnome shell remix and get it released as gnome shell remix or any other name. I will try to contact him. 

Anyone in this? Cypher2, can you help us?   
> Stay tuned all you faithful fans of Gnome and UbuntuWe are, for sure!   
Don't just close this thread, just rename it. If you are trying to get the official approval somehow, that will be wonderful. Anyways keep us informed.

---

### Post by jbicha on 2012-09-03
I think most Ubuntu users who are GNOME fans want there to be a successful and popular GNOME flavor of Ubuntu.

And if we're going to ship GNOME 3.6, we might as well ship all of it, right?

On the other hand, there are huge advantages to becoming an officially [recognized Ubuntu flavor]("https://wiki.ubuntu.com/RecognizedFlavors").

[LIST]
[*]Canonical will supply the bandwidth for our images so that we don't have to force our users to use torrents.
[*]Official daily images (For 12.10, since we're unofficial we may only have as few official images as one Alpha, one Beta, and a final build.)
[*]Canonical builds the images for us, which saves a huge amount of time and effort and will end up significantly improving the quality of the images.
[*]Equal status with the other recognized flavors
[*]Far more users, as it's easier for users to use our releases and our releases are more trusted since they are coming from ubuntu.com infrastructure.
[*]More consideration for bugs that badly affect the GNOME remix (or similar GNOME remixes)
[*]I believe an official Ubuntu GNOME flavor will get more attention than UGR or the Ubuntu GNOME Shell Remix got.
[/LIST]
We will have a better, more successful product if we are a recognized flavor.

One of the rules of official flavors is that they must not use PPAs. It's hard enough to become a recognized flavor without trying to bend the rules.

One complication is that we share a significant number of packages with the flagship Ubuntu image. That means that we have to compromise with them on some issues, like what versions of specific components we can ship. Generally, the Canonical Desktop Team has good reasons for holding back on components and I could do an entire article about those decisions. We did manage to push gnome-control-center 3.4 and gnome-shell 3.4 into Ubuntu 12.04. Even though it wasn't quite perfect, it was better for us than shipping 3.2 would have been.

In fact, last cycle the stated plan was to ship 3.2 with some pieces of 3.4 let in. I feel we basically reversed that with only a few pieces of 3.2 left in. It's a give and take relationship and we're able to influence what GNOME and Ubuntu do. We have much more influence as insiders than as outsiders. The GNOME remix isn't the only flavor to be affected by Canonical decisions: the Xubuntu developers had to rescue the GTK2 indicators as Canonical dropped them from the archives. (There was coordination and discussion ahead of time, but it still was extra work for Xubuntu).

For those who want the rest of 3.6, it's very easy to install (& I believe it will be quite safe) to install the few remaining pieces from the GNOME3 PPA. Here's how to do so from the command line (GUI instructions aren't much harder):
```

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get upgrade

```The work we're doing on the GNOME Remix significantly benefits all other GNOME remixes. We're splitting Ubuntu customizations into separate packages so that it's easier to get a purer GNOME for those that want it. Any GNOME Remix can take our spin as a base and wouldn't need to make near as many changes.

If you're going to make a remixed GNOME remix that only has the GNOME3 PPA added, I don't think that's worth the effort.

---

### Post by smartboyhw on 2012-09-03
> **jbicha said:**
> I think most Ubuntu users who are GNOME fans want there to be a successful and popular GNOME flavor of Ubuntu.

And if we're going to ship GNOME 3.6, we might as well ship all of it, right?

On the other hand, there are huge advantages to becoming an officially [recognized Ubuntu flavor]("https://wiki.ubuntu.com/RecognizedFlavors").

[LIST]
[*]Canonical will supply the bandwidth for our images so that we don't have to force our users to use torrents.
[*]Official daily images (For 12.10, since we're unofficial we may only have as few official images as one Alpha, one Beta, and a final build.)
[*]Canonical builds the images for us, which saves a huge amount of time and effort and will end up significantly improving the quality of the images.
[*]Equal status with the other recognized flavors
[*]Far more users, as it's easier for users to use our releases and our releases are more trusted since they are coming from ubuntu.com infrastructure.
[*]More consideration for bugs that badly affect the GNOME remix (or similar GNOME remixes)
[*]I believe an official Ubuntu GNOME flavor will get more attention than UGR or the Ubuntu GNOME Shell Remix got.
[/LIST]
We will have a better, more successful product if we are a recognized flavor.

One of the rules of official flavors is that they must not use PPAs. It's hard enough to become a recognized flavor without trying to bend the rules.

One complication is that we share a significant number of packages with the flagship Ubuntu image. That means that we have to compromise with them on some issues, like what versions of specific components we can ship. Generally, the Canonical Desktop Team has good reasons for holding back on components and I could do an entire article about those decisions. We did manage to push gnome-control-center 3.4 and gnome-shell 3.4 into Ubuntu 12.04. Even though it wasn't quite perfect, it was better for us than shipping 3.2 would have been.

In fact, last cycle the stated plan was to ship 3.2 with some pieces of 3.4 let in. I feel we basically reversed that with only a few pieces of 3.2 left in. It's a give and take relationship and we're able to influence what GNOME and Ubuntu do. We have much more influence as insiders than as outsiders. The GNOME remix isn't the only flavor to be affected by Canonical decisions: the Xubuntu developers had to rescue the GTK2 indicators as Canonical dropped them from the archives. (There was coordination and discussion ahead of time, but it still was extra work for Xubuntu).

For those who want the rest of 3.6, it's very easy to install (& I believe it will be quite safe) to install the few remaining pieces from the GNOME3 PPA. Here's how to do so from the command line (GUI instructions aren't much harder):
```

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get upgrade

```The work we're doing on the GNOME Remix significantly benefits all other GNOME remixes. We're splitting Ubuntu customizations into separate packages so that it's easier to get a purer GNOME for those that want it. Any GNOME Remix can take our spin as a base and wouldn't need to make near as many changes.

If you're going to make a remixed GNOME remix that only has the GNOME3 PPA added, I don't think that's worth the effort.

I absolutely agree. Just install the whole thing yourself. It isn't a problem of having only part of 3.6.

---

### Post by cortman on 2012-09-03
What can I do to contribute to this project?
I'm a Gnome shell fan and would love to see this become a successful official flavor.

---

### Post by Stinger on 2012-09-03
> **jbicha said:**
> I think most Ubuntu users who are GNOME fans want there to be a successful and popular GNOME flavor of Ubuntu.

And if we're going to ship GNOME 3.6, we might as well ship all of it, right?

On the other hand, there are huge advantages to becoming an officially [recognized Ubuntu flavor]("https://wiki.ubuntu.com/RecognizedFlavors").
I see your point, thank's for taking time to explain.
I hope you don't mind my previously frustations [-o< 

What about an agreement ?
You go ahead with the official GNObuntu and we get all the goodies to make a clean upstream Gnome 3.6 in the 
ppa:gnome3-team/gnome3 / ppa:ricotz/testing
That'll be: 
Gnome-Shell, Nautilus, Gstreamer and Totem/Videos.
Don't know if there is more missing on my list ?

Would that be agreeable To you, [the developers]("https://launchpad.net/~ubuntu-gnome/+mugshots") ? ;)

---

### Post by cmcanulty on 2012-09-03
will we be able to upgrade to gnomebuntu from classic? I ask because once I had gnome-shell remix and it wasn't upgradeable I think it is now but not sure

---

### Post by jbicha on 2012-09-03
> **cmcanulty said:**
> will we be able to upgrade to gnomebuntu from classic? I ask because once I had gnome-shell remix and it wasn't upgradeable I think it is now but not sure

That is not supported. Just like trying to "upgrade" from Ubuntu to Kubuntu isn't supported.

---

### Post by Mr.JJ on 2012-09-03
Jeremy, 
I understand your stand on this. Official recognition is really a good starting point. 

> **jbicha said:**
> We're splitting Ubuntu customizations into separate packages so that it's easier to get a purer GNOME for those that want it. 
  
This is great news! This was one of the major frustrations from a gnome user perspective (apart from keeping those unnecessary unity packages). The changes that ubuntu made to the gnome applications were spoiling the gnome experience. 

Why don't we also remove those customisations by default, if we are splitting it into different packages?

> **jbicha said:**
> One of the rules of official flavors is that they must not use PPAs.  

But then again, we are not really like 'other flavours'. We are sharing the same DE and as you said, too many packages with the official version. At the same time, both projects are moving in entirely different directions. So, if ubuntu has to have a vanilla gnome experience, there should be lot of adjustments to be made.  Splitting the ubuntu changes etc. into different packages is a good start in this direction. In the long run, without those adjustments and a vanilla gnome  experience, this spin-off has no relevance from a user stand point. 

But I guess, we need more time and effort/discussions etc. for that to happen. Let's see how it goes; I am hopeful.

---

### Post by jerrylamos on 2012-09-03
Live session booted O.K. as far as I can tell, I'm not familiar with the remix.

I've a number of partitions quantal unity, lxde, gnome-shell/gdm, also precise for recovery, .... on a Aspire1 netbook.  All running more or less like Alpha code does.

Manual install remix to a selected partition, as soon as I select EXT4 then Ubiquity crashes.  Three times with as much variation as I could think of to get there.  EXT3 same crash.  I can't even get to select "format" before Ubiquity crashes.

what about update/upgrade to the live session?  Oops, no way I could get wireless WPA with the intel N-1000 to connect.  Apport won't report a bug unless internet is connected.

I joined the gnome remix team, at least the mailing list.  Can't do much testing.  Will try again in a few days.

Jerry

BTW, I'm not a purist.  My preferred desktop on Quantal done by full install of quantal then apt-get install lxde on top.  Still have the ubuntu applications & tools I use.  I use 2D on precise.  Yes my 3 test systems will run Unity then I switch to another desktop ASAP.

---

### Post by VinDSL on 2012-09-03
Whoopsie!

n/m

---

### Post by julo42 on 2012-09-04
> **jbicha said:**
> One complication is that we share a significant number of packages with the flagship Ubuntu image. That means that we have to compromise with them on some issues, like what versions of specific components we can ship. Generally, the Canonical Desktop Team has good reasons for holding back on components and I could do an entire article about those decisions. We did manage to push gnome-control-center 3.4 and gnome-shell 3.4 into Ubuntu 12.04. Even though it wasn't quite perfect, it was better for us than shipping 3.2 would have been.

Just one question about this issue: isn't it possible to have both a nautilus3.4 package and a nautilus3.6 package in the repository, and maybe have a nautilus dummy package pointing to the nautilus3.4 one, just like for python versions? This way, ubuntu-gnome-desktop could depend on nautilus3.6 while unity depends on nautilus (hence nautilus3.4). And the same could be done for totem I guess.

Is it too much work? Or simply undoable for other reasons?

---

### Post by smartboyhw on 2012-09-04
> **cortman said:**
> What can I do to contribute to this project?
I'm a Gnome shell fan and would love to see this become a successful official flavor.

Hi cortman.

Please first join the Launchpad team on [https://launchpad.net/~ubuntu-gnome](https://launchpad.net/~ubuntu-gnome). 
Then
1. Report bugs in [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes)
2. You can try to submit fixes for bugs. Go to [https://launchpad.net/~ubuntu-gnome-dev](https://launchpad.net/~ubuntu-gnome-dev)
and work on it, you might even get in the team!!!
[]("https://launchpad.net/~ubuntu-gnome-dev")3. We DO need some minimal art:) Help us!!!
4. Contribute in anyway you think it is necessary:)

Regards,
smartboyhw

---

### Post by Stinger on 2012-09-04
> **smartboyhw said:**
> 3. We DO need some minimal art:) Help us!!!
As said before on this thread.
> **Stinger said:**
> 
And [Satyajit Sahoo]("https://launchpad.net/~satyajit-happy") is on hold, this could mean some serious artwork :D

Why don't you guy's let [Satyajit Sahoo]("https://launchpad.net/~satyajit-happy") inside, it's so obvious ?
As you can se he's on the [waiting list here]("https://launchpad.net/~ubuntu-gnome-dev")
Look at [his page on deviantART]("http://satya164.deviantart.com/")
I'm sure he can do the job ;)

---

### Post by smartboyhw on 2012-09-04
> **Stinger said:**
> As said before on this thread.

Why don't you guy's let [Satyajit Sahoo]("https://launchpad.net/~satyajit-happy") inside, it's so obvious ?
As you can se he's on the [waiting list here]("https://launchpad.net/~ubuntu-gnome-dev")
Look at [his page on deviantART]("http://satya164.deviantart.com/")
I'm sure he can do the job ;)
For the first part, I just copied it from the PM from jbicha.

For the second part, well, ask jbicha:)

---

### Post by jerrylamos on 2012-09-04
> **cmcanulty said:**
> will we be able to upgrade to gnomebuntu from classic? I ask because once I had gnome-shell remix and it wasn't upgradeable I think it is now but not sure

Well, this is a test forum for the latest development usually has oops and breaks.  So we run multiple partitions and install frequently - everything's backed up.

Testing purposes we do want to see how install will go, and it is a ripe field for bugs.  Right now with gnome remix on this netbook Ubiquity install crashes when I select the install partition.

Past experience and many posts people will do an upgrade, especially at Alpha Beta time, may crash and they are stuck without a back up.  I've tried upgrade to see if it works - sometimes - and always takes more disk space than a fresh install.

Now I learn a lot of linux testing new unstable development code.

---

### Post by Cypher2 on 2012-09-04
In regards to the 'pure gnome experience' discussion, I do have to agree that it would be kind of irrelevant to provide all the effort, if in the long run, we do not end up with the real thing. KDE, LXDE, XFCE all beneficiate of such a privilege, which was most probably attributed later on in the dev cycle, but we must not let this project become a half-baked attempt at what a lot of fervent users were waiting for.

Can we argue with Canonical on how to fork the packaging tree for gnome and have the true default 'vanilla' be built and hosted for this? If the aim is to become an official spin-off, the attempt is worthwhile IMHO.

Who's with me on this?

Great work on the alpha btw! :)

---

### Post by RavisPohan on 2012-09-04
> **Cypher2 said:**
> 
Who's with me on this?

Great work on the alpha btw! :)

Yeah, seconded. Said alpha is currently working without a hitch on one of my testing partitions.

---

### Post by Stinger on 2012-09-04
> **Cypher2 said:**
> In regards to the 'pure gnome experience' discussion, I do have to agree that it would be kind of irrelevant to provide all the effort, if in the long run, we do not end up with the real thing. KDE, LXDE, XFCE all beneficiate of such a privilege, which was most probably attributed later on in the dev cycle, but we must not let this project become a half-baked attempt at what a lot of fervent users were waiting for.

Can we argue with Canonical on how to fork the packaging tree for gnome and have the true default 'vanilla' be built and hosted for this? If the aim is to become an official spin-off, the attempt is worthwhile IMHO.

Who's with me on this?

Great work on the alpha btw! :)
In general I like your idea, I said it myself earlier, and as a long term solution I'm with you, but Jeremy has a strong point going for the official privileges, and that's the nr.1 goal for now (yours could be second).

I have thought about the second best solution to this dilemma.
I think that would be to have a "stable ppa" for the [&#8220;Ubuntu GNOME&#8221; team ]("https://launchpad.net/~ubuntu-gnome"), that would include the latest stable version of Gnome, the missing Gnome-parts from Ubuntu to make stable Gnome 3.6, 3.8..... maintained by the "Ubuntu Gnome" team, or use the &#8220;GNOME3 Team&#8221; ppa if that's better.
This ppa should be available in package-kit / software-center / synaptic, but not be enabled by default.

It would give the user the possibility to choose between the official and the upstream release and we wouldn't have to rely on any testing ppa's for an upstream Gnome experience. :D

---

### Post by Cypher2 on 2012-09-04
Could be an idea.. for now. But still, long term would still mean getting UbuntuGSR its own repo with upstream configured packs to get the real deal. it's a must.

How could I contribute to changing some of the more visual features of the distro to unify certain things and make it more pleasurable, and maybe even inspire the canonical team to do so themselves for Ubuntu?

---

### Post by Stinger on 2012-09-05
> **Cypher2 said:**
> 
How could I contribute to changing some of the more visual features of the distro to unify certain things and make it more pleasurable, and maybe even inspire the canonical team to do so themselves for Ubuntu?

Signing up [here]("https://launchpad.net/~ubuntu-gnome") or [here]("https://launchpad.net/~ubuntu-gnome-dev") ?

---

### Post by smartboyhw on 2012-09-05
Er guys: Bad news for those who want the original Ubuntu GNOME Shell Remix.

This is a reply from Jan Hoffman, the developer of Ubuntu GNOME Shell Remix, after I sent an email asking to help her in the Remix.

```
Hi Howard!

Thank you for your offer to help.As there will be an official Ubuntu GNOME edition from 12.10 on, you should probably help with that project: [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes)
  Development of Ubuntu GNOME Shell Remix as it is now will stop in the near future.


Regards,
Jan

```

Er so....

---

### Post by jbicha on 2012-09-05
> **Cypher2 said:**
> 
How could I contribute to changing some of the more visual features of the distro to unify certain things and make it more pleasurable, and maybe even inspire the canonical team to do so themselves for Ubuntu?

I think we should stick with the default GNOME wallpaper or something very close to it (Fedora 15's variation on it wasn't bad). I would like to see a plymouth theme that matches. We can also customize the grub background and the isolinux background (what you see when booting the live image from DVD or USB).

I think we'll distribute it as part of the  ubuntu-gnome-settings source package. You can look at what the other  Ubuntu derivatives have done to get an idea of how that works. Once you've got some stuff to submit, you can open a bug report and we'll take a look at it. Or we can discuss it on the mailing list.

---

### Post by julo42 on 2012-09-05
> **jbicha said:**
> I think we should stick with the default GNOME wallpaper or something very close to it (Fedora 15's variation on it wasn't bad). I would like to see a plymouth theme that matches. We can also customize the grub background and the isolinux background (what you see when booting the live image from DVD or USB).

I think we'll distribute it as part of the  ubuntu-gnome-settings source package. You can look at what the other  Ubuntu derivatives have done to get an idea of how that works. Once you've got some stuff to submit, you can open a bug report and we'll take a look at it. Or we can discuss it on the mailing list.

I agree too: GNOME designers are doing a great work at making a nice-looking desktop. There is no reason to change anything inside the desktop and GDM. The only parts that do need changing, however, are grub and plymouth. But, even for them, the artwork should be based on upstream artwork.

---

### Post by sml on 2012-09-05
how can we use the gnome extensions?
[https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by cmcanulty on 2012-09-05
when I go to the gnome extensions all are grayed out is this a bug I am running classic no effects

---

### Post by sgage on 2012-09-05
> **cmcanulty said:**
> when I go to the gnome extensions all are grayed out is this a bug I am running classic no effects

Gnome Classic doesn't use the Gnome Shell Extensions - they are for Gnome Shell.

Even if you were running Gnome Shell in 12.10, you would find most of the extensions grayed out, because they haven't been updated to work with the newer version of GS in 12.10.

Remember, 12.10 is in heavy development...

---

### Post by mc4man on 2012-09-05
> **sml said:**
> how can we use the gnome extensions?
[https://extensions.gnome.org/](https://extensions.gnome.org/)
see here
[http://ubuntuforums.org/showthread.php?t=2050183](http://ubuntuforums.org/showthread.php?t=2050183)

Is possible that many of the ext. would work but the website seems to reject a 12.10 or 12.10+ gnome-session out of hand.

Here I wanted to try the 'Quicklists" ext. so installed it on 12.04, copied over, edited the ~/local/share/gnome-shell/extensions/metadata.json for version, enabled in tweak & it works fine.

Obviously doing like this represents some risk of incompatible ext. so keep fixing that possibility in mind if pursuing, otherwise wait for website to square up or look elsewhere with care

---

### Post by Stinger on 2012-09-05
I don't think this is the right thread to discuss the extensions.
As mc4man already pointed out, this thread would be more appropriate.

 [Cannot install GNOME extensions]("http://ubuntuforums.org/showthread.php?t=2050183")

Extensions will work with the _official Gnome releases_ from version 3.2

Extensions are not guarantied to work between official releases, but this may change from Gnome 3.8

[Gnome 3.8 features: Automatic Extension Updates]("http://worldofgnome.org/gnome-3-8-features-automatic-extension-updates/")

Please post your extension trouble at the other thread. :cool:

---

### Post by cshin9 on 2012-09-12
> **Stinger said:**
> I'm so glad to hear that we are sticking to upstream Nautilus. :D
Thank's a lot for answering my question.

The naming thing is difficult, **Gubuntu** is ruled out I think, because of googles Goobuntu.
**GNObuntu** maybe ? But some say it sound a little like "Gee no buntu" they don't like the negation.
**Gnubuntu** is taken and would indicate that it follows the free Software Foundation guidelines.
**Gnomebuntu** is actually not bad maybe we should stick with that one ?
Cheers

> **BigSilly said:**
> With respect, why the need to avoid the name **Gubuntu**? So what if Google uses a similar sounding name? I mean, they don't own the 'buntu name, and to me nothing fits the project better than Gubuntu. It makes sense alongside Kubuntu, Xubuntu and Lubuntu.

I just don't get why the need to avoid the most obvious name. What's Google got to do with things? Gubuntu is the most obvious choice, and to me the alternatives don't really suit.

> **hugmenot said:**
> Also, call it Gubuntu. On the internet it doesn’t matter if it is a homophone, only spelling matters. And Goobuntu is a name internal  to Google only anyhow.

> **manliodp said:**
> I know that the name is not important but i think GNOBUNTU is a lot better than GNOMEBUNTU..i thought GNOBUNTU was the chosen name, I really hope you think again about it :)

Anyway I would really say THANK YOU for your effort, it will be a great release!

> **checoimg said:**
> WHat do you guys think about "Gnubuntu" ?

> **jerrylamos said:**
> Sure.  ubuntu, lubuntu, xubuntu, kubuntu, gnubuntu (list order your option)

As I understand from this forum, the ubuntu management mantra is "unity everywhere", pc's, ipads, ipods, smartphones, ...

Well, maybe when Nook has 2 gHz dual processors with 4G memory and a very fast SSD it might handle the then further developed (I presume more features are coming) Unity/Compiz.  My opinion.  I don't intend to cause any problem with the ubuntu development forum COC.

The market will decide.  Meanwhile I'm trying a few different desktops, which works as long as ubuntu is compatible with debian.

> **vasa1 said:**
> I think they've decided on Gnomebuntu? Would be mods consider renaming the thread if that is correct?

> **Stinger said:**
> Hey all Ubuntu guys and girls ( really like the last ones ;) )

I've been spreading the word, hope the dev's don't mind. I think all Gnome fans need to know about GNObuntu. 
This has resulted in a few nice articles :D
Look here:

**[GNOMEbuntu is set to arrive in October, 18!]("http://worldofgnome.org/gnomebuntu-is-set-to-arrive-in-october-18/")**

**[GNOMEbuntu Will Be Available This October]("http://www.muktware.com/4247/gnomebuntu-will-be-available-october")**

**[GNOME-flavoured Ubuntu Spin Coming October 18th]("http://www.omgubuntu.co.uk/2012/08/gnome-flavoured-ubuntu-spin-coming-october-18th")**

Especially like the one from [Muktware]("http://www.muktware.com/"), very informative !

More good news, another developer has joined the team,  [Robert Ancell]("https://launchpad.net/~robert-ancell"), thanks for joining the team.
And [Satyajit Sahoo]("https://launchpad.net/~satyajit-happy") is on hold, this could mean some serious artwork :D

And we are starting to get some code, look here:
[https://code.launchpad.net/~ubuntu-gnome-dev](https://code.launchpad.net/~ubuntu-gnome-dev)

A new suggestion for a name could be **uGuntu** ?
Suggested by frank_O from the [Gnome board]("https://mail.gnome.org/archives/marketing-list/2012-August/msg00029.html")

Cheers !

Aesthetically, I'd prefer Gubuntu > Gnubuntu > GNUbuntu > Gnobuntu > GNObuntu > Ubuntu GNOME > the rest. Realistically, Gubuntu is out because of [Goobuntu]("https://en.wikipedia.org/wiki/Goobuntu"). (Pronunciation does in fact matter.) Gnubuntu and GNUbuntu are also out because it implies some kind of direct hierarchy with the [GNU Project]("https://en.wikipedia.org/wiki/GNU_Project") (and [Richard Stallman]("https://en.wikipedia.org/wiki/Richard_Stallman")). So I'd go with Gnobuntu. By the way, the homophonous Nubuntu (of Gnubuntu) is already taken by [nUbuntu]("https://en.wikipedia.org/wiki/NUbuntu").

> **jbicha said:**
> That is not supported. Just like trying to "upgrade" from Ubuntu to Kubuntu isn't supported.

Isn't there a "[kubuntu-desktop]("http://packages.ubuntu.com/precise/kubuntu-desktop")" package that you could install over Ubuntu? That's how I got Kubuntu on Wubi.

---

### Post by smartboyhw on 2012-09-13
> **cshin9 said:**
> Aesthetically, I'd prefer Gubuntu > Gnubuntu > GNUbuntu > Gnobuntu > GNObuntu > Ubuntu GNOME > the rest. Realistically, Gubuntu is out because of [Goobuntu]("https://en.wikipedia.org/wiki/Goobuntu"). (Pronunciation does in fact matter.) Gnubuntu and GNUbuntu are also out because it implies some kind of direct hierarchy with the [GNU Project]("https://en.wikipedia.org/wiki/GNU_Project") (and [Richard Stallman]("https://en.wikipedia.org/wiki/Richard_Stallman")). So I'd go with Gnobuntu. By the way, the homophonous Nubuntu (of Gnubuntu) is already taken by [nUbuntu]("https://en.wikipedia.org/wiki/NUbuntu").



Isn't there a "[kubuntu-desktop]("http://packages.ubuntu.com/precise/kubuntu-desktop")" package that you could install over Ubuntu? That's how I got Kubuntu on Wubi.

Next time just don't multi-quote too many posts:)

I think jbicha is still trying to settle down the name issue:)

jbicha: He's correct, there is a "kubuntu-desktop" package in kubuntu, there's "ubuntustudio-desktop" package in Ubuntu Studio (we are going to make a -all package). So er it IS possible to upgrade:)

---

### Post by kansasnoob on 2012-09-13
> jbicha: He's correct, there is a "kubuntu-desktop" package in kubuntu, there's "ubuntustudio-desktop" package in Ubuntu Studio (we are going to make a -all package). So er it IS possible to upgrade

You'll notice that jbicha used the term "supported" rather than "possible".

I've helped work on some DE conversions like those shown in the Playing Around section here:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

But possible and supported mean two very different things :D

---

### Post by smartboyhw on 2012-09-13
> **kansasnoob said:**
> You'll notice that jbicha used the term "supported" rather than "possible".

I've helped work on some DE conversions like those shown in the Playing Around section here:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

But possible and supported mean two very different things :D
Challenge: Supported means it has the latest packages. And I do think Kubuntu supports it. At least in Ubuntu Studio we do support it using a wiki page (needs updating)

---

### Post by kansasnoob on 2012-09-13
> Aesthetically, I'd prefer Gubuntu > Gnubuntu > GNUbuntu > Gnobuntu > GNObuntu > Ubuntu GNOME > the rest. Realistically, Gubuntu is out because of Goobuntu. (**Pronunciation does in fact matter**.) Gnubuntu and GNUbuntu are also out because it implies some kind of direct hierarchy with the GNU Project (and Richard Stallman). So I'd go with Gnobuntu. By the way, the homophonous Nubuntu (of Gnubuntu) is already taken by nUbuntu.

I guess a lot of it depends on how one pronounces Ubuntu itself. I pronounce it "uh-boon-too", and each new flavor is simply the addition of the sound of the letter, like for Lubuntu;

el-uh-boon-too

or for Kubuntu

kay-uh-boon-too

etc :D

---

### Post by kansasnoob on 2012-09-13
> **smartboyhw said:**
> Challenge: **Supported means it has the latest packages**. And I do think Kubuntu supports it. At least in Ubuntu Studio we do support it using a wiki page (needs updating)

Under that scenario are 10.04 and 11.04 still supported? There are certainly newer packages available ;)

Supported can undeniably mean different things in different contexts, I was just applying my best guess to the context Jeremy intended :)

---

### Post by smartboyhw on 2012-09-13
> **kansasnoob said:**
> Under that scenario are 10.04 and 11.04 still supported? There are certainly newer packages available ;)

Supported can undeniably mean different things in different contexts, I was just applying my best guess to the context Jeremy intended :)
Well 11.04 stopped technical support, and 10.04 support will end soon. It is a complele stop of support, not just the upgrade.

Anyway news: The autologin bug has been fixed and now the daily build I just compiled is working greatly:)

---

### Post by jbicha on 2012-09-13
> **cshin9 said:**
> Aesthetically, I'd prefer Gubuntu > Gnubuntu > GNUbuntu > Gnobuntu > GNObuntu > Ubuntu GNOME > the rest. Realistically, Gubuntu is out because of [Goobuntu]("https://en.wikipedia.org/wiki/Goobuntu"). (Pronunciation does in fact matter.) Gnubuntu and GNUbuntu are also out because it implies some kind of direct hierarchy with the [GNU Project]("https://en.wikipedia.org/wiki/GNU_Project") (and [Richard Stallman]("https://en.wikipedia.org/wiki/Richard_Stallman")). So I'd go with Gnobuntu. By the way, the homophonous Nubuntu (of Gnubuntu) is already taken by [nUbuntu]("https://en.wikipedia.org/wiki/NUbuntu").
Except that the GNOME Foundation Board doesn't want us to combine their trademark (GNOME) with another word to make a compound word name.

> **cshin9 said:**
> 
Isn't there a "[kubuntu-desktop]("http://packages.ubuntu.com/precise/kubuntu-desktop")" package that you could install over Ubuntu? That's how I got Kubuntu on Wubi.

Sure, if you have Ubuntu 12.10, you can install ubuntu-gnome-desktop and get GNOME Shell in addition to your Unity. I thought the question was asked whether you could take a 12.04 install and use the Ubuntu GNOME image to "upgrade" that to Ubuntu GNOME 12.10. That will not be supported.

---

### Post by mcellius on 2012-09-13
... and UbuntuG just sounds ugly.  (Or maybe even a little cute.)

---

### Post by jerrylamos on 2012-09-14
> **jbicha said:**
> Except that the GNOME Foundation Board doesn't want us to combine their trademark (GNOME) with another word to make a compound word name. Sure, if you have Ubuntu 12.10, you can install ubuntu-gbuntu GNOME image to "upgrade" that to Ubuntu GNOME 12.10.
To follow through with trademarks, doesn't that make it:
GNU-Ubuntu-Gnome 12.10
following through from Stallman and GNOME?  At least Linus doesn't seem to be picky that I've seen.

---

### Post by smartboyhw on 2012-09-15
Hmm.....GNOMbuntu is better for me. Not GNOME, but GNOM. Makes more sense:)

---

### Post by sgage on 2012-09-15
> **smartboyhw said:**
> Hmm.....GNOMbuntu is better for me. Not GNOME, but GNOM. Makes more sense:)

Whatever! Just so long as we agree on something, so we'll all know what we're talking about. Something quick to write, too. :KS

Gnom- or Gno- buntu seem sensible to me...

---

### Post by hugmenot on 2012-09-15
Jeremy, do you have any idea why GDM refuses to let me log in now?
It used to work with gdm but now I always get "Authentication failure". Lightdm still works for login, but then I run into problems with the screen lock.

The only relevant log output I found is this:

```

cat :0-slave.log 
gdm-launch-environment][2381]: AccountsService-WARNING: SetLanguage call failed: GDBus.Error:org.freedesktop.Accounts.Error.Failed: not access to HOME yet so language not saved
gdm-launch-environment][2381]: pam_unix(gdm-launch-environment:session): session opened for user gdm by (uid=0)
gdm-launch-environment][2381]: pam_ck_connector(gdm-launch-environment:session): nox11 mode, ignoring PAM_TTY :0
gdm-password][2487]: pam_succeed_if(gdm-password:auth): requirement "user ingroup nopasswdlogin" not met by user "hugme"
gdm-password][2487]: pam_unix(gdm-password:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=hugme
gdm-password][2501]: pam_succeed_if(gdm-password:auth): requirement "user ingroup nopasswdlogin" not met by user "hugme"

```

Do I have to install any other packages? Is this PAM related?

---

### Post by MikeCyber on 2012-09-17
If Ubuntu would let users select a/many desktop at install alike FreeBSD, openSuse etc. we wouldn't need such silly splits. 
They could even go beyond and let users select configurations for gamers etc. as probably gnome3 without compiz would be fastest?

---

### Post by kansasnoob on 2012-09-17
> **jbicha said:**
> Except that the GNOME Foundation Board doesn't want us to combine their trademark (GNOME) with another word to make a compound word name.



Sure, if you have Ubuntu 12.10, you can install ubuntu-gnome-desktop and get GNOME Shell in addition to your Unity. I thought the question was asked whether you could take a 12.04 install and use the Ubuntu GNOME image to "upgrade" that to Ubuntu GNOME 12.10. That will not be supported.

IMHO Gubuntu makes the most sense.

KDE + Ubuntu = Kubuntu
LXDE + Ubuntu = Lubuntu
Xfce + Ubuntu = Xubuntu

If we truly want to become an official Ubuntu flavor I suggest following that pattern ;)

---

### Post by MikeCyber on 2012-09-17
which was rejected because of resemblance to:
[http://en.wikipedia.org/wiki/Goobuntu](http://en.wikipedia.org/wiki/Goobuntu)

---

### Post by Stinger on 2012-09-17
What do you all think of:

**uGuntu ?**

[Suggested by frank on the Gnome board mailing list]("https://mail.gnome.org/archives/marketing-list/2012-August/msg00029.html")
( the one in the middle )

---

### Post by smartboyhw on 2012-09-17
> **Stinger said:**
> What do you all think of:

**uGuntu ?**

[Suggested by frank on the Gnome board mailing list]("https://mail.gnome.org/archives/marketing-list/2012-August/msg00029.html")
( the one in the middle )
Objection due to that All have a *buntu. uGuntu doesn't make sense then:)

---

### Post by kansasnoob on 2012-09-17
> **MikeCyber said:**
> which was rejected because of resemblance to:
[http://en.wikipedia.org/wiki/Goobuntu](http://en.wikipedia.org/wiki/Goobuntu)

But the question is, "has Canonical rejected it"?

I did some testing for UGR before it's early demise:

[http://ugr.teampr0xy.net/home-1](http://ugr.teampr0xy.net/home-1)

But I think it was mostly just a couple of very smart teens that didn't realize what they were getting into :)

Regardless of distro name I have a lot of faith in Jeremy Bicha. He's proven himself to be consistent, and he works very well with others :guitar:

---

### Post by Stinger on 2012-09-17
> **kansasnoob said:**
> 
Regardless of distro name I have a lot of faith in Jeremy Bicha. He's proven himself to be consistent, and he works very well with others
Hear hear ! the man deserves a lot of credit =D> ( coping with me can be a task in itself :redface: ) and so do all others who contribute to the project.

---

### Post by smartboyhw on 2012-09-17
> **kansasnoob said:**
> But the question is, "has Canonical rejected it"?

I did some testing for UGR before it's early demise:

[http://ugr.teampr0xy.net/home-1](http://ugr.teampr0xy.net/home-1)

But I think it was mostly just a couple of very smart teens that didn't realize what they were getting into :)

Regardless of distro name I have a lot of faith in Jeremy Bicha. He's proven himself to be consistent, and he works very well with others :guitar:
Yay... Jeremy Bicha has a lot of faith and I do think he is a good guy:)

---

### Post by Mr.JJ on 2012-09-17
> **kansasnoob said:**
>  I think it was just a couple of very smart teens that didn't realize what they were getting into  

 Exactly my thoughts back then. Frsustrated, I moved on to Arch and then to Fedora. Fedora achieved the best gnome3 implementation (in any distro) in the last cycle. 
 
 I presume this release is meant as an alpha release and we started late in the cycle. So, I am happy with the progress we are making, but still a long way to go. Jeremy, sure, needs appreciation; happy hacking!

---

### Post by cmcanulty on 2012-09-17
I think I am a bit confused about the new gnomewhatever distro. Will it be mainly for pure gnome3 or for fallback. I have fallback installed now and like that it has 5 years support. But apparently to go to the new gnome distro I will have to reinstall or can I keep using it for the 5 years.

---

### Post by jbicha on 2012-09-17
> **cmcanulty said:**
> I think I am a bit confused about the new gnomewhatever distro. Will it be mainly for pure gnome3 or for fallback. I have fallback installed now and like that it has 5 years support. But apparently to go to the new gnome distro I will have to reinstall or can I keep using it for the 5 years.

If you like GNOME Classic (gnome-panel), you're welcome to keep using Ubuntu 12.04 LTS.

The new Ubuntu GNOME Remix will only be available on Ubuntu 12.10 and later. For now, we're including GNOME Classic & GNOME Shell. Shell is the default and is our main focus. It's too early to tell whether we'll continue to include GNOME Classic  by default in future releases. There is absolutely no reason why it would be dropped from the Ubuntu repositories any time soon though.

---

### Post by Stinger on 2012-09-20
Quick update.

Everaldo Canuto is doing some work that may result in a [new plymouth theme for Ubuntu Gnome remix]("https://launchpad.net/~ecanuto/+archive/dev/+packages"), let's hope it makes it into the beta release so we can test it.

Really good news:
From this article [Gnome 3.8 Release Schedule [Draft]]("http://worldofgnome.org/gnome-3-8-release-schedule-draft/"), Bottom of the page.
> The most highly anticipated feature in 3.8 will be the support of Wayland. Even if the Distros don’t run it by default, Wayland will exist in repositories of the most distros and GTK 3.8 will be compiled with Wayland flags.
Can't wait to test Wayland :-D

---

### Post by MikeCyber on 2012-09-20
Gnobuntu sure, no beta yet? But Wayland, why should that be better?

---

### Post by Stinger on 2012-09-20
> **MikeCyber said:**
> Gnobuntu sure, no beta yet? But Wayland, why should that be better?
No the beta is scheduled for the same week as Ubuntu 12.10 Beta 2 (September 27). you can follow it here: [UbuntuGNOME/ReleaseNotes]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes?action=show")

Wayland is to complex for me to explain in a few words but her you can see the [Wayland Architecture]("http://wayland.freedesktop.org/architecture.html") 
And I like the  fact that the developer Kristian Høgsberg is a Danish guy like me.. naah just kidding you ;)

---

### Post by Stinger on 2012-09-21
Please have a look at this article:
[Gnome Shell 3.6 Preview]("http://worldofgnome.org/gnome-shell-3-6-preview/") the demo video in paticular, if your bandwith allows it I would recommend to watch it in 720p ad full-screen to enhance the experience.

A preview of what Ubuntu Gnome Remix is about to become.

---

### Post by cmcanulty on 2012-09-21
I just wish they would get off all the black with white text. I find it very hard to read. I have explored lots of themes but they all seem to have the black bars and white text. I may have missed one but I am a senior and need something easy to see.The features look very neat though.

---

### Post by Stinger on 2012-09-21
> **cmcanulty said:**
> I just wish they would get off all the black with white text. I find it very hard to read. I have explored lots of themes but they all seem to have the black bars and white text. I may have missed one but I am a senior and need something easy to see.The features look very neat though.
If I find an interesting theme I'll let you know.

---

### Post by MikeCyber on 2012-09-22
Yes, I'll look for another theme as well as I don't like orange. I don't have black with white text...did you change some settings?
Seems it will be named: Gnomebuntu?
[http://gnomebuntu.org/](http://gnomebuntu.org/)

---

### Post by BigSilly on 2012-09-22
> **MikeCyber said:**
> Yes, I'll look for another theme as well as I don't like orange. I don't have black with white text...did you change some settings?
Seems it will be named: Gnomebuntu?
[http://gnomebuntu.org/](http://gnomebuntu.org/)

I thought Gnome themselves had put the kibosh on that name as they didn't want their name lost in Ubuntu's branding?

---

### Post by PaulW2U on 2012-09-22
> **BigSilly said:**
> I thought Gnome themselves had put the kibosh on that name as they didn't want their name lost in Ubuntu's branding?

I've read that here too.

A quick "whois" of various possible domain names that include combinations of "Gnome" and "Ubuntu" shows that many have already been registered with .com, .net and .org extensions. I think every one that I found has been registered to either stop their use or in the hope that the domain name might one day become valuable. I haven't found anything that looks in any way official yet.

---

### Post by cmcanulty on 2012-09-22
I can;t find a setting for that and I have tried everything I could find on google and forums everything changes except the menus

---

### Post by Stinger on 2012-09-28
Hey
We got a really nice review from worldofgnome.org :

**[Ubuntu Gnome beta is out ..and is ready for (ab)use!]("http://worldofgnome.org/ubuntu-gnome-beta-is-out-and-is-ready-for-abuse/")** :D

Please watch the promoting video, it's absolutely great \\:D/
Thanks to Alex.

Have to find out where he got the Gnome-boxes from.

---

### Post by jozmak on 2012-09-28
I am unable to install beta. I downloaded the iso 3 times already and I always get the same error. The iso starts as normal and soon after it puts me on busybox.
With alfa 2 there was no problem.

---

### Post by jbicha on 2012-09-28
> **jozmak said:**
> I am unable to install beta. I downloaded the iso 3 times already and I always get the same error. The iso starts as normal and soon after it puts me on busybox.
With alfa 2 there was no problem.

Yours is the first I've heard of problems with the build. Are you using the 32-bit or 64-bit version? Did you try comparing the [MD5SUMS]("http://bicha.net/ubuntu-gnome-remix/MD5SUMS")? Are you having the same problem with the Ubuntu Beta 2?

---

### Post by jozmak on 2012-09-28
> **jbicha said:**
> Yours is the first I've heard of problems with the build. Are you using the 32-bit or 64-bit version? Did you try comparing the [MD5SUMS]("http://bicha.net/ubuntu-gnome-remix/MD5SUMS")? Are you having the same problem with the Ubuntu Beta 2?

I'm using 64 bit. I couldn't check the md5sum because I didn't find the md5sum anywhere on the download page. But now that you posted it I checked and I see it didn't match. 

I've downloaded the iso from this site: [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta)

It doesn't say it is beta 1 or beta 2.

Right now, I am downloading it again to see what happens. I report back when finished installing. 

Thanks.

---

### Post by cariboo on 2012-09-28
> **jozmak said:**
> I'm using 64 bit. I couldn't check the md5sum because I didn't find the md5sum anywhere on the download page. But now that you posted it I checked and I see it didn't match. 

I've downloaded the iso from this site: [https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta)

It doesn't say it is beta 1 or beta 2.

Right now, I am downloading it again to see what happens. I report back when finished installing. 

Thanks.

How are you downloading it? What are you using to create the image on your usb drive?

I just downloaded the iso via the torrent, and aside from having to create the usb drive in Precise because the Startup Disk Creator crashed on Quantal, It booted and installed with only the corrupted video problem that most of us seem to be suffering from until the next kernel update.

---

### Post by jbicha on 2012-09-28
Because we were so late this cycle with the first build only a few days before Beta 1, I called that first build Alpha. There were enough installer bugs that I also released an Alpha 2. The current release is Beta but it was released at the same time as Beta 2. Sorry for the confusion.

---

### Post by jozmak on 2012-09-28
After spending a whole afternoon trying to install gnubuntu this is the summary of my efforts.

I download the 64 bit version and this time the md5sum matched. 

First, I used unetbootin burning the iso, because unetbootin works with ubuntu too. After reboot, the purple splash comes up then a few seconds later it puts me to busybox. This time I got the following message:
```
(initramfs) mount: mounting /dev/loop0 // filesystem.squashfs failed: No such device. Can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on // filesystem.squashfs
```

Then I used ubuntu usb creator, thinking maybe that one works. The exact same error. 

Next, I burned a cd. This time the cd booted into the desktop but veeeery slowly. I started the installer and after the partition selection part I got an error message: probably due to burning error blah blah blah try burning the cd with slower speed.

I looked up the syslog file and I found the following error message:
```
Sep 28 22:24:44 ubuntu kernel: [  467.663387] SQUASHFS error: zlib_inflate error, data probably corrupt
Sep 28 22:24:44 ubuntu kernel: [  467.663393] SQUASHFS error: squashfs_read_data failed to read block 0x32d8a7
Sep 28 22:24:44 ubuntu kernel: [  467.663396] SQUASHFS error: Unable to read fragment cache entry [32d8a7]
Sep 28 22:24:44 ubuntu kernel: [  467.663398] SQUASHFS error: Unable to read page, block 32d8a7, size c668
Sep 28 22:24:44 ubuntu kernel: [  467.663403] SQUASHFS error: Unable to read fragment cache entry [32d8a7]
Sep 28 22:24:44 ubuntu kernel: [  467.663404] SQUASHFS error: Unable to read page, block 32d8a7, size c668
Sep 28 22:24:44 ubuntu kernel: [  467.663408] SQUASHFS error: Unable to read fragment cache entry [32d8a7]
Sep 28 22:24:44 ubuntu kernel: [  467.663409] SQUASHFS error: Unable to read page, block 32d8a7, size c668
Sep 28 22:24:44 ubuntu kernel: [  467.663412] SQUASHFS error: Unable to read fragment cache entry [32d8a7]
Sep 28 22:24:44 ubuntu kernel: [  467.663414] SQUASHFS error: Unable to read page, block 32d8a7, size c668
Sep 28 22:24:44 ubuntu kernel: [  467.663417] SQUASHFS error: Unable to read fragment cache entry [32d8a7]
Sep 28 22:24:44 ubuntu kernel: [  467.663418] SQUASHFS error: Unable to read page, block 32d8a7, size c668
Sep 28 22:24:44 ubuntu kernel: [  467.663421] SQUASHFS error: Unable to read fragment cache entry [32d8a7]
Sep 28 22:24:44 ubuntu kernel: [  467.663422] SQUASHFS error: Unable to read page, block 32d8a7, size c668
Sep 28 22:24:44 ubuntu kernel: [  467.663426] SQUASHFS error: Unable to read fragment cache entry [32d8a7]
Sep 28 22:24:44 ubuntu kernel: [  467.663427] SQUASHFS error: Unable to read page, block 32d8a7, size c668
Sep 28 22:24:44 ubuntu kernel: [  467.663431] SQUASHFS error: Unable to read fragment cache entry [32d8a7]
Sep 28 22:24:44 ubuntu kernel: [  467.663432] SQUASHFS error: Unable to read page, block 32d8a7, size c668
Sep 28 22:24:44 ubuntu kernel: [  467.663436] SQUASHFS error: Unable to read fragment cache entry [32d8a7]
Sep 28 22:24:44 ubuntu kernel: [  467.663437] SQUASHFS error: Unable to read page, block 32d8a7, size c668
```

I don't know what's next?

---

### Post by Lightstar on 2012-09-28
I thought Ubuntu came with gnome.
Is that removed in 12.10?

If it's still included, I don't see the point of yet another distro added to the 50 distributions based on ubuntu.

---

### Post by jbicha on 2012-09-28
jozmak, you could try dd directly. If you USB stick is recognized as /dev/sdb; note this command will effectively erase everything on /dev/sdb!

```

dd if=quantal-ubuntu-gnome-amd64-20120927.iso of=/dev/sdb
```

---

### Post by jozmak on 2012-09-29
The dd method didn't work at all. It puts me back into the harddrive without any message.

---

### Post by jbicha on 2012-09-29
Oops, it needs to begin with ```
sudo
```

---

### Post by jozmak on 2012-09-29
> **jbicha said:**
> Oops, it needs to begin with ```
sudo
```

I did burn with sudo and it still puts me back to harddrive

---

### Post by Stinger on 2012-09-29
> **jozmak said:**
> I did burn with sudo and it still puts me back to harddrive
Same here, no joy with the dd command it only creates an non boot-able  ISO 9660 image :( 
I can't get the usb-creator to work either as you can see here:
[usb-creator-gtk crashed]("http://ubuntuforums.org/showthread.php?t=2064033"), a bad case of catch 22.

Not completely unsolvable though, I had a usb-pen with the Gnome-Shell Remix 12.04 available, I booted into a live session with that one, launched the usb-creator from there, 
selected the Ubuntu Gnome Remix beta iso from my hard-drive and badabing badaboom I had a working bootable Beta usb-pen :D

Not an ideal solution, but just to find out if the beta iso worked or not, and it does, nothing wrong with the iso ;)

---

### Post by jozmak on 2012-09-29
> **Stinger said:**
> Same here, no joy with the dd command it only creates an non boot-able  ISO 9660 image :( 
I can't get the usb-creator to work either as you can see here:
[usb-creator-gtk crashed]("http://ubuntuforums.org/showthread.php?t=2064033"), a bad case of catch 22.

Not completely unsolvable though, I had a usb-pen with the Gnome-Shell Remix 12.04 available, I booted into a live session with that one, launched the usb-creator from there, 
selected the Ubuntu Gnome Remix beta iso from my hard-drive and badabing badaboom I had a working bootable Beta usb-pen :D

Not an ideal solution, but just to find out if the beta iso worked or not, and it does, nothing wrong with the iso ;)

I've tried every conceivable variation. The only time I managed to boot up when I burnt the image into cd. But when I tried to install it I got an error.

---

### Post by mc4man on 2012-09-29
> **jozmak said:**
> I've tried every conceivable variation. The only time I managed to boot up when I burnt the image into cd. But when I tried to install it I got an error.
Well forget Startup disc creator in 12.10, been somewhat broken for weeks, now probably totally so.

Have had no issue with unetbootin (plain repo version
Because I use a couple of usb sticks just for booting live images **before **starting unetbootin I always reformat the stick (FAT32) in Disks (or gparted

Sometimes unet doesn't handle overwriting a previous boot disc properly & it won't boot up.
Otherwise get another or new usb stick

---

