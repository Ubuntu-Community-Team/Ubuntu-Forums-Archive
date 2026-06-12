---
title: "features Ubuntu shoould implement.  critique on Kumail HT's blog"
date: 2008-10-19
forum: The Cafe
---

### Post by adamogardner on 2008-10-19
[http://www.kumailht.com/blog/linux/10-features-ubuntu-should-implement/](http://www.kumailht.com/blog/linux/10-features-ubuntu-should-implement/)

has some very exciting ideas such as time based wall papers and intelligent icons.  Any comments?

---

### Post by cardinals_fan on 2008-10-19
Numbers 1-8 are issues with GNOME.  Only 9 is directly related to Ubuntu.

---

### Post by billgoldberg on 2008-10-19
> **adamogardner said:**
> [http://www.kumailht.com/blog/linux/10-features-ubuntu-should-implement/](http://www.kumailht.com/blog/linux/10-features-ubuntu-should-implement/)

has some very exciting ideas such as time based wall papers and intelligent icons.  Any comments?

Most of what he suggested already exists. It just is not installed/actived by default.

I don't agree with him.

--

A feature I want to see in the next Ubuntu version is an advanced option in the linux live cd installer that will enable you to select the packages you want to install, or the packages you don't want installed.

---

### Post by Mr. Picklesworth on 2008-10-19
#2 already exists, albeit at an early stage :)
[http://ubuntuforums.org/showthread.php?t=784881](http://ubuntuforums.org/showthread.php?t=784881)

It would be cooler if a wallpaper could instead be powered by a small Python script that works with the proper sunrise / sunset times...

Not a fan of how all these mockups are done on top of MacOS screenshots :/

The stuff for the desktop and icons would be nice. (Calcium FTW!)

---

### Post by cardinals_fan on 2008-10-19
> **Mr. Picklesworth said:**
> 
It would be cooler if a wallpaper could instead be powered by a small Python script that works with the proper sunrise / sunset times...

That should be possible with a simple Perl script.  I'll give it a shot and post back once I've done a little work.

---

### Post by Mr. Picklesworth on 2008-10-19
> **cardinals_fan said:**
> That should be possible with a simple Perl script.  I'll give it a shot and post back once I've done a little work.

This is true. I believe there's a dbus interface for the wallpaper stuff now. (Check out D-Feet to find it; that program is great).

However, it would be nice if a wallpaper that is actually a full-fledged Python script was presented in the wallpaper preferences. I believe Enlightenment has some sort of fancy animated wallpapers going on.

---

### Post by cardinals_fan on 2008-10-19
> **Mr. Picklesworth said:**
> This is true. I believe there's a dbus interface for the wallpaper stuff now. (Check out D-Feet to find it; that program is great).
I'm just using hsetroot, since I don't use nautilus.

---

### Post by Mr. Picklesworth on 2008-10-19
> **cardinals_fan said:**
> I'm just using hsetroot, since I don't use nautilus.

Ah, as it should be! Good man :P

(I despise file managers rendering the desktop. But, alas...)

---

### Post by cardinals_fan on 2008-10-19
> **Mr. Picklesworth said:**
> Ah, as it should be! Good man :P

(I despise file managers rendering the desktop. But, alas...)
A forgotten-until-now French project has put things on hold, but the script itself should only take me 15 minutes.  The trouble is finding good images that don't have licensing issues - can anyone help with that?

---

### Post by elmer_42 on 2008-10-19
Perhaps you could use the "Dawn of Ubuntu" images? Or take some yourself, out in your backyard or something?

---

### Post by cardinals_fan on 2008-10-19
> **elmer_42 said:**
> Perhaps you could use the "Dawn of Ubuntu" images? Or take some yourself, out in your backyard or something?
Never mind, I had a better idea.  It may take a couple days (this week is very hectic for me), but I will have a bloatless weather script done soon :)

---

### Post by Polygon on 2008-10-19
some of those ideas are kinda stupid. Like...if ubuntu only notified me through the icons that my drive was almost full, then i would never notice it. Especially since by default the icons are kinda small, even if you did look you would have to squint.

Having an analog clock on the taskbar is the stupidest thing ive ever heard. Unless you have a huge taskbar, then you would not be able to read it, and even if you could, you would have no idea what time it is.

weather based wallpaper: sounds like a cool program, but should not be installed by default

time based wallpaper: ability to change wallpapers after a certain timelimit should be in by default, and make it so it picks them from a certain (or multiple) folders would be great as well.

and a short little introduction would be nice too, kinda like what OEM computers do. Maybe load up a little movie on first boot.

---

### Post by Paqman on 2008-10-19
> **Polygon said:**
> 
and a short little introduction would be nice too, kinda like what OEM computers do. Maybe load up a little movie on first boot.

I've been thinking that for a while. Even just a short intro on using Add/Remove would be handy for new users.

---

### Post by Lord Xeb on 2008-10-20
I like a lot of those features. But the biggy is the animated intro to Ubuntu. It would make trasition a little but easier for the newbie and stuff. There should be an option when you log in for the first time if you would an into tutorial.

---

### Post by adamogardner on 2008-10-20
> **cardinals_fan said:**
> That should be possible with a simple Perl script.  I'll give it a shot and post back once I've done a little work.

Dude, you're hardcore.

---

### Post by cardinals_fan on 2008-10-20
I just remembered this thread ;)

The whole weather idea seems stupid to me, but if you're convinced you want it, set up [conkyForecast]("http://ubuntuforums.org/showthread.php?t=869328&highlight=conky+weather").  Something along these lines should work from there on out (this is coming straight out of the brain onto the post, so it hasn't been tested):```
#!/usr/bin/perl

$code="*****";

while ($g=exec "conkyForecast -d CC -l $code")
{

if ($g=="Fair")
{
	exec "hsetroot -full ~/.weather/fair.jpg";
}
}
```I leave it up to you to pick images and continue.

