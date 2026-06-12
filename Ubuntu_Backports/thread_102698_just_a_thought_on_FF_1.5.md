---
title: "just a thought on FF 1.5"
date: 2005-12-12
forum: Ubuntu Backports
---

### Post by muszek on 2005-12-12
I'm not an expert (just a regular user), so please forgive me if I'm saying something really stupid.  I just read the article on distrowatch about FF 1.5.

Would such solution work?
 - FF 1.5 installed as a completely separate package/set of packages.
 - FF 1.0.x would remain and everything depending on it would keep doing so.

---

### Post by jdong on 2005-12-12
Yes, that would, though no such packages exist and Backports does not have the authority to make such a package for Dapper, and nor does it make sense for such a package to be made.

I have proposed separate firefox and mozilla-firefox-browser packages, firefox being the system's Firefox and mozilla-firefox-browser being a repackaged version of the official binaries at Mozilla.com. I've received neutral comments on that.

---

### Post by canadianwriterman on 2005-12-12
I believe that if you install Firefox 1.5 by using the following instructions from the Wiki...

[https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29)

...it is a separate installation and leaves the default Firefox in place.

---

### Post by jdong on 2005-12-12
Yes --- those methods of installing Firefox are the recommended way, as opposed to Backporting. Firefox 1.5 is more of an impossibility.

---

### Post by muszek on 2005-12-13
yeah, but try telling that to the average user.  a browser is one of the most important (if not the most) applications and telling average people "please either wait till april or follow our 20-or-so-steps-instructions if you want a newer, shiny verion of your favorite app" basically means "please choose another operating system".

btw... 1.5 has been out for a short period of time.  here are yesterday's google analytics stats for firefox on one of my sites: 1.0.7 - 624 visits, 54% of all FF visits.  1.5 - 280 (24%).  People are switching rather quickly (pre-1.0.7 versions are little over 22% alltogether, and 1.0.7 hasn't been around all that long).  Soon, we'll start seeing 1.5-only extensions (it has different api) and people will need to have 1.5.

Not providing an easy (synaptic-based) way of installing 1.5 is a bit silly reason for losing user base... am I right?

edit: repositories have 2 different versions of apache, 3 diffferent versions of php and 2 versions of mysql (I guess it will be 3 once they include mysql 5).  
And Ubuntu is an easy-to-use, relatively bleeding edge desktop distro... which either stops being a bleeding-edge (not providing new version of one of the most important pieces of software for almost half a year) or easy to use (forcing users to find a solution and implement it on their own).  Some people would rather go back to double-clicking on setup.exe.

Just to add something positive: my sister (smart person; not computer savvy, but a very frequent user) has had Ubuntu for 2 weeks on her laptop (single boot, windows has gone to the trashcan) and she's not complaining a lot (even though gnome seems to freeze often for an unknown reason).  I made a file named "most_important_commands" and most of the time she knows what to do by herself :) (sadly, it often involves a kill command).

---

### Post by jdong on 2005-12-13
[QUOTE=muszek]yeah, but try telling that to the average user.  a browser is one of the most important (if not the most) applications and telling average people "please either wait till april or follow our 20-or-so-steps-instructions if you want a newer, shiny verion of your favorite app" basically means "please choose another operating system".
[/quote]
Don't exaggerate. There are equal number of steps for unpacking the tar.gz from mozilla.org to a folder in your home directory as for installing Firefox 1.5 under Windows.

---

### Post by aysiu on 2005-12-13
[QUOTE=muszek]
btw... 1.5 has been out for a short period of time.  here are yesterday's google analytics stats for firefox on one of my sites: 1.0.7 - 624 visits, 54% of all FF visits.  1.5 - 280 (24%).  People are switching rather quickly (pre-1.0.7 versions are little over 22% alltogether, and 1.0.7 hasn't been around all that long).[/QUOTE] I would actually say the stats you cited work against your argument. If people are so impatient that they can't wait a few months to get the latest version of Firefox, then surely the majority of Firefox users would be using 1.5 already--that's clearly not the case.

The "average user" you're talking about, first of all, probably doesn't even use Firefox. Most "average users" are still using Internet Explorer, believe it or not. Also, the "average users" I converted over to Firefox at my workplace--you know what version they're using? Whatever version I first installed for them. If it was 1.0.4, it's still 1.0.4. If it was 0.9, it's still 0.9.

These "average people" you keep talking about not only do not want the latest and greatest version of the software they use--they rarely (if ever) upgrade at all. They just want to *use* their software, not get the bleeding edge version of it.

Average users, as I've seen in real life, are perfect Ubuntu users--a little notifier tells them there are updates and all their packages get the security patches they need. That's it. Otherwise, they just *use* the programs.

---

### Post by muszek on 2005-12-14
Points taken, I'll behave from now on :)

---

### Post by aysiu on 2005-12-14
You're behaving just fine.
What got me all worked up was the "average user" thing.