---

### Post by gletob on 2008-10-20
> **cardinals_fan said:**
> A forgotten-until-now French project has put things on hold, but the script itself should only take me 15 minutes.  The trouble is finding good images that don't have licensing issues - can anyone help with that?

This site is great but I don't know about licensing.

[http://interfacelift.com/wallpaper_beta/downloads/date/any/](http://interfacelift.com/wallpaper_beta/downloads/date/any/)

---

### Post by Riffer on 2008-10-20
I found that most (all) his ideas to be (for me) uninteresting.  I wouldn't any as a default.

---

### Post by Dev'olution on 2008-10-20
In my opinion a lot of his ideas were not well thought out, and to be honest... as shown by the defrag pic... rather spurred on by a windows theme.

We are ubuntu, not doze.

---

### Post by etnlIcarus on 2008-10-21
Only idea that caught my attention was the visual directory heirarchy. Does anything like that exist for *nix (or any OS)?

---

### Post by pt123 on 2008-10-21
You could do a few of those things with Conky

---

### Post by armageddon08 on 2008-10-21
As far as I remember, Fedora 9's 'Infinity' wallpaper had implemented the time-based wallpaper concept where the color of the wallpaper used to change gradually as time passed by (though it was not as dynamic as the one suggested in the blog).
Another proposition which caught my attention was the 'Visual File Hierarchy' system, but then again it's upto the GNOME(Nautilus) devs to do not Ubuntu's.

---

### Post by adamogardner on 2008-10-21
> **WestAussieUbu said:**
> We are ubuntu, not doze.

Not me;  I'm ibuntooze. (gentoo is in there too)

---

### Post by K.Mandla on 2008-10-21
Meh. Nothing there that particularly enthralls me. Certainly not talking icons.

---

### Post by klerfayt on 2008-10-21
bananas in my trash bin? c'mon...

---

### Post by Canis familiaris on 2008-10-21
> **cardinals_fan said:**
> I just remembered this thread ;)

The whole weather idea seems stupid to me, but if you're convinced you want it, set up [conkyForecast]("http://ubuntuforums.org/showthread.php?t=869328&highlight=conky+weather").  Something along these lines should work from there on out (this is coming straight out of the brain onto the post, so it hasn't been tested):```
#!/usr/bin/perl

$code="*****";

while ($g=exec "conkyForecast -d CC -l $code")
{

if ($g=="Fair")
{
	exec "hsetroot -full ~/.weather/fair.jpg";
}
}
```I leave it up to you to pick images and continue.

Short and Sweet...very clever idea :)

---

### Post by chucky chuckaluck on 2008-10-21
a dorian gray style wallpaper (that actually worked) might be kind of cool.

---

### Post by majabl on 2008-10-21
> **K.Mandla said:**
> Meh. Nothing there that particularly enthralls me. Certainly not talking icons.

I thought similarly.  For instance, weather on my desktop?  If my computer's on then I'm not looking at my desktop: I'm browsing the web, word processing, or whatever.  If I were to be looking at my desktop for any length of time then I may as well save some energy and turn the computer off.  Then I can look out of a *real* window and see the weather first hand.  Controversial, I know. ;-)

---

### Post by Wolki on 2008-10-21
> **Mr. Picklesworth said:**
> (I despise file managers rendering the desktop. But, alas...)

Without file manager as desktop, no home as desktop, though, and that setting is really nice. Everything you need is just a "show desktop" away.

---

### Post by PocketSam on 2008-10-22
I've found an interesting [blog page]("http://www.kumailht.com/blog/linux/10-features-ubuntu-should-implement/"). I think that the author has very exciting ideas.
What do you think?

---

### Post by biji on 2008-10-22
wow that's hard man ^^

---

### Post by sethvath on 2008-10-22
The author should select a team, pick one of the 9 features and get working on it.

---

### Post by LeAstrale on 2008-10-22
Very nice read, however those should be non-distro specific if you ask me.

---

### Post by overdrank on 2008-10-22
Moved to Cafe :)

---

### Post by Wolki on 2008-10-22
dupe of [http://ubuntuforums.org/showthread.php?t=953013](http://ubuntuforums.org/showthread.php?t=953013)

---

### Post by kernelhaxor on 2008-10-22
This was discussed just a couple days back

---

### Post by Helios1276 on 2008-10-22
I liked the folder hierarchy idea and the 'smart' icons that were mentioned. However, the rest seemed like unimportant eye-candy and the addition of a media software which should remain the choice of the user IMO.Having things like synaptic and the terminal, I think, allows for the ability to not have bloat an installation.

---

### Post by Archmage on 2008-10-22
Sorry, but all the features are already there. So why bother?

---

### Post by overdrank on 2008-10-22
Threads merged   :oops: after being moved to cafe.

---

### Post by Solicitous on 2008-10-22
I have to ask why some people are obsessed with weather applets?  I look out the window to see if it is sunny, raining or cloudy.

The timebased background image idea sounds kind of cool, but that is something I wouldn't want implemented by default.  I know for me everytime I use my PC I never see the background (except when I first login) as I've always got applications running.

---

### Post by adamogardner on 2008-10-22
> **Archmage said:**
> Sorry, but all the features are already there. So why bother?

I ACCEPT YOUR APOLOGY, BUT THEN WHY BOTHER :popcorn:

---

### Post by easybake on 2008-10-22
There is a simple way to change wallpapers relative to time of day. It's a simple script. [Here.]("http://joeamined.wordpress.com/2008/02/15/automatically-changing-wallpaper-relatively-to-daytime-in-ubuntu/")

You can also trigger your compiz rain/snow effects according to what the weather is. [Here.]("http://ubuntuforums.org/showthread.php?t=669922") You could use that same idea to change the background.

---

### Post by bruce89 on 2008-10-22
It all seems like useless bloat to me.

Also, I notice the person doesn't understand this for upstream GNOME to implement.

---

### Post by golusweet on 2009-03-22
I saw these features on blog,and these features looks cool.:p

What you guys think?


[http://www.kumailht.com/blog/linux/10-features-ubuntu-should-implement/](http://www.kumailht.com/blog/linux/10-features-ubuntu-should-implement/)

---

### Post by Rokurosv on 2009-03-22
I think some are really nice, the weather and wallpaper thing I don't consider to be that important. But I don't think we'll be seeing them anytime soon,

---

### Post by cardinals_fan on 2009-03-22
[http://ubuntuforums.org/showthread.php?t=953013](http://ubuntuforums.org/showthread.php?t=953013)

---

### Post by gjoellee on 2009-03-22
Some of the ideas already exists though

---

### Post by Mehall on 2009-03-22
this was posted the other day.

we have a search function for a reason people.

---

### Post by apmcd47 on 2009-03-22
Item 5 - visual folder hierarchy: Sun's File Manager had that, what, 20 years ago? Makes me feel old... I think that was the least useful part of File Manager. It took too much screen space and told you very little. I always turned it off. No wonder KDE and Gnome don't implement it.

Andrew

---

### Post by andamaru on 2009-03-22
Number one can be done with a widget, and looking out your window goes a long way.

Number two is already in Fedora.

Number three is already present in KDE 4. There is a little bar under the icon that tells you how much space is left.

the 5th one takes up way too much space for the information that it provides you.

the sixth looks like a good idea, but how it was presented looks bad. May a desktop wide tool instead of doing it at the folder level

not sure what he is trying to do in the seventh

and the 8th option would require an update to dvd iso instead of cd's

I believe opensuse comes with a presentation like presented in the 9th option

:D I love pretending I'm an Linux and UI designer expert

---

### Post by jimi_hendrix on 2009-03-22
> **Rokurosv said:**
> I think some are really nice, the weather and wallpaper thing I don't consider to be that important. But I don't think we'll be seeing them anytime soon,

not that hard for those

windows7 already hase wallpapers that change after X seconds, just make something that works in conjunctions with the weather thing in the toolbar in gnome

---

### Post by K.Mandla on 2009-03-22
Implement any of those features on my desktop and I will immediately rip them out. :evil:

---

### Post by Jimmynemo2 on 2009-03-22
I could enjoy the time based wallpaper one, but then I think about it and realize I'd disable it anyway becuase it's wasted cycles for something that only has a wow effect when its new.

Three is the only one I'd use and thought was cool, and linux is already progrssing towards that anyway- pdf icons show the document, jpeg does same. The only thing I'd like fixed is for the computer location to show the same progress bars that vista shows for HDD usage per drive.

Lastly, did no one notice there was no number four? Goes from three to 5....

---