Thing is... you kind of have a point--it's just not the average user but the average *Ubuntu* user (who is *not* the average user), and my guess is the average *Ubuntu* user wants Firefox 1.5 now. In fact, that gives me an idea for a poll...

I think I'm probably in the minority in the Ubuntu community--still using 1.0.7.

I guess the idea, though, is that most people computer savvy enough to:
1. Know about Ubuntu
2. Actually want to install and configure an operating system

can probably copy and paste some commands from [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) into a terminal.

**Edit**: I made [the poll](http://www.ubuntuforums.org/showthread.php?t=103393). My guess is most people will say 1.5.

---

### Post by Confuse on 2005-12-15
Off topic but firefox related anyway, do you guys get weird blinking on the firefox menus sometimes? I'm using ubuntu's default clearlooks theme (non-cario). Its sort of annoying but not life threatening.

---

### Post by towsonu2003 on 2005-12-15
[QUOTE=Confuse]Off topic but firefox related anyway, do you guys get weird blinking on the firefox menus sometimes? I'm using ubuntu's default clearlooks theme (non-cario). Its sort of annoying but not life threatening.[/QUOTE]
I remember seeing a bug for that in firefox bugzilla ( [http://www.mozilla.org/support/firefox/bugs](http://www.mozilla.org/support/firefox/bugs) ). May be they have a workaround? (hopefully, I'm not forking the thread?)

---

### Post by jdong on 2005-12-15
I get the blinking menu bug at times, yes, that is a known issue with Firefox 1.5, and not Ubuntu specific.

---

### Post by kingsidy on 2005-12-15
When i am using the noia theme, a white stripe appears on the very top. If using another theme, that does not happen as much. Don't know why

---

### Post by ubuntu_demon on 2005-12-15
[QUOTE=jdong]Yes, that would, though no such packages exist and Backports does not have the authority to make such a package for Dapper, and nor does it make sense for such a package to be made.

I have proposed separate firefox and mozilla-firefox-browser packages, firefox being the system's Firefox and mozilla-firefox-browser being a repackaged version of the official binaries at Mozilla.com. I've received neutral comments on that.[/QUOTE]

That seems like a good way to solve this backporting problem for Dapper.  It's important that the devs understand that most Ubuntu users like backports.

---

### Post by iMerlin on 2005-12-19
I suggest trying Klik ([http://klik.atekon.de/](http://klik.atekon.de/)) and downloading FF 1.5 from there if you want to try it on your machine.

It's alot faster than 1.0 on my computer at least. Besides, uninstalling a Klik package is as easy as deleting the file from your desktop.

---

### Post by Zotova on 2005-12-19
[QUOTE=aysiu]The "average user" you're talking about, first of all, probably doesn't even use Firefox. Most "average users" are still using Internet Explorer, believe it or not.[/quote]

Agreed, but if they are using IE I disagree that they'd be using Linux at all.

With that in mind Linux users are generally going to be a bit more techy minded and will want to be up-to-date so they are not vulnerable to any known security issues and so things generally improve (speed, features etc).

By next April (Dapper) Firefox 2.0 will be very close if not already out - so for those who like to only use apt-get that will basically mean they will never get to use 1.5. Or, if 2.0 isn't out by April it will most likely be released shortly after the Dapper release, which means the same problem is going to arise again - people will be stuck with an old outdated and possibly dangerous version of Firefox.

My point being some kind of solution needs to be put into action instead of the attitude of users can wait, users are dumb, they probably don't even know what version of Firefox they are using anyway. That may be true for Windows users but in general I'd say Linux users are more aware of what they are using and what version it is.

So basically why can't Firefox 1.5 be put into the backports like the first user suggested with no links to the current firefox (e.g. it doesn't overwrite 1.07). That is basically the same as the how-to's suggest and provides a way for users who only install something if it is in apt-get.

After all the overall aim of Ubuntu is supposed to be ease of use. A distro for everyone that everyone can use - however I don't see why easy to use should also mean outdated and potentially vulnerable software.

---

### Post by aysiu on 2005-12-19
[QUOTE=Zotova]
With that in mind Linux users are generally going to be a bit more techy minded and will want to be up-to-date so they are not vulnerable to any known security issues and so things generally improve (speed, features etc).

By next April (Dapper) Firefox 2.0 will be very close if not already out - so for those who like to only use apt-get that will basically mean they will never get to use 1.5. Or, if 2.0 isn't out by April it will most likely be released shortly after the Dapper release, which means the same problem is going to arise again - people will be stuck with an old outdated and possibly dangerous version of Firefox.[/QUOTE] First of all, one of the new features in 1.5 is self-updating--the Firefox application itself downloads and installs updates. My hope is that the Ubuntu developers will leave Firefox to do its job rather than making the repositories responsible for updating Firefox. If that's the case, 1.5 users will get automatic updates to 2.0.

Secondly, Ubuntu's packages may be out of date, but each release gets security updates for eighteen or more months after release. I remember Hoary got an update to Firefox 1.0.7 not because the developers wanted people to have cutting edge software but because 1.0.7 was a security update to 1.0.6.

Security is not an issue. It's only people who want cutting edge software and don't want to bother doing command-line instructions to get it that are frustrated. I'm perfectly fine using 1.0.7.

---

### Post by Zotova on 2005-12-19
[QUOTE=aysiu]First of all, one of the new features in 1.5 is self-updating--the Firefox application itself downloads and installs updates. My hope is that the Ubuntu developers will leave Firefox to do its job rather than making the repositories responsible for updating Firefox. If that's the case, 1.5 users will get automatic updates to 2.0.[/quote]

True the built-in Firefox update does work very well now. But this in itself has a security issue. The folder where Firefox is stored has to have user permissions - otherwise it doesn't work. This doesn't bother me personally as I aren't security obsessed - but I'm sure it would bother some other Linux users who are more security minded. However I do agree with you, it would be the way to go.

But then there is Epiphany. In its current state it is useless without Firefox, if Firefox updates itself to 2.0 then I'd suspect epiphany is not going to work again... The same as if you replace 1.07 with 1.5. The Gnome developers should really fix Epiphany but that is besides the point really.

> Security is not an issue. It's only people who want cutting edge software and don't want to bother doing command-line instructions to get it that are frustrated. I'm perfectly fine using 1.0.7.

But what about the numerous bugs which have been fixed since 1.07? I personally don't want to be 6 months behind the rest of the world and I'm sure I'm not the only one who shares that view. I wouldn't even call Firefox 1.5 cutting edge either, if you want the latest you'd use a nightly build. Whilst you may be ok with 1.0.7 I personally wasn't. For me 1.0.7 was slow and crashed every time I opened a page with a few large images.

Mozilla's 1.0.7 did not have any of those problems nor has 1.5. To add to that there was the problem with 1.0.4 (I think, I forget the exact no.) - where Ubuntu's Firefox could not access the Mozilla Update section. Personally I feel Firefox is very badly handled by Ubuntu considering it is supposed to be the main browser.

---

### Post by macleod199 on 2005-12-20
[QUOTE=aysiu]First of all, one of the new features in 1.5 is self-updating--the Firefox application itself downloads and installs updates. My hope is that the Ubuntu developers will leave Firefox to do its job rather than making the repositories responsible for updating Firefox. If that's the case, 1.5 users will get automatic updates to 2.0.
[/QUOTE]

I really, really doubt that, based on all the reasons why it is hard to backport stated above.

---

### Post by poofyhairguy on 2005-12-20
[QUOTE=Zotova] I personally don't want to be 6 months behind the rest of the world and I'm sure I'm not the only one who shares that view. [/QUOTE]

You are not or Gentoo would not exist.

---

### Post by Zotova on 2005-12-21
[QUOTE=poofyhairguy]You are not or Gentoo would not exist.[/QUOTE]

Just looking at the Gentoo install put me off using it. Again, I'm sure I'm not alone there either! :)

---

### Post by jdong on 2005-12-21
[QUOTE=poofyhairguy]You are not or Gentoo would not exist.[/QUOTE]
:)

I'm setting up Gentoo as we speak :). Gonna try my ex-favorite distro again.

I gotta say, while watching emerge do its magic, **majority** of the stable-marked packages are actually **older** than Breezy's packages. However, using packages.keywords to unmask certain packages satisfies my bleeding edge urge.

---

### Post by mark on 2005-12-21
Being kind o' simple, dumb and stupid, I used the brute-force approach.  I downloaded the binary tarball from mozilla, untarred it into my home directory, spent c. 15-20 minutes setting links, etc. and it seems to be working fine.

Of course, I'm the sole user of this computer, so I don't have to worry about anybody else...

---

### Post by AgenT on 2005-12-21
You can also install it system wide. It is very simple and took about 3 minutes. Just read the wiki page dealing with FireFox updating and just adapt it to your computer and Firefox version. It is rather easy to "do it yourself".

One really annoying thing about 1.5 is that for some reason, it still likes to start the updating applet once in awhile even though all the auto update options in about:config and preferences are off. Maybe there is something in about:config that is not obvious.

---

### Post by zbowling on 2005-12-24
[QUOTE=jdong]I have proposed separate firefox and mozilla-firefox-browser packages, firefox being the system's Firefox and mozilla-firefox-browser being a repackaged version of the official binaries at Mozilla.com. I've received neutral comments on that.[/QUOTE]

There is a big problem with that. Mozilla.com doesn't release binaries for all platforms. They release x86 win32, x86 linux, and macos x. Contributions for solaris and sometime O/S2 and some off beat OSs get posted but none for Powerpc Linux and x86_64 Windows and Linux. That would mean that package would be x86 specific.

---

